---
title: Strukturen und andere Programmierelemente
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 26c98adda7305783b0220141db35b08285b21554
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084085"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="1f854-102">Strukturen und andere Programmierelemente (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f854-102">Structures and Other Programming Elements (Visual Basic)</span></span>

<span data-ttu-id="1f854-103">Sie können Strukturen in Verbindung mit Arrays, Objekten und Prozeduren sowie untereinander verwenden.</span><span class="sxs-lookup"><span data-stu-id="1f854-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="1f854-104">Die Interaktionen verwenden die gleiche Syntax wie diese Elemente einzeln verwenden.</span><span class="sxs-lookup"><span data-stu-id="1f854-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f854-105">Sie können keines der Structure-Elemente in der Struktur Deklaration initialisieren.</span><span class="sxs-lookup"><span data-stu-id="1f854-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="1f854-106">Sie können Werte nur Elementen einer Variablen zuweisen, die als Strukturtyp deklariert wurde.</span><span class="sxs-lookup"><span data-stu-id="1f854-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="1f854-107">Strukturen und Arrays</span><span class="sxs-lookup"><span data-stu-id="1f854-107">Structures and Arrays</span></span>  

 <span data-ttu-id="1f854-108">Eine Struktur kann ein Array als ein oder mehrere Elemente enthalten.</span><span class="sxs-lookup"><span data-stu-id="1f854-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="1f854-109">Dies wird anhand des folgenden Beispiels veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f854-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 <span data-ttu-id="1f854-110">Sie greifen auf die Werte eines Arrays innerhalb einer Struktur auf die gleiche Weise zu, wie Sie auf eine Eigenschaft in einem Objekt zugreifen.</span><span class="sxs-lookup"><span data-stu-id="1f854-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="1f854-111">Dies wird anhand des folgenden Beispiels veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f854-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="1f854-112">Sie können auch ein Array von-Strukturen deklarieren.</span><span class="sxs-lookup"><span data-stu-id="1f854-112">You can also declare an array of structures.</span></span> <span data-ttu-id="1f854-113">Dies wird anhand des folgenden Beispiels veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f854-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="1f854-114">Sie befolgen die gleichen Regeln für den Zugriff auf die Komponenten dieser Datenarchitektur.</span><span class="sxs-lookup"><span data-stu-id="1f854-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="1f854-115">Dies wird anhand des folgenden Beispiels veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f854-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="1f854-116">Strukturen und Objekte</span><span class="sxs-lookup"><span data-stu-id="1f854-116">Structures and Objects</span></span>  

 <span data-ttu-id="1f854-117">Eine Struktur kann ein Objekt als ein oder mehrere Elemente enthalten.</span><span class="sxs-lookup"><span data-stu-id="1f854-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="1f854-118">Dies wird anhand des folgenden Beispiels veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f854-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="1f854-119">Sie sollten eine bestimmte Objektklasse in einer solchen Deklaration anstelle von verwenden `Object` .</span><span class="sxs-lookup"><span data-stu-id="1f854-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="1f854-120">Strukturen und Prozeduren</span><span class="sxs-lookup"><span data-stu-id="1f854-120">Structures and Procedures</span></span>  

 <span data-ttu-id="1f854-121">Sie können eine Struktur als Prozedur Argument übergeben.</span><span class="sxs-lookup"><span data-stu-id="1f854-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="1f854-122">Dies wird anhand des folgenden Beispiels veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f854-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="1f854-123">Im vorangehenden Beispiel wird die Struktur als *Verweis*weitergeleitet, sodass die Prozedur die Elemente ändern kann, sodass die Änderungen im aufrufenden Code wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="1f854-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="1f854-124">Wenn Sie eine Struktur vor solchen Änderungen schützen möchten, übergeben Sie Sie als Wert.</span><span class="sxs-lookup"><span data-stu-id="1f854-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="1f854-125">Sie können auch eine Struktur aus einer Prozedur zurückgeben `Function` .</span><span class="sxs-lookup"><span data-stu-id="1f854-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="1f854-126">Dies wird anhand des folgenden Beispiels veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f854-126">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a><span data-ttu-id="1f854-127">Strukturen innerhalb von Strukturen</span><span class="sxs-lookup"><span data-stu-id="1f854-127">Structures Within Structures</span></span>  

 <span data-ttu-id="1f854-128">Strukturen können andere Strukturen enthalten.</span><span class="sxs-lookup"><span data-stu-id="1f854-128">Structures can contain other structures.</span></span> <span data-ttu-id="1f854-129">Dies wird anhand des folgenden Beispiels veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f854-129">The following example illustrates this.</span></span>  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 <span data-ttu-id="1f854-130">Sie können dieses Verfahren auch verwenden, um eine Struktur zu kapseln, die in einem Modul innerhalb einer Struktur definiert ist, die in einem anderen Modul definiert ist.</span><span class="sxs-lookup"><span data-stu-id="1f854-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="1f854-131">Strukturen können andere Strukturen in beliebiger Tiefe enthalten.</span><span class="sxs-lookup"><span data-stu-id="1f854-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f854-132">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1f854-132">See also</span></span>

- [<span data-ttu-id="1f854-133">Datentypen</span><span class="sxs-lookup"><span data-stu-id="1f854-133">Data Types</span></span>](index.md)
- [<span data-ttu-id="1f854-134">Elementare Datentypen</span><span class="sxs-lookup"><span data-stu-id="1f854-134">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="1f854-135">Zusammengesetzte Datentypen</span><span class="sxs-lookup"><span data-stu-id="1f854-135">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="1f854-136">Wert- und Verweistypen</span><span class="sxs-lookup"><span data-stu-id="1f854-136">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="1f854-137">Strukturen</span><span class="sxs-lookup"><span data-stu-id="1f854-137">Structures</span></span>](structures.md)
- [<span data-ttu-id="1f854-138">Problembehandlung bei Datentypen</span><span class="sxs-lookup"><span data-stu-id="1f854-138">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="1f854-139">Vorgehensweise: Deklarieren einer Struktur</span><span class="sxs-lookup"><span data-stu-id="1f854-139">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="1f854-140">Strukturvariablen</span><span class="sxs-lookup"><span data-stu-id="1f854-140">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="1f854-141">Strukturen und Klassen</span><span class="sxs-lookup"><span data-stu-id="1f854-141">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="1f854-142">Structure Statement</span><span class="sxs-lookup"><span data-stu-id="1f854-142">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
