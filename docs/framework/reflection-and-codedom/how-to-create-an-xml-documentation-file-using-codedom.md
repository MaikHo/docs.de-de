---
title: 'Vorgehensweise: Erstellen einer XML-Dokumentationsdatei mit CodeDOM'
description: In diesem ausführlichen Beispiel erfahren Sie, wie Sie Code erstellen, mit dem eine XML-Dokumentationsdatei mit dem Code Document Object Model (CodeDom) erstellt wird.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
ms.openlocfilehash: f905b996910c6cfbc62378cc4cd6bb8c0e0e6fd4
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865150"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="2e6d2-103">Vorgehensweise: Erstellen einer XML-Dokumentation mit CodeDOM</span><span class="sxs-lookup"><span data-stu-id="2e6d2-103">How to: Create an XML documentation file using CodeDOM</span></span>

<span data-ttu-id="2e6d2-104">CodeDOM kann zum Erstellen von Code verwendet werden, der eine XML-Dokumentation erstellt.</span><span class="sxs-lookup"><span data-stu-id="2e6d2-104">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="2e6d2-105">Der Vorgang bringt die Erstellung des CodeDOM-Diagramms mit sich, das die XML-Dokumentationskommentare enthält, das Generieren des Codes und Kompilieren des generierten Codes mit der Compileroption, die die Ausgabe der XML-Dokumentation erstellt.</span><span class="sxs-lookup"><span data-stu-id="2e6d2-105">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
## <a name="create-a-codedom-graph"></a><span data-ttu-id="2e6d2-106">Erstellen eines CodeDOM-Graphen</span><span class="sxs-lookup"><span data-stu-id="2e6d2-106">Create a CodeDOM graph</span></span>
  
1. <span data-ttu-id="2e6d2-107">Erstellen Sie eine <xref:System.CodeDom.CodeCompileUnit>, die das CodeDOM-Diagramm für die Beispielanwendung enthält.</span><span class="sxs-lookup"><span data-stu-id="2e6d2-107">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2. <span data-ttu-id="2e6d2-108">Verwenden Sie den <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A>-Konstruktor mit dem `docComment`-Parameter, der auf `true` festgelegt ist, um die Kommentarelemente und den Kommentartext der XML-Dokumentation zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2e6d2-108">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="2e6d2-109">Generieren des Codes aus der CodeCompileUnit</span><span class="sxs-lookup"><span data-stu-id="2e6d2-109">Generate the code from the CodeCompileUnit</span></span>
  
1. <span data-ttu-id="2e6d2-110">Verwenden Sie die <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A>-Methode, um den Code zu generieren und eine Quelldatei zu erstellen, die kompiliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="2e6d2-110">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="2e6d2-111">Kompilieren des Codes und Generieren der Dokumentationsdatei</span><span class="sxs-lookup"><span data-stu-id="2e6d2-111">Compile the code and generate the documentation file</span></span>
  
1. <span data-ttu-id="2e6d2-112">Fügen Sie die Compileroption **/doc** der <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A>-Eigenschaft eines <xref:System.CodeDom.Compiler.CompilerParameters>-Objekts hinzu, und übermitteln Sie das Objekt an die <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A>-Methode, um die XML-Dokumentationsdatei zu erstellen, wenn der Code kompiliert wird.</span><span class="sxs-lookup"><span data-stu-id="2e6d2-112">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="2e6d2-113">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2e6d2-113">Example</span></span>

<span data-ttu-id="2e6d2-114">Das folgende Codebeispiel erstellt ein CodeDOM-Diagramm mit Dokumentationskommentaren, generiert eine Codedatei aus dem Diagramm und kompiliert die Datei und erstellt eine zugeordnete XML-Dokumentationsdatei.</span><span class="sxs-lookup"><span data-stu-id="2e6d2-114">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="2e6d2-115">Das Codebeispiel erstellt die folgende XML-Dokumentation in der *HelloWorldDoc.xml*-Datei.</span><span class="sxs-lookup"><span data-stu-id="2e6d2-115">The code example creates the following XML documentation in the *HelloWorldDoc.xml* file.</span></span>  
  
```xml  
<?xml version="1.0" ?>
<doc>  
  <assembly>  
    <name>HelloWorld</name>
  </assembly>  
  <members>  
    <member name="T:Samples.Class1">  
      <summary>  
        Create a Hello World application.
      </summary>
      <seealso cref="M:Samples.Class1.Main" />
    </member>  
    <member name="M:Samples.Class1.Main">  
      <summary>  
        Main method for HelloWorld application.
        <para>Add a new paragraph to the description.</para>
      </summary>  
    </member>  
  </members>  
</doc>  
```  
  
## <a name="compile-permissions"></a><span data-ttu-id="2e6d2-116">Kompilierberechtigungen</span><span class="sxs-lookup"><span data-stu-id="2e6d2-116">Compile permissions</span></span>
  
<span data-ttu-id="2e6d2-117">Dieses Codebeispiel benötigt die festgelegte `FullTrust`-Berechtigung, damit es erfolgreich ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="2e6d2-117">This code example requires the `FullTrust` permission set to execute successfully.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2e6d2-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2e6d2-118">See also</span></span>

- [<span data-ttu-id="2e6d2-119">Dokumentieren von Code mit XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e6d2-119">Document your code with XML (Visual Basic)</span></span>](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="2e6d2-120">XML-Dokumentationskommentare</span><span class="sxs-lookup"><span data-stu-id="2e6d2-120">XML documentation comments</span></span>](../../csharp/programming-guide/xmldoc/index.md)
- [<span data-ttu-id="2e6d2-121">XML-Dokumentation (Visual C++)</span><span class="sxs-lookup"><span data-stu-id="2e6d2-121">XML documentation (C++)</span></span>](/cpp/ide/xml-documentation-visual-cpp)
