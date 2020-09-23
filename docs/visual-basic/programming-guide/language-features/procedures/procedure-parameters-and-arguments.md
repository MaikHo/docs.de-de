---
title: Parameter und Argumente von Prozeduren
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: c7f8eb1fa4e1fa3d87474d048d5a60994b0b7fc5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071273"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="609ed-102">Parameter und Argumente von Prozeduren (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="609ed-102">Procedure Parameters and Arguments (Visual Basic)</span></span>

<span data-ttu-id="609ed-103">In den meisten Fällen benötigt eine Prozedur einige Informationen zu den Bedingungen, in denen Sie aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="609ed-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="609ed-104">Eine Prozedur, die wiederholte oder freigegebene Tasks ausführt, verwendet für jeden-Rückruf verschiedene Informationen.</span><span class="sxs-lookup"><span data-stu-id="609ed-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="609ed-105">Diese Informationen bestehen aus Variablen, Konstanten und Ausdrücken, die Sie an die Prozedur übergeben, wenn Sie sie aufgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="609ed-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="609ed-106">Ein *Parameter* stellt einen Wert dar, den die Prozedur beim Aufrufen erwartet.</span><span class="sxs-lookup"><span data-stu-id="609ed-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="609ed-107">Die-Deklaration der Prozedur definiert ihre Parameter.</span><span class="sxs-lookup"><span data-stu-id="609ed-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="609ed-108">Sie können eine Prozedur ohne Parameter, einen Parameter oder mehr als einen Parameter definieren.</span><span class="sxs-lookup"><span data-stu-id="609ed-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="609ed-109">Der Teil der Prozedur Definition, der die Parameter angibt, wird als *Parameterliste*bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="609ed-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="609ed-110">Ein *Argument* stellt den Wert dar, den Sie für einen Prozedur Parameter angeben, wenn Sie die Prozedur aufrufen.</span><span class="sxs-lookup"><span data-stu-id="609ed-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="609ed-111">Der Aufruf Code liefert die Argumente, wenn die Prozedur aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="609ed-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="609ed-112">Der Teil des Prozedur Aufrufs, der die Argumente angibt, wird als *Argumentliste*bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="609ed-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="609ed-113">Die folgende Abbildung zeigt den Code, der die Prozedur `safeSquareRoot` von zwei verschiedenen Stellen aus aufrufen.</span><span class="sxs-lookup"><span data-stu-id="609ed-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="609ed-114">Der erste-Befehl übergibt den Wert der-Variablen `x` (4,0) an den `number` -Parameter, und der Rückgabewert in `root` (2,0) wird der-Variablen zugewiesen `y` .</span><span class="sxs-lookup"><span data-stu-id="609ed-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="609ed-115">Der zweite-Rückruf übergibt den Literalwert 9,0 an `number` und weist den Rückgabewert (3,0) der Variablen zu `z` .</span><span class="sxs-lookup"><span data-stu-id="609ed-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![Diagramm, das die Übergabe eines Arguments an einen Parameter anzeigt](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="609ed-117">Weitere Informationen finden Sie [unter Unterschiede zwischen Parametern und Argumenten](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="609ed-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="609ed-118">Parameter Datentyp</span><span class="sxs-lookup"><span data-stu-id="609ed-118">Parameter Data Type</span></span>  

 <span data-ttu-id="609ed-119">Sie definieren einen Datentyp für einen Parameter, indem Sie die- `As` Klausel in der-Deklaration verwenden.</span><span class="sxs-lookup"><span data-stu-id="609ed-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="609ed-120">Die folgende Funktion akzeptiert z. b. eine Zeichenfolge und eine ganze Zahl.</span><span class="sxs-lookup"><span data-stu-id="609ed-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="609ed-121">Wenn der Schalter für die Typüberprüfung ([Option Strict-Anweisung](../../../language-reference/statements/option-strict-statement.md)) ist `Off,` `As` , ist die-Klausel optional, mit dem Unterschied, dass alle Parameter diese verwenden müssen, wenn Sie von einem Parameter verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="609ed-121">If the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="609ed-122">Wenn die Typüberprüfung `On` den Wert hat, ist die- `As` Klausel für alle Prozedur Parameter erforderlich.</span><span class="sxs-lookup"><span data-stu-id="609ed-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="609ed-123">Wenn der aufrufende Code erwartet, dass ein Argument mit einem Datentyp, der sich von dem des entsprechenden Parameters unterscheidet, z. b. einem Parameter, bereitgestellt wird, `Byte` `String` muss er eine der folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="609ed-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="609ed-124">Geben Sie nur Argumente mit Datentypen an, die in den Parameter Datentyp erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="609ed-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="609ed-125">Festlegen `Option Strict Off` , um implizite einschränkende Konvertierungen zuzulassen; oder</span><span class="sxs-lookup"><span data-stu-id="609ed-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="609ed-126">Verwenden Sie ein Konvertierungs Schlüsselwort, um den Datentyp explizit zu konvertieren</span><span class="sxs-lookup"><span data-stu-id="609ed-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="609ed-127">Typparameter</span><span class="sxs-lookup"><span data-stu-id="609ed-127">Type Parameters</span></span>  

 <span data-ttu-id="609ed-128">Eine *generische Prozedur* definiert Zusätzlich zu ihren normalen Parametern auch einen oder mehrere *Typparameter* .</span><span class="sxs-lookup"><span data-stu-id="609ed-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="609ed-129">Eine generische Prozedur ermöglicht es dem aufrufenden Code, beim Aufrufen der Prozedur verschiedene Datentypen zu übergeben, sodass die Datentypen an die Anforderungen der einzelnen Aufrufe angepasst werden können.</span><span class="sxs-lookup"><span data-stu-id="609ed-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="609ed-130">Siehe [Generic Procedures in Visual Basic](../data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="609ed-130">See [Generic Procedures in Visual Basic](../data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609ed-131">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="609ed-131">See also</span></span>

- [<span data-ttu-id="609ed-132">Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="609ed-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="609ed-133">Sub-Prozeduren</span><span class="sxs-lookup"><span data-stu-id="609ed-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="609ed-134">Function-Prozeduren</span><span class="sxs-lookup"><span data-stu-id="609ed-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="609ed-135">Eigenschaftenprozeduren</span><span class="sxs-lookup"><span data-stu-id="609ed-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="609ed-136">Operatorprozeduren</span><span class="sxs-lookup"><span data-stu-id="609ed-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="609ed-137">Vorgehensweise: Definieren eines Parameters für eine Prozedur</span><span class="sxs-lookup"><span data-stu-id="609ed-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="609ed-138">Vorgehensweise: Übergeben von Argumenten an eine Prozedur</span><span class="sxs-lookup"><span data-stu-id="609ed-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="609ed-139">Übergeben von Argumenten als Wert und als Verweis</span><span class="sxs-lookup"><span data-stu-id="609ed-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="609ed-140">Prozedurüberladung</span><span class="sxs-lookup"><span data-stu-id="609ed-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="609ed-141">Typkonvertierung in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="609ed-141">Type Conversions in Visual Basic</span></span>](../data-types/type-conversions.md)
