---
title: SqlClient für Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: 7f3a1d4bbd18977bbb1dc9ce65140428ea6fe2f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156536"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="0d429-102">SqlClient für Entity Framework</span><span class="sxs-lookup"><span data-stu-id="0d429-102">SqlClient for the Entity Framework</span></span>

<span data-ttu-id="0d429-103">Dieser Abschnitt beschreibt den .NET Framework-Datenanbieter für SQL Server (SqlClient), der dem Entity Framework die Arbeit mit Microsoft SQL Server ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="0d429-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="0d429-104">Anbieterschemaattribut</span><span class="sxs-lookup"><span data-stu-id="0d429-104">Provider Schema Attribute</span></span>  

 <span data-ttu-id="0d429-105">`Provider` ist ein Attribut des `Schema`-Elements der Datenspeicherschema-Definitionssprache (Store Schema Definition Language, SSDL).</span><span class="sxs-lookup"><span data-stu-id="0d429-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="0d429-106">Um SqlClient zu verwenden, weisen Sie dem `Provider`-Attribut des `Schema`-Elements die Zeichenfolge "System.Data.SqlClient" zu.</span><span class="sxs-lookup"><span data-stu-id="0d429-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="0d429-107">'ProviderManifestToken'-Schemaattribut</span><span class="sxs-lookup"><span data-stu-id="0d429-107">ProviderManifestToken Schema Attribute</span></span>  

 <span data-ttu-id="0d429-108">Das `ProviderManifestToken`-Element ist ein erforderliches Attribut des `Schema`-Elements.</span><span class="sxs-lookup"><span data-stu-id="0d429-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="0d429-109">Dieses Token wird verwendet, um das Anbietermanifest für Offlineszenarien zu laden.</span><span class="sxs-lookup"><span data-stu-id="0d429-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="0d429-110">Weitere Informationen zum- `ProviderManifestToken` Attribut finden Sie unter [Schema-Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="0d429-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="0d429-111">SqlClient kann als Datenanbieter für verschiedene Versionen von SQL Server verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0d429-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="0d429-112">Diese Versionen haben verschiedene Funktionen.</span><span class="sxs-lookup"><span data-stu-id="0d429-112">These versions have different capabilities.</span></span> <span data-ttu-id="0d429-113">Beispielsweise unterstützt SQL Server 2000 nicht `varchar(max)` `nvarchar(max)` die Typen und, die mit SQL Server 2005 eingeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="0d429-113">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="0d429-114">SqlClient erzeugt und akzeptiert die folgenden Anbietermanifesttoken für die verschiedenen Versionen von SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0d429-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="0d429-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="0d429-115">SQL Server 2000</span></span>|<span data-ttu-id="0d429-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="0d429-116">SQL Server 2005</span></span>|<span data-ttu-id="0d429-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="0d429-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="0d429-118">2000</span><span class="sxs-lookup"><span data-stu-id="0d429-118">2000</span></span>|<span data-ttu-id="0d429-119">2005</span><span class="sxs-lookup"><span data-stu-id="0d429-119">2005</span></span>|<span data-ttu-id="0d429-120">2008</span><span class="sxs-lookup"><span data-stu-id="0d429-120">2008</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="0d429-121">Ab Visual Studio 2010 unterstützen die [ADO.NET Entity Data Model-Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) SQL Server 2000 nicht.</span><span class="sxs-lookup"><span data-stu-id="0d429-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="0d429-122">Anbieternamespacename</span><span class="sxs-lookup"><span data-stu-id="0d429-122">Provider Namespace Name</span></span>  

 <span data-ttu-id="0d429-123">Alle Anbieter müssen einen Namespace angeben.</span><span class="sxs-lookup"><span data-stu-id="0d429-123">All providers must specify a namespace.</span></span> <span data-ttu-id="0d429-124">Anhand dieser Eigenschaft ermittelt Entity Framework, welches Präfix von diesem Anbieter für spezifische Konstrukte wie Typen und Funktionen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0d429-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="0d429-125">Der Namespace für SqlClient-Anbietermanifeste lautet `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="0d429-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="0d429-126">Weitere Informationen zu Namespaces finden Sie unter [Namespaces](./language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0d429-126">For more information about namespaces, see [Namespaces](./language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="0d429-127">Typen</span><span class="sxs-lookup"><span data-stu-id="0d429-127">Types</span></span>  

 <span data-ttu-id="0d429-128">Der SqlClient-Anbieter für das Entity Framework stellt Zuordnungsinformationen zwischen Typen des konzeptionellen Modells und SQL Server-Typen bereit.</span><span class="sxs-lookup"><span data-stu-id="0d429-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="0d429-129">Weitere Informationen finden Sie unter [SqlClient für Entity frameworktypes](sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="0d429-129">For more information, see [SqlClient for Entity FrameworkTypes](sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="0d429-130">Functions</span><span class="sxs-lookup"><span data-stu-id="0d429-130">Functions</span></span>  

 <span data-ttu-id="0d429-131">Der SqlClient-Anbieter für das Entity Framework definiert die Liste der vom Anbieter unterstützten Funktionen.</span><span class="sxs-lookup"><span data-stu-id="0d429-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="0d429-132">Eine Liste der unterstützten Funktionen finden Sie unter [SqlClient für Entity Framework Funktionen](sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0d429-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d429-133">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="0d429-133">In This Section</span></span>  

 [<span data-ttu-id="0d429-134">SqlClient für Entity Framework-Funktionen</span><span class="sxs-lookup"><span data-stu-id="0d429-134">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="0d429-135">SqlClient für Entity Framework-Typen</span><span class="sxs-lookup"><span data-stu-id="0d429-135">SqlClient for Entity FrameworkTypes</span></span>](sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="0d429-136">Bekannte Probleme in SqlClient für Entity Framework</span><span class="sxs-lookup"><span data-stu-id="0d429-136">Known Issues in SqlClient for Entity Framework</span></span>](known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="0d429-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0d429-137">See also</span></span>

- [<span data-ttu-id="0d429-138">Entity SQL-Sprache</span><span class="sxs-lookup"><span data-stu-id="0d429-138">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="0d429-139">Sprachreferenz</span><span class="sxs-lookup"><span data-stu-id="0d429-139">Language Reference</span></span>](./language-reference/index.md)
- [<span data-ttu-id="0d429-140">Bekannte Probleme im SqlClient-Anbieter für Entity Framework</span><span class="sxs-lookup"><span data-stu-id="0d429-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](sqlclient-for-the-entity-framework.md)
