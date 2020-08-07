---
title: Form von WordprocessingML-Dokumenten (C#)
description: Erfahren Sie mehr über das Format eines WordprocessingML-Dokuments. Verschiedene C#-Beispiele verwenden ein WordprocessingML-Dokument.
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 4a7716d775a634c5ad3719714be68fce67d5cbfe
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302346"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="0d2ae-104">Form von WordprocessingML-Dokumenten (C#)</span><span class="sxs-lookup"><span data-stu-id="0d2ae-104">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="0d2ae-105">Dieses Thema enthält eine Einführung in die XML-Form von WordprocessingML-Dokumenten.</span><span class="sxs-lookup"><span data-stu-id="0d2ae-105">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="0d2ae-106">Microsoft Office-Formate</span><span class="sxs-lookup"><span data-stu-id="0d2ae-106">Microsoft Office Formats</span></span>  
 <span data-ttu-id="0d2ae-107">Das systemeigene Dateiformat für das 2007 Microsoft Office-System ist Office Open XML (häufig als Open XML bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="0d2ae-107">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="0d2ae-108">Open XML ist ein XML-basiertes Format, das von der Ecma als Standard übernommen wurde und für das die ISO-IEC-Standardisierung beantragt wurde.</span><span class="sxs-lookup"><span data-stu-id="0d2ae-108">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="0d2ae-109">Die Markupsprache für Textverarbeitungsdateien innerhalb von Open XML heißt WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="0d2ae-109">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="0d2ae-110">Dieses Lernprogramm verwendet als Eingabe für die Beispiele WordprocessingML-Quelldateien.</span><span class="sxs-lookup"><span data-stu-id="0d2ae-110">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="0d2ae-111">Benutzer von Microsoft Office 2003 müssen Microsoft Office Compatibility Pack für Word, Excel und PowerPoint 2007-Dateiformate installiert haben, um Dokumente im Office Open XML-Format speichern zu können.</span><span class="sxs-lookup"><span data-stu-id="0d2ae-111">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="0d2ae-112">Form der WordprocessingML-Dokumente</span><span class="sxs-lookup"><span data-stu-id="0d2ae-112">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="0d2ae-113">Als Erstes sollten Sie die Form von WordprocessingML-Dokumenten verstehen.</span><span class="sxs-lookup"><span data-stu-id="0d2ae-113">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="0d2ae-114">WordprocessingML-Dokumente enthalten ein Textkörperelement (mit der Bezeichnung `w:body`) mit den Absätzen des Dokuments.</span><span class="sxs-lookup"><span data-stu-id="0d2ae-114">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="0d2ae-115">Jeder Absatz enthält mindestens einen Textrun (mit der Bezeichnung `w:r`).</span><span class="sxs-lookup"><span data-stu-id="0d2ae-115">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="0d2ae-116">Jeder Textrun enthält mindestens ein Textstück (mit der Bezeichnung `w:t`).</span><span class="sxs-lookup"><span data-stu-id="0d2ae-116">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="0d2ae-117">Das folgende Beispiel ist ein sehr einfaches WordprocessingML-Dokument:</span><span class="sxs-lookup"><span data-stu-id="0d2ae-117">The following is a very simple WordprocessingML document:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 <span data-ttu-id="0d2ae-118">Dieses Dokument besteht aus zwei Absätzen.</span><span class="sxs-lookup"><span data-stu-id="0d2ae-118">This document contains two paragraphs.</span></span> <span data-ttu-id="0d2ae-119">Beide Absätze enthalten genau einen Textrun, und jeder Textrun enthält genau ein Textstück.</span><span class="sxs-lookup"><span data-stu-id="0d2ae-119">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="0d2ae-120">Die einfachste Möglichkeit, sich den Inhalt eines WordprocessingML-Dokuments in XML-Form anzusehen, besteht darin, ein WordprocessingML-Dokument in Microsoft Word zu erstellen, das Dokument zu speichern und dann das folgende Programm zum Ausgeben des XML-Codes auf der Konsole auszuführen:</span><span class="sxs-lookup"><span data-stu-id="0d2ae-120">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="0d2ae-121">Dieses Beispiel verwendet Klassen aus der <legacyBold>WindowsBase</legacyBold>-Assembly.</span><span class="sxs-lookup"><span data-stu-id="0d2ae-121">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="0d2ae-122">Außerdem werden Typen im <xref:System.IO.Packaging?displayProperty=nameWithType>-Namespace verwendet.</span><span class="sxs-lookup"><span data-stu-id="0d2ae-122">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="0d2ae-123">Externe Ressourcen</span><span class="sxs-lookup"><span data-stu-id="0d2ae-123">External resources</span></span>

- [<span data-ttu-id="0d2ae-124">Einführung in die Microsoft Office (2007) Open XML-Dateiformate</span><span class="sxs-lookup"><span data-stu-id="0d2ae-124">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- [<span data-ttu-id="0d2ae-125">Übersicht über WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="0d2ae-125">Overview of WordprocessingML</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)
- [<span data-ttu-id="0d2ae-126">Anatomy of a WordProcessingML File (Aufbau einer WordprocessingML-Datei)</span><span class="sxs-lookup"><span data-stu-id="0d2ae-126">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)
- [<span data-ttu-id="0d2ae-127">Introduction to WordprocessingML (Einführung in WordprocessingML)</span><span class="sxs-lookup"><span data-stu-id="0d2ae-127">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a><span data-ttu-id="0d2ae-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0d2ae-128">See also</span></span>

- [<span data-ttu-id="0d2ae-129">Tutorial: Bearbeiten von Inhalten in einem WordprocessingML-Dokument (C#)</span><span class="sxs-lookup"><span data-stu-id="0d2ae-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
