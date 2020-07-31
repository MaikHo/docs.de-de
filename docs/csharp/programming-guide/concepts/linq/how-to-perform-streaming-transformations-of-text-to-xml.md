---
title: 'Vorgehensweise: Durchführen einer Streamingtransformation von Text in XML (C#)'
description: In diesem Artikel erfahren Sie, wie Sie eine Streamingtransformation von XML-Text in C# ausführen. Hierfür wird eine Textdatei zeilenweise gestreamt und eine LINQ-Abfrage zum Verarbeiten der Textdatei verwendet.
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: f933064be70d39b59cf7dbe51b4ee92e5226647a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104744"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="4184c-103">Vorgehensweise: Durchführen einer Streamingtransformation von Text in XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4184c-103">How to perform streaming transformations of text to XML (C#)</span></span>

<span data-ttu-id="4184c-104">Ein Ansatz für die Verarbeitung einer Textdatei besteht darin, eine Erweiterungsmethode zu schreiben, die die Textdatei mit dem `yield return`-Konstrukt zeilenweise streamt.</span><span class="sxs-lookup"><span data-stu-id="4184c-104">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="4184c-105">Anschließend können Sie eine LINQ-Abfrage schreiben, die die Textdatei verzögert verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="4184c-105">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="4184c-106">Wenn Sie dann die Ausgabe mit <xref:System.Xml.Linq.XStreamingElement> streamen, erstellen Sie eine Transformation der Textdatei in XML, die, unabhängig von der Größe der ursprünglichen Textdatei, nur einen minimalen Teil des Arbeitsspeichers beansprucht.</span><span class="sxs-lookup"><span data-stu-id="4184c-106">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

 <span data-ttu-id="4184c-107">Beim Streamen von Transformationen gilt es jedoch, einige Punkte zu beachten.</span><span class="sxs-lookup"><span data-stu-id="4184c-107">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="4184c-108">Streamingtransformationen eignen sich am besten in Situationen, in denen Sie die gesamte Datei auf einmal verarbeiten können und in denen Sie die Zeilen in derselben Reihenfolge wie im ursprünglichen Dokument verarbeiten können.</span><span class="sxs-lookup"><span data-stu-id="4184c-108">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="4184c-109">Wenn Sie die Datei mehr als einmal verarbeiten müssen oder wenn Sie vor der Verarbeitung der Zeilen deren Reihenfolge ändern müssen, gehen viele Vorteile des Streamingverfahrens verloren.</span><span class="sxs-lookup"><span data-stu-id="4184c-109">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>

## <a name="example"></a><span data-ttu-id="4184c-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4184c-110">Example</span></span>

 <span data-ttu-id="4184c-111">In diesem Beispiel wird die folgende Textdatei, <legacyBold>People.txt</legacyBold>, als Quelldatei verwendet:</span><span class="sxs-lookup"><span data-stu-id="4184c-111">The following text file, People.txt, is the source for this example.</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 <span data-ttu-id="4184c-112">Der folgende Code enthält eine Erweiterungsmethode, die die Zeilen der Textdatei verzögert streamt.</span><span class="sxs-lookup"><span data-stu-id="4184c-112">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>

```csharp
public static class StreamReaderSequence
{
    public static IEnumerable<string> Lines(this StreamReader source)
    {
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
        while ((line = source.ReadLine()) != null)
        {
            yield return line;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
            from line in sr.Lines()
            let items = line.Split(',')
            where !line.StartsWith("#")
            select new XElement("Person",
                       new XAttribute("ID", items[0]),
                       new XElement("First", items[1]),
                       new XElement("Last", items[2]),
                       new XElement("Occupation", items[3])
                   )
        );
        Console.WriteLine(xmlTree);
        sr.Close();
    }
}
```

 <span data-ttu-id="4184c-113">Dieses Beispiel erzeugt die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="4184c-113">This example produces the following output:</span></span>

```xml
<Root>
  <Person ID="1">
    <First>Tai</First>
    <Last>Yee</Last>
    <Occupation>Writer</Occupation>
  </Person>
  <Person ID="2">
    <First>Nikolay</First>
    <Last>Grachev</Last>
    <Occupation>Programmer</Occupation>
  </Person>
  <Person ID="3">
    <First>David</First>
    <Last>Wright</Last>
    <Occupation>Inventor</Occupation>
  </Person>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="4184c-114">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4184c-114">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
