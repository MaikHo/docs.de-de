---
description: virtual – C#-Referenz
title: virtual – C#-Referenz
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 67bdfcf27bb108ca85e94ba7fdce208e4cd83b80
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141724"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="ee541-103">virtual (C#-Referenz)</span><span class="sxs-lookup"><span data-stu-id="ee541-103">virtual (C# Reference)</span></span>

<span data-ttu-id="ee541-104">Das Schlüsselwort `virtual` wird zum Ändern einer Methoden-, Eigenschaften-, Indexer- oder Ereignisdeklaration verwendet, und lässt zu, dass sie in einer abgeleiteten Klasse außer Kraft gesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="ee541-104">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="ee541-105">Diese Methode kann z.B. von jeder Klasse, die sie erbt, überschrieben werden:</span><span class="sxs-lookup"><span data-stu-id="ee541-105">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area()
{
    return x * y;
}
```

<span data-ttu-id="ee541-106">Die Implementierung eines virtuellen Members kann durch einen [overriding member](override.md) (überschreibenden Member) in einer abgeleiteten Klasse geändert werden.</span><span class="sxs-lookup"><span data-stu-id="ee541-106">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="ee541-107">Weitere Informationen zur Verwendung des `virtual`-Schlüsselworts finden Sie unter [Versionsverwaltung mit den Schlüsselwörtern „override“ und „new“](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) und [Wann müssen die Schlüsselwörter „override“ und „new“ verwendet werden?](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="ee541-107">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="ee541-108">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="ee541-108">Remarks</span></span>

<span data-ttu-id="ee541-109">Wenn eine virtuelle Methode aufgerufen wird, wird der Laufzeittyp des Objekts auf einen überschreibenden Member überprüft.</span><span class="sxs-lookup"><span data-stu-id="ee541-109">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="ee541-110">Der überschreibende Member in der abgeleitetsten Klasse (bei dem es sich um den ursprünglichen Member handeln könnte) wird aufgerufen, wenn keine abgeleitete Klasse den Member außer Kraft gesetzt hat.</span><span class="sxs-lookup"><span data-stu-id="ee541-110">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="ee541-111">Standardmäßig sind Methoden nicht virtuell.</span><span class="sxs-lookup"><span data-stu-id="ee541-111">By default, methods are non-virtual.</span></span> <span data-ttu-id="ee541-112">Sie können keine nicht virtuelle Methode überschreiben.</span><span class="sxs-lookup"><span data-stu-id="ee541-112">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="ee541-113">Sie können den Modifizierer `virtual` nicht mit den Modifizierern `static`, `abstract`, `private` oder `override` verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee541-113">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="ee541-114">Im folgenden Beispiel wird eine virtuelle Methode gezeigt:</span><span class="sxs-lookup"><span data-stu-id="ee541-114">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="ee541-115">Virtuelle Eigenschaften verhalten sich wie virtuelle Methoden – sie unterscheiden sich lediglich in der Deklarations- und Aufrufsyntax.</span><span class="sxs-lookup"><span data-stu-id="ee541-115">Virtual properties behave like virtual methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="ee541-116">Es ist ein unzulässig, den `virtual`-Modifizierer für eine statische Eigenschaft zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee541-116">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="ee541-117">Eine virtuelle vererbte Eigenschaft kann in einer abgeleiteten Klasse mithilfe der Eigenschaftendeklaration, die den Modifizierer `override` verwendet, außer Kraft gesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="ee541-117">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="ee541-118">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ee541-118">Example</span></span>

<span data-ttu-id="ee541-119">In diesem Beispiel enthält die Klasse `Shape` die zwei Koordinaten `x` und `y` und die virtuelle Methode `Area()`.</span><span class="sxs-lookup"><span data-stu-id="ee541-119">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="ee541-120">Andere Formklassen, z.B. `Circle`, `Cylinder` und `Sphere` erben die Klasse `Shape`. Die Oberfläche wird für jede Abbildung berechnet.</span><span class="sxs-lookup"><span data-stu-id="ee541-120">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="ee541-121">Jede abgeleitete Klasse verfügt über ihre eigene Überschreibungsimplementierung von `Area()`.</span><span class="sxs-lookup"><span data-stu-id="ee541-121">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="ee541-122">Beachten Sie, dass die geerbten Klassen `Circle`, `Sphere` und `Cylinder` alle Konstruktoren verwenden, die die Basisklasse initialisieren, wie in der folgenden Deklaration gezeigt.</span><span class="sxs-lookup"><span data-stu-id="ee541-122">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="ee541-123">Das folgende Programm berechnet und zeigt den entsprechenden Bereich für jede Abbildung durch Aufruf der entsprechenden Implementierung der `Area()`-Methode gemäß dem Objekt, das der Methode zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="ee541-123">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="ee541-124">C#-Sprachspezifikation</span><span class="sxs-lookup"><span data-stu-id="ee541-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ee541-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ee541-125">See also</span></span>

- [<span data-ttu-id="ee541-126">Polymorphismus</span><span class="sxs-lookup"><span data-stu-id="ee541-126">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="ee541-127">abstract</span><span class="sxs-lookup"><span data-stu-id="ee541-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="ee541-128">override</span><span class="sxs-lookup"><span data-stu-id="ee541-128">override</span></span>](override.md)
- [<span data-ttu-id="ee541-129">new (Modifizierer)</span><span class="sxs-lookup"><span data-stu-id="ee541-129">new (modifier)</span></span>](new-modifier.md)
