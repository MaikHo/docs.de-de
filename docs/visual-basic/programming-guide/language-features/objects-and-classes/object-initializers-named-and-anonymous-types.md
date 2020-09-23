---
title: 'Objektinitialisierer: benannte und anonyme Typen'
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 724407fed5bf90ed6e3e470cbabc9e42856cb99a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087478"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="807cc-102">Objektinitialisierer: Benannte und anonyme Typen (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="807cc-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>

<span data-ttu-id="807cc-103">Objektinitialisierer ermöglichen es Ihnen, mithilfe eines einzelnen Ausdrucks Eigenschaften für ein komplexes Objekt anzugeben.</span><span class="sxs-lookup"><span data-stu-id="807cc-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="807cc-104">Sie können verwendet werden, um Instanzen benannter Typen und anonymer Typen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="807cc-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="807cc-105">Deklarationen</span><span class="sxs-lookup"><span data-stu-id="807cc-105">Declarations</span></span>  

 <span data-ttu-id="807cc-106">Deklarationen von Instanzen von benannten und anonymen Typen können nahezu identisch aussehen, aber ihre Auswirkungen sind nicht identisch.</span><span class="sxs-lookup"><span data-stu-id="807cc-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="807cc-107">Jede Kategorie verfügt über eigene Möglichkeiten und Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="807cc-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="807cc-108">Das folgende Beispiel zeigt eine bequeme Methode zum Deklarieren und Initialisieren einer Instanz einer benannten Klasse, `Customer` , mithilfe einer Objektinitialisiererliste.</span><span class="sxs-lookup"><span data-stu-id="807cc-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="807cc-109">Beachten Sie, dass der Name der Klasse nach dem-Schlüsselwort angegeben wird `New` .</span><span class="sxs-lookup"><span data-stu-id="807cc-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 <span data-ttu-id="807cc-110">Ein anonymer Typ hat keinen verwendbaren Namen.</span><span class="sxs-lookup"><span data-stu-id="807cc-110">An anonymous type has no usable name.</span></span> <span data-ttu-id="807cc-111">Daher kann eine Instanziierung eines anonymen Typs keinen Klassennamen enthalten.</span><span class="sxs-lookup"><span data-stu-id="807cc-111">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 <span data-ttu-id="807cc-112">Die Anforderungen und Ergebnisse der beiden Deklarationen sind nicht identisch.</span><span class="sxs-lookup"><span data-stu-id="807cc-112">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="807cc-113">Für `namedCust` muss eine `Customer` Klasse, die über eine- `Name` Eigenschaft verfügt, bereits vorhanden sein, und die-Deklaration erstellt eine Instanz dieser Klasse.</span><span class="sxs-lookup"><span data-stu-id="807cc-113">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="807cc-114">Für `anonymousCust` definiert der Compiler eine neue Klasse, die über eine Eigenschaft, eine Zeichenfolge `Name` mit dem Namen und eine neue Instanz dieser Klasse verfügt.</span><span class="sxs-lookup"><span data-stu-id="807cc-114">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="807cc-115">Benannte Typen</span><span class="sxs-lookup"><span data-stu-id="807cc-115">Named Types</span></span>  

 <span data-ttu-id="807cc-116">Objektinitialisierer bieten eine einfache Möglichkeit, den Konstruktor eines Typs aufzurufen und dann die Werte einiger oder aller Eigenschaften in einer einzelnen Anweisung festzulegen.</span><span class="sxs-lookup"><span data-stu-id="807cc-116">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="807cc-117">Der Compiler ruft den entsprechenden Konstruktor für die-Anweisung auf: den Parameter losen Konstruktor, wenn keine Argumente dargestellt werden, oder einen parametrisierten Konstruktor, wenn mindestens ein Argument gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="807cc-117">The compiler invokes the appropriate constructor for the statement: the parameterless constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="807cc-118">Anschließend werden die angegebenen Eigenschaften in der Reihenfolge initialisiert, in der Sie in der Initialisiererliste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="807cc-118">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="807cc-119">Jede Initialisierung in der Initialisiererliste besteht aus der Zuweisung eines Anfangs Werts zu einem Member der Klasse.</span><span class="sxs-lookup"><span data-stu-id="807cc-119">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="807cc-120">Die Namen und Datentypen der Elemente werden bestimmt, wenn die Klasse definiert ist.</span><span class="sxs-lookup"><span data-stu-id="807cc-120">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="807cc-121">In den folgenden Beispielen muss die `Customer` -Klasse vorhanden sein, und Sie müssen Member mit dem Namen und enthalten, `Name` `City` die Zeichen folgen Werte akzeptieren können.</span><span class="sxs-lookup"><span data-stu-id="807cc-121">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 <span data-ttu-id="807cc-122">Sie können das gleiche Ergebnis auch mithilfe des folgenden Codes abrufen:</span><span class="sxs-lookup"><span data-stu-id="807cc-122">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 <span data-ttu-id="807cc-123">Jede dieser Deklarationen entspricht dem folgenden Beispiel, das ein `Customer` -Objekt mit dem Parameter losen Konstruktor erstellt und dann `Name` `City` mithilfe einer-Anweisung die Anfangswerte für die-Eigenschaft und die-Eigenschaft angibt `With` .</span><span class="sxs-lookup"><span data-stu-id="807cc-123">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the parameterless constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 <span data-ttu-id="807cc-124">Wenn die `Customer` Klasse einen parametrisierten Konstruktor enthält, der es Ihnen ermöglicht, beispielsweise einen Wert für zu senden `Name` , können Sie auch ein-Objekt wie folgt deklarieren und initialisieren `Customer` :</span><span class="sxs-lookup"><span data-stu-id="807cc-124">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 <span data-ttu-id="807cc-125">Sie müssen nicht alle Eigenschaften initialisieren, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="807cc-125">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 <span data-ttu-id="807cc-126">Die Initialisierungs Liste darf jedoch nicht leer sein.</span><span class="sxs-lookup"><span data-stu-id="807cc-126">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="807cc-127">Nicht initialisierte Eigenschaften behalten ihre Standardwerte bei.</span><span class="sxs-lookup"><span data-stu-id="807cc-127">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="807cc-128">Typrückschluss mit benannten Typen</span><span class="sxs-lookup"><span data-stu-id="807cc-128">Type Inference with Named Types</span></span>  

 <span data-ttu-id="807cc-129">Sie können den Code für die Deklaration von kürzen, `cust1` indem Sie Objektinitialisierer und den lokalen Typrückschluss kombinieren.</span><span class="sxs-lookup"><span data-stu-id="807cc-129">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="807cc-130">Auf diese Weise können Sie die- `As` Klausel in der Variablen Deklaration weglassen.</span><span class="sxs-lookup"><span data-stu-id="807cc-130">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="807cc-131">Der Datentyp der Variablen wird vom Objekttyp abgeleitet, der von der Zuweisung erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="807cc-131">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="807cc-132">Im folgenden Beispiel ist der Typ von `cust6` `Customer` .</span><span class="sxs-lookup"><span data-stu-id="807cc-132">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="807cc-133">Hinweise zu benannten Typen</span><span class="sxs-lookup"><span data-stu-id="807cc-133">Remarks About Named Types</span></span>  
  
- <span data-ttu-id="807cc-134">Ein Klassenmember kann nicht mehr als einmal in der Objektinitialisiererliste initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="807cc-134">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="807cc-135">Die Deklaration von `cust7` verursacht einen Fehler.</span><span class="sxs-lookup"><span data-stu-id="807cc-135">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- <span data-ttu-id="807cc-136">Ein Member kann verwendet werden, um sich selbst oder ein anderes Feld zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="807cc-136">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="807cc-137">Wenn auf einen Member zugegriffen wird, bevor er initialisiert wurde, wie in der folgenden Deklaration für `cust8` , wird der Standardwert verwendet.</span><span class="sxs-lookup"><span data-stu-id="807cc-137">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="807cc-138">Beachten Sie, dass beim Verarbeiten einer Deklaration, die einen Objektinitialisierer verwendet, das erste passiert, dass der entsprechende Konstruktor aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="807cc-138">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="807cc-139">Danach werden die einzelnen Felder in der Initialisiererliste initialisiert.</span><span class="sxs-lookup"><span data-stu-id="807cc-139">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="807cc-140">In den folgenden Beispielen wird der Standardwert für `Name` zugewiesen `cust8` , und es wird ein initialisierter Wert in zugewiesen `cust9` .</span><span class="sxs-lookup"><span data-stu-id="807cc-140">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     <span data-ttu-id="807cc-141">Im folgenden Beispiel wird der parametrisierte Konstruktor von `cust3` und verwendet `cust4` , um und zu deklarieren und zu initialisieren `cust10` `cust11` .</span><span class="sxs-lookup"><span data-stu-id="807cc-141">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- <span data-ttu-id="807cc-142">Objektinitialisierer können eingebettet werden.</span><span class="sxs-lookup"><span data-stu-id="807cc-142">Object initializers can be nested.</span></span> <span data-ttu-id="807cc-143">Im folgenden Beispiel `AddressClass` ist eine Klasse mit zwei Eigenschaften, `City` und `State` , und die- `Customer` Klasse verfügt über eine- `Address` Eigenschaft, die eine Instanz von ist `AddressClass` .</span><span class="sxs-lookup"><span data-stu-id="807cc-143">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- <span data-ttu-id="807cc-144">Die Initialisierungs Liste darf nicht leer sein.</span><span class="sxs-lookup"><span data-stu-id="807cc-144">The initialization list cannot be empty.</span></span>  
  
- <span data-ttu-id="807cc-145">Die initialisierte Instanz kann nicht vom Typ "Object" sein.</span><span class="sxs-lookup"><span data-stu-id="807cc-145">The instance being initialized cannot be of type Object.</span></span>  
  
- <span data-ttu-id="807cc-146">Klassenmember, die initialisiert werden, können keine freigegebenen Member, keine schreibgeschützten Member, Konstanten oder Methodenaufrufe sein.</span><span class="sxs-lookup"><span data-stu-id="807cc-146">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
- <span data-ttu-id="807cc-147">Klassenmember, die initialisiert werden, können nicht indiziert oder qualifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="807cc-147">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="807cc-148">In den folgenden Beispielen werden Compilerfehler hervorrufen:</span><span class="sxs-lookup"><span data-stu-id="807cc-148">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="807cc-149">Anonyme Typen</span><span class="sxs-lookup"><span data-stu-id="807cc-149">Anonymous Types</span></span>  

 <span data-ttu-id="807cc-150">Anonyme Typen verwenden Objektinitialisierer, um Instanzen von neuen Typen zu erstellen, die Sie nicht explizit definieren und benennen.</span><span class="sxs-lookup"><span data-stu-id="807cc-150">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="807cc-151">Stattdessen generiert der Compiler einen Typ entsprechend den Eigenschaften, die Sie in der Objektinitialisiererliste festlegen.</span><span class="sxs-lookup"><span data-stu-id="807cc-151">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="807cc-152">Da der Name des Typs nicht angegeben wird, wird er als *anonymer Typ*bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="807cc-152">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="807cc-153">Vergleichen Sie beispielsweise die folgende Deklaration mit der vorherigen Deklaration für `cust6` .</span><span class="sxs-lookup"><span data-stu-id="807cc-153">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 <span data-ttu-id="807cc-154">Der einzige Unterschied besteht darin, dass nach `New` für den Datentyp kein Name angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="807cc-154">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="807cc-155">Was passiert jedoch ganz anders.</span><span class="sxs-lookup"><span data-stu-id="807cc-155">However, what happens is quite different.</span></span> <span data-ttu-id="807cc-156">Der Compiler definiert einen neuen anonymen Typ, der über zwei Eigenschaften verfügt: `Name` und `City` , und erstellt eine Instanz davon mit den angegebenen Werten.</span><span class="sxs-lookup"><span data-stu-id="807cc-156">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="807cc-157">Der Typrückschluss bestimmt die Typen von `Name` und im Beispiel als Zeichen folgen `City` .</span><span class="sxs-lookup"><span data-stu-id="807cc-157">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="807cc-158">Der Name des anonymen Typs wird vom Compiler generiert und kann von der Kompilierung bis zur Kompilierung abweichen.</span><span class="sxs-lookup"><span data-stu-id="807cc-158">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="807cc-159">Der Code darf nicht den Namen eines anonymen Typs verwenden oder sich darauf verlassen.</span><span class="sxs-lookup"><span data-stu-id="807cc-159">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="807cc-160">Da der Name des Typs nicht verfügbar ist, können Sie keine-Klausel verwenden, `As` um zu deklarieren `cust13` .</span><span class="sxs-lookup"><span data-stu-id="807cc-160">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="807cc-161">Der Typ muss abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="807cc-161">Its type must be inferred.</span></span> <span data-ttu-id="807cc-162">Ohne die späte Bindung zu verwenden, schränkt dies die Verwendung anonymer Typen auf lokale Variablen ein.</span><span class="sxs-lookup"><span data-stu-id="807cc-162">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="807cc-163">Anonyme Typen bieten wichtige Unterstützung für LINQ-Abfragen.</span><span class="sxs-lookup"><span data-stu-id="807cc-163">Anonymous types provide critical support for LINQ queries.</span></span> <span data-ttu-id="807cc-164">Weitere Informationen zur Verwendung anonymer Typen in Abfragen finden Sie unter [Anonyme Typen](anonymous-types.md) und [Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md).</span><span class="sxs-lookup"><span data-stu-id="807cc-164">For more information about the use of anonymous types in queries, see [Anonymous Types](anonymous-types.md) and [Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="807cc-165">Hinweise zu anonymen Typen</span><span class="sxs-lookup"><span data-stu-id="807cc-165">Remarks About Anonymous Types</span></span>  
  
- <span data-ttu-id="807cc-166">In der Regel sind alle oder die meisten Eigenschaften in einer Deklaration eines anonymen Typs Schlüsseleigenschaften, die durch Eingabe des Schlüssel Worts `Key` vor dem Eigenschaftsnamen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="807cc-166">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     <span data-ttu-id="807cc-167">Weitere Informationen zu Schlüsseleigenschaften finden Sie unter [Key](../../../language-reference/modifiers/key.md).</span><span class="sxs-lookup"><span data-stu-id="807cc-167">For more information about key properties, see [Key](../../../language-reference/modifiers/key.md).</span></span>  
  
- <span data-ttu-id="807cc-168">Wie benannte Typen müssen die Initialisiererlisten für anonyme Typdefinitionen mindestens eine Eigenschaft deklarieren.</span><span class="sxs-lookup"><span data-stu-id="807cc-168">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- <span data-ttu-id="807cc-169">Wenn eine Instanz eines anonymen Typs deklariert ist, generiert der Compiler eine entsprechende anonyme Typdefinition.</span><span class="sxs-lookup"><span data-stu-id="807cc-169">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="807cc-170">Die Namen und Datentypen der Eigenschaften werden aus der Instanzdeklaration entnommen und vom Compiler in der Definition eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="807cc-170">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="807cc-171">Die Eigenschaften werden nicht im Voraus benannt und definiert, wie dies bei einem benannten Typ der Fall wäre.</span><span class="sxs-lookup"><span data-stu-id="807cc-171">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="807cc-172">Ihre Typen werden abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="807cc-172">Their types are inferred.</span></span> <span data-ttu-id="807cc-173">Die Datentypen der Eigenschaften können nicht mithilfe einer-Klausel angegeben werden `As` .</span><span class="sxs-lookup"><span data-stu-id="807cc-173">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
- <span data-ttu-id="807cc-174">Anonyme Typen können auch auf verschiedene Weise die Namen und Werte ihrer Eigenschaften festlegen.</span><span class="sxs-lookup"><span data-stu-id="807cc-174">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="807cc-175">Beispielsweise kann eine Eigenschaft eines anonymen Typs sowohl den Namen als auch den Wert einer Variablen oder den Namen und den Wert einer Eigenschaft eines anderen Objekts annehmen.</span><span class="sxs-lookup"><span data-stu-id="807cc-175">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     <span data-ttu-id="807cc-176">Weitere Informationen zu den Optionen zum Definieren von Eigenschaften in anonymen Typen finden Sie unter Gewusst [wie: Ableiten von Eigenschaften Namen und Typen in Deklarationen anonymer](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)Typen.</span><span class="sxs-lookup"><span data-stu-id="807cc-176">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="807cc-177">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="807cc-177">See also</span></span>

- [<span data-ttu-id="807cc-178">Lokaler Typrückschluss</span><span class="sxs-lookup"><span data-stu-id="807cc-178">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="807cc-179">Anonyme Typen</span><span class="sxs-lookup"><span data-stu-id="807cc-179">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="807cc-180">Einführung in LINQ in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="807cc-180">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="807cc-181">Vorgehensweise: Ableiten von Eigenschaftennamen und Typen in Deklarationen von anonymen Typen</span><span class="sxs-lookup"><span data-stu-id="807cc-181">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="807cc-182">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="807cc-182">Key</span></span>](../../../language-reference/modifiers/key.md)
- [<span data-ttu-id="807cc-183">Vorgehensweise: Deklarieren eines Objekts mithilfe eines Objektinitialisierers</span><span class="sxs-lookup"><span data-stu-id="807cc-183">How to: Declare an Object by Using an Object Initializer</span></span>](how-to-declare-an-object-by-using-an-object-initializer.md)
