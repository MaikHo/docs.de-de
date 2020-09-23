---
title: Aufrufen von XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 8ffe6d5ed368aee6d6984ec6ab28c8832921a3f8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080178"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="069a4-102">Zugreifen auf XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="069a4-102">Accessing XML in Visual Basic</span></span>

<span data-ttu-id="069a4-103">Visual Basic stellt XML-Achsen Eigenschaften zum Zugreifen auf und Navigieren in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Strukturen bereit.</span><span class="sxs-lookup"><span data-stu-id="069a4-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="069a4-104">Diese Eigenschaften verwenden eine spezielle Syntax, damit Sie auf Elemente und Attribute zugreifen können, indem Sie die XML-Namen angeben.</span><span class="sxs-lookup"><span data-stu-id="069a4-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="069a4-105">In der folgenden Tabelle sind die sprach Features aufgelistet, die Ihnen den Zugriff auf XML-Elemente und-Attribute in Visual Basic ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="069a4-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="069a4-106">XML-Achseneigenschaften</span><span class="sxs-lookup"><span data-stu-id="069a4-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="069a4-107">Beschreibung der Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="069a4-107">Property description</span></span>|<span data-ttu-id="069a4-108">Beispiel</span><span class="sxs-lookup"><span data-stu-id="069a4-108">Example</span></span>|<span data-ttu-id="069a4-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="069a4-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="069a4-110">*Untergeordnete Achse*</span><span class="sxs-lookup"><span data-stu-id="069a4-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="069a4-111">Ruft alle- `phone` Elemente ab, die untergeordnete Elemente des- `contact` Elements sind.</span><span class="sxs-lookup"><span data-stu-id="069a4-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="069a4-112">*Attributachse*</span><span class="sxs-lookup"><span data-stu-id="069a4-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="069a4-113">Ruft alle `type` Attribute des `phone` Elements ab.</span><span class="sxs-lookup"><span data-stu-id="069a4-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="069a4-114">*descendant-Achse*</span><span class="sxs-lookup"><span data-stu-id="069a4-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="069a4-115">Ruft alle `name` Elemente des- `contacts` Elements ab, unabhängig davon, wie tief Sie in der Hierarchie vorkommen.</span><span class="sxs-lookup"><span data-stu-id="069a4-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="069a4-116">*Erweiterungsindexer*</span><span class="sxs-lookup"><span data-stu-id="069a4-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="069a4-117">Ruft das erste `name` Element aus der Sequenz ab.</span><span class="sxs-lookup"><span data-stu-id="069a4-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="069a4-118">*value*</span><span class="sxs-lookup"><span data-stu-id="069a4-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="069a4-119">Ruft die Zeichen folgen Darstellung des ersten Objekts in der Sequenz ab, oder, `Nothing` Wenn die Sequenz leer ist.</span><span class="sxs-lookup"><span data-stu-id="069a4-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="069a4-120">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="069a4-120">In This Section</span></span>  

 [<span data-ttu-id="069a4-121">Vorgehensweise: Zugreifen auf XML-Nachfolgerelemente</span><span class="sxs-lookup"><span data-stu-id="069a4-121">How to: Access XML Descendant Elements</span></span>](how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="069a4-122">Zeigt, wie Sie mithilfe einer untergeordneten Achsen Eigenschaft auf alle XML-Elemente zugreifen, die einen angegebenen Namen aufweisen und die unter einem angegebenen XML-Element enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="069a4-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="069a4-123">Vorgehensweise: Zugreifen auf untergeordnete XML-Elemente</span><span class="sxs-lookup"><span data-stu-id="069a4-123">How to: Access XML Child Elements</span></span>](how-to-access-xml-child-elements.md)  
 <span data-ttu-id="069a4-124">Zeigt, wie Sie mit einer untergeordneten Achsen Eigenschaft auf alle untergeordneten XML-Elemente zugreifen, die einen angegebenen Namen in einem XML-Element aufweisen.</span><span class="sxs-lookup"><span data-stu-id="069a4-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="069a4-125">Vorgehensweise: Zugreifen auf XML-Attribute</span><span class="sxs-lookup"><span data-stu-id="069a4-125">How to: Access XML Attributes</span></span>](how-to-access-xml-attributes.md)  
 <span data-ttu-id="069a4-126">Zeigt, wie eine Attribut Achsen Eigenschaft für den Zugriff auf alle XML-Attribute mit einem angegebenen Namen in einem XML-Element verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="069a4-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="069a4-127">Vorgehensweise: Deklarieren und Verwenden von XML-Namespacepräfixen</span><span class="sxs-lookup"><span data-stu-id="069a4-127">How to: Declare and Use XML Namespace Prefixes</span></span>](how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="069a4-128">Zeigt, wie ein XML-Namespace Präfix deklariert und zum Erstellen und Zugreifen auf XML-Elemente verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="069a4-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="069a4-129">Verwandte Abschnitte</span><span class="sxs-lookup"><span data-stu-id="069a4-129">Related Sections</span></span>  

 [<span data-ttu-id="069a4-130">XML-Achseneigenschaften</span><span class="sxs-lookup"><span data-stu-id="069a4-130">XML Axis Properties</span></span>](../../../language-reference/xml-axis/index.md)  
 <span data-ttu-id="069a4-131">Enthält Links zu Abschnitten, in denen die verschiedenen XML-Zugriffs Eigenschaften beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="069a4-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="069a4-132">Übersicht über LINQ to XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="069a4-132">Overview of LINQ to XML in Visual Basic</span></span>](overview-of-linq-to-xml.md)  
 <span data-ttu-id="069a4-133">Bietet eine Einführung in die Verwendung von [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="069a4-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="069a4-134">Erstellen von XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="069a4-134">Creating XML in Visual Basic</span></span>](creating-xml.md)  
 <span data-ttu-id="069a4-135">Bietet eine Einführung in die Verwendung von XML-Literalen in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="069a4-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="069a4-136">Bearbeiten von XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="069a4-136">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)  
 <span data-ttu-id="069a4-137">Enthält Links zu Abschnitten über das Laden und Ändern von XML in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="069a4-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="069a4-138">XML</span><span class="sxs-lookup"><span data-stu-id="069a4-138">XML</span></span>](index.md)  
 <span data-ttu-id="069a4-139">Enthält Links zu Abschnitten, in denen die Verwendung von [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="069a4-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
