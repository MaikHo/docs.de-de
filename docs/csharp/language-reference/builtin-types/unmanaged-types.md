---
description: Informationen zu nicht verwalteten Typen in C#
title: 'Nicht verwaltete Typen: C#-Verweis'
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: b5a689ca3ade36ef77da958549894f76e074986e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2020
ms.locfileid: "89143531"
---
# <a name="unmanaged-types-c-reference"></a>Nicht verwaltete Typen (C#-Verweis)

Ein Typ ist ein **nicht verwalteter Typ**, wenn es sich um einen der folgenden Typen handelt:

- `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` oder `bool`
- Beliebiger [Enumerationstyp](enum.md)
- Beliebiger [Zeigertyp](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Jeder benutzerdefinierte [Strukturtyp](struct.md), der nur Felder mit nicht verwalteten Typen enthält und – in C# 7.3 und früher – kein konstruierter Typ ist (ein konstruierter Typ ist ein Typ, der mindestens ein Typargument enthält)

Ab C# 7.3 können Sie die [`unmanaged`-Einschränkung](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) verwenden, um anzugeben, dass ein Typparameter ein nicht verwalteter Nicht-Nullable-Nichtzeigertyp ist.

Ab C# 8.0 ist ein *konstruierter* Strukturtyp, der Felder mit nicht verwalteten Typen enthält, ebenfalls nicht verwaltet, wie das folgende Beispiel zeigt:

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

Eine generische Struktur kann als Quelle sowohl für nicht verwaltete als auch für verwaltete konstruierte Typen dienen. Das oben stehende Beispiel definiert die generische Struktur `Coords<T>` und zeigt Beispiele nicht verwalteter konstruierter Typen. Ein Beispiel für einen verwalteten Typ ist `Coords<object>`. Der Typ ist verwaltet, weil er Felder des Typs `object` enthält, der verwaltet ist. Wenn *alle* konstruierten Typen nicht verwaltet sein sollen, verwenden Sie die `unmanaged`-Einschränkung in der Definition einer generischen Struktur:

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>C#-Sprachspezifikation

Weitere Informationen finden Sie im Abschnitt [Zeigertypen](~/_csharplang/spec/unsafe-code.md#pointer-types) der [Spezifikation für die Sprache C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Siehe auch

- [C#-Referenz](../index.md)
- [Zeigertypen](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Memory- und Span-bezogene Typen](../../../standard/memory-and-spans/index.md)
- [sizeof (Operator)](../operators/sizeof.md)
- [stackalloc](../operators/stackalloc.md)
