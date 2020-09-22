---
title: Fehler beim Laden der DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 35733fe2e20d46207f6cfdaee32f6559fceed6eb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874380"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="1f8e9-102">Fehler beim Laden der DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f8e9-102">Error in loading DLL (Visual Basic)</span></span>

<span data-ttu-id="1f8e9-103">Eine Dynamic Link Library (dll) ist eine Bibliothek, die in der-Klausel einer-Anweisung angegeben ist `Lib` `Declare` .</span><span class="sxs-lookup"><span data-stu-id="1f8e9-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="1f8e9-104">Mögliche Ursachen für diesen Fehler:</span><span class="sxs-lookup"><span data-stu-id="1f8e9-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="1f8e9-105">Die Datei ist keine ausführbare DLL-Datei.</span><span class="sxs-lookup"><span data-stu-id="1f8e9-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="1f8e9-106">Bei der Datei handelt es sich nicht um eine Microsoft Windows-DLL.</span><span class="sxs-lookup"><span data-stu-id="1f8e9-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="1f8e9-107">Die dll verweist auf eine andere dll, die nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="1f8e9-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="1f8e9-108">Die dll oder die referenzierte DLL befindet sich nicht in einem Verzeichnis, das im Pfad angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="1f8e9-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1f8e9-109">So beheben Sie diesen Fehler</span><span class="sxs-lookup"><span data-stu-id="1f8e9-109">To correct this error</span></span>  
  
- <span data-ttu-id="1f8e9-110">Handelt es sich bei der Datei um eine Quell Textdatei und somit nicht um eine ausführbare DLL-Datei, muss sie kompiliert und mit einem ausführbaren DLL-Formular verknüpft werden.</span><span class="sxs-lookup"><span data-stu-id="1f8e9-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="1f8e9-111">Wenn die Datei keine Microsoft Windows-dll ist, müssen Sie die Microsoft Windows-Entsprechung abrufen.</span><span class="sxs-lookup"><span data-stu-id="1f8e9-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="1f8e9-112">Wenn die dll auf eine andere dll verweist, die nicht vorhanden ist, können Sie die referenzierte DLL abrufen und verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="1f8e9-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="1f8e9-113">Wenn sich die dll oder die referenzierte DLL nicht in einem Verzeichnis befindet, das durch den Pfad angegeben ist, verschieben Sie die dll in ein referenziertes Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="1f8e9-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f8e9-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1f8e9-114">See also</span></span>

- [<span data-ttu-id="1f8e9-115">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="1f8e9-115">Declare Statement</span></span>](../statements/declare-statement.md)
