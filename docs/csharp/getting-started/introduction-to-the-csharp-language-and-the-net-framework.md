---
title: Einführung in die Programmiersprache C# und in .NET
description: Lernen Sie die Grundlagen von C# und .NET kennen. Verschaffen Sie sich einen Überblick über die Programmiersprache C# und das .NET-Ökosystem.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 9e84726a8f6056c5beeedae9081a68980150efdd
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465168"
---
# <a name="introduction-to-the-c-language-and-net"></a>Einführung in die Programmiersprache C# und in .NET

C# ist eine elegante, typsichere und objektorientierte Sprache, mit der Entwickler eine Vielzahl sicherer und robuster Anwendungen erstellen können, die im .NET-Ökosystem ausgeführt werden. Das .NET-Ökosystem besteht aus allen Implementierungen von .NET, einschließlich, aber nicht beschränkt auf [.NET Core](../../core/introduction.md) und [.NET Framework](../../framework/index.yml). Der Schwerpunkt dieses Artikels liegt auf .NET Framework. Mit C# können Sie Windows-Clientanwendungen, XML-Webdienste, verteilte Komponenten, Client-/Serveranwendungen, Datenbankanwendungen und vieles mehr erstellen.

> [!NOTE]
> Bei der Visual C#-Dokumentation werden Kenntnisse zu allgemeinen Programmierkonzepten vorausgesetzt. Als Anfänger sollten Sie sich mit Visual C# Express vertraut machen, das im Web verfügbar ist. Außerdem können Sie sich anhand von Büchern und Webressourcen über C# praktische Programmierkenntnisse aneignen.

## <a name="c-language"></a>C#-Sprache

Die C#-Syntax ist trotz ihrer Ausdrucksfülle einfach und leicht zu erlernen. Die C#-Syntax mit geschweiften Klammern ist für alle Benutzer sofort erkennbar, die mit C, C++ oder Java vertraut sind. Entwickler, die mit einer dieser Sprachen vertraut sind, können C# normalerweise innerhalb kürzester Zeit produktiv nutzen. Mit der C#-Syntax werden viele der Komplexitäten von C++ vereinfacht. Zugleich stehen leistungsfähige Features zur Verfügung, z. B. Nullable-Typen, Enumerationen, Delegaten, Lambdaausdrücke und direkter Arbeitsspeicherzugriff. C# unterstützt generische Methoden und Typen für verbesserte Typsicherheit und Leistung sowie Iteratoren, mit denen Implementierer von Auflistungsklassen benutzerdefiniertes Iterationsverhalten definieren können, das vom Clientcode einfach verwendet werden kann. LINQ-Ausdrücke (Language Integrated Query) machen eine Abfrage mit starker Typisierung zu einem erstklassigen Sprachkonstrukt.

Als objektorientierte Sprache unterstützt C# die Konzepte der Kapselung, Vererbung und Polymorphie. Alle Variablen und Methoden, einschließlich der `Main`-Methode, die den Einstiegspunkt der Anwendung darstellt, werden innerhalb der Klassendefinition gekapselt. Eine Klasse kann direkt von einer übergeordneten Klasse erben, aber auch eine beliebige Anzahl von Schnittstellen implementieren. Methoden, die virtuelle Methoden in einer übergeordneten Klasse überschreiben, erfordern das `override`-Schlüsselwort als Möglichkeit, eine versehentliche Neudefinition zu verhindern. In C# verhält sich eine Struktur wie eine vereinfachte Klasse. Sie entspricht einem auf dem Stapel reservierten Typ, der Schnittstellen implementieren kann, jedoch keine Vererbung unterstützt.

Neben diesen objektorientierten Grundprinzipien vereinfacht C# die Entwicklung von Softwarekomponenten mithilfe mehrerer innovativer Sprachkonstrukte, z.&nbsp;B. folgender:

- Gekapselte Methodensignaturen, *Delegaten* genannt, die typsichere Ereignisbenachrichtigungen ermöglichen.
- Eigenschaften, die als Zugriffsmethoden für private Membervariablen dienen.
- Attribute, die zur Laufzeit deklarative Metadaten zu Typen bereitstellen.
- Inline-XML-Dokumentationskommentare.
- LINQ (Language Integrated Query), die integrierte Abfragefunktionen für eine Vielzahl von Datenquellen bereitstellt.

Die Interaktion mit weiterer Windows-Software, z.B. COM-Objekten oder systemeigenen Win32-DLLs, wird in C# durch einen Prozess mit dem Namen „Interop“ ermöglicht. Mithilfe von Interop bieten C#-Programme dieselbe Funktionalität wie systemeigene C++-Anwendungen. C# unterstützt sogar Zeiger und das Konzept des „unsicheren“ Codes für jene Fälle, in denen direkter Speicherzugriff wichtig ist.

Der C#-Erstellungsprozess ist im Vergleich zu C und C++ einfach und flexibler als in Java. Es gibt keine separaten Headerdateien. Außerdem ist es nicht erforderlich, Methoden und Typen in einem bestimmten Ordner zu deklarieren. Eine C#-Quelldatei kann eine beliebige Anzahl von Klassen, Strukturen, Schnittstellen und Ereignissen definieren.

Die folgenden zusätzlichen C#-Ressourcen stehen zur Verfügung:

- Eine gute allgemeine Einführung in die Sprache finden Sie in Kapitel 1 der [C#-Sprachspezifikation](/dotnet/csharp/language-reference/language-specification/introduction).
- Ausführliche Informationen zu bestimmten Aspekte der Programmiersprache C# finden Sie in der [C#-Referenz](../language-reference/index.md).
- Weitere Informationen zu LINQ finden Sie unter [LINQ (Language-Integrated Query)](../programming-guide/concepts/linq/index.md).

## <a name="net-platform-architecture"></a>.NET-Plattformarchitektur

C#-Programme werden auf Grundlage von .NET ausgeführt, einer integralen Windows-Komponente, die ein virtuelles Ausführungssystem namens Common Language Runtime (CLR) sowie einheitliche Klassenbibliotheken enthält. CLR ist die kommerzielle Microsoft-Implementierung der Common Language Infrastructure (CLI), einem internationalen Standard, der die Grundlage für das Erstellen von Ausführungs- und Entwicklungsumgebungen darstellt, in denen Sprachen und Bibliotheken nahtlos zusammenarbeiten.

Der in C# geschriebene Quellcode wird in eine [Zwischensprache](../../standard/managed-code.md) kompiliert, die konform mit der CLI-Spezifikation ist. Der IL-Code wird zusammen mit Ressourcen wie z.&nbsp;B. Bitmaps und Zeichenfolgen in einer ausführbaren Datei gespeichert, der so genannten Assembly, die normalerweise die Erweiterung EXE oder DLL aufweist. Eine Assembly enthält ein Manifest, das Informationen über die Typen, die Version, die Kultur und die Sicherheitsanforderungen der Assembly bereitstellt.

Beim Ausführen des C#-Programms wird die Assembly in die CLR geladen, was je nach den im Manifest enthaltenen Informationen die Durchführung verschiedener Aktionen erfordert. Wenn die Sicherheitsanforderungen erfüllt sind, konvertiert die CLR den IL-Code mithilfe der JIT-Kompilierung (Just-In-Time) in native Computeranweisungen. Die CLR stellt darüber hinaus weitere Dienste zur automatischen Garbage Collection, Ausnahmebehandlung und Ressourcenverwaltung bereit. Der über die CLR ausgeführte Code wird manchmal als „verwalteter Code“ bezeichnet. Dieser steht im Gegensatz zum „nicht verwalteten Code“, der in native Maschinensprache kompiliert wird, die auf ein bestimmtes System abgestimmt ist. Das folgende Diagramm veranschaulicht die Beziehungen zwischen C#-Quellcodedateien, der .NET-Klassenbibliothek, Assemblys sowie der CLR zur Kompilierzeit und zur Laufzeit.

![Vom C#-Quellcode zur Computerausführung](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)

Eines der wichtigsten Features in .NET ist die Sprachinteroperabilität. Da der vom C#-Compiler generierte IL-Code der CTS (Common Type Specification) entspricht, kann er mit Code interagieren, der mit den .NET-Versionen von Visual Basic, Visual C++ oder mit einer der mehr als 20 weiteren CTS-kompatiblen Sprachen generiert wurde. Eine einzelne Assembly kann mehrere in verschiedenen .NET-Sprachen erstellte Module enthalten, und die Typen können aufeinander verweisen, als wären sie in derselben Sprache geschrieben worden.

Zusätzlich zu den Runtimediensten enthält .NET eine umfangreiche Bibliothek mit mehr als 4000 in Namespaces organisierten Klassen, die eine Vielzahl hilfreicher Funktionen bereitstellen: von der Dateieingabe und -ausgabe über die Zeichenfolgenbearbeitung bis hin zur XML-Analyse und zu Windows Forms-Steuerelementen. Eine typische C#-Anwendung verwendet für die Ausführung von Routinevorgängen ausgiebig die .NET-Klassenbibliothek.

Weitere Informationen zu .NET Framework finden Sie unter [Overview of the Microsoft .NET Framework 3.0](../../framework/get-started/overview.md) (Überblick über Microsoft .NET Framework 3.0).

## <a name="see-also"></a>Siehe auch

- [Erste Schritte mit Visual C#](/visualstudio/ide/quickstart-csharp-console)
