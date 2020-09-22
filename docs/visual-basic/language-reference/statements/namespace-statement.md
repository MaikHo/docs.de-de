---
title: Namespace-Anweisung
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: cef339a66458ee9657dc1706082c3c5328746dc6
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875212"
---
# <a name="namespace-statement"></a><span data-ttu-id="58689-102">Namespace-Anweisung</span><span class="sxs-lookup"><span data-stu-id="58689-102">Namespace Statement</span></span>

<span data-ttu-id="58689-103">Deklariert den Namen eines Namespace und bewirkt, dass der Quell Code, der der Deklaration folgt, in diesem Namespace kompiliert wird.</span><span class="sxs-lookup"><span data-stu-id="58689-103">Declares the name of a namespace and causes the source code that follows the declaration to be compiled within that namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58689-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="58689-104">Syntax</span></span>  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a><span data-ttu-id="58689-105">Bestandteile</span><span class="sxs-lookup"><span data-stu-id="58689-105">Parts</span></span>  

 <span data-ttu-id="58689-106">Global</span><span class="sxs-lookup"><span data-stu-id="58689-106">Global</span></span>  
 <span data-ttu-id="58689-107">Dies ist optional.</span><span class="sxs-lookup"><span data-stu-id="58689-107">Optional.</span></span> <span data-ttu-id="58689-108">Ermöglicht es Ihnen, einen Namespace aus dem Stamm Namespace des Projekts zu definieren.</span><span class="sxs-lookup"><span data-stu-id="58689-108">Allows you to define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="58689-109">Weitere Informationen finden Sie [unter Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="58689-109">See [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 `name`  
 <span data-ttu-id="58689-110">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="58689-110">Required.</span></span> <span data-ttu-id="58689-111">Ein eindeutiger Name, der den Namespace identifiziert.</span><span class="sxs-lookup"><span data-stu-id="58689-111">A unique name that identifies the namespace.</span></span> <span data-ttu-id="58689-112">Muss ein gültiger Visual Basic Bezeichner sein.</span><span class="sxs-lookup"><span data-stu-id="58689-112">Must be a valid Visual Basic identifier.</span></span> <span data-ttu-id="58689-113">Weitere Informationen finden Sie unter [deklarierte Element Namen](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="58689-113">For more information, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `componenttypes`  
 <span data-ttu-id="58689-114">Dies ist optional.</span><span class="sxs-lookup"><span data-stu-id="58689-114">Optional.</span></span> <span data-ttu-id="58689-115">Elemente, die den-Namespace bilden.</span><span class="sxs-lookup"><span data-stu-id="58689-115">Elements that make up the namespace.</span></span> <span data-ttu-id="58689-116">Dazu zählen Enumerationen, Strukturen, Schnittstellen, Klassen, Module, Delegaten und andere Namespaces, sind jedoch nicht darauf beschränkt.</span><span class="sxs-lookup"><span data-stu-id="58689-116">These include, but are not limited to, enumerations, structures, interfaces, classes, modules, delegates, and other namespaces.</span></span>  
  
 `End Namespace`  
 <span data-ttu-id="58689-117">Beendet einen- `Namespace` Block.</span><span class="sxs-lookup"><span data-stu-id="58689-117">Terminates a `Namespace` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58689-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="58689-118">Remarks</span></span>  

 <span data-ttu-id="58689-119">Namespaces werden als Organisationssystem verwendet.</span><span class="sxs-lookup"><span data-stu-id="58689-119">Namespaces are used as an organizational system.</span></span> <span data-ttu-id="58689-120">Sie bieten eine Möglichkeit zum klassifizieren und darstellen von Programmier Elementen, die für andere Programme und Anwendungen verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="58689-120">They provide a way to classify and present programming elements that are exposed to other programs and applications.</span></span> <span data-ttu-id="58689-121">Beachten Sie, dass es sich bei einem Namespace nicht um einen *Typ* handelt, der eine Klasse oder Struktur ist – Sie können kein Programmier Element deklarieren, um den Datentyp eines Namespace zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="58689-121">Note that a namespace is not a *type* in the sense that a class or structure is—you cannot declare a programming element to have the data type of a namespace.</span></span>  
  
 <span data-ttu-id="58689-122">Alle Programmier Elemente, die nach einer-Anweisung deklariert werden, `Namespace` gehören zu diesem Namespace.</span><span class="sxs-lookup"><span data-stu-id="58689-122">All programming elements declared after a `Namespace` statement belong to that namespace.</span></span> <span data-ttu-id="58689-123">Visual Basic werden Elemente weiterhin in den letzten deklarierten Namespace kompiliert, bis entweder eine- `End Namespace` Anweisung oder eine andere-Anweisung gefunden wird `Namespace` .</span><span class="sxs-lookup"><span data-stu-id="58689-123">Visual Basic continues to compile elements into the last declared namespace until it encounters either an `End Namespace` statement or another `Namespace` statement.</span></span>  
  
 <span data-ttu-id="58689-124">Wenn ein Namespace bereits definiert ist, können Sie auch außerhalb des Projekts Programmier Elemente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="58689-124">If a namespace is already defined, even outside your project, you can add programming elements to it.</span></span> <span data-ttu-id="58689-125">Zu diesem Zweck verwenden Sie eine- `Namespace` Anweisung, um Visual Basic anzuweisen, Elemente in diesen Namespace zu kompilieren.</span><span class="sxs-lookup"><span data-stu-id="58689-125">To do this, you use a `Namespace` statement to direct Visual Basic to compile elements into that namespace.</span></span>  
  
 <span data-ttu-id="58689-126">Eine-Anweisung kann `Namespace` nur auf Datei-oder Namespace Ebene verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="58689-126">You can use a `Namespace` statement only at the file or namespace level.</span></span> <span data-ttu-id="58689-127">Dies bedeutet, dass der *Deklarations Kontext* für einen Namespace eine Quelldatei oder ein anderer Namespace sein muss und weder eine Klasse noch eine Struktur, ein Modul, eine Schnittstelle oder eine Prozedur sein darf.</span><span class="sxs-lookup"><span data-stu-id="58689-127">This means the *declaration context* for a namespace must be a source file or another namespace, and cannot be a class, structure, module, interface, or procedure.</span></span> <span data-ttu-id="58689-128">Weitere Informationen finden Sie unter [Deklarationskontexte und Standardzugriffsebenen](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="58689-128">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="58689-129">Sie können einen Namespace in einem anderen deklarieren.</span><span class="sxs-lookup"><span data-stu-id="58689-129">You can declare one namespace within another.</span></span> <span data-ttu-id="58689-130">Es gibt keine strikte Beschränkung für die Schachtelungs Ebenen, die Sie deklarieren können. Bedenken Sie jedoch, dass beim Zugreifen auf die im innersten Namespace deklarierten Elemente eine Qualifizierungs Zeichenfolge verwendet werden muss, die alle Namespace Namen in der Schachtelungs Hierarchie enthält.</span><span class="sxs-lookup"><span data-stu-id="58689-130">There is no strict limit to the levels of nesting you can declare, but remember that when other code accesses the elements declared in the innermost namespace, it must use a qualification string that contains all the namespace names in the nesting hierarchy.</span></span>  
  
## <a name="access-level"></a><span data-ttu-id="58689-131">Zugriffsebene</span><span class="sxs-lookup"><span data-stu-id="58689-131">Access Level</span></span>  

 <span data-ttu-id="58689-132">Namespaces werden so behandelt, als ob Sie über eine `Public` Zugriffsebene verfügen.</span><span class="sxs-lookup"><span data-stu-id="58689-132">Namespaces are treated as if they have a `Public` access level.</span></span> <span data-ttu-id="58689-133">Auf einen Namespace kann von einem beliebigen Speicherort im gleichen Projekt aus zugegriffen werden, von anderen Projekten, die auf das Projekt verweisen, und aus einer Assembly, die aus dem Projekt erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="58689-133">A namespace can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project.</span></span>  
  
 <span data-ttu-id="58689-134">Programmier Elemente, die auf Namespace Ebene deklariert werden, d. h. in einem Namespace, aber nicht in einem anderen Element, können über- `Public` oder- `Friend` Zugriff verfügen</span><span class="sxs-lookup"><span data-stu-id="58689-134">Programming elements declared at namespace level, meaning in a namespace but not inside any other element, can have `Public` or `Friend` access.</span></span> <span data-ttu-id="58689-135">Wenn nicht angegeben, verwendet die Zugriffsebene eines solchen Elements `Friend` standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="58689-135">If unspecified, the access level of such an element uses `Friend` by default.</span></span> <span data-ttu-id="58689-136">Elemente, die Sie auf Namespace Ebene deklarieren können, sind Klassen, Strukturen, Module, Schnittstellen, Enumerationen und Delegaten.</span><span class="sxs-lookup"><span data-stu-id="58689-136">Elements you can declare at namespace level include classes, structures, modules, interfaces, enumerations, and delegates.</span></span> <span data-ttu-id="58689-137">Weitere Informationen finden Sie unter [Deklarationskontexte und Standardzugriffsebenen](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="58689-137">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="root-namespace"></a><span data-ttu-id="58689-138">Stamm Namespace</span><span class="sxs-lookup"><span data-stu-id="58689-138">Root Namespace</span></span>  

 <span data-ttu-id="58689-139">Alle Namespace Namen in Ihrem Projekt basieren auf einem *Root-Namespace*.</span><span class="sxs-lookup"><span data-stu-id="58689-139">All namespace names in your project are based on a *root namespace*.</span></span> <span data-ttu-id="58689-140">Visual Studio weist den Projektnamen als den Standard-Stammnamespace für den gesamten Code des Projekts zu.</span><span class="sxs-lookup"><span data-stu-id="58689-140">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="58689-141">Wenn Ihr Projekt beispielsweise den Namen `Payroll`hat, gehören die Programmierelemente zum Namespace `Payroll`.</span><span class="sxs-lookup"><span data-stu-id="58689-141">For example, if your project is named `Payroll`, its programming elements belong to namespace `Payroll`.</span></span> <span data-ttu-id="58689-142">Wenn Sie deklarieren `Namespace funding` , ist der vollständige Name dieses Namespace `Payroll.funding` .</span><span class="sxs-lookup"><span data-stu-id="58689-142">If you declare `Namespace funding`, the full name of that namespace is `Payroll.funding`.</span></span>  
  
 <span data-ttu-id="58689-143">Wenn Sie einen vorhandenen Namespace in einer-Anweisung angeben möchten `Namespace` , z. b. im Beispiel der generischen List-Klasse, können Sie den Root-Namespace auf einen NULL-Wert festlegen.</span><span class="sxs-lookup"><span data-stu-id="58689-143">If you want to specify an existing namespace in a `Namespace` statement, such as in the generic list class example, you can set your root namespace to a null value.</span></span> <span data-ttu-id="58689-144">Klicken Sie hierzu im Menü **Projekt** auf **Projekteigenschaften** , und löschen Sie dann den Eintrag **Root Namespace** , sodass das Feld leer ist.</span><span class="sxs-lookup"><span data-stu-id="58689-144">To do this, click **Project Properties** from the **Project** menu and then clear the **Root namespace** entry so that the box is empty.</span></span> <span data-ttu-id="58689-145">Wenn Sie dies nicht im Beispiel der generischen List-Klasse durchgeführt haben, würde der Visual Basic-Compiler `System.Collections.Generic` als neuen Namespace innerhalb von Project `Payroll` mit dem vollständigen Namen von übernehmen `Payroll.System.Collections.Generic` .</span><span class="sxs-lookup"><span data-stu-id="58689-145">If you did not do this in the generic list class example, the Visual Basic compiler would take `System.Collections.Generic` as a new namespace within project `Payroll`, with the full name of `Payroll.System.Collections.Generic`.</span></span>  
  
 <span data-ttu-id="58689-146">Alternativ können Sie das- `Global` Schlüsselwort verwenden, um auf Elemente von Namespaces zu verweisen, die außerhalb des Projekts definiert sind.</span><span class="sxs-lookup"><span data-stu-id="58689-146">Alternatively, you can use the `Global` keyword to refer to elements of namespaces defined outside your project.</span></span> <span data-ttu-id="58689-147">Auf diese Weise können Sie den Projektnamen als Stamm Namespace beibehalten.</span><span class="sxs-lookup"><span data-stu-id="58689-147">Doing so lets you retain your project name as the root namespace.</span></span> <span data-ttu-id="58689-148">Dadurch wird die Wahrscheinlichkeit verringert, dass ihre Programmier Elemente versehentlich zusammen mit den vorhandenen Namespaces zusammengeführt werden.</span><span class="sxs-lookup"><span data-stu-id="58689-148">This reduces the chance of unintentionally merging your programming elements together with those of existing namespaces.</span></span> <span data-ttu-id="58689-149">Weitere Informationen finden Sie im Abschnitt "globales Schlüsselwort in voll qualifizierten Namen" unter [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="58689-149">For more information, see the "Global Keyword in Fully Qualified Names" section in [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="58689-150">Das- `Global` Schlüsselwort kann auch in einer Namespace-Anweisung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="58689-150">The `Global` keyword can also be used in a Namespace statement.</span></span> <span data-ttu-id="58689-151">Dadurch können Sie einen Namespace aus dem Stammnamespace des Projekts definieren.</span><span class="sxs-lookup"><span data-stu-id="58689-151">This lets you define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="58689-152">Weitere Informationen finden Sie im Abschnitt "Global-Schlüsselwort in Namespace-Anweisungen" unter [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="58689-152">For more information, see the "Global Keyword in Namespace Statements" section in [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="58689-153">**Problem.**</span><span class="sxs-lookup"><span data-stu-id="58689-153">**Troubleshooting.**</span></span> <span data-ttu-id="58689-154">Der Stamm Namespace kann zu unerwarteten Verkettungen von Namespace Namen führen.</span><span class="sxs-lookup"><span data-stu-id="58689-154">The root namespace can lead to unexpected concatenations of namespace names.</span></span> <span data-ttu-id="58689-155">Wenn Sie Verweise auf Namespaces erstellen, die außerhalb des Projekts definiert sind, kann der Visual Basic Compiler Sie als schsted Namespaces im Stamm Namespace erstellen.</span><span class="sxs-lookup"><span data-stu-id="58689-155">If you make reference to namespaces defined outside your project, the Visual Basic compiler can construe them as nested namespaces in the root namespace.</span></span> <span data-ttu-id="58689-156">In diesem Fall erkennt der Compiler keine Typen, die bereits in den externen Namespaces definiert wurden.</span><span class="sxs-lookup"><span data-stu-id="58689-156">In such a case, the compiler does not recognize any types that have been already defined in the external namespaces.</span></span> <span data-ttu-id="58689-157">Um dies zu vermeiden, legen Sie entweder den Stamm Namespace auf einen NULL-Wert fest, wie unter "Root Namespace" beschrieben, oder verwenden Sie das `Global` Schlüsselwort, um auf Elemente externer Namespaces zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="58689-157">To avoid this, either set your root namespace to a null value as described in "Root Namespace," or use the `Global` keyword to access elements of external namespaces.</span></span>  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="58689-158">Attribute und modifiziererer</span><span class="sxs-lookup"><span data-stu-id="58689-158">Attributes and Modifiers</span></span>  

 <span data-ttu-id="58689-159">Attribute können nicht auf einen Namespace angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="58689-159">You cannot apply attributes to a namespace.</span></span> <span data-ttu-id="58689-160">Ein Attribut trägt Informationen zu den Metadaten der Assembly bei, was für Quell Klassifizierungen (z. b. Namespaces) nicht von Bedeutung ist.</span><span class="sxs-lookup"><span data-stu-id="58689-160">An attribute contributes information to the assembly's metadata, which is not meaningful for source classifiers such as namespaces.</span></span>  
  
 <span data-ttu-id="58689-161">Sie können keinen Zugriffs-oder Prozedur Modifizierer oder andere Modifizierer auf einen Namespace anwenden.</span><span class="sxs-lookup"><span data-stu-id="58689-161">You cannot apply any access or procedure modifiers, or any other modifiers, to a namespace.</span></span> <span data-ttu-id="58689-162">Da es sich nicht um einen-Typ handelt, sind diese Modifizierer nicht sinnvoll.</span><span class="sxs-lookup"><span data-stu-id="58689-162">Because it is not a type, these modifiers are not meaningful.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58689-163">Beispiel</span><span class="sxs-lookup"><span data-stu-id="58689-163">Example</span></span>  

 <span data-ttu-id="58689-164">Im folgenden Beispiel werden zwei Namespaces deklariert, eine in der anderen.</span><span class="sxs-lookup"><span data-stu-id="58689-164">The following example declares two namespaces, one nested in the other.</span></span>  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a><span data-ttu-id="58689-165">Beispiel</span><span class="sxs-lookup"><span data-stu-id="58689-165">Example</span></span>  

 <span data-ttu-id="58689-166">Im folgenden Beispiel werden mehrere schsted Namespaces in einer einzelnen Zeile deklariert, und Sie entspricht dem vorherigen Beispiel.</span><span class="sxs-lookup"><span data-stu-id="58689-166">The following example declares multiple nested namespaces on a single line, and it is equivalent to the previous example.</span></span>  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="58689-167">Beispiel</span><span class="sxs-lookup"><span data-stu-id="58689-167">Example</span></span>  

 <span data-ttu-id="58689-168">Im folgenden Beispiel wird auf die-Klasse zugegriffen, die in den vorherigen Beispielen definiert wurde.</span><span class="sxs-lookup"><span data-stu-id="58689-168">The following example accesses the class defined in the previous examples.</span></span>  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a><span data-ttu-id="58689-169">Beispiel</span><span class="sxs-lookup"><span data-stu-id="58689-169">Example</span></span>  

 <span data-ttu-id="58689-170">Im folgenden Beispiel wird das Gerüst einer neuen generischen List-Klasse definiert und dem- <xref:System.Collections.Generic?displayProperty=nameWithType> Namespace hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="58689-170">The following example defines the skeleton of a new generic list class and adds it to the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="58689-171">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="58689-171">See also</span></span>

- [<span data-ttu-id="58689-172">Imports-Anweisung (.NET-Namespace und Typ)</span><span class="sxs-lookup"><span data-stu-id="58689-172">Imports Statement (.NET Namespace and Type)</span></span>](imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="58689-173">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="58689-173">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="58689-174">Namespaces in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58689-174">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
