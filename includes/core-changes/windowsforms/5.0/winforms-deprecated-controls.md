---
ms.openlocfilehash: d3bfeda8309af83d8e4199999ed91263a17caeea
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556183"
---
### <a name="removed-status-bar-controls"></a><span data-ttu-id="862de-101">Statusleisten-Steuerelement wurde entfernt</span><span class="sxs-lookup"><span data-stu-id="862de-101">Removed status bar controls</span></span>

<span data-ttu-id="862de-102">Ab .NET 5.0 sind einige Windows Forms-Steuerelemente nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="862de-102">Starting in .NET 5.0, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="862de-103">Änderungsbeschreibung</span><span class="sxs-lookup"><span data-stu-id="862de-103">Change description</span></span>

<span data-ttu-id="862de-104">Ab .NET 5.0 sind einige Windows Forms-Steuerelemente für Statusleistenfunktionen nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="862de-104">Starting with .NET 5.0, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="862de-105">Ersatzsteuerelemente, die ein besseres Design und eine umfassendere Unterstützung bieten, wurden in .NET Framework 2.0 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="862de-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="862de-106">Die veralteten Steuerelemente wurden zwar bereits aus den Designer-Toolboxen entfernt, konnten aber weiterhin verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="862de-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="862de-107">Nun wurden sie vollständig entfernt.</span><span class="sxs-lookup"><span data-stu-id="862de-107">Now, they have been completely removed.</span></span>

<span data-ttu-id="862de-108">Die folgenden Typen stehen nicht mehr länger zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="862de-108">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

#### <a name="version-introduced"></a><span data-ttu-id="862de-109">Eingeführt in Version</span><span class="sxs-lookup"><span data-stu-id="862de-109">Version introduced</span></span>

<span data-ttu-id="862de-110">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="862de-110">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="862de-111">Empfohlene Aktion</span><span class="sxs-lookup"><span data-stu-id="862de-111">Recommended action</span></span>

<span data-ttu-id="862de-112">Wechseln Sie zu den Ersetzungs-APIs für diese Steuerelemente und ihre Szenarios:</span><span class="sxs-lookup"><span data-stu-id="862de-112">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="862de-113">Altes Steuerelement (API)</span><span class="sxs-lookup"><span data-stu-id="862de-113">Old Control (API)</span></span> | <span data-ttu-id="862de-114">Empfohlener Ersatz</span><span class="sxs-lookup"><span data-stu-id="862de-114">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="862de-115">StatusBar</span><span class="sxs-lookup"><span data-stu-id="862de-115">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="862de-116">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="862de-116">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

#### <a name="category"></a><span data-ttu-id="862de-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="862de-117">Category</span></span>

<span data-ttu-id="862de-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="862de-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="862de-119">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="862de-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle` 

-->
