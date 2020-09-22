---
title: <expression> kann nicht als Typeinschränkung verwendet werden.
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 4f1db6bdbe6f25d0362b55acd95e716fbc2417ed
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874275"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="479c6-102">\<expression> kann nicht als Typeinschränkung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="479c6-102">'\<expression>' cannot be used as a type constraint</span></span>

<span data-ttu-id="479c6-103">Eine Einschränkungsliste enthält einen Ausdruck, der keine gültige Einschränkung für einen Typparameter darstellt.</span><span class="sxs-lookup"><span data-stu-id="479c6-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="479c6-104">Eine Einschränkungsliste erzwingt Anforderungen für das Typargument, das an den Typparameter übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="479c6-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="479c6-105">Sie können die folgenden Anforderungen in beliebiger Kombination angeben:</span><span class="sxs-lookup"><span data-stu-id="479c6-105">You can specify the following requirements in any combination:</span></span>  
  
- <span data-ttu-id="479c6-106">Das Typargument muss mindestens eine Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="479c6-106">The type argument must implement one or more interfaces</span></span>  
  
- <span data-ttu-id="479c6-107">Das Typargument darf von höchstens einer Klasse erben.</span><span class="sxs-lookup"><span data-stu-id="479c6-107">The type argument must inherit from at most one class</span></span>  
  
- <span data-ttu-id="479c6-108">Das Typargument muss einen parameterlosen Konstruktor verfügbar machen, auf den der erstellende Code zugreifen kann (die `New` -Einschränkung muss enthalten sein)</span><span class="sxs-lookup"><span data-stu-id="479c6-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="479c6-109">Wenn Sie keine bestimmte Klasse oder Schnittstelle in die Einschränkungsliste aufnehmen, können Sie eine allgemeinere Anforderung festlegen, indem Sie eine der folgenden Festlegungen treffen:</span><span class="sxs-lookup"><span data-stu-id="479c6-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
- <span data-ttu-id="479c6-110">Das Typargument muss ein Werttyp sein (die Einschränkung `Structure` enthalten)</span><span class="sxs-lookup"><span data-stu-id="479c6-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
- <span data-ttu-id="479c6-111">Das Typargument muss ein Verweistyp sein (die Einschränkung `Class` enthalten)</span><span class="sxs-lookup"><span data-stu-id="479c6-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="479c6-112">Sie können nicht sowohl `Structure` als auch `Class` für den gleichen Typparameter angeben, und Sie können jedes Schlüsselwort nur einmal angeben.</span><span class="sxs-lookup"><span data-stu-id="479c6-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="479c6-113">**Fehler-ID:** BC32061</span><span class="sxs-lookup"><span data-stu-id="479c6-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="479c6-114">So beheben Sie diesen Fehler</span><span class="sxs-lookup"><span data-stu-id="479c6-114">To correct this error</span></span>  
  
- <span data-ttu-id="479c6-115">Stellen Sie sicher, dass der Ausdruck und dessen Elemente richtig geschrieben sind.</span><span class="sxs-lookup"><span data-stu-id="479c6-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
- <span data-ttu-id="479c6-116">Wenn der Ausdruck die Anforderungen der vorangehenden Liste nicht erfüllt, entfernen Sie ihn aus der Einschränkungsliste.</span><span class="sxs-lookup"><span data-stu-id="479c6-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
- <span data-ttu-id="479c6-117">Wenn der Ausdruck auf eine Schnittstelle oder Klasse verweist, stellen Sie sicher, dass der Compiler Zugriff auf diese Schnittstelle oder Klasse hat.</span><span class="sxs-lookup"><span data-stu-id="479c6-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="479c6-118">Möglicherweise müssen Sie deren Namen qualifizieren und einen Verweis auf Ihr Projekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="479c6-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="479c6-119">Weitere Informationen finden Sie unter "Verweise auf Projekte" in [Verweise auf deklarierte Elemente](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="479c6-119">For more information, see "References to Projects" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="479c6-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="479c6-120">See also</span></span>

- [<span data-ttu-id="479c6-121">Generische Typen in Visual Basic (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="479c6-121">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="479c6-122">Wert- und Verweistypen</span><span class="sxs-lookup"><span data-stu-id="479c6-122">Value Types and Reference Types</span></span>](../../programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="479c6-123">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="479c6-123">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
