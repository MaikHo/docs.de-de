---
title: Operator -=
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 9149d9b350fc05c5e576f9f7800725aeb330e79d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873296"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="a74c7-102">-=-Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a74c7-102">-= Operator (Visual Basic)</span></span>

<span data-ttu-id="a74c7-103">Subtrahiert den Wert eines Ausdrucks vom Wert einer Variablen oder Eigenschaft und weist das Ergebnis der Variablen oder der Eigenschaft zu.</span><span class="sxs-lookup"><span data-stu-id="a74c7-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a74c7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a74c7-104">Syntax</span></span>  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="a74c7-105">Bestandteile</span><span class="sxs-lookup"><span data-stu-id="a74c7-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="a74c7-106">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a74c7-106">Required.</span></span> <span data-ttu-id="a74c7-107">Eine beliebige numerische Variable oder Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="a74c7-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="a74c7-108">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a74c7-108">Required.</span></span> <span data-ttu-id="a74c7-109">Ein beliebiger numerischer Ausdruck.</span><span class="sxs-lookup"><span data-stu-id="a74c7-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a74c7-110">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="a74c7-110">Remarks</span></span>  

 <span data-ttu-id="a74c7-111">Das Element auf der linken Seite des `-=` Operators kann eine einfache skalare Variable, eine Eigenschaft oder ein Element eines Arrays sein.</span><span class="sxs-lookup"><span data-stu-id="a74c7-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="a74c7-112">Die Variable oder [Eigenschaft darf nicht schreibgeschützt sein.](../modifiers/readonly.md)</span><span class="sxs-lookup"><span data-stu-id="a74c7-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="a74c7-113">Der `-=` Operator subtrahiert zuerst den Wert des Ausdrucks (auf der rechten Seite des Operators) vom Wert der Variablen oder Eigenschaft (auf der linken Seite des Operators).</span><span class="sxs-lookup"><span data-stu-id="a74c7-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="a74c7-114">Der-Operator weist dann das Ergebnis dieses Vorgangs der Variablen oder der Eigenschaft zu.</span><span class="sxs-lookup"><span data-stu-id="a74c7-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a74c7-115">Überladen</span><span class="sxs-lookup"><span data-stu-id="a74c7-115">Overloading</span></span>  

 <span data-ttu-id="a74c7-116">Der [-Operator (Visual Basic)](subtraction-operator.md) kann *überladen*werden. Dies bedeutet, dass eine Klasse oder Struktur das Verhalten neu definieren kann, wenn ein Operand den Typ dieser Klasse oder Struktur aufweist.</span><span class="sxs-lookup"><span data-stu-id="a74c7-116">The [- Operator (Visual Basic)](subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a74c7-117">Das Überladen des- `-` Operators wirkt sich auf das Verhalten des- `-=` Operators aus.</span><span class="sxs-lookup"><span data-stu-id="a74c7-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="a74c7-118">Wenn Ihr Code `-=` für eine Klasse oder Struktur verwendet, die überlastet `-` ist, stellen Sie sicher, dass Sie das neu definierte Verhalten verstehen.</span><span class="sxs-lookup"><span data-stu-id="a74c7-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a74c7-119">Weitere Informationen finden Sie unter [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a74c7-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a74c7-120">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a74c7-120">Example</span></span>  

 <span data-ttu-id="a74c7-121">Im folgenden Beispiel wird der `-=` -Operator verwendet, um eine Variable von einer anderen zu subtrahieren `Integer` und das Ergebnis der letzteren Variablen zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="a74c7-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="a74c7-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a74c7-122">See also</span></span>

- [<span data-ttu-id="a74c7-123">--Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a74c7-123">- Operator (Visual Basic)</span></span>](subtraction-operator.md)
- [<span data-ttu-id="a74c7-124">Zuweisungsoperatoren</span><span class="sxs-lookup"><span data-stu-id="a74c7-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="a74c7-125">Arithmetic Operators (Arithmetische Operatoren)</span><span class="sxs-lookup"><span data-stu-id="a74c7-125">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="a74c7-126">Operatorrangfolge in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a74c7-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="a74c7-127">Nach Funktionalität sortierte Operatoren</span><span class="sxs-lookup"><span data-stu-id="a74c7-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="a74c7-128">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="a74c7-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
