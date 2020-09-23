---
title: Struktur von Visual Basic-Programmen
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 90bc1fd62a05f670424e1fac368376401d1030c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097773"
---
# <a name="structure-of-a-visual-basic-program"></a><span data-ttu-id="2fab4-102">Struktur von Visual Basic-Programmen</span><span class="sxs-lookup"><span data-stu-id="2fab4-102">Structure of a Visual Basic Program</span></span>

<span data-ttu-id="2fab4-103">Ein Visual Basic Programm ist aus Standard Bausteinen aufgebaut.</span><span class="sxs-lookup"><span data-stu-id="2fab4-103">A Visual Basic program is built up from standard building blocks.</span></span> <span data-ttu-id="2fab4-104">Eine Projekt *Mappe besteht aus einem oder* mehreren Projekten.</span><span class="sxs-lookup"><span data-stu-id="2fab4-104">A *solution* comprises one or more projects.</span></span> <span data-ttu-id="2fab4-105">Ein *Projekt* kann wiederum eine oder mehrere Assemblys enthalten.</span><span class="sxs-lookup"><span data-stu-id="2fab4-105">A *project* in turn can contain one or more assemblies.</span></span> <span data-ttu-id="2fab4-106">Jede *Assembly* wird aus einer oder mehreren Quelldateien kompiliert.</span><span class="sxs-lookup"><span data-stu-id="2fab4-106">Each *assembly* is compiled from one or more source files.</span></span> <span data-ttu-id="2fab4-107">Eine *Quelldatei* stellt die Definition und Implementierung von Klassen, Strukturen, Modulen und Schnittstellen bereit, die letztendlich den gesamten Code enthalten.</span><span class="sxs-lookup"><span data-stu-id="2fab4-107">A *source file* provides the definition and implementation of classes, structures, modules, and interfaces, which ultimately contain all your code.</span></span>  
  
 <span data-ttu-id="2fab4-108">Weitere Informationen zu diesen Bausteinen eines Visual Basic Programms finden Sie Unterprojekt Mappen [und Projekte](/visualstudio/ide/solutions-and-projects-in-visual-studio) und Assemblys [in .net](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="2fab4-108">For more information about these building blocks of a Visual Basic program, see [Solutions and Projects](/visualstudio/ide/solutions-and-projects-in-visual-studio) and [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
## <a name="file-level-programming-elements"></a><span data-ttu-id="2fab4-109">Programmier Elemente auf Dateiebene</span><span class="sxs-lookup"><span data-stu-id="2fab4-109">File-Level Programming Elements</span></span>  

 <span data-ttu-id="2fab4-110">Wenn Sie ein Projekt oder eine Datei starten und den Code-Editor öffnen, sehen Sie, dass Code bereits vorhanden und in der richtigen Reihenfolge vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2fab4-110">When you start a project or file and open the code editor, you see some code already in place and in the correct order.</span></span> <span data-ttu-id="2fab4-111">Jeder Code, den Sie schreiben, sollte der folgenden Reihenfolge folgen:</span><span class="sxs-lookup"><span data-stu-id="2fab4-111">Any code that you write should follow the following sequence:</span></span>  
  
1. <span data-ttu-id="2fab4-112">`Option` Äußerungen</span><span class="sxs-lookup"><span data-stu-id="2fab4-112">`Option` statements</span></span>  
  
2. <span data-ttu-id="2fab4-113">`Imports` Äußerungen</span><span class="sxs-lookup"><span data-stu-id="2fab4-113">`Imports` statements</span></span>  
  
3. <span data-ttu-id="2fab4-114">`Namespace` -Anweisungen und Elemente auf Namespace Ebene</span><span class="sxs-lookup"><span data-stu-id="2fab4-114">`Namespace` statements and namespace-level elements</span></span>  
  
 <span data-ttu-id="2fab4-115">Wenn Sie-Anweisungen in einer anderen Reihenfolge eingeben, können Kompilierungsfehler auftreten.</span><span class="sxs-lookup"><span data-stu-id="2fab4-115">If you enter statements in a different order, compilation errors can result.</span></span>  
  
 <span data-ttu-id="2fab4-116">Ein Programm kann auch bedingte Kompilierungs Anweisungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="2fab4-116">A program can also contain conditional compilation statements.</span></span> <span data-ttu-id="2fab4-117">Sie können diese in der Quelldatei mit den Anweisungen der vorangehenden Sequenz interagieren.</span><span class="sxs-lookup"><span data-stu-id="2fab4-117">You can intersperse these in the source file among the statements of the preceding sequence.</span></span>  
  
### <a name="option-statements"></a><span data-ttu-id="2fab4-118">Options Anweisungen</span><span class="sxs-lookup"><span data-stu-id="2fab4-118">Option Statements</span></span>  

 <span data-ttu-id="2fab4-119">`Option` -Anweisungen richten Grundregeln für nachfolgenden Code ein, um Syntax-und Logikfehler zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="2fab4-119">`Option` statements establish ground rules for subsequent code, helping prevent syntax and logic errors.</span></span> <span data-ttu-id="2fab4-120">Mit der [Option explizite-Anweisung](../../language-reference/statements/option-explicit-statement.md) wird sichergestellt, dass alle Variablen deklariert und richtig geschrieben werden, wodurch die Debugzeit verringert wird.</span><span class="sxs-lookup"><span data-stu-id="2fab4-120">The [Option Explicit Statement](../../language-reference/statements/option-explicit-statement.md) ensures that all variables are declared and spelled correctly, which reduces debugging time.</span></span> <span data-ttu-id="2fab4-121">Mit der [Option Strict-Anweisung](../../language-reference/statements/option-strict-statement.md) können Sie logische Fehler und Datenverluste minimieren, die auftreten können, wenn Sie zwischen Variablen verschiedener Datentypen arbeiten.</span><span class="sxs-lookup"><span data-stu-id="2fab4-121">The [Option Strict Statement](../../language-reference/statements/option-strict-statement.md) helps to minimize logic errors and data loss that can occur when you work between variables of different data types.</span></span> <span data-ttu-id="2fab4-122">Die [Option Compare-Anweisung](../../language-reference/statements/option-compare-statement.md) gibt an, wie Zeichen folgen miteinander verglichen werden, basierend auf Ihren- `Binary` oder- `Text` Werten.</span><span class="sxs-lookup"><span data-stu-id="2fab4-122">The [Option Compare Statement](../../language-reference/statements/option-compare-statement.md) specifies the way strings are compared to each other, based on either their `Binary` or `Text` values.</span></span>  
  
### <a name="imports-statements"></a><span data-ttu-id="2fab4-123">Imports-Anweisungen</span><span class="sxs-lookup"><span data-stu-id="2fab4-123">Imports Statements</span></span>  

 <span data-ttu-id="2fab4-124">Sie können eine [Imports-Anweisung (.NET-Namespace und-Typ)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) einschließen, um Namen zu importieren, die außerhalb des Projekts definiert sind.</span><span class="sxs-lookup"><span data-stu-id="2fab4-124">You can include an [Imports Statement (.NET Namespace and Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) to import names defined outside your project.</span></span> <span data-ttu-id="2fab4-125">Mit einer- `Imports` Anweisung kann Ihr Code auf Klassen und andere Typen verweisen, die im importierten Namespace definiert sind, ohne Sie qualifizieren zu müssen.</span><span class="sxs-lookup"><span data-stu-id="2fab4-125">An `Imports` statement allows your code to refer to classes and other types defined within the imported namespace, without having to qualify them.</span></span> <span data-ttu-id="2fab4-126">Sie können beliebig viele- `Imports` Anweisungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="2fab4-126">You can use as many `Imports` statements as appropriate.</span></span> <span data-ttu-id="2fab4-127">Weitere Informationen finden Sie unter [Verweise und die Imports-Anweisung](references-and-the-imports-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2fab4-127">For more information, see [References and the Imports Statement](references-and-the-imports-statement.md).</span></span>  
  
### <a name="namespace-statements"></a><span data-ttu-id="2fab4-128">Namespace-Anweisungen</span><span class="sxs-lookup"><span data-stu-id="2fab4-128">Namespace Statements</span></span>  

 <span data-ttu-id="2fab4-129">Namespaces helfen Ihnen beim organisieren und klassifizieren ihrer Programmier Elemente, um die Gruppierung und den Zugriff zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="2fab4-129">Namespaces help you organize and classify your programming elements for ease of grouping and accessing.</span></span> <span data-ttu-id="2fab4-130">Mit der [Namespace-Anweisung](../../language-reference/statements/namespace-statement.md) können Sie die folgenden Anweisungen in einem bestimmten Namespace klassifizieren.</span><span class="sxs-lookup"><span data-stu-id="2fab4-130">You use the [Namespace Statement](../../language-reference/statements/namespace-statement.md) to classify the following statements within a particular namespace.</span></span> <span data-ttu-id="2fab4-131">Weitere Informationen finden Sie unter [Namespaces in Visual Basic](namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="2fab4-131">For more information, see [Namespaces in Visual Basic](namespaces.md).</span></span>  
  
### <a name="conditional-compilation-statements"></a><span data-ttu-id="2fab4-132">Bedingte Kompilierungs Anweisungen</span><span class="sxs-lookup"><span data-stu-id="2fab4-132">Conditional Compilation Statements</span></span>  

 <span data-ttu-id="2fab4-133">Bedingte Kompilierungs Anweisungen können fast überall in der Quelldatei vorkommen.</span><span class="sxs-lookup"><span data-stu-id="2fab4-133">Conditional compilation statements can appear almost anywhere in your source file.</span></span> <span data-ttu-id="2fab4-134">Sie bewirken, dass Teile Ihres Codes zur Kompilierzeit in Abhängigkeit von bestimmten Bedingungen eingeschlossen oder ausgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="2fab4-134">They cause parts of your code to be included or excluded at compile time depending on certain conditions.</span></span> <span data-ttu-id="2fab4-135">Sie können Sie auch zum Debuggen Ihrer Anwendung verwenden, da bedingter Code nur im Debugmodus ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2fab4-135">You can also use them for debugging your application, because conditional code runs in debugging mode only.</span></span> <span data-ttu-id="2fab4-136">Weitere Informationen finden Sie unter [bedingte Kompilierung](conditional-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="2fab4-136">For more information, see [Conditional Compilation](conditional-compilation.md).</span></span>  
  
## <a name="namespace-level-programming-elements"></a><span data-ttu-id="2fab4-137">Programmier Elemente auf Namespace Ebene</span><span class="sxs-lookup"><span data-stu-id="2fab4-137">Namespace-Level Programming Elements</span></span>  

 <span data-ttu-id="2fab4-138">Klassen, Strukturen und Module enthalten den gesamten Code in der Quelldatei.</span><span class="sxs-lookup"><span data-stu-id="2fab4-138">Classes, structures, and modules contain all the code in your source file.</span></span> <span data-ttu-id="2fab4-139">Sie sind Elemente auf *Namespace Ebene* , die in einem Namespace oder auf der Quelldatei Ebene vorkommen können.</span><span class="sxs-lookup"><span data-stu-id="2fab4-139">They are *namespace-level* elements, which can appear within a namespace or at the source file level.</span></span> <span data-ttu-id="2fab4-140">Sie enthalten die Deklarationen aller anderen Programmier Elemente.</span><span class="sxs-lookup"><span data-stu-id="2fab4-140">They hold the declarations of all other programming elements.</span></span> <span data-ttu-id="2fab4-141">Schnittstellen, die Element Signaturen definieren, aber keine Implementierung bereitstellen, werden auch auf Modulebene angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2fab4-141">Interfaces, which define element signatures but provide no implementation, also appear at module level.</span></span> <span data-ttu-id="2fab4-142">Weitere Informationen zu den Elementen auf Modulebene finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="2fab4-142">For more information on the module-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="2fab4-143">Class-Anweisung</span><span class="sxs-lookup"><span data-stu-id="2fab4-143">Class Statement</span></span>](../../language-reference/statements/class-statement.md)  
  
- [<span data-ttu-id="2fab4-144">Structure Statement</span><span class="sxs-lookup"><span data-stu-id="2fab4-144">Structure Statement</span></span>](../../language-reference/statements/structure-statement.md)  
  
- [<span data-ttu-id="2fab4-145">Module-Anweisung</span><span class="sxs-lookup"><span data-stu-id="2fab4-145">Module Statement</span></span>](../../language-reference/statements/module-statement.md)  
  
- [<span data-ttu-id="2fab4-146">Interface-Anweisung</span><span class="sxs-lookup"><span data-stu-id="2fab4-146">Interface Statement</span></span>](../../language-reference/statements/interface-statement.md)  
  
 <span data-ttu-id="2fab4-147">Datenelemente auf Namespace Ebene sind Enumerationen und Delegaten.</span><span class="sxs-lookup"><span data-stu-id="2fab4-147">Data elements at namespace level are enumerations and delegates.</span></span>  
  
## <a name="module-level-programming-elements"></a><span data-ttu-id="2fab4-148">Programmier Elemente auf Modulebene</span><span class="sxs-lookup"><span data-stu-id="2fab4-148">Module-Level Programming Elements</span></span>  

 <span data-ttu-id="2fab4-149">Prozeduren, Operatoren, Eigenschaften und Ereignisse sind die einzigen Programmier Elemente, die ausführbaren Code enthalten können (Anweisungen, die zur Laufzeit Aktionen ausführen).</span><span class="sxs-lookup"><span data-stu-id="2fab4-149">Procedures, operators, properties, and events are the only programming elements that can hold executable code (statements that perform actions at run time).</span></span> <span data-ttu-id="2fab4-150">Dabei handelt es sich um die Elemente des Programms auf *Modulebene* .</span><span class="sxs-lookup"><span data-stu-id="2fab4-150">They are the *module-level* elements of your program.</span></span> <span data-ttu-id="2fab4-151">Weitere Informationen zu den Elementen auf Prozedur Ebene finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="2fab4-151">For more information on the procedure-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="2fab4-152">Function-Anweisung</span><span class="sxs-lookup"><span data-stu-id="2fab4-152">Function Statement</span></span>](../../language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="2fab4-153">Sub-Anweisung</span><span class="sxs-lookup"><span data-stu-id="2fab4-153">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)  
  
- [<span data-ttu-id="2fab4-154">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="2fab4-154">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)  
  
- [<span data-ttu-id="2fab4-155">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="2fab4-155">Operator Statement</span></span>](../../language-reference/statements/operator-statement.md)  
  
- [<span data-ttu-id="2fab4-156">Property Statement</span><span class="sxs-lookup"><span data-stu-id="2fab4-156">Property Statement</span></span>](../../language-reference/statements/property-statement.md)  
  
- [<span data-ttu-id="2fab4-157">Event-Anweisung</span><span class="sxs-lookup"><span data-stu-id="2fab4-157">Event Statement</span></span>](../../language-reference/statements/event-statement.md)  
  
 <span data-ttu-id="2fab4-158">Datenelemente auf Modulebene sind Variablen, Konstanten, Enumerationen und Delegaten.</span><span class="sxs-lookup"><span data-stu-id="2fab4-158">Data elements at module level are variables, constants, enumerations, and delegates.</span></span>  
  
## <a name="procedure-level-programming-elements"></a><span data-ttu-id="2fab4-159">Programmier Elemente auf Prozedur Ebene</span><span class="sxs-lookup"><span data-stu-id="2fab4-159">Procedure-Level Programming Elements</span></span>  

 <span data-ttu-id="2fab4-160">Die meisten Inhalte von Elementen auf *Prozedur Ebene* sind ausführbare Anweisungen, die den Lauf Zeit Code des Programms bilden.</span><span class="sxs-lookup"><span data-stu-id="2fab4-160">Most of the contents of *procedure-level* elements are executable statements, which constitute the run-time code of your program.</span></span> <span data-ttu-id="2fab4-161">Der gesamte ausführbare Code muss sich in einer Prozedur befinden ( `Function` , `Sub` , `Operator` , `Get` , `Set` , `AddHandler` , `RemoveHandler` , `RaiseEvent` ).</span><span class="sxs-lookup"><span data-stu-id="2fab4-161">All executable code must be in some procedure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span></span> <span data-ttu-id="2fab4-162">Weitere Informationen finden Sie unter [Transact-SQL-Anweisungen](../language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="2fab4-162">For more information, see [Statements](../language-features/statements.md).</span></span>  
  
 <span data-ttu-id="2fab4-163">Datenelemente auf Prozedur Ebene sind auf lokale Variablen und Konstanten beschränkt.</span><span class="sxs-lookup"><span data-stu-id="2fab4-163">Data elements at procedure level are limited to local variables and constants.</span></span>  
  
## <a name="the-main-procedure"></a><span data-ttu-id="2fab4-164">Die Haupt Prozedur</span><span class="sxs-lookup"><span data-stu-id="2fab4-164">The Main Procedure</span></span>  

 <span data-ttu-id="2fab4-165">Die `Main` Prozedur ist der erste Code, der ausgeführt wird, wenn die Anwendung geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="2fab4-165">The `Main` procedure is the first code to run when your application has been loaded.</span></span> <span data-ttu-id="2fab4-166">`Main` dient als Ausgangspunkt und allgemeine Kontrolle für Ihre Anwendung.</span><span class="sxs-lookup"><span data-stu-id="2fab4-166">`Main` serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="2fab4-167">Es gibt vier Arten von `Main` :</span><span class="sxs-lookup"><span data-stu-id="2fab4-167">There are four varieties of `Main`:</span></span>  
  
- `Sub Main()`  
  
- `Sub Main(ByVal cmdArgs() As String)`  
  
- `Function Main() As Integer`  
  
- `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 <span data-ttu-id="2fab4-168">Die häufigste Auswahl dieser Prozedur ist `Sub Main()` .</span><span class="sxs-lookup"><span data-stu-id="2fab4-168">The most common variety of this procedure is `Sub Main()`.</span></span> <span data-ttu-id="2fab4-169">Weitere Informationen finden Sie unter [Main Procedure in Visual Basic](main-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="2fab4-169">For more information, see [Main Procedure in Visual Basic](main-procedure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fab4-170">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2fab4-170">See also</span></span>

- [<span data-ttu-id="2fab4-171">Main-Prozedur in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2fab4-171">Main Procedure in Visual Basic</span></span>](main-procedure.md)
- [<span data-ttu-id="2fab4-172">Benennungskonventionen in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2fab4-172">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="2fab4-173">Beschränkungen in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2fab4-173">Visual Basic Limitations</span></span>](limitations.md)
