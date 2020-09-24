---
title: Batchvorgänge (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 95524c1397172e645d682a6ef3f03b17bb3a639d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166065"
---
# <a name="batching-operations-wcf-data-services"></a>Batchvorgänge (WCF Data Services)

Der Open Data Protocol (odata) unterstützt die Batch Verarbeitung von Anforderungen an einen odata-basierten Dienst. Weitere Informationen finden Sie unter [odata: Batch Verarbeitung](https://www.odata.org/documentation/odata-version-2-0/batch-processing/). In WCF Data Services führt jeder Vorgang, der verwendet <xref:System.Data.Services.Client.DataServiceContext> , z. b. das Ausführen einer Abfrage oder das Speichern von Änderungen, dazu, dass eine separate Anforderung an den Datendienst gesendet wird. Sie können Vorgangsbatches explizit definieren, um einen logischen Bereich für mehrere Vorgänge beizubehalten. Dadurch wird sichergestellt, dass alle Vorgänge im Batch an den Datendienst in einer einzelnen HTTP-Anforderung gesendet werden, der Server wird aktiviert, um den Vorgang atomar zu verarbeiten, und die Anzahl von Roundtrips zum Datendienst wird reduziert.  
  
## <a name="batching-query-operations"></a>Batchverarbeitungsabfragevorgänge  

 Sie müssen jede Abfrage im Batch als separate Instanz der <xref:System.Data.Services.Client.DataServiceRequest%601>-Klasse erstellen, um mehrere Abfragen in einem Batch auszuführen. Wenn Sie auf diese Weise eine Abfrageanforderung erstellen, wird die Abfrage selbst als URI definiert und folgt den Regeln zum Adressieren von Ressourcen. Weitere Informationen finden Sie unter [zugreifen auf Datendienst Ressourcen](accessing-data-service-resources-wcf-data-services.md). Die zusammengefassten Abfrageanforderungen werden an den Datendienst gesendet, wenn die <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A>-Methode aufgerufen wird, die die Abfrageanforderungsobjekte enthält. Diese Methode gibt ein <xref:System.Data.Services.Client.DataServiceResponse>-Objekt zurück, das eine Auflistung von <xref:System.Data.Services.Client.QueryOperationResponse%601>-Objekten ist, die Antworten auf einzelne Abfragen im Batch darstellen, von denen jede entweder eine Auflistung von der Abfrage zurückgegebenen Objekten oder Fehlerinformationen enthält. Wenn ein einzelner Abfragevorgang im Batch fehlschlägt, werden Fehlerinformationen im <xref:System.Data.Services.Client.QueryOperationResponse%601>-Objekt für die fehlgeschlagene Operation zurückgegeben, und die übrigen Vorgänge werden noch ausgeführt. Weitere Informationen finden Sie unter Gewusst [wie: Ausführen von Abfragen in einem Batch](how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Zusammengefasste Abfragen können auch asynchron ausgeführt werden. Weitere Informationen finden Sie unter [asynchrone Vorgänge](asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Batchverarbeitung des SaveChanges-Vorgangs  

 Wenn Sie die- <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> Methode aufzurufen, werden alle Änderungen, die der Kontext verfolgt, in Rest-basierte Vorgänge übersetzt, die als Anforderungen an den odata-Dienst gesendet werden. Standardmäßig werden diese Änderungen nicht in einer einzelnen Anforderungsnachricht gesendet. Wenn alle Änderungen in einer einzelnen Anforderung gesendet werden sollen, müssen Sie die <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> -Methode und den Wert <xref:System.Data.Services.Client.SaveChangesOptions.Batch> in die-Enumeration einschließen, die <xref:System.Data.Services.Client.SaveChangesOptions> Sie für die-Methode bereitstellen.  
  
 Sie können zusammengefasste Änderungen auch asynchron speichern. Weitere Informationen finden Sie unter [asynchrone Vorgänge](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Weitere Informationen

- [WCF Data Services-Clientbibliothek](wcf-data-services-client-library.md)
