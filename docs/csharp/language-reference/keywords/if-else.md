---
description: if-else – C#-Referenz
title: if-else – C#-Referenz
ms.date: 07/20/2015
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
ms.openlocfilehash: e2de84807a049bd47ea277db9fb010d0c2e4857d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118506"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="b1520-103">if-else (C#-Referenz)</span><span class="sxs-lookup"><span data-stu-id="b1520-103">if-else (C# Reference)</span></span>

<span data-ttu-id="b1520-104">Eine `if` -Anweisung ermittelt, welche Anweisung basierend auf dem Wert eines booleschen Ausdrucks auszuführen ist.</span><span class="sxs-lookup"><span data-stu-id="b1520-104">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="b1520-105">Im folgenden Beispiel wird die `bool` Variable `condition` auf `true` festgelegt und dann in der `if` Anweisung überprüft.</span><span class="sxs-lookup"><span data-stu-id="b1520-105">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="b1520-106">Die Ausgabe lautet `The variable is set to true.`.</span><span class="sxs-lookup"><span data-stu-id="b1520-106">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="b1520-107">Die können die Beispiele in diesem Thema ausführen, indem Sie sie in die `Main` -Methode einer Konsolenanwendung platzieren.</span><span class="sxs-lookup"><span data-stu-id="b1520-107">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="b1520-108">Eine `if` -Anweisung in C# kann zwei Formen annehmen, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="b1520-108">An `if` statement in C# can take two forms, as the following example shows.</span></span>

```csharp
// if-else statement
if (condition)
{
    then-statement;
}
else
{
    else-statement;
}
// Next statement in the program.

// if statement without an else
if (condition)
{
    then-statement;
}
// Next statement in the program.
```

<span data-ttu-id="b1520-109">In einer `if-else` -Anweisung wird, wenn `condition` zu true ausgewertet wird, `then-statement` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b1520-109">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="b1520-110">Wenn `condition` false ist, wird `else-statement` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b1520-110">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="b1520-111">Da `condition` nicht gleichzeitig true und false sein kann, können `then-statement` und `else-statement` einer `if-else` -Anweisung niemals beide ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b1520-111">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="b1520-112">Nachdem `then-statement` oder `else-statement` ausgeführt wurde, wird die Steuerung an die `if` -Anweisung übergeben.</span><span class="sxs-lookup"><span data-stu-id="b1520-112">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="b1520-113">In einer `if` -Anweisung, die keine `else` -Anweisung enthält, wird, wenn `condition` true ist, `then-statement` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b1520-113">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="b1520-114">Wenn `condition` false ist, wird die Steuerung an die nächste Anweisung nach der `if` Anweisung übergeben.</span><span class="sxs-lookup"><span data-stu-id="b1520-114">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="b1520-115">Sowohl `then-statement` als auch `else-statement` können aus einer einzelnen Anweisung oder mehreren in Klammern eingeschlossenen Anweisungen bestehen (`{}`).</span><span class="sxs-lookup"><span data-stu-id="b1520-115">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="b1520-116">Bei einer Anweisung sind die Klammern optional, sie werden aber empfohlen.</span><span class="sxs-lookup"><span data-stu-id="b1520-116">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="b1520-117">Die Anweisung bzw. die Anweisungen in `then-statement` und `else-statement` können von einer beliebigen Art sein und eine weitere `if` Anweisung enthalten, die in der ursprünglichen `if` -Anweisung geschachtelt ist.</span><span class="sxs-lookup"><span data-stu-id="b1520-117">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="b1520-118">In geschachtelten `if` Anweisungen gehört jede `else` -Klausel zur letzten `if` -Anweisung, die nicht über eine zugehörige `else`-Anweisung verfügt.</span><span class="sxs-lookup"><span data-stu-id="b1520-118">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="b1520-119">Im folgenden Beispiel wird `Result1` angezeigt, wenn `m > 10` und `n > 20` zu true ausgewertet werden.</span><span class="sxs-lookup"><span data-stu-id="b1520-119">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="b1520-120">Wenn `m > 10` true ist, `n > 20` hingegen false, wird `Result2` angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b1520-120">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="b1520-121">Wenn stattdessen `Result2` angezeigt werden soll, wenn `(m > 10)` false ist, können Sie diese Zuordnung mithilfe von Klammern festlegen, um den Beginn und das Ende der geschachtelten `if` Anweisung anzugeben, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="b1520-121">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="b1520-122">`Result2` wird angezeigt, wenn die Bedingung `(m > 10)` als FALSE ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="b1520-122">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="b1520-123">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b1520-123">Example</span></span>

<span data-ttu-id="b1520-124">Im folgenden Beispiel geben Sie ein Zeichen über die Tastatur ein. Das Programm verwendet eine geschachtelte `if` -Anweisung, um zu bestimmen, ob das eingegebene Zeichen ein alphabetisches Zeichen ist.</span><span class="sxs-lookup"><span data-stu-id="b1520-124">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="b1520-125">Wenn das eingegebene Zeichen ein alphabetisches Zeichen ist, überprüft das Programm, ob das eingegebene Zeichen in Groß- oder in Kleinschreibung ist.</span><span class="sxs-lookup"><span data-stu-id="b1520-125">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="b1520-126">In beiden Fällen wird eine Meldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b1520-126">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="b1520-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b1520-127">Example</span></span>

<span data-ttu-id="b1520-128">Sie können eine `if` Anweisung auch in einem else-Block schachteln, wie der folgende Codeausschnitt zeigt.</span><span class="sxs-lookup"><span data-stu-id="b1520-128">You can also nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="b1520-129">Im Beispiel werden `if` Anweisungen in zwei else-Blocks und einem then-Block geschachtelt.</span><span class="sxs-lookup"><span data-stu-id="b1520-129">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="b1520-130">In den Kommentaren ist angegeben, welche Bedingungen in jedem Block true oder false sind.</span><span class="sxs-lookup"><span data-stu-id="b1520-130">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="b1520-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b1520-131">Example</span></span>

<span data-ttu-id="b1520-132">Im folgenden Beispiel wird bestimmt, ob ein eingegebenes Zeichen ein Kleinbuchstabe, ein Großbuchstabe oder eine Zahl ist.</span><span class="sxs-lookup"><span data-stu-id="b1520-132">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="b1520-133">Wenn alle drei Bedingungen false sind, ist das Zeichen kein alphanumerisches Zeichen.</span><span class="sxs-lookup"><span data-stu-id="b1520-133">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="b1520-134">Das Beispiel zeigt für jeden Fall eine Meldung an.</span><span class="sxs-lookup"><span data-stu-id="b1520-134">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="b1520-135">So, wie eine Anweisung im else-Block oder then-Block jede beliebige Anweisung sein kann, können Sie für die Bedingungen einen beliebigen gültigen booleschen Ausdruck verwenden.</span><span class="sxs-lookup"><span data-stu-id="b1520-135">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="b1520-136">Sie können [logische Operatoren](../operators/boolean-logical-operators.md) wie `!`, `&&`, `||`, `&`, `|` und `^` verwenden, um Verbundbedingungen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b1520-136">You can use [logical operators](../operators/boolean-logical-operators.md) such as `!`, `&&`, `||`, `&`, `|`, and `^` to make compound conditions.</span></span> <span data-ttu-id="b1520-137">Der folgende Code enthält Beispiele.</span><span class="sxs-lookup"><span data-stu-id="b1520-137">The following code shows examples.</span></span>

```csharp
// NOT
bool result = true;
if (!result)
{
    Console.WriteLine("The condition is true (result is false).");
}
else
{
    Console.WriteLine("The condition is false (result is true).");
}

// Short-circuit AND
int m = 9;
int n = 7;
int p = 5;
if (m >= n && m >= p)
{
    Console.WriteLine("Nothing is larger than m.");
}

// AND and NOT
if (m >= n && !(p > m))
{
    Console.WriteLine("Nothing is larger than m.");
}

// Short-circuit OR
if (m > n || m > p)
{
    Console.WriteLine("m isn't the smallest.");
}

// NOT and OR
m = 4;
if (!(m >= n || m >= p))
{
    Console.WriteLine("Now m is the smallest.");
}
// Output:
// The condition is false (result is true).
// Nothing is larger than m.
// Nothing is larger than m.
// m isn't the smallest.
// Now m is the smallest.
```

## <a name="c-language-specification"></a><span data-ttu-id="b1520-138">C#-Sprachspezifikation</span><span class="sxs-lookup"><span data-stu-id="b1520-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b1520-139">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b1520-139">See also</span></span>

- [<span data-ttu-id="b1520-140">C#-Referenz</span><span class="sxs-lookup"><span data-stu-id="b1520-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b1520-141">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="b1520-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b1520-142">C#-Schlüsselwörter</span><span class="sxs-lookup"><span data-stu-id="b1520-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b1520-143">?: Operator</span><span class="sxs-lookup"><span data-stu-id="b1520-143">?: Operator</span></span>](../operators/conditional-operator.md)
- [<span data-ttu-id="b1520-144">if-else-Anweisung (C++)</span><span class="sxs-lookup"><span data-stu-id="b1520-144">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)
- [<span data-ttu-id="b1520-145">switch</span><span class="sxs-lookup"><span data-stu-id="b1520-145">switch</span></span>](switch.md)
