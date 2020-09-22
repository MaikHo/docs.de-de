---
title: Schlüssel
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 582ed5bb67b9c7504e736710aa4649cffb12ef45
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867991"
---
# <a name="key-visual-basic"></a><span data-ttu-id="f2526-102">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2526-102">Key (Visual Basic)</span></span>

<span data-ttu-id="f2526-103">Mit dem- `Key` Schlüsselwort können Sie das Verhalten von Eigenschaften anonymer Typen angeben.</span><span class="sxs-lookup"><span data-stu-id="f2526-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="f2526-104">Nur Eigenschaften, die Sie als Schlüsseleigenschaften festlegen, nehmen an Gleichheits Tests zwischen anonymen Typinstanzen oder der Berechnung von Hash Code Werten Teil.</span><span class="sxs-lookup"><span data-stu-id="f2526-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="f2526-105">Die Werte der Schlüsseleigenschaften können nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="f2526-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="f2526-106">Sie legen eine Eigenschaft eines anonymen Typs als Schlüsseleigenschaft fest, indem Sie das-Schlüsselwort `Key` vor der Deklaration in der Initialisierungs Liste platzieren.</span><span class="sxs-lookup"><span data-stu-id="f2526-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="f2526-107">Im folgenden Beispiel `Airline` `FlightNo` sind und Schlüsseleigenschaften, aber `Gate` nicht.</span><span class="sxs-lookup"><span data-stu-id="f2526-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 <span data-ttu-id="f2526-108">Wenn ein neuer anonymer Typ erstellt wird, erbt er direkt von <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="f2526-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="f2526-109">Der Compiler überschreibt drei geerbte Member: <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> und <xref:System.Object.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="f2526-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="f2526-110">Der für und erstellte Überschreibungs Code <xref:System.Object.Equals%2A> <xref:System.Object.GetHashCode%2A> basiert auf Schlüsseleigenschaften.</span><span class="sxs-lookup"><span data-stu-id="f2526-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="f2526-111">Wenn keine Schlüsseleigenschaften im Typ vorhanden sind <xref:System.Object.GetHashCode%2A> und <xref:System.Object.Equals%2A> nicht überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="f2526-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="f2526-112">Gleichheit</span><span class="sxs-lookup"><span data-stu-id="f2526-112">Equality</span></span>  

 <span data-ttu-id="f2526-113">Zwei anonyme Typinstanzen sind gleich, wenn Sie Instanzen desselben Typs sind und die Werte ihrer Schlüsseleigenschaften gleich sind.</span><span class="sxs-lookup"><span data-stu-id="f2526-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="f2526-114">In den folgenden Beispielen `flight2` ist gleich `flight1` dem vorherigen Beispiel, da Sie Instanzen desselben anonymen Typs sind und über übereinstimmende Werte für Ihre Schlüsseleigenschaften verfügen.</span><span class="sxs-lookup"><span data-stu-id="f2526-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="f2526-115">Ist jedoch `flight3` nicht gleich, `flight1` da Sie einen anderen Wert für eine Schlüsseleigenschaft hat: `FlightNo` .</span><span class="sxs-lookup"><span data-stu-id="f2526-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="f2526-116">Die-Instanz hat `flight4` nicht denselben Typ wie, `flight1` weil Sie unterschiedliche Eigenschaften als Schlüsseleigenschaften festlegen.</span><span class="sxs-lookup"><span data-stu-id="f2526-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 <span data-ttu-id="f2526-117">Wenn zwei Instanzen nur mit nicht Schlüsseleigenschaften deklariert werden, die in Name, Typ, Reihenfolge und Wert identisch sind, sind die beiden Instanzen nicht gleich.</span><span class="sxs-lookup"><span data-stu-id="f2526-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="f2526-118">Eine Instanz ohne Schlüsseleigenschaften ist nur mit sich selbst identisch.</span><span class="sxs-lookup"><span data-stu-id="f2526-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="f2526-119">Weitere Informationen zu den Bedingungen, unter denen zwei Instanzen eines anonymen Typs Instanzen desselben anonymen Typs sind, finden Sie unter [Anonyme Typen](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="f2526-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="f2526-120">Hash Code Berechnung</span><span class="sxs-lookup"><span data-stu-id="f2526-120">Hash Code Calculation</span></span>  

 <span data-ttu-id="f2526-121">Ebenso <xref:System.Object.Equals%2A> basiert die Hash Funktion, die in <xref:System.Object.GetHashCode%2A> für einen anonymen Typ definiert ist, auf den Schlüsseleigenschaften des-Typs.</span><span class="sxs-lookup"><span data-stu-id="f2526-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="f2526-122">Die folgenden Beispiele zeigen die Interaktion zwischen Schlüsseleigenschaften und Hashcodewerten.</span><span class="sxs-lookup"><span data-stu-id="f2526-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="f2526-123">Instanzen eines anonymen Typs, die dieselben Werte für alle Schlüsseleigenschaften aufweisen, haben denselben Hash Codewert, auch wenn nicht Schlüsseleigenschaften nicht übereinstimmende Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="f2526-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="f2526-124">Die folgende Anweisung gibt `True` zurück.</span><span class="sxs-lookup"><span data-stu-id="f2526-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 <span data-ttu-id="f2526-125">Instanzen eines anonymen Typs, die unterschiedliche Werte für eine oder mehrere Schlüsseleigenschaften aufweisen, haben unterschiedliche Hashcode-Werte.</span><span class="sxs-lookup"><span data-stu-id="f2526-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="f2526-126">Die folgende Anweisung gibt `False` zurück.</span><span class="sxs-lookup"><span data-stu-id="f2526-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 <span data-ttu-id="f2526-127">Instanzen anonymer Typen, die andere Eigenschaften als Schlüsseleigenschaften festlegen, sind keine Instanzen desselben Typs.</span><span class="sxs-lookup"><span data-stu-id="f2526-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="f2526-128">Sie haben verschiedene Hashcodewerte, auch wenn die Namen und Werte aller Eigenschaften identisch sind.</span><span class="sxs-lookup"><span data-stu-id="f2526-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="f2526-129">Die folgende Anweisung gibt `False` zurück.</span><span class="sxs-lookup"><span data-stu-id="f2526-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a><span data-ttu-id="f2526-130">Schreibgeschützte Werte</span><span class="sxs-lookup"><span data-stu-id="f2526-130">Read-Only Values</span></span>  

 <span data-ttu-id="f2526-131">Die Werte der Schlüsseleigenschaften können nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="f2526-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="f2526-132">Beispielsweise sind in `flight1` in den vorherigen Beispielen die `Airline` Felder und schreibgeschützt `FlightNo` , `Gate` können aber geändert werden.</span><span class="sxs-lookup"><span data-stu-id="f2526-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="f2526-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f2526-133">See also</span></span>

- [<span data-ttu-id="f2526-134">Definition von anonymen Typen</span><span class="sxs-lookup"><span data-stu-id="f2526-134">Anonymous Type Definition</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [<span data-ttu-id="f2526-135">Vorgehensweise: Ableiten von Eigenschaftennamen und Typen in Deklarationen von anonymen Typen</span><span class="sxs-lookup"><span data-stu-id="f2526-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="f2526-136">Anonyme Typen</span><span class="sxs-lookup"><span data-stu-id="f2526-136">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
