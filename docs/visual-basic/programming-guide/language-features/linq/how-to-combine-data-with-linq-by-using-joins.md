---
title: 'Vorgehensweise: Kombinieren von Daten mit LINQ mithilfe von Joins'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: ebda8d3b7fa2e712c337ed2c1fadc580bed7fe61
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075069"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="67c86-102">Gewusst wie: Kombinieren von Daten mit LINQ mithilfe von Joins (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67c86-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>

<span data-ttu-id="67c86-103">Visual Basic stellt die `Join` -und- `Group Join` Abfrage Klauseln bereit, mit denen Sie den Inhalt mehrerer Auflistungen basierend auf gemeinsamen Werten zwischen den Auflistungen kombinieren können.</span><span class="sxs-lookup"><span data-stu-id="67c86-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="67c86-104">Diese Werte werden als *Schlüssel* Werte bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="67c86-104">These values are known as *key* values.</span></span> <span data-ttu-id="67c86-105">Entwickler, die mit relationalen Datenbankkonzepten vertraut sind, erkennen die `Join` -Klausel als inneren Join und die- `Group Join` Klausel als einen linken äußeren Join.</span><span class="sxs-lookup"><span data-stu-id="67c86-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="67c86-106">Die Beispiele in diesem Thema veranschaulichen einige Möglichkeiten zum Kombinieren von Daten mithilfe der `Join` `Group Join` Abfrage Klauseln und.</span><span class="sxs-lookup"><span data-stu-id="67c86-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="67c86-107">Erstellen eines Projekts und Hinzufügen von Beispiel Daten</span><span class="sxs-lookup"><span data-stu-id="67c86-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="67c86-108">So erstellen Sie ein Projekt, das Beispiel Daten und-Typen enthält</span><span class="sxs-lookup"><span data-stu-id="67c86-108">To create a project that contains sample data and types</span></span>  
  
1. <span data-ttu-id="67c86-109">Öffnen Sie Visual Studio, und fügen Sie ein neues Visual Basic Konsolen Anwendungsprojekt hinzu, um die Beispiele in diesem Thema auszuführen.</span><span class="sxs-lookup"><span data-stu-id="67c86-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="67c86-110">Doppelklicken Sie auf die durch Visual Basic erstellte Datei Module1. vb.</span><span class="sxs-lookup"><span data-stu-id="67c86-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2. <span data-ttu-id="67c86-111">In den Beispielen in diesem Thema werden der-Typ und der- `Person` `Pet` Typ sowie die Daten aus dem folgenden Codebeispiel verwendet.</span><span class="sxs-lookup"><span data-stu-id="67c86-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="67c86-112">Kopieren Sie diesen Code in das Standardmodul, das `Module1` von Visual Basic erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="67c86-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="67c86-113">Ausführen einer inneren Verknüpfung mithilfe der Join-Klausel</span><span class="sxs-lookup"><span data-stu-id="67c86-113">Perform an Inner Join by Using the Join Clause</span></span>  

 <span data-ttu-id="67c86-114">Ein innerer Join kombiniert Daten aus zwei Auflistungen.</span><span class="sxs-lookup"><span data-stu-id="67c86-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="67c86-115">Elemente, für die die angegebenen Schlüsselwerte Stimmen, werden eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="67c86-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="67c86-116">Alle Elemente aus einer Auflistung, die nicht über ein übereinstimmendes Element in der anderen Sammlung verfügen, werden ausgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="67c86-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="67c86-117">In Visual Basic bietet LINQ zwei Optionen für die Durchführung eines inneren Joins: einen impliziten Join und einen expliziten Join.</span><span class="sxs-lookup"><span data-stu-id="67c86-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="67c86-118">Ein impliziter Join gibt die Auflistungen an, die in einer-Klausel miteinander verknüpft werden sollen, `From` und identifiziert die übereinstimmenden Schlüsselfelder `Where`</span><span class="sxs-lookup"><span data-stu-id="67c86-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="67c86-119">Visual Basic die zwei Auflistungen implizit auf der Grundlage der angegebenen Schlüsselfelder verbindet.</span><span class="sxs-lookup"><span data-stu-id="67c86-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="67c86-120">Sie können einen expliziten Join angeben, indem Sie die- `Join` Klausel verwenden, wenn Sie spezifisch sein möchten, welche Schlüsselfelder im Join verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="67c86-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="67c86-121">In diesem Fall kann eine- `Where` Klausel weiterhin verwendet werden, um die Abfrageergebnisse zu filtern.</span><span class="sxs-lookup"><span data-stu-id="67c86-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="67c86-122">So führen Sie einen inneren Join mithilfe der Join-Klausel aus</span><span class="sxs-lookup"><span data-stu-id="67c86-122">To perform an Inner Join by using the Join clause</span></span>  
  
1. <span data-ttu-id="67c86-123">Fügen Sie dem- `Module1` Modul in Ihrem Projekt den folgenden Code hinzu, um Beispiele für einen impliziten und einen expliziten inneren Join anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="67c86-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="67c86-124">Ausführen eines Left Outer Join mithilfe der Group Join-Klausel</span><span class="sxs-lookup"><span data-stu-id="67c86-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  

 <span data-ttu-id="67c86-125">Ein linker äußerer Join schließt alle Elemente aus der linksseitigen Auflistung des Joins und nur übereinstimmende Werte aus der rechten Auflistung der Verknüpfung ein.</span><span class="sxs-lookup"><span data-stu-id="67c86-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="67c86-126">Alle Elemente aus der rechten Auflistung des Joins, die nicht über ein übereinstimmendes Element in der Auflistung auf der linken Seite verfügen, werden aus dem Abfrageergebnis ausgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="67c86-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="67c86-127">Die- `Group Join` Klausel führt in der Tat einen Left Outer Join aus.</span><span class="sxs-lookup"><span data-stu-id="67c86-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="67c86-128">Der Unterschied zwischen dem, der in der Regel als linker äußerer Join bezeichnet wird, und der `Group Join` Rückgabe der Klausel besteht darin, dass die- `Group Join` Klausel Ergebnisse aus der rechten Auflistung des Joins für jedes Element in der linken Auflistung gruppiert.</span><span class="sxs-lookup"><span data-stu-id="67c86-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="67c86-129">In einer relationalen Datenbank gibt ein linker äußerer Join ein nicht gruppiertes Ergebnis zurück, in dem jedes Element im Abfrageergebnis übereinstimmende Elemente aus beiden Auflistungen im Join enthält.</span><span class="sxs-lookup"><span data-stu-id="67c86-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="67c86-130">In diesem Fall werden die Elemente aus der linksseitigen Auflistung der Verknüpfung für jedes übereinstimmende Element aus der rechten Auflistung wiederholt.</span><span class="sxs-lookup"><span data-stu-id="67c86-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="67c86-131">Wenn Sie das nächste Verfahren ausführen, sehen Sie, wie es aussieht.</span><span class="sxs-lookup"><span data-stu-id="67c86-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="67c86-132">Sie können die Ergebnisse einer `Group Join` Abfrage als nicht gruppiertes Ergebnis abrufen, indem Sie die Abfrage so erweitern, dass ein Element für jedes gruppierte Abfrageergebnis zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="67c86-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="67c86-133">Um dies zu erreichen, müssen Sie sicherstellen, dass Sie die- `DefaultIfEmpty` Methode der gruppierten Auflistung Abfragen.</span><span class="sxs-lookup"><span data-stu-id="67c86-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="67c86-134">Dadurch wird sichergestellt, dass Elemente aus der linksseitigen Auflistung des Joins weiterhin im Abfrageergebnis enthalten sind, auch wenn Sie über keine übereinstimmenden Ergebnisse aus der rechten Auflistung verfügen.</span><span class="sxs-lookup"><span data-stu-id="67c86-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="67c86-135">Sie können der Abfrage Code hinzufügen, um einen Standard Ergebniswert bereitzustellen, wenn kein übereinstimmender Wert aus der rechtsseitigen Auflistung des Joins vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="67c86-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="67c86-136">So führen Sie einen Left Outer Join mithilfe der Group Join-Klausel aus</span><span class="sxs-lookup"><span data-stu-id="67c86-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1. <span data-ttu-id="67c86-137">Fügen Sie dem- `Module1` Modul in Ihrem Projekt den folgenden Code hinzu, um Beispiele für einen gruppierten linken äußeren Join und einen nicht gruppierten linken äußeren Join anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="67c86-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="67c86-138">Ausführen eines Joins mithilfe eines zusammengesetzten Schlüssels</span><span class="sxs-lookup"><span data-stu-id="67c86-138">Perform a Join by Using a Composite Key</span></span>  

 <span data-ttu-id="67c86-139">Sie können das- `And` Schlüsselwort in einer- `Join` oder- `Group Join` Klausel verwenden, um mehrere Schlüsselfelder zu identifizieren, die beim Abgleichen von Werten aus den verbundenen Auflistungen verwendet</span><span class="sxs-lookup"><span data-stu-id="67c86-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="67c86-140">Das `And` Schlüsselwort gibt an, dass alle angegebenen Schlüsselfelder für Elemente, die verknüpft werden sollen, entsprechen müssen.</span><span class="sxs-lookup"><span data-stu-id="67c86-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="67c86-141">So führen Sie einen Join mit einem zusammengesetzten Schlüssel aus</span><span class="sxs-lookup"><span data-stu-id="67c86-141">To perform a Join by using a composite key</span></span>  
  
1. <span data-ttu-id="67c86-142">Fügen Sie dem- `Module1` Modul in Ihrem Projekt den folgenden Code hinzu, um Beispiele für einen Join anzuzeigen, der einen zusammengesetzten Schlüssel verwendet.</span><span class="sxs-lookup"><span data-stu-id="67c86-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a><span data-ttu-id="67c86-143">Ausführen des Codes</span><span class="sxs-lookup"><span data-stu-id="67c86-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="67c86-144">So fügen Sie Code zum Ausführen der Beispiele hinzu</span><span class="sxs-lookup"><span data-stu-id="67c86-144">To add code to run the examples</span></span>  
  
1. <span data-ttu-id="67c86-145">Ersetzen `Sub Main` Sie im- `Module1` Modul in Ihrem Projekt durch den folgenden Code, um die Beispiele in diesem Thema auszuführen.</span><span class="sxs-lookup"><span data-stu-id="67c86-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. <span data-ttu-id="67c86-146">Drücken Sie F5, um die Beispiele auszuführen.</span><span class="sxs-lookup"><span data-stu-id="67c86-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c86-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="67c86-147">See also</span></span>

- [<span data-ttu-id="67c86-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="67c86-148">LINQ</span></span>](index.md)
- [<span data-ttu-id="67c86-149">Einführung in LINQ in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67c86-149">Introduction to LINQ in Visual Basic</span></span>](introduction-to-linq.md)
- [<span data-ttu-id="67c86-150">Join-Klausel</span><span class="sxs-lookup"><span data-stu-id="67c86-150">Join Clause</span></span>](../../../language-reference/queries/join-clause.md)
- [<span data-ttu-id="67c86-151">Group Join-Klausel</span><span class="sxs-lookup"><span data-stu-id="67c86-151">Group Join Clause</span></span>](../../../language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="67c86-152">From-Klausel</span><span class="sxs-lookup"><span data-stu-id="67c86-152">From Clause</span></span>](../../../language-reference/queries/from-clause.md)
- [<span data-ttu-id="67c86-153">WHERE-Klausel</span><span class="sxs-lookup"><span data-stu-id="67c86-153">Where Clause</span></span>](../../../language-reference/queries/where-clause.md)
- [<span data-ttu-id="67c86-154">Abfragen</span><span class="sxs-lookup"><span data-stu-id="67c86-154">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="67c86-155">Datentransformationen mit LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="67c86-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
