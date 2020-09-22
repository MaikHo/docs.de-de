---
title: SyncLock-Anweisung
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: cc8706b95e0785459e36abe27ce915b5bab8711a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875199"
---
# <a name="synclock-statement"></a><span data-ttu-id="018d3-102">SyncLock-Anweisung</span><span class="sxs-lookup"><span data-stu-id="018d3-102">SyncLock Statement</span></span>

<span data-ttu-id="018d3-103">Erhält eine exklusive Sperre für einen Anweisungsblock, bevor der-Block ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="018d3-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="018d3-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="018d3-104">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="018d3-105">Bestandteile</span><span class="sxs-lookup"><span data-stu-id="018d3-105">Parts</span></span>  

 `lockobject`  
 <span data-ttu-id="018d3-106">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="018d3-106">Required.</span></span> <span data-ttu-id="018d3-107">Ausdruck, der zu einem Objekt Verweis ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="018d3-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="018d3-108">Dies ist optional.</span><span class="sxs-lookup"><span data-stu-id="018d3-108">Optional.</span></span> <span data-ttu-id="018d3-109">Ein Block von-Anweisungen, die ausgeführt werden sollen, wenn die Sperre abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="018d3-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="018d3-110">Beendet einen- `SyncLock` Block.</span><span class="sxs-lookup"><span data-stu-id="018d3-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="018d3-111">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="018d3-111">Remarks</span></span>  

 <span data-ttu-id="018d3-112">Die- `SyncLock` Anweisung stellt sicher, dass der Anweisungsblock nicht gleichzeitig von mehreren Threads ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="018d3-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="018d3-113">`SyncLock` verhindert, dass jeder Thread den Block eingibt, bis er von keinem anderen Thread ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="018d3-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="018d3-114">Die häufigste Verwendung von `SyncLock` besteht darin, Daten vor der gleichzeitigen Aktualisierung durch mehr als einen Thread zu schützen.</span><span class="sxs-lookup"><span data-stu-id="018d3-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="018d3-115">Wenn die Anweisungen, die die Daten bearbeiten, ohne Unterbrechung in den Abschluss gehen müssen, platzieren Sie Sie in einem- `SyncLock` Block.</span><span class="sxs-lookup"><span data-stu-id="018d3-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="018d3-116">Ein Anweisungsblock, der durch eine exklusive Sperre geschützt ist, wird manchmal als *kritischer Abschnitt*bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="018d3-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="018d3-117">Regeln</span><span class="sxs-lookup"><span data-stu-id="018d3-117">Rules</span></span>  
  
- <span data-ttu-id="018d3-118">Verzweigung.</span><span class="sxs-lookup"><span data-stu-id="018d3-118">Branching.</span></span> <span data-ttu-id="018d3-119">Sie können nicht von außerhalb des-Blocks in einen-Block verzweigen `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="018d3-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="018d3-120">Objektwert sperren.</span><span class="sxs-lookup"><span data-stu-id="018d3-120">Lock Object Value.</span></span> <span data-ttu-id="018d3-121">Der Wert von `lockobject` darf nicht sein `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="018d3-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="018d3-122">Sie müssen das Lock-Objekt erstellen, bevor Sie es in einer- `SyncLock` Anweisung verwenden.</span><span class="sxs-lookup"><span data-stu-id="018d3-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="018d3-123">Der Wert von kann `lockobject` beim Ausführen eines-Blocks nicht geändert werden `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="018d3-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="018d3-124">Der Mechanismus erfordert, dass das Sperr Objekt unverändert bleibt.</span><span class="sxs-lookup"><span data-stu-id="018d3-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="018d3-125">Sie [können den Erwartungs](../operators/await-operator.md) Operator nicht in einem- `SyncLock` Block verwenden.</span><span class="sxs-lookup"><span data-stu-id="018d3-125">You can't use the [Await](../operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="018d3-126">Verhalten</span><span class="sxs-lookup"><span data-stu-id="018d3-126">Behavior</span></span>  
  
- <span data-ttu-id="018d3-127">Verfahren.</span><span class="sxs-lookup"><span data-stu-id="018d3-127">Mechanism.</span></span> <span data-ttu-id="018d3-128">Wenn ein Thread die- `SyncLock` Anweisung erreicht, wertet er den Ausdruck aus und hält die `lockobject` Ausführung an, bis er eine exklusive Sperre für das Objekt erhält, das vom Ausdruck zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="018d3-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="018d3-129">Wenn ein anderer Thread die- `SyncLock` Anweisung erreicht, erhält er erst dann eine Sperre, wenn der erste Thread die- `End SyncLock` Anweisung ausführt.</span><span class="sxs-lookup"><span data-stu-id="018d3-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="018d3-130">Geschützte Daten.</span><span class="sxs-lookup"><span data-stu-id="018d3-130">Protected Data.</span></span> <span data-ttu-id="018d3-131">Wenn `lockobject` eine `Shared` Variable ist, verhindert die exklusive Sperre, dass ein Thread in einer Instanz der Klasse den Block ausführt, `SyncLock` während er von einem anderen Thread ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="018d3-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="018d3-132">Dies schützt Daten, die von allen Instanzen gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="018d3-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="018d3-133">Wenn `lockobject` eine Instanzvariable (nicht `Shared` ) ist, verhindert die Sperre, dass ein Thread, der in der aktuellen Instanz ausgeführt wird, den `SyncLock` Block gleichzeitig mit einem anderen Thread in derselben Instanz ausführt.</span><span class="sxs-lookup"><span data-stu-id="018d3-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="018d3-134">Dadurch werden die Daten geschützt, die von der einzelnen Instanz verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="018d3-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="018d3-135">Erwerb und Release.</span><span class="sxs-lookup"><span data-stu-id="018d3-135">Acquisition and Release.</span></span> <span data-ttu-id="018d3-136">Ein- `SyncLock` Block verhält sich wie eine `Try...Finally` Konstruktion, bei der der `Try` -Block eine exklusive Sperre für abruft `lockobject` und der-Block `Finally` Sie freigibt.</span><span class="sxs-lookup"><span data-stu-id="018d3-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="018d3-137">Aus diesem Grund garantiert der- `SyncLock` Block die Freigabe der Sperre, unabhängig davon, wie Sie den Block beenden.</span><span class="sxs-lookup"><span data-stu-id="018d3-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="018d3-138">Dies gilt auch im Fall einer nicht behandelten Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="018d3-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="018d3-139">Framework-Aufrufe.</span><span class="sxs-lookup"><span data-stu-id="018d3-139">Framework Calls.</span></span> <span data-ttu-id="018d3-140">Der `SyncLock` -Block Ruft die exklusive Sperre ab und gibt Sie frei, indem Sie die `Enter` -und- `Exit` Methoden der- `Monitor` Klasse im- <xref:System.Threading> Namespace aufrufen.</span><span class="sxs-lookup"><span data-stu-id="018d3-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="018d3-141">Programmierverfahren</span><span class="sxs-lookup"><span data-stu-id="018d3-141">Programming Practices</span></span>  

 <span data-ttu-id="018d3-142">Der `lockobject` Ausdruck sollte immer zu einem Objekt ausgewertet werden, das exklusiv zu ihrer Klasse gehört.</span><span class="sxs-lookup"><span data-stu-id="018d3-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="018d3-143">Sie sollten eine- `Private` Objekt Variable deklarieren, um Daten zu schützen, die zur aktuellen Instanz gehören, oder eine- `Private Shared` Objekt Variable, um die Daten zu schützen, die für alle Instanzen</span><span class="sxs-lookup"><span data-stu-id="018d3-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="018d3-144">Sie sollten das- `Me` Schlüsselwort nicht verwenden, um ein Sperr Objekt für Instanzdaten bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="018d3-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="018d3-145">Wenn der Code, der sich außerhalb ihrer Klasse befindet, einen Verweis auf eine Instanz der Klasse aufweist, könnte dieser Verweis als Sperr Objekt für einen `SyncLock` Block verwendet werden, der sich vollständig von Ihnen unterscheidet und verschiedene Daten schützt.</span><span class="sxs-lookup"><span data-stu-id="018d3-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="018d3-146">Auf diese Weise können Ihre Klasse und die andere Klasse verhindern, dass Sie Ihre nicht verbundenen `SyncLock` Blöcke ausführen.</span><span class="sxs-lookup"><span data-stu-id="018d3-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="018d3-147">Ähnliches Sperren für eine Zeichenfolge können problematisch sein, da jeder andere Code im Prozess, der dieselbe Zeichenfolge verwendet, dieselbe Sperre gemeinsam verwendet.</span><span class="sxs-lookup"><span data-stu-id="018d3-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="018d3-148">Sie sollten auch die-Methode nicht verwenden `Me.GetType` , um ein Sperr Objekt für freigegebene Daten bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="018d3-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="018d3-149">Dies liegt daran, dass `GetType` `Type` für einen angegebenen Klassennamen immer das gleiche Objekt zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="018d3-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="018d3-150">Externer Code könnte `GetType` für Ihre Klasse aufzurufen und das gleiche Sperr Objekt erhalten, das Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="018d3-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="018d3-151">Dies würde dazu führen, dass die beiden Klassen Ihre Blöcke gegenseitig blockieren `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="018d3-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="018d3-152">Beispiele</span><span class="sxs-lookup"><span data-stu-id="018d3-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="018d3-153">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="018d3-153">Description</span></span>  

 <span data-ttu-id="018d3-154">Das folgende Beispiel zeigt eine Klasse, die eine einfache Liste von Nachrichten verwaltet.</span><span class="sxs-lookup"><span data-stu-id="018d3-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="018d3-155">Sie enthält die Nachrichten in einem Array und das zuletzt verwendete Element dieses Arrays in einer Variablen.</span><span class="sxs-lookup"><span data-stu-id="018d3-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="018d3-156">Die `addAnotherMessage` Prozedur erhöht das letzte Element und speichert die neue Nachricht.</span><span class="sxs-lookup"><span data-stu-id="018d3-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="018d3-157">Diese beiden Vorgänge werden durch die `SyncLock` -und- `End SyncLock` Anweisungen geschützt, denn sobald das letzte Element inkrementiert wurde, muss die neue Nachricht gespeichert werden, bevor ein anderer Thread das letzte Element erneut erhöhen kann.</span><span class="sxs-lookup"><span data-stu-id="018d3-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="018d3-158">Wenn die `simpleMessageList` Klasse eine Liste von Nachrichten für alle Instanzen freigegeben hat, `messagesList` werden die Variablen und `messagesLast` als deklariert `Shared` .</span><span class="sxs-lookup"><span data-stu-id="018d3-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="018d3-159">In diesem Fall sollte die Variable `messagesLock` auch sein `Shared` , sodass es ein einzelnes Sperr Objekt gibt, das von jeder Instanz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="018d3-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="018d3-160">Code</span><span class="sxs-lookup"><span data-stu-id="018d3-160">Code</span></span>  

 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="018d3-161">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="018d3-161">Description</span></span>  

 <span data-ttu-id="018d3-162">Im folgenden Beispiel werden Threads und verwendet `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="018d3-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="018d3-163">Solange die- `SyncLock` Anweisung vorhanden ist, ist der Anweisungsblock ein kritischer Abschnitt und `balance` wird nie eine negative Zahl sein.</span><span class="sxs-lookup"><span data-stu-id="018d3-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="018d3-164">Sie können die `SyncLock` -Anweisung und die-Anweisung auskommentieren `End SyncLock` , um die Auswirkung des auslassen des `SyncLock` Schlüssel Worts anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="018d3-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="018d3-165">Code</span><span class="sxs-lookup"><span data-stu-id="018d3-165">Code</span></span>  

 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="018d3-166">Kommentare</span><span class="sxs-lookup"><span data-stu-id="018d3-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="018d3-167">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="018d3-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="018d3-168">Übersicht über Synchronisierungsprimitiven</span><span class="sxs-lookup"><span data-stu-id="018d3-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
