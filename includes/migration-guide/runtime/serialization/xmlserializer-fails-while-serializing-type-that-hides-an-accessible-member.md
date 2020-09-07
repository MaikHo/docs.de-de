---
ms.openlocfilehash: 75c7385bceec2595683d1c0d97a7df9264e3bf0b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497296"
---
### <a name="xmlserializer-fails-while-serializing-a-type-that-hides-an-accessible-member-with-an-inaccessible-one"></a><span data-ttu-id="cc90c-101">„XmlSerializer“ schlägt während der Serialisierung eines Typs fehl, der einen verfügbaren Member mit einem nicht verfügbaren überdeckt</span><span class="sxs-lookup"><span data-stu-id="cc90c-101">XmlSerializer fails while serializing a type that hides an accessible member with an inaccessible one</span></span>

#### <a name="details"></a><span data-ttu-id="cc90c-102">Details</span><span class="sxs-lookup"><span data-stu-id="cc90c-102">Details</span></span>

<span data-ttu-id="cc90c-103">Bei der Serialisierung eines abgeleiteten Typs kann <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> fehlschlagen, wenn der Typ einen verfügbaren Member oder eine Eigenschaft enthält, die ein Feld oder eine Eigenschaft mit dem gleichen Namen ausblendet (durch das Schlüsselwort „new“), das bzw. die zuvor im Basistyp verfügbar (z.B. „public“) war.</span><span class="sxs-lookup"><span data-stu-id="cc90c-103">When serializing a derived type, the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> can fail if the type contains an inaccessible field or property that hides (via the 'new' keyword) a field or property of the same name that was previously accessible (public, for example) on the base type.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cc90c-104">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="cc90c-104">Suggestion</span></span>

<span data-ttu-id="cc90c-105">Dieses Problem kann gelöst werden, indem der neue, ausgeblendete Member für <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> zur Verfügung gestellt wird, indem es z.B. als „public“ gekennzeichnet wird. Alternativ kann das Verhalten von <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> unter 4.0 mithilfe von folgenden Konfigurationseinstellungen wiederhergestellt und das Problem somit behoben werden:</span><span class="sxs-lookup"><span data-stu-id="cc90c-105">This problem can be solved by making the new, hiding member accessible to the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> (by marking it public, for example).Alternatively, the following config setting will revert to 4.0 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> behavior, which will fix the problem:</span></span><pre><code class="lang-xml">&lt;system.xml.serialization&gt;&#13;&#10;&lt;xmlSerializer useLegacySerializerGeneration=&quot;true&quot; /&gt;&#13;&#10;&lt;/system.xml.serialization&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="cc90c-106">name</span><span class="sxs-lookup"><span data-stu-id="cc90c-106">Name</span></span>    | <span data-ttu-id="cc90c-107">Wert</span><span class="sxs-lookup"><span data-stu-id="cc90c-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cc90c-108">Bereich</span><span class="sxs-lookup"><span data-stu-id="cc90c-108">Scope</span></span>   |<span data-ttu-id="cc90c-109">Gering</span><span class="sxs-lookup"><span data-stu-id="cc90c-109">Minor</span></span>|
|<span data-ttu-id="cc90c-110">Version</span><span class="sxs-lookup"><span data-stu-id="cc90c-110">Version</span></span>|<span data-ttu-id="cc90c-111">4.5</span><span class="sxs-lookup"><span data-stu-id="cc90c-111">4.5</span></span>|
|<span data-ttu-id="cc90c-112">Typ</span><span class="sxs-lookup"><span data-stu-id="cc90c-112">Type</span></span>|<span data-ttu-id="cc90c-113">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="cc90c-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="cc90c-114">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="cc90c-114">Affected APIs</span></span>

- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)`

-->
