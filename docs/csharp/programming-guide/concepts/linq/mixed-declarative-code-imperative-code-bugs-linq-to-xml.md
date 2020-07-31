---
title: Fehler durch Vermischung von deklarativem und imperativem Code (LINQ to XML) (C#)
description: LINQ to XML-Methoden können eine XML-Struktur direkt ändern. Das Durchlaufen einer der Achsen während der Änderung der XML-Struktur kann zu unkalkulierbaren Fehlern führen.
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 4eaed10f0a2e64abeb7725dcd70816d75d8a0423
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165295"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a>Fehler durch Vermischung von deklarativem und imperativem Code (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enthält verschiedene Methoden, mit denen Sie eine XML-Struktur direkt ändern können. Sie können Elemente hinzufügen, Elemente löschen, den Inhalt eines Elements ändern, Attribute hinzufügen usw. Diese Programmierschnittstelle wird in [Ändern von XML-Strukturen (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md) beschrieben. Wenn Sie eine Iteration durch eine der Achsen, z. B. <xref:System.Xml.Linq.XContainer.Elements%2A> durchlaufen, und Sie dabei die XML-Struktur ändern, kann es zu einer Reihe eigenartiger Fehler kommen.  
  
 Dieses Problem wird manchmal als "Halloween-Problem" bezeichnet.  
  
## <a name="definition-of-the-problem"></a>Definition des Problems  
 Wenn Sie unter Verwendung von LINQ Code schreiben, der eine Auflistung durchläuft, schreiben Sie Code in einem deklarativen Stil. Dabei beschreiben Sie eher, *was* Sie möchten, statt zu beschreiben, *wie* Sie es möchten. Wenn Sie Code schreiben würden, der 1.) das erste Element abruft, 2.) das Element auf bestimmte Bedingungen testet, 3.) das Element modifiziert und 4.) das Element dann wieder in die Liste setzt, wäre dies imperativer Code. Sie würden dem Computer damit sagen, *wie* er die von Ihnen gestellte Aufgabe ausführen soll.  
  
 Wenn nun diese Formen von Code in ein und derselben Operation miteinander vermischt werden, treten Probleme auf. Nehmen wir einmal die folgende Situation:  
  
 Stellen Sie sich vor, Sie haben eine verknüpfte Liste mit drei Elementen darin (a, b und c):  
  
 `a -> b -> c`  
  
 Stellen Sie sich nun vor, Sie möchten die verknüpfte Liste durchgehen und drei neue Elemente (a', b' und c') hinzufügen. Die resultierende verknüpfte Liste soll dann wie folgt aussehen:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Sie schreiben also Code, der die Liste durchläuft, und der sofort anschließend für jedes Element ein neues Element hinzufügt. Nun geschieht Folgendes: Ihr Code sieht zuerst das `a`-Element und fügt dahinter `a'` ein. Der Code geht dann zum nächsten Knoten in der Liste, dieser Knoten ist aber jetzt `a'`. Das stört den Code nicht, und er fügt der Liste ein neues Element, also `a''`, hinzu.  
  
 Wie würden Sie dieses Problem im richtigen Leben lösen? Nun, Sie könnten eine Kopie der ursprünglichen verknüpften Liste anlegen und eine vollkommen neue Liste erstellen. Sie könnten aber auch rein imperativen Code schreiben. Dieser würde dann das erste Element finden, das neue Element hinzufügen und dann in der verknüpften Liste zwei Knoten weitergehen und damit das Element übergehen, das Sie gerade hinzugefügt haben.  
  
## <a name="adding-while-iterating"></a>Hinzufügungen beim Durchlaufen  
 Angenommen, Sie möchten Code schreiben, der für jedes Element in einer Struktur ein Duplikat erstellt.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 Dieser Code führt zu einer Endlosschleife. Die `foreach`-Anweisung durchläuft die `Elements()`-Achse und fügt dabei dem `doc`-Element neue Elemente hinzu. Das Ergebnis ist, dass die Anweisung auch die gerade hinzugefügten Elemente durchläuft und bei jedem Durchlaufen der Schleife neue Objekte zuweist. Irgendwann wird der gesamte verfügbare Arbeitsspeicher dafür in Beschlag genommen.  
  
 Dieses Problem können Sie beheben, indem Sie die Auflistung mit dem <xref:System.Linq.Enumerable.ToList%2A>-Standardabfrageoperator in den Arbeitsspeicher ziehen. Dies ist im Folgenden dargestellt:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    root.Add(new XElement(e.Name, (string)e));  
Console.WriteLine(root);  
```  
  
 Jetzt funktioniert der Code. Die resultierende XML-Struktur sieht wie folgt aus:  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## <a name="deleting-while-iterating"></a>Löschungen beim Durchlaufen  
 Wenn Sie alle Knoten auf einer bestimmten Ebene löschen möchten, könnten Sie versucht sein, Code wie den folgenden zu schreiben:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 Ein solcher Code würde aber nicht zum gewünschten Ergebnis führen. Nachdem Sie das erste Element, A, entfernt haben, würde es aus der im Stamm enthaltenen XML-Struktur entfernt werden, sodass der Code in der <legacyBold>Elements</legacyBold>-Methode, der die Iteration vornimmt, das nächste Element nicht finden könnte.  
  
 Der oben genannte Code erzeugt die folgende Ausgabe:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Auch hier besteht die Lösung darin, <xref:System.Linq.Enumerable.ToList%2A> aufzurufen, um die Auflistung wie folgt zu materialisieren:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 Dies erzeugt die folgende Ausgabe:  
  
```xml  
<Root />  
```  
  
 Alternativ dazu können Sie die Iteration ganz eliminieren, indem Sie für das übergeordnete Element <xref:System.Xml.Linq.XElement.RemoveAll%2A> aufrufen:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>Warum kann LINQ dieses Problem nicht automatisch lösen?  
 Eine Herangehensweise bestünde darin, immer alles in den Arbeitsspeicher zu holen, statt mit verzögerter Auswertung zu arbeiten. Dies würde aber massive Leistungseinbußen und einen hohen Arbeitsspeicherbedarf mit sich bringen. Im praktischen Einsatz würden LINQ und LINQ to XML bei dieser Variante scheitern.  
  
 Ein anderer möglicher Ansatz bestünde darin, eine gewisse Transaktionssyntax in LINQ einzubauen und den Compiler zu veranlassen, den Code zu analysieren und zu bestimmen, ob irgendeine Auflistung materialisiert werden muss. Der Versuch, allen Code zu bestimmen, der Nebenwirkungen hat, ist aber eine unglaublich komplexe Angelegenheit. Betrachten Sie folgenden Code:  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 Solch ein Analysecode müsste die Methoden <legacyBold>TestSomeCondition</legacyBold> und <legacyBold>DoMyProjection</legacyBold> sowie alle von diesen Methoden aufgerufenen Methoden analysieren, um zu bestimmen, ob Code mit Nebenwirkungen vorhanden ist. Der Analysecode kann aber nicht nur einfach nach Code mit Nebenwirkungen suchen. Er dürfte nur den Code auswählen, der in dieser Situation Nebenwirkungen auf die untergeordneten Elemente von `root` hat.  
  
 LINQ to XML unternimmt keine Versuche, eine solche Analyse durchzuführen.  
  
 Für die Vermeidung dieser Probleme sind allein Sie zuständig.  
  
## <a name="guidance"></a>Empfehlungen  
 Vermischen Sie deklarativen Code nicht mit imperativem Code.  
  
 Auch wenn Sie die Semantik Ihrer Auflistungen und die Semantik der Methoden, die die XML-Struktur ändern, exakt kennen und "cleveren" Code schreiben, der diese Art von Problemen vermeidet, muss Ihr Code zukünftig von anderen Entwicklern gewartet werden, die sich vielleicht mit dieser Problematik nicht so gut auskennen. Wenn Sie deklarativen und imperativen Code mischen, ist der Code anfälliger.  
  
 Wenn Sie Code schreiben, der eine Auflistung so materialisiert, dass diese Probleme vermieden werden, versehen Sie ihn mit entsprechenden Kommentaren, um die für die Wartung zuständigen Programmierer über die Problematik zu informieren.  
  
 Wenn die Arbeitsgeschwindigkeit und andere Überlegungen es zulassen, sollten Sie immer nur deklarativen Code verwenden. Ändern Sie nicht Ihre vorhandene XML-Struktur. Generieren Sie stattdessen eine neue Struktur.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
XElement newRoot = new XElement("Root",  
    root.Elements(),  
    root.Elements()  
);  
Console.WriteLine(newRoot);  
```  
