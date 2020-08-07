---
title: 'Vorgehensweise: Serialisieren mit DataContractSerializer (C#)'
description: Erfahren Sie, wie Sie Objekte mit DataContractSerializer serialisieren. Hier finden Sie ein Beispiel, das Objekte erstellt, in Textdateien serialisiert und dann wieder deserialisiert.
ms.date: 07/20/2015
ms.assetid: 3320ecbf-cdbe-480e-979c-2c14bbef9988
ms.openlocfilehash: b713f36cde594f7cd7011073345d33c6f46585e0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301527"
---
# <a name="how-to-serialize-using-datacontractserializer-c"></a><span data-ttu-id="d8b0a-104">Vorgehensweise: Serialisieren mit DataContractSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="d8b0a-104">How to serialize using DataContractSerializer (C#)</span></span>
<span data-ttu-id="d8b0a-105">Dieses Thema enthält ein Beispiel, das zum Serialisieren und Deserialisieren <xref:System.Runtime.Serialization.DataContractSerializer> verwendet.</span><span class="sxs-lookup"><span data-stu-id="d8b0a-105">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8b0a-106">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d8b0a-106">Example</span></span>  
 <span data-ttu-id="d8b0a-107">Im folgenden Beispiel wird eine Reihe von Objekten erstellt, die <xref:System.Xml.Linq.XElement>-Objekte enthalten.</span><span class="sxs-lookup"><span data-stu-id="d8b0a-107">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d8b0a-108">Anschließend werden diese Objekte in Textdateien serialisiert und dann aus den Textdateien wieder deserialisiert.</span><span class="sxs-lookup"><span data-stu-id="d8b0a-108">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Linq;  
using System.IO;  
using System.Runtime.Serialization;  
  
public class XLinqTest  
{  
    public static void Main()  
    {  
        Test<XElement>(CreateXElement());  
        Test<XElementContainer>(new XElementContainer());  
        Test<XElementNullContainer>(new XElementNullContainer());  
    }  
  
    public static void Test<T>(T obj)  
    {  
        DataContractSerializer s = new DataContractSerializer(typeof(T));  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Create))  
        {  
            Console.WriteLine("Testing for type: {0}", typeof(T));
            s.WriteObject(fs, obj);  
        }  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Open))  
        {  
            object s2 = s.ReadObject(fs);  
            if (s2 == null)  
                Console.WriteLine("  Deserialized object is null (Nothing in VB)");  
            else  
                Console.WriteLine("  Deserialized type: {0}", s2.GetType());  
        }  
    }  
  
    public static XElement CreateXElement()  
    {  
        return new XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"));  
    }  
}  
  
[DataContract]  
public class XElementContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementContainer()  
    {  
        member = XLinqTest.CreateXElement();  
    }  
}  
  
[DataContract]  
public class XElementNullContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementNullContainer()  
    {  
        member = null;  
    }  
}  
```  
  
 <span data-ttu-id="d8b0a-109">Dieses Beispiel erzeugt die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="d8b0a-109">This example produces the following output:</span></span>  
  
```output  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
