---
title: 'Tutorial: Kategorisieren von Supportproblemen (Multiklassenklassifizierung)'
description: Erfahren Sie hier, wie Sie mit ML.NET in einem Szenario zur Multiklassenklassifizierung GitHub-Issues klassifizieren, um sie einem bestimmten Bereich zuzuweisen.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: fa00306e80046097c1269533d3a3ca1e85f10288
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679494"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a><span data-ttu-id="a82f1-103">Tutorial: Kategorisieren von Supportproblemen unter Verwendung von Multiklassenklassifizierung mit ML.NET</span><span class="sxs-lookup"><span data-stu-id="a82f1-103">Tutorial: Categorize support issues using multiclass classification with ML.NET</span></span>

<span data-ttu-id="a82f1-104">In diesem Beispieltutorial wird veranschaulicht, wie Sie ML.NET zum Erstellen eines Klassifizierers für GitHub-Issues über eine .NET Core-Konsolenanwendung mithilfe von C# in Visual Studio verwenden können, um ein Modell zu trainieren, dass die Bereichsbezeichnung für ein GitHub-Issue klassifiziert und vorhersagt.</span><span class="sxs-lookup"><span data-stu-id="a82f1-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="a82f1-105">In diesem Tutorial lernen Sie, wie die folgenden Aufgaben ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="a82f1-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="a82f1-106">Vorbereiten Ihrer Daten</span><span class="sxs-lookup"><span data-stu-id="a82f1-106">Prepare your data</span></span>
> * <span data-ttu-id="a82f1-107">Transformieren der Daten</span><span class="sxs-lookup"><span data-stu-id="a82f1-107">Transform the data</span></span>
> * <span data-ttu-id="a82f1-108">Trainieren des Modells</span><span class="sxs-lookup"><span data-stu-id="a82f1-108">Train the model</span></span>
> * <span data-ttu-id="a82f1-109">Evaluieren des Modells</span><span class="sxs-lookup"><span data-stu-id="a82f1-109">Evaluate the model</span></span>
> * <span data-ttu-id="a82f1-110">Vorhersagen treffen mit dem trainierten Modell</span><span class="sxs-lookup"><span data-stu-id="a82f1-110">Predict with the trained model</span></span>
> * <span data-ttu-id="a82f1-111">Bereitstellen eines geladenen Modells und Vorhersagen mit diesem treffen</span><span class="sxs-lookup"><span data-stu-id="a82f1-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="a82f1-112">Sie finden den Quellcode für dieses Tutorial im Repository [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).</span><span class="sxs-lookup"><span data-stu-id="a82f1-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a82f1-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="a82f1-113">Prerequisites</span></span>

* <span data-ttu-id="a82f1-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) oder höher oder Visual Studio 2017 Version 15.6 oder höher mit installierter Workload „Plattformübergreifende .NET Core-Entwicklung“.</span><span class="sxs-lookup"><span data-stu-id="a82f1-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* <span data-ttu-id="a82f1-115">Die [durch Tabstopp getrennte Datei mit GitHub-Issues (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="a82f1-115">The [GitHub issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="a82f1-116">Die [durch Tabstopp getrennte Testdatei für GitHub-Issues (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="a82f1-116">The [GitHub issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="a82f1-117">Erstellen einer Konsolenanwendung</span><span class="sxs-lookup"><span data-stu-id="a82f1-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="a82f1-118">Erstellen eines Projekts</span><span class="sxs-lookup"><span data-stu-id="a82f1-118">Create a project</span></span>

1. <span data-ttu-id="a82f1-119">Öffnen Sie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a82f1-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="a82f1-120">Wählen Sie **Datei** > **Neu** > **Projekt** aus der Menüleiste aus.</span><span class="sxs-lookup"><span data-stu-id="a82f1-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="a82f1-121">Wählen Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C#** und anschließend den Knoten **.NET Core** aus.</span><span class="sxs-lookup"><span data-stu-id="a82f1-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="a82f1-122">Klicken Sie dann auf die Projektvorlage **Konsolen-App (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="a82f1-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="a82f1-123">Geben Sie „GitHubIssueClassification“ im Textfeld **Name** ein, und wählen Sie die Schaltfläche **OK** aus.</span><span class="sxs-lookup"><span data-stu-id="a82f1-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="a82f1-124">Erstellen Sie ein Verzeichnis mit dem Namen *Data* in Ihrem Projekt, um die Datasetdateien zu speichern:</span><span class="sxs-lookup"><span data-stu-id="a82f1-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="a82f1-125">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Hinzufügen** > **Neuer Ordner** aus.</span><span class="sxs-lookup"><span data-stu-id="a82f1-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="a82f1-126">Geben Sie „Data“ ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="a82f1-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="a82f1-127">Erstellen Sie ein Verzeichnis mit dem Namen *Models* in Ihrem Projekt, um Ihr Modell zu speichern:</span><span class="sxs-lookup"><span data-stu-id="a82f1-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="a82f1-128">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Hinzufügen** > **Neuer Ordner** aus.</span><span class="sxs-lookup"><span data-stu-id="a82f1-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="a82f1-129">Geben Sie „Models“ ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="a82f1-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="a82f1-130">Installieren des **Microsoft.ML NuGet-Pakets**:</span><span class="sxs-lookup"><span data-stu-id="a82f1-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="a82f1-131">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **NuGet-Pakete verwalten** aus.</span><span class="sxs-lookup"><span data-stu-id="a82f1-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="a82f1-132">Wählen Sie als Paketquelle „nuget.org“ aus. Klicken Sie dann auf die Registerkarte „Durchsuchen“ aus, suchen Sie nach **Microsoft.ML**, und klicken Sie anschließend auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="a82f1-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="a82f1-133">Wählen Sie die Schaltfläche **OK** im Dialogfeld **Vorschau der Änderungen** und dann die Schaltfläche **Ich stimme zu** im Dialogfeld **Zustimmung zur Lizenz** aus, wenn Sie den Lizenzbedingungen für die aufgelisteten Pakete zustimmen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="a82f1-134">Vorbereiten Ihrer Daten</span><span class="sxs-lookup"><span data-stu-id="a82f1-134">Prepare your data</span></span>

1. <span data-ttu-id="a82f1-135">Laden Sie die Datasets [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) und [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) herunter, und speichern Sie sie im zuvor erstellten Ordner *Daten*.</span><span class="sxs-lookup"><span data-stu-id="a82f1-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="a82f1-136">Das erste Dataset trainiert das Machine Learning-Modell, und das zweite kann verwendet werden, um zu evaluieren, wie genau das Modell ist.</span><span class="sxs-lookup"><span data-stu-id="a82f1-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="a82f1-137">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die \*.tsv-Dateien, und wählen Sie **Eigenschaften** aus.</span><span class="sxs-lookup"><span data-stu-id="a82f1-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="a82f1-138">Ändern Sie unter **Erweitert** den Wert von **In Ausgabeverzeichnis kopieren** in **Kopieren, wenn neuer**.</span><span class="sxs-lookup"><span data-stu-id="a82f1-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="a82f1-139">Erstellen von Klassen und Definieren von Pfaden</span><span class="sxs-lookup"><span data-stu-id="a82f1-139">Create classes and define paths</span></span>

<span data-ttu-id="a82f1-140">Fügen Sie am Anfang der Datei *Program.cs* folgende zusätzliche `using`-Anweisungen hinzu:</span><span class="sxs-lookup"><span data-stu-id="a82f1-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](./snippets/github-issue-classification/csharp/Program.cs#AddUsings)]

<span data-ttu-id="a82f1-141">Erstellen Sie drei globale Felder, die die Pfade zu den zuletzt heruntergeladenen Dateien sowie globale Variablen für `MLContext`, `DataView` und `PredictionEngine` enthalten:</span><span class="sxs-lookup"><span data-stu-id="a82f1-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="a82f1-142">`_trainDataPath` enthält den Pfad zu dem Dataset, das zum Trainieren des Modells verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a82f1-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="a82f1-143">`_testDataPath` enthält den Pfad zu dem Dataset, das zum Evaluieren des Modells verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a82f1-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="a82f1-144">`_modelPath` enthält den Pfad zu dem Speicherort, in dem das trainierte Modell gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="a82f1-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="a82f1-145">`_mlContext` ist die <xref:Microsoft.ML.MLContext>-Klasse, die den Verarbeitungskontext enthält.</span><span class="sxs-lookup"><span data-stu-id="a82f1-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="a82f1-146">`_trainingDataView` ist die zum Verarbeiten des Trainingsdatasets verwendete <xref:Microsoft.ML.IDataView>-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="a82f1-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="a82f1-147">`_predEngine` ist die für einzelne Vorhersagen verwendete <xref:Microsoft.ML.PredictionEngine%602>-Klasse.</span><span class="sxs-lookup"><span data-stu-id="a82f1-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="a82f1-148">Fügen Sie den folgenden Code der Zeile direkt über der `Main`-Methode hinzu, um diese Pfade und die anderen Variablen anzugeben:</span><span class="sxs-lookup"><span data-stu-id="a82f1-148">Add the following code to the line directly above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](./snippets/github-issue-classification/csharp/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="a82f1-149">Erstellen Sie einige Klassen für Ihre Eingabedaten und Vorhersagen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="a82f1-150">Fügen Sie dem Projekt eine neue Klasse hinzu:</span><span class="sxs-lookup"><span data-stu-id="a82f1-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="a82f1-151">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Hinzufügen** > **Neues Element** aus.</span><span class="sxs-lookup"><span data-stu-id="a82f1-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="a82f1-152">Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Klasse** aus, und ändern Sie das Feld **Name** in *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="a82f1-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="a82f1-153">Wählen Sie dann die Schaltfläche **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="a82f1-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="a82f1-154">Die Datei *GitHubIssueData.cs* wird im Code-Editor geöffnet.</span><span class="sxs-lookup"><span data-stu-id="a82f1-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="a82f1-155">Fügen Sie am Anfang der Datei *GitHubIssueData.cs* die folgende `using`-Anweisung hinzu:</span><span class="sxs-lookup"><span data-stu-id="a82f1-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](./snippets/github-issue-classification/csharp/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="a82f1-156">Entfernen Sie die vorhandene Klassendefinition, und fügen Sie der Datei *GitHubIssueData.cs* den folgenden Code mit den beiden Klassen `GitHubIssue` und `IssuePrediction` hinzu:</span><span class="sxs-lookup"><span data-stu-id="a82f1-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](./snippets/github-issue-classification/csharp/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="a82f1-157">`label` ist die Spalte, die vorhergesagt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a82f1-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="a82f1-158">Die identifizierten `Features` sind die Eingaben, die Sie für das Modell zum Vorhersagen der Bezeichnung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="a82f1-159">Verwenden Sie das [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute), um die Indizes der Quellspalten im Dataset festzulegen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="a82f1-160">`GitHubIssue` ist die Klasse des Eingabedatasets mit den folgenden <xref:System.String>-Feldern:</span><span class="sxs-lookup"><span data-stu-id="a82f1-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="a82f1-161">Die erste Spalte: `ID` (ID des GitHub-Issues)</span><span class="sxs-lookup"><span data-stu-id="a82f1-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="a82f1-162">Die zweite Spalte: `Area` (Vorhersage für das Training)</span><span class="sxs-lookup"><span data-stu-id="a82f1-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="a82f1-163">Die dritte Spalte `Title` (Titel des GitHub-Issues) ist das erste `feature` zur Vorhersage von `Area`</span><span class="sxs-lookup"><span data-stu-id="a82f1-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="a82f1-164">Die vierte Spalte `Description` ist das zweite `feature` für die Vorhersage von `Area`</span><span class="sxs-lookup"><span data-stu-id="a82f1-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="a82f1-165">Die `IssuePrediction`-Klasse wird für die Vorhersage verwendet, nachdem das Modell trainiert wurde.</span><span class="sxs-lookup"><span data-stu-id="a82f1-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="a82f1-166">Sie verfügt über ein einzelnes `string`- (`Area`) und ein `PredictedLabel` `ColumnName`-Attribut.</span><span class="sxs-lookup"><span data-stu-id="a82f1-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="a82f1-167">Das `PredictedLabel` wird während der Vorhersage und Evaluierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="a82f1-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="a82f1-168">Für die Evaluierung werden eine Eingabe mit Trainingsdaten, die vorhergesagten Werte und das Modell verwendet.</span><span class="sxs-lookup"><span data-stu-id="a82f1-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="a82f1-169">Alle ML.NET-Operationen beginnen in der [MLContext](xref:Microsoft.ML.MLContext)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="a82f1-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="a82f1-170">Beim Initialisieren von `mlContext` wird eine neue ML.NET-Umgebung erstellt, die für alle Objekte des Workflows für die Modellerstellung gemeinsam genutzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="a82f1-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="a82f1-171">Die Klasse ähnelt dem Konzept von `DBContext` in `Entity Framework`.</span><span class="sxs-lookup"><span data-stu-id="a82f1-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="a82f1-172">Initialisieren von Variablen in Main</span><span class="sxs-lookup"><span data-stu-id="a82f1-172">Initialize variables in Main</span></span>

<span data-ttu-id="a82f1-173">Initialisieren Sie die globale Variable `_mlContext` mit einer neuen Instanz von `MLContext` mit einem zufälligen Ausgangswert (`seed: 0`), um in mehreren Trainings wiederholbare/deterministische Ergebnisse zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a82f1-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="a82f1-174">Ersetzen Sie die Zeile `Console.WriteLine("Hello World!")` mit dem folgenden Code in der `Main`-Methode:</span><span class="sxs-lookup"><span data-stu-id="a82f1-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](./snippets/github-issue-classification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="a82f1-175">Laden der Daten</span><span class="sxs-lookup"><span data-stu-id="a82f1-175">Load the data</span></span>

<span data-ttu-id="a82f1-176">Für ML.NET wird die [IDataView-Klasse](xref:Microsoft.ML.IDataView) als flexible, effiziente Möglichkeit zum Beschreiben von Tabellendaten in Zahlen- oder Textform verwendet.</span><span class="sxs-lookup"><span data-stu-id="a82f1-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="a82f1-177">Mit `IDataView` können entweder Textdateien geladen werden, oder es kann ein Echtzeitladevorgang durchgeführt werden (z.B. SQL-Datenbank- oder Protokolldateien).</span><span class="sxs-lookup"><span data-stu-id="a82f1-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="a82f1-178">Fügen Sie nach der Initialisierung von `mlContext` den folgenden Code hinzu, um die globale Variable `_trainingDataView` zur Verwendung für die Pipeline zu initialisieren und zu laden:</span><span class="sxs-lookup"><span data-stu-id="a82f1-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](./snippets/github-issue-classification/csharp/Program.cs#LoadTrainData)]

<span data-ttu-id="a82f1-179">Die [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29)-Methode definiert das Datenschema und liest die Datei ein.</span><span class="sxs-lookup"><span data-stu-id="a82f1-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="a82f1-180">Diese Methode akzeptiert Datenpfadvariablen und gibt ein `IDataView`-Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="a82f1-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="a82f1-181">Fügen Sie den folgenden Text als nächste Codezeile in die `Main`-Methode ein:</span><span class="sxs-lookup"><span data-stu-id="a82f1-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](./snippets/github-issue-classification/csharp/Program.cs#CallProcessData)]

<span data-ttu-id="a82f1-182">Die `ProcessData`-Methode führt die folgenden Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="a82f1-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="a82f1-183">Extrahieren und Transformieren der Daten.</span><span class="sxs-lookup"><span data-stu-id="a82f1-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="a82f1-184">Zurückgeben der Verarbeitungspipeline</span><span class="sxs-lookup"><span data-stu-id="a82f1-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="a82f1-185">Erstellen Sie die `ProcessData`-Methode mit dem folgenden Code direkt nach der `Main`-Methode:</span><span class="sxs-lookup"><span data-stu-id="a82f1-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="a82f1-186">Extrahieren von Features und Transformieren der Daten</span><span class="sxs-lookup"><span data-stu-id="a82f1-186">Extract Features and transform the data</span></span>

<span data-ttu-id="a82f1-187">Da Sie die GitHub-Bereichsbezeichnung für ein `GitHubIssue` vorhersagen möchten, verwenden Sie die [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A)-Methode, um die `Area`-Spalte in eine `Label`-Spalte eines numerischen Typs zu transformieren (ein Format, das von Klassifizierungsalgorithmen akzeptiert wird), und fügen Sie sie als neue Datasetspalte hinzu:</span><span class="sxs-lookup"><span data-stu-id="a82f1-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](./snippets/github-issue-classification/csharp/Program.cs#MapValueToKey)]

<span data-ttu-id="a82f1-188">Rufen Sie als Nächstes `mlContext.Transforms.Text.FeaturizeText` auf, wodurch die Textspalten (`Title` und `Description`) jeweils in einen numerischen Vektor namens `TitleFeaturized` und `DescriptionFeaturized` transformiert werden.</span><span class="sxs-lookup"><span data-stu-id="a82f1-188">Next, call `mlContext.Transforms.Text.FeaturizeText`, which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="a82f1-189">Fügen Sie an die Pipeline die Featurebereitstellung für beide Spalten mit dem folgenden Code an:</span><span class="sxs-lookup"><span data-stu-id="a82f1-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](./snippets/github-issue-classification/csharp/Program.cs#FeaturizeText)]

<span data-ttu-id="a82f1-190">Im letzten Schritt der Vorbereitung der Daten werden alle Feature-Spalten mithilfe der [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A)-Methode in die Spalte **Features** kombiniert.</span><span class="sxs-lookup"><span data-stu-id="a82f1-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="a82f1-191">Standardmäßig verarbeitet ein Lernalgorithmus nur Merkmale aus der Spalte **Features**.</span><span class="sxs-lookup"><span data-stu-id="a82f1-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="a82f1-192">Fügen Sie an die Pipeline diese Transformation mit dem folgenden Code an:</span><span class="sxs-lookup"><span data-stu-id="a82f1-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](./snippets/github-issue-classification/csharp/Program.cs#Concatenate)]

 <span data-ttu-id="a82f1-193">Fügen Sie anschließend wie im folgenden Code veranschaulicht eine <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A>-Methode zum Zwischenspeichern von DataView an. Dadurch erhalten Sie beim mehrmaligen Durchlaufen der Daten mit dem Cache möglicherweise eine bessere Leistung:</span><span class="sxs-lookup"><span data-stu-id="a82f1-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](./snippets/github-issue-classification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="a82f1-194">Verwenden Sie AppendCacheCheckpoint für kleine/mittlere Datasets, um die Zeit für das Training zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="a82f1-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="a82f1-195">Verwenden Sie dies NICHT bei der Verarbeitung sehr großer Datasets (entfernen Sie .AppendCacheCheckpoint()).</span><span class="sxs-lookup"><span data-stu-id="a82f1-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="a82f1-196">Geben Sie die Pipeline am Ende der `ProcessData`-Methode zurück.</span><span class="sxs-lookup"><span data-stu-id="a82f1-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](./snippets/github-issue-classification/csharp/Program.cs#ReturnPipeline)]

<span data-ttu-id="a82f1-197">In diesem Schritt wird die Vorverarbeitung/Featurebereitstellung behandelt.</span><span class="sxs-lookup"><span data-stu-id="a82f1-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="a82f1-198">Die Verwendung zusätzlicher in ML.NET verfügbarer Komponenten kann bessere Ergebnisse mit dem Modell ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="a82f1-199">Erstellen und Trainieren des Modells</span><span class="sxs-lookup"><span data-stu-id="a82f1-199">Build and train the model</span></span>

<span data-ttu-id="a82f1-200">Fügen Sie der `BuildAndTrainModel`-Methode den folgenden Aufruf als nächste Codezeile der `Main`-Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="a82f1-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](./snippets/github-issue-classification/csharp/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="a82f1-201">Die `BuildAndTrainModel`-Methode führt die folgenden Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="a82f1-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="a82f1-202">Erstellen der Algorithmusklasse für das Training</span><span class="sxs-lookup"><span data-stu-id="a82f1-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="a82f1-203">Trainieren des Modells.</span><span class="sxs-lookup"><span data-stu-id="a82f1-203">Trains the model.</span></span>
* <span data-ttu-id="a82f1-204">Vorhersagen des Bereichs basierend auf den Trainingsdaten</span><span class="sxs-lookup"><span data-stu-id="a82f1-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="a82f1-205">Zurückgeben des Modells.</span><span class="sxs-lookup"><span data-stu-id="a82f1-205">Returns the model.</span></span>

<span data-ttu-id="a82f1-206">Erstellen Sie die `BuildAndTrainModel`-Methode mit dem folgenden Code direkt nach der `Main`-Methode:</span><span class="sxs-lookup"><span data-stu-id="a82f1-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="a82f1-207">Informationen zur Klassifizierungsaufgabe</span><span class="sxs-lookup"><span data-stu-id="a82f1-207">About the classification task</span></span>

<span data-ttu-id="a82f1-208">Die Klassifizierung ist eine Machine Learning-Aufgabe, die Daten zum **Bestimmen** von Kategorie, Typ oder Klasse eines Elements oder einer Datenzeile verwendet, und ist oft eine der folgenden Typen:</span><span class="sxs-lookup"><span data-stu-id="a82f1-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="a82f1-209">Binär: entweder A oder B.</span><span class="sxs-lookup"><span data-stu-id="a82f1-209">Binary: either A or B.</span></span>
* <span data-ttu-id="a82f1-210">Multiklasse: mehrere Kategorien, die mit einem einzelnen Modell vorhergesagt werden können.</span><span class="sxs-lookup"><span data-stu-id="a82f1-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="a82f1-211">Verwenden Sie für diese Art von Problemen einen Lernalgorithmus für die Klassifizierung, da es wahrscheinlicher ist, dass Ihre Vorhersage einer Problemkategorie einer von vielen Kategorien (Multiklasse) als einer von zwei (Binär) entspricht.</span><span class="sxs-lookup"><span data-stu-id="a82f1-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="a82f1-212">Fügen Sie den unten aufgeführten Code als erste Codezeilen in `BuildAndTrainModel()` ein, um den Machine Learning-Algorithmus festzulegen und ihn an die Datentransformationsdefinitionen anzufügen:</span><span class="sxs-lookup"><span data-stu-id="a82f1-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](./snippets/github-issue-classification/csharp/Program.cs#AddTrainer)]

<span data-ttu-id="a82f1-213">Der [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) Algorithmus für die Multiklassenklassifizierung.</span><span class="sxs-lookup"><span data-stu-id="a82f1-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="a82f1-214">Dieser wird an die `pipeline` angefügt und akzeptiert die mit Features ausgestatteten `Title`- und `Description`-Parameter (`Features`) sowie die `Label`-Eingabeparameter, um aus den historischen Daten zu lernen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="a82f1-215">Trainieren des Modells</span><span class="sxs-lookup"><span data-stu-id="a82f1-215">Train the model</span></span>

<span data-ttu-id="a82f1-216">Fügen Sie den unten aufgeführten Code als nächste Codezeilen in die `BuildAndTrainModel()`-Methode ein, um das Modell an die `splitTrainSet`-Daten anzupassen und das trainierte Modell zurückzugeben:</span><span class="sxs-lookup"><span data-stu-id="a82f1-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](./snippets/github-issue-classification/csharp/Program.cs#TrainModel)]

<span data-ttu-id="a82f1-217">Mit der `Fit()`-Methode wird Ihr Modell trainiert, indem das Dataset transformiert und das Training angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="a82f1-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="a82f1-218">Die [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) ist eine Hilfs-API, mit der Sie eine einzelne Instanz der Daten übergeben und dafür dann eine Vorhersage treffen können.</span><span class="sxs-lookup"><span data-stu-id="a82f1-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="a82f1-219">Fügen Sie das als nächste Zeile in der `BuildAndTrainModel()`-Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="a82f1-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](./snippets/github-issue-classification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="a82f1-220">Vorhersagen treffen mit dem trainierten Modell</span><span class="sxs-lookup"><span data-stu-id="a82f1-220">Predict with the trained model</span></span>

<span data-ttu-id="a82f1-221">Fügen Sie ein GitHub-Issue hinzu, um die Vorhersage des trainierten Modells in der `Predict`-Methode zu testen, indem Sie eine `GitHubIssue`-Instanz erstellen:</span><span class="sxs-lookup"><span data-stu-id="a82f1-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](./snippets/github-issue-classification/csharp/Program.cs#CreateTestIssue1)]

<span data-ttu-id="a82f1-222">Die [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A)-Funktion trifft eine Vorhersage für eine einzelne Datenzeile:</span><span class="sxs-lookup"><span data-stu-id="a82f1-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](./snippets/github-issue-classification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="a82f1-223">Verwenden des Modells: Vorhersageergebnisse</span><span class="sxs-lookup"><span data-stu-id="a82f1-223">Using the model: prediction results</span></span>

<span data-ttu-id="a82f1-224">Zeigen Sie `GitHubIssue` und die entsprechende Vorhersage der `Area`-Bezeichnung an, um die Ergebnisse freizugeben und entsprechenden Aktionen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="a82f1-225">Erstellen Sie mit dem folgenden <xref:System.Console.WriteLine?displayProperty=nameWithType>-Code eine Anzeige für die Ergebnisse:</span><span class="sxs-lookup"><span data-stu-id="a82f1-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](./snippets/github-issue-classification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="a82f1-226">Zurückgeben des für die Evaluierung trainierten Modells</span><span class="sxs-lookup"><span data-stu-id="a82f1-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="a82f1-227">Geben Sie das Modell am Ende der `BuildAndTrainModel`-Methode zurück.</span><span class="sxs-lookup"><span data-stu-id="a82f1-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](./snippets/github-issue-classification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="a82f1-228">Evaluieren des Modells</span><span class="sxs-lookup"><span data-stu-id="a82f1-228">Evaluate the model</span></span>

<span data-ttu-id="a82f1-229">Da Sie nun das Modell erstellt und trainiert haben, müssen Sie es zur Qualitätssicherung und Validierung mit einem anderen Dataset evaluieren.</span><span class="sxs-lookup"><span data-stu-id="a82f1-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="a82f1-230">In der `Evaluate`-Methode wird das in `BuildAndTrainModel` erstellte Modell zur Evaluierung übergeben.</span><span class="sxs-lookup"><span data-stu-id="a82f1-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="a82f1-231">Erstellen Sie die `Evaluate`-Methode direkt nach `BuildAndTrainModel` wie im folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="a82f1-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="a82f1-232">Die `Evaluate`-Methode führt die folgenden Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="a82f1-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="a82f1-233">Laden des Testdatasets.</span><span class="sxs-lookup"><span data-stu-id="a82f1-233">Loads the test dataset.</span></span>
* <span data-ttu-id="a82f1-234">Erstellen des Multiklassenauswerters</span><span class="sxs-lookup"><span data-stu-id="a82f1-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="a82f1-235">Evaluieren des Modells und Erstellen von Metriken.</span><span class="sxs-lookup"><span data-stu-id="a82f1-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="a82f1-236">Anzeigen der Metriken.</span><span class="sxs-lookup"><span data-stu-id="a82f1-236">Displays the metrics.</span></span>

<span data-ttu-id="a82f1-237">Fügen Sie einen Aufruf der neuen Methode aus der `Main`-Methode mit dem folgenden Code direkt unter dem `BuildAndTrainModel`-Methodenaufruf hinzu:</span><span class="sxs-lookup"><span data-stu-id="a82f1-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](./snippets/github-issue-classification/csharp/Program.cs#CallEvaluate)]

<span data-ttu-id="a82f1-238">Wie zuvor beim Trainingsdataset laden Sie das Testdataset, indem Sie den folgenden Code zur `Evaluate`-Methode hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="a82f1-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](./snippets/github-issue-classification/csharp/Program.cs#LoadTestDataset)]

<span data-ttu-id="a82f1-239">Die [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A)-Methode berechnet die Qualitätsmetriken für das Modell mit dem angegebenen Dataset.</span><span class="sxs-lookup"><span data-stu-id="a82f1-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="a82f1-240">Das zurückgegebene <xref:Microsoft.ML.Data.MulticlassClassificationMetrics>-Objekt enthält alle von Auswertern der Multiklassenklassifizierung berechneten Metriken.</span><span class="sxs-lookup"><span data-stu-id="a82f1-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="a82f1-241">Um diese Metriken zum Ermitteln der Modellqualität anzuzeigen, müssen Sie sie zunächst abrufen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="a82f1-242">Beachten Sie die Verwendung der [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A)-Methode der globalen Machine Learning-Variable `_trainedModel` (ein [Transformator](xref:Microsoft.ML.ITransformer)), um die Features einzugeben und die Vorhersagen zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="a82f1-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="a82f1-243">Fügen Sie der `Evaluate`-Methode folgenden Code als nächste Zeile hinzu:</span><span class="sxs-lookup"><span data-stu-id="a82f1-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](./snippets/github-issue-classification/csharp/Program.cs#Evaluate)]

<span data-ttu-id="a82f1-244">Für die Multiklassenklassifizierung werden die folgenden Metriken ausgewertet:</span><span class="sxs-lookup"><span data-stu-id="a82f1-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="a82f1-245">Mikrogenauigkeit: Jedes Beispiel/Klasse-Paar trägt zu gleichen Teilen zur Genauigkeitsmetrik bei.</span><span class="sxs-lookup"><span data-stu-id="a82f1-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="a82f1-246">Die Mikrogenauigkeit sollte so nahe wie möglich bei 1 liegen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-246">You want Micro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="a82f1-247">Makrogenauigkeit: Jede Klasse trägt zu gleichen Teilen zur Genauigkeitsmetrik bei.</span><span class="sxs-lookup"><span data-stu-id="a82f1-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="a82f1-248">Minderheitsklassen werden gleich wie größere Klassen gewichtet.</span><span class="sxs-lookup"><span data-stu-id="a82f1-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="a82f1-249">Die Makrogenauigkeit sollte so nahe wie möglich bei 1 liegen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-249">You want Macro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="a82f1-250">Protokollverlust: Siehe [Protokollverlust](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="a82f1-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="a82f1-251">Der Protokollverlust sollte so nahe wie möglich bei 0 liegen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="a82f1-252">Verringerung des Protokollverlusts: Dieser liegt zwischen -inf und 1.00, wobei „1.00“ perfekte Vorhersagen und „0“ durchschnittliche Vorhersagen bedeutet.</span><span class="sxs-lookup"><span data-stu-id="a82f1-252">Log-loss reduction - Ranges from [-inf, 1.00], where 1.00 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="a82f1-253">Die Verringerung des Protokollverlusts sollte so nahe wie möglich bei 0 liegen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-253">You want Log-loss reduction to be as close to one as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="a82f1-254">Anzeigen der Metriken zur Modellvalidierung</span><span class="sxs-lookup"><span data-stu-id="a82f1-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="a82f1-255">Verwenden Sie den folgenden Code, um die Metriken anzuzeigen, die Ergebnisse freizugeben und dann mit ihnen zu arbeiten:</span><span class="sxs-lookup"><span data-stu-id="a82f1-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](./snippets/github-issue-classification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="a82f1-256">Speichern des Modells in einer Datei</span><span class="sxs-lookup"><span data-stu-id="a82f1-256">Save the model to a file</span></span>

<span data-ttu-id="a82f1-257">Wenn Sie mit Ihrem Modell zufrieden sind, speichern Sie es in einer Datei, um Vorhersagen zu einem späteren Zeitpunkt oder in einer anderen Anwendung zu treffen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="a82f1-258">Fügen Sie der `Evaluate` -Methode folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a82f1-258">Add the following code to the `Evaluate` method.</span></span>

[!code-csharp[SnippetCallSaveModel](./snippets/github-issue-classification/csharp/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="a82f1-259">Erstellen Sie die `SaveModelAsFile`-Methode unter der `Evaluate`-Methode.</span><span class="sxs-lookup"><span data-stu-id="a82f1-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="a82f1-260">Fügen Sie der `SaveModelAsFile`-Methode den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a82f1-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="a82f1-261">Dieser Code verwendet die [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save%2A)-Methode, um das trainierte Modell zu serialisieren und als ZIP-Datei zu speichern.</span><span class="sxs-lookup"><span data-stu-id="a82f1-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save%2A) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](./snippets/github-issue-classification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="a82f1-262">Bereitstellen eines Modells und Treffen von Vorhersagen</span><span class="sxs-lookup"><span data-stu-id="a82f1-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="a82f1-263">Fügen Sie einen Aufruf der neuen Methode aus der `Main`-Methode mit dem folgenden Code direkt unter dem `Evaluate`-Methodenaufruf hinzu:</span><span class="sxs-lookup"><span data-stu-id="a82f1-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](./snippets/github-issue-classification/csharp/Program.cs#CallPredictIssue)]

<span data-ttu-id="a82f1-264">Erstellen Sie die `PredictIssue`-Methode unmittelbar nach der `Evaluate`-Methode (und direkt vor der `SaveModelAsFile`-Methode) mithilfe des folgenden Codes:</span><span class="sxs-lookup"><span data-stu-id="a82f1-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="a82f1-265">Die `PredictIssue`-Methode führt die folgenden Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="a82f1-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="a82f1-266">Laden des gespeicherte Modells</span><span class="sxs-lookup"><span data-stu-id="a82f1-266">Loads the saved model</span></span>
* <span data-ttu-id="a82f1-267">Erstellen eines einzelnen Issues aus Testdaten</span><span class="sxs-lookup"><span data-stu-id="a82f1-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="a82f1-268">Vorhersagen des Bereichs basierend auf Testdaten</span><span class="sxs-lookup"><span data-stu-id="a82f1-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="a82f1-269">Kombinieren von Testdaten und Vorhersagen für die Berichterstattung.</span><span class="sxs-lookup"><span data-stu-id="a82f1-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="a82f1-270">Anzeigen der vorhergesagten Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="a82f1-270">Displays the predicted results.</span></span>

<span data-ttu-id="a82f1-271">Laden Sie das gespeicherte Modell in Ihre Anwendung, indem Sie der `PredictIssue`-Methode den folgenden Code hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="a82f1-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](./snippets/github-issue-classification/csharp/Program.cs#SnippetLoadModel)]

<span data-ttu-id="a82f1-272">Fügen Sie ein GitHub-Issue hinzu, um die Vorhersage des trainierten Modells in der `Predict`-Methode zu testen, indem Sie eine `GitHubIssue`-Instanz erstellen:</span><span class="sxs-lookup"><span data-stu-id="a82f1-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](./snippets/github-issue-classification/csharp/Program.cs#AddTestIssue)]

<span data-ttu-id="a82f1-273">Erstellen Sie wie zuvor eine `PredictionEngine`-Instanz mit dem folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="a82f1-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](./snippets/github-issue-classification/csharp/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="a82f1-274">Die [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) ist eine Hilfs-API, mit der Sie eine Vorhersage für eine einzelne Instanz der Daten treffen können.</span><span class="sxs-lookup"><span data-stu-id="a82f1-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="a82f1-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) ist nicht threadsicher.</span><span class="sxs-lookup"><span data-stu-id="a82f1-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="a82f1-276">Die Verwendung in Singlethread-oder Prototypumgebungen ist zulässig.</span><span class="sxs-lookup"><span data-stu-id="a82f1-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="a82f1-277">Zur Verbesserung der Leistung und Threadsicherheit in Produktionsumgebungen verwenden Sie den `PredictionEnginePool`-Dienst, der einen [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) aus [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)-Objekten für die Verwendung in Ihrer gesamten Anwendung erstellt.</span><span class="sxs-lookup"><span data-stu-id="a82f1-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="a82f1-278">Informationen zur [Verwendung von `PredictionEnginePool` in einer ASP.NET Core-Web-API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application) finden Sie in dieser Anleitung.</span><span class="sxs-lookup"><span data-stu-id="a82f1-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="a82f1-279">Die `PredictionEnginePool`-Diensterweiterung ist derzeit als Vorschauversion verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a82f1-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="a82f1-280">Verwenden Sie die `PredictionEngine`, um die GitHub-Bereichsbezeichnung vorherzusagen, indem Sie den folgenden Code zur `PredictIssue`-Methode für die Vorhersage hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="a82f1-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](./snippets/github-issue-classification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="a82f1-281">Verwenden des geladenen Modells für Vorhersagen</span><span class="sxs-lookup"><span data-stu-id="a82f1-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="a82f1-282">Zeigen Sie `Area` an, um das Issue zu kategorisieren und eine entsprechende Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="a82f1-283">Erstellen Sie mit dem folgenden <xref:System.Console.WriteLine?displayProperty=nameWithType>-Code eine Anzeige für die Ergebnisse:</span><span class="sxs-lookup"><span data-stu-id="a82f1-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](./snippets/github-issue-classification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="a82f1-284">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="a82f1-284">Results</span></span>

<span data-ttu-id="a82f1-285">Die Ergebnisse sollten den unten dargestellten ähneln.</span><span class="sxs-lookup"><span data-stu-id="a82f1-285">Your results should be similar to the following.</span></span> <span data-ttu-id="a82f1-286">Während der Pipelineverarbeitung werden Meldungen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a82f1-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="a82f1-287">Sie können Warnungen oder Verarbeitungsmeldungen sehen.</span><span class="sxs-lookup"><span data-stu-id="a82f1-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="a82f1-288">Diese Nachrichten wurden der Übersichtlichkeit halber aus den folgenden Ergebnissen entfernt.</span><span class="sxs-lookup"><span data-stu-id="a82f1-288">These messages have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="a82f1-289">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="a82f1-289">Congratulations!</span></span> <span data-ttu-id="a82f1-290">Sie haben jetzt erfolgreich ein Machine Learning-Modell zur Klassifizierung und Vorhersage der Bereichsbezeichnung für ein GitHub-Issue erstellt.</span><span class="sxs-lookup"><span data-stu-id="a82f1-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="a82f1-291">Sie finden den Quellcode für dieses Tutorial im Repository [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).</span><span class="sxs-lookup"><span data-stu-id="a82f1-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a82f1-292">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="a82f1-292">Next steps</span></span>

<span data-ttu-id="a82f1-293">In diesem Tutorial haben Sie gelernt, wie die folgenden Aufgaben ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="a82f1-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="a82f1-294">Vorbereiten Ihrer Daten</span><span class="sxs-lookup"><span data-stu-id="a82f1-294">Prepare your data</span></span>
> * <span data-ttu-id="a82f1-295">Transformieren der Daten</span><span class="sxs-lookup"><span data-stu-id="a82f1-295">Transform the data</span></span>
> * <span data-ttu-id="a82f1-296">Trainieren des Modells</span><span class="sxs-lookup"><span data-stu-id="a82f1-296">Train the model</span></span>
> * <span data-ttu-id="a82f1-297">Evaluieren des Modells</span><span class="sxs-lookup"><span data-stu-id="a82f1-297">Evaluate the model</span></span>
> * <span data-ttu-id="a82f1-298">Vorhersagen treffen mit dem trainierten Modell</span><span class="sxs-lookup"><span data-stu-id="a82f1-298">Predict with the trained model</span></span>
> * <span data-ttu-id="a82f1-299">Bereitstellen eines geladenen Modells und Vorhersagen mit diesem treffen</span><span class="sxs-lookup"><span data-stu-id="a82f1-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="a82f1-300">Wechseln Sie zum nächsten Tutorial, um mehr zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="a82f1-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a82f1-301">Vorhersage des Taxifahrtpreises</span><span class="sxs-lookup"><span data-stu-id="a82f1-301">Taxi Fare Predictor</span></span>](predict-prices.md)
