---
ms.openlocfilehash: 0d38e2177377e7e9ea911071eb65aa13aa1f5900
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497420"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a><span data-ttu-id="592fe-101">Die App-Einstellung „dataAnnotations:dataTypeAttribute:disableRegEx“ ist in .NET Framework 4.7.2 standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="592fe-101">"dataAnnotations:dataTypeAttribute:disableRegEx" app setting is on by default in .NET Framework 4.7.2</span></span>

#### <a name="details"></a><span data-ttu-id="592fe-102">Details</span><span class="sxs-lookup"><span data-stu-id="592fe-102">Details</span></span>

<span data-ttu-id="592fe-103">In .NET Framework 4.6.1 wurde die App-Einstellung <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> eingeführt, mir der Benutzer die Verwendung regulärer Ausdrücke in Datentypattributen (z.B. <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> und <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>) deaktivieren können.</span><span class="sxs-lookup"><span data-stu-id="592fe-103">In .NET Framework 4.6.1, an app setting (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) was introduced that allows users to disable the use of regular expressions in data type attributes (such as <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>, and <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="592fe-104">So können Sicherheitsrisiken wie mögliche Denial-of-Service-Angriffe mit bestimmten regulären Ausdrücken gesenkt werden.</span><span class="sxs-lookup"><span data-stu-id="592fe-104">This helps to reduce security vulnerability such as avoiding the possibility of a Denial of Service attack using specific regular expressions.</span></span><br/><span data-ttu-id="592fe-105">In .NET Framework 4.6.1 war diese App-Einstellung zur Verwendung von regulären Ausdrücken standardmäßig auf <code>false</code> festgelegt.</span><span class="sxs-lookup"><span data-stu-id="592fe-105">In .NET Framework 4.6.1, this app setting to disable RegEx usage was set to <code>false</code> by default.</span></span> <span data-ttu-id="592fe-106">Ab .NET Framework 4.7.2 ist dieser Konfigurationsparameter standardmäßig auf <code>true</code> festgelegt, um Sicherheitsrisiken für Webanwendungen für .NET Framework 4.7.2 und höher weiter zu senken.</span><span class="sxs-lookup"><span data-stu-id="592fe-106">Starting with .NET Framework 4.7.2, this config switch is set to <code>true</code> by default to further reduce secure vulnerability for web applications that target .NET Framework 4.7.2 and above.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="592fe-107">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="592fe-107">Suggestion</span></span>

<span data-ttu-id="592fe-108">Wenn regulärer Ausdrücke in Ihrer Webanwendung nach dem Upgrade auf .NET Framework 4.7.2 nicht mehr funktionieren, können Sie den Wert der Einstellung <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> in <code>false</code> ändern, um wieder das alte Verhalten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="592fe-108">If you find that regular expressions in your web application do not work after upgrading to .NET Framework 4.7.2, you can update the value of the <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> setting to <code>false</code> to revert to the previous behavior.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="592fe-109">name</span><span class="sxs-lookup"><span data-stu-id="592fe-109">Name</span></span>    | <span data-ttu-id="592fe-110">Wert</span><span class="sxs-lookup"><span data-stu-id="592fe-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="592fe-111">Bereich</span><span class="sxs-lookup"><span data-stu-id="592fe-111">Scope</span></span>   |<span data-ttu-id="592fe-112">Gering</span><span class="sxs-lookup"><span data-stu-id="592fe-112">Minor</span></span>|
|<span data-ttu-id="592fe-113">Version</span><span class="sxs-lookup"><span data-stu-id="592fe-113">Version</span></span>|<span data-ttu-id="592fe-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="592fe-114">4.7.2</span></span>|
|<span data-ttu-id="592fe-115">Typ</span><span class="sxs-lookup"><span data-stu-id="592fe-115">Type</span></span>|<span data-ttu-id="592fe-116">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="592fe-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="592fe-117">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="592fe-117">Affected APIs</span></span>

<span data-ttu-id="592fe-118">Nicht über API-Analyse erkennbar.</span><span class="sxs-lookup"><span data-stu-id="592fe-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
