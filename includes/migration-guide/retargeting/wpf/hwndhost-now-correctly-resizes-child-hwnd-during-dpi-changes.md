---
ms.openlocfilehash: 77e231f8ef1dde8a263b8622311099a4a404062d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606379"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a><span data-ttu-id="3af21-101">HwndHost ändert nun die Größe eines untergeordneten HWND bei DPI-Änderungen ordnungsgemäß</span><span class="sxs-lookup"><span data-stu-id="3af21-101">HwndHost now correctly resizes child-HWND during DPI changes</span></span>

#### <a name="details"></a><span data-ttu-id="3af21-102">Details</span><span class="sxs-lookup"><span data-stu-id="3af21-102">Details</span></span>

<span data-ttu-id="3af21-103">Wenn WPF im PMA-Modus (Per-Monitor Aware) ausgeführt wurde, wurde in .NET Framework 4.7.2 und früheren Versionen die Größe von in <xref:System.Windows.Interop.HwndHost> gehosteten Steuerelementen nach DPI-Änderungen, also beispielsweise beim Verschieben von Anwendungen von einem Monitor zu einem anderen, nicht ordnungsgemäß geändert.</span><span class="sxs-lookup"><span data-stu-id="3af21-103">In .NET Framework 4.7.2 and earlier versions, when WPF was run in Per-Monitor Aware mode, controls hosted within <xref:System.Windows.Interop.HwndHost> were not sized correctly after DPI changes, such as when moving applications from one monitor to another.</span></span> <span data-ttu-id="3af21-104">Mit dieser Korrektur wird sichergestellt, dass die Größe von gehosteten Steuerelementen ordnungsgemäß geändert wird.</span><span class="sxs-lookup"><span data-stu-id="3af21-104">This fix ensures that hosted controls are sized appropriately.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3af21-105">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="3af21-105">Suggestion</span></span>

<span data-ttu-id="3af21-106">Damit die Anwendung von diesen Änderungen profitiert, muss sie unter .NET Framework 4.7.2 oder höher ausgeführt werden. Zudem muss dieses Verhalten aktiviert werden, indem der folgende [AppContext-Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) im `<runtime>`-Abschnitt der Konfigurationsdatei der Anwendung wie im folgenden Beispiel auf `false` festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="3af21-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later, and it must opt-in to this behavior by setting the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) in the `<runtime>` section of the app config file to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="3af21-107">name</span><span class="sxs-lookup"><span data-stu-id="3af21-107">Name</span></span>    | <span data-ttu-id="3af21-108">Wert</span><span class="sxs-lookup"><span data-stu-id="3af21-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3af21-109">Bereich</span><span class="sxs-lookup"><span data-stu-id="3af21-109">Scope</span></span>   | <span data-ttu-id="3af21-110">Hauptversion</span><span class="sxs-lookup"><span data-stu-id="3af21-110">Major</span></span>       |
| <span data-ttu-id="3af21-111">Version</span><span class="sxs-lookup"><span data-stu-id="3af21-111">Version</span></span> | <span data-ttu-id="3af21-112">4.8</span><span class="sxs-lookup"><span data-stu-id="3af21-112">4.8</span></span>         |
| <span data-ttu-id="3af21-113">Typ</span><span class="sxs-lookup"><span data-stu-id="3af21-113">Type</span></span>    | <span data-ttu-id="3af21-114">Neuzuweisung</span><span class="sxs-lookup"><span data-stu-id="3af21-114">Retargeting</span></span> |
