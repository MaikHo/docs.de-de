---
title: Join-Vorgänge (C#)
description: Bei einem Join von zwei Datenquellen werden Objekte anderen Objekten mit einem gemeinsamen Attribut aus unterschiedlichen Datenquellen zugeordnet. Informationen zu Join-Methoden im LINQ-Framework in C#
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165696"
---
# <a name="no-locjoin-operations-c"></a>Join-Vorgänge (C#)

Eine *Verknüpfung* zweier Datenquellen entspricht der Zuordnung von Objekten einer Datenquelle zu den Objekten einer anderen Datenquelle, die ein Attribut gemeinsam haben.  
  
 Der Join-Vorgang ist für Abfragen sehr wichtig. Er ist auf Datenquellen ausgerichtet, deren Beziehungen zueinander nicht direkt verfolgt werden können. Bei der objektorientierten Programmierung könnte dies eine nicht modellierte Korrelation zwischen Objekten bedeuten, z. B. die entgegengesetzte Richtung einer unidirektionalen Beziehung. Ein Beispiel einer unidirektionalen Beziehung ist die Klasse "Kunde" mit der Eigenschaft vom Typ "Ort", während die Klasse "Ort" keine Eigenschaft besitzt, die einer Auflistung von "Kunde"-Objekten entspricht. Wenn Sie eine Liste von "Ort"-Objekten besitzen und alle Kunden in den einzelnen Orten finden möchten, könnten Sie eine Join-Operation verwenden, um diese zu finden.  
  
 Die im LINQ-Framework bereitgestellten Join-Methoden sind <xref:System.Linq.Enumerable.Join%2A> und <xref:System.Linq.Enumerable.GroupJoin%2A>. Diese Methoden führen Gleichheitsverknüpfungen oder Verknüpfungen durch, bei denen zwei Datenquellen auf Basis der Gleichheit ihrer Schlüssel verglichen werden. (Zum Vergleich: Transact-SQL unterstützt auch andere Join-Operatoren als "ist gleich", z. B. den Operator "kleiner als".) Für relationale Datenbanken bedeutet dies, dass <xref:System.Linq.Enumerable.Join%2A> eine innere Verknüpfung implementiert, d.h. eine Art von Verknüpfung, bei der nur die Objekte zurückgegeben werden, die über eine Entsprechung im anderen Datensatz verfügen. Für die <xref:System.Linq.Enumerable.GroupJoin%2A>-Methode hat bei relationalen Datenbanken kein direktes Äquivalent. Sie implementieren eine übergeordnete Menge innerer und linker äußerer Joins. Ein Left Outer Join ist eine Verknüpfung, die jedes Element der ersten (linken) Datenquelle zurückgibt, selbst wenn die andere Datenquelle keine zugehörigen Elemente enthält.  
  
 Die folgende Abbildung zeigt eine Konzeptansicht zweier Sätze sowie der Elemente innerhalb dieser Sätze, die entweder in eine innere oder linke äußere Verknüpfung einbezogen sind.  
  
 ![Zwei überlappende Kreise innen&#47;außen.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Methoden  
  
|Methodenname|Beschreibung|C#-Abfrageausdruckssyntax|Weitere Informationen|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Die Join-Methode verknüpft zwei Sequenzen auf Basis von Schlüsselauswahlfunktionen und extrahiert Wertepaare.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Die Methode verknüpft (Join) zwei Sequenzen auf Basis von Schlüsselauswahlfunktionen und gruppiert die daraus resultierenden Übereinstimmungen für die einzelnen Elemente.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Beispiele für die Abfrageausdruckssyntax
  
### Join  
  
Im folgenden Beispiel wird die `join … in … on … equals …`-Klausel verwendet, um zwei Sequenzen auf der Grundlage eines bestimmten Werts zu verknüpfen:
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

Im folgenden Beispiel wird die `join … in … on … equals … into …`-Klausel verwendet, um zwei Sequenzen auf der Grundlage eines bestimmten Werts zu verknüpfen und die resultierenden Übereinstimmungen für jedes Element zu gruppieren:
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a>Siehe auch

- <xref:System.Linq>
- [Standard Query Operators Overview (C#) (Übersicht über Standardabfrageoperatoren (C#))](./standard-query-operators-overview.md)
- [Anonyme Typen](../../classes-and-structs/anonymous-types.md)
- [Formulieren von Joins und produktübergreifenden Abfragen](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [join-Klausel](../../../language-reference/keywords/join-clause.md)
- [Join mithilfe zusammengesetzter Schlüssel](../../../linq/join-by-using-composite-keys.md)
- [Vorgehensweise: Verknüpfen des Inhalts unterschiedlicher Dateien (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Sortieren der Ergebnisse einer Join-Klausel](../../../linq/order-the-results-of-a-join-clause.md)
- [Ausführen von benutzerdefinierten Verknüpfungsoperationen](../../../linq/perform-custom-join-operations.md)
- [Ausführen von Gruppenverknüpfungen](../../../linq/perform-grouped-joins.md)
- [Ausführen innerer Verknüpfungen](../../../linq/perform-inner-joins.md)
- [Ausführen linker äußerer Verknüpfungen](../../../linq/perform-left-outer-joins.md)
- [Vorgehensweise: Auffüllen von Objektsammlungen mit Daten aus mehreren Quellen (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
