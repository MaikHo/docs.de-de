---
title: Interoperabilität – C#-Programmierhandbuch
description: Die Interoperabilität unterstützt zusätzlich zu unter der Common Language Runtime ausgeführtem Code auch nicht verwalteten Code. Diese Ressourcen bringen Ihnen die Interoperabilitätsoptionen näher.
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: d85eb51107d50e023270fcbe1ef6e08a7788ae78
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302970"
---
# <a name="interoperability-c-programming-guide"></a>Interoperabilität (C#-Programmierhandbuch)

Interoperabilität ermöglicht es Ihnen, vorhandene Investitionen in nicht verwalteten Code zu schützen und weiter zu nutzen. Code, der unter der Steuerung der Common Language Runtime (CLR) ausgeführt wird, wird als *verwalteter Code* bezeichnet. Code, der außerhalb der CLR ausgeführt wird, wird als *nicht verwalteter Code* bezeichnet. COM, COM+, C++-Komponenten, ActiveX-Komponenten und die Microsoft Windows-API sind Beispiele für nicht verwalteten Code.  
  
.NET ermöglicht Interoperabilität mit nicht verwaltetem Code über Plattformaufrufdienste, dem <xref:System.Runtime.InteropServices>-Namespace, C++-Interoperabilität und COM-Interoperabilität (COM-Interop).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Überblick über die Interoperabilität](./interoperability-overview.md)  
 Dieser Artikel beschreibt Methoden zum Ermöglichen der Interoperabilität zwischen von C#-verwaltetem und nicht verwaltetem Code.  
  
 [Zugreifen auf Office-Interop-Objekte mithilfe von Visual C#-Funktionen](./how-to-access-office-onterop-objects.md)  
 Dieser Artikel beschreibt Funktionen, die in Visual C# zur Erleichterung der Office-Programmierung eingeführt wurden.  
  
 [Indizierte Eigenschaften bei der COM-Interop-Programmierung](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Dieser Artikel beschreibt die Verwendung von indizierten Eigenschaften zum Zugriff auf COM-Eigenschaften, die über Parameter verfügen.  
  
 [Verwenden eines Plattformaufrufs zum Wiedergeben einer Wavedatei](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Dieser Artikel beschreibt die Verwendung von Plattformaufrufdiensten zum Abspielen einer WAV-Audiodatei im Windows-Betriebssystem.  
  
 [Exemplarische Vorgehensweise: Office-Programmierung](./walkthrough-office-programming.md)  
 Dieser Artikel zeigt das Erstellen einer Excel-Arbeitsmappe und eines Word-Dokuments, das einen Link zur Arbeitsmappe enthält.  
  
 [COM-Beispielklasse](./example-com-class.md)  
 Dieser Artikel veranschaulicht, wie eine C#-Klasse als COM-Objekt verfügbar gemacht wird.  
  
## <a name="c-language-specification"></a>C#-Programmiersprachenspezifikation  

Weitere Informationen finden Sie in den [grundlegenden Konzepten](~/_csharplang/spec/unsafe-code.md) und der[C#-Sprachspezifikation](/dotnet/csharp/language-reference/language-specification/introduction). Die Sprachspezifikation ist die verbindliche Quelle für die Syntax und Verwendung von C#.
  
## <a name="see-also"></a>Siehe auch

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [C#-Programmierhandbuch](../index.md)
- [Interoperabilität mit nicht verwaltetem Code](../../../framework/interop/index.md)
- [Exemplarische Vorgehensweise: Office-Programmierung](./walkthrough-office-programming.md)
