---
title: Entfernen von doppelten Elementen aus einer Sequenz
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: 0dca1a635fd1cc6e48e8ad914909769b2cf0e66d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161372"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a>Entfernen von doppelten Elementen aus einer Sequenz

Verwenden Sie den <xref:System.Linq.Queryable.Distinct%2A>-Operator, um doppelte Elemente aus einer Sequenz auszuschließen.  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird <xref:System.Linq.Queryable.Distinct%2A> verwendet, um eine Sequenz der eindeutigen Orte auszuwählen, die Kunden aufweisen.  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a>Weitere Informationen

- [Abfrage Beispiele](query-examples.md)
