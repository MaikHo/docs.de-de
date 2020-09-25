---
title: "\"ChildViews\" und Beziehungen"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d475d356-6abb-4701-8fd1-2906fb93dfba
ms.openlocfilehash: 74b2de7a9ee62ae42a932c94261cf425d6a94808
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203734"
---
# <a name="childviews-and-relations"></a><span data-ttu-id="7d9c0-102">"ChildViews" und Beziehungen</span><span class="sxs-lookup"><span data-stu-id="7d9c0-102">ChildViews and Relations</span></span>

<span data-ttu-id="7d9c0-103">Wenn zwischen Tabellen in einem <xref:System.Data.DataSet> Beziehungen vorhanden sind, können Sie eine <xref:System.Data.DataView> mit Zeilen aus der verwandten untergeordneten Tabelle erstellen, indem Sie die <xref:System.Data.DataRowView.CreateChildView%2A>-Methode der <xref:System.Data.DataRowView> für die Zeilen in der übergeordneten Tabelle verwenden.</span><span class="sxs-lookup"><span data-stu-id="7d9c0-103">If a relationship exists between tables in a <xref:System.Data.DataSet>, you can create a <xref:System.Data.DataView> containing rows from the related child table by using the <xref:System.Data.DataRowView.CreateChildView%2A> method of the <xref:System.Data.DataRowView> for the rows in the parent table.</span></span> <span data-ttu-id="7d9c0-104">Der folgende Code zeigt z. b. **Kategorien** und ihre zugehörigen **Produkte** in alphabetischer Reihenfolge nach " **CategoryName** " und " **ProductName**" sortiert an.</span><span class="sxs-lookup"><span data-stu-id="7d9c0-104">For example, the following code displays **Categories** and their related **Products** in alphabetical order sorted by **CategoryName** and **ProductName**.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
Dim prodTable As DataTable = catDS.Tables("Products")  
  
' Create a relation between the Categories and Products tables.  
Dim relation As DataRelation = catDS.Relations.Add("CatProdRel", _  
  catTable.Columns("CategoryID"), _  
  prodTable.Columns("CategoryID"))  
  
' Create DataViews for the Categories and Products tables.  
Dim catView As DataView = New DataView(catTable, "", _  
  "CategoryName", DataViewRowState.CurrentRows)  
Dim prodView As DataView  
  
' Iterate through the Categories table.  
Dim catDRV, prodDRV As DataRowView  
  
For Each catDRV In catView  
  Console.WriteLine(catDRV("CategoryName"))  
  
  ' Create a DataView of the child product records.  
  prodView = catDRV.CreateChildView(relation)  
  prodView.Sort = "ProductName"  
  
  For Each prodDRV In prodView  
    Console.WriteLine(vbTab & prodDRV("ProductName"))  
  Next  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
DataTable prodTable = catDS.Tables["Products"];  
  
// Create a relation between the Categories and Products tables.  
DataRelation relation = catDS.Relations.Add("CatProdRel",
  catTable.Columns["CategoryID"],  
                                                            prodTable.Columns["CategoryID"]);  
  
// Create DataViews for the Categories and Products tables.  
DataView catView = new DataView(catTable, "", "CategoryName",
  DataViewRowState.CurrentRows);  
DataView prodView;  
  
// Iterate through the Categories table.  
foreach (DataRowView catDRV in catView)  
{  
  Console.WriteLine(catDRV["CategoryName"]);  
  
  // Create a DataView of the child product records.  
  prodView = catDRV.CreateChildView(relation);  
  prodView.Sort = "ProductName";  
  
  foreach (DataRowView prodDRV in prodView)  
    Console.WriteLine("\t" + prodDRV["ProductName"]);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d9c0-105">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7d9c0-105">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="7d9c0-106">"DataViews"</span><span class="sxs-lookup"><span data-stu-id="7d9c0-106">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="7d9c0-107">Übersicht über ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7d9c0-107">ADO.NET Overview</span></span>](../ado-net-overview.md)
