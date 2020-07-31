---
title: Verketten von Standardabfrageoperatoren (C#)
description: Dieses Beispiel zeigt, wie Standardabfrageoperatoren in C# ebenfalls verkettet werden können. Die Abfrage materialisiert keine Zwischenergebnisse.
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 41a7e4c7910c783d07181fe16254b0cac6902794
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104073"
---
# <a name="chaining-standard-query-operators-together-c"></a>Verketten von Standardabfrageoperatoren (C#)
Das ist das letzte Thema im [Tutorial: Verketten von Abfragen (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 Die Standardabfrageoperatoren können ebenfalls verkettet werden. So können Sie z. B. den <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType>-Operator verwenden; dieser funktioniert ebenfalls verzögert. Er materialisiert keinerlei Zwischenergebnisse.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird die <xref:System.Linq.Enumerable.Where%2A>-Methode aufgerufen, bevor `ConvertCollectionToUpperCase` aufgerufen wird. Die <xref:System.Linq.Enumerable.Where%2A>-Methode funktioniert fast genauso wie die in den vorherigen Beispielen dieses Lernprogramms verwendeten verzögerten Methoden `ConvertCollectionToUpperCase` und `AppendString`.  
  
 Ein Unterschied besteht darin, dass die <xref:System.Linq.Enumerable.Where%2A>-Methode in diesem Fall ihre Quellauflistung durchläuft, dabei feststellt, dass das erste Element kein Prädikat übergibt, und dann zum nächsten Element geht, das ein Prädikat übergibt. Anschließend gibt die Methode das zweite Element zurück.  
  
 Die Grundidee bleibt jedoch dieselbe: Zwischenauflistungen werden nur dann materialisiert, wenn dies erforderlich ist.  
  
 Bei Verwendung von Abfrageausdrücken werden diese in Aufrufe für die Standardabfrageoperatoren umgewandelt, und es werden dieselben Prinzipien angewendet.  
  
 Alle Beispiele in diesem Abschnitt, die Office Open-XML-Dokumente abfragen, verwenden dasselbe Prinzip. Die verzögerte Ausführung und die verzögerte Auswertung sind nur zwei der grundlegenden Konzepte, mit denen Sie vertraut sein müssen, um LINQ (und LINQ to XML) effektiv nutzen zu können.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            where s.CompareTo("D") >= 0  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 Dieses Beispiel erzeugt die folgende Ausgabe:  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
