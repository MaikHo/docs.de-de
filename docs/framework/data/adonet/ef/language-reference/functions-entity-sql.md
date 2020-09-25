---
title: Funktionen (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: bef959ae6a835b5d1d696162528a8f904c59e8e5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201069"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="3fc34-102">Funktionen (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3fc34-102">Functions (Entity SQL)</span></span>

<span data-ttu-id="3fc34-103">Entity SQL unterstützt benutzerdefinierte Funktionen sowie kanonische und anbieterspezifische Funktionen.</span><span class="sxs-lookup"><span data-stu-id="3fc34-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="3fc34-104">Benutzerdefinierte Funktionen werden im konzeptionellen Modell oder inline in der Abfrage angegeben.</span><span class="sxs-lookup"><span data-stu-id="3fc34-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="3fc34-105">Weitere Informationen finden Sie unter [benutzerdefinierte Funktionen](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3fc34-105">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="3fc34-106">Kanonische Funktionen sind im Entity Framework vordefiniert und müssen von Datenanbietern unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="3fc34-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="3fc34-107">Entity SQL-Befehle schlagen fehl, wenn ein Benutzer eine Funktion aufruft, die von einem Anbieter nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="3fc34-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="3fc34-108">Deshalb werden kanonische Funktionen im Allgemeinen speicherspezifischen Funktionen vorgezogen, die sich in einem anbieterspezifischen Namespace befinden.</span><span class="sxs-lookup"><span data-stu-id="3fc34-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="3fc34-109">Weitere Informationen finden Sie unter [kanonische Funktionen](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3fc34-109">For more information, see [Canonical Functions](canonical-functions.md).</span></span>  
  
 <span data-ttu-id="3fc34-110">Der verwaltete Anbieter des Microsoft SQL Client stellt eine Reihe anbieterspezifischer Funktionen bereit.</span><span class="sxs-lookup"><span data-stu-id="3fc34-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="3fc34-111">Weitere Informationen finden Sie unter [SqlClient für Entity Framework Funktionen](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3fc34-111">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3fc34-112">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="3fc34-112">In This Section</span></span>  

 [<span data-ttu-id="3fc34-113">Benutzerdefinierte Funktionen</span><span class="sxs-lookup"><span data-stu-id="3fc34-113">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="3fc34-114">Auflösung von Funktionsüberladungen</span><span class="sxs-lookup"><span data-stu-id="3fc34-114">Function Overload Resolution</span></span>](function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="3fc34-115">Aggregatfunktionen</span><span class="sxs-lookup"><span data-stu-id="3fc34-115">Aggregate Functions</span></span>](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="3fc34-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3fc34-116">See also</span></span>

- [<span data-ttu-id="3fc34-117">Übersicht über Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3fc34-117">Entity SQL Overview</span></span>](entity-sql-overview.md)
