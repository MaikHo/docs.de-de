---
title: Zuweisungsoperatoren (C#-Referenz)
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 7b4f3b3f4d6b697903461f08435552f2df36bfe4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916929"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="ab5ce-102">Zuweisungsoperatoren (C#-Referenz)</span><span class="sxs-lookup"><span data-stu-id="ab5ce-102">Assignment operators (C# reference)</span></span>

<span data-ttu-id="ab5ce-103">Der Zuweisungsoperator `=` weist den Wert seines rechtsseitigen Operanden einer Variablen, einer [Eigenschaft](../../programming-guide/classes-and-structs/properties.md) oder einem, durch seinen linksseitigen Operanden angegebenen [Indexer](../../programming-guide/indexers/index.md)-Element zu.</span><span class="sxs-lookup"><span data-stu-id="ab5ce-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="ab5ce-104">Das Ergebnis eines Zuweisungsausdrucks ist der Wert, der dem linksseitigen Operanden zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="ab5ce-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="ab5ce-105">Der Typ des rechtsseitigen Operanden muss mit dem Typ des linksseitigen Operanden übereinstimmen oder implizit in ihn konvertierbar sein.</span><span class="sxs-lookup"><span data-stu-id="ab5ce-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="ab5ce-106">Der Zuweisungsoperator `=` ist rechtsassoziativ, d. h. ein Ausdruck der Form</span><span class="sxs-lookup"><span data-stu-id="ab5ce-106">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="ab5ce-107">wird als ausgewertet,</span><span class="sxs-lookup"><span data-stu-id="ab5ce-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="ab5ce-108">Das folgende Beispiel zeigt die Verwendung des Zuweisungsoperators mit einer lokalen Variablen, einer Eigenschaft und einem Indexerelement als linksseitigem Operanden:</span><span class="sxs-lookup"><span data-stu-id="ab5ce-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](snippets/shared/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="ab5ce-109">ref-Zuweisungsoperator</span><span class="sxs-lookup"><span data-stu-id="ab5ce-109">ref assignment operator</span></span>

<span data-ttu-id="ab5ce-110">Ab C# 7.3 können Sie mit dem ref-Zuweisungsoperator `= ref` eine [ref local](../keywords/ref.md#ref-locals)- oder [ref readonly local](../keywords/ref.md#ref-readonly-locals)-Variable neu zuweisen.</span><span class="sxs-lookup"><span data-stu-id="ab5ce-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="ab5ce-111">Im folgenden Beispiel wird die Verwendung des ref-Zuweisungsoperators veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="ab5ce-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](snippets/shared/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="ab5ce-112">Im Fall des REF-Zuweisungsoperators müssen beide Operanden vom gleichen Typ sein.</span><span class="sxs-lookup"><span data-stu-id="ab5ce-112">In the case of the ref assignment operator, the both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="ab5ce-113">Verbundzuweisung</span><span class="sxs-lookup"><span data-stu-id="ab5ce-113">Compound assignment</span></span>

<span data-ttu-id="ab5ce-114">Bei einem binären Operator `op` entspricht ein Verbundzuweisungsausdruck der Form</span><span class="sxs-lookup"><span data-stu-id="ab5ce-114">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="ab5ce-115">für die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="ab5ce-115">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="ab5ce-116">außer dass `x` nur einmal überprüft wird.</span><span class="sxs-lookup"><span data-stu-id="ab5ce-116">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="ab5ce-117">Verbundzuweisungen werden von [arithmetischen](arithmetic-operators.md#compound-assignment), [logischen booleschen](boolean-logical-operators.md#compound-assignment) und [bitweisen logischen und Verschiebungs-](bitwise-and-shift-operators.md#compound-assignment)-Operatoren unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ab5ce-117">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="ab5ce-118">NULL-Coalescing-Zuweisung</span><span class="sxs-lookup"><span data-stu-id="ab5ce-118">Null-coalescing assignment</span></span>

<span data-ttu-id="ab5ce-119">Sie können ab C# 8.0 den NULL-Coalescing-Zuweisungsoperator `??=` verwenden, um den Wert des rechten Operanden dem linken Operanden nur dann zuzuweisen, wenn die Auswertung des linken Operanden `null` ergibt.</span><span class="sxs-lookup"><span data-stu-id="ab5ce-119">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="ab5ce-120">Weitere Informationen finden Sie im Artikel zu den Operatoren [?? und ??=](null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ab5ce-120">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ab5ce-121">Operatorüberladbarkeit</span><span class="sxs-lookup"><span data-stu-id="ab5ce-121">Operator overloadability</span></span>

<span data-ttu-id="ab5ce-122">Ein benutzerdefinierter Typ kann den Zuweisungsoperator [nicht überladen](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="ab5ce-122">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="ab5ce-123">Ein benutzerdefinierter Typ kann jedoch eine implizite Konvertierung in einen anderen Typ definieren.</span><span class="sxs-lookup"><span data-stu-id="ab5ce-123">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="ab5ce-124">Auf diese Weise kann der Wert eines benutzerdefinierten Typs einer Variablen, einer Eigenschaft oder einem Indexerelement eines anderen Typs zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="ab5ce-124">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="ab5ce-125">Weitere Informationen finden Sie unter [Benutzerdefinierte Konvertierungsoperatoren](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ab5ce-125">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="ab5ce-126">Ein benutzerdefinierter Typ kann einen Verbundzuweisungsoperator nicht explizit überladen.</span><span class="sxs-lookup"><span data-stu-id="ab5ce-126">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="ab5ce-127">Wenn jedoch ein benutzerdefinierter Typ einen binären `op`-Operator überlädt, wird der `op=`-Operator, sofern vorhanden, ebenfalls implizit überladen.</span><span class="sxs-lookup"><span data-stu-id="ab5ce-127">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ab5ce-128">C#-Sprachspezifikation</span><span class="sxs-lookup"><span data-stu-id="ab5ce-128">C# language specification</span></span>

<span data-ttu-id="ab5ce-129">Weitere Informationen finden Sie im Abschnitt [Zuweisungsoperatoren](~/_csharplang/spec/expressions.md#assignment-operators) der [C#-Sprachspezifikation](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ab5ce-129">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="ab5ce-130">Weitere Informationen zum REF-Zuweiseungsoperator `= ref` finden Sie unter [Hinweis zum Featurevorschlag](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="ab5ce-130">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab5ce-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ab5ce-131">See also</span></span>

- [<span data-ttu-id="ab5ce-132">C#-Referenz</span><span class="sxs-lookup"><span data-stu-id="ab5ce-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ab5ce-133">C#-Operatoren und -Ausdrücke</span><span class="sxs-lookup"><span data-stu-id="ab5ce-133">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="ab5ce-134">ref (C#-Referenz)</span><span class="sxs-lookup"><span data-stu-id="ab5ce-134">ref keyword</span></span>](../keywords/ref.md)
