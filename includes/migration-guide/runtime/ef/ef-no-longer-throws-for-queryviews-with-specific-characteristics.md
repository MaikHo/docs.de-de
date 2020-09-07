---
ms.openlocfilehash: ceae6b85c14862b1b1183d01def0dda723ee0c2b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497690"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="632b5-101">Entity Framework löst für QueryViews bei bestimmten Zeichen keine Ausnahmen mehr aus</span><span class="sxs-lookup"><span data-stu-id="632b5-101">EF no longer throws for QueryViews with specific characteristics</span></span>

#### <a name="details"></a><span data-ttu-id="632b5-102">Details</span><span class="sxs-lookup"><span data-stu-id="632b5-102">Details</span></span>

<span data-ttu-id="632b5-103">Entity Framework löst keine <xref:System.StackOverflowException?displayProperty=fullName>-Ausnahme mehr aus, wenn eine App eine Abfrage ausführt, die ein QueryView-Element mit einer 0..1-Navigationseigenschaft umfasst und versucht, die verwandten Entitäten als Teil der Abfrage zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="632b5-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=fullName> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="632b5-104">(Z.B. durch Aufrufen von <code>.Include(e =&gt; e.RelatedNavProp)</code>.)</span><span class="sxs-lookup"><span data-stu-id="632b5-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="632b5-105">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="632b5-105">Suggestion</span></span>

<span data-ttu-id="632b5-106">Diese Änderung betrifft nur Code, der QueryViews mit 1-0..1-Beziehungen verwendet, wenn Abfragen ausgeführt werden, die .Include aufrufen.</span><span class="sxs-lookup"><span data-stu-id="632b5-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="632b5-107">Diese Änderung verbessert die Zuverlässigkeit und sollte für beinahe alle Apps transparent sein.</span><span class="sxs-lookup"><span data-stu-id="632b5-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="632b5-108">Falls jedoch ein unerwünschtes Verhalten auftritt, können Sie dieses Feature deaktivieren, indem Sie den folgenden Eintrag im <code>&lt;appSettings&gt;</code>-Bereich der Anwendungskonfigurationsdatei einfügen:</span><span class="sxs-lookup"><span data-stu-id="632b5-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="632b5-109">name</span><span class="sxs-lookup"><span data-stu-id="632b5-109">Name</span></span>    | <span data-ttu-id="632b5-110">Wert</span><span class="sxs-lookup"><span data-stu-id="632b5-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="632b5-111">Bereich</span><span class="sxs-lookup"><span data-stu-id="632b5-111">Scope</span></span>   |<span data-ttu-id="632b5-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="632b5-112">Edge</span></span>|
|<span data-ttu-id="632b5-113">Version</span><span class="sxs-lookup"><span data-stu-id="632b5-113">Version</span></span>|<span data-ttu-id="632b5-114">4.5.2</span><span class="sxs-lookup"><span data-stu-id="632b5-114">4.5.2</span></span>|
|<span data-ttu-id="632b5-115">Typ</span><span class="sxs-lookup"><span data-stu-id="632b5-115">Type</span></span>|<span data-ttu-id="632b5-116">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="632b5-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="632b5-117">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="632b5-117">Affected APIs</span></span>

<span data-ttu-id="632b5-118">Nicht über API-Analyse erkennbar.</span><span class="sxs-lookup"><span data-stu-id="632b5-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
