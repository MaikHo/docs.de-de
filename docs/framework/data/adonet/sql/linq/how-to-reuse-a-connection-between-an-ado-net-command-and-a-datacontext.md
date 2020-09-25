---
title: 'Vorgehensweise: Wiederverwenden einer Verbindung zwischen einem ADO.NET-Befehl und einem DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 89c9a12399d3d76487d1fdc2bd82aa037c167710
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197351"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="75543-102">Vorgehensweise: Wiederverwenden einer Verbindung zwischen einem ADO.NET-Befehl und einem DataContext</span><span class="sxs-lookup"><span data-stu-id="75543-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>

<span data-ttu-id="75543-103">Da [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ein Teil der ADO.NET-Technologie ist und auf Diensten basiert, die von ADO.NET bereitgestellt werden, können Sie eine Verbindung zwischen einem ADO.net-Befehl und einem wieder verwenden <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="75543-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the ADO.NET family of technologies and is based on services provided by ADO.NET, you can reuse a connection between an ADO.NET command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75543-104">Beispiel</span><span class="sxs-lookup"><span data-stu-id="75543-104">Example</span></span>  

 <span data-ttu-id="75543-105">Im folgenden Beispiel wird gezeigt, wie die gleiche Verbindung zwischen einem ADO.net-Befehl und der wieder verwendet wird <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="75543-105">The following example shows how to reuse the same connection between an ADO.NET command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="75543-106">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="75543-106">See also</span></span>

- [<span data-ttu-id="75543-107">Hintergrundinformationen</span><span class="sxs-lookup"><span data-stu-id="75543-107">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="75543-108">ADO.NET und LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="75543-108">ADO.NET and LINQ to SQL</span></span>](ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="75543-109">Kommunizieren mit der Datenbank</span><span class="sxs-lookup"><span data-stu-id="75543-109">Communicating with the Database</span></span>](communicating-with-the-database.md)
