---
title: 'Beispiele für die Abfrageausdruckssyntax: Aggregierungsoperatoren (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85dafa07-e102-46e7-ab78-37bf06f257a6
ms.openlocfilehash: 2277058c4dad4632f4f47a39e32463eaf77dcd5e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164570"
---
# <a name="query-expression-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="44f20-102">Beispiele für die Abfrageausdruckssyntax: Aggregierungsoperatoren (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="44f20-102">Query Expression Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="44f20-103">In den Beispielen in diesem Thema wird gezeigt, wie Sie mithilfe der Methoden <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A> und <xref:System.Linq.Enumerable.Sum%2A> und der Abfrageausdruckssyntax ein <xref:System.Data.DataSet> abfragen und Daten aggregieren können.</span><span class="sxs-lookup"><span data-stu-id="44f20-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data using query expression syntax.</span></span>  
  
 <span data-ttu-id="44f20-104">Die `FillDataSet` in diesen Beispielen verwendete Methode wird beim [Laden von Daten in ein DataSet](loading-data-into-a-dataset.md)angegeben.</span><span class="sxs-lookup"><span data-stu-id="44f20-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="44f20-105">In den Beispielen in diesem Thema wird auf die Tabellen &lt;legacyBold&gt;Contact&lt;/legacyBold&gt;, &lt;legacyBold&gt;Address&lt;/legacyBold&gt;, &lt;legacyBold&gt;Product&lt;/legacyBold&gt;, &lt;legacyBold&gt;SalesOrderHeader&lt;/legacyBold&gt; und &lt;legacyBold&gt;SalesOrderDetail&lt;/legacyBold&gt; in der &lt;legacyBold&gt;AdventureWorks&lt;/legacyBold&gt;-Beispieldatenbank zurückgegriffen.</span><span class="sxs-lookup"><span data-stu-id="44f20-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="44f20-106">In den Beispielen in diesem Thema werden die folgenden- `using` / `Imports` Anweisungen verwendet:</span><span class="sxs-lookup"><span data-stu-id="44f20-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="44f20-107">Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines LINQ to DataSet Projekts in Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="44f20-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="average"></a><span data-ttu-id="44f20-108">Average</span><span class="sxs-lookup"><span data-stu-id="44f20-108">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="44f20-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="44f20-109">Example</span></span>  

 <span data-ttu-id="44f20-110">In diesem Beispiel wird die <xref:System.Linq.Enumerable.Average%2A>-Methode verwendet, um den durchschnittlichen Listenpreis der Produkte für die einzelnen Stile zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="44f20-110">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="44f20-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="44f20-111">Example</span></span>  

 <span data-ttu-id="44f20-112">In diesem Beispiel wird die <xref:System.Linq.Enumerable.Average%2A>-Methode verwendet, um für jede Kontakt-ID den durchschnittlichen fälligen Gesamtbetrag zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="44f20-112">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="44f20-113">Beispiel</span><span class="sxs-lookup"><span data-stu-id="44f20-113">Example</span></span>  

 <span data-ttu-id="44f20-114">In diesem Beispiel wird die <xref:System.Linq.Enumerable.Average%2A>-Methode verwendet, um für jede Kontakt-ID die Aufträge mit dem durchschnittlichen `TotalDue`-Wert zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="44f20-114">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="44f20-115">Anzahl</span><span class="sxs-lookup"><span data-stu-id="44f20-115">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="44f20-116">Beispiel</span><span class="sxs-lookup"><span data-stu-id="44f20-116">Example</span></span>  

 <span data-ttu-id="44f20-117">In diesem Beispiel wird die <xref:System.Linq.Enumerable.Count%2A>-Methode verwendet, um eine Liste der Kontakt-IDs und der jeweiligen Anzahl von Aufträgen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="44f20-117">This example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="44f20-118">Beispiel</span><span class="sxs-lookup"><span data-stu-id="44f20-118">Example</span></span>  

 <span data-ttu-id="44f20-119">In diesem Beispiel werden die Produkte nach ihrer Farbe gruppiert. Anschließend wird die <xref:System.Linq.Enumerable.Count%2A>-Methode verwendet, um die Anzahl der Produkte in jeder Farbgruppe abzurufen.</span><span class="sxs-lookup"><span data-stu-id="44f20-119">This example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="44f20-120">Max</span><span class="sxs-lookup"><span data-stu-id="44f20-120">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="44f20-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="44f20-121">Example</span></span>  

 <span data-ttu-id="44f20-122">In diesem Beispiel wird die <xref:System.Linq.Enumerable.Max%2A>-Methode verwendet, um für jede Kontakt-ID den größten fälligen Gesamtbetrag zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="44f20-122">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="44f20-123">Beispiel</span><span class="sxs-lookup"><span data-stu-id="44f20-123">Example</span></span>  

 <span data-ttu-id="44f20-124">In diesem Beispiel wird die <xref:System.Linq.Enumerable.Max%2A>-Methode verwendet, um für jede Kontakt-ID die Aufträge mit dem größten `TotalDue`-Wert abzurufen.</span><span class="sxs-lookup"><span data-stu-id="44f20-124">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="44f20-125">Min</span><span class="sxs-lookup"><span data-stu-id="44f20-125">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="44f20-126">Beispiel</span><span class="sxs-lookup"><span data-stu-id="44f20-126">Example</span></span>  

 <span data-ttu-id="44f20-127">In diesem Beispiel wird die <xref:System.Linq.Enumerable.Min%2A>-Methode verwendet, um für jede Kontakt-ID den kleinsten fälligen Gesamtbetrag zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="44f20-127">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="44f20-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="44f20-128">Example</span></span>  

 <span data-ttu-id="44f20-129">In diesem Beispiel wird die <xref:System.Linq.Enumerable.Min%2A>-Methode verwendet, um für jeden Kontakt die Aufträge mit dem kleinsten fälligen Gesamtbetrag zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="44f20-129">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="44f20-130">SUM</span><span class="sxs-lookup"><span data-stu-id="44f20-130">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="44f20-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="44f20-131">Example</span></span>  

 <span data-ttu-id="44f20-132">In diesem Beispiel wird die <xref:System.Linq.Enumerable.Sum%2A>-Methode verwendet, um für jede Kontakt-ID den fälligen Gesamtbetrag zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="44f20-132">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="44f20-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="44f20-133">See also</span></span>

- [<span data-ttu-id="44f20-134">Laden von Daten in ein DataSet</span><span class="sxs-lookup"><span data-stu-id="44f20-134">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="44f20-135">Beispiele für LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="44f20-135">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="44f20-136">Standard Query Operators Overview (C#) (Übersicht über Standardabfrageoperatoren (C#))</span><span class="sxs-lookup"><span data-stu-id="44f20-136">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="44f20-137">Standard Query Operators Overview (Visual Basic) (Übersicht über Standardabfrageoperatoren (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="44f20-137">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
