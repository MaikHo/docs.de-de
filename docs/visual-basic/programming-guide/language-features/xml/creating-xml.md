---
title: Erstellen von XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: a6a927c8dc1a4f3e38a99a1f730be68a2566d048
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090026"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="dc9c1-102">Erstellen von XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc9c1-102">Creating XML in Visual Basic</span></span>

<span data-ttu-id="dc9c1-103">Mit Visual Basic können Sie *XML-Literale* direkt in Ihrem Code verwenden.</span><span class="sxs-lookup"><span data-stu-id="dc9c1-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="dc9c1-104">Die XML-Literalsyntax stellt [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] -Objekte dar und ähnelt der Syntax von XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="dc9c1-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="dc9c1-105">Dadurch wird das programmgesteuerte Erstellen von XML-Elementen,-Dokumenten und-Fragmenten vereinfacht, da der Code die gleiche Struktur wie der endgültige XML-Code aufweist.</span><span class="sxs-lookup"><span data-stu-id="dc9c1-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc9c1-106">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="dc9c1-106">In This Section</span></span>  
  
|<span data-ttu-id="dc9c1-107">Begriff</span><span class="sxs-lookup"><span data-stu-id="dc9c1-107">Term</span></span>|<span data-ttu-id="dc9c1-108">Definition</span><span class="sxs-lookup"><span data-stu-id="dc9c1-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="dc9c1-109">Übersicht über XML-Literale</span><span class="sxs-lookup"><span data-stu-id="dc9c1-109">XML Literals Overview</span></span>](xml-literals-overview.md)|<span data-ttu-id="dc9c1-110">Einführung in XML-Literale und deren Beziehung [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dc9c1-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="dc9c1-111">Eingebettete Ausdrücke in XML</span><span class="sxs-lookup"><span data-stu-id="dc9c1-111">Embedded Expressions in XML</span></span>](embedded-expressions-in-xml.md)|<span data-ttu-id="dc9c1-112">Beschreibt, wie eingebettete Ausdrücke in XML-Literalen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="dc9c1-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="dc9c1-113">Vorgehensweise: Erstellen von XML-Literalen</span><span class="sxs-lookup"><span data-stu-id="dc9c1-113">How to: Create XML Literals</span></span>](how-to-create-xml-literals.md)|<span data-ttu-id="dc9c1-114">Beschreibt, wie ein XML-Element im Code mithilfe eines XML-Literals erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="dc9c1-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="dc9c1-115">Leerzeichen in XML-Literalen</span><span class="sxs-lookup"><span data-stu-id="dc9c1-115">White Space in XML Literals</span></span>](white-space-in-xml-literals.md)|<span data-ttu-id="dc9c1-116">Beschreibt, wie Visual Basic Leerraum in XML-Literalen behandelt.</span><span class="sxs-lookup"><span data-stu-id="dc9c1-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="dc9c1-117">XML-Literale und die XML 1.0-Spezifikation</span><span class="sxs-lookup"><span data-stu-id="dc9c1-117">XML Literals and the XML 1.0 Specification</span></span>](xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="dc9c1-118">Beschreibt, wie die XML-Literalsyntax in Visual Basic mit der XML 1,0-Spezifikation verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="dc9c1-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="dc9c1-119">Vorgehensweise: Einbetten von Ausdrücken in XML-Literale</span><span class="sxs-lookup"><span data-stu-id="dc9c1-119">How to: Embed Expressions in XML Literals</span></span>](how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="dc9c1-120">Beschreibt, wie eingebettete Ausdrücke in XML-Literalen verwendet werden, um Inhalte zur Laufzeit zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="dc9c1-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="dc9c1-121">Namen von deklarierten XML-Elementen und Attributen</span><span class="sxs-lookup"><span data-stu-id="dc9c1-121">Names of Declared XML Elements and Attributes</span></span>](names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="dc9c1-122">Beschreibt Richtlinien für das Benennen von XML-Elementen und-Attributen.</span><span class="sxs-lookup"><span data-stu-id="dc9c1-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc9c1-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="dc9c1-123">See also</span></span>

- [<span data-ttu-id="dc9c1-124">XML</span><span class="sxs-lookup"><span data-stu-id="dc9c1-124">XML</span></span>](index.md)
