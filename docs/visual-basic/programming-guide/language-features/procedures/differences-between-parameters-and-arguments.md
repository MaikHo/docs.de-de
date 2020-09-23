---
title: Unterschiede zwischen Parametern und Argumenten
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: 0ad9104f347205cebc6e078aac246a413c0d9b78
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057844"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="14a5d-102">Unterschiede zwischen Parametern und Argumenten (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14a5d-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>

<span data-ttu-id="14a5d-103">In den meisten Fällen muss eine Prozedur über einige Informationen zu den Bedingungen verfügen, in denen Sie aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="14a5d-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="14a5d-104">Eine Prozedur, die wiederholte oder freigegebene Tasks ausführt, verwendet für jeden-Rückruf verschiedene Informationen.</span><span class="sxs-lookup"><span data-stu-id="14a5d-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="14a5d-105">Diese Informationen bestehen aus Variablen, Konstanten und Ausdrücken, die Sie an die Prozedur übergeben, wenn Sie sie aufgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="14a5d-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="14a5d-106">Um diese Informationen an die Prozedur zu übermitteln, definiert die Prozedur einen *Parameter*, und der aufrufende Code übergibt ein *Argument* an diesen Parameter.</span><span class="sxs-lookup"><span data-stu-id="14a5d-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="14a5d-107">Sie können sich den-Parameter als Platz als Platz für das-und-Argument vorstellen.</span><span class="sxs-lookup"><span data-stu-id="14a5d-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="14a5d-108">Ebenso wie unterschiedliche Fahrzeuge sich zu unterschiedlichen Zeiten in einem Park Platz befinden können, kann der aufrufende Code jedes Mal, wenn die Prozedur aufgerufen wird, ein anderes Argument an denselben Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="14a5d-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="14a5d-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="14a5d-109">Parameters</span></span>  

 <span data-ttu-id="14a5d-110">Ein *Parameter* stellt einen Wert dar, den die Prozedur beim Aufrufen erwartet.</span><span class="sxs-lookup"><span data-stu-id="14a5d-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="14a5d-111">Die-Deklaration der Prozedur definiert ihre Parameter.</span><span class="sxs-lookup"><span data-stu-id="14a5d-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="14a5d-112">Wenn Sie eine- `Function` oder- `Sub` Prozedur definieren, geben Sie eine *Parameterliste* direkt nach dem Prozedur Namen in Klammern an.</span><span class="sxs-lookup"><span data-stu-id="14a5d-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="14a5d-113">Für jeden Parameter geben Sie einen Namen, einen Datentyp und einen Übergabe Mechanismus an ([ByVal](../../../language-reference/modifiers/byval.md) oder [ByRef](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="14a5d-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="14a5d-114">Sie können auch angeben, dass ein Parameter optional ist.</span><span class="sxs-lookup"><span data-stu-id="14a5d-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="14a5d-115">Dies bedeutet, dass der aufrufenden Code keinen Wert für ihn übergeben muss.</span><span class="sxs-lookup"><span data-stu-id="14a5d-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="14a5d-116">Der Name jedes Parameters dient als *lokale Variable* in der Prozedur.</span><span class="sxs-lookup"><span data-stu-id="14a5d-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="14a5d-117">Sie verwenden den Parameternamen auf dieselbe Weise wie eine beliebige andere Variable.</span><span class="sxs-lookup"><span data-stu-id="14a5d-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="14a5d-118">Argumente</span><span class="sxs-lookup"><span data-stu-id="14a5d-118">Arguments</span></span>  

 <span data-ttu-id="14a5d-119">Ein *Argument* stellt den Wert dar, den Sie an einen Prozedur Parameter übergeben, wenn Sie die Prozedur aufrufen.</span><span class="sxs-lookup"><span data-stu-id="14a5d-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="14a5d-120">Der Aufruf Code liefert die Argumente, wenn die Prozedur aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="14a5d-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="14a5d-121">Wenn Sie eine- `Function` oder-Prozedur aufzurufen `Sub` , fügen Sie eine *Argumentliste* direkt nach dem Prozedur Namen in Klammern ein.</span><span class="sxs-lookup"><span data-stu-id="14a5d-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="14a5d-122">Jedes Argument entspricht dem-Parameter an derselben Position in der Liste.</span><span class="sxs-lookup"><span data-stu-id="14a5d-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="14a5d-123">Im Gegensatz zur Parameterdefinition haben Argumente keine Namen.</span><span class="sxs-lookup"><span data-stu-id="14a5d-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="14a5d-124">Jedes Argument ist ein Ausdruck, der NULL oder mehr Variablen, Konstanten und Literale enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="14a5d-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="14a5d-125">Der Datentyp des ausgewerteten Ausdrucks sollte in der Regel mit dem Datentyp übereinstimmen, der für den entsprechenden Parameter definiert ist, und in jedem Fall muss er in den Parametertyp konvertierbar sein.</span><span class="sxs-lookup"><span data-stu-id="14a5d-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a5d-126">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="14a5d-126">See also</span></span>

- [<span data-ttu-id="14a5d-127">Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="14a5d-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="14a5d-128">Sub-Prozeduren</span><span class="sxs-lookup"><span data-stu-id="14a5d-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="14a5d-129">Function-Prozeduren</span><span class="sxs-lookup"><span data-stu-id="14a5d-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="14a5d-130">Eigenschaftenprozeduren</span><span class="sxs-lookup"><span data-stu-id="14a5d-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="14a5d-131">Operatorprozeduren</span><span class="sxs-lookup"><span data-stu-id="14a5d-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="14a5d-132">Vorgehensweise: Definieren eines Parameters für eine Prozedur</span><span class="sxs-lookup"><span data-stu-id="14a5d-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="14a5d-133">Vorgehensweise: Übergeben von Argumenten an eine Prozedur</span><span class="sxs-lookup"><span data-stu-id="14a5d-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="14a5d-134">Übergeben von Argumenten als Wert und als Verweis</span><span class="sxs-lookup"><span data-stu-id="14a5d-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="14a5d-135">Rekursive Prozeduren</span><span class="sxs-lookup"><span data-stu-id="14a5d-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="14a5d-136">Prozedurüberladung</span><span class="sxs-lookup"><span data-stu-id="14a5d-136">Procedure Overloading</span></span>](./procedure-overloading.md)
