---
title: Erhöhte Zugriffsrechte für dotnet-Befehle
description: Erfahren Sie mehr über die Best Practices für dotnet-Befehle, die erhöhte Zugriffsrechte erfordern.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 3d874a76eadbf5330c4e5efe4e86bfeca0a9b504
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410628"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="8e024-103">Erhöhte Zugriffsrechte für dotnet-Befehle</span><span class="sxs-lookup"><span data-stu-id="8e024-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="8e024-104">Durch Best Practices in der Softwareentwicklung schreiben Entwickler Software, für die die geringsten Berechtigungen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="8e024-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="8e024-105">Einige Software, wie z.B. Tools zur Leistungsüberwachung, benötigen jedoch aufgrund von Betriebssystemregeln Administratorrechte.</span><span class="sxs-lookup"><span data-stu-id="8e024-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="8e024-106">Die folgende Anleitung beschreibt unterstützte Szenarien für das Schreiben derartiger Software mit .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e024-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span> 

<span data-ttu-id="8e024-107">Die folgenden Befehle können mit erhöhten Rechten ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="8e024-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="8e024-108">`dotnet tool`-Befehle wie [dotnet tool install](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="8e024-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`

<span data-ttu-id="8e024-109">Wir empfehlen nicht, andere Befehle mit erhöhten Rechten auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8e024-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="8e024-110">Insbesondere empfehlen wir keine Erhöhung der Rechte mit Befehlen, die MSBuild verwenden, wie z.B. [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md) und [dotnet run](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="8e024-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="8e024-111">Das Hauptproblem ist die Berechtigungsverwaltung, wenn ein Benutzer nach der Ausgabe von dotnet-Befehlen zwischen einem Root- und einem eingeschränkten Konto hin und her wechselt.</span><span class="sxs-lookup"><span data-stu-id="8e024-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="8e024-112">Sie stellen als eingeschränkter Benutzer möglicherweise fest, dass Sie keinen Zugriff auf die von einem Root-Benutzer erstellte Datei haben.</span><span class="sxs-lookup"><span data-stu-id="8e024-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="8e024-113">Es gibt Möglichkeiten, diese Situation zu lösen, aber sie sind zunächst unnötig.</span><span class="sxs-lookup"><span data-stu-id="8e024-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="8e024-114">Sie können Befehle als Root ausführen, solange Sie nicht zwischen dem Stammkonto und einem eingeschränkten Konto hin und her wechseln.</span><span class="sxs-lookup"><span data-stu-id="8e024-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="8e024-115">Beispielsweise werden Dockercontainer standardmäßig als Root ausgeführt, daher haben sie dieses Merkmal.</span><span class="sxs-lookup"><span data-stu-id="8e024-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="8e024-116">Installation des globalen Tools</span><span class="sxs-lookup"><span data-stu-id="8e024-116">Global tool installation</span></span>

<span data-ttu-id="8e024-117">Die folgenden Anweisungen zeigen die empfohlene Vorgehensweise bei der Installation, Ausführung und Deinstallation von.NET Core-Tools, die erhöhte Berechtigungen für die Ausführung erfordern.</span><span class="sxs-lookup"><span data-stu-id="8e024-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="8e024-118">Windows</span><span class="sxs-lookup"><span data-stu-id="8e024-118">Windows</span></span>](#tab/windows)

### <a name="install-the-global-tool"></a><span data-ttu-id="8e024-119">Installieren des globalen Tools</span><span class="sxs-lookup"><span data-stu-id="8e024-119">Install the global tool</span></span>

<span data-ttu-id="8e024-120">Wenn der Ordner `%ProgramFiles%\dotnet-tools` bereits vorhanden ist, überprüfen Sie anhand der folgenden Schritte, ob die Gruppe „Benutzer“ die Berechtigung hat, dieses Verzeichnis zu schreiben oder zu ändern:</span><span class="sxs-lookup"><span data-stu-id="8e024-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

* <span data-ttu-id="8e024-121">Klicken Sie mit der rechten Maustaste auf den Ordner `%ProgramFiles%\dotnet-tools`, und wählen Sie **Eigenschaften** aus.</span><span class="sxs-lookup"><span data-stu-id="8e024-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="8e024-122">Das Dialogfeld **Allgemeine Eigenschaften** wird geöffnet.</span><span class="sxs-lookup"><span data-stu-id="8e024-122">The **Common Properties** dialog box opens.</span></span> 
* <span data-ttu-id="8e024-123">Wählen Sie die Registerkarte **Sicherheit** aus. Überprüfen Sie unter **Gruppen-oder Benutzernamen**, ob die Gruppe „Benutzer“ die Berechtigung hat, dieses Verzeichnis zu schreiben oder zu ändern.</span><span class="sxs-lookup"><span data-stu-id="8e024-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span> 
* <span data-ttu-id="8e024-124">Wenn die Gruppe „Benutzer“ das Verzeichnis schreiben oder ändern kann, verwenden Sie bei der Installation der Tools einen anderen Verzeichnisnamen als *dotnet-tools*.</span><span class="sxs-lookup"><span data-stu-id="8e024-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="8e024-125">Führen Sie den folgenden Befehl in einer Eingabeaufforderung mit erhöhten Rechten aus, um Tools zu installieren.</span><span class="sxs-lookup"><span data-stu-id="8e024-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="8e024-126">Damit wird während der Installation der Ordner *dotnet-tools* erstellt.</span><span class="sxs-lookup"><span data-stu-id="8e024-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```cmd
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="8e024-127">Ausführen des globalen Tools</span><span class="sxs-lookup"><span data-stu-id="8e024-127">Run the global tool</span></span>

<span data-ttu-id="8e024-128">**Option 1** Verwenden des vollständigen Pfads in einer Eingabeaufforderung mit erhöhten Rechten:</span><span class="sxs-lookup"><span data-stu-id="8e024-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="8e024-129">**Option 2** Hinzufügen des neu erstellten Ordners zu `%Path%`.</span><span class="sxs-lookup"><span data-stu-id="8e024-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="8e024-130">Dieser Vorgang ist nur einmalig erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8e024-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="8e024-131">Und ausführen mit:</span><span class="sxs-lookup"><span data-stu-id="8e024-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="8e024-132">Deinstallieren des globalen Tools</span><span class="sxs-lookup"><span data-stu-id="8e024-132">Uninstall the global tool</span></span>

<span data-ttu-id="8e024-133">Geben Sie in der Eingabeaufforderung mit erhöhten Rechten folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="8e024-133">In an elevated prompt, type the following command:</span></span>

```cmd
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linuxtablinux"></a>[<span data-ttu-id="8e024-134">Linux</span><span class="sxs-lookup"><span data-stu-id="8e024-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macostabmacos"></a>[<span data-ttu-id="8e024-135">macOS</span><span class="sxs-lookup"><span data-stu-id="8e024-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="8e024-136">Lokale Tools</span><span class="sxs-lookup"><span data-stu-id="8e024-136">Local tools</span></span>

<span data-ttu-id="8e024-137">Lokale Tools werden pro Unterverzeichnisstruktur und Benutzer definiert.</span><span class="sxs-lookup"><span data-stu-id="8e024-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="8e024-138">Wenn die lokalen Tools mit erhöhten Rechten ausgeführt werden, verwenden sie eine eingeschränkte Benutzerumgebung zusammen mit der Umgebung mit erhöhten Rechten.</span><span class="sxs-lookup"><span data-stu-id="8e024-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="8e024-139">In Linux und MacOS führt dies dazu, dass auf Dateien nur mit Root-Benutzerzugriff zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="8e024-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="8e024-140">Wenn der Benutzer zu einem eingeschränkten Konto zurückkehrt, kann der Benutzer nicht mehr auf die Dateien zugreifen oder in diese schreiben.</span><span class="sxs-lookup"><span data-stu-id="8e024-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="8e024-141">Daher wird die Installation von Tools, die höhere Rechte als lokale Tools erfordern, nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="8e024-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="8e024-142">Verwenden Sie stattdessen die Option `--tool-path` und die vorherigen Richtlinien für globale Tools.</span><span class="sxs-lookup"><span data-stu-id="8e024-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="8e024-143">Erhöhung der Rechte während der Entwicklung</span><span class="sxs-lookup"><span data-stu-id="8e024-143">Elevation during development</span></span>

<span data-ttu-id="8e024-144">Während der Entwicklung benötigen Sie möglicherweise erhöhte Zugriffsrechte, um Ihre Anwendung zu testen.</span><span class="sxs-lookup"><span data-stu-id="8e024-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="8e024-145">Dieses Szenario ist z.B. bei IoT-Apps üblich.</span><span class="sxs-lookup"><span data-stu-id="8e024-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="8e024-146">Wir empfehlen Ihnen, die Anwendung ohne Erhöhung der Rechte zu erstellen und sie dann mit erhöhten Rechten auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8e024-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="8e024-147">Es gibt einige Muster, wie z.B.:</span><span class="sxs-lookup"><span data-stu-id="8e024-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="8e024-148">Verwenden generierter ausführbaren Dateien (die bietet die beste Leistung beim Start):</span><span class="sxs-lookup"><span data-stu-id="8e024-148">Using generated executable (it provides the best startup performance):</span></span>

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- <span data-ttu-id="8e024-149">Verwenden des Befehls [dotnet run](dotnet-run.md) mit dem Flag `—no-build`, um das Generieren neuer Binärdateien zu vermeiden:</span><span class="sxs-lookup"><span data-stu-id="8e024-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="8e024-150">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8e024-150">See also</span></span>

* [<span data-ttu-id="8e024-151">Übersicht über globale .NET Core-Tools</span><span class="sxs-lookup"><span data-stu-id="8e024-151">.NET Core Global Tools overview</span></span>](global-tools.md)