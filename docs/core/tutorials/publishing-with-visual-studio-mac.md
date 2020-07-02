---
title: Veröffentlichen einer .NET Core-Konsolenanwendung mit Visual Studio für Mac
description: Bei der Veröffentlichung werden die Dateien erstellt, die zum Ausführen Ihrer .NET Core-Anwendung benötigt werden.
ms.date: 06/08/2020
ms.openlocfilehash: 67762481d3a56b8473e643f71b8df909b6e54fc6
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713352"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="60dab-103">Tutorial: Veröffentlichen einer .NET Core-Konsolenanwendung mit Visual Studio für Mac</span><span class="sxs-lookup"><span data-stu-id="60dab-103">Tutorial: Publish a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="60dab-104">In diesem Tutorial wird gezeigt, wie eine Konsolen-App veröffentlicht wird, damit sie von anderen Benutzern ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="60dab-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="60dab-105">Die Veröffentlichung erstellt eine Reihe von Dateien, die zum Ausführen Ihrer Anwendung benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="60dab-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="60dab-106">Zum Bereitstellen der Dateien kopieren Sie diese auf den Zielcomputer.</span><span class="sxs-lookup"><span data-stu-id="60dab-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="60dab-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="60dab-107">Prerequisites</span></span>

- <span data-ttu-id="60dab-108">Dieses Tutorial funktioniert mit der Konsolen-App, die Sie in [Erstellen einer .NET Core-Konsolenanwendung in Visual Studio für Mac](with-visual-studio-mac.md) erstellen.</span><span class="sxs-lookup"><span data-stu-id="60dab-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="60dab-109">Veröffentlichen der App</span><span class="sxs-lookup"><span data-stu-id="60dab-109">Publish the app</span></span>

1. <span data-ttu-id="60dab-110">Starten Sie Visual Studio für Mac.</span><span class="sxs-lookup"><span data-stu-id="60dab-110">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="60dab-111">Öffnen Sie das Projekt HelloWorld, das Sie in [Erstellen einer .NET Core-Konsolenanwendung in Visual Studio für Mac](with-visual-studio-mac.md) erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="60dab-111">Open the HelloWorld project that you created in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="60dab-112">Stellen Sie sicher, dass Visual Studio die endgültige Produktversion der Anwendung erstellt.</span><span class="sxs-lookup"><span data-stu-id="60dab-112">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="60dab-113">Ändern Sie ggf. die Einstellung der Buildkonfiguration auf der Symbolleiste von **Debuggen** in **Freigabe**.</span><span class="sxs-lookup"><span data-stu-id="60dab-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="Visual Studio-Symbolleiste mit ausgewähltem Releasebuild":::

1. <span data-ttu-id="60dab-115">Wählen Sie im Hauptmenü **Build** > **In Ordner veröffentlichen...** aus.</span><span class="sxs-lookup"><span data-stu-id="60dab-115">From the main menu, choose **Build** > **Publish to Folder...**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Visual Studio-Kontextmenü „Veröffentlichen“":::

1. <span data-ttu-id="60dab-117">Wählen Sie im Dialogfeld **In Ordner veröffentlichen** den Befehl **Veröffentlichen** aus.</span><span class="sxs-lookup"><span data-stu-id="60dab-117">In the **Publish to Folder** dialog, select **Publish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Visual Studio-Dialogfeld „In Ordner veröffentlichen“":::

   <span data-ttu-id="60dab-119">Der Ordner „publish“ wird mit den erstellten Dateien geöffnet.</span><span class="sxs-lookup"><span data-stu-id="60dab-119">The publish folder opens, showing the files that were created.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="Ordner „publish“":::

1. <span data-ttu-id="60dab-121">Wählen Sie das Zahnradsymbol und dann im Kontextmenü **„publish“ als Pfadname kopieren**.</span><span class="sxs-lookup"><span data-stu-id="60dab-121">Select the gear icon, and select **Copy "publish" as Pathname** from the context menu.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="Kopieren des Pfads zum Ordner „publish“":::

## <a name="inspect-the-files"></a><span data-ttu-id="60dab-123">Untersuchen der Dateien</span><span class="sxs-lookup"><span data-stu-id="60dab-123">Inspect the files</span></span>

<span data-ttu-id="60dab-124">Der Veröffentlichungsprozess erstellt eine frameworkabhängige Bereitstellung. Dies ist ein Bereitstellungstyp, bei dem die veröffentlichte Anwendung auf einem Computer ausgeführt werden kann, auf dem die .NET Core Runtime installiert ist.</span><span class="sxs-lookup"><span data-stu-id="60dab-124">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="60dab-125">Benutzer können die veröffentlichte App ausführen, indem sie an einer Eingabeaufforderung den Befehl `dotnet HelloWorld.dll` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="60dab-125">Users can run the published app by running the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="60dab-126">Wie in der vorherigen Abbildung gezeigt, enthält die veröffentlichte Ausgabe die folgenden Dateien:</span><span class="sxs-lookup"><span data-stu-id="60dab-126">As the preceding image shows, the published output includes the following files:</span></span>

* <span data-ttu-id="60dab-127">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="60dab-127">*HelloWorld.deps.json*</span></span>

  <span data-ttu-id="60dab-128">Dies ist Datei für Runtimeabhängigkeiten der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="60dab-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="60dab-129">In dieser werden die Komponenten und Bibliotheken (einschließlich der Dynamic Link Library, die Ihre Anwendung enthält) von .NET Core definiert, die zum Ausführen der App erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="60dab-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="60dab-130">Weitere Informationen finden Sie unter [Konfigurationsdateien der Runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="60dab-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

* <span data-ttu-id="60dab-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="60dab-131">*HelloWorld.dll*</span></span>

   <span data-ttu-id="60dab-132">Dies ist die [frameworkabhängige Bereitstellungsversion](../deploying/deploy-with-cli.md#framework-dependent-deployment) der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="60dab-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="60dab-133">Um diese Dynamic Link Library (DLL) auszuführen, geben Sie an einer Eingabeaufforderung `dotnet HelloWorld.dll` ein.</span><span class="sxs-lookup"><span data-stu-id="60dab-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="60dab-134">Diese Methode zum Ausführen der App funktioniert auf allen Plattformen, auf denen die .NET Core-Runtime installiert ist.</span><span class="sxs-lookup"><span data-stu-id="60dab-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

* <span data-ttu-id="60dab-135">*HelloWorld.pdb* (optional für die Bereitstellung)</span><span class="sxs-lookup"><span data-stu-id="60dab-135">*HelloWorld.pdb* (optional for deployment)</span></span>

   <span data-ttu-id="60dab-136">Dies ist die Debugsymboldatei.</span><span class="sxs-lookup"><span data-stu-id="60dab-136">This is the debug symbols file.</span></span> <span data-ttu-id="60dab-137">Sie müssen die Datei nicht zusammen mit der Anwendung bereitstellen, obwohl Sie sie speichern sollten für den Fall, dass Sie die veröffentlichte Version der Anwendung debuggen müssen.</span><span class="sxs-lookup"><span data-stu-id="60dab-137">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

* <span data-ttu-id="60dab-138">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="60dab-138">*HelloWorld.runtimeconfig.json*</span></span>

   <span data-ttu-id="60dab-139">Dies ist die Runtimekonfigurationsdatei der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="60dab-139">This is the application's run-time configuration file.</span></span> <span data-ttu-id="60dab-140">Diese Datei identifiziert die Version von .NET Core, für die Ihre Anwendung erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="60dab-140">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="60dab-141">Außerdem können Sie Konfigurationsoptionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="60dab-141">You can also add configuration options to it.</span></span> <span data-ttu-id="60dab-142">Weitere Informationen finden Sie unter [Konfigurationseinstellungen für die .NET Core-Runtime](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="60dab-142">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="60dab-143">Ausführen der veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="60dab-143">Run the published app</span></span>

1. <span data-ttu-id="60dab-144">Öffnen Sie ein Terminal, und navigieren Sie zum Ordner *publish*.</span><span class="sxs-lookup"><span data-stu-id="60dab-144">Open a terminal and navigate to the *publish* folder.</span></span> <span data-ttu-id="60dab-145">Geben Sie dazu `cd` ein, und fügen Sie dann den zuvor kopierten Pfad ein.</span><span class="sxs-lookup"><span data-stu-id="60dab-145">To do that, enter `cd` and then paste the path that you copied earlier.</span></span> <span data-ttu-id="60dab-146">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="60dab-146">For example:</span></span>

   ```
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/netcoreapp3.1/publish/
   ```

1. <span data-ttu-id="60dab-147">Führen Sie die App mit dem Befehl `dotnet` aus:</span><span class="sxs-lookup"><span data-stu-id="60dab-147">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="60dab-148">Geben Sie `dotnet HelloWorld.dll` ein, und drücken Sie die <kbd>EINGABETASTE</kbd>.</span><span class="sxs-lookup"><span data-stu-id="60dab-148">Enter `dotnet HelloWorld.dll` and press <kbd>enter</kbd>.</span></span>

   1. <span data-ttu-id="60dab-149">Geben Sie als Antwort auf die Eingabeaufforderung einen Namen ein, und drücken Sie zum Beenden eine beliebige Taste.</span><span class="sxs-lookup"><span data-stu-id="60dab-149">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="60dab-150">Zusätzliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="60dab-150">Additional resources</span></span>

- [<span data-ttu-id="60dab-151">.NET Core-Anwendungsbereitstellung</span><span class="sxs-lookup"><span data-stu-id="60dab-151">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="60dab-152">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="60dab-152">Next steps</span></span>

<span data-ttu-id="60dab-153">In diesem Tutorial haben Sie eine Konsolen-App veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="60dab-153">In this tutorial, you published a console app.</span></span> <span data-ttu-id="60dab-154">Im nächsten Tutorial erstellen Sie eine Klassenbibliothek.</span><span class="sxs-lookup"><span data-stu-id="60dab-154">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="60dab-155">Erstellen einer .NET Standard-Bibliothek in Visual Studio für Mac</span><span class="sxs-lookup"><span data-stu-id="60dab-155">Create a .NET Standard library in Visual Studio for mac</span></span>](library-with-visual-studio-mac.md)