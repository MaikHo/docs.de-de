---
title: Frühes und spätes Binden
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: ce74498225fb7947c92f2f4f61ec46e6b2594151
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086009"
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="1b538-102">Frühes und spätes Binden (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b538-102">Early and Late Binding (Visual Basic)</span></span>

<span data-ttu-id="1b538-103">Der Visual Basic-Compiler führt einen Prozess aus, der aufgerufen `binding` wird, wenn ein Objekt einer Objektvariablen zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="1b538-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="1b538-104">Objekt wird *früh gebunden*, wenn es einer Variablen zugeordnet wird, für die ein spezifischer Objekttyp deklariert wurde.</span><span class="sxs-lookup"><span data-stu-id="1b538-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="1b538-105">Früh gebundene Objekte ermöglichen es dem Compiler, die Speicherbelegung und andere Optimierungen vor der Ausführung einer Anwendung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="1b538-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="1b538-106">Das folgende Codefragment deklariert beispielsweise eine Variable des Typs <xref:System.IO.FileStream>:</span><span class="sxs-lookup"><span data-stu-id="1b538-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="1b538-107">Da <xref:System.IO.FileStream> ein spezifischer Objekttyp ist, handelt es sich bei der Zuweisung der Instanz zu `FS` um eine frühe Bindung.</span><span class="sxs-lookup"><span data-stu-id="1b538-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="1b538-108">Im Gegensatz dazu wird ein Objekt *spät gebunden*, wenn es einer Variablen zugeordnet wird, für die der Typ `Object` deklariert wurde.</span><span class="sxs-lookup"><span data-stu-id="1b538-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="1b538-109">Objekte dieses Typs können Verweise zu beliebigen Objekten enthalten, jedoch gehen einige der Vorteile früh gebundener Objekte verloren.</span><span class="sxs-lookup"><span data-stu-id="1b538-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="1b538-110">Das folgende Codefragment deklariert beispielsweise eine Objektvariable, die ein von der `CreateObject`-Funktion zurückgegebenes Objekt enthalten soll:</span><span class="sxs-lookup"><span data-stu-id="1b538-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="1b538-111">Vorteile der frühen Bindung</span><span class="sxs-lookup"><span data-stu-id="1b538-111">Advantages of Early Binding</span></span>  

 <span data-ttu-id="1b538-112">Sie sollten soweit möglich früh gebundene Objekte verwenden, da diese dem Compiler wichtige Optimierungen ermöglichen, die zu effizienteren Anwendungen führen.</span><span class="sxs-lookup"><span data-stu-id="1b538-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="1b538-113">Früh gebundene Objekte sind bedeutend schneller als spät gebundene Objekte, verbessern die Lesbarkeit des Codes und erleichtern dessen Verwaltung, weil sie die Art der verwendeten Objekte genau angeben.</span><span class="sxs-lookup"><span data-stu-id="1b538-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="1b538-114">Ein weiterer Vorteil der frühen Bindung besteht darin, dass Sie nützliche Features wie automatische Codevervollständigung und dynamische Hilfe ermöglicht, da die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio genau bestimmen kann, mit welchem Objekttyp Sie arbeiten, während Sie den Code bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="1b538-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="1b538-115">Die frühe Bindung reduziert die Anzahl und den Schweregrad von Laufzeitfehlern, da sie dem Compiler die Ausgabe von Fehlern während der Programmkompilierung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="1b538-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b538-116">Die späte Bindung kann nur für den Zugriff auf als `Public` deklarierte Typmember verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1b538-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="1b538-117">Der Zugriff auf als `Friend` oder `Protected Friend` deklarierte Member führt zu Laufzeitfehlern.</span><span class="sxs-lookup"><span data-stu-id="1b538-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b538-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1b538-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="1b538-119">Objektlebensdauer: Erstellen und Zerstören von Objekten</span><span class="sxs-lookup"><span data-stu-id="1b538-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="1b538-120">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="1b538-120">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
