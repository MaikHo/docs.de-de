---
title: Option Compare-Anweisung
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: 396770a2fc6996475d408cf8023a4eafdf6d3011
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869654"
---
# <a name="option-compare-statement"></a><span data-ttu-id="1606b-102">Option Compare-Anweisung</span><span class="sxs-lookup"><span data-stu-id="1606b-102">Option Compare Statement</span></span>

<span data-ttu-id="1606b-103">Deklariert die Standardvergleichsmethode, die beim Vergleichen von Zeichenfolgendaten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1606b-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1606b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1606b-104">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="1606b-105">Bestandteile</span><span class="sxs-lookup"><span data-stu-id="1606b-105">Parts</span></span>  
  
|<span data-ttu-id="1606b-106">Begriff</span><span class="sxs-lookup"><span data-stu-id="1606b-106">Term</span></span>|<span data-ttu-id="1606b-107">Definition</span><span class="sxs-lookup"><span data-stu-id="1606b-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="1606b-108">Dies ist optional.</span><span class="sxs-lookup"><span data-stu-id="1606b-108">Optional.</span></span> <span data-ttu-id="1606b-109">Resultiert in Zeichenfolgenvergleichen basierend auf einer Sortierreihenfolge, die sich von den internen binären Darstellungen der Zeichen ableitet.</span><span class="sxs-lookup"><span data-stu-id="1606b-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="1606b-110">Diese Art von Vergleich ist besonders hilfreich, da die Zeichenfolgen Zeichen enthalten können, die nicht als Text interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="1606b-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="1606b-111">In diesem Fall sollten Sie Vergleiche nicht alphabetischen Äquivalenzen, z. B. Groß-/Kleinschreibung vorziehen.</span><span class="sxs-lookup"><span data-stu-id="1606b-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="1606b-112">Dies ist optional.</span><span class="sxs-lookup"><span data-stu-id="1606b-112">Optional.</span></span> <span data-ttu-id="1606b-113">Führt zu einem Zeichenfolgenvergleich basierend auf einer schreibungsunabhängigen Textsortierreihenfolge, die durch das Gebietsschema des Systems bestimmt wird.</span><span class="sxs-lookup"><span data-stu-id="1606b-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="1606b-114">Diese Art von Vergleich ist nützlich, wenn die Zeichenfolgen nur Textzeichen enthalten und Sie nur anhand alphabetischer Äquivalenzen z. B. Groß-/Kleinschreibung oder eng verwandter Buchstaben vergleichen möchten.</span><span class="sxs-lookup"><span data-stu-id="1606b-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="1606b-115">Sie könnten zum Beispiel `A` und `a` als gleich ansehen und `Ä` und `ä`, die vor `B` und `b` kommen.</span><span class="sxs-lookup"><span data-stu-id="1606b-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1606b-116">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="1606b-116">Remarks</span></span>  

 <span data-ttu-id="1606b-117">Wenn sie verwendet wird, muss die `Option Compare`-Anweisung in einer Datei vor allen anderen Quellcodeanweisungen angeordnet sein.</span><span class="sxs-lookup"><span data-stu-id="1606b-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="1606b-118">Die `Option Compare`-Anweisung gibt die Zeichenfolgenvergleichsmethode vor (`Binary` oder `Text`).</span><span class="sxs-lookup"><span data-stu-id="1606b-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="1606b-119">Die Standardmethode zum Textvergleich ist `Binary`.</span><span class="sxs-lookup"><span data-stu-id="1606b-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="1606b-120">Ein `Binary`-Vergleich vergleicht den numerischen Unicode-Wert jedes Zeichens in jeder Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="1606b-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="1606b-121">Ein `Text`-Vergleich vergleicht alle Unicode-Zeichen anhand der lexikalische Bedeutung in der aktuellen Kultur.</span><span class="sxs-lookup"><span data-stu-id="1606b-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="1606b-122">In Microsoft Windows wird die Sortierreihenfolge durch die Codepage festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1606b-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="1606b-123">Weitere Informationen finden Sie unter [Codepages](/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="1606b-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="1606b-124">Im folgenden Beispiel werden Zeichen der Codepage für Westeuropäisch (ANSI 1252) mit `Option Compare Binary` sortiert, wodurch eine typische binäre Sortierreihenfolge erzeugt wird.</span><span class="sxs-lookup"><span data-stu-id="1606b-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="1606b-125">Wenn dieselben Zeichen in derselben Codepage `Option Compare Text` mit sortiert werden, wird die folgende Sortierreihenfolge erzeugt.</span><span class="sxs-lookup"><span data-stu-id="1606b-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="1606b-126">Wenn eine Option Compare-Anweisung nicht vorhanden ist</span><span class="sxs-lookup"><span data-stu-id="1606b-126">When an Option Compare Statement Is Not Present</span></span>  

 <span data-ttu-id="1606b-127">Wenn der Quellcode keine- `Option Compare` Anweisung enthält, wird die **Option Compare** -Einstellung auf der [Seite "kompilieren", Projekt-Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) verwendet.</span><span class="sxs-lookup"><span data-stu-id="1606b-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="1606b-128">Wenn Sie den Befehlszeilen Compiler verwenden, wird die von der [-optioncompare-](../../reference/command-line-compiler/optioncompare.md) Compileroption angegebene Einstellung verwendet.</span><span class="sxs-lookup"><span data-stu-id="1606b-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="1606b-129">Festelegen der Option Compare in der IDE</span><span class="sxs-lookup"><span data-stu-id="1606b-129">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="1606b-130">Wählen Sie in **Projektmappen-Explorer**ein Projekt aus.</span><span class="sxs-lookup"><span data-stu-id="1606b-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="1606b-131">Klicken Sie im Menü **Projekt** auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="1606b-131">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="1606b-132">Klicken Sie auf die Registerkarte **Kompilieren**.</span><span class="sxs-lookup"><span data-stu-id="1606b-132">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="1606b-133">Legen Sie den Wert im Feld **options Vergleich** fest.</span><span class="sxs-lookup"><span data-stu-id="1606b-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="1606b-134">Wenn Sie ein Projekt erstellen, wird die **Option Compare** -Einstellung auf der Registerkarte **Kompilieren** auf die **Option Compare** -Einstellung im Dialogfeld **Optionen** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1606b-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="1606b-135">Klicken Sie **im Menü Extras** auf **Optionen**, um diese Einstellung zu ändern.</span><span class="sxs-lookup"><span data-stu-id="1606b-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="1606b-136">Erweitern Sie im Dialogfeld **Optionen\*\*\*\*Projekte und Lösungen**, und klicken Sie dann auf **VB Defaults**.</span><span class="sxs-lookup"><span data-stu-id="1606b-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="1606b-137">Die ursprüngliche Standardeinstellung in **VB-Standardeinstellungen** ist **Binär**.</span><span class="sxs-lookup"><span data-stu-id="1606b-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="1606b-138">Festlegen der Option Compare in der Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="1606b-138">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="1606b-139">Schließen Sie die [-optioncompare-](../../reference/command-line-compiler/optioncompare.md) Compileroption in den **vbc** -Befehl ein.</span><span class="sxs-lookup"><span data-stu-id="1606b-139">Include the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1606b-140">Beispiel</span><span class="sxs-lookup"><span data-stu-id="1606b-140">Example</span></span>  

 <span data-ttu-id="1606b-141">Das folgenden Beispiel verwendet die `Option Compare`-Anweisung, um den binären Vergleich als die Standardzeichenfolgenvergleichsmethode festzulegen.</span><span class="sxs-lookup"><span data-stu-id="1606b-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="1606b-142">Um diesen Code zu verwenden, heben Sie die Auskommentierung der `Option Compare Binary`-Anweisung auf und positionieren Sie sie am Anfang der Quelldatei.</span><span class="sxs-lookup"><span data-stu-id="1606b-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="1606b-143">Beispiel</span><span class="sxs-lookup"><span data-stu-id="1606b-143">Example</span></span>  

 <span data-ttu-id="1606b-144">Im folgenden Beispiel wird die `Option Compare`-Anweisung verwendet, um die Textsortierreihenfolge als die Standardzeichenfolgenvergleichsmethode festzulegen.</span><span class="sxs-lookup"><span data-stu-id="1606b-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="1606b-145">Um diesen Code zu verwenden, heben Sie die Auskommentierung der `Option Compare Text`-Anweisung auf und positionieren Sie sie am Anfang der Quelldatei.</span><span class="sxs-lookup"><span data-stu-id="1606b-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="1606b-146">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1606b-146">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="1606b-147">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="1606b-147">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="1606b-148">Comparison Operators (Vergleichsoperatoren)</span><span class="sxs-lookup"><span data-stu-id="1606b-148">Comparison Operators</span></span>](../operators/comparison-operators.md)
- [<span data-ttu-id="1606b-149">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1606b-149">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="1606b-150">Like-Operator</span><span class="sxs-lookup"><span data-stu-id="1606b-150">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="1606b-151">Zeichenfolgenfunktionen</span><span class="sxs-lookup"><span data-stu-id="1606b-151">String Functions</span></span>](../functions/string-functions.md)
- [<span data-ttu-id="1606b-152">Option Explicit-Anweisung</span><span class="sxs-lookup"><span data-stu-id="1606b-152">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="1606b-153">Option Strict-Anweisung</span><span class="sxs-lookup"><span data-stu-id="1606b-153">Option Strict Statement</span></span>](option-strict-statement.md)
