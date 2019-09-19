---
title: 'Vorgehensweise: Erstellen einer Mehrfachdateiassembly'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b95d686529da83a5a52edb80219874530212dcc
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991261"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="f262c-102">Vorgehensweise: Erstellen einer Mehrfachdateiassembly</span><span class="sxs-lookup"><span data-stu-id="f262c-102">How to: Build a multifile assembly</span></span>

<span data-ttu-id="f262c-103">In diesem Artikel wird beschrieben, wie eine Mehrfachdateiassembly erstellt wird, und es wird Code vorgestellt, der jeden Schritt in der Vorgehensweise veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="f262c-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="f262c-104">Die Visual Studio-IDE für C# und Visual Basic kann nur zum Erstellen von Einzeldateiassemblys verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f262c-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="f262c-105">Wenn Sie Mehrfachdateiassemblys erstellen möchten, müssen Sie auf Befehlszeilencompiler oder auf Visual Studio mit Visual C++ zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="f262c-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="f262c-106">Mehrfachdateiassemblys werden nur im .NET Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f262c-106">Multifile assemblies are supported by .NET Framework only.</span></span>

## <a name="create-a-multifile-assembly"></a><span data-ttu-id="f262c-107">Erstellen einer Mehrfachdateiassembly</span><span class="sxs-lookup"><span data-stu-id="f262c-107">Create a multifile assembly</span></span>

1. <span data-ttu-id="f262c-108">Kompilieren Sie alle Dateien mit Namespaces, auf die andere Module der Assembly verweisen, in Codemodule.</span><span class="sxs-lookup"><span data-stu-id="f262c-108">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="f262c-109">Die Standarderweiterung für Codemodule ist *.netmodule*.</span><span class="sxs-lookup"><span data-stu-id="f262c-109">The default extension for code modules is *.netmodule*.</span></span>

   <span data-ttu-id="f262c-110">Beispielsweise weist die Datei `Stringer` den Namespace `myStringer` auf, der die Klasse `Stringer` enthält.</span><span class="sxs-lookup"><span data-stu-id="f262c-110">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="f262c-111">Die `Stringer`-Klasse enthält die `StringerMethod`-Methode, die eine einzelne Zeile auf der Konsole ausgibt.</span><span class="sxs-lookup"><span data-stu-id="f262c-111">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Imports System

   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. <span data-ttu-id="f262c-112">Verwenden Sie folgenden Befehl, um diesen Code zu kompilieren:</span><span class="sxs-lookup"><span data-stu-id="f262c-112">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   <span data-ttu-id="f262c-113">Durch die Compileroption **/t:** in Verbindung mit dem Parameter *module* wird die Datei als Modul kompiliert, nicht als Assembly.</span><span class="sxs-lookup"><span data-stu-id="f262c-113">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="f262c-114">Der Compiler erzeugt ein Modul mit dem Namen *Stringer.netmodule*, das anschließend einer Assembly hinzugefügt werden kann.</span><span class="sxs-lookup"><span data-stu-id="f262c-114">The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.</span></span>

3. <span data-ttu-id="f262c-115">Kompilieren Sie alle weiteren Module unter Verwendung der erforderlichen Compileroptionen, um die anderen Module anzugeben, auf die im Code verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="f262c-115">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="f262c-116">In diesem Schritt kommt die **/addmodule**-Compileroption zum Einsatz.</span><span class="sxs-lookup"><span data-stu-id="f262c-116">This step uses the **/addmodule** compiler option.</span></span>

   <span data-ttu-id="f262c-117">Im folgenden Beispiel verfügt ein Codemodul mit dem Namen *Client* über die `Main`-Methode als Einstiegspunkt. Diese verweist wiederum auf eine Methode im *Stringer.dll*-Modul, das in Schritt 1 erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="f262c-117">In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.</span></span>

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports System
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. <span data-ttu-id="f262c-118">Verwenden Sie folgenden Befehl, um diesen Code zu kompilieren:</span><span class="sxs-lookup"><span data-stu-id="f262c-118">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   <span data-ttu-id="f262c-119">Verwenden Sie die Option **/t:module**, da dieses Modul in einem späteren Schritt zu einer Assembly hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="f262c-119">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="f262c-120">Legen Sie die Option **/addmodule** fest, da der Code in *Client* auf einen Namespace verweist, der vom Code in *Stringer.netmodule* erzeugt wurde.</span><span class="sxs-lookup"><span data-stu-id="f262c-120">Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*.</span></span> <span data-ttu-id="f262c-121">Der Compiler erzeugt ein Modul mit dem Namen *Client.netmodule*, das einen Verweis auf ein anderes Modul namens *Stringer.netmodule* enthält.</span><span class="sxs-lookup"><span data-stu-id="f262c-121">The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="f262c-122">Die C#- und Visual Basic-Compiler unterstützen das direkte Erstellen von Mehrfachdateiassemblys unter Verwendung der beiden folgenden unterschiedlichen Syntaxformen.</span><span class="sxs-lookup"><span data-stu-id="f262c-122">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
   >
   > <span data-ttu-id="f262c-123">Zwei Kompilierungen erzeugen eine aus zwei Dateien bestehende Assembly:</span><span class="sxs-lookup"><span data-stu-id="f262c-123">Two compilations create a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > <span data-ttu-id="f262c-124">Eine Kompilierung erzeugt eine aus zwei Dateien bestehende Assembly:</span><span class="sxs-lookup"><span data-stu-id="f262c-124">One compilation creates a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. <span data-ttu-id="f262c-125">Erstellen Sie mit dem [Assembly Linker-Tool (Al.exe)](../tools/al-exe-assembly-linker.md) eine Ausgabedatei, die das Assemblymanifest enthält.</span><span class="sxs-lookup"><span data-stu-id="f262c-125">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="f262c-126">In dieser Datei sind Referenzinformationen zu allen zur Assembly gehörenden Modulen und Ressourcen enthalten.</span><span class="sxs-lookup"><span data-stu-id="f262c-126">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="f262c-127">Geben Sie an der Eingabeaufforderung folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="f262c-127">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="f262c-128">**al** \<*modulname*> \<*modulname*> …</span><span class="sxs-lookup"><span data-stu-id="f262c-128">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="f262c-129">**/main:** \<*Methodenname*>  **/out:** \<*Dateiname*>  **/target:** \<*Assemblydateityp*></span><span class="sxs-lookup"><span data-stu-id="f262c-129">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="f262c-130">In diesem Befehl bezeichnen die *Modulname*-Argumente die Namen aller Module, die in der Assembly enthalten sein sollen.</span><span class="sxs-lookup"><span data-stu-id="f262c-130">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="f262c-131">Die Option **/main:** gibt den Methodennamen an, der den Einstiegspunkt der Assembly darstellt.</span><span class="sxs-lookup"><span data-stu-id="f262c-131">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="f262c-132">Die Option **/out:** gibt den Namen der Ausgabedatei an, die Assemblymetadaten enthält.</span><span class="sxs-lookup"><span data-stu-id="f262c-132">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="f262c-133">Die Option **/target:** gibt an, dass die Assembly eine ausführbare Datei für eine Konsolenanwendung ( *.exe*), eine ausführbare Windows-Datei ( *.win*) oder eine Bibliothek ist ( *.lib*).</span><span class="sxs-lookup"><span data-stu-id="f262c-133">The **/target:** option specifies that the assembly is a console application executable (*.exe*) file, a Windows executable (*.win*) file, or a library (*.lib*) file.</span></span>

    <span data-ttu-id="f262c-134">Im folgenden Beispiel erstellt *Al.exe* eine Assembly mit dem Namen *myAssembly.exe*, die eine ausführbare Datei für eine Konsolenanwendung ist.</span><span class="sxs-lookup"><span data-stu-id="f262c-134">In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*.</span></span> <span data-ttu-id="f262c-135">Die Anwendung besteht aus den zwei Modulen *Client.netmodule* und *Stringer.netmodule* sowie der ausführbaren Datei *myAssembly.exe*, die ausschließlich Assemblymetadaten enthält.</span><span class="sxs-lookup"><span data-stu-id="f262c-135">The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata.</span></span> <span data-ttu-id="f262c-136">Der Einstiegspunkt der Assembly ist die `Main`-Methode in der `MainClientApp`-Klasse, die sich in der *Client.dll* befindet.</span><span class="sxs-lookup"><span data-stu-id="f262c-136">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.</span></span>

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="f262c-137">Sie können das [MSIL Disassembler-Tool (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) verwenden, um den Inhalt einer Assembly zu untersuchen oder um zu bestimmen, ob es sich bei einer Datei um eine Assembly oder ein Modul handelt.</span><span class="sxs-lookup"><span data-stu-id="f262c-137">You can use the [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="f262c-138">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f262c-138">See also</span></span>

- [<span data-ttu-id="f262c-139">Erstellen von Assemblys</span><span class="sxs-lookup"><span data-stu-id="f262c-139">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="f262c-140">Vorgehensweise: Anzeigen des Assemblyinhalts</span><span class="sxs-lookup"><span data-stu-id="f262c-140">How to: View assembly contents</span></span>](../../standard/assembly/view-contents.md)
- [<span data-ttu-id="f262c-141">So sucht Common Language Runtime nach Assemblys</span><span class="sxs-lookup"><span data-stu-id="f262c-141">How the runtime locates assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="f262c-142">Mehrfachdateiassemblys</span><span class="sxs-lookup"><span data-stu-id="f262c-142">Multifile assemblies</span></span>](multifile-assemblies.md)