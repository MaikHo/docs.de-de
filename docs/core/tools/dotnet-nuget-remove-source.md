---
title: Befehl „dotnet nuget remove source“
description: Mit dem Befehl „dotnet nuget remove source“ wird eine vorhandene Quelle aus Ihren NuGet-Konfigurationsdateien entfernt.
ms.date: 03/20/2020
ms.openlocfilehash: 65c97b98ab50121fb4ebc184da65f021c16e0634
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148465"
---
# <a name="dotnet-nuget-remove-source"></a><span data-ttu-id="28783-103">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="28783-103">dotnet nuget remove source</span></span>

<span data-ttu-id="28783-104">**Dieser Artikel gilt für:** ✔️ .NET Core 3.1.200 SDK und neuere Versionen</span><span class="sxs-lookup"><span data-stu-id="28783-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="28783-105">Name</span><span class="sxs-lookup"><span data-stu-id="28783-105">Name</span></span>

<span data-ttu-id="28783-106">`dotnet nuget remove source`: Entfernen einer NuGet-Quelle.</span><span class="sxs-lookup"><span data-stu-id="28783-106">`dotnet nuget remove source` - Remove a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="28783-107">Übersicht</span><span class="sxs-lookup"><span data-stu-id="28783-107">Synopsis</span></span>

```dotnetcli
dotnet nuget remove source <NAME> [--configfile]
dotnet nuget remove source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="28783-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="28783-108">Description</span></span>

<span data-ttu-id="28783-109">Mit dem Befehl `dotnet nuget remove source` wird eine vorhandene Quelle aus Ihren NuGet-Konfigurationsdateien entfernt.</span><span class="sxs-lookup"><span data-stu-id="28783-109">The `dotnet nuget remove source` command removes an existing source from your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="28783-110">Argumente</span><span class="sxs-lookup"><span data-stu-id="28783-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="28783-111">Name der Quelle.</span><span class="sxs-lookup"><span data-stu-id="28783-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="28783-112">Optionen</span><span class="sxs-lookup"><span data-stu-id="28783-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="28783-113">Die NuGet-Konfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="28783-113">The NuGet configuration file.</span></span> <span data-ttu-id="28783-114">Sofern angegeben, werden nur die Einstellungen aus dieser Datei verwendet.</span><span class="sxs-lookup"><span data-stu-id="28783-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="28783-115">Falls nicht angegeben, wird die Hierarchie der Konfigurationsdateien aus dem aktuellen Verzeichnis verwendet.</span><span class="sxs-lookup"><span data-stu-id="28783-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="28783-116">Weitere Informationen finden Sie unter [Gängige NuGet-Konfigurationen](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="28783-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="28783-117">Beispiele</span><span class="sxs-lookup"><span data-stu-id="28783-117">Examples</span></span>

- <span data-ttu-id="28783-118">Entfernen einer Quelle mit dem Namen `mySource`:</span><span class="sxs-lookup"><span data-stu-id="28783-118">Remove a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="28783-119">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="28783-119">See also</span></span>

- [<span data-ttu-id="28783-120">Paketquellenabschnitte in NuGet.config-Dateien</span><span class="sxs-lookup"><span data-stu-id="28783-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="28783-121">Befehl „sources“ (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="28783-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)