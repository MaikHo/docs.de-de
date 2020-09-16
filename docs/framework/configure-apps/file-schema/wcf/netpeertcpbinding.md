---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 5fe221c5ec6c51afb199b2c66eab9d72cdfd750b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556140"
---
# \<netPeerTcpBinding>
<span data-ttu-id="19d98-101">Definiert eine Bindung für Peerkanal-spezifisches TCP-Messaging.</span><span class="sxs-lookup"><span data-stu-id="19d98-101">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="19d98-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="19d98-102">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding name="string"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           listenIPAddress="String"
           maxBufferPoolSize="integer"
           maxReceiveMessageSize="Integer"
           port="Integer">
    <security mode="None/Transport/Message/TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19d98-103">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="19d98-103">Attributes and Elements</span></span>  
 <span data-ttu-id="19d98-104">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente sowie übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="19d98-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19d98-105">Attribute</span><span class="sxs-lookup"><span data-stu-id="19d98-105">Attributes</span></span>  
  
|<span data-ttu-id="19d98-106">attribute</span><span class="sxs-lookup"><span data-stu-id="19d98-106">Attribute</span></span>|<span data-ttu-id="19d98-107">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="19d98-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19d98-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="19d98-108">closeTimeout</span></span>|<span data-ttu-id="19d98-109">Ein <xref:System.TimeSpan>-Wert, der das Zeitintervall für den Abschluss eines Schließvorgangs angibt.</span><span class="sxs-lookup"><span data-stu-id="19d98-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="19d98-110">Dieser Wert muss größer oder gleich <xref:System.TimeSpan.Zero> sein.</span><span class="sxs-lookup"><span data-stu-id="19d98-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="19d98-111">Der Standardwert ist 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="19d98-111">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="19d98-112">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="19d98-112">listenIPAddress</span></span>|<span data-ttu-id="19d98-113">Eine Zeichenfolge mit einer IP-Adresse, die der Peerknoten auf TCP-Nachrichten überwacht.</span><span class="sxs-lookup"><span data-stu-id="19d98-113">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="19d98-114">Der Standardwert ist `null`.</span><span class="sxs-lookup"><span data-stu-id="19d98-114">The default is `null`.</span></span>|  
|<span data-ttu-id="19d98-115">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="19d98-115">maxBufferPoolSize</span></span>|<span data-ttu-id="19d98-116">Eine ganze Zahl, die die maximale Pufferpoolgröße für diese Bindung angibt.</span><span class="sxs-lookup"><span data-stu-id="19d98-116">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="19d98-117">Der Standardwert ist 524.288 Byte (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="19d98-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="19d98-118">Viele Teile von Windows Communication Foundation (WCF) verwenden Puffer.</span><span class="sxs-lookup"><span data-stu-id="19d98-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="19d98-119">Das Erstellen und Zerstören von Puffern bei jeder Verwendung ist kostspielig. Dasselbe gilt für die Garbage Collection für Puffer.</span><span class="sxs-lookup"><span data-stu-id="19d98-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="19d98-120">Bei Pufferpools können Sie einen zu verwendenden Puffer aus dem Pool nehmen und ihn nach der Verwendung wieder dem Pool zuführen.</span><span class="sxs-lookup"><span data-stu-id="19d98-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="19d98-121">So wird der Aufwand beim Erstellen und Zerstören von Puffern vermieden.</span><span class="sxs-lookup"><span data-stu-id="19d98-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="19d98-122">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="19d98-122">maxReceivedMessageSize</span></span>|<span data-ttu-id="19d98-123">Eine positive ganze Zahl, die die maximale Nachrichtengröße in Bytes einschließlich Header angibt, die in einem für diese Bindung konfigurierten Kanal beim Nachrichtenempfang zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="19d98-123">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="19d98-124">Der Absender einer Nachricht, die diese Grenze überschreitet, erhält einen SOAP-Fehler.</span><span class="sxs-lookup"><span data-stu-id="19d98-124">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="19d98-125">Der Empfänger verwirft die Nachricht und erstellt einen Eintrag des Ereignisses im Ablaufverfolgungsprotokoll.</span><span class="sxs-lookup"><span data-stu-id="19d98-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="19d98-126">Der Standard ist 65536.</span><span class="sxs-lookup"><span data-stu-id="19d98-126">The default is 65536.</span></span>|  
|<span data-ttu-id="19d98-127">name</span><span class="sxs-lookup"><span data-stu-id="19d98-127">name</span></span>|<span data-ttu-id="19d98-128">Eine Zeichenfolge, die den Konfigurationsnamen der Bindung enthält.</span><span class="sxs-lookup"><span data-stu-id="19d98-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="19d98-129">Dieser Wert sollte eindeutig sein, da er von der Bindung zur Identifizierung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="19d98-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="19d98-130">Ab .NET Framework 4 müssen Bindungen und Verhaltensweisen keinen Namen haben.</span><span class="sxs-lookup"><span data-stu-id="19d98-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="19d98-131">Weitere Informationen zur Standardkonfiguration und zu den namenlosen Bindungen und Verhalten finden Sie unter [vereinfachte Konfiguration](../../../wcf/simplified-configuration.md) und [vereinfachte Konfiguration für WCF-Dienste](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="19d98-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="19d98-132">openTimeout</span><span class="sxs-lookup"><span data-stu-id="19d98-132">openTimeout</span></span>|<span data-ttu-id="19d98-133">Ein <xref:System.TimeSpan>-Wert, der das Zeitintervall für den Abschluss eines Öffnungsvorgangs angibt.</span><span class="sxs-lookup"><span data-stu-id="19d98-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="19d98-134">Dieser Wert muss größer oder gleich <xref:System.TimeSpan.Zero> sein.</span><span class="sxs-lookup"><span data-stu-id="19d98-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="19d98-135">Der Standardwert ist 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="19d98-135">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="19d98-136">port</span><span class="sxs-lookup"><span data-stu-id="19d98-136">port</span></span>|<span data-ttu-id="19d98-137">Eine ganze Zahl, die den Netzwerk-Schnittstellenanschluss angibt, an dem diese Bindung TCP-Peerkanalnachrichten verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="19d98-137">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="19d98-138">Dabei muss es sich um einen Wert zwischen <xref:System.Net.IPEndPoint.MinPort> und <xref:System.Net.IPEndPoint.MaxPort> handeln.</span><span class="sxs-lookup"><span data-stu-id="19d98-138">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="19d98-139">Die Standardeinstellung ist 0.</span><span class="sxs-lookup"><span data-stu-id="19d98-139">The default is 0.</span></span>|  
|<span data-ttu-id="19d98-140">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="19d98-140">receiveTimeout</span></span>|<span data-ttu-id="19d98-141">Ein <xref:System.TimeSpan>-Wert, der das Zeitintervall für den Abschluss eines Empfangsvorgangs angibt.</span><span class="sxs-lookup"><span data-stu-id="19d98-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="19d98-142">Dieser Wert muss größer oder gleich <xref:System.TimeSpan.Zero> sein.</span><span class="sxs-lookup"><span data-stu-id="19d98-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="19d98-143">Der Standardwert ist 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="19d98-143">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="19d98-144">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="19d98-144">sendTimeout</span></span>|<span data-ttu-id="19d98-145">Ein <xref:System.TimeSpan>-Wert, der das Zeitintervall für den Abschluss eines Sendevorgangs angibt.</span><span class="sxs-lookup"><span data-stu-id="19d98-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="19d98-146">Dieser Wert muss größer oder gleich <xref:System.TimeSpan.Zero> sein.</span><span class="sxs-lookup"><span data-stu-id="19d98-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="19d98-147">Der Standardwert ist 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="19d98-147">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19d98-148">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="19d98-148">Child Elements</span></span>  
  
|<span data-ttu-id="19d98-149">Element</span><span class="sxs-lookup"><span data-stu-id="19d98-149">Element</span></span>|<span data-ttu-id="19d98-150">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="19d98-150">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="19d98-151">Definiert die Beschränkungen der Komplexität von SOAP-Nachrichten, die von Endpunkten verarbeitet werden können, die mit dieser Bindung konfiguriert wurden.</span><span class="sxs-lookup"><span data-stu-id="19d98-151">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="19d98-152">Dieses Element ist vom Typ <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="19d98-152">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<resolver>](resolver.md)|<span data-ttu-id="19d98-153">Gibt einen Peerresolver an, der von dieser Bindung zum Auflösen einer Peermesh-ID in die Endpunkt-IP-Adressen von Knoten innerhalb des Peermesh verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="19d98-153">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="19d98-154">Definiert die Sicherheitseinstellungen für die Nachricht.</span><span class="sxs-lookup"><span data-stu-id="19d98-154">Defines the security settings for the message.</span></span> <span data-ttu-id="19d98-155">Dieses Element ist vom Typ <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="19d98-155">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19d98-156">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="19d98-156">Parent Elements</span></span>  
  
|<span data-ttu-id="19d98-157">Element</span><span class="sxs-lookup"><span data-stu-id="19d98-157">Element</span></span>|<span data-ttu-id="19d98-158">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="19d98-158">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="19d98-159">Dieses Element enthält eine Auflistung von standardmäßigen und benutzerdefinierten Bindungen.</span><span class="sxs-lookup"><span data-stu-id="19d98-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19d98-160">Hinweise</span><span class="sxs-lookup"><span data-stu-id="19d98-160">Remarks</span></span>  
 <span data-ttu-id="19d98-161">Diese Bindung bietet Unterstützung für das Erstellen von Peer-to-Peer- oder Mehrparteienanwendungen mithilfe von Peertransport über TCP.</span><span class="sxs-lookup"><span data-stu-id="19d98-161">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="19d98-162">Jeder Peerknoten kann als Host für mehrere mit diesem Bindungstyp definierte Peerkanäle fungieren.</span><span class="sxs-lookup"><span data-stu-id="19d98-162">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19d98-163">Beispiel</span><span class="sxs-lookup"><span data-stu-id="19d98-163">Example</span></span>  
 <span data-ttu-id="19d98-164">Im folgenden Beispiel wird die NetPeerTcpBinding-Bindung veranschaulicht, die Mehrparteienkommunikation über einen Peerkanal ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="19d98-164">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="19d98-165">Ein ausführliches Szenario für die Verwendung dieser Bindung finden Sie unter [net Peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="19d98-165">For a detailed scenario of using this binding, see [Net Peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netPeerBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 maxBufferSize="1001"
                 maxConnections="123"
                 maxReceiveMessageSize="1000">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="TransportWithMessageCredential">
            <message clientCredentialType="CardSpace" />
          </security>
        </binding>
      </netPeerBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="19d98-166">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="19d98-166">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="19d98-167">Bindungen</span><span class="sxs-lookup"><span data-stu-id="19d98-167">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="19d98-168">Konfigurieren der vom System bereitgestellten Bindungen</span><span class="sxs-lookup"><span data-stu-id="19d98-168">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="19d98-169">Verwenden von Bindungen, um Dienste und Clients zu konfigurieren</span><span class="sxs-lookup"><span data-stu-id="19d98-169">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- <span data-ttu-id="19d98-170">[Net-Peer-TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="19d98-170">[Net Peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="19d98-171">Peer-to-Peer-Netzwerke</span><span class="sxs-lookup"><span data-stu-id="19d98-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
