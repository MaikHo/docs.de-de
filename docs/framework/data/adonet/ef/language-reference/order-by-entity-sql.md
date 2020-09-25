---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 5e1c418a7f2bd40a42b259fb3784794b13098d7f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173678"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="57434-102">ORDER BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="57434-102">ORDER BY (Entity SQL)</span></span>

<span data-ttu-id="57434-103">Legt die Sortierreihenfolge für Objekte fest, die von einer SELECT-Anweisung zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="57434-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57434-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="57434-104">Syntax</span></span>  
  
```sql  
[ ORDER BY
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="57434-105">Argumente</span><span class="sxs-lookup"><span data-stu-id="57434-105">Arguments</span></span>  

 `order_by_expression`  
 <span data-ttu-id="57434-106">Ein gültiger Abfrageausdruck, der eine Eigenschaft angibt, nach der sortiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="57434-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="57434-107">Es können mehrere Sortierausdrücke angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="57434-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="57434-108">Die Reihenfolge der Sortierausdrücke in der ORDER BY-Klausel definiert den Aufbau des sortierten Resultsets.</span><span class="sxs-lookup"><span data-stu-id="57434-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="57434-109">COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="57434-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="57434-110">Gibt an, dass die ORDER BY-Operation nach der in `collation_name`angegebenen Sortierreihenfolge ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="57434-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="57434-111">COLLATE ist nur für Zeichenfolgenausdrücke anwendbar.</span><span class="sxs-lookup"><span data-stu-id="57434-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="57434-112">ASC</span><span class="sxs-lookup"><span data-stu-id="57434-112">ASC</span></span>  
 <span data-ttu-id="57434-113">Gibt an, dass die Werte der angegebenen Eigenschaft in aufsteigender Reihenfolge (vom kleinsten zum größten Wert) sortiert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="57434-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="57434-114">Dies ist die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="57434-114">This is the default.</span></span>  
  
 <span data-ttu-id="57434-115">DESC</span><span class="sxs-lookup"><span data-stu-id="57434-115">DESC</span></span>  
 <span data-ttu-id="57434-116">Gibt an, dass die Werte der angegebenen Eigenschaft in absteigender Reihenfolge (vom größten zum kleinsten Wert) sortiert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="57434-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="57434-117">LIMIT `n`</span><span class="sxs-lookup"><span data-stu-id="57434-117">LIMIT `n`</span></span>  
 <span data-ttu-id="57434-118">Nur die ersten `n` -Elemente werden ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="57434-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="57434-119">SKIP `n`</span><span class="sxs-lookup"><span data-stu-id="57434-119">SKIP `n`</span></span>  
 <span data-ttu-id="57434-120">Überspringt die ersten `n` -Elemente.</span><span class="sxs-lookup"><span data-stu-id="57434-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57434-121">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="57434-121">Remarks</span></span>  

 <span data-ttu-id="57434-122">Die ORDER BY-Klausel wird logisch auf das Ergebnis der SELECT-Klausel angewendet.</span><span class="sxs-lookup"><span data-stu-id="57434-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="57434-123">In der ORDER BY-Klausel kann auf Elemente in der Auswahlliste verwiesen werden, indem deren Aliase verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="57434-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="57434-124">Die ORDER BY-Klausel kann auch auf andere Variablen verweisen, die sich aktuell im Gültigkeitsbereich befinden.</span><span class="sxs-lookup"><span data-stu-id="57434-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="57434-125">Wenn die SELECT-Klausel jedoch mit einem DISTINCT-Modifizierer angegeben wurde, kann von der ORDER BY-Klausel nur auf Aliase der SELECT-Klausel verwiesen werden.</span><span class="sxs-lookup"><span data-stu-id="57434-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="57434-126">Jeder Ausdruck in der ORDER BY-Klausel muss zu einem Typ ausgewertet werden, der bzgl. geordneter Ungleichheit ("kleiner als", "größer als" usw.) verglichen werden kann.</span><span class="sxs-lookup"><span data-stu-id="57434-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="57434-127">Bei diesen Typen handelt es sich im Allgemeinen um skalare primitive Typen wie Zahlen, Zeichenfolgen und Datumsangaben.</span><span class="sxs-lookup"><span data-stu-id="57434-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="57434-128">"RowTypes" vergleichbarer Typen sind ebenfalls in der Reihenfolge vergleichbar.</span><span class="sxs-lookup"><span data-stu-id="57434-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="57434-129">Wenn Code eine geordnete Menge durchläuft, wird, anders als bei einer Projektion in der obersten Ebene, die Reihenfolge bei der Ausgabe möglicherweise nicht erhalten.</span><span class="sxs-lookup"><span data-stu-id="57434-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="57434-130">Im folgenden Beispiel wird die Reihenfolge garantiert beibehalten:</span><span class="sxs-lookup"><span data-stu-id="57434-130">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="57434-131">In der folgenden Abfrage wird die Reihenfolge der Abfrage ignoriert:</span><span class="sxs-lookup"><span data-stu-id="57434-131">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="57434-132">Verwenden Sie folgendes Muster, um eine geordnete UNION, UNION ALL, EXCEPT oder INTERSECT-Operation durchzuführen:</span><span class="sxs-lookup"><span data-stu-id="57434-132">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="57434-133">Eingeschränkte Schlüsselwörter</span><span class="sxs-lookup"><span data-stu-id="57434-133">Restricted keywords</span></span>  

 <span data-ttu-id="57434-134">Die folgenden Schlüsselwörter müssen bei der Verwendung in einer `ORDER BY` -Klausel in Anführungszeichen gesetzt werden:</span><span class="sxs-lookup"><span data-stu-id="57434-134">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="57434-135">CROSS</span><span class="sxs-lookup"><span data-stu-id="57434-135">CROSS</span></span>  
  
- <span data-ttu-id="57434-136">FULL</span><span class="sxs-lookup"><span data-stu-id="57434-136">FULL</span></span>  
  
- <span data-ttu-id="57434-137">KEY</span><span class="sxs-lookup"><span data-stu-id="57434-137">KEY</span></span>  
  
- <span data-ttu-id="57434-138">LEFT</span><span class="sxs-lookup"><span data-stu-id="57434-138">LEFT</span></span>  
  
- <span data-ttu-id="57434-139">ORDER</span><span class="sxs-lookup"><span data-stu-id="57434-139">ORDER</span></span>  
  
- <span data-ttu-id="57434-140">OUTER</span><span class="sxs-lookup"><span data-stu-id="57434-140">OUTER</span></span>  
  
- <span data-ttu-id="57434-141">RIGHT</span><span class="sxs-lookup"><span data-stu-id="57434-141">RIGHT</span></span>  
  
- <span data-ttu-id="57434-142">ROW</span><span class="sxs-lookup"><span data-stu-id="57434-142">ROW</span></span>  
  
- <span data-ttu-id="57434-143">VALUE</span><span class="sxs-lookup"><span data-stu-id="57434-143">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="57434-144">Reihenfolge geschachtelter Abfragen</span><span class="sxs-lookup"><span data-stu-id="57434-144">Ordering Nested Queries</span></span>  

 <span data-ttu-id="57434-145">In Entity Framework kann ein geschachtelter Ausdruck an jeder Stelle in der Abfrage verwendet werden. Die Reihenfolge einer geschachtelten Abfrage wird nicht beibehalten.</span><span class="sxs-lookup"><span data-stu-id="57434-145">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="57434-146">Mit der folgenden Abfrage werden die Ergebnisse nach dem Nachnamen sortiert:</span><span class="sxs-lookup"><span data-stu-id="57434-146">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="57434-147">In der folgenden Abfrage wird die Reihenfolge der Abfrage ignoriert:</span><span class="sxs-lookup"><span data-stu-id="57434-147">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="57434-148">Beispiel</span><span class="sxs-lookup"><span data-stu-id="57434-148">Example</span></span>  

 <span data-ttu-id="57434-149">In der folgenden [!INCLUDE[esql](../../../../../../includes/esql-md.md)] -Abfrage wird der ORDER BY-Operator verwendet, um die für von der SELECT-Anweisung zurückgegebene Objekte zu verwendende Sortierreihenfolge anzugeben.</span><span class="sxs-lookup"><span data-stu-id="57434-149">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="57434-150">Diese Abfrage beruht auf dem "AdventureWorks Sales"-Modell.</span><span class="sxs-lookup"><span data-stu-id="57434-150">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="57434-151">Führen Sie folgende Schritte aus, um diese Abfrage zu kompilieren und auszuführen:</span><span class="sxs-lookup"><span data-stu-id="57434-151">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="57434-152">Verwenden Sie das Verfahren unter [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="57434-152">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="57434-153">Übergeben Sie die folgende Abfrage als Argument an die `ExecuteStructuralTypeQuery` -Methode:</span><span class="sxs-lookup"><span data-stu-id="57434-153">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="57434-154">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="57434-154">See also</span></span>

- [<span data-ttu-id="57434-155">Abfrageausdrücke</span><span class="sxs-lookup"><span data-stu-id="57434-155">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="57434-156">Entity SQL-Referenz</span><span class="sxs-lookup"><span data-stu-id="57434-156">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="57434-157">SKIP</span><span class="sxs-lookup"><span data-stu-id="57434-157">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="57434-158">Ans</span><span class="sxs-lookup"><span data-stu-id="57434-158">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="57434-159">TOP</span><span class="sxs-lookup"><span data-stu-id="57434-159">TOP</span></span>](top-entity-sql.md)
