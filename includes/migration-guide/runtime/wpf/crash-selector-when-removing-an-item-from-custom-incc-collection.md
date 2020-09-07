---
ms.openlocfilehash: f50022d9a7bacd7be40fe3050ced26e7c25cf7aa
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497671"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a><span data-ttu-id="ae3d4-101">Selektor stürzt ab, wenn ein Element aus einer benutzerdefinierten INCC-Sammlung entfernt wird</span><span class="sxs-lookup"><span data-stu-id="ae3d4-101">Crash in Selector when removing an item from a custom INCC collection</span></span>

#### <a name="details"></a><span data-ttu-id="ae3d4-102">Details</span><span class="sxs-lookup"><span data-stu-id="ae3d4-102">Details</span></span>

<span data-ttu-id="ae3d4-103"><code>T:System.InvalidOperationException</code> kann in folgendem Szenario auftreten:</span><span class="sxs-lookup"><span data-stu-id="ae3d4-103">An <code>T:System.InvalidOperationException</code> can occur in the following scenario:</span></span><ul><li><span data-ttu-id="ae3d4-104">Das ItemsSource-Element für <code>T:System.Windows.Controls.Primitives.Selector</code> ist eine Sammlung mit einer benutzerdefinierten Implementierung von <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</span><span class="sxs-lookup"><span data-stu-id="ae3d4-104">The ItemsSource for a <code>T:System.Windows.Controls.Primitives.Selector</code> is a collection with a custom implementation of <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</span></span></li><li><span data-ttu-id="ae3d4-105">Das ausgewählte Element wird aus der Sammlung entfernt.</span><span class="sxs-lookup"><span data-stu-id="ae3d4-105">The selected item is removed from the collection.</span></span></li><li><span data-ttu-id="ae3d4-106"><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> weist den Wert <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code>=–1 auf, der eine unbekannte Position angibt.</span><span class="sxs-lookup"><span data-stu-id="ae3d4-106">The <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> has <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (indicating an unknown position).</span></span></li></ul><span data-ttu-id="ae3d4-107">Die Aufrufliste der Ausnahme beginnt bei „System.Windows.Threading.Dispatcher.VerifyAccess()“ in „System.Windows.DependencyObject.GetValue(DependencyProperty dp)“ in „System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element)“. Diese Ausnahme kann in .NET Framework 4.5 auftreten, wenn die Anwendung über mehr als einen Dispatcher-Thread verfügt.</span><span class="sxs-lookup"><span data-stu-id="ae3d4-107">The exception's callstack begins at System.Windows.Threading.Dispatcher.VerifyAccess() at System.Windows.DependencyObject.GetValue(DependencyProperty dp) at System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element)This exception can occur in .NET Framework 4.5 if the application has more than one Dispatcher thread.</span></span> <span data-ttu-id="ae3d4-108">In .NET Framework 4.7 kann diese Ausnahme auch bei Anwendungen mit einem einzelnen Dispatcher-Thread ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="ae3d4-108">In .NET Framework 4.7 the exception can also occur in applications with a single Dispatcher thread.</span></span> <span data-ttu-id="ae3d4-109">Dieses Problem wurde in .NET Framework 4.7.1 behoben.</span><span class="sxs-lookup"><span data-stu-id="ae3d4-109">The issue is fixed in .NET Framework 4.7.1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ae3d4-110">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="ae3d4-110">Suggestion</span></span>

<span data-ttu-id="ae3d4-111">Upgrade auf .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="ae3d4-111">Upgrade to .NET Framework 4.7.1.</span></span>

| <span data-ttu-id="ae3d4-112">Name</span><span class="sxs-lookup"><span data-stu-id="ae3d4-112">Name</span></span>    | <span data-ttu-id="ae3d4-113">Wert</span><span class="sxs-lookup"><span data-stu-id="ae3d4-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ae3d4-114">Bereich</span><span class="sxs-lookup"><span data-stu-id="ae3d4-114">Scope</span></span>   |<span data-ttu-id="ae3d4-115">Gering</span><span class="sxs-lookup"><span data-stu-id="ae3d4-115">Minor</span></span>|
|<span data-ttu-id="ae3d4-116">Version</span><span class="sxs-lookup"><span data-stu-id="ae3d4-116">Version</span></span>|<span data-ttu-id="ae3d4-117">4.7</span><span class="sxs-lookup"><span data-stu-id="ae3d4-117">4.7</span></span>|
|<span data-ttu-id="ae3d4-118">Typ</span><span class="sxs-lookup"><span data-stu-id="ae3d4-118">Type</span></span>|<span data-ttu-id="ae3d4-119">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="ae3d4-119">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ae3d4-120">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="ae3d4-120">Affected APIs</span></span>

<span data-ttu-id="ae3d4-121">Nicht über API-Analyse erkennbar.</span><span class="sxs-lookup"><span data-stu-id="ae3d4-121">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
