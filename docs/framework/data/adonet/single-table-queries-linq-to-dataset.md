---
title: Abfragen für einzelne Tabellen (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 17a2fcf54cae64d9443b0cc0e8a37e1002bbd394
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175355"
---
# <a name="single-table-queries-linq-to-dataset"></a>Abfragen für einzelne Tabellen (LINQ to DataSet)

LINQ-Abfragen (Language-Integrated Query) können für Datenquellen verwendet werden, die die- <xref:System.Collections.Generic.IEnumerable%601> Schnittstelle oder die- <xref:System.Linq.IQueryable%601> Schnittstelle implementieren. Die- <xref:System.Data.DataTable> Klasse implementiert keine der beiden Schnittstellen, sodass Sie die- <xref:System.Data.DataTableExtensions.AsEnumerable%2A> Methode verwenden müssen, wenn Sie das <xref:System.Data.DataTable> als Quelle in der- `From` Klausel einer LINQ-Abfrage verwenden möchten.  
  
 Das folgende Beispiel ruft alle Onlinebestellungen aus der Tabelle SalesOrderHeader ab und zeigt in der Konsole die Auftrags-ID, das Auftragsdatum und die Auftragsnummer an.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
 Die Abfrage der lokalen Variable wird mit einem Abfrage Ausdruck initialisiert, der für eine oder mehrere Informationsquellen durch Anwenden eines oder mehrerer Abfrage Operatoren entweder von den Standard Abfrage Operatoren oder, bei der LINQ to DataSet, für die-Klasse spezifische Operatoren angewendet wird <xref:System.Data.DataSet> . Der Abfrageausdruck im vorherigen Beispiel verwendet zwei der Standardabfrageoperatoren: `Where` und `Select`.  
  
 Die `Where`-Klausel filtert die Reihenfolge auf der Basis einer Bedingung. In diesem Fall lautet die Bedingung, dass für `OnlineOrderFlag` der Wert `true` gilt. Der `Select`-Operator ordnet ein aufzählbares Objekt zu, das die an den Operator übergebenen Argumente erfasst, und gibt das Objekt zurück. Im Beispiel oben wird ein anonymer Typ mit drei Eigenschaften erstellt: `SalesOrderID`, `OrderDate` und `SalesOrderNumber`. Als Werte für diese drei Eigenschaften werden die Werte der Spalten `SalesOrderID`, `OrderDate` und `SalesOrderNumber` aus der `SalesOrderHeader`-Tabelle verwendet.  
  
 Die `foreach`-Schleife zählt dann das von `Select` zurückgegebene aufzählbare Objekt auf und gibt die Abfrageergebnisse aus. Da es sich bei der Abfrage um eine <xref:System.Linq.Enumerable>-Abfrage handelt, die die <xref:System.Collections.Generic.IEnumerable%601>-Schnittstelle implementiert, wird die Auswertung der Abfrage so lange verzögert, bis die Abfragevariable mit der `foreach`-Schleife durchlaufen wird. Durch die verzögerte Abfrageauswertung können die Abfragen als Werte erhalten werden, die mehrere Male ausgewertet werden und dabei potenziell jedes Mal ein anderes Ergebnis erbringen können.  
  
 Die <xref:System.Data.DataRowExtensions.Field%2A>-Methode bietet Zugriff auf die Spaltenwerte einer <xref:System.Data.DataRow>, und das <xref:System.Data.DataRowExtensions.SetField%2A> (im Beispiel oben nicht dargestellt) gibt Spaltenwerte in einer <xref:System.Data.DataRow> an. Sowohl die <xref:System.Data.DataRowExtensions.Field%2A> -Methode als auch die- <xref:System.Data.DataRowExtensions.SetField%2A> Methode behandeln auf NULL festleg Bare Werttypen, sodass Sie nicht explizit nach NULL-Werten suchen müssen. Beide Methoden sind darüber hinaus generische Methoden. Der Rückgabetyp muss also nicht umgewandelt werden. Sie könnten die schon vorhandene Spaltenzugriffsmethode in <xref:System.Data.DataRow> (z. B. `o["OrderDate"]`) verwenden, müssten dann aber das Rückgabeobjekt in den entsprechenden Typ umwandeln.  Wenn die Spalte ein Werttyp ist, der NULL-Werte zulässt, müssen Sie mithilfe der-Methode überprüfen, ob der Wert NULL ist <xref:System.Data.DataRow.IsNull%2A> . Weitere Informationen finden Sie unter [generische Field-und SetField-Methoden](generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Beachten Sie, dass der im generischen `T`-Parameter der <xref:System.Data.DataRowExtensions.Field%2A>-Methode und der <xref:System.Data.DataRowExtensions.SetField%2A>-Methode angegebene Datentyp mit dem Typ des zugrunde liegenden Werts übereinstimmen muss. Anderenfalls wird eine <xref:System.InvalidCastException> ausgelöst. Der angegebene Spaltenname muss außerdem mit dem Namen einer <xref:System.Data.DataSet>-Spalte übereinstimmen. Wenn dies nicht der Fall ist, wird eine <xref:System.ArgumentException> ausgelöst. Die Auslösung der Ausnahme erfolgt in beiden Fällen bei der Datenenumeration zur Laufzeit, wenn die Abfrage ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen

- [Tabellenübergreifende Abfragen](cross-table-queries-linq-to-dataset.md)
- [Abfragen von typisierten DataSets](querying-typed-datasets.md)
- [Generische Field- und SetField-Methoden](generic-field-and-setfield-methods-linq-to-dataset.md)
