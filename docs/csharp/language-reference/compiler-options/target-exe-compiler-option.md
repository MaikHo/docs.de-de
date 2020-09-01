---
description: -target:exe (C#-Compileroptionen)
title: -target:exe (C#-Compileroptionen)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 3cea52fe872fcb407206ee2063b93dc81447a3b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128503"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="071b1-103">-target:exe (C#-Compileroptionen)</span><span class="sxs-lookup"><span data-stu-id="071b1-103">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="071b1-104">Die Option **-target:exe** bewirkt, dass der Compiler eine ausführbare Konsolenanwendung (EXE) erstellt.</span><span class="sxs-lookup"><span data-stu-id="071b1-104">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="071b1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="071b1-105">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="071b1-106">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="071b1-106">Remarks</span></span>  
 <span data-ttu-id="071b1-107">Die Option **-target:exe** ist standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="071b1-107">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="071b1-108">Die ausführbare Datei wird mit der Dateiendung „.exe“ erstellt.</span><span class="sxs-lookup"><span data-stu-id="071b1-108">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="071b1-109">Verwenden Sie [-target:winexe](./target-winexe-compiler-option.md), um ein ausführbares Windows-Programm zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="071b1-109">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="071b1-110">Sofern Sie nicht die Option [-out](./out-compiler-option.md) verwenden, erhält die Ausgabedatei den Namen der Eingabedatei, die die [Main](../../programming-guide/main-and-command-args/index.md)-Methode enthält.</span><span class="sxs-lookup"><span data-stu-id="071b1-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="071b1-111">Wenn es in der Befehlszeile angegeben wurde, werden alle Dateien bis zur nächsten Option **-out** oder **-target:module** verwendet, um die EXE-Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="071b1-111">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="071b1-112">Nur eine **Main**-Methode wird in den Quellcodedateien benötigt, die in eine EXE-Datei kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="071b1-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="071b1-113">Sollte Ihr Code mehr als eine Klasse mit einer **Main**-Methode haben, können Sie mit der Compileroption [-main](./main-compiler-option.md) angeben, welche Klasse die Methode **Main** enthält.</span><span class="sxs-lookup"><span data-stu-id="071b1-113">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="071b1-114">So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest</span><span class="sxs-lookup"><span data-stu-id="071b1-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="071b1-115">Öffnen Sie die Seite **Eigenschaften** des Projekts.</span><span class="sxs-lookup"><span data-stu-id="071b1-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="071b1-116">Klicken Sie auf die Eigenschaftenseite **Anwendung**.</span><span class="sxs-lookup"><span data-stu-id="071b1-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="071b1-117">Ändern Sie die Eigenschaft **Ausgabetyp**.</span><span class="sxs-lookup"><span data-stu-id="071b1-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="071b1-118">Informationen zum programmgesteuerten Festlegen dieser Compileroption finden Sie unter <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="071b1-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="071b1-119">Beispiel</span><span class="sxs-lookup"><span data-stu-id="071b1-119">Example</span></span>  
 <span data-ttu-id="071b1-120">Jede der folgenden Befehlszeilen wird `in.cs` kompilieren, wodurch `in.exe` erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="071b1-120">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="071b1-121">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="071b1-121">See also</span></span>

- [<span data-ttu-id="071b1-122">-target (C#-Compileroptionen)</span><span class="sxs-lookup"><span data-stu-id="071b1-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="071b1-123">C#-Compileroptionen</span><span class="sxs-lookup"><span data-stu-id="071b1-123">C# Compiler Options</span></span>](./index.md)
