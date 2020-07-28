---
title: Schwache Ereignismuster
description: Erfahren Sie mehr über das Windows Presentation Foundation schwache Ereignis Muster, das das Problem von Handlern behandelt, die nicht zerstört werden, und damit Speicher Verluste vermeiden.
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 75c6888c8ac20c41d13e3787005377c75248c5d9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168263"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="f1d5e-103">Schwache Ereignismuster</span><span class="sxs-lookup"><span data-stu-id="f1d5e-103">Weak Event Patterns</span></span>
<span data-ttu-id="f1d5e-104">In-Anwendungen ist es möglich, dass an Ereignis Quellen angefügte Handler nicht in Abstimmung mit dem Listenerobjekt zerstört werden, das den Handler an die Quelle angefügt hat.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-104">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="f1d5e-105">Diese Situation kann zu Speicher Verlusten führen.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-105">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="f1d5e-106">führt ein Entwurfsmuster ein, das verwendet werden kann, um dieses Problem zu beheben, indem eine dedizierte Manager-Klasse für bestimmte Ereignisse bereitgestellt und eine Schnittstelle für Listener für dieses Ereignis implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-106">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="f1d5e-107">Dieses Entwurfsmuster wird als *schwaches Ereignis Muster*bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-107">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="f1d5e-108">Gründe für die Implementierung des schwachen Ereignis Musters</span><span class="sxs-lookup"><span data-stu-id="f1d5e-108">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="f1d5e-109">Das Lauschen auf Ereignisse kann zu Speicher Verlusten führen.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-109">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="f1d5e-110">Die typische Vorgehensweise zum lauschen auf ein Ereignis besteht darin, die sprachspezifische Syntax zu verwenden, die einen Handler an ein Ereignis in einer Quelle anfügt.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-110">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="f1d5e-111">In c# lautet die Syntax z. b.: `source.SomeEvent += new SomeEventHandler(MyEventHandler)` .</span><span class="sxs-lookup"><span data-stu-id="f1d5e-111">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="f1d5e-112">Diese Technik erstellt einen starken Verweis von der Ereignis Quelle auf den Ereignislistener.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-112">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="f1d5e-113">Normalerweise bewirkt das Anfügen eines Ereignis Handlers für einen Listener, dass der Listener eine Objekt Lebensdauer hat, die von der Objekt Lebensdauer der Quelle beeinflusst wird (es sei denn, der Ereignishandler wird explizit entfernt).</span><span class="sxs-lookup"><span data-stu-id="f1d5e-113">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="f1d5e-114">Unter bestimmten Umständen möchten Sie jedoch möglicherweise, dass die Objekt Lebensdauer des Listener von anderen Faktoren gesteuert wird, z. b. ob er derzeit zur visuellen Struktur der Anwendung gehört, und nicht nach der Lebensdauer der Quelle.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-114">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="f1d5e-115">Wenn die Lebensdauer des Quell Objekts über die Objekt Lebensdauer des Listener hinausgeht, führt das normale Ereignis Muster zu einem Speicherleck: der Listener bleibt länger als beabsichtigt.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-115">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="f1d5e-116">Das schwache Ereignis Muster ist so konzipiert, dass dieses Speicherlecks-Problem gelöst wird.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-116">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="f1d5e-117">Das schwache Ereignis Muster kann immer dann verwendet werden, wenn ein Listener für ein Ereignis registriert werden muss, aber der Listener weiß nicht explizit, wann die Registrierung aufgehoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-117">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="f1d5e-118">Das schwache Ereignis Muster kann auch verwendet werden, wenn die Objekt Lebensdauer der Quelle die nützliche Objekt Lebensdauer des Listener überschreitet.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-118">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="f1d5e-119">(In diesem Fall wird *nützlich* von Ihnen bestimmt.) Das schwache Ereignis Muster ermöglicht dem Listener, sich für das Ereignis zu registrieren und das Ereignis zu empfangen, ohne die Eigenschaften der Objekt Lebensdauer in irgendeiner Weise zu beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-119">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="f1d5e-120">Tatsächlich bestimmt der implizierte Verweis aus der Quelle nicht, ob der Listener für Garbage Collection geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-120">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="f1d5e-121">Der Verweis ist eine schwache Referenz und somit die Benennung des schwachen Ereignis Musters und der zugehörigen APIs.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-121">The reference is a weak reference, thus the naming of the weak event pattern and the related APIs.</span></span> <span data-ttu-id="f1d5e-122">Der Listener kann auf eine Garbage Collection oder anderweitig zerstört werden, und die Quelle kann fortgesetzt werden, ohne dass nicht entladbare Handlerverweise auf ein jetzt zerstörtes Objekt beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-122">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="f1d5e-123">Wer sollte das schwache Ereignis Muster implementieren?</span><span class="sxs-lookup"><span data-stu-id="f1d5e-123">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="f1d5e-124">Die Implementierung des schwachen Ereignis Musters ist hauptsächlich für Autoren von Steuerelementen interessant.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-124">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="f1d5e-125">Als Autor eines Steuer Elements sind Sie größtenteils verantwortlich für das Verhalten und die Kapselung Ihres Steuer Elements und die Auswirkungen, die es auf Anwendungen hat, in die es eingefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-125">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="f1d5e-126">Dies schließt das Verhalten der Steuerungsobjekt Lebensdauer ein, insbesondere die Behandlung des beschriebenen Speicherlecks Problems.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-126">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="f1d5e-127">Bestimmte Szenarien sind von Natur aus für die Anwendung des schwachen Ereignis Musters geeignet.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-127">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="f1d5e-128">Ein solches Szenario ist die Datenbindung.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-128">One such scenario is data binding.</span></span> <span data-ttu-id="f1d5e-129">Bei der Datenbindung ist es üblich, dass das Quell Objekt vollständig unabhängig vom Listenerobjekt ist, das das Ziel einer Bindung ist.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-129">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="f1d5e-130">Viele Aspekte der [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Datenbindung verfügen bereits über das schwache Ereignis Muster, das in der Implementierung der Ereignisse angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-130">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="f1d5e-131">So implementieren Sie das schwache Ereignis Muster</span><span class="sxs-lookup"><span data-stu-id="f1d5e-131">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="f1d5e-132">Es gibt drei Möglichkeiten, ein schwaches Ereignis Muster zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-132">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="f1d5e-133">In der folgenden Tabelle werden die drei Ansätze aufgelistet und eine Anleitung für die Verwendung der einzelnen Methoden bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-133">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="f1d5e-134">Ansatz</span><span class="sxs-lookup"><span data-stu-id="f1d5e-134">Approach</span></span>|<span data-ttu-id="f1d5e-135">Zeitpunkt der Implementierung</span><span class="sxs-lookup"><span data-stu-id="f1d5e-135">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="f1d5e-136">Vorhandene schwache Ereignis-Manager-Klasse verwenden</span><span class="sxs-lookup"><span data-stu-id="f1d5e-136">Use an existing weak event manager class</span></span>|<span data-ttu-id="f1d5e-137">Wenn das Ereignis, das Sie abonnieren möchten, über ein entsprechendes Ereignis verfügt <xref:System.Windows.WeakEventManager> , verwenden Sie den vorhandenen schwachen Ereignis-Manager.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-137">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="f1d5e-138">Eine Liste der in WPF enthaltenen schwachen Ereignis-Manager finden Sie in der Vererbungs Hierarchie in der- <xref:System.Windows.WeakEventManager> Klasse.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-138">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="f1d5e-139">Da die enthaltenen schwachen Ereignis-Manager eingeschränkt sind, müssen Sie wahrscheinlich einen der anderen Ansätze auswählen.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-139">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="f1d5e-140">Verwenden einer generischen Weak EventManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f1d5e-140">Use a generic weak event manager class</span></span>|<span data-ttu-id="f1d5e-141">Verwenden Sie einen generischen <xref:System.Windows.WeakEventManager%602> , wenn eine vorhandene <xref:System.Windows.WeakEventManager> nicht verfügbar ist, Sie möchten eine einfache Implementierung durchführen und sich keine Gedanken um die Effizienz machen.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-141">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="f1d5e-142">Der generische <xref:System.Windows.WeakEventManager%602> ist weniger effizient als ein vorhandener oder benutzerdefinierter schwacher Ereignis-Manager.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-142">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="f1d5e-143">Die generische Klasse führt z. b. mehr Reflektion aus, um das Ereignis anhand des Ereignis namens zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-143">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="f1d5e-144">Außerdem ist der Code zum Registrieren des Ereignisses mithilfe der generischen-Methode <xref:System.Windows.WeakEventManager%602> ausführlicher als die Verwendung eines vorhandenen oder benutzerdefinierten <xref:System.Windows.WeakEventManager> .</span><span class="sxs-lookup"><span data-stu-id="f1d5e-144">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="f1d5e-145">Erstellen einer benutzerdefinierten Weak EventManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f1d5e-145">Create a custom weak event manager class</span></span>|<span data-ttu-id="f1d5e-146">Erstellen Sie eine benutzerdefinierte, <xref:System.Windows.WeakEventManager> Wenn eine vorhandene <xref:System.Windows.WeakEventManager> nicht verfügbar ist und Sie die beste Effizienz erzielen möchten.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-146">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="f1d5e-147">Die Verwendung eines benutzerdefinierten <xref:System.Windows.WeakEventManager> zum Abonnieren eines Ereignisses ist effizienter, aber Sie verursachen die Kosten für das Schreiben von mehr Code am Anfang.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-147">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="f1d5e-148">Verwenden eines schwachen Ereignis-Managers von Drittanbietern</span><span class="sxs-lookup"><span data-stu-id="f1d5e-148">Use a third-party weak event manager</span></span>|<span data-ttu-id="f1d5e-149">Nuget verfügt über [mehrere schwache Ereignis-Manager](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) , und viele WPF-Frameworks unterstützen auch das-Muster (z.b. [in der Prism-Dokumentation zu locker verknüpften Ereignis Abonnements](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="f1d5e-149">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="f1d5e-150">In den folgenden Abschnitten wird beschrieben, wie das schwache Ereignis Muster implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-150">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="f1d5e-151">Im Rahmen dieser Erläuterung weist das Ereignis, das abonniert werden soll, die folgenden Eigenschaften auf.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-151">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="f1d5e-152">Der Ereignis Name ist `SomeEvent` .</span><span class="sxs-lookup"><span data-stu-id="f1d5e-152">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="f1d5e-153">Das-Ereignis wird von der- `EventSource` Klasse ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-153">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="f1d5e-154">Der Ereignishandler weist den Typ auf: `SomeEventEventHandler` (oder `EventHandler<SomeEventEventArgs>` ).</span><span class="sxs-lookup"><span data-stu-id="f1d5e-154">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="f1d5e-155">Das-Ereignis übergibt einen Parameter vom Typ `SomeEventEventArgs` an die Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-155">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="f1d5e-156">Verwenden einer vorhandenen Weak Event Manager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f1d5e-156">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="f1d5e-157">Suchen Sie einen vorhandenen schwachen Ereignis-Manager.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-157">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="f1d5e-158">Eine Liste der in WPF enthaltenen schwachen Ereignis-Manager finden Sie in der Vererbungs Hierarchie in der- <xref:System.Windows.WeakEventManager> Klasse.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-158">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="f1d5e-159">Verwenden Sie den neuen schwachen Ereignis-Manager anstelle der normalen Ereignis Einbindung.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-159">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="f1d5e-160">Wenn Ihr Code z. b. das folgende Muster verwendet, um ein Ereignis zu abonnieren:</span><span class="sxs-lookup"><span data-stu-id="f1d5e-160">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="f1d5e-161">Ändern Sie den Wert in das folgende Muster:</span><span class="sxs-lookup"><span data-stu-id="f1d5e-161">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="f1d5e-162">Ebenso, wenn Ihr Code das folgende Muster verwendet, um ein Ereignis abzubestellen:</span><span class="sxs-lookup"><span data-stu-id="f1d5e-162">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="f1d5e-163">Ändern Sie den Wert in das folgende Muster:</span><span class="sxs-lookup"><span data-stu-id="f1d5e-163">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="f1d5e-164">Verwenden der generischen Weak Event Manager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f1d5e-164">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="f1d5e-165">Verwenden Sie die generische- <xref:System.Windows.WeakEventManager%602> Klasse anstelle der normalen Ereignis Einbindung.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-165">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="f1d5e-166">Wenn Sie <xref:System.Windows.WeakEventManager%602> zum Registrieren von Ereignislistenern verwenden, geben Sie die Ereignis Quelle und den Typ <xref:System.EventArgs> als Typparameter für die Klasse an, und geben Sie an, <xref:System.Windows.WeakEventManager%602.AddHandler%2A> wie im folgenden Code gezeigt:</span><span class="sxs-lookup"><span data-stu-id="f1d5e-166">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="f1d5e-167">Erstellen einer benutzerdefinierten Weak Event Manager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f1d5e-167">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="f1d5e-168">Kopieren Sie die folgende Klassen Vorlage in Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-168">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="f1d5e-169">Diese Klasse erbt von der- <xref:System.Windows.WeakEventManager> Klasse.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-169">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="f1d5e-170">Ersetzen `SomeEventWeakEventManager` Sie den Namen durch ihren eigenen Namen.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-170">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="f1d5e-171">Ersetzen Sie die drei zuvor beschriebenen Namen durch die entsprechenden Namen für das Ereignis.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-171">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="f1d5e-172">( `SomeEvent` , `EventSource` und `SomeEventEventArgs` )</span><span class="sxs-lookup"><span data-stu-id="f1d5e-172">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="f1d5e-173">Legen Sie die Sichtbarkeit (Public/Internal/private) der Weak EventManager-Klasse auf die gleiche Sichtbarkeit wie das Ereignis fest, das Sie verwaltet.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-173">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="f1d5e-174">Verwenden Sie den neuen schwachen Ereignis-Manager anstelle der normalen Ereignis Einbindung.</span><span class="sxs-lookup"><span data-stu-id="f1d5e-174">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="f1d5e-175">Wenn Ihr Code z. b. das folgende Muster verwendet, um ein Ereignis zu abonnieren:</span><span class="sxs-lookup"><span data-stu-id="f1d5e-175">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="f1d5e-176">Ändern Sie den Wert in das folgende Muster:</span><span class="sxs-lookup"><span data-stu-id="f1d5e-176">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="f1d5e-177">Ebenso, wenn Ihr Code das folgende Muster verwendet, um ein Ereignis abzubestellen:</span><span class="sxs-lookup"><span data-stu-id="f1d5e-177">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="f1d5e-178">Ändern Sie den Wert in das folgende Muster:</span><span class="sxs-lookup"><span data-stu-id="f1d5e-178">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f1d5e-179">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f1d5e-179">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="f1d5e-180">Übersicht über Routingereignisse</span><span class="sxs-lookup"><span data-stu-id="f1d5e-180">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="f1d5e-181">Übersicht über die Datenbindung</span><span class="sxs-lookup"><span data-stu-id="f1d5e-181">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
