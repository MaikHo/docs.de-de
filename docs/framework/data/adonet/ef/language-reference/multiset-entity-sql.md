---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: a81787da9ee1af084a903dcb50b024f3d26d18fc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175693"
---
# <a name="multiset-entity-sql"></a>MULTISET (Entity SQL)

Erstellt eine Instanz einer Multimenge aus einer Liste von Werten. Alle Werte im MULTISET-Konstruktor müssen von einem kompatiblen `T`-Typ sein. Leere Multimengenkonstruktoren sind nicht zulässig.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
MULTISET ( expression [{, expression }] )  
-- or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Argumente  

 `expression`  
 Eine beliebige Liste gültiger Werte.  
  
## <a name="return-value"></a>Rückgabewert  

 Eine Auflistung vom Typ "Multiset" \<T> .  
  
## <a name="remarks"></a>Bemerkungen  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] stellt drei Arten von Konstruktoren bereit: Zeilenkonstruktoren, Objektkonstruktoren und Multimengenkonstruktoren (oder Auflistungen). Weitere Informationen finden Sie unter [Konstruieren von Typen](constructing-types-entity-sql.md).  
  
 Der Multimengenkonstruktor erstellt eine Instanz einer Multimenge aus einer Liste von Werten. Alle Werte im Konstruktor müssen von einem kompatiblen Typ sein.  
  
 Zum Beispiel erstellt der folgende Ausdruck eine Multimenge von ganzen Zahlen.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> Unterstützte Multiset-Literale werden nur unterstützt, wenn eine Wrapping-Multimenge über ein einzelnes Multiset-Element verfügt. Beispiel: `{{1, 2, 3}}` . Wenn die Wrapping-Multimenge über mehrere Multimengenelemente verfügt, werden geschachtelte (z. B. `{{1, 2}, {3, 4}}`) Multimengenliterale nicht unterstützt.  
  
## <a name="example"></a>Beispiel  

 Die Folgende Entity SQL-Abfrage verwendet den MULTISET-Operator, um eine Instanz einer Multimenge aus einer Liste mit Werten zu erstellen. Diese Abfrage beruht auf dem "AdventureWorks Sales"-Modell. Führen Sie folgende Schritte aus, um diese Abfrage zu kompilieren und auszuführen:  
  
1. Verwenden Sie das Verfahren unter [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Übergeben Sie die folgende Abfrage als Argument an die `ExecuteStructuralTypeQuery` -Methode:  
  
 [!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]  
  
## <a name="see-also"></a>Weitere Informationen

- [Konstruktionstypen](constructing-types-entity-sql.md)
- [Entity SQL-Referenz](entity-sql-reference.md)
