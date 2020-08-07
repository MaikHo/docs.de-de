---
title: Reflektion (C#)
description: Die Reflexion stellt Objekte bereit, die Assemblys, Module und Typen in C# beschreiben. Wenn Ihr Code Attribute enthält, ermöglicht die Reflexion Ihnen den Zugriff auf diese Attribute.
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4d4f4c082dd2d58e212bae53524e5dd4fd06fb75
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302801"
---
# <a name="reflection-c"></a>Reflektion (C#)

Reflektion bietet Objekte (des Typs <xref:System.Type>), die Assemblys, Module und Typen beschreiben. Mithilfe von Reflektion können Sie dynamisch eine Instanz eines Typs erzeugen, den Typ an ein vorhandenes Objekt binden und Typinformationen von vorhandenen Objekten abfragen. Ebenso wird erläutert wie die Methoden vorhandener Objekte aufgerufen und auf ihre Felder und Eigenschaften zugegriffen werden kann. Wenn Sie Attribute in Ihrem Code verwenden, können Sie mit Reflektion auf diese zugreifen. Weitere Informationen finden Sie unter [Attribute](../../../standard/attributes/index.md).

Hier sehen Sie ein einfaches Beispiel für Reflektion mit der Methode <xref:System.Object.GetType>, die von allen Typen der Basisklasse `Object` geerbt wird, zum Abrufen von Typinformationen einer Variable:

> [!NOTE]
> Stellen Sie sicher, dass Sie `using System;` und `using System.Reflection;` am Anfang Ihrer *.cs*-Datei hinzufügen.

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

Die Ausgabe ist: `System.Int32`.

Im folgenden Beispiel wird Reflektion verwendet, um den vollständigen Namen der geladenen Assembly abzurufen.

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

Die Ausgabe ist: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.

> [!NOTE]
> Die C#-Schlüsselwörter `protected` und `internal` haben in IL keine Bedeutung und werden nicht in Reflektions-APIs verwendet. Die entsprechenden Begriffe in IL sind *Family* und *Assembly*. Verwenden Sie zum Identifizieren einer `internal`-Methode mithilfe von Reflektion die Eigenschaft <xref:System.Reflection.MethodBase.IsAssembly%2A>. Verwenden Sie <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A> zum Identifizieren einer Methode `protected internal`.

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

- [C#-Programmierhandbuch](../index.md)
- [Assemblys in .NET](../../../standard/assembly/index.md)
