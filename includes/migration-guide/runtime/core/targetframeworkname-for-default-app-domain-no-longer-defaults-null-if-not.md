---
ms.openlocfilehash: 4e685722271a8079e727ea9c2e0e501f68b30fc9
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497300"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a><span data-ttu-id="227b8-101">TargetFrameworkName für die Standardanwendungsdomäne erhält nicht mehr standardmäßig den Wert NULL, wenn kein Wert festgelegt wurde</span><span class="sxs-lookup"><span data-stu-id="227b8-101">TargetFrameworkName for default app domain no longer defaults to null if not set</span></span>

#### <a name="details"></a><span data-ttu-id="227b8-102">Details</span><span class="sxs-lookup"><span data-stu-id="227b8-102">Details</span></span>

<span data-ttu-id="227b8-103"><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> erhielt bereits in der Standardanwendungsdomäne den Wert NULL, sofern kein Wert explizit festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="227b8-103">The <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> was previously null in the default app domain, unless it was explicitly set.</span></span> <span data-ttu-id="227b8-104">Ab Version 4.6 weist die <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>-Eigenschaft für die Standardanwendungsdomäne einen Standardwert auf, der von TargetFrameworkAttribute (sofern vorhanden) abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="227b8-104">Beginning in 4.6, the <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> property for the default app domain will have a default value derived from the TargetFrameworkAttribute (if one is present).</span></span> <span data-ttu-id="227b8-105">Nicht standardmäßige Anwendungsdomänen erben ihr <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> weiterhin von der Standardanwendungsdomäne (die in Version 4.6 nicht standardmäßig auf NULL festgelegt ist), sofern sie nicht explizit außer Kraft gesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="227b8-105">Non-default app domains will continue to inherit their <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> from the default app domain (which will not default to null in 4.6) unless it is explicitly overridden.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="227b8-106">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="227b8-106">Suggestion</span></span>

<span data-ttu-id="227b8-107">Der Code sollte aktualisiert werden, um nicht davon abhängig zu sein, dass <xref:System.AppDomainSetup.TargetFrameworkName> standardmäßig NULL verwendet.</span><span class="sxs-lookup"><span data-stu-id="227b8-107">Code should be updated to not depend on <xref:System.AppDomainSetup.TargetFrameworkName> defaulting to null.</span></span> <span data-ttu-id="227b8-108">Wenn es erforderlich ist, dass diese Eigenschaft weiterhin zu NULL ausgewertet wird, kann dieser Wert explizit festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="227b8-108">If it is required that this property continue to evaluate to null, it can be explicitly set to that value.</span></span>

| <span data-ttu-id="227b8-109">name</span><span class="sxs-lookup"><span data-stu-id="227b8-109">Name</span></span>    | <span data-ttu-id="227b8-110">Wert</span><span class="sxs-lookup"><span data-stu-id="227b8-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="227b8-111">Bereich</span><span class="sxs-lookup"><span data-stu-id="227b8-111">Scope</span></span>   |<span data-ttu-id="227b8-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="227b8-112">Edge</span></span>|
|<span data-ttu-id="227b8-113">Version</span><span class="sxs-lookup"><span data-stu-id="227b8-113">Version</span></span>|<span data-ttu-id="227b8-114">4.6</span><span class="sxs-lookup"><span data-stu-id="227b8-114">4.6</span></span>|
|<span data-ttu-id="227b8-115">Typ</span><span class="sxs-lookup"><span data-stu-id="227b8-115">Type</span></span>|<span data-ttu-id="227b8-116">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="227b8-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="227b8-117">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="227b8-117">Affected APIs</span></span>

- <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.AppDomainSetup.TargetFrameworkName`

-->
