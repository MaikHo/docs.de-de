---
title: Netzwerkeinstellungsschema
description: Erfahren Sie mehr über das Schema der Netzwerkeinstellungen, die angeben, wie die .NET Framework eine Verbindung mit dem Internet herstellt und URIs behandelt.
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 8071fcfcdb16b6e71d8d7af05a704d8842b3e963
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158915"
---
# <a name="network-settings-schema"></a>Netzwerkeinstellungsschema

Netzwerkeinstellungen geben an, wie Verbindungen zwischen .NET Framework und dem Internet hergestellt werden.

\<system.net>Mit den Einstellungen wird angegeben, wie die .NET Framework eine Verbindung mit dem Netzwerk herstellt. In der folgenden Tabelle wird die Funktion der einzelnen untergeordneten Konfigurationselemente unter dem- [ \<system.Net> Element (Netzwerkeinstellungen)](system-net-element-network-settings.md)beschrieben.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[\<authenticationModules>-Element (Netzwerkeinstellungen)](authenticationmodules-element-network-settings.md)|Gibt die Module an, die zum Authentifizieren von Internetanforderungen verwendet werden.|  
|[\<connectionManagement>-Element (Netzwerkeinstellungen)](connectionmanagement-element-network-settings.md)|Gibt die maximale Anzahl von Verbindungen mit Internethosts an.|  
|[\<defaultProxy>-Element (Netzwerkeinstellungen)](defaultproxy-element-network-settings.md)|Gibt den Proxyserver an, der für HTTP-Anforderungen an das Internet verwendet wird.|  
|[\<mailSettings>-Element (Netzwerkeinstellungen)](mailsettings-element-network-settings.md)|Enthält Einstellungen für E-Mail-Sendeoptionen.|  
|[\<requestCaching>-Element (Netzwerkeinstellungen)](requestcaching-element-network-settings.md)|Steuert den zwischen Speicherungs Mechanismus für Netzwerk Anforderungen.|  
|[\<webRequestModules>-Element (Netzwerkeinstellungen)](webrequestmodules-element-network-settings.md)|Gibt die Module an, die zum Anfordern von Informationen von Internethosts verwendet werden.|  
  
Die \<uri> Einstellungen geben an, wie die .NET Framework Webadressen verarbeitet, die mithilfe von URIs (Uniform Resource Identifier) ausgedrückt werden. In der folgenden Tabelle wird die Funktion der einzelnen untergeordneten Konfigurationselemente unter dem- [ \<uri> Element (URI-Einstellungen)](uri-element-uri-settings.md)beschrieben.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[\<idn> -Element (URI-Einstellungen)](idn-element-uri-settings.md)|Gibt an, ob die Analyse für internationale Domänennamen (IDN) auf den Domänennamen angewendet wird.|  
|[\<iriParsing> -Element (URI-Einstellungen)](iriparsing-element-uri-settings.md)|Gibt an, ob die Analyse für internationale Ressourcenbezeichner (International Resource Identifier, IRI) auf <xref:System.Uri> angewendet wird und ob die IRI-Analyseregeln angewendet werden sollen.|  
|[\<schemeSettings> -Element (URI-Einstellungen)](schemesettings-element-uri-settings.md)|Gibt an, ob <xref:System.Uri> auf bestimmte Schemen analysiert wird.|  
  
## <a name="see-also"></a>Weitere Informationen

- [Konfigurieren von Internetanwendungen](../../../network-programming/configuring-internet-applications.md)
- [Konfigurationsdateischema](../index.md)
