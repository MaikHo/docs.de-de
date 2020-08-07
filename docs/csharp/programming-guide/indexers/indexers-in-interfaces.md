---
title: Indexer in Schnittstellen – C#-Programmierhandbuch
description: Indexer können in einer Schnittstelle in C# deklariert werden. Erfahren, wie Accessoren für Schnittstellenindexer sich von den Accessoren für Klassenindexer unterscheiden.
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: ec77843bdf3181a543bd6c02cfb034b21ded1ae7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303100"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indexer in Schnittstellen (C#-Programmierhandbuch)

Indexer können für eine [Schnittstelle](../../language-reference/keywords/interface.md) deklariert werden. Accessoren für Schnittstellenindexer unterscheiden sich von den Accessoren für [Klassen](../../language-reference/keywords/class.md)-Indexer in den folgenden Punkten:

- Schnittstellenaccessoren verwenden keine Modifizierer.
- Schnittstellenzugriffsmethoden weisen in der Regel keinen Text auf.

Der Zweck einer Zugriffsmethode besteht darin, anzugeben, ob der Indexer gleichzeitig Lese- und Schreibzugriff, nur Lesezugriff oder nur Schreibzugriff besitzt. In seltenen Fällen müssen Sie eine Implementierung für einen in einer Schnittstelle definierten Indexer angeben. Indexer definieren üblicherweise eine API für den Zugriff auf Datenfelder, und Datenfelder können nicht in einer Schnittstelle definiert werden.

Das folgende Beispiel zeigt den Accessor für einen Schnittstellenindexer:

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

Die Signatur eines Indexers muss sich von den Signaturen aller anderen in derselben Schnittstelle deklarierten Indexer unterscheiden.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Schnittstellenindexer implementiert werden.

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

Im vorherigen Beispiel könnte der Schnittstellenmember durch Verwendung des vollqualifizierten Namens des Schnittstellenmembers explizit implementiert werden. Beispiel:

```csharp
string IIndexInterface.this[int index]
{
}
```

Der vollqualifizierte Name ist jedoch nur erforderlich, um Mehrdeutigkeiten zu vermeiden, wenn mehr als eine Schnittstelle mit derselben Indexersignatur von der Klasse implementiert wird. Wenn z.B. eine `Employee`-Klasse die beiden Schnittstellen `ICitizen` und `IEmployee` implementiert und beide Schnittstellen dieselbe Indexersignatur besitzen, ist die explizite Implementierung des Schnittstellenmembers erforderlich. Das bedeutet, dass die folgende Indexerdeklaration:

```csharp
string IEmployee.this[int index]
{
}
```

den Indexer für die Schnittstelle `IEmployee` implementiert. Dahingegen implementiert die folgende Deklaration:

```csharp
string ICitizen.this[int index]
{
}
```

den Indexer für die Schnittstelle `ICitizen`.

## <a name="see-also"></a>Siehe auch

- [C#-Programmierhandbuch](../index.md)
- [Indexer](./index.md)
- [Eigenschaften](../classes-and-structs/properties.md)
- [Schnittstellen](../interfaces/index.md)
