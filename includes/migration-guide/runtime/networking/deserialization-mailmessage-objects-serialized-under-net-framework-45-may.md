---
ms.openlocfilehash: 2c44c2e1658f8de556d3f7222de3fa6d4594163a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497793"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="a300a-101">Die Deserialisierung von MailMessage-Objekten, die unter .NET Framework 4.5 serialisiert wurden, kann möglicherweise fehlschlagen</span><span class="sxs-lookup"><span data-stu-id="a300a-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

#### <a name="details"></a><span data-ttu-id="a300a-102">Details</span><span class="sxs-lookup"><span data-stu-id="a300a-102">Details</span></span>

<span data-ttu-id="a300a-103">Ab .NET Framework 4.5 können <xref:System.Web.Mail.MailMessage>-Objekte keine Zeichen mehr enthalten, die keine ASCII-Zeichen sind.</span><span class="sxs-lookup"><span data-stu-id="a300a-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="a300a-104">In .NET Framework 4 werden nur ASCII-Zeichen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a300a-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="a300a-105"><xref:System.Web.Mail.MailMessage>-Objekte, die Zeichen enthalten, bei denen es sich nicht um ASCII-Zeichen handelt, und unter .NET Framework 4.5 oder höher serialisiert werden, können unter .NET Framework 4 nicht deserialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="a300a-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a300a-106">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="a300a-106">Suggestion</span></span>

<span data-ttu-id="a300a-107">Vergewissern Sie sich, dass Ihr Code die Behandlung von Ausnahmen umfasst, wenn Sie ein <xref:System.Web.Mail.MailMessage>-Objekt deserialisieren.</span><span class="sxs-lookup"><span data-stu-id="a300a-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>

| <span data-ttu-id="a300a-108">name</span><span class="sxs-lookup"><span data-stu-id="a300a-108">Name</span></span>    | <span data-ttu-id="a300a-109">Wert</span><span class="sxs-lookup"><span data-stu-id="a300a-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a300a-110">Bereich</span><span class="sxs-lookup"><span data-stu-id="a300a-110">Scope</span></span>   |<span data-ttu-id="a300a-111">Gering</span><span class="sxs-lookup"><span data-stu-id="a300a-111">Minor</span></span>|
|<span data-ttu-id="a300a-112">Version</span><span class="sxs-lookup"><span data-stu-id="a300a-112">Version</span></span>|<span data-ttu-id="a300a-113">4.5</span><span class="sxs-lookup"><span data-stu-id="a300a-113">4.5</span></span>|
|<span data-ttu-id="a300a-114">Typ</span><span class="sxs-lookup"><span data-stu-id="a300a-114">Type</span></span>|<span data-ttu-id="a300a-115">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="a300a-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="a300a-116">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="a300a-116">Affected APIs</span></span>

- <xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.Mail.MailMessage`

-->
