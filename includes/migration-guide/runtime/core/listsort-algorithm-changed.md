---
ms.openlocfilehash: 09bd2c6312493f8b6369d05d8f1c4e88e4c05ece
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497027"
---
### <a name="listsort-algorithm-changed"></a><span data-ttu-id="7c9ad-101">Der List.Sort-Algorithmus wurde geändert</span><span class="sxs-lookup"><span data-stu-id="7c9ad-101">List.Sort algorithm changed</span></span>

#### <a name="details"></a><span data-ttu-id="7c9ad-102">Details</span><span class="sxs-lookup"><span data-stu-id="7c9ad-102">Details</span></span>

<span data-ttu-id="7c9ad-103">Ab .NET Framework 4.5 wird als Sortieralgorithmus von <xref:System.Collections.Generic.List%601?displayProperty=fullName> nicht mehr Quicksort, sondern Introsort verwendet.</span><span class="sxs-lookup"><span data-stu-id="7c9ad-103">Beginning in .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort algorithm has changed (to be an introspective sort instead of a quick sort).</span></span> <span data-ttu-id="7c9ad-104">Der Sortieralgorithmus von <xref:System.Collections.Generic.List%601?displayProperty=fullName> war noch nie stabil. Nun treten jedoch möglicherweise bei Sortiervorgängen in anderen Szenarios Instabilitäten auf.</span><span class="sxs-lookup"><span data-stu-id="7c9ad-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort has never been stable, but this change may cause different scenarios to sort in unstable ways.</span></span> <span data-ttu-id="7c9ad-105">Das bedeutet, dass gleichwertige Elemente bei aufeinanderfolgenden Aufrufen der API in verschiedenen Reihenfolgen sortiert werden.</span><span class="sxs-lookup"><span data-stu-id="7c9ad-105">That simply means that equivalent items may sort in different orders in subsequent calls of the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7c9ad-106">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="7c9ad-106">Suggestion</span></span>

<span data-ttu-id="7c9ad-107">Da der alte Sortieralgorithmus ebenfalls instabil war (wenn auch in anderer Hinsicht), sollte kein Code vorhanden sein, in dem gleichwertige Element immer in einer bestimmten Reihenfolge sortiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="7c9ad-107">Because the old sort algorithm was also unstable (though in slightly different ways), there should be no code that depends on equivalent items always sorting in a particular order.</span></span> <span data-ttu-id="7c9ad-108">Wenn andere Codeinstanzen auf dieses Verhalten oder das alte Verhalten angewiesen sind, sollte dieser Code durch die Einführung einer Vergleichsfunktion aktualisiert werden, die die Elemente deterministisch in der gewünschten Reihenfolge sortiert.</span><span class="sxs-lookup"><span data-stu-id="7c9ad-108">If there are instances of code depending upon that and being lucky with the old behavior, that code should be updated to use a comparer that will deterministically sort the items in the desired order.</span></span>

| <span data-ttu-id="7c9ad-109">name</span><span class="sxs-lookup"><span data-stu-id="7c9ad-109">Name</span></span>    | <span data-ttu-id="7c9ad-110">Wert</span><span class="sxs-lookup"><span data-stu-id="7c9ad-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7c9ad-111">Bereich</span><span class="sxs-lookup"><span data-stu-id="7c9ad-111">Scope</span></span>   |<span data-ttu-id="7c9ad-112">Transparent</span><span class="sxs-lookup"><span data-stu-id="7c9ad-112">Transparent</span></span>|
|<span data-ttu-id="7c9ad-113">Version</span><span class="sxs-lookup"><span data-stu-id="7c9ad-113">Version</span></span>|<span data-ttu-id="7c9ad-114">4.5</span><span class="sxs-lookup"><span data-stu-id="7c9ad-114">4.5</span></span>|
|<span data-ttu-id="7c9ad-115">Typ</span><span class="sxs-lookup"><span data-stu-id="7c9ad-115">Type</span></span>|<span data-ttu-id="7c9ad-116">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="7c9ad-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7c9ad-117">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="7c9ad-117">Affected APIs</span></span>

- <xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Generic.List`1.Sort``
- ``M:System.Collections.Generic.List`1.Sort(System.Collections.Generic.IComparer{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Comparison{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{`0})``

-->
