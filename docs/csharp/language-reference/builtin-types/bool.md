---
title: 'bool-Typ: C#-Referenz'
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
- "true"
- "false"
- true_CSharpKeyword
- false_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 4623dc7d6c8c6c437c78aee45f0eeee8a92e3200
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854879"
---
# <a name="bool-c-reference"></a>bool (C#-Referenz)

Das Schlüsselwort vom Typ `bool` ist ein Alias für den .NET-Strukturtyp <xref:System.Boolean?displayProperty=nameWithType>, der einen booleschen Wert (`true` oder `false`) darstellt.

Um logische Operationen mit Werten vom Typ `bool` durchzuführen, verwenden Sie die [booleschen Logikoperatoren](../operators/boolean-logical-operators.md). Der Typ `bool` ist der Ergebnistyp von [Vergleichs](../operators/comparison-operators.md)- und [Gleichheitsoperatoren](../operators/equality-operators.md). Ein `bool`-Ausdruck kann ein steuernder bedingter Ausdruck in [if](../keywords/if-else.md)-, [do](../keywords/do.md)-, [while](../keywords/while.md)- und [for](../keywords/for.md)-Anweisungen und im [bedingten Operator `?:`](../operators/conditional-operator.md) sein.

Der Standardwert des Typs `bool` ist `false`.

## <a name="literals"></a>Literale

Sie können die Literale `true` und `false` verwenden, um eine `bool`-Variable zu initialisieren oder einen `bool`-Wert zu übergeben:

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Dreiwertige boolesche Logik

Verwenden Sie den Nullable-Typ `bool?`, wenn Sie dreiwertige Logik unterstützen müssen (wenn Sie beispielsweise mit Datenbanken arbeiten, die einen dreiwertigen booleschen Typ unterstützen). Für die `bool?`-Operanden unterstützen die vordefinierten `&`- und `|`-Operatoren die dreiwertige Logik. Weitere Informationen finden Sie im Abschnitt [Boolesche logische Operatoren, die NULL-Werte zulassen](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) im Artikel [Boolesche logische Operatoren](../operators/boolean-logical-operators.md).

Weitere Informationen zu Nullable-Werttypen finden Sie unter [Nullable-Werttypen](nullable-value-types.md).

## <a name="conversions"></a>Konvertierungen

C# bietet nur zwei Konvertierungen, die den Typ `bool` beinhalten. Dabei handelt es sich um eine implizite Konvertierung in den entsprechenden Nullable-Typ `bool?` und eine explizite Konvertierung aus dem `bool?`-Typ. .NET bietet jedoch zusätzliche Methoden, die Sie verwenden können, um in den oder aus dem Typ `bool` zu konvertieren. Weitere Informationen finden Sie im Abschnitt [Konvertieren in boolesche Werte und aus booleschen Werten](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) auf der <xref:System.Boolean?displayProperty=nameWithType>-API-Referenzseite.

## <a name="c-language-specification"></a>C#-Sprachspezifikation

Weitere Informationen finden Sie im Abschnitt [Der Typ „bool“](~/_csharplang/spec/types.md#the-bool-type) in der [C#-Sprachspezifikation](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Weitere Informationen

- [C#-Referenz](../index.md)
- [Value types (Werttypen)](value-types.md)
- [Operatoren „true“ und „false“](../operators/true-false-operators.md)
