---
title: 'Vorgehensweise: Implementieren von CopyToDataTable<T> mit einem anderen generischen Typ „T“ als DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 776ff6062282d12b622ec89cfa9990513da64a07
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194595"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="75005-102">Vorgehensweise: Implementieren von CopyToDataTable\<T> mit einem anderen generischen Typ „T“ als DataRow</span><span class="sxs-lookup"><span data-stu-id="75005-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>

<span data-ttu-id="75005-103">Das <xref:System.Data.DataTable>-Objekt wird oft für die Datenbindung verwendet.</span><span class="sxs-lookup"><span data-stu-id="75005-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="75005-104">Die <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>-Methode kopiert die Ergebnisse einer Abfrage in eine <xref:System.Data.DataTable>, die dann für die Datenbindung verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="75005-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="75005-105">Die <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>-Methoden arbeiten allerdings nur mit einer <xref:System.Collections.Generic.IEnumerable%601>-Quelle, bei der der generische Parameter `T` den Typ <xref:System.Data.DataRow> aufweist.</span><span class="sxs-lookup"><span data-stu-id="75005-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="75005-106">Obwohl dies hilfreich ist, können Tabellen dabei nicht aus einer Sequenz von Skalartypen, aus Abfragen, die anonyme Typen darstellen oder aus Abfragen, die Tabellenjoins durchführen, erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="75005-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="75005-107">In diesem Thema wird beschrieben, wie zwei benutzerdefinierte `CopyToDataTable<T>`-Erweiterungsmethoden implementiert werden, die einen generischen Parameter `T` annehmen, der einen anderen Typ als <xref:System.Data.DataRow> aufweist.</span><span class="sxs-lookup"><span data-stu-id="75005-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="75005-108">Die Logik zum Erstellen einer <xref:System.Data.DataTable> aus einer <xref:System.Collections.Generic.IEnumerable%601>-Quelle ist in der `ObjectShredder<T>`-Klasse enthalten, die wiederum von zwei überladenen `CopyToDataTable<T>`-Erweiterungsmethoden umschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="75005-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="75005-109">Die `Shred`-Methode der `ObjectShredder<T>`-Klasse gibt die gefüllte <xref:System.Data.DataTable> zurück und nimmt drei Eingabeparameter an: eine <xref:System.Collections.Generic.IEnumerable%601>-Quelle, eine <xref:System.Data.DataTable> und eine <xref:System.Data.LoadOption>-Enumeration.</span><span class="sxs-lookup"><span data-stu-id="75005-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="75005-110">Das anfängliche Schema der zurückgegebenen <xref:System.Data.DataTable> basiert auf dem Schema des Typs `T`.</span><span class="sxs-lookup"><span data-stu-id="75005-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="75005-111">Wenn eine vorhandene Tabelle als Eingabe bereitgestellt wird, muss deren Schema mit dem Schema des Typs `T` übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="75005-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="75005-112">Jede öffentliche Eigenschaft und jedes Feld des Typs `T` wird in eine <xref:System.Data.DataColumn> in der zurückgegebenen Tabelle konvertiert.</span><span class="sxs-lookup"><span data-stu-id="75005-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="75005-113">Wenn die Quellsequenz einen von `T` abgeleiteten Typ enthält, wird das zurückgegebene Tabellenschema um zusätzliche öffentliche Eigeschaften bzw. Felder erweitert.</span><span class="sxs-lookup"><span data-stu-id="75005-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="75005-114">Beispiele für die Verwendung der benutzerdefinierten `CopyToDataTable<T>`-Methoden finden Sie unter [Creating a DataTable From a Query (Erstellen einer DataTable aus einer Abfrage)](creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="75005-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="75005-115">So implementieren Sie die benutzerdefinierten copydedatbare- \<T> Methoden in der Anwendung</span><span class="sxs-lookup"><span data-stu-id="75005-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="75005-116">Implementieren Sie die `ObjectShredder<T>`-Klasse, um eine <xref:System.Data.DataTable> aus einer <xref:System.Collections.Generic.IEnumerable%601>-Quelle zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="75005-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="75005-117">Im vorangehenden Beispiel wird davon ausgegangen, dass die Eigenschaften und Felder der keine auf NULL festleg `DataColumn` baren Werttypen sind.</span><span class="sxs-lookup"><span data-stu-id="75005-117">The preceding example assumes that the properties and fields of the `DataColumn` are not nullable value types.</span></span> <span data-ttu-id="75005-118">Verwenden Sie den folgenden Code, um Eigenschaften und Felder mit auf NULL festleg baren Werttypen zu behandeln:</span><span class="sxs-lookup"><span data-stu-id="75005-118">To handle properties and fields with nullable value types, use the following code:</span></span>

    ```csharp
    // Nullable-aware code for properties.
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);

    // Nullable-aware code for fields.
    DataColumn dc = table.Columns.Contains(f.Name) ? table.Columns[f.Name] : table.Columns.Add(f.Name, Nullable.GetUnderlyingType(f.FieldType) ?? f.FieldType);
    ```

2. <span data-ttu-id="75005-119">Implementieren Sie die benutzerdefinierten `CopyToDataTable<T>`-Erweiterungsmethoden in einer Klasse:</span><span class="sxs-lookup"><span data-stu-id="75005-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="75005-120">Fügen Sie die `ObjectShredder<T>`-Klasse und die `CopyToDataTable<T>`-Erweiterungsmethoden Ihrer Anwendung hinzu.</span><span class="sxs-lookup"><span data-stu-id="75005-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="75005-121">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="75005-121">See also</span></span>

- [<span data-ttu-id="75005-122">Erstellen einer DataTable aus einer Abfrage</span><span class="sxs-lookup"><span data-stu-id="75005-122">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="75005-123">Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="75005-123">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
