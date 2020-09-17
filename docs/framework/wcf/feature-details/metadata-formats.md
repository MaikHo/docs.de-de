---
title: Metadatenformate
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: 01f0d7a2212b2af7e2d3a959ed91624edec46ce8
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720464"
---
# <a name="metadata-formats"></a>Metadatenformate

Windows Communication Foundation (WCF) unterstützt die Metadatenformate in der folgenden Tabelle.  
  
## <a name="metadata-specifications-and-usage"></a>Metadatenspezifikation und -verwendung  
  
|Protokoll|Spezifikation und Verwendung|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1.1 (in englischer Sprache)](https://www.w3.org/TR/wsdl/)<br /><br /> WCF verwendet Web Services Description Language (WSDL) zum Beschreiben von Diensten.|  
|XML-Schema|[XML Schema Part 2: Datatypes Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/) und [XML Schema Part 1: Structures Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)<br /><br /> WCF verwendet das XML-Schema, um die in Nachrichten verwendeten Datentypen zu beschreiben.|  
|WS-Richtlinie|[-Web Services Policy 1.2 &amp;#8211; Framework (WS-Richtlinie) (Seite möglicherweise auf Englisch)](https://www.w3.org/Submission/WS-Policy/)<br /><br /> [Web Services Policy 1.5 &amp;#8211; Framework  (Seite möglicherweise auf Englisch)](https://www.w3.org/TR/ws-policy/)<br /><br /> WCF verwendet die WS-Policy 1,2-oder 1,5-Spezifikationen mit domänenspezifischen Assertionen, um Dienst Anforderungen und-Funktionen zu beschreiben.|  
|WS-Richtlinienanhänge|[Web Services Policy 1.2 &amp;#8211; Attachment (WS-PolicyAttachment)  (Seite möglicherweise auf Englisch)](https://www.w3.org/Submission/WS-PolicyAttachment/)<br /><br /> WCF implementiert WS-Richtlinien Anhänge, um Richtlinien Ausdrücke in verschiedenen Bereichen in WSDL anzufügen.|  
|WS-Metadatenaustausch|[Web Services Metadata Exchange (WS-MetadataExchange) Version 1.1  (Seite möglicherweise auf Englisch)](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implementiert WS-MetadataExchange zum Abrufen von XML-Schema, WSDL und WS-Policy.|  
|WS-Adressierungsbindung für WSDL|[Web Services Addressing 1.0 - WSDL-Bindung (in englischer Sprache)](https://www.w3.org/TR/ws-addr-wsdl/)<br /><br /> WCF implementiert die WS-Adressierungs Bindung für WSDL, um Adressierungs Informationen in WSDL anzufügen.|  
  
## <a name="see-also"></a>Weitere Informationen

- [Durch vom System bereitgestellte Interoperabilitätsbindungen unterstützte Webdienstprotokolle](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL und Richtlinie](wsdl-and-policy.md)
