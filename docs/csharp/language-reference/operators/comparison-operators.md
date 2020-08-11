---
title: 'Vergleichsoperatoren: C#-Referenz'
description: Erfahren Sie mehr über C#-Vergleichsoperatoren, mit denen Sie die Reihenfolge numerischer Werte überprüfen können.
ms.date: 05/11/2020
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: 9fa739d8b5461d4043f3ae51f5d14949a95c68e5
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916884"
---
# <a name="comparison-operators-c-reference"></a>Vergleichsoperatoren (C#-Referenz)

Die Vergleichsoperatoren [`<` (kleiner als)](#less-than-operator-), [`>` (größer als)](#greater-than-operator-), [`<=` (kleiner als oder gleich)](#less-than-or-equal-operator-) und [`>=` (größer als oder gleich)](#greater-than-or-equal-operator-) – auch bekannt als relationale Operatoren – vergleichen ihre Operanden. Diese Operatoren werden alle von numerischen [Ganzzahl](../builtin-types/integral-numeric-types.md)- und [Gleitkommatypen](../builtin-types/floating-point-numeric-types.md) unterstützt.

> [!NOTE]
> Bei den Operatoren `==`, `<`, `>`, `<=` und `>=` ist das Ergebnis eines Vorgangs gleich `false`, wenn einer der Operanden keine Zahl ist (<xref:System.Double.NaN?displayProperty=nameWithType> oder <xref:System.Single.NaN?displayProperty=nameWithType>). Das bedeutet, dass der `NaN`-Wert weder größer als noch kleiner als noch gleich einem anderen `double`-Wert (oder `float`-Wert) ist, einschließlich `NaN`. Weitere Informationen und Beispiele finden Sie im <xref:System.Double.NaN?displayProperty=nameWithType>- oder <xref:System.Single.NaN?displayProperty=nameWithType>-Referenzartikel.

Der [char](../builtin-types/char.md)-Typ unterstützt auch Vergleichsoperatoren. Im Fall von `char`-Operanden werden die entsprechenden Zeichencodes verglichen.

Enumerationstypen unterstützen auch Vergleichsoperatoren. Für Operanden desselben [enum](../builtin-types/enum.md)-Typs werden die entsprechenden Werte des zugrunde liegenden integralen Typs verglichen.

Die Operatoren [`==` und `!=`](equality-operators.md) überprüfen, ob die Operanden gleich sind oder nicht.

## <a name="less-than-operator-"></a>„Kleiner als“-Operator \<

Der `<`-Operator gibt `true` zurück, wenn sein linker Operand kleiner ist als sein rechter Operand, andernfalls `false`:

[!code-csharp-interactive[less than example](snippets/shared/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>„Größer als“-Operator >

Der `>`-Operator gibt `true` zurück, wenn sein linker Operand größer ist als sein rechter Operand, andernfalls `false`:

[!code-csharp-interactive[greater than example](snippets/shared/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>„Kleiner oder gleich“-Operator \<=

Der `<=`-Operator gibt `true` zurück, wenn sein linker Operand kleiner ist als der rechte Operand oder diesem entspricht, andernfalls `false`:

[!code-csharp-interactive[less than or equal example](snippets/shared/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>„Größer oder gleich“-Operator >=

Der `>=`-Operator gibt `true` zurück, wenn sein linker Operand größer ist als der rechte Operand oder diesem entspricht, andernfalls `false`:

[!code-csharp-interactive[greater than or equal example](snippets/shared/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Operatorüberladbarkeit

Ein benutzerdefinierter Typ kann die Operatoren `<`, `>`, `<=` und `>=`[überladen](operator-overloading.md).

Wenn ein Typ einen der `<`- oder `>`-Operatoren überlädt, muss er sowohl `<` als auch `>` überladen. Wenn ein Typ einen der `<=`- oder `>=`-Operatoren überlädt, muss er sowohl `<=` als auch `>=` überladen.

## <a name="c-language-specification"></a>C#-Sprachspezifikation

Weitere Informationen finden Sie im Abschnitt [Relationale und Typtestoperatoren](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) in der [C#-Sprachspezifikation](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Siehe auch

- [C#-Referenz](../index.md)
- [C#-Operatoren und -Ausdrücke](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Gleichheitsoperatoren](equality-operators.md)
