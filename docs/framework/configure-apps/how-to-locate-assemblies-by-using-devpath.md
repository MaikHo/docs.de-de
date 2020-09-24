---
title: 'Vorgehensweise: Suchen von Assemblys mit DEVPATH'
description: Testen Sie, ob eine freigegebene Assembly mit vielen Anwendungen in .net ordnungsgemäß funktioniert, indem Sie eine XML-Computer Konfigurationsdatei und die DEVPATH-Umgebungsvariable verwenden.
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 8ae807e46b11d2adb06d6af0c86e1c7297caa0c0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161983"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Vorgehensweise: Suchen von Assemblys mit DEVPATH

Entwickler möchten möglicherweise sicherstellen, dass eine freigegebene Assembly, die Sie erstellen, mit mehreren Anwendungen ordnungsgemäß funktioniert. Anstatt die Assembly während des Entwicklungsprozesses ständig in den globalen Assemblycache zu versetzen, kann der Entwickler eine DEVPATH-Umgebungsvariable erstellen, die auf das Buildausgabeverzeichnis für die Assembly zeigt.  
  
 Nehmen Sie beispielsweise an, dass Sie eine freigegebene Assembly namens MySharedAssembly erstellen und das Ausgabeverzeichnis c:\MySharedAssembly\Debug. Sie können "c:\MySharedAssembly\Debug" in der DEVPATH-Variablen ablegen. Sie müssen dann das- [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) Element in der Computer Konfigurationsdatei angeben. Dieses Element teilt dem Common Language Runtime mit, DEVPATH zum Suchen nach Assemblys zu verwenden.  
  
 Die freigegebene Assembly muss von der Laufzeit erkannt werden können.  Um ein privates Verzeichnis zum Auflösen von Assemblyverweisen anzugeben, verwenden Sie das- [ \<codeBase> Element](./file-schema/runtime/codebase-element.md) oder- [ \<probing> Element](./file-schema/runtime/probing-element.md) in einer Konfigurationsdatei, wie unter [angeben des Speicher Orts einer Assembly](specify-assembly-location.md)beschrieben.  Sie können die Assembly auch in einem Unterverzeichnis des Anwendungs Verzeichnisses platzieren. Weitere Informationen finden Sie unter [so](../deployment/how-the-runtime-locates-assemblies.md)sucht Common Language Runtime nach Assemblys.  
  
> [!NOTE]
> Dies ist eine erweiterte Funktion, die nur für die Entwicklung vorgesehen ist.  
  
 Im folgenden Beispiel wird gezeigt, wie Sie bewirken, dass die Laufzeit Assemblys in Verzeichnissen sucht, die durch die DEVPATH-Umgebungsvariable angegeben werden.  
  
## <a name="example"></a>Beispiel  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 Diese Einstellung ist standardmäßig auf false festgelegt.  
  
> [!NOTE]
> Verwenden Sie diese Einstellung nur zur Entwicklungszeit. Die Laufzeit überprüft nicht die Versionen von Assemblys mit starkem Namen, die im DEVPATH gefunden werden. Es wird einfach die erste gefundene Assembly verwendet.  
  
## <a name="see-also"></a>Weitere Informationen

- [Konfigurieren von Apps mithilfe von Konfigurationsdateien](index.md)
