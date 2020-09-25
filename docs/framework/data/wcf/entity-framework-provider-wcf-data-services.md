---
title: Entity Framework-Anbieter (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: cb7bd7e793f73fc34057150ee5217dba6653237e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172644"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Entity Framework-Anbieter (WCF Data Services)

Wie WCF Data Services basiert der ADO.NET-Entity Framework auf dem Entity Data Model, bei dem es sich um einen Typ von Entitäts Beziehungsmodell handelt. Der Entity Framework übersetzt Vorgänge für die Implementierung des Entity Data Model, die als *konzeptionelles Modell*bezeichnet wird, in entsprechende Vorgänge für eine Datenquelle. Dadurch wird die Entity Framework zu einem idealen Anbieter für Datendienste, die auf relationalen Daten basieren, und jede Datenbank mit einem Datenanbieter, der die Entity Framework unterstützt, kann mit WCF Data Services verwendet werden. Eine Liste der Datenquellen, die die Entity Framework derzeit unterstützen, finden Sie unter [Entity Framework Providers](/ef/ef6/fundamentals/providers/).
  
 In einem konzeptionellen Modell ist der Entitätscontainer der Stamm des Diensts. Sie müssen in Entity Framework ein konzeptionelles Modell definieren, bevor die Daten von einem Datendienst verfügbar gemacht werden können. Weitere Informationen finden Sie unter [How to: Create a Data Service using an ADO.NET Entity Framework Data Source](create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 WCF Data Services unterstützt das Modell der vollständigen Parallelität, indem es Ihnen ermöglicht wird, ein Parallelitäts Token für eine Entität zu definieren. Dieses Parallelitätstoken, das eine oder mehrere Eigenschaften der Entität beinhaltet, wird vom Datendienst verwendet, um zu bestimmen, ob eine Änderung in den angeforderten, aktualisierten oder gelöschten Daten aufgetreten ist. Wenn Tokenwerte die vom eTag in der Anforderung abgerufen wurden, sich von den aktuellen Werten der Entität unterscheiden, löst der Datendienst eine Ausnahme aus. Um anzugeben, dass eine Eigenschaft Teil des Parallelitäts Tokens ist, müssen Sie das-Attribut `ConcurrencyMode="Fixed"` im Datenmodell anwenden, das vom Entity Framework-Anbieter definiert wird. Im Parallelitätstoken darf keine Schlüsseleigenschaft oder Navigationseigenschaft enthalten sein. Weitere Informationen finden Sie unter [Aktualisieren des Daten Dienstanbieter](updating-the-data-service-wcf-data-services.md).  
  
 Weitere Informationen zum Entity Framework finden Sie unter [Entity Framework Übersicht](../adonet/ef/overview.md).  
  
## <a name="see-also"></a>Weitere Informationen

- [Datendienstanbieter](data-services-providers-wcf-data-services.md)
- [Reflektionsanbieter](reflection-provider-wcf-data-services.md)
- [Entity Data Model](../adonet/entity-data-model.md)
