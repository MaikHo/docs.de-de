---
title: 'Gewusst wie: Lesen von Text aus Dateien mit einem StreamReader'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 5ec161f5146d5bea7f34d4a5b6c154f6c45b1cf4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546496"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="74157-102">Gewusst wie: Lesen von Text aus Dateien mit einem StreamReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74157-102">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>

<span data-ttu-id="74157-103">Das `My.Computer.FileSystem`-Objekt bietet Methoden, mit denen Sie ein <xref:System.IO.TextReader>- und ein <xref:System.IO.TextWriter>-Objekt öffnen können.</span><span class="sxs-lookup"><span data-stu-id="74157-103">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="74157-104">Diese Methoden, `OpenTextFileWriter` und `OpenTextFileReader`, sind fortgeschrittene Methoden, die nicht in IntelliSense angezeigt werden, es sei denn, Sie wählen die Registerkarte **Alle** aus.</span><span class="sxs-lookup"><span data-stu-id="74157-104">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="74157-105">Lesen einer Zeile aus einer Datei mit einem Textreader</span><span class="sxs-lookup"><span data-stu-id="74157-105">To read a line from a file with a text reader</span></span>  
  
- <span data-ttu-id="74157-106">Verwenden Sie die `OpenTextFileReader`-Methode, um das <xref:System.IO.TextReader>-Objekt zu öffnen. und geben Sie die Datei an.</span><span class="sxs-lookup"><span data-stu-id="74157-106">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="74157-107">In diesem Beispiel wird die Datei `testfile.txt` geöffnet, eine Zeile daraus gelesen und in einem Meldungsfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="74157-107">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="74157-108">Stabile Programmierung</span><span class="sxs-lookup"><span data-stu-id="74157-108">Robust Programming</span></span>  

 <span data-ttu-id="74157-109">Die Datei, die gelesen wird, muss eine Textdatei sein.</span><span class="sxs-lookup"><span data-stu-id="74157-109">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="74157-110">Beurteilen Sie den Inhalt der Datei nicht anhand des Dateinamens.</span><span class="sxs-lookup"><span data-stu-id="74157-110">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="74157-111">Bei der Datei "Form1.vb" handelt es sich zum Beispiel nicht unbedingt um eine Visual Basic-Quelldatei.</span><span class="sxs-lookup"><span data-stu-id="74157-111">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="74157-112">Überprüfen Sie alle Eingaben, bevor Sie die Daten in der Anwendung verwenden.</span><span class="sxs-lookup"><span data-stu-id="74157-112">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="74157-113">Die Datei kann andere Inhalte als erwartet enthalten. Die Methoden zum Lesen aus der Datei können fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="74157-113">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="74157-114">.NET Framework-Sicherheit</span><span class="sxs-lookup"><span data-stu-id="74157-114">.NET Framework Security</span></span>  

 <span data-ttu-id="74157-115">Die Assembly benötigt zum Lesen aus dieser Datei eine von der <xref:System.Security.Permissions.FileIOPermission>-Klasse gewährte Berechtigungsebene.</span><span class="sxs-lookup"><span data-stu-id="74157-115">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="74157-116">Wenn Sie in einem teilweise vertrauenswürdigen Kontext arbeiten, kann der Code möglicherweise aufgrund fehlender Berechtigungen eine Ausnahme auslösen.</span><span class="sxs-lookup"><span data-stu-id="74157-116">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="74157-117">Weitere Informationen finden Sie unter [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="74157-117">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span> <span data-ttu-id="74157-118">Außerdem benötigt der Benutzer Zugriff auf die Datei.</span><span class="sxs-lookup"><span data-stu-id="74157-118">The user also needs access to the file.</span></span> <span data-ttu-id="74157-119">Weitere Informationen finden Sie unter [Übersicht über die ACL-Technologie](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="74157-119">For more information, see [ACL Technology Overview](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74157-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="74157-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [<span data-ttu-id="74157-121">SaveFileDialog-Komponente</span><span class="sxs-lookup"><span data-stu-id="74157-121">SaveFileDialog Component</span></span>](/dotnet/desktop/winforms/controls/savefiledialog-component-windows-forms)
- [<span data-ttu-id="74157-122">Lesen aus Dateien</span><span class="sxs-lookup"><span data-stu-id="74157-122">Reading from Files</span></span>](reading-from-files.md)
