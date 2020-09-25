---
title: Verwalten von Parallelität mit DependentTransaction
description: Verwalten Sie Transaktions Parallelität, einschließlich asynchroner Aufgaben, mithilfe der DependentTransaction-Klasse in .net.
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: 1e99006c127d83892155bd81e683f5995ac517ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186743"
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="02c2b-103">Verwalten von Parallelität mit DependentTransaction</span><span class="sxs-lookup"><span data-stu-id="02c2b-103">Managing Concurrency with DependentTransaction</span></span>

<span data-ttu-id="02c2b-104">Das <xref:System.Transactions.Transaction>-Objekt wird mit der <xref:System.Transactions.Transaction.DependentClone%2A>-Methode erstellt.</span><span class="sxs-lookup"><span data-stu-id="02c2b-104">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="02c2b-105">Sein einziger Zweck besteht darin, sicherzustellen, dass die Transaktion keinen Commit durchführen kann, während andere Codeteile (beispielsweise ein Arbeitsthread) noch Aktionen für die Transaktion ausführen.</span><span class="sxs-lookup"><span data-stu-id="02c2b-105">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="02c2b-106">Wenn die Aktionen innerhalb der geklonten Transaktion abgeschlossen und für den Commit bereit sind, kann es den Ersteller der Transaktion mithilfe der <xref:System.Transactions.DependentTransaction.Complete%2A>-Methode informieren.</span><span class="sxs-lookup"><span data-stu-id="02c2b-106">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="02c2b-107">Auf diese Weise können Sie Konsistenz und Richtigkeit der Daten bewahren.</span><span class="sxs-lookup"><span data-stu-id="02c2b-107">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="02c2b-108">Die <xref:System.Transactions.DependentTransaction>-Klasse kann ebenfalls verwendet werden, um Parallelität zwischen asynchronen Aufgaben zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="02c2b-108">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="02c2b-109">Bei diesem Szenario kann das übergeordnete Element weiter Code ausführen, während der abhängige Klon seine eigenen Aufgaben ausführt.</span><span class="sxs-lookup"><span data-stu-id="02c2b-109">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="02c2b-110">Anders ausgedrückt wird die Ausführung des übergeordneten Elements nicht blockiert, solange die Ausführung des abhängigen Elements nicht abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="02c2b-110">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="02c2b-111">Erstellen eines abhängigen Klons</span><span class="sxs-lookup"><span data-stu-id="02c2b-111">Creating a Dependent Clone</span></span>  

 <span data-ttu-id="02c2b-112">Um eine abhängige Transaktion zu erstellen, rufen Sie die <xref:System.Transactions.Transaction.DependentClone%2A>-Methode auf, und übergeben Sie die <xref:System.Transactions.DependentCloneOption>-Enumeration als Parameter.</span><span class="sxs-lookup"><span data-stu-id="02c2b-112">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="02c2b-113">Dieser Parameter definiert das Verhalten der Transaktion, wenn `Commit` für die übergeordnete Transaktion aufgerufen wird, bevor der abhängige Klon anzeigt, dass er für den Transaktionscommit bereit ist (durch Aufrufen der <xref:System.Transactions.DependentTransaction.Complete%2A>-Methode).</span><span class="sxs-lookup"><span data-stu-id="02c2b-113">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="02c2b-114">Die folgenden Werte sind für diesen Parameter gültig:</span><span class="sxs-lookup"><span data-stu-id="02c2b-114">The following values are valid for this parameter:</span></span>  
  
- <span data-ttu-id="02c2b-115"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> erstellt eine abhängige Transaktion, die den Commitprozess der übergeordneten Transaktion blockiert, bis das Timeout für die übergeordnete Transaktion auftritt oder bis <xref:System.Transactions.DependentTransaction.Complete%2A> für alle abhängigen Elemente aufgerufen wird, die ihren Abschluss angeben.</span><span class="sxs-lookup"><span data-stu-id="02c2b-115"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="02c2b-116">Das ist nützlich, wenn der Client den Commit der übergeordneten Transaktion erst zulassen will, wenn die abhängigen Transaktionen abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="02c2b-116">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="02c2b-117">Wenn die übergeordnete Transaktion ihre Aufgaben früher abschließt als die abhängige Transaktion und <xref:System.Transactions.CommittableTransaction.Commit%2A> für die Transaktion aufruft, wird der Commitprozess in einem Zustand blockiert, in dem weitere Aufgaben für die Transaktion ausgeführt und neue Eintragungen vorgenommen werden können, bis alle abhängigen Transaktionen <xref:System.Transactions.DependentTransaction.Complete%2A> aufrufen.</span><span class="sxs-lookup"><span data-stu-id="02c2b-117">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="02c2b-118">Sobald alle ihre Aufgaben abgeschlossen und <xref:System.Transactions.DependentTransaction.Complete%2A> aufgerufen haben, beginnt der Commitprozess für die Transaktion.</span><span class="sxs-lookup"><span data-stu-id="02c2b-118">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
- <span data-ttu-id="02c2b-119"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete> hingegen erstellt eine abhängige Transaktion, die automatisch abgebrochen wird, wenn <xref:System.Transactions.CommittableTransaction.Commit%2A> für die übergeordnete Transaktion aufgerufen wird, bevor <xref:System.Transactions.DependentTransaction.Complete%2A> aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="02c2b-119"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="02c2b-120">In diesem Fall bleiben alle für die abhängige Transaktion ausgeführten Aktionen innerhalb einer Transaktionslebensdauer intakt. Es ist nicht möglich, einen Commit nur für einen Teil davon auszuführen.</span><span class="sxs-lookup"><span data-stu-id="02c2b-120">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="02c2b-121">Die <xref:System.Transactions.DependentTransaction.Complete%2A>-Methode darf nur einmal aufgerufen werden, wenn die Anwendung ihre Aufgaben für die abhängige Transaktion beendet hat; anderenfalls wird eine <xref:System.InvalidOperationException>-Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="02c2b-121">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="02c2b-122">Führen Sie nach diesem Aufruf keine weiteren Aktionen für die Transaktion aus. Andernfalls wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="02c2b-122">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="02c2b-123">Das folgende Codebeispiel zeigt, wie eine abhängige Transaktion mit dem Ziel erstellt wird, zwei parallele Aufgaben durch Klonen einer abhängigen Transaktion und Übergabe der Transaktion an einen Arbeitsthread zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="02c2b-123">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
```csharp  
public class WorkerThread  
{  
    public void DoWork(DependentTransaction dependentTransaction)  
    {  
        Thread thread = new Thread(ThreadMethod);  
        thread.Start(dependentTransaction);
    }  
  
    public void ThreadMethod(object transaction)
    {
        DependentTransaction dependentTransaction = transaction as DependentTransaction;  
        Debug.Assert(dependentTransaction != null);
        try  
        {  
            using(TransactionScope ts = new TransactionScope(dependentTransaction))  
            {  
                /* Perform transactional work here */
                ts.Complete();  
            }  
        }  
        finally  
        {  
            dependentTransaction.Complete();
             dependentTransaction.Dispose();
        }  
    }  
  
//Client code
using(TransactionScope scope = new TransactionScope())  
{  
    Transaction currentTransaction = Transaction.Current;  
    DependentTransaction dependentTransaction;
    dependentTransaction = currentTransaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
    WorkerThread workerThread = new WorkerThread();  
    workerThread.DoWork(dependentTransaction);  
    /* Do some transactional work here, then: */  
    scope.Complete();  
}  
```  
  
 <span data-ttu-id="02c2b-124">Der Clientcode erstellt einen Transaktionsbereich, der auch die Ambient-Transaktion festlegt.</span><span class="sxs-lookup"><span data-stu-id="02c2b-124">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="02c2b-125">Sie sollten die Ambient-Transaktion nicht an den Arbeitsthread übergeben.</span><span class="sxs-lookup"><span data-stu-id="02c2b-125">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="02c2b-126">Stattdessen sollten Sie die aktuelle (Ambient-)Transaktion klonen, indem Sie die <xref:System.Transactions.Transaction.DependentClone%2A>-Methode für die aktuelle Transaktion aufrufen und die abhängige an den Arbeitsthread übergeben.</span><span class="sxs-lookup"><span data-stu-id="02c2b-126">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="02c2b-127">Die `ThreadMethod`-Methode wird für den neuen Thread ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="02c2b-127">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="02c2b-128">Der Client startet einen neuen Thread und übergibt die abhängige Transaktion als `ThreadMethod`-Parameter.</span><span class="sxs-lookup"><span data-stu-id="02c2b-128">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="02c2b-129">Da die abhängige Transaktion mit <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> erstellt wird, haben Sie die Gewissheit, dass der Transaktionscommit nicht ausgeführt werden kann, bevor alle Transaktionsaufgaben für den zweiten Thread abgeschlossen sind und <xref:System.Transactions.DependentTransaction.Complete%2A> für die abhängige Transaktion aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="02c2b-129">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="02c2b-130">Dies bedeutet Folgendes: Wenn der Client Bereich endet (wenn er versucht, das Transaktions Objekt am Ende der Anweisung zu verwerfen `using` ), bevor der neue Thread <xref:System.Transactions.DependentTransaction.Complete%2A> für die abhängige Transaktion aufruft, wird der Client Code blockiert, bis <xref:System.Transactions.DependentTransaction.Complete%2A> für den abhängigen aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="02c2b-130">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the `using` statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="02c2b-131">Dann kann die Transaktion durch Commit oder Abbruch beendet werden.</span><span class="sxs-lookup"><span data-stu-id="02c2b-131">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="02c2b-132">Parallelitätsprobleme</span><span class="sxs-lookup"><span data-stu-id="02c2b-132">Concurrency Issues</span></span>  

 <span data-ttu-id="02c2b-133">Es gibt noch einige weitere Parallelitätsaspekte, die Sie beachten müssen, wenn Sie die <xref:System.Transactions.DependentTransaction>-Klasse verwenden:</span><span class="sxs-lookup"><span data-stu-id="02c2b-133">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
- <span data-ttu-id="02c2b-134">Wenn der Arbeitsthread einen Rollback für die Transaktion ausführt, die übergeordnete Transaktion jedoch versucht, einen Commit dafür auszuführen, wird eine <xref:System.Transactions.TransactionAbortedException>-Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="02c2b-134">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
- <span data-ttu-id="02c2b-135">Sie sollten einen neuen abhängigen Klon für jeden Arbeitsthread in der Transaktion erstellen.</span><span class="sxs-lookup"><span data-stu-id="02c2b-135">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="02c2b-136">Übergeben Sie nicht denselben abhängigen Klon an mehrere Threads, da nur einer davon <xref:System.Transactions.DependentTransaction.Complete%2A> aufrufen kann.</span><span class="sxs-lookup"><span data-stu-id="02c2b-136">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
- <span data-ttu-id="02c2b-137">Wenn der Arbeitsthread einen neuen Arbeitsthread erzeugt, müssen Sie einen abhängigen Klon des abhängigen Klons erstellen und an den neuen Thread übergeben.</span><span class="sxs-lookup"><span data-stu-id="02c2b-137">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02c2b-138">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="02c2b-138">See also</span></span>

- <xref:System.Transactions.DependentTransaction>
