---
title: Erstellen einer .NET Standard-Klassenbibliothek in Visual Studio
description: Erfahren Sie, wie Sie eine .NET Standard-Klassenbibliothek mit Visual Studio erstellen.
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperfq1
ms.openlocfilehash: 45a44dcd73e1abcc8dfd75cd54da5a2310f027c4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118259"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a>Tutorial: Erstellen einer .NET-Standard-Bibliothek in Visual Studio

In diesem Tutorial erstellen Sie eine einfache Klassenbibliothek, die eine einzelne Methode zur Behandlung von Zeichenfolgen enthält.

Eine *Klassenbibliothek* definiert die Typen und Methoden, die von einer Anwendung aufgerufen werden können. Eine Klassenbibliothek, die sich auf .NET Standard 2.0 bezieht, ermöglicht das Aufrufen der Bibliothek aus jeder .NET-Implementierung, die diese Version von .NET Standard unterstützt.

Wenn Sie Ihre Klassenbibliothek fertig gestellt haben, können Sie diese als NuGet-Paket oder als mit der zugehörigen Anwendung gebündelte Komponente ausliefern.

## <a name="prerequisites"></a>Voraussetzungen

- [Visual Studio 2019 Version 16.6 oder höher](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) mit installierter Workload **Plattformübergreifende .NET Core-Entwicklung**. Das .NET Core 3.1 SDK wird automatisch installiert, wenn Sie diese Workload auswählen.

## <a name="create-a-solution"></a>Erstellen einer Projektmappe

Beginnen Sie, indem Sie eine leere Projektmappe erstellen, um das Klassenbibliotheksprojekt darin zu speichern. Eine Visual Studio-Projektmappe dient als ein Container für mindestens ein Projekt. Sie fügen der gleichen Projektmappe weitere verwandte Projekte hinzu.

So erstellen Sie eine leere Projektmappe:

1. Starten Sie Visual Studio.

2. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

3. Geben Sie auf der Seite **Neues Projekt erstellen** die Angabe **Projektmappe** in das Suchfeld ein. Wählen Sie die Vorlage **Leere Projektmappe** aus, und klicken Sie dann auf **Weiter**.

   ![Vorlage „Leere Projektmappe“ in Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. Geben Sie im auf der Seite **Neues Projekt konfigurieren** im Feld **Projektname** den Namen **ClassLibraryProjects** ein. Wählen Sie dann **Erstellen** aus.

## <a name="create-a-class-library-project"></a>Erstellen eines Klassenbibliotheksprojekts

1. Fügen Sie der Projektmappe ein neues .NET Standard-Klassenbibliotheksprojekt mit dem Namen „StringLibrary“ hinzu.

   1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Hinzufügen** > **Neues Projekt** aus.

   1. Geben Sie auf der Seite **Neues Projekt hinzufügen** **library** in das Suchfeld ein. Wählen Sie **C#** oder **Visual Basic** in der Liste der Sprachen und dann in der Liste der Plattformen **Alle Plattformen** aus. Wählen Sie die Vorlage **Klassenbibliothek (.NET Standard)** aus, und wählen Sie dann **Weiter**aus.

   1. Geben Sie im auf der Seite **Neues Projekt konfigurieren** im Feld **Projektname** den Namen **StringLibrary** ein. Wählen Sie anschließend **Erstellen** aus.

1. Stellen Sie sicher, dass die Bibliothek die richtige Version von .NET Standard als Ziel verwendet. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Bibliotheksprojekt, und klicken Sie dann auf **Eigenschaften**. Das Textfeld **Zielframework** zeigt dann, dass .NET Standard 2.0 als Ziel verwendet wird.

   ![Projekteigenschaften für die Klassenbibliothek](./media/library-with-visual-studio/library-project-properties.png)

1. Wenn Sie Visual Basic verwenden, löschen Sie den Text im Textfeld **Stammnamespace**.

   ![Projekteigenschaften für die Klassenbibliothek](./media/library-with-visual-studio/vb/library-project-properties.png)

   Für jedes Projekt erstellt Visual Basic automatisch einen Namespace, der dem Projektnamen entspricht. In diesem Tutorial definieren Sie einen Namespace der obersten Ebene mithilfe des Schlüsselworts [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) in der Codedatei.

1. Ersetzen Sie den Code im Codefenster für *Class1.cs* oder *Class1.vb* durch den folgenden Code, und speichern Sie die Datei. Wenn die gewünschte Sprache nicht angezeigt wird, ändern Sie die Sprachauswahl am oberen Rand der Seite.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   Die Klassenbibliothek (`UtilityLibraries.StringLibrary`) enthält eine Methode namens `StartsWithUpper`. Diese Methode gibt einen <xref:System.Boolean>-Wert zurück, der angibt, ob die aktuelle Zeichenfolgeninstanz mit einem Großbuchstaben beginnt. Der Unicode-Standard unterscheidet Groß- und Kleinschreibung. Die Methode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> gibt `true` zurück, wenn ein Zeichen ein Großbuchstabe ist.

   Die Methode `StartsWithUpper` wird als [Erweiterungsmethode](../../csharp/programming-guide/classes-and-structs/extension-methods.md) implementiert, damit sie wie ein Member der Klasse <xref:System.String> aufgerufen werden kann.

1. Klicken Sie auf der Menüleiste auf **Erstellen** > **Projektmappe erstellen**, oder drücken Sie <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>B</kbd>, um zu bestätigen, dass das Projekt ohne Fehler kompiliert wird.

## <a name="add-a-console-app-to-the-solution"></a>Hinzufügen einer Konsolen-App zur Projektmappe

Im Folgenden fügen Sie eine Konsolenanwendung hinzu, die die Klassenbibliothek verwendet. Die App fordert den Benutzer dazu auf, eine Zeichenfolge einzugeben, und meldet, ob die Zeichenfolge mit einem Großbuchstaben beginnt.

1. Fügen Sie der Projektmappe eine neue .NET Core-Konsolenanwendung mit dem Namen „ShowCase“ hinzu.

   1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Hinzufügen** > **Neues Projekt** aus.

   1. Geben Sie auf der Seite **Neues Projekt hinzufügen** die Angabe **Konsole** in das Suchfeld ein. Wählen Sie **C#** oder **Visual Basic** in der Liste der Sprachen und dann in der Liste der Plattformen **Alle Plattformen** aus.

   1. Wählen Sie die Vorlage **Konsolen-App (.NET Core)** und anschließend **Weiter** aus.

   1. Geben Sie **ShowCase** auf der Seite **Neues Projekt konfigurieren** in das Feld **Projektname** ein. Wählen Sie dann **Erstellen** aus.

1. Ersetzen Sie im Codefenster für die Datei *Program.cs* oder *Program.vb* den gesamten Code durch den folgenden Code.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   Der Code verwendet die `row`-Variable, um die Anzahl der in das Konsolenfenster geschriebenen Datenzeilen festzuhalten. Wenn sie mindestens 25 beträgt, löscht der Code das Konsolenfenster und zeigt eine Meldung für den Benutzer an.

   Das Programm selbst fordert den Benutzer zur Eingabe einer Zeichenfolge auf. Es zeigt an, ob die Zeichenfolge mit einem Großbuchstaben beginnt. Wenn der Benutzer die <kbd>EINGABETASTE</kbd> drückt, ohne eine Zeichenfolge einzugeben, wird die Anwendung beendet und das Konsolenfenster geschlossen.

## <a name="add-a-project-reference"></a>Hinzufügen eines Projektverweises

Anfänglich besitzt das neue Konsolen-App-Projekt keinen Zugriff auf die Klassenbibliothek. Damit es Methoden in der Klassenbibliothek aufrufen kann, erstellen Sie einen Projektverweis auf das Klassenbibliotheksprojekt.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Abhängigkeiten** des `ShowCase`-Projekts, und wählen Sie **Projektverweis hinzufügen** aus.

   ![Kontextmenü „Verweis hinzufügen“ in Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. Wählen Sie im Dialogfeld **Verweis-Manager** das Projekt **StringLibrary** und dann **OK** aus.

   ![Dialogfeld „Verweis-Manager“ mit ausgewählter StringLibrary](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a>Ausführen der App

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das **ShowCase**-Projekt, und wählen Sie **Als Startprojekt festlegen** aus.

   ![Visual Studio-Projektkontextmenü zum Festlegen des Startprojekts](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. Drücken Sie <kbd>STRG</kbd>+<kbd>F5</kbd>, um das Programm ohne Debuggen zu kompilieren und auszuführen.

   ![Visual Studio-Projektsymbolleiste mit Schaltfläche „Debuggen“](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. Testen Sie das Programm, indem Sie Zeichenfolgen eingeben und die <kbd>EINGABETASTE</kbd> drücken, und drücken Sie dann die <kbd>EINGABETASTE</kbd>, um das Programm zu beenden.

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Konsolenfenster, in dem ShowCase ausgeführt wird":::

## <a name="additional-resources"></a>Zusätzliche Ressourcen

* [Entwickeln von Bibliotheken mit der .NET Core-CLI](libraries.md)
* [.NET Standard-Versionen und die von ihnen unterstützten Plattformen](../../standard/net-standard.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie eine Klassenbibliothek erstellt. Im nächsten Tutorial erfahren Sie, wie Sie Komponententests für die Klassenbibliothek ausführen.

> [!div class="nextstepaction"]
> [Durchführen von Komponententests für eine .NET Standard-Bibliothek mithilfe von Visual Studio](testing-library-with-visual-studio.md)

Alternativ können Sie die automatisierten Komponententests auch überspringen und sich damit beschäftigen, wie die Bibliothek durch Erstellen eines NuGet-Pakets freigegeben werden kann:

> [!div class="nextstepaction"]
> [Erstellen und Veröffentlichen eines Pakets mithilfe von Visual Studio](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

Stattdessen können Sie sich auch über das Veröffentlichen einer Konsolen-App informieren. Wenn Sie die Konsolen-App aus der Projektmappe veröffentlichen, die Sie in diesem Tutorial erstellt haben, wird die Klassenbibliothek als *DLL*-Datei veröffentlicht.

> [!div class="nextstepaction"]
> [Veröffentlichen einer .NET Core-Konsolenanwendung in Visual Studio](publishing-with-visual-studio.md)
