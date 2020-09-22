---
title: TryCast-Operator
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: dc4807781f9e1aaf894016952911bd7b32c42948
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875314"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="95391-102">TryCast-Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95391-102">TryCast Operator (Visual Basic)</span></span>

<span data-ttu-id="95391-103">Führt einen Typkonvertierungs Vorgang ein, der keine Ausnahme auslöst.</span><span class="sxs-lookup"><span data-stu-id="95391-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95391-104">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="95391-104">Remarks</span></span>  

 <span data-ttu-id="95391-105">Wenn eine Konvertierungs Versuch fehlschlägt, lösen `CType` `DirectCast` beide einen <xref:System.InvalidCastException> Fehler aus.</span><span class="sxs-lookup"><span data-stu-id="95391-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="95391-106">Dies kann sich negativ auf die Leistung Ihrer Anwendung auswirken.</span><span class="sxs-lookup"><span data-stu-id="95391-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="95391-107">`TryCast` gibt [nichts](../nothing.md)zurück, sodass Sie nur das zurückgegebene Ergebnis für testen müssen, anstatt eine mögliche Ausnahme behandeln zu müssen `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="95391-107">`TryCast` returns [Nothing](../nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="95391-108">Sie verwenden das `TryCast` -Schlüsselwort auf die gleiche Weise wie die [CType-Funktion](../functions/ctype-function.md) und das [DirectCast-Operator](directcast-operator.md) Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="95391-108">You use the `TryCast` keyword the same way you use the [CType Function](../functions/ctype-function.md) and the [DirectCast Operator](directcast-operator.md) keyword.</span></span> <span data-ttu-id="95391-109">Sie geben einen Ausdruck als erstes Argument und einen Typ an, in den es als zweites Argument konvertiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="95391-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="95391-110">`TryCast` funktioniert nur für Verweis Typen, z. b. Klassen und Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="95391-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="95391-111">Es ist eine Vererbungs-oder Implementierungs Beziehung zwischen den beiden Typen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="95391-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="95391-112">Dies bedeutet, dass ein Typ von einem Typ erben oder ihn implementieren muss.</span><span class="sxs-lookup"><span data-stu-id="95391-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="95391-113">Fehler und Fehler</span><span class="sxs-lookup"><span data-stu-id="95391-113">Errors and Failures</span></span>  

 <span data-ttu-id="95391-114">`TryCast` generiert einen Compilerfehler, wenn erkannt wird, dass keine Vererbungs-oder Implementierungs Beziehung vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="95391-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="95391-115">Das Fehlen eines Compilerfehlers garantiert jedoch nicht die erfolgreiche Konvertierung.</span><span class="sxs-lookup"><span data-stu-id="95391-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="95391-116">Wenn die gewünschte Konvertierung einschränkend ist, kann Sie zur Laufzeit fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="95391-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="95391-117">Wenn dies der Fall ist, wird `TryCast` [nichts](../nothing.md)zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="95391-117">If this happens, `TryCast` returns [Nothing](../nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="95391-118">Konvertierungsschlüsselwörter</span><span class="sxs-lookup"><span data-stu-id="95391-118">Conversion Keywords</span></span>  

 <span data-ttu-id="95391-119">Ein Vergleich der Schlüsselwörter für die Typkonvertierung lautet wie folgt.</span><span class="sxs-lookup"><span data-stu-id="95391-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="95391-120">Stichwort</span><span class="sxs-lookup"><span data-stu-id="95391-120">Keyword</span></span>|<span data-ttu-id="95391-121">Datentypen</span><span class="sxs-lookup"><span data-stu-id="95391-121">Data types</span></span>|<span data-ttu-id="95391-122">Argument Beziehung</span><span class="sxs-lookup"><span data-stu-id="95391-122">Argument relationship</span></span>|<span data-ttu-id="95391-123">Laufzeitfehler</span><span class="sxs-lookup"><span data-stu-id="95391-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="95391-124">CType Function</span><span class="sxs-lookup"><span data-stu-id="95391-124">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="95391-125">Beliebige Datentypen</span><span class="sxs-lookup"><span data-stu-id="95391-125">Any data types</span></span>|<span data-ttu-id="95391-126">Zwischen den beiden Datentypen muss eine erweiternde oder einschränkende Konvertierung definiert werden.</span><span class="sxs-lookup"><span data-stu-id="95391-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="95391-127">KEH <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="95391-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="95391-128">DirectCast-Operator</span><span class="sxs-lookup"><span data-stu-id="95391-128">DirectCast Operator</span></span>](directcast-operator.md)|<span data-ttu-id="95391-129">Beliebige Datentypen</span><span class="sxs-lookup"><span data-stu-id="95391-129">Any data types</span></span>|<span data-ttu-id="95391-130">Ein Typ muss von einem anderen Typ erben oder ihn implementieren.</span><span class="sxs-lookup"><span data-stu-id="95391-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="95391-131">KEH <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="95391-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="95391-132">Nur Verweis Typen</span><span class="sxs-lookup"><span data-stu-id="95391-132">Reference types only</span></span>|<span data-ttu-id="95391-133">Ein Typ muss von einem anderen Typ erben oder ihn implementieren.</span><span class="sxs-lookup"><span data-stu-id="95391-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="95391-134">Gibt [nichts](../nothing.md) zurück.</span><span class="sxs-lookup"><span data-stu-id="95391-134">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="95391-135">Beispiel</span><span class="sxs-lookup"><span data-stu-id="95391-135">Example</span></span>  

 <span data-ttu-id="95391-136">Das folgende Beispiel veranschaulicht die Verwendung von `TryCast`.</span><span class="sxs-lookup"><span data-stu-id="95391-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="95391-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="95391-137">See also</span></span>

- [<span data-ttu-id="95391-138">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="95391-138">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="95391-139">Implizite und explizite Konvertierungen</span><span class="sxs-lookup"><span data-stu-id="95391-139">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
