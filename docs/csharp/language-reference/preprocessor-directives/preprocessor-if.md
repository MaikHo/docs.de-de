---
description: '#if-Präprozessoranweisung – C#-Referenz'
title: '#if-Präprozessoranweisung – C#-Referenz'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: dc3e235db49279691203a0db4d124239fb972c69
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065232"
---
# <a name="if-c-reference"></a>#if (C#-Referenz)

Wenn der C#-Compiler eine `#if`-Anweisung vorfindet, auf die möglicherweise eine [#endif](preprocessor-endif.md)-Anweisung folgt, wird der Code zwischen den Anweisungen nur dann kompiliert, wenn das angegebene Symbol definiert wurde. Im Gegensatz zu C und C++ können Sie einem Symbol keinen numerischen Wert zuweisen. Die `#if`-Anweisung in C# ist ein boolescher Wert und überprüft nur, ob das Symbol definiert wurde. Beispiel:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Sie können die Operatoren [==](../operators/equality-operators.md#equality-operator-) (Gleichheit) und [!=](../operators/equality-operators.md#inequality-operator-) (Ungleichheit) nur zum Testen auf die [booleschen Werte](../builtin-types/bool.md)`true` oder `false` verwenden. `true` bedeutet, dass das Symbol definiert wurde. Die `#if DEBUG`-Anweisung hat die gleiche Bedeutung wie `#if (DEBUG == true)`. Sie können die Operatoren [&& (und)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124; (oder)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) und [! (nicht)](../operators/boolean-logical-operators.md#logical-negation-operator-) verwenden, um auszuwerten, ob mehrere Symbole definiert wurden. Symbole und Operatoren können auch mit Klammern gruppiert werden.

## <a name="remarks"></a>Bemerkungen

Wenn Sie `#if` mit den Direktiven [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md) und [#undef](preprocessor-undef.md) verwenden, können Sie Code je nach dem Vorhandensein eines oder mehrerer Symbole ein- oder ausschließen. Dies kann hilfreich sein, wenn Code für einen Debugbuild oder für eine bestimmte Konfiguration kompiliert wird.

Eine bedingte Direktive, die mit einer `#if`-Direktive beginnt, muss explizit mit einer `#endif`-Direktive beendet werden.

Über `#define` können Sie ein Symbol definieren. Wenn dieses Symbol dann als Ausdruck an die `#if`-Anweisung übergeben wird, wird der Ausdruck als `true` ausgewertet.

Ein Symbol kann auch mit der Compileroption [-define](../compiler-options/define-compiler-option.md) definiert werden. Die Definition eines Symbols kann mit [#undef](preprocessor-undef.md) aufgehoben werden.

Zwischen einem Symbol, das mit `-define` oder mit `#define` definiert wird, und einer Variablen mit dem gleichen Namen kommt es zu keinem Konflikt. Das bedeutet, dass ein Variablenname nicht an eine Präprozessoranweisung übergeben werden sollte und ein Symbol nur von einer Präprozessoranweisung ausgewertet werden kann.

Der Gültigkeitsbereich eines mit `#define` erstellten Symbols ist die Datei, in der es definiert wurde.

Das Buildsystem kennt zudem vordefinierte Präprozessorsymbole, die verschiedene [Zielframeworks](../../../standard/frameworks.md) in Projekten im SDK-Format darstellen. Diese sind hilfreich, wenn Sie Anwendungen erstellen, die für mehr als eine .NET-Version bestimmt sind.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> Für herkömmliche Projekte, die kein SDK-Format aufweisen, müssen Sie die Symbole für die bedingte Kompilierung für die verschiedenen Zielframeworks in Visual Studio über die Eigenschaftenseite des Projekts manuell konfigurieren.

Weitere vordefinierte Symbole sind die Konstanten DEBUG und TRACE. Sie können die für das Projekt festgelegten Werte mit `#define` überschreiben. Das DEBUG-Symbol beispielsweise wird abhängig von den Buildkonfigurationseigenschaften (Modus „Debug“ oder „Release“) automatisch festgelegt.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird gezeigt, wie Sie ein MYTEST-Symbol für eine Datei definieren und dann die Werte der Symbole MYTEST und DEBUG testen. Die Ausgabe dieses Beispiels hängt davon ab, ob Sie das Projekt im Debug- oder im Release-Konfigurationsmodus erstellen.

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

Im folgenden Beispiel wird gezeigt, wie für andere Zielframeworks zu testen, damit Sie neuere APIs möglichst verwenden können:

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a>Siehe auch

- [C#-Referenz](../index.md)
- [C#-Programmierhandbuch](../../programming-guide/index.md)
- [C#-Präprozessoranweisungen](index.md)
- [How to: Bedingtes Kompilieren mit Ablaufverfolgung und Debuggen](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
