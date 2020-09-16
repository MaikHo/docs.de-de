---
title: Windows Communication Foundation zu Message Queuing
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: a6e322936740f7d88d30b9a205ac937a807bedc1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552926"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="b7331-102">Windows Communication Foundation zu Message Queuing</span><span class="sxs-lookup"><span data-stu-id="b7331-102">Windows Communication Foundation to Message Queuing</span></span>

<span data-ttu-id="b7331-103">Dieses Beispiel veranschaulicht, wie eine Windows Communication Foundation (WCF)-Anwendung eine Nachricht an eine Message Queuing (MSMQ)-Anwendung senden kann.</span><span class="sxs-lookup"><span data-stu-id="b7331-103">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="b7331-104">Der Dienst ist eine selbst gehostete Konsolenanwendung, die es Ihnen ermöglicht, den Dienst beim Empfang von Nachrichten in der Warteschlange zu beobachten.</span><span class="sxs-lookup"><span data-stu-id="b7331-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="b7331-105">Der Dienst und der Client müssen dazu nicht gleichzeitig ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b7331-105">The service and client do not have to be running at the same time.</span></span>

 <span data-ttu-id="b7331-106">Der Dienst empfängt Nachrichten von der Warteschlange und verarbeitet Bestellungen.</span><span class="sxs-lookup"><span data-stu-id="b7331-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="b7331-107">Der Dienst erstellt eine Transaktionswarteschlage und richtet einen "Nachricht empfangen"-Nachrichtenhandler ein, wie im folgenden Beispielcode gezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7331-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>

```csharp
static void Main(string[] args)
{
    if (!MessageQueue.Exists(
              ConfigurationManager.AppSettings["queueName"]))
       MessageQueue.Create(
           ConfigurationManager.AppSettings["queueName"], true);
        //Connect to the queue
        MessageQueue Queue = new
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);
    Queue.ReceiveCompleted +=
                 new ReceiveCompletedEventHandler(ProcessOrder);
    Queue.BeginReceive();
    Console.WriteLine("Order Service is running");
    Console.ReadLine();
}
```

 <span data-ttu-id="b7331-108">Wenn die Nachricht in der Warteschlange empfangen wird, wird der Nachrichtenhandler `ProcessOrder` aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="b7331-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>

```csharp
public static void ProcessOrder(Object source,
    ReceiveCompletedEventArgs asyncResult)
{
    try
    {
        // Connect to the queue.
        MessageQueue Queue = (MessageQueue)source;
        // End the asynchronous receive operation.
        System.Messaging.Message msg =
                     Queue.EndReceive(asyncResult.AsyncResult);
        msg.Formatter = new System.Messaging.XmlMessageFormatter(
                                new Type[] { typeof(PurchaseOrder) });
        PurchaseOrder po = (PurchaseOrder) msg.Body;
        Random statusIndexer = new Random();
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
        Console.WriteLine("Processing {0} ", po);
        Queue.BeginReceive();
    }
    catch (System.Exception ex)
    {
        Console.WriteLine(ex.Message);
    }

}
```

 <span data-ttu-id="b7331-109">Der Dienst extrahiert die `ProcessOrder` aus dem MSMQ-Nachrichtentext heraus und verarbeitet die Bestellung.</span><span class="sxs-lookup"><span data-stu-id="b7331-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>

 <span data-ttu-id="b7331-110">Der Name der MSMQ-Warteschlange wird im appSettings-Abschnitt der Konfigurationsdatei angegeben, wie in der folgenden Beispielkonfiguration gezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7331-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="b7331-111">Im Warteschlangennamen wird ein Punkt (.) für den lokalen Computer verwendet, und in der Pfadangabe werden umgekehrte Schrägstriche als Trennzeichen verwendet.</span><span class="sxs-lookup"><span data-stu-id="b7331-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>

 <span data-ttu-id="b7331-112">Der Client erstellt eine Bestellung und reicht die Bestellung im Geltungsbereich der Transaktion ein, wie im folgenden Beispielcode gezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7331-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>

```csharp
// Create the purchase order
PurchaseOrder po = new PurchaseOrder();
// Fill in the details
...

OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");

MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    client.SubmitPurchaseOrder(ordermsg);
    scope.Complete();
}
Console.WriteLine("Order has been submitted:{0}", po);

//Closing the client gracefully closes the connection and cleans up resources
client.Close();
```

 <span data-ttu-id="b7331-113">Der Client verwendet einen benutzerdefinierten Client zum Senden der MSMQ-Nachricht an die Warteschlange.</span><span class="sxs-lookup"><span data-stu-id="b7331-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="b7331-114">Da es sich bei der Anwendung, die die Nachricht empfängt und verarbeitet, um eine MSMQ-Anwendung und nicht um eine WCF-Anwendung handelt, gibt es keinen impliziten Dienstvertrag zwischen den beiden Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="b7331-114">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="b7331-115">Deshalb kann in diesem Szenario kein Proxy mit dem Tool "Svcutil.exe" erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="b7331-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="b7331-116">Der benutzerdefinierte Client ist für alle WCF-Anwendungen, die die- `MsmqIntegration` Bindung zum Senden von Nachrichten verwenden, im Wesentlichen identisch.</span><span class="sxs-lookup"><span data-stu-id="b7331-116">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="b7331-117">Im Gegensatz zu anderen Clients enthält dieser keinen Bereich von Dienstvorgängen.</span><span class="sxs-lookup"><span data-stu-id="b7331-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="b7331-118">Es ist nur ein Sende-Nachricht-Vorgang.</span><span class="sxs-lookup"><span data-stu-id="b7331-118">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor
{
    public OrderProcessorClient(){}

    public OrderProcessorClient(string configurationName)
        : base(configurationName)
    { }

    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SubmitPurchaseOrder(msg);
    }
}
```

 <span data-ttu-id="b7331-119">Wenn Sie das Beispiel ausführen, werden die Client- und Dienstaktivitäten sowohl im Dienst- als auch im Clientkonsolenfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7331-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="b7331-120">Sie können sehen, wie der Dienst Nachrichten vom Client empfängt.</span><span class="sxs-lookup"><span data-stu-id="b7331-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="b7331-121">Drücken Sie die EINGABETASTE in den einzelnen Konsolenfenstern, um den Dienst und den Client zu schließen.</span><span class="sxs-lookup"><span data-stu-id="b7331-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="b7331-122">Beachten Sie, dass aufgrund der Verwendung einer Warteschlange der Client und der Dienst nicht gleichzeitig ausgeführt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="b7331-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="b7331-123">Sie können beispielsweise den Client ausführen, ihn schließen und anschließend den Dienst starten, der dann trotzdem noch die Nachrichten des Clients empfängt.</span><span class="sxs-lookup"><span data-stu-id="b7331-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

> [!NOTE]
> <span data-ttu-id="b7331-124">Dieses Beispiel erfordert die Installation von Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="b7331-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="b7331-125">Weitere Informationen finden Sie in den Installationsanweisungen in [Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="b7331-125">See the installation instructions in [Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)).</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="b7331-126">Einrichten, erstellen und Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="b7331-126">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="b7331-127">Stellen Sie sicher, dass Sie das [einmalige Setup Verfahren für die Windows Communication Foundation Beispiele](one-time-setup-procedure-for-the-wcf-samples.md)ausgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="b7331-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b7331-128">Wenn der Dienst zuerst ausgeführt wird, wird überprüft, ob die Warteschlange vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b7331-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="b7331-129">Ist die Warteschlange nicht vorhanden, wird sie vom Dienst erstellt.</span><span class="sxs-lookup"><span data-stu-id="b7331-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="b7331-130">Sie können zuerst den Dienst ausführen, um die Warteschlange zu erstellen, oder Sie können sie über den MSMQ-Warteschlangen-Manager erstellen.</span><span class="sxs-lookup"><span data-stu-id="b7331-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="b7331-131">Führen Sie zum Erstellen einer Warteschlange in Windows 2008 die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="b7331-131">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="b7331-132">Öffnen Sie Server-Manager in Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="b7331-132">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="b7331-133">Erweitern Sie die Registerkarte **Features** .</span><span class="sxs-lookup"><span data-stu-id="b7331-133">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="b7331-134">Klicken Sie mit der rechten Maustaste auf **private Nachrichten Warteschlangen**, und wählen Sie **neue**  >  **private Warteschlange**</span><span class="sxs-lookup"><span data-stu-id="b7331-134">Right-click **Private Message Queues**, and then select **New** > **Private Queue**.</span></span>

    4. <span data-ttu-id="b7331-135">Aktivieren Sie das Kontrollkästchen **transaktional** .</span><span class="sxs-lookup"><span data-stu-id="b7331-135">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="b7331-136">Geben Sie `ServiceModelSamplesTransacted` als Namen für die neue Warteschlange ein.</span><span class="sxs-lookup"><span data-stu-id="b7331-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="b7331-137">Um die c#-oder Visual Basic Edition der Projekt Mappe zu erstellen, befolgen Sie die Anweisungen unter [Erstellen der Windows Communication Foundation Beispiele](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7331-137">To build the C# or Visual Basic edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="b7331-138">Um das Beispiel in einer Konfiguration mit einem einzelnen Computer auszuführen, befolgen Sie die Anweisungen unter [Ausführen der Windows Communication Foundation Beispiele](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7331-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="b7331-139">Führen Sie das Beispiel Computer übergreifend aus.</span><span class="sxs-lookup"><span data-stu-id="b7331-139">Run the sample across computers</span></span>

1. <span data-ttu-id="b7331-140">Kopieren Sie die Dienstprogrammdateien aus dem Ordner \service\bin\ (unterhalb des sprachspezifischen Ordners) auf den Dienstcomputer.</span><span class="sxs-lookup"><span data-stu-id="b7331-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="b7331-141">Kopieren Sie die Clientprogrammdateien aus dem Ordner \client\bin\ (unterhalb des sprachspezifischen Ordners) auf den Clientcomputer.</span><span class="sxs-lookup"><span data-stu-id="b7331-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="b7331-142">Ändern Sie in der Datei Client.exe.config die Clientendpunktadresse, und geben Sie anstelle von "." den Namen des Dienstcomputers an.</span><span class="sxs-lookup"><span data-stu-id="b7331-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="b7331-143">Starten Sie auf dem Dienstcomputer Service.exe an einer Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="b7331-143">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="b7331-144">Starten Sie auf dem Clientcomputer Client.exe an einer Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="b7331-144">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7331-145">Die Beispiele sind möglicherweise bereits auf dem Computer installiert.</span><span class="sxs-lookup"><span data-stu-id="b7331-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b7331-146">Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="b7331-146">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b7331-147">Wenn dieses Verzeichnis nicht vorhanden ist, wechseln Sie zu [Windows Communication Foundation (WCF) und Windows Workflow Foundation (WF)-Beispiele für .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , um alle Windows Communication Foundation (WCF) und Beispiele herunterzuladen [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b7331-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7331-148">Dieses Beispiel befindet sich im folgenden Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="b7331-148">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`

## <a name="see-also"></a><span data-ttu-id="b7331-149">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b7331-149">See also</span></span>

- [<span data-ttu-id="b7331-150">Vorgehensweise: Nachrichtenaustausch mit WCF-Endpunkten und Message Queuing-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="b7331-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="b7331-151">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b7331-151">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
