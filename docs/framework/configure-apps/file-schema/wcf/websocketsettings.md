---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 6cfddfb9ebfc7c3447af977e14738baabebc8fe9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177850"
---
# \<webSocketSettings>

Ein Konfigurationselement zum Angeben von WebSocket-Einstellungen.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  

 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|createNotificationOnConnection|Gibt an, ob eine Benachrichtigung bei Zustandekommen einer Verbindung gesendet wird.|  
|disablePayloadMasking|Gibt an, ob die WebSocket-Maske deaktiviert ist.|  
|keepAliveInterval|Gibt das Keep-Alive-Intervall an.|  
|maxPendingConnections|Gibt die maximale Anzahl von Verbindungen an, die im Dienst zum Verteilen bereitstehen.|  
|receiveBufferSize|Gibt die Größe des Empfangspuffers an.|  
|sendBufferSize|Gibt die Größe des Sendepuffers an.|  
|subProtocol|Gibt das WebSocket-Unterprotokoll an.|  
|transportUsage|Gibt an, wann WebSockets verwendet wird.|  
  
## <a name="transportusage-attribute"></a>transportUsage-Attribut  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|WhenDuplex|Verwendet das WebSocket-Protokoll bei einem Duplexvertrag.|  
|Always|Verwendet immer das WebSocket-Protokoll unabhängig vom Vertrag.|  
|Nie|Verwendet niemals das WebSocket-Protokoll.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  

 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|\<netHttpBinding>|Gibt das NetHttpBinding-Element an.|  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird die Verwendung des \<webSocketSettings>-Elements veranschaulicht.  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a>Weitere Informationen

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Bindungen](../../../wcf/bindings.md)
- [Konfigurieren der vom System bereitgestellten Bindungen](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Verwenden von Bindungen, um Dienste und Clients zu konfigurieren](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
