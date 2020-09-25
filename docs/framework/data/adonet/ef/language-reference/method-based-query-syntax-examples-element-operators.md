---
title: 'Beispiele für die methodenbasierte Abfragesyntax: Elementoperatoren'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 96d393a34af69935e75582ef1954ddd661a355f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192047"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="7eb4a-102">Beispiele für die methodenbasierte Abfragesyntax: Elementoperatoren</span><span class="sxs-lookup"><span data-stu-id="7eb4a-102">Method-Based Query Syntax Examples: Element Operators</span></span>

<span data-ttu-id="7eb4a-103">In den Beispielen in diesem Thema wird gezeigt, wie die-Methode verwendet wird <xref:System.Linq.Enumerable.First%2A> , um das [AdventureWorks Sales-Modell](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) mithilfe von Methoden basierter Abfrage Syntax abzufragen.</span><span class="sxs-lookup"><span data-stu-id="7eb4a-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="7eb4a-104">Für das in den Beispielen verwendete "AdventureWorks Sales"-Modell wurde auf die Tabellen Contact, Address, Product, SalesOrderHeader und SalesOrderDetail der "AdventureWorks"-Beispieldatenbank zurückgegriffen.</span><span class="sxs-lookup"><span data-stu-id="7eb4a-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7eb4a-105">Im Beispiel in diesem Thema werden die folgenden- `using` / `Imports` Anweisungen verwendet:</span><span class="sxs-lookup"><span data-stu-id="7eb4a-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="7eb4a-106">First</span><span class="sxs-lookup"><span data-stu-id="7eb4a-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="7eb4a-107">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7eb4a-107">Example</span></span>  

 <span data-ttu-id="7eb4a-108">Im folgenden Beispiel wird die <xref:System.Linq.Enumerable.First%2A> -Methode verwendet, um die erste e-Mail-Adresse zu suchen, die mit "Caroline" beginnt.</span><span class="sxs-lookup"><span data-stu-id="7eb4a-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="7eb4a-109">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7eb4a-109">See also</span></span>

- [<span data-ttu-id="7eb4a-110">Abfragen in LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="7eb4a-110">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
