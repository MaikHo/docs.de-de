---
title: Bereitstellen von WCF-Anwendungen mit ClickOnce
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: 52657c5f3b5bc6c57c59f4ef23e73089f3c681eb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550370"
---
# <a name="deploying-wcf-applications-with-clickonce"></a>Bereitstellen von WCF-Anwendungen mit ClickOnce
Client Anwendungen, die Windows Communication Foundation (WCF) verwenden, können mithilfe der ClickOnce-Technologie bereitgestellt werden. Diese Technologie ermöglicht es, den von der Codezugriffssicherheit bereitgestellten Laufzeitsicherheitsschutz zu nutzen, sofern die Clientanwendungen digital mit einem vertrauenswürdigen Zertifikat signiert sind. Das Zertifikat, mit dem die ClickOnce-Anwendung signiert wird, muss sich im Speicher für vertrauenswürdige Herausgeber befinden. Die lokale Sicherheitsrichtlinie auf dem Clientcomputer muss so konfiguriert sein, dass signierte Anwendungen mit dem Zertifikat des Herausgebers Berechtigungen für volle Vertrauenswürdigkeit erhalten.  
  
 Informationen zum Konfigurieren von ClickOnce-Anwendungen und vertrauenswürdigen Verlegern finden Sie unter [Konfigurieren von ClickOnce-vertrauenswürdigen Verlegern](/previous-versions/dotnet/articles/ms996418(v=msdn.10))  
  
## <a name="see-also"></a>Siehe auch

- [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](/visualstudio/deployment/trusted-application-deployment-overview)
- [ClickOnce-Bereitstellung für Windows Forms Anwendungen](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))
