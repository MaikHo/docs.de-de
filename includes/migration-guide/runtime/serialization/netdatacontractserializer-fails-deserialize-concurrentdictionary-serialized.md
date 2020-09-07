---
ms.openlocfilehash: 6c120f155660863ce5ae3cf5bd81ea858a68ef8d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497730"
---
### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a><span data-ttu-id="fc1b9-101">„NetDataContractSerializer“ kann eine ConcurrentDictionary-Klasse nicht deserialisieren, die mit einer anderen Version von .NET serialisiert wurde</span><span class="sxs-lookup"><span data-stu-id="fc1b9-101">NetDataContractSerializer fails to deserialize a ConcurrentDictionary serialized with a different .NET version</span></span>

#### <a name="details"></a><span data-ttu-id="fc1b9-102">Details</span><span class="sxs-lookup"><span data-stu-id="fc1b9-102">Details</span></span>

<span data-ttu-id="fc1b9-103">Programmbedingt kann <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> daher nur verwendet werden, wenn sowohl der Endpunkt für die Serialisierung als auch der Endpunkt für die Deserialisierung den gleichen CLR-Typ aufweisen.</span><span class="sxs-lookup"><span data-stu-id="fc1b9-103">By design, the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="fc1b9-104">Deshalb kann nicht gewährleistet werden, dass ein Objekt, das mit einer Version von .NET Framework serialisiert wurde, mit einer anderen Version deserialisiert werden kann. <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="fc1b9-104">Therefore, it is not guaranteed that an object serialized with one version of the .NET Framework can be deserialized by a different version.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName></span></span> <span data-ttu-id="fc1b9-105">ist ein Typ, bei dem bekannt ist, dass die Deserialisierung nicht korrekt durchgeführt wird, wenn dieser mit .NET Framework 4.5 oder früher serialisiert wurde und mit .NET Framework 4.5.1 oder höher deserialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="fc1b9-105">is a type that is known to not to deserialize correctly if serialized with the .NET Framework 4.5 or earlier and deserialized with the .NET Framework 4.5.1 or later.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fc1b9-106">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="fc1b9-106">Suggestion</span></span>

<span data-ttu-id="fc1b9-107">Es gibt einige Möglichkeiten, dieses Problem zu umgehen:</span><span class="sxs-lookup"><span data-stu-id="fc1b9-107">There are a number of possible work-arounds for this issue:</span></span><ul><li><span data-ttu-id="fc1b9-108">Führen Sie ein Upgrade durch, sodass der serialisierende Computer ebenfalls .NET Framework 4.5.1 verwendet.</span><span class="sxs-lookup"><span data-stu-id="fc1b9-108">Upgrade the serializing computer to use the .NET Framework 4.5.1, as well.</span></span></li><li><span data-ttu-id="fc1b9-109">Verwenden Sie <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> statt <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>, da dadurch nicht genau die gleichen CLR-Typen bei den Endpunkten für die Serialisierung und Deserialisierung erwartet werden.</span><span class="sxs-lookup"><span data-stu-id="fc1b9-109">Use <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> instead of <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> as this does not expect the exact same CLR types at both serializing and deserializing ends.</span></span></li><li><span data-ttu-id="fc1b9-110">Verwenden Sie <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> statt <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>, da dieses Element nicht die Unterbrechung zwischen 4.5 und 4.5.1 aufweist.</span><span class="sxs-lookup"><span data-stu-id="fc1b9-110">Use <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> instead of <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> since it does not exhibit this particular 4.5-&gt;4.5.1 break.</span></span></li></ul>

| <span data-ttu-id="fc1b9-111">name</span><span class="sxs-lookup"><span data-stu-id="fc1b9-111">Name</span></span>    | <span data-ttu-id="fc1b9-112">Wert</span><span class="sxs-lookup"><span data-stu-id="fc1b9-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fc1b9-113">Bereich</span><span class="sxs-lookup"><span data-stu-id="fc1b9-113">Scope</span></span>   |<span data-ttu-id="fc1b9-114">Gering</span><span class="sxs-lookup"><span data-stu-id="fc1b9-114">Minor</span></span>|
|<span data-ttu-id="fc1b9-115">Version</span><span class="sxs-lookup"><span data-stu-id="fc1b9-115">Version</span></span>|<span data-ttu-id="fc1b9-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="fc1b9-116">4.5.1</span></span>|
|<span data-ttu-id="fc1b9-117">Typ</span><span class="sxs-lookup"><span data-stu-id="fc1b9-117">Type</span></span>|<span data-ttu-id="fc1b9-118">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="fc1b9-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="fc1b9-119">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="fc1b9-119">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)`

-->
