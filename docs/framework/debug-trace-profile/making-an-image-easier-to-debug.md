---
title: Vereinfachen des Debuggens eines Images in .net
description: Erfahren Sie, wie Sie ein ausführbares Image für ein einfacheres Debuggen mithilfe von IDE-Switches und Befehlszeilenoptionen konfigurieren.
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
ms.openlocfilehash: a3305dc864e7852c2336009503732a51868410d2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558510"
---
# <a name="making-an-image-easier-to-debug-in-net"></a>Vereinfachen des Debuggens eines Images in .net

Beim Kompilieren von nicht verwaltetem Code können Sie durch das Festlegen von IDE-Schaltern oder Befehlszeilenoptionen ein ausführbares Abbild zum Debuggen konfigurieren. Sie können beispielsweise die Befehlszeilenoption /**Zi** in Visual C++ verwenden, um zur Ausgabe von Debugsymboldateien aufzufordern (Dateierweiterung „.pdb“). Dementsprechend weist die Befehlszeilenoption /**Od** den Compiler an, die Optimierung zu deaktivieren. Der resultierende Code ist langsamer, aber es ist einfacher zu debuggen, sollte dies erforderlich sein.

Beim Kompilieren .NET Framework verwalteten Codes kompilieren Compiler wie Visual C++, Visual Basic und c# Ihr Quell Programm in Microsoft Intermediate Language (MSIL). MSIL wird dann vor der Ausführung JIT-kompiliert in systemeigenen Computercode. Ähnlich wie bei nicht verwaltetem Code können Sie durch das Festlegen von IDE-Schaltern oder Befehlszeilenoptionen ein ausführbares Image zum Debuggen konfigurieren. Sie können auch die JIT-Kompilierung für das Debuggen auf die gleiche Weise konfigurieren.

Diese JIT-Konfiguration hat zwei Aspekte:

- Sie können den JIT-Compiler zum Generieren von Überwachungsinformationen anfordern. Dadurch kann der Debugger eine Kette von MSIL dem entsprechenden Computercode zuordnen und verfolgen, wo lokale Variablen und Funktionsargumente gespeichert werden. Beginnend mit dem .NET Framework, Version 2,0, generiert der JIT-Compiler immer Überwachungsinformationen, sodass es nicht erforderlich ist, ihn anzufordern.

- Sie können den JIT-Compiler bitten, den resultierenden Computercode nicht zu optimieren.

Normalerweise legt der Compiler, der die MSIL generiert, diese JIT-Compileroptionen entsprechend fest, basierend auf den von Ihnen angegebenen IDE-Switches oder Befehlszeilenoptionen, z. b./**od**.

Mitunter kann es erforderlich sein, das Verhalten des JIT-Compilers zu ändern, sodass der generierte Computercode einfacher zu debuggen ist. So können Sie z. B. JIT-Verfolgungsinformationen für eine Verkaufsversion generieren oder die Optimierung steuern. Dazu können Sie eine Initialisierungsdatei (INI) verwenden.

Wenn z. b. die Assembly, die Sie debuggen möchten, als *MyApp.exe*bezeichnet wird, können Sie eine Textdatei mit dem Namen *MyApp.ini*im selben Ordner wie *MyApp.exe*erstellen, der diese drei Zeilen enthält:

```ini
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

Sie können für die Optionen jeweils den Wert 0 oder 1 einstellen. Nicht vorhandene Optionen haben standardmäßig den Wert 0. Am einfachsten lässt sich die Assembly debuggen, wenn Sie für `GenerateTrackingInfo` 1 und für `AllowOptimize` 0 festlegen.

Beginnend mit der .NET Framework Version 2,0 generiert der JIT-Compiler immer nach Verfolgungs Informationen, unabhängig vom Wert für `GenerateTrackingInfo` `AllowOptimize` . der Wert hat jedoch weiterhin Auswirkungen. Wenn Sie das native Image mithilfe von [Ngen.exe (Native Image Generator)](../tools/ngen-exe-native-image-generator.md) ohne Optimierung vorkompilieren, muss bei der Ausführung von „Ngen.exe“ die INI-Datei im Zielordner mit der Einstellung `AllowOptimize=0` vorhanden sein. Wenn Sie eine Assembly ohne Optimierung vorkompiliert haben, müssen Sie den vorkompilierten Code mit NGen.exe **/Uninstall** -Option entfernen, bevor Sie Ngen.exe erneut ausführen, um den Code so zu konfigurieren, dass er als optimiert vorkompiliert wird. Wenn die INI-Datei nicht im Ordner vorhanden ist, wird der Code standardmäßig in Ngen.exe vorkompiliert.

<xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> kontrolliert die Einstellungen für eine Assembly. **DebuggableAttribute** enthält zwei Felder, die Steuern, ob der JIT-Compiler Überwachungsinformationen optimieren und/oder generieren soll. Beginnend mit der .NET Framework Version 2,0 generiert der JIT-Compiler immer Überwachungsinformationen.

Bei einem Retail-Build legen Compiler kein "Debug"- **Attribut**fest. Standardmäßig generiert der JIT-Compiler die höchste Leistung, am schwierigsten ist das Debuggen von Computercode. Durch Aktivieren der JIT-Verfolgung wird die Leistung geringfügig, durch Deaktivieren der Optimierung erheblich verschlechtert.

**DebuggableAttribute** gilt immer für die gesamte Assembly, nicht für einzelne Module innerhalb der Assembly. Aus diesem Grund müssen Entwicklungstools benutzerdefinierte Attribute an das Metadatentoken der Assembly anfügen, sofern bereits eine Assembly erstellt wurde oder aber an die **System.Runtime.CompilerServices.AssemblyAttributesGoHere**-Klasse. Das ALink-Tool stuft dann diese **DebuggableAttribute** -Attribute von den einzelnen Modulen in die Assembly herauf, zu der Sie gehören. Tritt ein Konflikt auf, schlägt der ALink-Vorgang fehl.

> [!NOTE]
> In Version 1.0 von .NET Framework fügt der Microsoft Visual C++-Compiler das **DebuggableAttribute** hinzu, wenn die Compileroptionen **/clr** und **/Zi** angegeben werden. In Version 1,1 des .NET Framework müssen Sie das **DebuggableAttribute** entweder manuell in Ihrem Code hinzufügen oder die Option **/ASSEMBLYDEBUG** (Linkeroption) verwenden.

## <a name="see-also"></a>Siehe auch

- [Debuggen, Ablaufverfolgung und Profilerstellung](index.md)
- [Aktivieren von JIT-attach Debugging](enabling-jit-attach-debugging.md)
- [Aktivieren der Profilerstellung](/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))
