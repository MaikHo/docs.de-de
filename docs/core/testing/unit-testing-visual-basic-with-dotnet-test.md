---
title: Komponententests für Visual Basic in .NET Core mit „dotnet test“ und xUnit
description: Erfahren Sie mehr über die Konzepte von Komponententests in .NET Core, indem Sie im Rahmen eines interaktiven Tutorials Schritt für Schritt eine Visual Basic-Beispielprojektmappe mithilfe von „dotnet test“ und xUnit erstellen.
author: billwagner
ms.author: wiwagn
ms.date: 05/18/2020
ms.openlocfilehash: d384bf08f0b6031a519a8430c876eafc05d03a2e
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656422"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="eb041-103">Komponententests für Visual Basic .NET Core-Bibliotheken mithilfe von „dotnet test“ und xUnit</span><span class="sxs-lookup"><span data-stu-id="eb041-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="eb041-104">In diesem Tutorial wird gezeigt, wie Sie eine Lösung erstellen, die ein Komponententest- und ein Bibliotheksprojekt enthält.</span><span class="sxs-lookup"><span data-stu-id="eb041-104">This tutorial shows how to build a solution containing a unit test project and library project.</span></span> <span data-ttu-id="eb041-105">Um dem Tutorial mit einer vorkonfigurierten Projektmappe zu folgen, können Sie sich [den Beispielcode ansehen oder ihn herunterladen](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span><span class="sxs-lookup"><span data-stu-id="eb041-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="eb041-106">Anweisungen zum Herunterladen finden Sie unter [Beispiele und Lernprogramme](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="eb041-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="eb041-107">Erstellen der Projektmappe</span><span class="sxs-lookup"><span data-stu-id="eb041-107">Create the solution</span></span>

<span data-ttu-id="eb041-108">In diesem Abschnitt wird eine Projektmappe erstellt, die das Quell- und Testprojekt enthält.</span><span class="sxs-lookup"><span data-stu-id="eb041-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="eb041-109">Die vervollständigte Projektmappe hat die folgende Verzeichnisstruktur:</span><span class="sxs-lookup"><span data-stu-id="eb041-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.vb
        PrimeService.vbproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.vb
        PrimeServiceTests.vbproj
```

<span data-ttu-id="eb041-110">In den folgenden Anweisungen werden die Schritte zur Erstellung der Testprojektmappe beschrieben.</span><span class="sxs-lookup"><span data-stu-id="eb041-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="eb041-111">Anweisungen zum Erstellen der Testprojektmappe in einem Schritt finden Sie unter [Befehle zum Erstellen einer Testprojektmappe](#create-test-cmd).</span><span class="sxs-lookup"><span data-stu-id="eb041-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="eb041-112">Öffnen eines Shell-Fensters.</span><span class="sxs-lookup"><span data-stu-id="eb041-112">Open a shell window.</span></span>
* <span data-ttu-id="eb041-113">Führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="eb041-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="eb041-114">Der Befehl [`dotnet new sln`](../tools/dotnet-new.md) erstellt im Verzeichnis *unit-testing-using-dotnet-test* eine neue Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="eb041-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="eb041-115">Ändern Sie das Verzeichnis in *unit-testing-using-dotnet-test*.</span><span class="sxs-lookup"><span data-stu-id="eb041-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="eb041-116">Führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="eb041-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService --lang VB
  ```

   <span data-ttu-id="eb041-117">Der Befehl [`dotnet new classlib`](../tools/dotnet-new.md) erstellt im Ordner *PrimeService* ein neues Klassenbibliotheksprojekt.</span><span class="sxs-lookup"><span data-stu-id="eb041-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="eb041-118">Die neue Klassenbibliothek enthält den zu testenden Code.</span><span class="sxs-lookup"><span data-stu-id="eb041-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="eb041-119">Benennen Sie *Class1.vb* in *PrimeService.vb* um.</span><span class="sxs-lookup"><span data-stu-id="eb041-119">Rename *Class1.vb* to *PrimeService.vb*.</span></span>
* <span data-ttu-id="eb041-120">Ersetzen Sie den Code in *PrimeService.vb* durch folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="eb041-120">Replace the code in *PrimeService.vb* with the following code:</span></span>
  
  ```vb
  Imports System
  
  Namespace Prime.Services
      Public Class PrimeService
          Public Function IsPrime(candidate As Integer) As Boolean
              Throw New NotImplementedException("Not implemented.")
          End Function
      End Class
  End Namespace
  ```

* <span data-ttu-id="eb041-121">Der vorangehende Code:</span><span class="sxs-lookup"><span data-stu-id="eb041-121">The preceding code:</span></span>
  * <span data-ttu-id="eb041-122">Löst eine <xref:System.NotImplementedException> mit der Meldung aus, dass die Implementierung fehlt.</span><span class="sxs-lookup"><span data-stu-id="eb041-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="eb041-123">Wird später im Tutorial aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="eb041-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="eb041-124">Führen Sie im Verzeichnis *unit-testing-using-dotnet-test* den folgenden Befehl aus, um das Klassenbibliotheksprojekt zur Projektmappe hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="eb041-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.vbproj
  ```

* <span data-ttu-id="eb041-125">Erstellen Sie das Projekt *PrimeService.Tests*, indem Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="eb041-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="eb041-126">Für den obigen Befehl gilt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="eb041-126">The preceding command:</span></span>
  * <span data-ttu-id="eb041-127">Erstellt das Projekt *PrimeService.Tests* im Verzeichnis *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="eb041-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="eb041-128">Das Testprojekt verwendet [xUnit](https://xunit.net/) als Testbibliothek.</span><span class="sxs-lookup"><span data-stu-id="eb041-128">The test project uses [xUnit](https://xunit.net/) as the test library.</span></span>
  * <span data-ttu-id="eb041-129">Konfiguriert den Test Runner, indem die folgenden `<PackageReference />`-Elemente zur Projektdatei hinzugefügt werden:</span><span class="sxs-lookup"><span data-stu-id="eb041-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="eb041-130">Microsoft.NET.Test.Sdk</span><span class="sxs-lookup"><span data-stu-id="eb041-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="eb041-131">xunit</span><span class="sxs-lookup"><span data-stu-id="eb041-131">"xunit"</span></span>
    * <span data-ttu-id="eb041-132">xunit.runner.visualstudio</span><span class="sxs-lookup"><span data-stu-id="eb041-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="eb041-133">Fügen Sie das Testprojekt zur Projektmappendatei hinzu, indem Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="eb041-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
  ```

* <span data-ttu-id="eb041-134">Fügen Sie die Klassenbibliothek `PrimeService` dem Projekt *PrimeService.Tests* als Abhängigkeit hinzu:</span><span class="sxs-lookup"><span data-stu-id="eb041-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="eb041-135">Befehle zum Erstellen der Projektmappe</span><span class="sxs-lookup"><span data-stu-id="eb041-135">Commands to create the solution</span></span>

<span data-ttu-id="eb041-136">In diesem Abschnitt sind alle Befehle des vorherigen Abschnitts zusammengefasst.</span><span class="sxs-lookup"><span data-stu-id="eb041-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="eb041-137">Überspringen Sie diesen Abschnitt, wenn Sie die Schritte im vorherigen Abschnitt ausgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="eb041-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="eb041-138">Mit den folgenden Befehlen wird die Testprojektmappe auf einem Windows-Computer erstellt.</span><span class="sxs-lookup"><span data-stu-id="eb041-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="eb041-139">Ändern Sie unter macOS und UNIX den Befehl `ren` in die Betriebssystemversion von `ren`, um eine Datei umzubenennen:</span><span class="sxs-lookup"><span data-stu-id="eb041-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.vb PrimeService.vb
dotnet sln add ./PrimeService/PrimeService.vbproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
```

<span data-ttu-id="eb041-140">Befolgen Sie die Anweisungen unter „Ersetzen Sie den Code in *PrimeService.vb* durch folgenden Code“ im vorherigen Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="eb041-140">Follow the instructions for "Replace the code in *PrimeService.vb* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="eb041-141">Erstellen eines Tests</span><span class="sxs-lookup"><span data-stu-id="eb041-141">Create a test</span></span>

<span data-ttu-id="eb041-142">Ein beliebter Ansatz bei der testgesteuerten Entwicklung ist das Schreiben eines Tests vor Implementierung des Zielcodes.</span><span class="sxs-lookup"><span data-stu-id="eb041-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="eb041-143">In diesem Tutorial wird der Ansatz der testgesteuerten Entwicklung befolgt.</span><span class="sxs-lookup"><span data-stu-id="eb041-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="eb041-144">Die `IsPrime`-Methode ist aufrufbar, aber nicht implementiert.</span><span class="sxs-lookup"><span data-stu-id="eb041-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="eb041-145">Ein Testaufruf von `IsPrime` schlägt fehl.</span><span class="sxs-lookup"><span data-stu-id="eb041-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="eb041-146">Bei der testgesteuerten Entwicklung wird ein Test geschrieben, der bekanntermaßen fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="eb041-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="eb041-147">Der Zielcode wird aktualisiert, damit der Test bestanden wird.</span><span class="sxs-lookup"><span data-stu-id="eb041-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="eb041-148">Sie wiederholen diesen Ansatz kontinuierlich, schreiben einen nicht erfolgreichen Test und aktualisieren dann den Zielcode so, dass er bestanden wird.</span><span class="sxs-lookup"><span data-stu-id="eb041-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="eb041-149">Aktualisieren Sie das Projekt *PrimeService.Tests*:</span><span class="sxs-lookup"><span data-stu-id="eb041-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="eb041-150">Löschen Sie *PrimeService.Tests/UnitTest1.vb*.</span><span class="sxs-lookup"><span data-stu-id="eb041-150">Delete *PrimeService.Tests/UnitTest1.vb*.</span></span>
* <span data-ttu-id="eb041-151">Erstellen Sie die Datei *PrimeService.Tests/PrimeService_IsPrimeShould.vb*.</span><span class="sxs-lookup"><span data-stu-id="eb041-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.vb*  file.</span></span>
* <span data-ttu-id="eb041-152">Ersetzen Sie den Code in *PrimeService_IsPrimeShould.vb* durch folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="eb041-152">Replace the code in *PrimeService_IsPrimeShould.vb* with the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private ReadOnly _primeService As Prime.Services.PrimeService

        Public Sub New()
            _primeService = New Prime.Services.PrimeService()
        End Sub


        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="eb041-153">Das `[Fact]`-Attribut deklariert eine Testmethode, die vom Test Runner ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="eb041-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="eb041-154">Führen Sie `dotnet test` im Ordner *PrimeService.Tests* aus.</span><span class="sxs-lookup"><span data-stu-id="eb041-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="eb041-155">Der Befehl [dotnet test](../tools/dotnet-test.md) erstellt beide Projekte und führt die Tests aus.</span><span class="sxs-lookup"><span data-stu-id="eb041-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="eb041-156">Der Test Runner für xUnit enthält den Programmeinstiegspunkt zum Ausführen der Tests.</span><span class="sxs-lookup"><span data-stu-id="eb041-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="eb041-157">`dotnet test` startet den Test Runner mithilfe des Komponententestprojekts.</span><span class="sxs-lookup"><span data-stu-id="eb041-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="eb041-158">Der Test schlägt fehl, da `IsPrime` nicht implementiert wurde.</span><span class="sxs-lookup"><span data-stu-id="eb041-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="eb041-159">Schreiben Sie bei Befolgen des Ansatzes zur testgesteuerten Entwicklung nur so viel Code, dass dieser Test bestanden wird.</span><span class="sxs-lookup"><span data-stu-id="eb041-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="eb041-160">Aktualisieren Sie `IsPrime` mit folgendem Code:</span><span class="sxs-lookup"><span data-stu-id="eb041-160">Update `IsPrime` with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Not implemented.")
End Function
```

<span data-ttu-id="eb041-161">Führen Sie aus `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="eb041-161">Run `dotnet test`.</span></span> <span data-ttu-id="eb041-162">Der Test wurde erfolgreich ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="eb041-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="eb041-163">Hinzufügen weiterer Tests</span><span class="sxs-lookup"><span data-stu-id="eb041-163">Add more tests</span></span>

<span data-ttu-id="eb041-164">Fügen Sie Primzahlentests für 0 und-1 hinzu.</span><span class="sxs-lookup"><span data-stu-id="eb041-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="eb041-165">Sie können den vorangehenden Test kopieren und den folgenden Code so ändern, dass 0 und-1 verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="eb041-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```vb
Dim result As Boolean = _primeService.IsPrime(1)

Assert.False(result, "1 should not be prime")
```

<span data-ttu-id="eb041-166">Das Kopieren von Testcode, wenn sich nur ein Parameter ändert, führt zu Codeduplizierung und Testüberfrachtung.</span><span class="sxs-lookup"><span data-stu-id="eb041-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="eb041-167">Die folgenden xUnit-Attribute ermöglichen das Schreiben einer Sammlung ähnlicher Tests:</span><span class="sxs-lookup"><span data-stu-id="eb041-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="eb041-168">`[Theory]` repräsentiert eine Reihe von Tests, die zwar denselben Code ausführen, aber unterschiedliche Eingabeargumente verwenden.</span><span class="sxs-lookup"><span data-stu-id="eb041-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>
- <span data-ttu-id="eb041-169">Das `[InlineData]`-Attribut gibt Werte für diese Eingaben an.</span><span class="sxs-lookup"><span data-stu-id="eb041-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="eb041-170">Anstatt neue Tests zu erstellen, wenden Sie die vorhergehenden xUnit-Attribute an, um eine einzelne Theorie zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="eb041-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="eb041-171">Ersetzen Sie den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="eb041-171">Replace the following code:</span></span>

```vb
<Fact>
Sub IsPrime_InputIs1_ReturnFalse()
    Dim result As Boolean = _primeService.IsPrime(1)

    Assert.False(result, "1 should not be prime")
End Sub
```

<span data-ttu-id="eb041-172">durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="eb041-172">with the following code:</span></span>

```vb
<Theory>
<InlineData(-1)>
<InlineData(0)>
<InlineData(1)>
Sub IsPrime_ValuesLessThan2_ReturnFalse(ByVal value As Integer)
    Dim result As Boolean = _primeService.IsPrime(value)

    Assert.False(result, $"{value} should not be prime")
End Sub
```

<span data-ttu-id="eb041-173">Im vorangehenden Code ermöglichen `[Theory]` und `[InlineData]` das Testen mehrerer Werte, die kleiner als 2 sind.</span><span class="sxs-lookup"><span data-stu-id="eb041-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="eb041-174">2 ist die kleinste Primzahl.</span><span class="sxs-lookup"><span data-stu-id="eb041-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="eb041-175">Führen Sie `dotnet test` aus. Zwei dieser Tests schlagen fehl.</span><span class="sxs-lookup"><span data-stu-id="eb041-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="eb041-176">Aktualisieren Sie die `IsPrime`-Methode mit folgendem Code, damit alle Tests bestanden werden:</span><span class="sxs-lookup"><span data-stu-id="eb041-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate < 2 Then
        Return False
    End If
    Throw New NotImplementedException("Not fully implemented.")
End Function
```

<span data-ttu-id="eb041-177">Fügen Sie unter Befolgen des Ansatzes zur testgesteuerten Entwicklung weitere nicht erfolgreiche Tests hinzu, und aktualisieren Sie anschließend den Zielcode.</span><span class="sxs-lookup"><span data-stu-id="eb041-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="eb041-178">Sehen Sie sich die [endgültige Version der Tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) und die [vollständige Implementierung der Bibliothek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb) an.</span><span class="sxs-lookup"><span data-stu-id="eb041-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="eb041-179">Die vervollständigte `IsPrime`-Methode ist kein effizienter Algorithmus für den Primzahltest.</span><span class="sxs-lookup"><span data-stu-id="eb041-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="eb041-180">Zusätzliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="eb041-180">Additional resources</span></span>

- [<span data-ttu-id="eb041-181">xUnit.net official site (Offizielle xUnit-Website)</span><span class="sxs-lookup"><span data-stu-id="eb041-181">xUnit.net official site</span></span>](https://xunit.net/)
- [<span data-ttu-id="eb041-182">Testen von Controllerlogik in ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eb041-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
