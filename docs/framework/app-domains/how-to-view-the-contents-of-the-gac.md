---
title: 'Vorgehensweise: Anzeigen der Inhalte des globalen Assemblycaches'
description: Informationen zum Aufrufen der Inhalte des globalen Assemblycache in .NET mithilfe des Global Assembly Cache-Tools (gacutil.exe).
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
ms.openlocfilehash: 8b81f78f4ea28b3b9fca374029fe49f809826d8e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558562"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Vorgehensweise: Anzeigen der Inhalte des globalen Assemblycaches

Verwenden Sie das [Global Assembly Cache-Tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), um den Inhalt des globalen Assemblycaches (GAC) anzuzeigen.

## <a name="view-the-assemblies-in-the-gac"></a>Anzeigen der Assemblys im GAC

Um eine Liste der Assemblys im globalen Assemblycache anzuzeigen, öffnen Sie die [Developer-Eingabeaufforderung für Visual Studio](../tools/developer-command-prompt-for-vs.md), und geben Sie dann den folgenden Befehl ein:

```shell
gacutil -l
```

- oder -

```shell
gacutil /l
```

> [!NOTE]
> In früheren Versionen von .NET Framework ermöglichte die Windows Shell-Erweiterung [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) das Anzeigen des globalen Assemblycaches im Datei-Explorer. Seit .NET Framework 4 ist Shfusion.dll veraltet.

## <a name="see-also"></a>Siehe auch

- [Arbeiten mit Assemblys und dem globalen Assemblychache](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (Global Assembly Cache-Tool)](../tools/gacutil-exe-gac-tool.md)
