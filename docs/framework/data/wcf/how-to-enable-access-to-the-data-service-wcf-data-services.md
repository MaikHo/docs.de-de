---
title: 'Vorgehensweise: Aktivieren des Zugriffs auf den Datendienst (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 377b031c48ed831cfa5e270426283ed03a55f886
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542306"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Vorgehensweise: Aktivieren des Zugriffs auf den Datendienst (WCF Data Services)
In WCF Data Services müssen Sie explizit Zugriff auf die Ressourcen gewähren, die von einem Datendienst verfügbar gemacht werden. Daher müssen Sie nach der Erstellung eines neuen Datendiensts explizit den Zugriff auf einzelne Ressourcen als Entitätenmengen bereitstellen. In diesem Thema wird gezeigt, wie Sie den Lese-und Schreibzugriff auf fünf der Entitätenmengen im Northwind-Datendienst aktivieren, der beim Abschluss des [Schnellstarts](quickstart-wcf-data-services.md)erstellt wird. Da die <xref:System.Data.Services.EntitySetRights>-Enumeration mit dem <xref:System.FlagsAttribute> definiert wird, können Sie mehrere Berechtigungen für eine einzelne Entitätenmenge mithilfe eines logischen OR-Operators angeben.  
  
> [!NOTE]
> Jeder Client, der auf die ASP.NET-Anwendung zugreifen kann, kann auch auf die vom Datendienst verfügbar gemachten Ressourcen zugreifen. Sie sollten in einem Produktionsdatendienst auch die Anwendung selbst schützen, um nicht autorisierten Zugriff auf Ressourcen zu verhindern. Weitere Informationen finden Sie unter [Sichern von ASP.NET Websites](/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
### <a name="to-enable-access-to-the-data-service"></a>So aktivieren Sie den Zugriff auf den Datendienst  
  
- Ersetzen Sie im Code für den Datendienst den Platzhaltercode in der `InitializeService`-Funktion durch Folgendes:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     Dies ermöglicht Clients, Lese- und Schreibzugriff auf die `Orders`-Entitätenmenge und die `Order_Details`-Entitätenmenge sowie Lesezugriff auf die `Customers`-Entitätenmenge zu erhalten.  
  
## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Entwickeln eines mit IIS ausgeführten WCF-Datendiensts](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Konfigurieren des Datendiensts](configuring-the-data-service-wcf-data-services.md)
