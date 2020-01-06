---
title: Installieren von .NET Core auf Debian 9 mit einem Paket-Manager (.NET Core)
description: Verwenden Sie einen Paket-Manager, um das .NET Core SDK und die -Runtime auf Debian 9 zu installieren.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: b8b6a3039efcc2fbd15e0c3948984086c619bd44
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74998966"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="281a6-103">Debian 9-Paket-Manager: Installieren von .NET Core</span><span class="sxs-lookup"><span data-stu-id="281a6-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="281a6-104">In diesem Artikel wird beschrieben, wie Sie mit einem Paket-Manager .NET Core auf Debian 9 installieren.</span><span class="sxs-lookup"><span data-stu-id="281a6-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span> <span data-ttu-id="281a6-105">Wenn Sie die Runtime installieren, wird die Installation der [ASP.NET Core-Runtime](#install-the-aspnet-core-runtime) empfohlen, da diese sowohl .NET Core- als auch ASP.NET Core-Runtimes umfasst.</span><span class="sxs-lookup"><span data-stu-id="281a6-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="281a6-106">Registrieren von Microsoft-Schlüsseln und -Feeds</span><span class="sxs-lookup"><span data-stu-id="281a6-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="281a6-107">Vor der Installation von .NET müssen Sie folgende Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="281a6-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="281a6-108">Registrieren Sie den Microsoft-Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="281a6-108">Register the Microsoft key</span></span>
- <span data-ttu-id="281a6-109">Registrieren Sie das Produktrepository.</span><span class="sxs-lookup"><span data-stu-id="281a6-109">register the product repository</span></span>
- <span data-ttu-id="281a6-110">Installieren Sie erforderliche Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="281a6-110">Install required dependencies</span></span>

<span data-ttu-id="281a6-111">Dies muss nur einmal pro Computer ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="281a6-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="281a6-112">Öffnen Sie ein Terminal, und führen Sie die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="281a6-112">Open a terminal and run the following commands.</span></span>

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="281a6-113">Installieren des .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="281a6-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="281a6-114">Aktualisieren Sie die zur Installation verfügbaren Produkte, und installieren Sie dann das .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="281a6-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="281a6-115">Führen Sie in Ihrem Terminal die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="281a6-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="281a6-116">Installieren der ASP.NET Core-Runtime</span><span class="sxs-lookup"><span data-stu-id="281a6-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="281a6-117">Aktualisieren Sie die zur Installation verfügbaren Produkte, und installieren Sie dann die ASP.NET-Runtime.</span><span class="sxs-lookup"><span data-stu-id="281a6-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="281a6-118">Führen Sie in Ihrem Terminal die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="281a6-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="281a6-119">Installieren der .NET Core-Runtime</span><span class="sxs-lookup"><span data-stu-id="281a6-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="281a6-120">Aktualisieren Sie die zur Installation verfügbaren Produkte, und installieren Sie dann die .NET Core-Runtime.</span><span class="sxs-lookup"><span data-stu-id="281a6-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="281a6-121">Führen Sie in Ihrem Terminal die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="281a6-121">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="281a6-122">Installieren anderer Versionen</span><span class="sxs-lookup"><span data-stu-id="281a6-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]