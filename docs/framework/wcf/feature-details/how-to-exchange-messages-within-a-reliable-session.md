---
title: 'Vorgehensweise: Austauschen von Nachrichten innerhalb einer zuverlässigen Sitzung'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 97371f8572d5d0db633ab8dd1ca82067d9d55c3f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550188"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Vorgehensweise: Austauschen von Nachrichten innerhalb einer zuverlässigen Sitzung

Dieses Thema enthält einen Überblick über die Schritte zum Aktivieren einer zuverlässigen Sitzung mithilfe einer der vom System bereitgestellten Bindungen, die eine solche Sitzung zwar unterstützen, dies jedoch nicht standardmäßig. Sie können eine zuverlässige Sitzung Imperativ mithilfe von Code oder deklarativ in der Konfigurationsdatei aktivieren. In diesem Verfahren werden die Client-und Dienst Konfigurationsdateien verwendet, um die zuverlässige Sitzung zu aktivieren und festzulegen, dass die Nachrichten in derselben Reihenfolge eintreffen, in der Sie gesendet wurden.

Der wesentliche Teil dieser Prozedur ist, dass das Endpunkt Konfigurationselement ein- `bindingConfiguration` Attribut enthält, das auf eine Bindungs Konfiguration mit dem Namen verweist `Binding1` . Das [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) Configuration-Element verweist auf diesen Namen, um zuverlässige Sitzungen zu aktivieren, indem das- `enabled` Attribut des-Elements auf festgelegt wird [**\<reliableSession>**](/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) `true` . Sie geben die Zusicherung einer Zustellung in der richtigen Reihenfolge für die zuverlässige Sitzung an, indem Sie das `ordered`-Attribut auf `true` festlegen.

Die Quell Kopie dieses Beispiels finden Sie unter [zuverlässige WS-Sitzung](../samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurieren Sie den Dienst mit einer wsHttpBinding, um eine zuverlässige Sitzung zu verwenden.

1. Definieren Sie einen Dienstvertrag für den Diensttyp.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Implementieren Sie den Dienstvertrag in einer Dienstklasse. Beachten Sie, dass die Adresse oder die Bindungs Informationen nicht in der Implementierung des Dienstanbieter angegeben werden. Sie müssen keinen Code schreiben, um die Adresse oder die Bindungs Informationen aus der Konfigurationsdatei abzurufen.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Erstellen Sie eine *Web.config* -Datei, um einen Endpunkt für die zu konfigurieren `CalculatorService` , die <xref:System.ServiceModel.WSHttpBinding> mit aktivierter zuverlässiger Sitzung und geordneter Übermittlung von Nachrichten verwendet.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Erstellen Sie eine *Service. svc* -Datei, die die folgende Zeile enthält:

   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Platzieren Sie die Datei " *Service. svc* " in Ihrem virtuellen Verzeichnis für Internetinformationsdienste (IIS).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurieren des Clients mit WSHttpBinding zur Verwendung einer zuverlässigen Sitzung

1. Verwenden Sie das [Service Model Metadata Utility-Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) von der Befehlszeile aus, um Code aus Dienst Metadaten zu generieren:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Der generierte Client enthält die `ICalculator` Schnittstelle, die den Dienstvertrag definiert, den die Client Implementierung erfüllen muss.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. Die generierte Clientanwendung enthält außerdem die Implementierung von `ClientCalculator`. Beachten Sie, dass die Adress-und Bindungs Informationen nicht in der Implementierung des Dienstanbieter angegeben werden. Sie müssen keinen Code schreiben, um die Adresse oder die Bindungs Informationen aus der Konfigurationsdatei abzurufen.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe* generiert auch die Konfiguration für den Client, der die- <xref:System.ServiceModel.WSHttpBinding> Klasse verwendet. Benennen Sie die Konfigurationsdatei *App.config* , wenn Sie Visual Studio verwenden.

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Erstellen Sie eine Instanz von `ClientCalculator` in einer Anwendung, und rufen Sie die Dienst Vorgänge auf.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Kompilieren Sie den Code, und führen Sie den Client aus.

## <a name="example"></a>Beispiel

Mehrere der vom System bereitgestellten Bindungen unterstützen standardmäßig zuverlässige Sitzungen. Dazu gehören:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Ein Beispiel für das Erstellen einer benutzerdefinierten Bindung, die zuverlässige Sitzungen unterstützt, finden Sie unter Gewusst [wie: Erstellen einer benutzerdefinierten zuverlässigen Sitzungs Bindung mit HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Siehe auch

- [Zuverlässige Sitzungen](reliable-sessions.md)
