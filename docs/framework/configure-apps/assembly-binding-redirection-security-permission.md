---
title: Sicherheitsberechtigung für die Umleitung der Assemblybindung
description: Erfahren Sie mehr über die für die explizite Umleitung von Assemblybindungen in einer Anwendungs Konfigurationsdatei in .net erforderliche Sicherheits Berechtigung.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: 2de2c50f5adb9e9fa36ea015ef498e9953c83005
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165220"
---
# <a name="assembly-binding-redirection-security-permission"></a>Sicherheitsberechtigung für die Umleitung der Assemblybindung

Für die explizite Umleitung einer Assemblybindung in einer Anwendungskonfigurationsdatei ist eine Sicherheitsberechtigung erforderlich. Dies betrifft die Umleitung von .NET Framework-Assemblys und Assemblys von Drittanbietern. Die Berechtigung wird erteilt, indem das-Flag auf festgelegt wird <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> . Verwaltete Assemblys haben standardmäßig keine Berechtigungen.  
  
 Die Sicherheits Berechtigung wird Anwendungen gewährt, die in der vertrauenswürdigen Zone (dem lokalen Computer) und in der Intranetzone ausgeführt werden. Anwendungen, die in der Internet Zone ausgeführt werden, dürfen keine Umleitung der Assemblybindung durchführen.  
  
 Die Berechtigung ist nicht erforderlich, wenn die Assemblyumleitung in einer Herausgeber Richtlinien Datei durchgeführt wird, die vom Komponenten Verleger gesteuert wird, oder in der vom Administrator kontrollierten Computer Konfigurationsdatei. Allerdings ist die-Berechtigung erforderlich, damit eine Anwendung die Herausgeber Richtlinie mit dem- [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) Element in der Anwendungs Konfigurationsdatei explizit ignoriert.  
  
 In der folgenden Tabelle werden die Standard Sicherheitseinstellungen für das **bindingreumleitungen** -Flag aufgeführt.  
  
|Zone|Einstellung für das bindingreumgeleitet-Flag|  
|----------|-----------------------------------|  
|Vertrauenswürdige Zone (lokaler Computer)|**ON**|  
|Intranetzone|**ON**|  
|Internetzone|**OFF**|  
|Nicht vertrauenswürdige Zonen|**OFF**|  
  
 Ein Administrator kann diese Sicherheitseinstellungen ändern, um bestimmte Szenarien auf einem bestimmten Computer zu unterstützen oder einzuschränken. Es gibt keine Tools zum Ändern der Einstellung für das **bindingreumleitungen** -Flag von der Standardeinstellung. ein Administrator muss die Security.config Datei manuell auf dem Computer eines Benutzers bearbeiten.  
  
## <a name="see-also"></a>Weitere Informationen

- [Herausgeberrichtliniendateien und parallele Ausführung](/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))
- [How to: Aktivieren und Deaktivieren der Bindungsumleitung](how-to-enable-and-disable-automatic-binding-redirection.md)
- [Parallele Ausführung](../deployment/side-by-side-execution.md)
