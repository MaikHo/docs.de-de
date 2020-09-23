---
title: Parameterarrays
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: 2c8c60015d834ffa3f8618dd98616350e13f0e5c
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100658"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="fbdd7-102">Parameterarrays (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbdd7-102">Parameter Arrays (Visual Basic)</span></span>

<span data-ttu-id="fbdd7-103">In der Regel ist es nicht möglich, eine Prozedur mit mehr Argumenten aufzurufen, als die Prozedur Deklaration angibt.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="fbdd7-104">Wenn Sie eine unbegrenzte Anzahl von Argumenten benötigen, können Sie ein *Parameter Array*deklarieren, das es einer Prozedur ermöglicht, ein Array von Werten für einen Parameter zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="fbdd7-105">Wenn Sie die Prozedur definieren, müssen Sie nicht die Anzahl der Elemente im Parameter Array kennen.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="fbdd7-106">Die Array Größe wird einzeln durch jeden aufzurufenden Vorgang bestimmt.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="fbdd7-107">Deklarieren eines ParamArray</span><span class="sxs-lookup"><span data-stu-id="fbdd7-107">Declaring a ParamArray</span></span>  

 <span data-ttu-id="fbdd7-108">Sie verwenden das [ParamArray](../../../language-reference/modifiers/paramarray.md) -Schlüsselwort, um ein Parameter Array in der Parameterliste anzugeben.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-108">You use the [ParamArray](../../../language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="fbdd7-109">Es gelten die folgenden Regeln:</span><span class="sxs-lookup"><span data-stu-id="fbdd7-109">The following rules apply:</span></span>  
  
- <span data-ttu-id="fbdd7-110">Eine Prozedur kann nur ein Parameter Array definieren, und es muss der letzte Parameter in der Prozedur Definition sein.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
- <span data-ttu-id="fbdd7-111">Das Parameter Array muss als Wert übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="fbdd7-112">Es empfiehlt sich, das [ByVal](../../../language-reference/modifiers/byval.md) -Schlüsselwort explizit in die Prozedur Definition einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-112">It is good programming practice to explicitly include the [ByVal](../../../language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
- <span data-ttu-id="fbdd7-113">Das Parameter Array ist automatisch optional.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="fbdd7-114">Der Standardwert ist ein leeres eindimensionales Array des Elementtyps des Parameter Arrays.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
- <span data-ttu-id="fbdd7-115">Alle Parameter, die dem Parameter Array vorangestellt sind, müssen erforderlich sein.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="fbdd7-116">Das Parameter Array muss der einzige optionale Parameter sein.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="fbdd7-117">Aufrufen eines ParamArray-Parametern</span><span class="sxs-lookup"><span data-stu-id="fbdd7-117">Calling a ParamArray</span></span>  

 <span data-ttu-id="fbdd7-118">Wenn Sie eine Prozedur aufrufen, die ein Parameter Array definiert, können Sie das Argument auf eine der folgenden Arten angeben:</span><span class="sxs-lookup"><span data-stu-id="fbdd7-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
- <span data-ttu-id="fbdd7-119">Nothing – das heißt, Sie können das [ParamArray](../../../language-reference/modifiers/paramarray.md) -Argument weglassen.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-119">Nothing — that is, you can omit the [ParamArray](../../../language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="fbdd7-120">In diesem Fall wird ein leeres Array an die Prozedur übermittelt.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="fbdd7-121">Wenn Sie das [Nothing](../../../language-reference/nothing.md) -Schlüsselwort explizit übergeben, wird ein NULL-Array an die Prozedur übergeben und kann zu einer NullReferenceException führen, wenn die aufgerufene Prozedur nicht auf diese Bedingung überprüft.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-121">If you explicitly pass the [Nothing](../../../language-reference/nothing.md) keyword, a null array is passed to the procedure and may result in a NullReferenceException if the called procedure does not check for this condition.</span></span>
  
- <span data-ttu-id="fbdd7-122">Eine Liste mit einer beliebigen Anzahl von Argumenten, die durch Kommas getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="fbdd7-123">Der Datentyp der einzelnen Argumente muss implizit in den Elementtyp konvertierbar sein `ParamArray` .</span><span class="sxs-lookup"><span data-stu-id="fbdd7-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
- <span data-ttu-id="fbdd7-124">Ein Array mit demselben Elementtyp wie der Elementtyp des Parameter Arrays.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="fbdd7-125">In allen Fällen behandelt der Code in der Prozedur das Parameter Array als eindimensionales Array mit Elementen desselben Datentyps wie der `ParamArray` Datentyp.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fbdd7-126">Wenn Sie sich mit einem Array befassen, das unbegrenzt groß sein kann, besteht das Risiko, dass eine interne Kapazität der Anwendung überschritten wird.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="fbdd7-127">Wenn Sie ein Parameter Array akzeptieren, sollten Sie die Größe des Arrays testen, das dem aufrufenden Code übergeben wurde.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="fbdd7-128">Führen Sie die entsprechenden Schritte aus, wenn Sie für Ihre Anwendung zu groß sind.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="fbdd7-129">Weitere Informationen finden Sie unter [Arrays](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="fbdd7-129">For more information, see [Arrays](../arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbdd7-130">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fbdd7-130">Example</span></span>  

 <span data-ttu-id="fbdd7-131">Im folgenden Beispiel wird die-Funktion definiert und aufgerufen `calcSum` .</span><span class="sxs-lookup"><span data-stu-id="fbdd7-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="fbdd7-132">Der- `ParamArray` Modifizierer für den-Parameter `args` ermöglicht der-Funktion, eine Variable Anzahl von Argumenten zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="fbdd7-133">Im folgenden Beispiel wird eine Prozedur mit einem Parameter Array definiert und die Werte aller Array Elemente ausgegeben, die an das Parameter Array übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="fbdd7-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="fbdd7-134">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="fbdd7-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="fbdd7-135">Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="fbdd7-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="fbdd7-136">Parameter und Argumente von Prozeduren</span><span class="sxs-lookup"><span data-stu-id="fbdd7-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="fbdd7-137">Übergeben von Argumenten als Wert und als Verweis</span><span class="sxs-lookup"><span data-stu-id="fbdd7-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="fbdd7-138">Übergeben von Argumenten nach Position und Name</span><span class="sxs-lookup"><span data-stu-id="fbdd7-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="fbdd7-139">Optionale Parameter</span><span class="sxs-lookup"><span data-stu-id="fbdd7-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="fbdd7-140">Prozedurüberladung</span><span class="sxs-lookup"><span data-stu-id="fbdd7-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="fbdd7-141">Arrays</span><span class="sxs-lookup"><span data-stu-id="fbdd7-141">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="fbdd7-142">Optional</span><span class="sxs-lookup"><span data-stu-id="fbdd7-142">Optional</span></span>](../../../language-reference/modifiers/optional.md)
