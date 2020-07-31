---
title: Implizit typisierte lokale Variablen – C#-Programmierhandbuch
description: Das var-Schlüsselwort in C# weist den Compiler an, den Typ der Variablen vom Ausdruck auf der rechten Seite der Initialisierungsanweisung abzuleiten.
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 6badb8588dedda80227ab38bee027cf2890c8672
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864214"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="8fd0c-103">Implizit typisierte lokale Variablen (C#-Programmierhandbuch)</span><span class="sxs-lookup"><span data-stu-id="8fd0c-103">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="8fd0c-104">Lokale Variablen können deklariert werden, ohne einen expliziten Typ anzugeben.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-104">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="8fd0c-105">Das `var`-Schlüsselwort weist den Compiler an, den Typ der Variablen vom Ausdruck auf der rechten Seite der Initialisierungsanweisung abzuleiten.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-105">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="8fd0c-106">Der hergeleitete Typ ist möglicherweise ein integrierter Typ, ein anonymer Typ, ein benutzerdefinierter Typ oder ein Typ, der in der .NET-Klassenbibliothek definiert wurde.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-106">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET class library.</span></span> <span data-ttu-id="8fd0c-107">Weitere Informationen zur Initialisierung von Arrays mithilfe von `var` finden Sie unter [Implizit typisierte Arrays](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="8fd0c-107">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="8fd0c-108">Die folgenden Beispiele veranschaulichen verschiedene Arten, wie Sie lokale Variablen mit `var` deklarieren können:</span><span class="sxs-lookup"><span data-stu-id="8fd0c-108">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="8fd0c-109">Es ist von großer Bedeutung zu verstehen, dass das `var`-Schlüsselwort nicht „variant“ bedeutet, und das es nicht darauf hinweist, dass die Variable schwach typisiert oder spät gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-109">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="8fd0c-110">Es bedeutet nur, dass der Compiler den angemessensten Typen bestimmt und zuweist.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-110">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="8fd0c-111">Das `var`-Schlüsselwort kann in folgendem Kontext verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="8fd0c-111">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="8fd0c-112">Für lokale Variablen (Variablen, die im Geltungsbereich der Methode deklariert wurden), wie in vorherigem Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-112">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="8fd0c-113">In einer [for](../../language-reference/keywords/for.md)-Initialisierungsanweisung.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-113">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="8fd0c-114">In einer [foreach](../../language-reference/keywords/foreach-in.md)-Initialisierungsanweisung.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-114">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach (var item in list) {...}
    ```

- <span data-ttu-id="8fd0c-115">In einer [using](../../language-reference/keywords/using-statement.md)-Anweisung.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-115">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="8fd0c-116">Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von implizit typisierten lokalen Variablen und Arrays in einem Abfrageausdruck](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="8fd0c-116">For more information, see [How to use implicitly typed local variables and arrays in a query expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="8fd0c-117">var und anonyme Typen</span><span class="sxs-lookup"><span data-stu-id="8fd0c-117">var and anonymous types</span></span>

<span data-ttu-id="8fd0c-118">In vielen Fällen ist der Einsatz von `var` optional und nur eine praktische Syntax.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-118">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="8fd0c-119">Wenn eine Variable allerdings mit einem anonymen Typ initialisiert wird, müssen Sie die Variable als `var` deklarieren, wenn Sie zu einem späteren Zeitpunkt auf die Eigenschaften des Objekts zugreifen möchten.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-119">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="8fd0c-120">Das ist ein häufiges Szenario in LINQ-Abfrageausdrücken.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-120">This is a common scenario in LINQ query expressions.</span></span> <span data-ttu-id="8fd0c-121">Weitere Informationen finden Sie unter [Anonyme Typen](anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="8fd0c-121">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="8fd0c-122">Aus der Perspektive Ihres Quellcodes hat ein anonymer Typ keinen Namen.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-122">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="8fd0c-123">Wenn eine Abfragevariable mit `var` initialisiert wurde, ist es deshalb nur möglich, auf die Eigenschaften in der zurückgegebenen Objektsequenz zuzugreifen, wenn Sie `var` in der `foreach`-Anweisung als Typen der Iterationvariablen verwenden.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-123">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="8fd0c-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8fd0c-124">Remarks</span></span>

<span data-ttu-id="8fd0c-125">Die folgenden Einschränkungen gelten für implizit typisierte Variablendeklarationen:</span><span class="sxs-lookup"><span data-stu-id="8fd0c-125">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="8fd0c-126">`var` kann nur verwendet werden, wenn eine lokale Variable deklariert und in derselben Anweisung initialisiert wird; die Variable kann weder mit NULL noch mit einer Methodengruppe oder einer anonymen Funktion initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-126">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="8fd0c-127">`var` kann nicht für Felder im Klassenbereich verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-127">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="8fd0c-128">Variablen, die mit `var` deklariert wurden, können nicht im Initialisierungsausdruck verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-128">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="8fd0c-129">Sprich, dieser Ausdruck ist gültig: `int i = (i = 20);`, aber dieser Ausdruck führt zu einem Kompilierzeitfehler: `var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="8fd0c-129">In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="8fd0c-130">Es können nicht mehrere implizit typisierte Variablen in derselben Anweisung initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-130">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="8fd0c-131">Wenn sich ein Typ mit dem Namen `var` im Geltungsbereich befindet, löst sich das `var`-Schlüsselwort zu diesem Typnamen auf und wird nicht als Teil der Deklaration einer implizit typisierten lokalen Variablen behandelt.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-131">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="8fd0c-132">Implizite Typisierung mit dem `var` -Schlüsselwort kann nur auf Variablen im Gültigkeitsbereich der lokalen Methode angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-132">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="8fd0c-133">Implizite Typisierung ist für Klassenfelder nicht verfügbar, weil der C#-Compiler während der Verarbeitung des Codes auf ein logisches Paradox treffen würde: Der Compiler muss den Typ des Felds kennen, aber er kann den Typ erst bestimmen, wenn der Zuordnungsausdruck analysiert ist, und der Ausdruck kann nicht ohne Kenntnis des Typs ausgewertet werden.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-133">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="8fd0c-134">Betrachten Sie folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="8fd0c-134">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="8fd0c-135">`bookTitles` ist ein Klassenfeld, das den Typ `var` erhält.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-135">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="8fd0c-136">Da das Feld keinen Ausdruck zur Auswertung enthält, kann der Compiler nicht ableiten, von welchem Typ `bookTitles` ist.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-136">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="8fd0c-137">Darüber hinaus ist es auch nicht ausreichend, dem Feld einen Ausdruck hinzuzufügen (wie für eine lokale Variable):</span><span class="sxs-lookup"><span data-stu-id="8fd0c-137">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="8fd0c-138">Wenn der Compiler während der Codekompilierung auf Felder trifft, zeichnet er den Typ jedes Felds auf, bevor er dem Feld zugeordnete Ausdrücke verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-138">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="8fd0c-139">Der Compiler erkennt das gleiche Paradox bei dem Versuch, `bookTitles` zu analysieren: Er muss den Typ des Felds kennen, aber der Compiler würde den Typ von `var` normalerweise durch Analysieren des Ausdrucks bestimmen, was nicht möglich ist, ohne vorher den Typ zu kennen.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-139">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="8fd0c-140">`var` erweist sich auch bei Abfrageausdrücken als nützlich, deren genauer konstruierter Typ der Abfragevariable schwer ermittelbar ist.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-140">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="8fd0c-141">Dies kann bei Gruppierungs- und Sortierungsvorgängen auftreten.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-141">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="8fd0c-142">Das `var`-Schlüsselwort erweist sich auch als nützlich, wenn es umständlich ist, den Variablentypen mit der Tastatur einzugeben – oder wenn der Typ offensichtlich ist, oder nicht zur Lesbarkeit des Codes beiträgt.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-142">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="8fd0c-143">`var` ist z.B. bei geschachtelten generischen Typen wie die, die in Gruppenvorgängen verwendet werden, auf diese Weise nützlich.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-143">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="8fd0c-144">In der folgenden Abfrage ist der Typ der Abfragevariablen `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-144">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="8fd0c-145">Solange dies Ihnen und denen, die Ihren Code verwalten müssen, klar ist, spricht nichts dagegen, implizite Typisierung aus Gründen der Zweckmäßigkeit und der Kürze zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-145">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="8fd0c-146">Die Verwendung von `var` trägt zur Vereinfachung Ihres Codes bei, aber die Verwendung sollte auf die Fälle beschränkt werden, in denen sie erforderlich ist oder wenn sie Ihren Code leichter lesbar macht.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-146">The use of `var` helps simplify your code, but its use should be restricted to cases where it is required, or when it makes your code easier to read.</span></span> <span data-ttu-id="8fd0c-147">Weitere Informationen zur ordnungsgemäßen Verwendung von `var` finden Sie im Abschnitt [Implizit typisierte lokale Variablen](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) im Artikel zu „C#-Richtlinien für das Codieren“.</span><span class="sxs-lookup"><span data-stu-id="8fd0c-147">For more information about when to use `var` properly, see the [Implicitly typed local variables](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) section on the C# Coding Guidelines article.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fd0c-148">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8fd0c-148">See also</span></span>

- [<span data-ttu-id="8fd0c-149">C#-Referenz</span><span class="sxs-lookup"><span data-stu-id="8fd0c-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="8fd0c-150">Implizit typisierte Arrays</span><span class="sxs-lookup"><span data-stu-id="8fd0c-150">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="8fd0c-151">Verwenden von implizit typisierten lokalen Variablen und Arrays in einem Abfrageausdruck</span><span class="sxs-lookup"><span data-stu-id="8fd0c-151">How to use implicitly typed local variables and arrays in a query expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="8fd0c-152">Anonyme Typen</span><span class="sxs-lookup"><span data-stu-id="8fd0c-152">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="8fd0c-153">Objekt- und Auflistungsinitialisierer</span><span class="sxs-lookup"><span data-stu-id="8fd0c-153">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="8fd0c-154">var</span><span class="sxs-lookup"><span data-stu-id="8fd0c-154">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="8fd0c-155">LINQ in C#</span><span class="sxs-lookup"><span data-stu-id="8fd0c-155">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="8fd0c-156">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="8fd0c-156">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="8fd0c-157">for</span><span class="sxs-lookup"><span data-stu-id="8fd0c-157">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="8fd0c-158">foreach, in</span><span class="sxs-lookup"><span data-stu-id="8fd0c-158">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="8fd0c-159">Using-Anweisung</span><span class="sxs-lookup"><span data-stu-id="8fd0c-159">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
