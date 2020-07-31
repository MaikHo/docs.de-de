---
title: 'Vorgehensweise: Auffangen von Parsingfehlern (C#)'
description: Dieses Beispiel für LINQ to XML in C# erkennt falsch formatierte oder ungültige XML-Daten. LINQ to XML verwendet die XmlReader-Klasse, die eine Ausnahme für falsch formatierte oder ungültige XML-Daten auslöst.
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 0a891097322ef6acce062ea927692b01cc425e6c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105410"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="aa249-104">Vorgehensweise: Auffangen von Parsingfehlern (C#)</span><span class="sxs-lookup"><span data-stu-id="aa249-104">How to catch parsing errors (C#)</span></span>
<span data-ttu-id="aa249-105">In diesem Thema wird gezeigt, wie nicht wohlgeformter oder ungültiger XML-Code erkannt werden kann.</span><span class="sxs-lookup"><span data-stu-id="aa249-105">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="aa249-106">wird mithilfe von <xref:System.Xml.XmlReader> implementiert.</span><span class="sxs-lookup"><span data-stu-id="aa249-106">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="aa249-107">Wenn nicht wohlgeformter oder ungültiger XML-Code an [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] übergeben wird, löst die zugrunde liegende <xref:System.Xml.XmlReader>-Klasse eine Ausnahme aus.</span><span class="sxs-lookup"><span data-stu-id="aa249-107">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="aa249-108">Die verschiedenen Methoden, die XML analysieren, z.B. <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, fangen die Ausnahme nicht ab. Die Ausnahme kann dann von Ihrer Anwendung abgefangen werden.</span><span class="sxs-lookup"><span data-stu-id="aa249-108">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa249-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="aa249-109">Example</span></span>  
 <span data-ttu-id="aa249-110">Der folgende Code versucht, ungültiges XML zu analysieren:</span><span class="sxs-lookup"><span data-stu-id="aa249-110">The following code tries to parse invalid XML:</span></span>  
  
```csharp  
try {  
    XElement contacts = XElement.Parse(  
        @"<Contacts>  
            <Contact>  
                <Name>Jim Wilson</Name>  
            </Contact>  
          </Contcts>");  
  
    Console.WriteLine(contacts);  
}  
catch (System.Xml.XmlException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
 <span data-ttu-id="aa249-111">Wenn Sie diesen Code ausführen, wird die folgende Ausnahme ausgelöst:</span><span class="sxs-lookup"><span data-stu-id="aa249-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="aa249-112">Weitere Informationen zu den Ausnahmen, von denen Sie ausgehen können, dass sie von den Methoden <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> und <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> ausgelöst werden, finden Sie in der <xref:System.Xml.XmlReader>-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="aa249-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  