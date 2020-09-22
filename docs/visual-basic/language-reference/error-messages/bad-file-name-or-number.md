---
title: Der Dateiname oder die Zahl ist ungültig.
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: d57a9e78e6ae179d3050e5a92399ca731fa16ba7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874908"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="3a6fd-102">Der Dateiname oder die Zahl ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="3a6fd-102">Bad file name or number</span></span>

<span data-ttu-id="3a6fd-103">Fehler beim Zugriff auf die angegebene Datei.</span><span class="sxs-lookup"><span data-stu-id="3a6fd-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="3a6fd-104">Zu den möglichen Ursachen für diesen Fehler gehören:</span><span class="sxs-lookup"><span data-stu-id="3a6fd-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="3a6fd-105">Eine-Anweisung verweist auf eine Datei mit einem Dateinamen oder einer Zahl, der nicht in der-Anweisung angegeben wurde `FileOpen` oder der in einer-Anweisung angegeben wurde, `FileOpen` aber anschließend geschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="3a6fd-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="3a6fd-106">Eine-Anweisung verweist auf eine Datei mit einer Zahl außerhalb des Bereichs von Datei Nummern.</span><span class="sxs-lookup"><span data-stu-id="3a6fd-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="3a6fd-107">Eine-Anweisung verweist auf einen ungültigen Dateinamen oder eine ungültige Nummer.</span><span class="sxs-lookup"><span data-stu-id="3a6fd-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3a6fd-108">So beheben Sie diesen Fehler</span><span class="sxs-lookup"><span data-stu-id="3a6fd-108">To correct this error</span></span>  
  
1. <span data-ttu-id="3a6fd-109">Stellen Sie sicher, dass der Dateiname in einer-Anweisung angegeben ist `FileOpen` .</span><span class="sxs-lookup"><span data-stu-id="3a6fd-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="3a6fd-110">Beachten Sie, dass Sie, wenn Sie die `FileClose` Anweisung ohne Argumente aufgerufen haben, möglicherweise versehentlich alle geöffneten Dateien geschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="3a6fd-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="3a6fd-111">Wenn Ihr Code Datei Nummern algorithmisch erzeugt, stellen Sie sicher, dass die Zahlen gültig sind.</span><span class="sxs-lookup"><span data-stu-id="3a6fd-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="3a6fd-112">Überprüfen Sie die Dateinamen, um sicherzustellen, dass Sie den Betriebssystem Konventionen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="3a6fd-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a6fd-113">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3a6fd-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="3a6fd-114">Benennungskonventionen in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a6fd-114">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
