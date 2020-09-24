---
title: Übersicht über Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: e9a5117984380938e48e0cd1113107c74389480f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148126"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="21c2e-102">Übersicht über Entity SQL</span><span class="sxs-lookup"><span data-stu-id="21c2e-102">Entity SQL Overview</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="21c2e-103">ist eine SQL-ähnliche Sprache, die es Ihnen ermöglicht, konzeptionelle Modelle in der Entity Framework abzufragen.</span><span class="sxs-lookup"><span data-stu-id="21c2e-103">is a SQL-like language that enables you to query conceptual models in the Entity Framework.</span></span> <span data-ttu-id="21c2e-104">Konzeptionelle Modelle stellen Daten als Entitäten und Beziehungen dar und [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ermöglichen es Ihnen, diese Entitäten und Beziehungen in einem Format abzufragen, das den Benutzern, die SQL verwendet haben, vertraut ist.</span><span class="sxs-lookup"><span data-stu-id="21c2e-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  

 <span data-ttu-id="21c2e-105">Der Entity Framework arbeitet mit Speicher spezifischen Datenanbietern zusammen, um generische [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in Speicher spezifische Abfragen zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="21c2e-105">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="21c2e-106">Der EntityClient-Anbieter bietet die Möglichkeit, einen [!INCLUDE[esql](../../../../../../includes/esql-md.md)]-Befehl für ein Entitätenmodell auszuführen und vielfältige Datentypen, einschließlich skalarer Ergebnisse, Resultsets und Objektdiagrammen, zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="21c2e-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="21c2e-107">Wenn Sie <xref:System.Data.EntityClient.EntityCommand>-Objekte erstellen, können Sie den Namen einer gespeicherten Prozedur oder den Text einer Abfrage angeben, indem Sie der [!INCLUDE[esql](../../../../../../includes/esql-md.md)]-Eigenschaft eine <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>-Abfragezeichenfolge zuweisen.</span><span class="sxs-lookup"><span data-stu-id="21c2e-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="21c2e-108">Der <xref:System.Data.EntityClient.EntityDataReader> stellt die Ergebnisse eines für ein EDM ausgeführten <xref:System.Data.EntityClient.EntityCommand> zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="21c2e-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="21c2e-109">Zum Ausführen des Befehls, das den <xref:System.Data.EntityClient.EntityDataReader> zurückgibt, rufen Sie <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A> auf.</span><span class="sxs-lookup"><span data-stu-id="21c2e-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="21c2e-110">Neben dem EntityClient-Anbieter ermöglicht die Entity Framework die Verwendung [!INCLUDE[esql](../../../../../../includes/esql-md.md)] von, um Abfragen für ein konzeptionelles Modell auszuführen und Daten als stark typisierte CLR-Objekte zurückzugeben, die Instanzen von Entitäts Typen sind.</span><span class="sxs-lookup"><span data-stu-id="21c2e-110">In addition to the EntityClient provider, the Entity Framework enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="21c2e-111">Weitere Informationen finden Sie unter [Arbeiten mit Objekten](../working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="21c2e-111">For more information, see [Working with Objects](../working-with-objects.md).</span></span>  
  
 <span data-ttu-id="21c2e-112">In diesem Abschnitt werden konzeptionelle Informationen zu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="21c2e-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21c2e-113">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="21c2e-113">In This Section</span></span>  

 [<span data-ttu-id="21c2e-114">Unterschiede zwischen Entity SQL und Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="21c2e-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="21c2e-115">Entity SQL-Kurzreferenz</span><span class="sxs-lookup"><span data-stu-id="21c2e-115">Entity SQL Quick Reference</span></span>](entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="21c2e-116">Typensystem</span><span class="sxs-lookup"><span data-stu-id="21c2e-116">Type System</span></span>](type-system-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-117">Typdefinitionen</span><span class="sxs-lookup"><span data-stu-id="21c2e-117">Type Definitions</span></span>](type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-118">Konstruktionstypen</span><span class="sxs-lookup"><span data-stu-id="21c2e-118">Constructing Types</span></span>](constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-119">Zwischenspeichern von Abfrageplänen</span><span class="sxs-lookup"><span data-stu-id="21c2e-119">Query Plan Caching</span></span>](query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-120">Namespaces</span><span class="sxs-lookup"><span data-stu-id="21c2e-120">Namespaces</span></span>](namespaces-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-121">Identifiers (Bezeichner)</span><span class="sxs-lookup"><span data-stu-id="21c2e-121">Identifiers</span></span>](identifiers-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-122">Parameter</span><span class="sxs-lookup"><span data-stu-id="21c2e-122">Parameters</span></span>](parameters-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-123">Variablen</span><span class="sxs-lookup"><span data-stu-id="21c2e-123">Variables</span></span>](variables-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-124">Nicht unterstützte Ausdrücke</span><span class="sxs-lookup"><span data-stu-id="21c2e-124">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-125">Literale</span><span class="sxs-lookup"><span data-stu-id="21c2e-125">Literals</span></span>](literals-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-126">NULL-Literale und Typrückschluss</span><span class="sxs-lookup"><span data-stu-id="21c2e-126">Null Literals and Type Inference</span></span>](null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-127">Eingabezeichensatz</span><span class="sxs-lookup"><span data-stu-id="21c2e-127">Input Character Set</span></span>](input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-128">Abfrageausdrücke</span><span class="sxs-lookup"><span data-stu-id="21c2e-128">Query Expressions</span></span>](query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-129">Funktionen</span><span class="sxs-lookup"><span data-stu-id="21c2e-129">Functions</span></span>](functions-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-130">Operatorrangfolge</span><span class="sxs-lookup"><span data-stu-id="21c2e-130">Operator Precedence</span></span>](operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-131">Paging</span><span class="sxs-lookup"><span data-stu-id="21c2e-131">Paging</span></span>](paging-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-132">Vergleichssemantik</span><span class="sxs-lookup"><span data-stu-id="21c2e-132">Comparison Semantics</span></span>](comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="21c2e-133">Zusammenstellen verschachtelter Entity SQL-Abfragen</span><span class="sxs-lookup"><span data-stu-id="21c2e-133">Composing Nested Entity SQL Queries</span></span>](composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="21c2e-134">Strukturierte Typen, die NULL-Werte zulassen</span><span class="sxs-lookup"><span data-stu-id="21c2e-134">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="21c2e-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="21c2e-135">See also</span></span>

- [<span data-ttu-id="21c2e-136">Entity SQL-Referenz</span><span class="sxs-lookup"><span data-stu-id="21c2e-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="21c2e-137">Entity SQL-Sprache</span><span class="sxs-lookup"><span data-stu-id="21c2e-137">Entity SQL Language</span></span>](entity-sql-language.md)
- [<span data-ttu-id="21c2e-138">CSDL-, SSDL- und MSL-Spezifikationen</span><span class="sxs-lookup"><span data-stu-id="21c2e-138">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
