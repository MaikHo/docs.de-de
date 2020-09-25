---
title: Interceptors (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: 64c5c82f33daf677e58d49655897c392f1f7b7f9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204397"
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="38ea0-102">Interceptors (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="38ea0-102">Interceptors (WCF Data Services)</span></span>

<span data-ttu-id="38ea0-103">WCF Data Services ermöglicht einer Anwendung das Abfangen von Anforderungs Nachrichten, damit Sie einem Vorgang benutzerdefinierte Logik hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="38ea0-103">WCF Data Services enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="38ea0-104">Sie können Daten in eingehenden Nachrichten mithilfe dieser benutzerdefinierten Logik überprüfen.</span><span class="sxs-lookup"><span data-stu-id="38ea0-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="38ea0-105">Sie können damit außerdem den Bereich einer Abfrageanforderung weiter einschränken, z. B. um eine benutzerdefinierte Autorisierungsrichtlinie für jede Anforderung einzufügen.</span><span class="sxs-lookup"><span data-stu-id="38ea0-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="38ea0-106">Das Abfangen wird von speziell attributierten Methoden im Datendienst ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="38ea0-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="38ea0-107">Diese Methoden werden von WCF Data Services an der entsprechenden Stelle der Nachrichtenverarbeitung aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="38ea0-107">These methods are called by WCF Data Services at the appropriate point in message processing.</span></span> <span data-ttu-id="38ea0-108">Interceptoren werden für jede Entitätenmenge definiert, und Interceptormethoden können im Gegensatz zu Dienstvorgängen keine Parameter aus der Anforderung akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="38ea0-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="38ea0-109">Abfrage-Interceptor-Methoden, die beim Verarbeiten einer HTTP GET-Anforderung aufgerufen werden, müssen einen Lambda-Ausdruck zurückgeben, der bestimmt, ob eine Instanz der Entitätenmenge des Interceptors von den Abfrageergebnissen zurückgegeben werden soll.</span><span class="sxs-lookup"><span data-stu-id="38ea0-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="38ea0-110">Dieser Ausdruck wird vom Datendienst verwendet, um den angeforderten Vorgang weiter zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="38ea0-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="38ea0-111">Nachfolgend wird eine Beispieldefinition eines Abfrage-Interceptors dargestellt.</span><span class="sxs-lookup"><span data-stu-id="38ea0-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="38ea0-112">Weitere Informationen finden Sie unter Gewusst [wie: Abfangen von Datendienst Nachrichten](how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="38ea0-112">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="38ea0-113">Change-Interceptoren, die beim Verarbeiten von Nicht-Abfragevorgängen aufgerufen werden, müssen `void` (`Nothing` in Visual Basic) zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="38ea0-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="38ea0-114">Change-Interceptor-Methoden müssen die folgenden beiden Parameter akzeptieren:</span><span class="sxs-lookup"><span data-stu-id="38ea0-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1. <span data-ttu-id="38ea0-115">Ein Parameter eines Typs, der mit dem Entitätstyp der Entitätenmenge kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="38ea0-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="38ea0-116">Wenn der Datendienst den Change-Interceptor aufruft, spiegelt der Wert dieses Parameters die von der Anforderung gesendeten Entitätsinformationen wider.</span><span class="sxs-lookup"><span data-stu-id="38ea0-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2. <span data-ttu-id="38ea0-117">Ein Parameter vom Typ <xref:System.Data.Services.UpdateOperations>.</span><span class="sxs-lookup"><span data-stu-id="38ea0-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="38ea0-118">Wenn der Datendienst den Change-Interceptor aufruft, spiegelt der Wert dieses Parameters den Vorgang wider, den die Anforderung auszuführen versucht.</span><span class="sxs-lookup"><span data-stu-id="38ea0-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="38ea0-119">Nachfolgend wird eine Beispieldefinition eines Change-Interceptors dargestellt.</span><span class="sxs-lookup"><span data-stu-id="38ea0-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="38ea0-120">Weitere Informationen finden Sie unter Gewusst [wie: Abfangen von Datendienst Nachrichten](how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="38ea0-120">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="38ea0-121">Die folgenden Attribute werden für das Abfangen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="38ea0-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="38ea0-122">**[Queryinterceptor (** *entitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="38ea0-122">**[QueryInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="38ea0-123">Methoden mit angewendetem <xref:System.Data.Services.QueryInterceptorAttribute>-Attribut werden aufgerufen, wenn eine HTTP GET-Anforderung für die Ziel-Entitätenmengenressource empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="38ea0-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="38ea0-124">Diese Methoden müssen immer einen Lambdaausdruck in Form von `Expression<Func<T,bool>>` zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="38ea0-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="38ea0-125">**[Changeinterceptor (** *entitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="38ea0-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="38ea0-126">Methoden mit angewendetem <xref:System.Data.Services.ChangeInterceptorAttribute>-Attribut werden aufgerufen, wenn eine andere HTTP-Anforderung als eine HTTP GET-Anforderung für die Ziel-Entitätenmengenressource empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="38ea0-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="38ea0-127">Diese Methoden müssen immer `void` (`Nothing` in Visual Basic) zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="38ea0-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="38ea0-128">Weitere Informationen finden Sie unter Gewusst [wie: Abfangen von Datendienst Nachrichten](how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="38ea0-128">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ea0-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="38ea0-129">See also</span></span>

- [<span data-ttu-id="38ea0-130">Dienstoperationen</span><span class="sxs-lookup"><span data-stu-id="38ea0-130">Service Operations</span></span>](service-operations-wcf-data-services.md)
