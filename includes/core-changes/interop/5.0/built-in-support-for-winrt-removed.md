---
ms.openlocfilehash: d21b2e092d460fdfc367d0f490228ed44ad5c6cc
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365646"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a><span data-ttu-id="caad8-101">Integrierte Unterstützung für WinRT wird aus .NET entfernt</span><span class="sxs-lookup"><span data-stu-id="caad8-101">Built-in support for WinRT is removed from .NET</span></span>

<span data-ttu-id="caad8-102">Die integrierte Unterstützung für die Nutzung von [WinRT-APIs (Windows Runtime)](/uwp/winrt-cref/winrt-type-system) in .NET wird entfernt.</span><span class="sxs-lookup"><span data-stu-id="caad8-102">Built-in support for consumption of [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) APIs in .NET is removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="caad8-103">Eingeführt in Version</span><span class="sxs-lookup"><span data-stu-id="caad8-103">Version introduced</span></span>

<span data-ttu-id="caad8-104">Version 5.0 Vorschau 6</span><span class="sxs-lookup"><span data-stu-id="caad8-104">5.0 Preview 6</span></span>

#### <a name="change-description"></a><span data-ttu-id="caad8-105">Änderungsbeschreibung</span><span class="sxs-lookup"><span data-stu-id="caad8-105">Change description</span></span>

<span data-ttu-id="caad8-106">Zuvor konnte CoreCLR [Windows-Metadatendateien (WinMD)](/uwp/winrt-cref/winmd-files) verwenden, um WinRT-Typen zu aktivieren und zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="caad8-106">Previously, CoreCLR could consume [Windows metadata (WinMD) files](/uwp/winrt-cref/winmd-files) to active and consume WinRT types.</span></span> <span data-ttu-id="caad8-107">Ab .NET 5.0 kann CoreCLR WinMD-Dateien nicht mehr direkt nutzen.</span><span class="sxs-lookup"><span data-stu-id="caad8-107">Starting in .NET 5.0, CoreCLR can no longer consume WinMD files directly.</span></span>

<span data-ttu-id="caad8-108">Wenn Sie versuchen, auf eine nicht unterstützte Assembly zu verweisen, wird eine <xref:System.IO.FileNotFoundException> zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="caad8-108">If you attempt to reference an unsupported assembly, you'll get a <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="caad8-109">Wenn Sie eine WinRT-Klasse aktivieren, wird eine <xref:System.PlatformNotSupportedException> zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="caad8-109">If you activate a WinRT class, you'll get a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="caad8-110">Dieser Breaking Change wurde aus den folgenden Gründen vorgenommen:</span><span class="sxs-lookup"><span data-stu-id="caad8-110">This breaking change was made for the following reasons:</span></span>

- <span data-ttu-id="caad8-111">WinRT kann jetzt unabhängig von der .NET-Runtime entwickelt und verbessert werden.</span><span class="sxs-lookup"><span data-stu-id="caad8-111">So WinRT can be developed and improved separately from the .NET runtime.</span></span>
- <span data-ttu-id="caad8-112">Außerdem dient dies der Symmetrie mit Interopsystemen, die für andere Betriebssysteme wie iOS und Android bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="caad8-112">For symmetry with interop systems provided for other operating systems, such as iOS and Android.</span></span>
- <span data-ttu-id="caad8-113">Andere .NET-Features wie C#-Features, IL-Verknüpfungen (Intermediate Language) und die AOT-Kompilierung (Ahead-of-Time) können genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="caad8-113">To take advantage of other .NET features, such as C# features, intermediate language (IL) linking, and ahead-of-time (AOT) compilation.</span></span>
- <span data-ttu-id="caad8-114">Die .NET-Runtimecodebasis kann vereinfacht werden.</span><span class="sxs-lookup"><span data-stu-id="caad8-114">To simplify the .NET runtime codebase.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="caad8-115">Empfohlene Aktion</span><span class="sxs-lookup"><span data-stu-id="caad8-115">Recommended action</span></span>

- <span data-ttu-id="caad8-116">Entfernen Sie Verweise auf das [Microsoft.Windows.SDK.Contracts-Paket](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts), und ersetzen Sie sie durch Verweise auf das [Microsoft.Windows.SDK.NET-Paket](https://www.nuget.org/packages/microsoft.windows.sdk.net).</span><span class="sxs-lookup"><span data-stu-id="caad8-116">Remove references to the [Microsoft.Windows.SDK.Contracts package](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) and replace them with references to the [Microsoft.Windows.SDK.NET package](https://www.nuget.org/packages/microsoft.windows.sdk.net).</span></span>

- <span data-ttu-id="caad8-117">Verwenden Sie die [C#/WinRT](/windows/uwp/csharp-winrt/)-Toolkette, um WinRT-APIs und Typen in .NET 5.0 und höheren Versionen zu generieren oder anzupassen.</span><span class="sxs-lookup"><span data-stu-id="caad8-117">Use the [C#/WinRT](/windows/uwp/csharp-winrt/) tool chain to generate or customize WinRT APIs and types in .NET 5.0 and later versions.</span></span>

#### <a name="category"></a><span data-ttu-id="caad8-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="caad8-118">Category</span></span>

<span data-ttu-id="caad8-119">Interop</span><span class="sxs-lookup"><span data-stu-id="caad8-119">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="caad8-120">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="caad8-120">Affected APIs</span></span>

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->