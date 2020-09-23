---
title: Spiegelung
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 79603e0951732c7d0d0031d4fc44ddd7dbd392c9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077253"
---
# <a name="reflection-visual-basic"></a>Reflektion (Visual Basic)

Reflektion bietet Objekte (vom Typ <xref:System.Type>), die Assemblys, Module und Typen beschreiben. Mithilfe von Reflektion können Sie dynamisch eine Instanz eines Typs erzeugen, den Typ an ein vorhandenes Objekt binden und Typinformationen von vorhandenen Objekten abfragen. Ebenso wird erläutert wie die Methoden vorhandener Objekte aufgerufen und auf ihre Felder und Eigenschaften zugegriffen werden kann. Wenn Sie Attribute in Ihrem Code verwenden, können Sie mit Reflektion auf diese zugreifen. Weitere Informationen finden Sie unter [Attribute](../../../standard/attributes/index.md).  
  
 Hier sehen Sie ein einfaches Beispiel für Reflektion mit der statischen Methode `GetType`, die von allen Typen der Basisklasse `Object` geerbt wird, zum Abrufen von Typinformationen einer Variable:  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 Die Ausgabe lautet wie folgt:  
  
 `System.Int32`  
  
 Im folgenden Beispiel wird Reflektion verwendet, um den vollständigen Namen der geladenen Assembly abzurufen.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 Die Ausgabe lautet wie folgt:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Übersicht über Reflektion  

 Reflektion ist in folgenden Situationen nützlich:  
  
- Wenn Sie in den Metadaten Ihres Programms auf Attribute zugreifen müssen Weitere Informationen finden Sie unter [Abrufen von Informationen aus Attributen](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- Zum Untersuchen und Instanziieren von Typen in einer Assembly  
  
- Zum Erstellen neuer Typen zur Laufzeit Verwenden Sie Klassen in <xref:System.Reflection.Emit>.  
  
- Zum Ausführen von spätem Binden mit Zugriff auf Methoden der zur Laufzeit erstellten Typen Weitere Informationen finden Sie im Thema [Dynamisches Laden und Verwenden von Typen](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Verwandte Abschnitte  

 Weitere Informationen finden Sie unter:  
  
- [Reflexion](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Anzeigen von Typinformationen](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Reflektion und generische Typen](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Abrufen von Informationen aus Attributen](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Weitere Informationen

- [Visual Basic-Programmierhandbuch](../index.md)
- [Assemblys in .NET](../../../standard/assembly/index.md)
