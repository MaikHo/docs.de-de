---
title: Overrides
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 8506aba7e64f2dbd975cc275cefb7b5bb1aefda5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875008"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="02272-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02272-102">Overridable (Visual Basic)</span></span>

<span data-ttu-id="02272-103">Gibt an, dass eine Eigenschaft oder Prozedur durch eine identisch benannte Eigenschaft oder Prozedur in einer abgeleiteten Klasse überschrieben werden kann.</span><span class="sxs-lookup"><span data-stu-id="02272-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02272-104">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="02272-104">Remarks</span></span>  

 <span data-ttu-id="02272-105">Der- `Overridable` Modifizierer ermöglicht, dass eine Eigenschaft oder Methode in einer Klasse in einer abgeleiteten Klasse überschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="02272-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="02272-106">Der [nodeverridable](notoverridable.md) -Modifizierer verhindert, dass eine Eigenschaft oder Methode in einer abgeleiteten Klasse überschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="02272-106">The [NotOverridable](notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="02272-107">Weitere Informationen finden Sie unter [Grundlagen der Vererbung](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="02272-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="02272-108">Wenn der `Overridable` - `NotOverridable` Modifizierer oder der-Modifizierer nicht angegeben wird, ist die Standardeinstellung davon abhängig, ob die Eigenschaft oder Methode eine Basisklassen Eigenschaft oder-Methode überschreibt.</span><span class="sxs-lookup"><span data-stu-id="02272-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="02272-109">Wenn die Eigenschaft oder Methode eine Basisklassen Eigenschaft oder-Methode überschreibt, ist die Standardeinstellung `Overridable` . andernfalls ist Sie `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="02272-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="02272-110">Sie können einen Schatten oder überschreiben, um ein geerbtes Element neu zu definieren, aber es gibt bedeutende Unterschiede zwischen den beiden Ansätzen.</span><span class="sxs-lookup"><span data-stu-id="02272-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="02272-111">Weitere Informationen finden Sie unter [shadowingin Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="02272-111">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="02272-112">Ein Element, das überschrieben werden kann, wird manchmal als *Virtuelles* Element bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="02272-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="02272-113">Wenn Sie überschrieben werden kann, aber nicht sein muss, wird Sie manchmal auch als *konkretes* Element bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="02272-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="02272-114">Sie können `Overridable` nur in einer Deklarations Anweisung für eine Eigenschaft oder Prozedur verwenden.</span><span class="sxs-lookup"><span data-stu-id="02272-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="02272-115">Kombinierte modifiziererer</span><span class="sxs-lookup"><span data-stu-id="02272-115">Combined Modifiers</span></span>  

 <span data-ttu-id="02272-116">Sie können `Overridable` oder `NotOverridable` für eine `Private` Methode nicht angeben.</span><span class="sxs-lookup"><span data-stu-id="02272-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="02272-117">Sie können nicht `Overridable` mit `MustOverride` , `NotOverridable` oder `Shared` in derselben Deklaration angeben.</span><span class="sxs-lookup"><span data-stu-id="02272-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="02272-118">Da ein überschreibendes Element implizit überschreibbar ist, können Sie `Overridable` nicht mit `Overrides` kombinieren.</span><span class="sxs-lookup"><span data-stu-id="02272-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="02272-119">Verwendung</span><span class="sxs-lookup"><span data-stu-id="02272-119">Usage</span></span>  

 <span data-ttu-id="02272-120">Der `Overridable`-Modifizierer kann in folgenden Kontexten verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="02272-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="02272-121">Function-Anweisung</span><span class="sxs-lookup"><span data-stu-id="02272-121">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="02272-122">Property Statement</span><span class="sxs-lookup"><span data-stu-id="02272-122">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="02272-123">Sub-Anweisung</span><span class="sxs-lookup"><span data-stu-id="02272-123">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="02272-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="02272-124">See also</span></span>

- [<span data-ttu-id="02272-125">Modifizierer</span><span class="sxs-lookup"><span data-stu-id="02272-125">Modifiers</span></span>](index.md)
- [<span data-ttu-id="02272-126">Grundlagen der Vererbung</span><span class="sxs-lookup"><span data-stu-id="02272-126">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="02272-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="02272-127">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="02272-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="02272-128">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="02272-129">Überschreibt</span><span class="sxs-lookup"><span data-stu-id="02272-129">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="02272-130">Schlüsselwörter</span><span class="sxs-lookup"><span data-stu-id="02272-130">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="02272-131">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="02272-131">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
