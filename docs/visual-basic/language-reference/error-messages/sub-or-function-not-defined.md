---
title: "\"Sub\" oder \"Function\" ist nicht definiert"
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 24e290ce1193cd6bc6a0ec8985902576332423f2
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870524"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="e5b5d-102">Sub oder Funktion ist nicht definiert (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5b5d-102">Sub or Function not defined (Visual Basic)</span></span>

<span data-ttu-id="e5b5d-103">Ein `Sub` oder `Function` muss definiert werden, um aufgerufen werden zu können.</span><span class="sxs-lookup"><span data-stu-id="e5b5d-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="e5b5d-104">Dieser Fehler kann folgende Ursachen haben:</span><span class="sxs-lookup"><span data-stu-id="e5b5d-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="e5b5d-105">Falsche Rechtschreibprüfung für den Namen der Prozedur.</span><span class="sxs-lookup"><span data-stu-id="e5b5d-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="e5b5d-106">Es wird versucht, eine Prozedur aus einem anderen Projekt aufzurufen, ohne explizit einen Verweis auf dieses Projekt im Dialogfeld **Verweise** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="e5b5d-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="e5b5d-107">Angeben einer Prozedur, die für die aufrufenden Prozeduren nicht sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="e5b5d-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="e5b5d-108">Deklarieren einer Windows-DLL-Routine (Dynamic-Link Library) oder einer Macintosh-Code Ressourcen Routine, die nicht in der angegebenen Bibliothek oder Code Ressource ist.</span><span class="sxs-lookup"><span data-stu-id="e5b5d-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e5b5d-109">So beheben Sie diesen Fehler</span><span class="sxs-lookup"><span data-stu-id="e5b5d-109">To correct this error</span></span>  
  
1. <span data-ttu-id="e5b5d-110">Stellen Sie sicher, dass der Name der Prozedur richtig geschrieben ist.</span><span class="sxs-lookup"><span data-stu-id="e5b5d-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="e5b5d-111">Suchen Sie den Namen des Projekts, das die Prozedur enthält, die Sie im Dialogfeld **Verweise** aufzurufen möchten.</span><span class="sxs-lookup"><span data-stu-id="e5b5d-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="e5b5d-112">Wenn Sie nicht angezeigt wird, klicken Sie auf die Schaltfläche **Durchsuchen** , um Sie zu suchen.</span><span class="sxs-lookup"><span data-stu-id="e5b5d-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="e5b5d-113">Aktivieren Sie das Kontrollkästchen links neben dem Projektnamen, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="e5b5d-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="e5b5d-114">Überprüfen Sie den Namen der Routine.</span><span class="sxs-lookup"><span data-stu-id="e5b5d-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b5d-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5b5d-115">See also</span></span>

- [<span data-ttu-id="e5b5d-116">Fehlertypen</span><span class="sxs-lookup"><span data-stu-id="e5b5d-116">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="e5b5d-117">Verwalten von Verweisen in einem Projekt</span><span class="sxs-lookup"><span data-stu-id="e5b5d-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="e5b5d-118">Sub-Anweisung</span><span class="sxs-lookup"><span data-stu-id="e5b5d-118">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="e5b5d-119">Function-Anweisung</span><span class="sxs-lookup"><span data-stu-id="e5b5d-119">Function Statement</span></span>](../statements/function-statement.md)
