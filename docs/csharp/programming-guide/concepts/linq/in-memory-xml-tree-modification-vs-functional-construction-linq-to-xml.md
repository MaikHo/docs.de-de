---
title: Änderung der XML-Struktur im Arbeitsspeicher und Funktionale Konstruktion (LINQ to XML) (C#)
description: Diese Beispiele ändern die Form eines XML-Dokuments, indem es direkt bearbeitet und die funktionale LINQ to XML-Konstruktion in C# verwendet wird.
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 7a2e3d2ddcd452cf6a58e9d5cc886f3e8b8dd325
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165782"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a><span data-ttu-id="1be70-103">Änderung der XML-Struktur im Arbeitsspeicher und Funktionale Konstruktion (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1be70-103">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>
<span data-ttu-id="1be70-104">Zur Änderung der Form eines XML-Dokuments wird üblicherweise die XML-Struktur an Ort und Stelle geändert.</span><span class="sxs-lookup"><span data-stu-id="1be70-104">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="1be70-105">Eine typische Anwendung lädt ein Dokument in einen Datenspeicher, z. B. DOM oder [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], verwendet eine Programmierschnittstelle, um Knoten einzufügen, zu löschen oder zu ändern, und speichert den XML-Code dann in einer Datei bzw. überträgt ihn über ein Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="1be70-105">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="1be70-106">ermöglicht eine andere Herangehensweise, die sich in vielen Szenarios als hilfreich erweist: *die funktionale Konstruktion*.</span><span class="sxs-lookup"><span data-stu-id="1be70-106">enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="1be70-107">Bei der funktionalen Konstruktion wird das Ändern von Daten als ein Transformationsproblem und nicht als detaillierte Manipulation eines Datenspeichers angesehen.</span><span class="sxs-lookup"><span data-stu-id="1be70-107">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="1be70-108">Wenn Sie eine Datendarstellung effizient von einer Form in eine andere Form transformieren können, sieht das Ergebnis genauso aus, als hätten Sie einen Datenspeicher so manipuliert, dass er eine andere Form erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="1be70-108">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="1be70-109">Ein entscheidender Punkt bei der funktionalen Konstruktion ist die Übergabe der Ergebnisse von Abfragen an die Konstruktoren <xref:System.Xml.Linq.XDocument> und <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1be70-109">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="1be70-110">Das Schreiben des Transformationscodes kostet Sie häufig nur einen Bruchteil der Zeit, die Sie für die Manipulation des Datenspeichers hätten aufwenden müssen, und der Code ist robuster und leichter zu unterhalten.</span><span class="sxs-lookup"><span data-stu-id="1be70-110">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="1be70-111">In diesen Fällen ist die Verwendung von Transformationscode die effektivere Möglichkeit, Daten zu ändern, auch wenn die Transformation mehr CPU-Leistung beansprucht.</span><span class="sxs-lookup"><span data-stu-id="1be70-111">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="1be70-112">Wenn ein Entwickler mit dem funktionalen Ansatz vertraut ist, ist der entstehende Code häufig einfacher zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="1be70-112">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="1be70-113">Es ist dann auch leichter, den Code zu finden, der die einzelnen Teile der Struktur ändert.</span><span class="sxs-lookup"><span data-stu-id="1be70-113">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="1be70-114">Das Ändern einer XML-Struktur an Ort und Stelle ist vielen DOM-Programmierern vertrauter, während Code, der mit dem funktionalen Ansatz geschrieben wurde, für Entwickler, die diesen Ansatz nicht kennen, eher fremd aussieht.</span><span class="sxs-lookup"><span data-stu-id="1be70-114">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="1be70-115">Wenn an einer großen XML-Struktur nur eine kleine Änderung vorgenommen werden muss, wird die CPU durch das Ändern der Struktur an Ort und Stelle weniger beansprucht.</span><span class="sxs-lookup"><span data-stu-id="1be70-115">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="1be70-116">Dieses Thema enthält ein Beispiel, das mit beiden Ansätzen implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="1be70-116">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="1be70-117">Transformieren von Attributen in Elemente</span><span class="sxs-lookup"><span data-stu-id="1be70-117">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="1be70-118">Nehmen wir für dieses Beispiel an, Sie möchten das folgende einfache XML-Dokument so ändern, dass aus den Attributen Elemente werden.</span><span class="sxs-lookup"><span data-stu-id="1be70-118">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="1be70-119">Zunächst wird in diesem Thema der herkömmliche Ansatz gezeigt: das Ändern einer Struktur an Ort und Stelle.</span><span class="sxs-lookup"><span data-stu-id="1be70-119">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="1be70-120">Anschließend wird der Ansatz der funktionalen Konstruktion dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1be70-120">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="1be70-121">Ändern der XML-Struktur</span><span class="sxs-lookup"><span data-stu-id="1be70-121">Modifying the XML Tree</span></span>  
 <span data-ttu-id="1be70-122">Sie können prozeduralen Code zum Erstellen von Elementen aus Attributen schreiben und dann die Attribute löschen. Dies sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="1be70-122">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="1be70-123">Dieser Code erzeugt die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="1be70-123">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="1be70-124">Funktionale Konstruktion</span><span class="sxs-lookup"><span data-stu-id="1be70-124">Functional Construction Approach</span></span>  
 <span data-ttu-id="1be70-125">Bei der funktionalen Konstruktion wird zunächst eine neue Struktur erstellt. Dann werden Elemente und Attribute aus der Quellstruktur ausgewählt und der neuen Struktur hinzugefügt, wobei sie entsprechend transformiert werden.</span><span class="sxs-lookup"><span data-stu-id="1be70-125">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="1be70-126">Der funktionale Ansatz sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="1be70-126">The functional approach looks like the following:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="1be70-127">Dieses Beispiel gibt denselben XML-Code wie das erste Beispiel aus.</span><span class="sxs-lookup"><span data-stu-id="1be70-127">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="1be70-128">Beachten Sie dabei aber, dass Sie beim funktionalen Ansatz die entstehende Struktur des neuen XML-Codes auch tatsächlich sehen können.</span><span class="sxs-lookup"><span data-stu-id="1be70-128">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="1be70-129">Sie können die Erstellung des `Root`-Elements, den Code, der das `Child1`-Element aus der ursprünglichen Struktur abruft, und den Code sehen, der die Attribute aus der Quellstruktur in Elemente in der neuen Struktur transformiert.</span><span class="sxs-lookup"><span data-stu-id="1be70-129">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="1be70-130">Der funktionale Ansatz ist in diesem Beispiel nicht kürzer und auch in keiner Weise einfacher als das erste Beispiel.</span><span class="sxs-lookup"><span data-stu-id="1be70-130">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="1be70-131">Wenn an einer XML-Struktur aber viele Änderungen vorgenommen werden müssen, wird der nicht-funktionale Ansatz ziemlich komplex und in gewisser Weise stumpf.</span><span class="sxs-lookup"><span data-stu-id="1be70-131">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="1be70-132">Im Unterschied dazu erstellen Sie beim funktionalen Ansatz lediglich den gewünschten XML-Code mit entsprechenden eingebetteten Abfragen und Ausdrücken, sodass Sie den gewünschten Inhalt erhalten.</span><span class="sxs-lookup"><span data-stu-id="1be70-132">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="1be70-133">Der funktionale Ansatz erzeugt Code, der leichter zu unterhalten ist.</span><span class="sxs-lookup"><span data-stu-id="1be70-133">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="1be70-134">Beachten Sie, dass der funktionale Ansatz in diesem Fall wahrscheinlich nicht so gut funktioniert wie die direkte Bearbeitung der Struktur.</span><span class="sxs-lookup"><span data-stu-id="1be70-134">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="1be70-135">Das Hauptproblem dabei ist, dass beim funktionalen Ansatz kurzlebigere Objekte entstehen.</span><span class="sxs-lookup"><span data-stu-id="1be70-135">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="1be70-136">Der funktionale Ansatz zahlt sich aber aus, wenn der Programmierer dadurch produktiver wird.</span><span class="sxs-lookup"><span data-stu-id="1be70-136">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="1be70-137">Das hier verwendete Beispiel ist ein sehr einfaches Beispiel, das lediglich dazu dient, die grundlegenden Unterschiede zwischen den beiden Ansätzen zu verdeutlichen.</span><span class="sxs-lookup"><span data-stu-id="1be70-137">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="1be70-138">Beim Transformieren großer XML-Dokumente sind beim funktionalen Ansatz eindeutig größere Produktivitätsgewinne zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="1be70-138">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  