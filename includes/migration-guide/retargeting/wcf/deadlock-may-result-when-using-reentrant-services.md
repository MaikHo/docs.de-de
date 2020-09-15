---
ms.openlocfilehash: f61cf21f9f30662cc8e383bb3aeb5c642f1665b8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497952"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a><span data-ttu-id="fd35a-101">Bei der Verwendung von Eintrittsinvarianzdiensten können Deadlocks auftreten</span><span class="sxs-lookup"><span data-stu-id="fd35a-101">Deadlock may result when using Reentrant services</span></span>

#### <a name="details"></a><span data-ttu-id="fd35a-102">Details</span><span class="sxs-lookup"><span data-stu-id="fd35a-102">Details</span></span>

<span data-ttu-id="fd35a-103">Ein Deadlock kann zu einem Eintrittsinvarianzdienst führen, der Instanzen des Diensts auf jeweils einen Ausführungsthread beschränkt.</span><span class="sxs-lookup"><span data-stu-id="fd35a-103">A deadlock may result in a Reentrant service, which restricts instances of the service to one thread of execution at a time.</span></span> <span data-ttu-id="fd35a-104">Dienste, die anfällig für dieses Problem sind, verfügen über das folgende <xref:System.ServiceModel.ServiceBehaviorAttribute> in ihrem Code:</span><span class="sxs-lookup"><span data-stu-id="fd35a-104">Services prone to encounter this problem will have the following <xref:System.ServiceModel.ServiceBehaviorAttribute> in their code:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a><span data-ttu-id="fd35a-105">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="fd35a-105">Suggestion</span></span>

<span data-ttu-id="fd35a-106">Dieses Problem können Sie wie folgt beheben:</span><span class="sxs-lookup"><span data-stu-id="fd35a-106">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="fd35a-107">Legen Sie den Parallelitätsmodus des Diensts auf <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> oder <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> fest.</span><span class="sxs-lookup"><span data-stu-id="fd35a-107">Set the service's concurrency mode to <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> or <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fd35a-108">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="fd35a-108">For example:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- <span data-ttu-id="fd35a-109">Installieren Sie das neueste Update für .NET Framework 4.6.2, oder führen Sie ein Upgrade auf eine höhere Version von .NET Framework durch.</span><span class="sxs-lookup"><span data-stu-id="fd35a-109">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="fd35a-110">Dies deaktiviert die Weitergabe von <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd35a-110">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fd35a-111">Dieses Verhalten kann konfiguriert werden. Es entspricht dem Hinzufügen der folgenden App-Einstellung zu Ihrer Konfigurationsdatei:</span><span class="sxs-lookup"><span data-stu-id="fd35a-111">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

<span data-ttu-id="fd35a-112">Der Wert `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` darf für Reentrant-Dienste nicht auf `false` festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="fd35a-112">The value of `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` should never be set to `false` for Reentrant services.</span></span>

| <span data-ttu-id="fd35a-113">name</span><span class="sxs-lookup"><span data-stu-id="fd35a-113">Name</span></span>    | <span data-ttu-id="fd35a-114">Wert</span><span class="sxs-lookup"><span data-stu-id="fd35a-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fd35a-115">Bereich</span><span class="sxs-lookup"><span data-stu-id="fd35a-115">Scope</span></span>   | <span data-ttu-id="fd35a-116">Gering</span><span class="sxs-lookup"><span data-stu-id="fd35a-116">Minor</span></span>       |
| <span data-ttu-id="fd35a-117">Version</span><span class="sxs-lookup"><span data-stu-id="fd35a-117">Version</span></span> | <span data-ttu-id="fd35a-118">4.6.2</span><span class="sxs-lookup"><span data-stu-id="fd35a-118">4.6.2</span></span>       |
| <span data-ttu-id="fd35a-119">Typ</span><span class="sxs-lookup"><span data-stu-id="fd35a-119">Type</span></span>    | <span data-ttu-id="fd35a-120">Neuzuweisung</span><span class="sxs-lookup"><span data-stu-id="fd35a-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fd35a-121">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="fd35a-121">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>
