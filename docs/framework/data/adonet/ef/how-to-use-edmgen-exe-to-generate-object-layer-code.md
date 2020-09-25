---
title: 'Vorgehensweise: Generieren von Objektebenencode mit „EdmGen.exe“'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: a243a588dcb6f7e7001de331cb9011a23ee2fdbe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198222"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="43dff-102">Vorgehensweise: Generieren von Objektebenencode mit „EdmGen.exe“</span><span class="sxs-lookup"><span data-stu-id="43dff-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>

<span data-ttu-id="43dff-103">In diesem Thema wird gezeigt, wie Sie mithilfe des [EDM-Generators (EdmGen.exe)](edm-generator-edmgen-exe.md) auf der Grundlage der CSDL-Datei Code auf Objektebene generieren.</span><span class="sxs-lookup"><span data-stu-id="43dff-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="43dff-104">So generieren Sie mithilfe von EdmGen.exe den Objektebenencode für das Modell "School" für ein Visual Basic-Projekt</span><span class="sxs-lookup"><span data-stu-id="43dff-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="43dff-105">Erstellen der Datenbank "School".</span><span class="sxs-lookup"><span data-stu-id="43dff-105">Create the School database.</span></span> <span data-ttu-id="43dff-106">Weitere Informationen finden Sie unter [Erstellen der Beispieldatenbank "School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))".</span><span class="sxs-lookup"><span data-stu-id="43dff-106">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="43dff-107">Generieren Sie das Modell "School", oder verwenden Sie die Datei School.csdl.</span><span class="sxs-lookup"><span data-stu-id="43dff-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="43dff-108">Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von EdmGen.exe zum Generieren von Modell-und Mapping-Dateien](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="43dff-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="43dff-109">Führen Sie an der Eingabeaufforderung den folgenden Befehl ohne Zeilenumbrüche aus:</span><span class="sxs-lookup"><span data-stu-id="43dff-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="43dff-110">So generieren Sie mithilfe von EdmGen.exe den Objektebenencode für das Modell "School" für ein C#-Projekt</span><span class="sxs-lookup"><span data-stu-id="43dff-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="43dff-111">Erstellen der Datenbank "School".</span><span class="sxs-lookup"><span data-stu-id="43dff-111">Create the School database.</span></span> <span data-ttu-id="43dff-112">Weitere Informationen finden Sie unter [Erstellen der Beispieldatenbank "School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))".</span><span class="sxs-lookup"><span data-stu-id="43dff-112">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="43dff-113">Generieren Sie das Modell "School", oder verwenden Sie die Datei School.csdl.</span><span class="sxs-lookup"><span data-stu-id="43dff-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="43dff-114">Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von EdmGen.exe zum Generieren von Modell-und Mapping-Dateien](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="43dff-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="43dff-115">Führen Sie an der Eingabeaufforderung den folgenden Befehl ohne Zeilenumbrüche aus:</span><span class="sxs-lookup"><span data-stu-id="43dff-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="43dff-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="43dff-116">See also</span></span>

- [<span data-ttu-id="43dff-117">Modellieren und Zuordnen</span><span class="sxs-lookup"><span data-stu-id="43dff-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="43dff-118">[Gewusst wie: Manuelles Konfigurieren eines Entity Framework-Projekts](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="43dff-118">[How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="43dff-119">[ADO.NET Entity Data Model Tools (ADO.NET Entity Data Model-Tools)](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="43dff-119">[ADO.NET Entity Data Model  Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="43dff-120">[Gewusst wie: Vorgenerieren von Ansichten zur Verbesserung der Abfrageleistung](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="43dff-120">[How to: Pre-Generate Views to Improve Query Performance](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="43dff-121">Vorgehensweise: Generieren von Modell- und Zuordnungsdateien mit „EdmGen.exe“</span><span class="sxs-lookup"><span data-stu-id="43dff-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
