---
title: Beispiele für DataSet-spezifische Operatoren (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 4cd99a103fabee3c87036a9933077a3a967f5a13
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173691"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="4637f-102">Beispiele für DataSet-spezifische Operatoren (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="4637f-102">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>

<span data-ttu-id="4637f-103">In den Beispielen in diesem Thema wird gezeigt, wie Sie die <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>-Methode und die <xref:System.Data.DataRowComparer>-Klasse verwenden können.</span><span class="sxs-lookup"><span data-stu-id="4637f-103">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="4637f-104">Die `FillDataSet` in diesen Beispielen verwendete Methode wird beim [Laden von Daten in ein DataSet](loading-data-into-a-dataset.md)angegeben.</span><span class="sxs-lookup"><span data-stu-id="4637f-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="4637f-105">In den Beispielen in diesem Thema wird auf die Tabellen &lt;legacyBold&gt;Contact&lt;/legacyBold&gt;, &lt;legacyBold&gt;Address&lt;/legacyBold&gt;, &lt;legacyBold&gt;Product&lt;/legacyBold&gt;, &lt;legacyBold&gt;SalesOrderHeader&lt;/legacyBold&gt; und &lt;legacyBold&gt;SalesOrderDetail&lt;/legacyBold&gt; in der &lt;legacyBold&gt;AdventureWorks&lt;/legacyBold&gt;-Beispieldatenbank zurückgegriffen.</span><span class="sxs-lookup"><span data-stu-id="4637f-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="4637f-106">In den Beispielen in diesem Thema werden die folgenden- `using` / `Imports` Anweisungen verwendet:</span><span class="sxs-lookup"><span data-stu-id="4637f-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="4637f-107">Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines LINQ to DataSet Projekts in Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="4637f-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="4637f-108">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="4637f-108">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="4637f-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4637f-109">Example</span></span>  

 <span data-ttu-id="4637f-110">In diesem Beispiel wird eine <xref:System.Data.DataTable> mithilfe der <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>-Methode mit Abfrageergebnissen geladen.</span><span class="sxs-lookup"><span data-stu-id="4637f-110">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="4637f-111">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="4637f-111">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="4637f-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4637f-112">Example</span></span>  

 <span data-ttu-id="4637f-113">In diesem Beispiel werden zwei verschiedene Datenzeilen mithilfe von <xref:System.Data.DataRowComparer> miteinander verglichen.</span><span class="sxs-lookup"><span data-stu-id="4637f-113">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="4637f-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4637f-114">See also</span></span>

- [<span data-ttu-id="4637f-115">Laden von Daten in ein DataSet</span><span class="sxs-lookup"><span data-stu-id="4637f-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="4637f-116">Beispiele für LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="4637f-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
