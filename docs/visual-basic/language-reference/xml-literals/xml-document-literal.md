---
title: XML-Dokumentliteral
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: bd1b2f43fce563af431d67b3817b05c7c1048314
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866017"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="f0449-102">XML-Dokumentliteral (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0449-102">XML Document Literal (Visual Basic)</span></span>

<span data-ttu-id="f0449-103">Ein Literalwert, der ein <xref:System.Xml.Linq.XDocument> Objekt darstellt.</span><span class="sxs-lookup"><span data-stu-id="f0449-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0449-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f0449-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="f0449-105">Bestandteile</span><span class="sxs-lookup"><span data-stu-id="f0449-105">Parts</span></span>  
  
|<span data-ttu-id="f0449-106">Begriff</span><span class="sxs-lookup"><span data-stu-id="f0449-106">Term</span></span>|<span data-ttu-id="f0449-107">Definition</span><span class="sxs-lookup"><span data-stu-id="f0449-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="f0449-108">Dies ist optional.</span><span class="sxs-lookup"><span data-stu-id="f0449-108">Optional.</span></span> <span data-ttu-id="f0449-109">Literaler Text, der deklariert, welche Codierung das Dokument verwendet.</span><span class="sxs-lookup"><span data-stu-id="f0449-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="f0449-110">Dies ist optional.</span><span class="sxs-lookup"><span data-stu-id="f0449-110">Optional.</span></span> <span data-ttu-id="f0449-111">LiteralText.</span><span class="sxs-lookup"><span data-stu-id="f0449-111">Literal text.</span></span> <span data-ttu-id="f0449-112">Muss "yes" oder "No" lauten.</span><span class="sxs-lookup"><span data-stu-id="f0449-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="f0449-113">Dies ist optional.</span><span class="sxs-lookup"><span data-stu-id="f0449-113">Optional.</span></span> <span data-ttu-id="f0449-114">Die Liste der XML-Verarbeitungsanweisungen und XML-Kommentare.</span><span class="sxs-lookup"><span data-stu-id="f0449-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="f0449-115">Hat das folgende Format:</span><span class="sxs-lookup"><span data-stu-id="f0449-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="f0449-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="f0449-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="f0449-117">Dabei kann es sich um `piComment` einen der folgenden handeln:</span><span class="sxs-lookup"><span data-stu-id="f0449-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="f0449-118">-   [XML-Verarbeitungs Anweisungs Literale](xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="f0449-118">-   [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="f0449-119">-   [XML-Kommentarliteral.](xml-comment-literal.md)</span><span class="sxs-lookup"><span data-stu-id="f0449-119">-   [XML Comment Literal](xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="f0449-120">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f0449-120">Required.</span></span> <span data-ttu-id="f0449-121">Das Stamm Element des Dokuments.</span><span class="sxs-lookup"><span data-stu-id="f0449-121">Root element of the document.</span></span> <span data-ttu-id="f0449-122">Das Format ist einer der folgenden:</span><span class="sxs-lookup"><span data-stu-id="f0449-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="f0449-123">[XML-Elementliterale](xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="f0449-123">[XML Element Literal](xml-element-literal.md).</span></span></li><li><span data-ttu-id="f0449-124">Eingebetteter Ausdruck des Formulars `<%=` `elementExp` `%>` .</span><span class="sxs-lookup"><span data-stu-id="f0449-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="f0449-125">Der `elementExp` gibt eine der folgenden zurück:</span><span class="sxs-lookup"><span data-stu-id="f0449-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="f0449-126">Ein <xref:System.Xml.Linq.XElement>-Objekt.</span><span class="sxs-lookup"><span data-stu-id="f0449-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="f0449-127">Eine Auflistung, die ein <xref:System.Xml.Linq.XElement> -Objekt und eine beliebige Anzahl von <xref:System.Xml.Linq.XProcessingInstruction> -Objekten und- <xref:System.Xml.Linq.XComment> Objekten enthält.</span><span class="sxs-lookup"><span data-stu-id="f0449-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="f0449-128">Weitere Informationen finden Sie unter [eingebettete Ausdrücke in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f0449-128">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="f0449-129">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="f0449-129">Return Value</span></span>  

 <span data-ttu-id="f0449-130">Ein <xref:System.Xml.Linq.XDocument>-Objekt.</span><span class="sxs-lookup"><span data-stu-id="f0449-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0449-131">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="f0449-131">Remarks</span></span>  

 <span data-ttu-id="f0449-132">Ein XML-Dokumentliteral wird durch die XML-Deklaration am Anfang des Literals identifiziert.</span><span class="sxs-lookup"><span data-stu-id="f0449-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="f0449-133">Obwohl jedes XML-Dokumentliteral genau ein XML-Stamm Element aufweisen muss, kann es eine beliebige Anzahl von XML-Verarbeitungsanweisungen und XML-Kommentaren enthalten.</span><span class="sxs-lookup"><span data-stu-id="f0449-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="f0449-134">Ein XML-Dokumentliteral darf nicht in einem XML-Element vorkommen.</span><span class="sxs-lookup"><span data-stu-id="f0449-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0449-135">Ein XML-Literale kann mehrere Zeilen umfassen, ohne Zeilen Fortsetzungs Zeichen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f0449-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="f0449-136">Auf diese Weise können Sie Inhalte aus einem XML-Dokument kopieren und direkt in ein Visual Basic Programm einfügen.</span><span class="sxs-lookup"><span data-stu-id="f0449-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="f0449-137">Der Visual Basic Compiler konvertiert das XML-Dokumentliteral in Aufrufe der <xref:System.Xml.Linq.XDocument.%23ctor%2A> -und- <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> Konstruktoren.</span><span class="sxs-lookup"><span data-stu-id="f0449-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0449-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f0449-138">Example</span></span>  

 <span data-ttu-id="f0449-139">Im folgenden Beispiel wird ein XML-Dokument erstellt, das eine XML-Deklaration, eine Verarbeitungsanweisung, einen Kommentar und ein-Element enthält, das ein anderes-Element enthält.</span><span class="sxs-lookup"><span data-stu-id="f0449-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="f0449-140">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f0449-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="f0449-141">XML-Verarbeitungsanweisungsliteral</span><span class="sxs-lookup"><span data-stu-id="f0449-141">XML Processing Instruction Literal</span></span>](xml-processing-instruction-literal.md)
- [<span data-ttu-id="f0449-142">XML-Kommentarliteral</span><span class="sxs-lookup"><span data-stu-id="f0449-142">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="f0449-143">XML-Elementliteral</span><span class="sxs-lookup"><span data-stu-id="f0449-143">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="f0449-144">XML-Literale</span><span class="sxs-lookup"><span data-stu-id="f0449-144">XML Literals</span></span>](index.md)
- [<span data-ttu-id="f0449-145">Erstellen von XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0449-145">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="f0449-146">Eingebettete Ausdrücke in XML</span><span class="sxs-lookup"><span data-stu-id="f0449-146">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
