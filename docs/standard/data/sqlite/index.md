---
title: Übersicht
ms.date: 12/13/2019
description: Eine Übersicht über Microsoft.Data.Sqlite
ms.openlocfilehash: 7c952848f7e7ea04f11fe9340f77a1f376a1be07
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552439"
---
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="36e76-103">Übersicht über Microsoft.Data.Sqlite</span><span class="sxs-lookup"><span data-stu-id="36e76-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="36e76-104">Microsoft.Data.Sqlite ist ein einfacher [ADO.NET](../../../framework/data/adonet/index.md)-Anbieter für SQLite.</span><span class="sxs-lookup"><span data-stu-id="36e76-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="36e76-105">Der [Entity Framework Core](/ef/core/)-Anbieter für SQLite ist auf dieser Bibliothek aufgebaut.</span><span class="sxs-lookup"><span data-stu-id="36e76-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="36e76-106">Dieser kann aber auch unabhängig oder mit anderen Datenzugriffsbibliotheken verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="36e76-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="36e76-107">Installation</span><span class="sxs-lookup"><span data-stu-id="36e76-107">Installation</span></span>

<span data-ttu-id="36e76-108">Die neuste stabile Version ist unter [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="36e76-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="36e76-109">.NET Core-CLI</span><span class="sxs-lookup"><span data-stu-id="36e76-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[<span data-ttu-id="36e76-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="36e76-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="36e76-111">Verwendung</span><span class="sxs-lookup"><span data-stu-id="36e76-111">Usage</span></span>

<span data-ttu-id="36e76-112">Diese Bibliothek implementiert die allgemeinen ADO.NET-Abstraktionen für Verbindungen, Befehle, Datenleser usw.</span><span class="sxs-lookup"><span data-stu-id="36e76-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="36e76-113">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="36e76-113">See also</span></span>

* [<span data-ttu-id="36e76-114">Verbindungszeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="36e76-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="36e76-115">API-Referenz</span><span class="sxs-lookup"><span data-stu-id="36e76-115">API Reference</span></span>](../../../../api/index.md?view=msdata-sqlite-3.0)
* [<span data-ttu-id="36e76-116">SQL-Syntax</span><span class="sxs-lookup"><span data-stu-id="36e76-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
