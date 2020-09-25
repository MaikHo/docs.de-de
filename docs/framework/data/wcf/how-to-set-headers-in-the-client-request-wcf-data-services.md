---
title: 'Vorgehensweise: Festlegen von Headern in der Clientanforderung (WCF Data Services)'
description: Erfahren Sie, wie Sie das SendingRequest-Ereignis behandeln, um der Anforderungs Nachricht einen neuen Header hinzuzufügen, bevor dieser in WCF Data Services an den Datendienst gesendet wird.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 47e40f416b256fbd06160a5ee2683eb8364d48b7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204384"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Vorgehensweise: Festlegen von Headern in der Clientanforderung (WCF Data Services)

Wenn Sie die WCF Data Services-Client Bibliothek für den Zugriff auf einen Datendienst verwenden, der die Open Data Protocol (odata) unterstützt, legt die Client Bibliothek die erforderlichen HTTP-Header in Anforderungs Nachrichten, die an den Datendienst gesendet werden, automatisch fest. Die Clientbibliothek ist jedoch nicht in der Lage, Nachrichtenheader festzulegen, die in bestimmten Fällen erforderlich sind, z. B. wenn der Datendienst die anspruchsbasierte Authentifizierung oder Cookies erfordert. Weitere Informationen finden Sie unter [Securing WCF Data Services](securing-wcf-data-services.md#clientAuthentication). In diesen Fällen müssen Sie Nachrichtenheader in der Anforderungsnachricht vor dem Senden manuell festlegen. Das Beispiel in diesem Thema zeigt, wie das <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>-Ereignis behandelt wird, um der Anforderungsnachricht einen neuen Header hinzuzufügen, bevor sie an den Datendienst gesendet wird.  
  
 Im Beispiel in diesem Thema werden der Northwind-Beispieldatendienst und automatisch generierte Client-Datendienstklassen verwendet. Dieser Dienst und die Client Daten Klassen werden erstellt, wenn Sie den [WCF Data Services Schnellstart](quickstart-wcf-data-services.md)ausführen. Sie können auch den [Northwind-Beispiel Datendienst](https://services.odata.org/Northwind/Northwind.svc/) verwenden, der auf der odata-Website veröffentlicht wird. dieser Beispiel Datendienst ist schreibgeschützt. Wenn Sie versuchen, Änderungen zu speichern, wird ein Fehler zurückgegeben. Die Beispiel Datendienste auf der odata-Website ermöglichen die anonyme Authentifizierung.  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird ein Handler für das <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>-Ereignis registriert und anschließend eine Abfrage für den Datendienst ausgeführt.  
  
> [!NOTE]
> Wenn Sie bei einem Datendienst den Nachrichtenheader für jede Anforderung manuell festlegen müssen, ist es u. U. sinnvoll, den Handler für das <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>-Ereignis durch Überschreiben der partiellen `OnContextCreated`-Methode im Entitätscontainer, der den Datendienst darstellt (in diesem Fall `NorthwindEntities`), zu registrieren.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Beispiel  

 Die folgende Methode behandelt das <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>-Ereignis und fügt der Anforderung einen Authentifizierungsheader hinzu.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Weitere Informationen

- [Sichern von WCF Data Services](securing-wcf-data-services.md)
- [WCF Data Services-Clientbibliothek](wcf-data-services-client-library.md)
