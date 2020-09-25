---
title: Überlegungen zu LINQ (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 2523aac510516fdf19087425b10ab3f2296eb726
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194340"
---
# <a name="linq-considerations-wcf-data-services"></a><span data-ttu-id="d6c83-102">Überlegungen zu LINQ (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="d6c83-102">LINQ Considerations (WCF Data Services)</span></span>

<span data-ttu-id="d6c83-103">Dieses Thema enthält Informationen über die Art und Weise, in der LINQ-Abfragen zusammengestellt und ausgeführt werden, wenn Sie den WCF Data Services-Client verwenden und Einschränkungen bei der Verwendung von LINQ zum Abfragen eines Daten Dienstanbieter, der die Open Data Protocol (odata) implementiert.</span><span class="sxs-lookup"><span data-stu-id="d6c83-103">This topic provides information about the way in which LINQ queries are composed and executed when you are using the WCF Data Services client and limitations of using LINQ to query a data service that implements the Open Data Protocol (OData).</span></span> <span data-ttu-id="d6c83-104">Weitere Informationen zum Erstellen und Ausführen von Abfragen für einen odata-basierten Datendienst finden Sie unter [Abfragen des Daten Dienstanbieter](querying-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d6c83-104">For more information about composing and executing queries against an OData-based data service, see [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="composing-linq-queries"></a><span data-ttu-id="d6c83-105">Verfassen von LINQ-Abfragen</span><span class="sxs-lookup"><span data-stu-id="d6c83-105">Composing LINQ Queries</span></span>  

 <span data-ttu-id="d6c83-106">LINQ ermöglicht es Ihnen, Abfragen für eine Auflistung von Objekten zu verfassen, die <xref:System.Collections.Generic.IEnumerable%601> implementiert.</span><span class="sxs-lookup"><span data-stu-id="d6c83-106">LINQ enables you to compose queries against a collection of objects that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d6c83-107">Sowohl das Dialogfeld " **Dienstverweis hinzufügen** " in Visual Studio als auch das DataSvcUtil.exe-Tool werden verwendet, um eine Darstellung eines odata-Dienstanbieter als Entitäts Container Klasse zu generieren, die von erbt, sowie von <xref:System.Data.Services.Client.DataServiceContext> Objekten, die die in Feeds zurückgegebenen Entitäten darstellen.</span><span class="sxs-lookup"><span data-stu-id="d6c83-107">Both the **Add Service Reference** dialog box in Visual Studio and the DataSvcUtil.exe tool are used to generate a representation of an OData service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>, as well as objects that represent the entities returned in feeds.</span></span> <span data-ttu-id="d6c83-108">Diese Tools generieren auch Eigenschaften der Entitätscontainerklasse für die Auflistungen, die als Feeds vom Dienst verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="d6c83-108">These tools also generate properties on the entity container class for the collections that are exposed as feeds by the service.</span></span> <span data-ttu-id="d6c83-109">Jede Eigenschaft der Klasse, die den Datendienst kapselt, gibt eine <xref:System.Data.Services.Client.DataServiceQuery%601> zurück.</span><span class="sxs-lookup"><span data-stu-id="d6c83-109">Each of these properties of the class that encapsulates the data service return a <xref:System.Data.Services.Client.DataServiceQuery%601>.</span></span> <span data-ttu-id="d6c83-110">Da die <xref:System.Data.Services.Client.DataServiceQuery%601>-Klasse die von LINQ definierte <xref:System.Linq.IQueryable%601>-Schnittstelle implementiert, können Sie eine LINQ-Abfrage für vom Datendienst verfügbar gemachte Feeds verfassen. Diese Abfrage wird von der Clientbibliothek in einen Abfrageanforderungs-URI übersetzt, der bei der Ausführung an den Datendienst gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="d6c83-110">Because the <xref:System.Data.Services.Client.DataServiceQuery%601> class implements the <xref:System.Linq.IQueryable%601> interface defined by LINQ, you can compose a LINQ query against feeds exposed by the data service, which are translated by the client library into a query request URI that is sent to the data service on execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d6c83-111">Der Satz von Abfragen, der in der LINQ-Syntax ausgedrückt werden kann, ist breiter als der Satz von Abfragen, der in der von odata Data Services verwendeten URI-Syntax aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="d6c83-111">The set of queries expressible in the LINQ syntax is broader than those enabled in the URI syntax that is used by OData data services.</span></span> <span data-ttu-id="d6c83-112">Wenn die Abfrage keinem URI im Zieldatendienst zugeordnet werden kann, wird eine Ausnahme vom Typ <xref:System.NotSupportedException> ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d6c83-112">A <xref:System.NotSupportedException> is raised when the query cannot be mapped to a URI in the target data service.</span></span> <span data-ttu-id="d6c83-113">Weitere Informationen finden Sie unter den [nicht unterstützten LINQ-Methoden](linq-considerations-wcf-data-services.md#unsupportedMethods) in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="d6c83-113">For more information, see the [Unsupported LINQ Methods](linq-considerations-wcf-data-services.md#unsupportedMethods) in this topic.</span></span>  
  
 <span data-ttu-id="d6c83-114">Das folgende Beispiel zeigt eine LINQ-Abfrage, die `Orders` mit Frachtkosten über $30 zurückgibt und die Ergebnisse nach dem Lieferdatum sortiert (beginnend mit dem aktuellsten Lieferdatum):</span><span class="sxs-lookup"><span data-stu-id="d6c83-114">The following example is a LINQ query that returns `Orders` that have a freight cost of more than $30 and sorts the results by the shipping date, starting with the latest ship date:</span></span>  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]
  
 <span data-ttu-id="d6c83-115">Diese LINQ-Abfrage wird in den folgenden Abfrage-URI übersetzt, der für den auf Northwind basierenden [Schnellstart](quickstart-wcf-data-services.md) -Datendienst ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="d6c83-115">This LINQ query is translated into the following query URI that is executed against the Northwind-based [quickstart](quickstart-wcf-data-services.md) data service:</span></span>  
  
```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 <span data-ttu-id="d6c83-116">Weitere allgemeine Informationen zu LINQ finden Sie unter [Language-Integrated Query (LINQ)-c#](../../../csharp/programming-guide/concepts/linq/index.md) oder [Language-Integrated Query (LINQ)-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="d6c83-116">For more general information about LINQ, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
 <span data-ttu-id="d6c83-117">Mit LINQ können Sie Abfragen sowohl unter Verwendung der im obigen Beispiel gezeigten sprachspezifischen deklarativen Abfragesyntax als auch mit einem als Standardabfrageoperatoren bezeichneten Satz von Abfragemethoden verfassen.</span><span class="sxs-lookup"><span data-stu-id="d6c83-117">LINQ enables you to compose queries by using both the language-specific declarative query syntax, shown in the previous example, as well as a set of query methods known as standard query operators.</span></span> <span data-ttu-id="d6c83-118">Eine Abfrage, die dem obigen Beispiel funktional entspricht, kann wie im folgenden Beispiel dargestellt auch nur mithilfe der methodenbasierten Syntax verfasst werden:</span><span class="sxs-lookup"><span data-stu-id="d6c83-118">An equivalent query to the previous example can be composed by using only the method-based syntax, as shown the following example:</span></span>  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpressionspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpressionspecific)]
  
 <span data-ttu-id="d6c83-119">Der WCF Data Services Client ist in der Lage, beide Arten von zusammengesetzten Abfragen in einen Abfrage-URI zu übersetzen, und Sie können eine LINQ-Abfrage erweitern, indem Sie Abfrage Methoden an einen Abfrage Ausdruck anhängen.</span><span class="sxs-lookup"><span data-stu-id="d6c83-119">The WCF Data Services client is able to translate both kinds of composed queries into a query URI, and you can extend a LINQ query by appending query methods to a query expression.</span></span> <span data-ttu-id="d6c83-120">Wenn Sie LINQ-Abfragen verfassen, indem Sie Methodensyntax an einen Abfrageausdruck oder eine <xref:System.Data.Services.Client.DataServiceQuery%601> anfügen, werden die Vorgänge dem Abfrage-URI in der Reihenfolge hinzugefügt, in der Methoden aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="d6c83-120">When you compose LINQ queries by appending method syntax to a query expression or a <xref:System.Data.Services.Client.DataServiceQuery%601>, the operations are added to the query URI in the order in which methods are called.</span></span> <span data-ttu-id="d6c83-121">Dies hat die gleiche Funktion wie das Aufrufen der <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>-Methode zum Hinzufügen der einzelnen Abfrageoptionen zum Abfrage-URI.</span><span class="sxs-lookup"><span data-stu-id="d6c83-121">This is equivalent to calling the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method to add each query option to the query URI.</span></span>  
  
## <a name="executing-linq-queries"></a><span data-ttu-id="d6c83-122">Ausführen von LINQ-Abfragen</span><span class="sxs-lookup"><span data-stu-id="d6c83-122">Executing LINQ Queries</span></span>  

 <span data-ttu-id="d6c83-123">Wenn bestimmte LINQ-Abfragemethoden wie <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> oder <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> an die Abfrage angefügt werden, führt dies dazu, dass die Abfrage ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d6c83-123">Certain LINQ query methods, such as <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> or <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, when appended to the query, cause the query to be executed.</span></span> <span data-ttu-id="d6c83-124">Eine Abfrage wird auch ausgeführt, wenn Ergebnisse implizit aufgezählt werden, z. B. während einer `foreach`-Schleife oder wenn die Abfrage einer `List`-Auflistung zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="d6c83-124">A query is also executed when results are enumerated implicitly, such as during a `foreach` loop or when the query is assigned to a `List` collection.</span></span> <span data-ttu-id="d6c83-125">Weitere Informationen finden Sie unter [Abfragen des Daten Dienstanbieter](querying-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d6c83-125">For more information, see [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="d6c83-126">Der Client führt eine LINQ-Abfrage in zwei Teilen aus.</span><span class="sxs-lookup"><span data-stu-id="d6c83-126">The client executes a LINQ query in two parts.</span></span> <span data-ttu-id="d6c83-127">Nach Möglichkeit werden LINQ-Ausdrücke in einer Abfrage zuerst auf dem Client ausgewertet, und anschließend wird eine URI-basierte Abfrage generiert und zur Auswertung anhand der Daten im Dienst an den Datendienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="d6c83-127">Whenever possible, LINQ expressions in a query are first evaluated on the client, and then a URI-based query is generated and sent to the data service for evaluation against data in the service.</span></span> <span data-ttu-id="d6c83-128">Weitere Informationen finden Sie im Abschnitt [Client im Vergleich zur Server Ausführung](querying-the-data-service-wcf-data-services.md#executingQueries) unter [Abfragen des Daten Dienstanbieter](querying-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d6c83-128">For more information, see the section [Client versus Server Execution](querying-the-data-service-wcf-data-services.md#executingQueries) in [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="d6c83-129">Wenn eine LINQ-Abfrage nicht in einen odata-kompatiblen Abfrage-URI übersetzt werden kann, wird eine Ausnahme ausgelöst, wenn versucht wird, eine Ausführung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="d6c83-129">When a LINQ query cannot be translated in an OData-compliant query URI, an exception is raised when execution is attempted.</span></span> <span data-ttu-id="d6c83-130">Weitere Informationen finden Sie unter [Abfragen des Daten Dienstanbieter](querying-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d6c83-130">For more information, see [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="linq-query-examples"></a><span data-ttu-id="d6c83-131">LINQ-Abfragebeispiele</span><span class="sxs-lookup"><span data-stu-id="d6c83-131">LINQ Query Examples</span></span>  

 <span data-ttu-id="d6c83-132">In den Beispielen in den folgenden Abschnitten werden die Arten von LINQ-Abfragen veranschaulicht, die für einen odata-Dienst ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="d6c83-132">The examples in the following sections demonstrate the kinds of LINQ queries that can be executed against an OData service.</span></span>  
  
<a name="filtering"></a>

### <a name="filtering"></a><span data-ttu-id="d6c83-133">Filtern</span><span class="sxs-lookup"><span data-stu-id="d6c83-133">Filtering</span></span>  

 <span data-ttu-id="d6c83-134">In den LINQ-Abfragebeispielen in diesem Abschnitt werden Daten in dem vom Dienst zurückgegebenen Feed gefiltert.</span><span class="sxs-lookup"><span data-stu-id="d6c83-134">The LINQ query examples in this section filter data in the feed returned by the service.</span></span>  
  
 <span data-ttu-id="d6c83-135">Die folgenden Beispiele zeigen funktional gleichwertige Abfragen, durch die zurückgegebene `Orders`-Entitäten so gefiltert werden, dass nur Aufträge mit Frachtkosten über $30 zurückgegeben werden:</span><span class="sxs-lookup"><span data-stu-id="d6c83-135">The following examples are equivalent queries that filter the returned `Orders` entities so that only orders with a freight cost greater than $30 are returned:</span></span>  
  
- <span data-ttu-id="d6c83-136">Verwendung der LINQ-Abfragesyntax:</span><span class="sxs-lookup"><span data-stu-id="d6c83-136">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwhereclausespecific)]
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwhereclausespecific)]
  
- <span data-ttu-id="d6c83-137">Verwendung von LINQ-Abfragemethoden:</span><span class="sxs-lookup"><span data-stu-id="d6c83-137">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwheremethodspecific)]
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwheremethodspecific)]
  
- <span data-ttu-id="d6c83-138">`$filter`-Option für die URI-Abfragezeichenfolge:</span><span class="sxs-lookup"><span data-stu-id="d6c83-138">The URI query string `$filter` option:</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitquerywheremethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitquerywheremethodspecific)]
  
 <span data-ttu-id="d6c83-139">Die obigen Beispiele werden alle in den Abfrage-URI übersetzt: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.</span><span class="sxs-lookup"><span data-stu-id="d6c83-139">All of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.</span></span>  
  
<a name="sorting"></a>

### <a name="sorting"></a><span data-ttu-id="d6c83-140">Sortieren</span><span class="sxs-lookup"><span data-stu-id="d6c83-140">Sorting</span></span>  

 <span data-ttu-id="d6c83-141">Die folgenden Beispiele zeigen funktional gleichwertige Abfragen, durch die zurückgegebene Daten in absteigender Reihenfolge nach dem Firmennamen und der Postleitzahl sortiert werden:</span><span class="sxs-lookup"><span data-stu-id="d6c83-141">The following examples show equivalent queries that sort returned data both by the company name and by postal code, descending:</span></span>  
  
- <span data-ttu-id="d6c83-142">Verwendung der LINQ-Abfragesyntax:</span><span class="sxs-lookup"><span data-stu-id="d6c83-142">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbyclausespecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbyclausespecific)]
  
- <span data-ttu-id="d6c83-143">Verwendung von LINQ-Abfragemethoden:</span><span class="sxs-lookup"><span data-stu-id="d6c83-143">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbymethodspecific)]
  
- <span data-ttu-id="d6c83-144">`$orderby`-Option für die URI-Abfragezeichenfolge:</span><span class="sxs-lookup"><span data-stu-id="d6c83-144">URI query string `$orderby` option):</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryorderbymethodspecific)]
  
 <span data-ttu-id="d6c83-145">Die obigen Beispiele werden alle in den Abfrage-URI übersetzt: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.</span><span class="sxs-lookup"><span data-stu-id="d6c83-145">All of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.</span></span>  
  
<a name="projection"></a>

### <a name="projection"></a><span data-ttu-id="d6c83-146">Projektion</span><span class="sxs-lookup"><span data-stu-id="d6c83-146">Projection</span></span>  

 <span data-ttu-id="d6c83-147">Die folgenden Beispiele zeigen funktional gleichwertige Abfragen, durch die zurückgegebene Daten in den enger gefassten `CustomerAddress`-Typ projiziert werden:</span><span class="sxs-lookup"><span data-stu-id="d6c83-147">The following examples show equivalent queries that project returned data into the narrower `CustomerAddress` type:</span></span>  
  
- <span data-ttu-id="d6c83-148">Verwendung der LINQ-Abfragesyntax:</span><span class="sxs-lookup"><span data-stu-id="d6c83-148">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectclausespecific)]
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectclausespecific)]
  
- <span data-ttu-id="d6c83-149">Verwendung von LINQ-Abfragemethoden:</span><span class="sxs-lookup"><span data-stu-id="d6c83-149">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectmethodspecific)]

> [!NOTE]
> <span data-ttu-id="d6c83-150">Die `$select`-Abfrageoption kann einem Abfrage-URI nicht mit der <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>-Methode hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="d6c83-150">The `$select` query option cannot be added to a query URI by using the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method.</span></span> <span data-ttu-id="d6c83-151">Es wird empfohlen, die <xref:System.Linq.Enumerable.Select%2A>-LINQ-Methode zu verwenden, damit der Client die `$select`-Abfrageoption im Anforderungs-URI generiert.</span><span class="sxs-lookup"><span data-stu-id="d6c83-151">We recommend that you use the LINQ <xref:System.Linq.Enumerable.Select%2A> method to have the client generate the `$select` query option in the request URI.</span></span>  
  
 <span data-ttu-id="d6c83-152">Die obigen Beispiele werden beide in den Abfrage-URI übersetzt: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.</span><span class="sxs-lookup"><span data-stu-id="d6c83-152">Both of the previous examples are translated to the query URI: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.</span></span>  
  
<a name="paging"></a>

### <a name="client-paging"></a><span data-ttu-id="d6c83-153">Clientpaging</span><span class="sxs-lookup"><span data-stu-id="d6c83-153">Client Paging</span></span>  

 <span data-ttu-id="d6c83-154">Die folgenden Beispiele zeigen funktional gleichwertige Abfragen, durch die eine Seite sortierter Order-Entitäten angefordert wird, die 25 Aufträge enthält und auf der die ersten 50 Aufträge übersprungen werden:</span><span class="sxs-lookup"><span data-stu-id="d6c83-154">The following examples show equivalent queries that request a page of sorted order entities that includes 25 orders, skipping the first 50 orders:</span></span>  
  
- <span data-ttu-id="d6c83-155">Anwendung von Abfragemethoden auf eine LINQ-Abfrage:</span><span class="sxs-lookup"><span data-stu-id="d6c83-155">Applying query methods to a LINQ query:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqskiptakemethodspecific)]
  
- <span data-ttu-id="d6c83-156">`$skip`- und `$top`-Optionen für die URI-Abfragezeichenfolge:</span><span class="sxs-lookup"><span data-stu-id="d6c83-156">URI query string `$skip` and `$top` options):</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryskiptakemethodspecific)]
  
 <span data-ttu-id="d6c83-157">Die obigen Beispiele werden beide in den Abfrage-URI übersetzt: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.</span><span class="sxs-lookup"><span data-stu-id="d6c83-157">Both of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.</span></span>  
  
<a name="expand"></a>

### <a name="expand"></a><span data-ttu-id="d6c83-158">Expand</span><span class="sxs-lookup"><span data-stu-id="d6c83-158">Expand</span></span>  

 <span data-ttu-id="d6c83-159">Wenn Sie einen odata-Datendienst Abfragen, können Sie anfordern, dass Entitäten im Zusammenhang mit der Entität, die von der Abfrage betroffen ist, den zurückgegebenen Feed einschließen.</span><span class="sxs-lookup"><span data-stu-id="d6c83-159">When you query an OData data service, you can request that entities related to the entity targeted by the query be included the returned feed.</span></span> <span data-ttu-id="d6c83-160">Die <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>-Methode wird in der <xref:System.Data.Services.Client.DataServiceQuery%601> für die in der LINQ-Abfrage angegebene Entität aufgerufen, und der Name der verknüpften Entitätenmenge wird als `path`-Parameter angegeben.</span><span class="sxs-lookup"><span data-stu-id="d6c83-160">The <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is called on the <xref:System.Data.Services.Client.DataServiceQuery%601> for the entity set targeted by the LINQ query, with the related entity set name supplied as the `path` parameter.</span></span> <span data-ttu-id="d6c83-161">Weitere Informationen finden Sie unter [Laden von verzögertem Inhalt](loading-deferred-content-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d6c83-161">For more information, see [Loading Deferred Content](loading-deferred-content-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="d6c83-162">Die folgenden Beispiele zeigen funktional gleichwertige Möglichkeiten zur Verwendung der <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>-Methode in einer Abfrage:</span><span class="sxs-lookup"><span data-stu-id="d6c83-162">The following examples show equivalent ways to use the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method in a query:</span></span>  
  
- <span data-ttu-id="d6c83-163">In der LINQ-Abfragesyntax:</span><span class="sxs-lookup"><span data-stu-id="d6c83-163">In LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandspecific)]  
  
- <span data-ttu-id="d6c83-164">Mit LINQ-Abfragemethoden:</span><span class="sxs-lookup"><span data-stu-id="d6c83-164">With LINQ query methods:</span></span>  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandmethodspecific)]

 <span data-ttu-id="d6c83-165">Die obigen Beispiele werden beide in den Abfrage-URI übersetzt: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.</span><span class="sxs-lookup"><span data-stu-id="d6c83-165">Both of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.</span></span>  
  
<a name="unsupportedMethods"></a>

## <a name="unsupported-linq-methods"></a><span data-ttu-id="d6c83-166">Nicht unterstützte LINQ-Methoden</span><span class="sxs-lookup"><span data-stu-id="d6c83-166">Unsupported LINQ Methods</span></span>  

 <span data-ttu-id="d6c83-167">Die folgende Tabelle enthält die Klassen von LINQ-Methoden, die nicht unterstützt werden und nicht in einer Abfrage enthalten sein können, die für einen odata-Dienst ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="d6c83-167">The following table contains the classes of LINQ methods are not supported and cannot be included in a query executed against an OData service:</span></span>  
  
|<span data-ttu-id="d6c83-168">Vorgangstyp</span><span class="sxs-lookup"><span data-stu-id="d6c83-168">Operation Type</span></span>|<span data-ttu-id="d6c83-169">Nicht unterstützte Methode</span><span class="sxs-lookup"><span data-stu-id="d6c83-169">Unsupported Method</span></span>|  
|--------------------|------------------------|  
|<span data-ttu-id="d6c83-170">Mengenoperatoren</span><span class="sxs-lookup"><span data-stu-id="d6c83-170">Set operators</span></span>|<span data-ttu-id="d6c83-171">Alle Mengenoperatoren werden nicht für eine <xref:System.Data.Services.Client.DataServiceQuery%601> unterstützt. Dazu zählen folgende Operatoren:</span><span class="sxs-lookup"><span data-stu-id="d6c83-171">All set operators are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, which included the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|<span data-ttu-id="d6c83-172">Sortierungsoperatoren</span><span class="sxs-lookup"><span data-stu-id="d6c83-172">Ordering operators</span></span>|<span data-ttu-id="d6c83-173">Die folgenden Sortierungsoperatoren, die <xref:System.Collections.Generic.IComparer%601> erfordern, werden für eine <xref:System.Data.Services.Client.DataServiceQuery%601> nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="d6c83-173">The following ordering operators that require <xref:System.Collections.Generic.IComparer%601> are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|<span data-ttu-id="d6c83-174">Projektions- und Filterungsoperatoren</span><span class="sxs-lookup"><span data-stu-id="d6c83-174">Projection and filtering operators</span></span>|<span data-ttu-id="d6c83-175">Die folgenden Projektions- und Filterungsoperatoren, die ein Positionsargument akzeptieren, werden für eine <xref:System.Data.Services.Client.DataServiceQuery%601> nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="d6c83-175">The following projection and filtering operators that accept a positional argument are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|<span data-ttu-id="d6c83-176">Gruppierungsoperatoren</span><span class="sxs-lookup"><span data-stu-id="d6c83-176">Grouping operators</span></span>|<span data-ttu-id="d6c83-177">Alle Gruppierungsoperatoren werden nicht für eine <xref:System.Data.Services.Client.DataServiceQuery%601> unterstützt. Dazu zählen folgende Operatoren:</span><span class="sxs-lookup"><span data-stu-id="d6c83-177">All grouping operators are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, including the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> <span data-ttu-id="d6c83-178">Gruppierungsvorgänge müssen auf dem Client ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d6c83-178">Grouping operations must be performed on the client.</span></span>|  
|<span data-ttu-id="d6c83-179">Aggregatoperatoren</span><span class="sxs-lookup"><span data-stu-id="d6c83-179">Aggregate operators</span></span>|<span data-ttu-id="d6c83-180">Alle Aggregatoperatoren werden nicht für eine <xref:System.Data.Services.Client.DataServiceQuery%601> unterstützt. Dazu zählen folgende Operatoren:</span><span class="sxs-lookup"><span data-stu-id="d6c83-180">All aggregate operations are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, including the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> <span data-ttu-id="d6c83-181">Aggregatvorgänge müssen entweder auf dem Client ausgeführt oder von einem Dienstvorgang gekapselt werden.</span><span class="sxs-lookup"><span data-stu-id="d6c83-181">Aggregate operations must either be performed on the client or be encapsulated by a service operation.</span></span>|  
|<span data-ttu-id="d6c83-182">Pagingoperatoren</span><span class="sxs-lookup"><span data-stu-id="d6c83-182">Paging operators</span></span>|<span data-ttu-id="d6c83-183">Die folgenden Pagingoperatoren werden nicht für eine <xref:System.Data.Services.Client.DataServiceQuery%601> unterstützt:</span><span class="sxs-lookup"><span data-stu-id="d6c83-183">The following paging operators are not supported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A><br/><br/><span data-ttu-id="d6c83-184">**Hinweis:**  Pagingoperatoren, die für eine leere Sequenz ausgeführt werden, geben NULL zurück.</span><span class="sxs-lookup"><span data-stu-id="d6c83-184">**Note:**  Paging operators that are executed on an empty sequence return null.</span></span>|  
|<span data-ttu-id="d6c83-185">Andere Operatoren</span><span class="sxs-lookup"><span data-stu-id="d6c83-185">Other operators</span></span>|<span data-ttu-id="d6c83-186">Die folgenden Operatoren werden auch nicht für eine unterstützt <xref:System.Data.Services.Client.DataServiceQuery%601> :</span><span class="sxs-lookup"><span data-stu-id="d6c83-186">The following operators are also not supported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> - <xref:System.Linq.Enumerable.Empty%2A><br />- <xref:System.Linq.Enumerable.Range%2A><br />- <xref:System.Linq.Enumerable.Repeat%2A><br />- <xref:System.Linq.Enumerable.ToDictionary%2A><br />- <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>

## <a name="supported-expression-functions"></a><span data-ttu-id="d6c83-187">Unterstützte Ausdrucksfunktionen</span><span class="sxs-lookup"><span data-stu-id="d6c83-187">Supported Expression Functions</span></span>  

 <span data-ttu-id="d6c83-188">Die folgenden CLR (Common Language Runtime)-Methoden und-Eigenschaften werden unterstützt, da Sie in einen Abfrage Ausdruck konvertiert werden können, um Sie in den Anforderungs-URI für einen odata-Dienst einzubeziehen:</span><span class="sxs-lookup"><span data-stu-id="d6c83-188">The following common-language runtime (CLR) methods and properties are supported because they can be translated in a query expression for inclusion in the request URI to an OData service:</span></span>  
  
|<span data-ttu-id="d6c83-189"><xref:System.String>-Member</span><span class="sxs-lookup"><span data-stu-id="d6c83-189"><xref:System.String> Member</span></span>|<span data-ttu-id="d6c83-190">Unterstützte odata-Funktion</span><span class="sxs-lookup"><span data-stu-id="d6c83-190">Supported OData Function</span></span>|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<span data-ttu-id="d6c83-191"><xref:System.DateTime> Mitglied<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d6c83-191"><xref:System.DateTime> Member<sup>1</sup></span></span>|<span data-ttu-id="d6c83-192">Unterstützte odata-Funktion</span><span class="sxs-lookup"><span data-stu-id="d6c83-192">Supported OData Function</span></span>|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <span data-ttu-id="d6c83-193"><sup>1</sup> Die entsprechenden Datums-und Uhrzeit Eigenschaften von <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType> und die- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> Methode in Visual Basic werden ebenfalls unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d6c83-193"><sup>1</sup>The equivalent date and time properties of <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType> and the <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> method in Visual Basic are also supported.</span></span>  
  
|<span data-ttu-id="d6c83-194"><xref:System.Math>-Member</span><span class="sxs-lookup"><span data-stu-id="d6c83-194"><xref:System.Math> Member</span></span>|<span data-ttu-id="d6c83-195">Unterstützte odata-Funktion</span><span class="sxs-lookup"><span data-stu-id="d6c83-195">Supported OData Function</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<span data-ttu-id="d6c83-196"><xref:System.Linq.Expressions.Expression>-Member</span><span class="sxs-lookup"><span data-stu-id="d6c83-196"><xref:System.Linq.Expressions.Expression> Member</span></span>|<span data-ttu-id="d6c83-197">Unterstützte odata-Funktion</span><span class="sxs-lookup"><span data-stu-id="d6c83-197">Supported OData Function</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 <span data-ttu-id="d6c83-198">Der Client kann möglicherweise auch weitere CLR-Funktionen auf dem Client auswerten.</span><span class="sxs-lookup"><span data-stu-id="d6c83-198">The client may also be able to evaluate additional CLR functions on the client.</span></span> <span data-ttu-id="d6c83-199">Für einen Ausdruck, der nicht auf dem Client ausgewertet und nicht in einen gültigen URI für die Auswertung auf dem Server übersetzt werden kann, wird eine <xref:System.NotSupportedException> ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d6c83-199">A <xref:System.NotSupportedException> is raised for any expression that cannot be evaluated on the client and cannot be translated into a valid request URI for evaluation on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c83-200">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d6c83-200">See also</span></span>

- [<span data-ttu-id="d6c83-201">Abfragen des Datendiensts</span><span class="sxs-lookup"><span data-stu-id="d6c83-201">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)
- [<span data-ttu-id="d6c83-202">Abfrageprojektionen</span><span class="sxs-lookup"><span data-stu-id="d6c83-202">Query Projections</span></span>](query-projections-wcf-data-services.md)
- [<span data-ttu-id="d6c83-203">Objektmaterialisierung</span><span class="sxs-lookup"><span data-stu-id="d6c83-203">Object Materialization</span></span>](object-materialization-wcf-data-services.md)
- [<span data-ttu-id="d6c83-204">OData: URI-Konventionen</span><span class="sxs-lookup"><span data-stu-id="d6c83-204">OData: URI Conventions</span></span>](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)
