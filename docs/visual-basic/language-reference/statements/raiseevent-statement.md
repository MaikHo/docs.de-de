---
title: RaiseEvent-Anweisung
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: 13d86aad8b68391f7effe2f6637adc68d8a3b59a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872014"
---
# <a name="raiseevent-statement"></a><span data-ttu-id="9127c-102">RaiseEvent-Anweisung</span><span class="sxs-lookup"><span data-stu-id="9127c-102">RaiseEvent Statement</span></span>

<span data-ttu-id="9127c-103">Löst ein Ereignis aus, das auf Modulebene innerhalb einer Klasse, eines Formulars oder eines Dokuments deklariert ist.</span><span class="sxs-lookup"><span data-stu-id="9127c-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9127c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9127c-104">Syntax</span></span>  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="9127c-105">Bestandteile</span><span class="sxs-lookup"><span data-stu-id="9127c-105">Parts</span></span>  

 `eventname`  
 <span data-ttu-id="9127c-106">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9127c-106">Required.</span></span> <span data-ttu-id="9127c-107">Der Name des Ereignisses, das auslöst werden soll.</span><span class="sxs-lookup"><span data-stu-id="9127c-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="9127c-108">Dies ist optional.</span><span class="sxs-lookup"><span data-stu-id="9127c-108">Optional.</span></span> <span data-ttu-id="9127c-109">Eine durch Trennzeichen getrennte Liste von Variablen, Arrays oder Ausdrücken.</span><span class="sxs-lookup"><span data-stu-id="9127c-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="9127c-110">Das `argumentlist` Argument muss in Klammern eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="9127c-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="9127c-111">Wenn keine Argumente vorhanden sind, müssen die Klammern ausgelassen werden.</span><span class="sxs-lookup"><span data-stu-id="9127c-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9127c-112">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="9127c-112">Remarks</span></span>  

 <span data-ttu-id="9127c-113">Der erforderliche `eventname` ist der Name eines Ereignisses, das im Modul deklariert ist.</span><span class="sxs-lookup"><span data-stu-id="9127c-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="9127c-114">Es folgt Visual Basic Variablen Namenskonventionen.</span><span class="sxs-lookup"><span data-stu-id="9127c-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="9127c-115">Wenn das Ereignis nicht innerhalb des Moduls deklariert wurde, in dem es ausgelöst wird, tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="9127c-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="9127c-116">Das folgende Code Fragment veranschaulicht eine Ereignis Deklaration und eine Prozedur, in der das-Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="9127c-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 <span data-ttu-id="9127c-117">Sie können nicht verwenden `RaiseEvent` , um Ereignisse, die nicht explizit im Modul deklariert sind, zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="9127c-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="9127c-118">Beispielsweise erben alle Formulare ein- <xref:System.Windows.Forms.Control.Click> Ereignis von <xref:System.Windows.Forms.Form?displayProperty=nameWithType> , es kann nicht mithilfe von `RaiseEvent` in einem abgeleiteten Formular ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="9127c-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="9127c-119">Wenn Sie ein `Click` -Ereignis im Form-Modul deklarieren, wird das eigene Ereignis des Formulars überschattet <xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="9127c-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="9127c-120">Sie können das-Ereignis des Formulars weiterhin aufrufen, <xref:System.Windows.Forms.Control.Click> indem Sie die- <xref:System.Windows.Forms.Control.OnClick%2A> Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="9127c-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="9127c-121">Standardmäßig löst ein Ereignis, das in Visual Basic definiert ist, seine Ereignishandler in der Reihenfolge aus, in der die Verbindungen hergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="9127c-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="9127c-122">Da Ereignisse über Parameter verfügen können `ByRef` , empfängt ein Prozess, der spät eine Verbindung herstellt, möglicherweise Parameter, die von einem früheren Ereignishandler geändert wurden.</span><span class="sxs-lookup"><span data-stu-id="9127c-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="9127c-123">Nachdem die Ereignishandler ausgeführt wurden, wird die Steuerung an die Unterroutine zurückgegeben, die das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="9127c-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9127c-124">Nicht freigegebene Ereignisse sollten nicht innerhalb des Konstruktors der Klasse ausgelöst werden, in der Sie deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="9127c-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="9127c-125">Obwohl solche Ereignisse keine Laufzeitfehler verursachen, werden Sie möglicherweise von zugeordneten Ereignis Handlern nicht abgefangen.</span><span class="sxs-lookup"><span data-stu-id="9127c-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="9127c-126">Verwenden Sie den- `Shared` Modifizierer, um ein frei gegebenes Ereignis zu erstellen, wenn Sie ein Ereignis aus einem Konstruktor erstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="9127c-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9127c-127">Sie können das Standardverhalten von Ereignissen ändern, indem Sie ein benutzerdefiniertes Ereignis definieren.</span><span class="sxs-lookup"><span data-stu-id="9127c-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="9127c-128">Für benutzerdefinierte Ereignisse `RaiseEvent` Ruft die-Anweisung den- `RaiseEvent` Accessor des Ereignisses auf.</span><span class="sxs-lookup"><span data-stu-id="9127c-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="9127c-129">Weitere Informationen zu benutzerdefinierten Ereignissen finden Sie unter [Event-Anweisung](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9127c-129">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9127c-130">Beispiel</span><span class="sxs-lookup"><span data-stu-id="9127c-130">Example</span></span>  

 <span data-ttu-id="9127c-131">Im folgenden Beispiel werden Ereignisse zum Herunterzählen der Sekunden von 10 bis 0 verwendet.</span><span class="sxs-lookup"><span data-stu-id="9127c-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="9127c-132">Der Code veranschaulicht einige der ereignisbezogenen Methoden, Eigenschaften und Anweisungen, einschließlich der- `RaiseEvent` Anweisung.</span><span class="sxs-lookup"><span data-stu-id="9127c-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="9127c-133">Die Klasse, die ein Ereignis auslöst, ist die Ereignisquelle, und die Methoden, die das Ereignis verarbeiten, sind die Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="9127c-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="9127c-134">Eine Ereignisquelle kann über mehrere Handler für die Ereignisse verfügen, die sie generiert.</span><span class="sxs-lookup"><span data-stu-id="9127c-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="9127c-135">Wenn die Klasse das Ereignis auslöst, wird dieses Ereignis in jeder Klasse ausgelöst, die das Verarbeiten von Ereignissen für diese Instanz des Objekts ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="9127c-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="9127c-136">Im Beispiel wird außerdem ein Formular (`Form1`) mit einer Schaltfläche (`Button1`) und einem Textfeld (`TextBox1`) verwendet.</span><span class="sxs-lookup"><span data-stu-id="9127c-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="9127c-137">Wenn Sie auf die Schaltfläche klicken, zeigt das erste Textfeld einen Countdown von 10 bis 0 Sekunden an.</span><span class="sxs-lookup"><span data-stu-id="9127c-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="9127c-138">Nach Ablauf der vollständigen Zeitspanne (10 Sekunden) wird im ersten Textfeld „Fertig“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9127c-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="9127c-139">Der Code für `Form1` gibt die Anfangs- und Beendigungsstatus des Formulars an.</span><span class="sxs-lookup"><span data-stu-id="9127c-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="9127c-140">Er enthält zudem den Code, der ausgeführt wird, wenn Ereignisse ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="9127c-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="9127c-141">Um dieses Beispiel zu verwenden, öffnen Sie ein neues Windows-Anwendungsprojekt, fügen Sie `Button1` `TextBox1` dem Hauptformular mit dem Namen eine Schaltfläche mit dem Namen und ein Textfeld mit dem Namen hinzu `Form1` .</span><span class="sxs-lookup"><span data-stu-id="9127c-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="9127c-142">Klicken Sie dann mit der rechten Maustaste auf das Formular und dann auf **Code anzeigen** , um den Code-Editor zu öffnen</span><span class="sxs-lookup"><span data-stu-id="9127c-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="9127c-143">Fügen Sie `WithEvents` dem Deklarations Abschnitt der-Klasse eine Variable hinzu `Form1` .</span><span class="sxs-lookup"><span data-stu-id="9127c-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="9127c-144">Beispiel</span><span class="sxs-lookup"><span data-stu-id="9127c-144">Example</span></span>  

 <span data-ttu-id="9127c-145">Fügen Sie den folgenden Code zum Code für `Form1` hinzu.</span><span class="sxs-lookup"><span data-stu-id="9127c-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="9127c-146">Ersetzen Sie alle möglicherweise vorhandenen doppelten Prozeduren, z `Form_Load` `Button_Click` . b. oder.</span><span class="sxs-lookup"><span data-stu-id="9127c-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 <span data-ttu-id="9127c-147">Drücken Sie F5, um das vorherige Beispiel auszuführen, und klicken Sie auf die Schaltfläche **Start**.</span><span class="sxs-lookup"><span data-stu-id="9127c-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="9127c-148">Im ersten Textfeld werden die Sekunden heruntergezählt.</span><span class="sxs-lookup"><span data-stu-id="9127c-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="9127c-149">Nach Ablauf der vollständigen Zeitspanne (10 Sekunden) wird im ersten Textfeld „Fertig“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9127c-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9127c-150">Die- `My.Application.DoEvents` Methode verarbeitet Ereignisse nicht exakt auf die gleiche Weise wie das Formular.</span><span class="sxs-lookup"><span data-stu-id="9127c-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="9127c-151">Um dem Formular das direkte behandeln der Ereignisse zu ermöglichen, können Sie Multithreading verwenden.</span><span class="sxs-lookup"><span data-stu-id="9127c-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="9127c-152">Weitere Informationen finden Sie unter [verwaltetes Threading](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="9127c-152">For more information, see [Managed Threading](../../../standard/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9127c-153">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9127c-153">See also</span></span>

- [<span data-ttu-id="9127c-154">Ereignisse</span><span class="sxs-lookup"><span data-stu-id="9127c-154">Events</span></span>](../../programming-guide/language-features/events/index.md)
- [<span data-ttu-id="9127c-155">Event-Anweisung</span><span class="sxs-lookup"><span data-stu-id="9127c-155">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="9127c-156">AddHandler-Anweisung</span><span class="sxs-lookup"><span data-stu-id="9127c-156">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="9127c-157">RemoveHandler-Anweisung</span><span class="sxs-lookup"><span data-stu-id="9127c-157">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="9127c-158">Ziehpunkte</span><span class="sxs-lookup"><span data-stu-id="9127c-158">Handles</span></span>](handles-clause.md)
