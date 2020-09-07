---
ms.openlocfilehash: 05f60978f5380c406c43aa98ded0c812b1d50694
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496430"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Enumerable.Empty&lt;TResult&gt; gibt immer die zwischengespeicherte Instanz zurück

#### <a name="details"></a>Details

Ab .NET Framework 4.5 gibt <xref:System.Linq.Enumerable.Empty%60%601> eine zwischengespeicherte interne Instanz von <xref:System.Collections.Generic.IEnumerable%601> zurück. Zuvor zwischenspeicherte <xref:System.Linq.Enumerable.Empty%60%601> beim Aufruf der API eine leere <xref:System.Collections.Generic.IEnumerable%601>-Instanz, wodurch unter bestimmten Umständen, durch die <xref:System.Linq.Enumerable.Empty%60%601> schnell und gleichzeitig aufgerufen wurde, verschiedene Instanzen des Typs für unterschiedliche Aufrufe der API zurückgegeben werden konnten.

#### <a name="suggestion"></a>Vorschlag

Da das vorherige Verhalten nicht deterministisch war, ist es unwahrscheinlich, dass der Code davon abhängig ist. Jedoch für den unwahrscheinlichen Fall, dass leere Enumerables verglichen werden und dabei erwartet wird, dass diese gelegentlich ungleich sind, sollten explizite leere Arrays erstellt werden (<code>new T[0]</code>), anstatt <xref:System.Linq.Enumerable.Empty%60%601> zu verwenden.

| name    | Wert       |
|:--------|:------------|
| Bereich   |Microsoft Edge|
|Version|4.5|
|Typ|Laufzeit|

#### <a name="affected-apis"></a>Betroffene APIs

- <xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Linq.Enumerable.Empty``1``

-->
