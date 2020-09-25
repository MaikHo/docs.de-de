---
title: <requestCaching>-Element (Netzwerkeinstellungen)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: 3eb32b7ae643efdb19892410b669c1e7ff80e0ad
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174159"
---
# <a name="requestcaching-element-network-settings"></a>\<requestCaching>-Element (Netzwerkeinstellungen)

Steuert den zwischen Speicherungs Mechanismus für Netzwerk Anforderungen.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh:mm:ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  

 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`isPrivateCache`|Gibt an, ob der Cache eine Isolation zwischen den Informationen verschiedener Benutzer bereitstellt. Standardwert: `true`. Dieser Wert sollte `false` für Anwendungen der mittleren Ebene sein.|  
|`disableAllCaching`|Gibt an, dass das Zwischenspeichern für alle Webanwendungen deaktiviert ist und nicht Programm gesteuert überschrieben werden kann.|  
|`defaultPolicyLevel`|Einer der Werte in der <xref:System.Net.Cache.RequestCacheLevel>-Enumeration. Standardwert: `BypassCache`.|  
|`unspecifiedMaximumAge`|Gibt die Standardzeit an, nach der der Inhalt als abgelaufen gekennzeichnet wird.|  
  
## <a name="policylevel-attribute"></a>PolicyLevel-Attribut  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`Default`|Gibt die zwischengespeicherte Ressource zurück, wenn die Ressource neu ist, die Länge des Inhalts genau ist und die Attribute für die Ablauf-, Änderungs-und Inhalts Länge vorhanden sind.|  
|`BypassCache`|Gibt die Ressource vom Server zurück.|  
|`CacheOnly`|Gibt die zwischengespeicherte Ressource zurück, wenn die Inhalts Länge vorhanden ist und mit der Eingabe Größe übereinstimmt.|  
|`CacheIfAvailable`|Gibt die zwischengespeicherte Ressource zurück, wenn die Inhalts Länge angegeben wird und mit der Eintrags Größe übereinstimmt. Andernfalls wird die Ressource vom Server heruntergeladen und an den Aufrufer zurückgegeben.|  
|`Revalidate`|Gibt die zwischengespeicherte Ressource zurück, wenn der Zeitstempel der zwischengespeicherten Ressource mit dem Zeitstempel der Ressource auf dem Server identisch ist. Andernfalls wird die Ressource vom Server heruntergeladen, im Cache gespeichert und an den Aufrufer zurückgegeben.|  
|`Reload`|Lädt die Ressource vom Server herunter, speichert Sie im Cache und gibt die Ressource an den Aufrufer zurück.|  
|`NoCacheNoStore`|Wenn eine zwischengespeicherte Ressource vorhanden ist, wird Sie gelöscht. Die Ressource wird vom Server heruntergeladen und an den Aufrufer zurückgegeben.|  
|`Revalidate`|Erfüllt eine Anforderung mithilfe der zwischengespeicherten Kopie der Ressource, wenn der Zeitstempel mit dem Zeitstempel der Ressource auf dem Server identisch ist. Andernfalls wird die Ressource vom Server heruntergeladen, dem Aufrufer präsentiert und im Cache gespeichert.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](defaulthttpcachepolicy-element-network-settings.md)|Optionales Element.<br /><br /> Beschreibt, ob HTTP-Zwischenspeicherung aktiviert ist, und beschreibt die Standard Cache Richtlinie.|  
|[\<defaultFtpCachePolicy>-Element (Netzwerkeinstellungen)](defaultftpcachepolicy-element-network-settings.md)|Optionales Element.<br /><br /> Beschreibt, ob das FTP-Caching aktiv ist, und beschreibt die Standard Cache Richtlinie.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|Enthält Einstellungen, die festlegen, wie Verbindungen zwischen .NET Framework und dem Netzwerk hergestellt werden.|  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird gezeigt, wie alle zwischen Speicherungen deaktiviert werden.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Weitere Informationen

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [Network Settings Schema (Schema für Netzwerkeinstellungen)](index.md)
