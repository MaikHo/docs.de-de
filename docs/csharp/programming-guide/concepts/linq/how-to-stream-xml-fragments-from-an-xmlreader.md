---
title: 'Vorgehensweise: Streamen von XML-Fragmenten aus einem XmlReader (C#)'
description: Erfahren Sie, wie Sie XML-Fragmente aus einem XmlReader streamen. Diese Methode wird zur Verarbeitung großer XML-Dateien verwendet.
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: e35322724712816180d48c1957719cf87079aedd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301020"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="42add-104">Vorgehensweise: Streamen von XML-Fragmenten aus einem XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="42add-104">How to stream XML fragments from an XmlReader (C#)</span></span>

<span data-ttu-id="42add-105">Wenn Sie große XML-Dateien verarbeiten müssen, kann u. U. nicht die gesamte XML-Struktur in den Arbeitsspeicher geladen werden.</span><span class="sxs-lookup"><span data-stu-id="42add-105">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="42add-106">In diesem Thema wird gezeigt, wie mit einem <xref:System.Xml.XmlReader> Fragmente gestreamt werden können.</span><span class="sxs-lookup"><span data-stu-id="42add-106">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="42add-107">Eine der effektivsten Möglichkeiten, einen <xref:System.Xml.XmlReader> zum Lesen von <xref:System.Xml.Linq.XElement>-Objekten zu verwenden, besteht darin, eine eigene benutzerdefinierte Achsenmethode zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="42add-107">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="42add-108">Achsenmethoden geben in der Regel eine Auflistung, z. B. die <xref:System.Collections.Generic.IEnumerable%601> von <xref:System.Xml.Linq.XElement> zurück, wie dies im Beispiel in diesem Thema dargestellt ist.</span><span class="sxs-lookup"><span data-stu-id="42add-108">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="42add-109">Nachdem Sie in der benutzerdefinierten Achsenmethode durch Aufrufen der <xref:System.Xml.Linq.XNode.ReadFrom%2A>-Methode das XML-Fragment erstellt haben, geben Sie die Auflistung mit `yield return` zurück.</span><span class="sxs-lookup"><span data-stu-id="42add-109">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="42add-110">Auf diese Weise versehen Sie Ihre benutzerdefinierte Achsenmethode mit der Semantik für eine verzögerte Ausführung.</span><span class="sxs-lookup"><span data-stu-id="42add-110">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="42add-111">Wenn Sie eine XML-Struktur auf der Grundlage eines <xref:System.Xml.XmlReader>-Objekts erstellen, muss der <xref:System.Xml.XmlReader> auf einem Element positioniert sein.</span><span class="sxs-lookup"><span data-stu-id="42add-111">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="42add-112">Die <xref:System.Xml.Linq.XNode.ReadFrom%2A>-Methode gibt erst dann einen Wert zurück, wenn sie das Endtag des Elements gelesen hat.</span><span class="sxs-lookup"><span data-stu-id="42add-112">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="42add-113">Wenn Sie eine Teilstruktur erstellen möchten, können Sie einen <xref:System.Xml.XmlReader> instanziieren, den Reader auf dem Knoten positionieren, der in eine <xref:System.Xml.Linq.XElement>-Struktur umgewandelt werden soll, und dann das <xref:System.Xml.Linq.XElement>-Objekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="42add-113">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="42add-114">Unter [Vorgehensweise: Streamen von XML-Fragmenten mit Zugriff auf Headerinformationen (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) finden Sie weitere Informationen und ein Beispiel, wie Sie ein komplexeres Dokument streamen können.</span><span class="sxs-lookup"><span data-stu-id="42add-114">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="42add-115">Unter [Vorgehensweise: Durchführen einer Streamingtransformation großer XML-Dokumente (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) finden Sie ein Beispiel für das Verwenden von LINQ to XML, um ein sehr großes XML-Dokument zu transformieren, während Sie gleichzeitig eine geringe Speicherbeanspruchung beibehalten.</span><span class="sxs-lookup"><span data-stu-id="42add-115">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42add-116">Beispiel</span><span class="sxs-lookup"><span data-stu-id="42add-116">Example</span></span>  
 <span data-ttu-id="42add-117">Dieses Beispiel erstellt eine benutzerdefinierte Achsenmethode.</span><span class="sxs-lookup"><span data-stu-id="42add-117">This example creates a custom axis method.</span></span> <span data-ttu-id="42add-118">Zum Abfragen kann eine LINQ-Abfrage verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="42add-118">You can query it by using a LINQ query.</span></span> <span data-ttu-id="42add-119">Die benutzerdefinierte Achsenmethode `StreamRootChildDoc` eignet sich vor allem zum Lesen eines Dokuments, das ein sich wiederholendes `Child`-Element enthält.</span><span class="sxs-lookup"><span data-stu-id="42add-119">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 <span data-ttu-id="42add-120">Dieses Beispiel erzeugt die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="42add-120">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="42add-121">In diesem Beispiel ist das Quelldokument sehr klein.</span><span class="sxs-lookup"><span data-stu-id="42add-121">In this example, the source document is very small.</span></span> <span data-ttu-id="42add-122">Dieses Beispiel würde aber auch dann wenig Speicher beanspruchen, wenn das Quelldokument Millionen `Child`-Elemente enthielte.</span><span class="sxs-lookup"><span data-stu-id="42add-122">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
