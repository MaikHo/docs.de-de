---
title: <mailSettings>-Element (Netzwerkeinstellungen)
description: Das <mailSettings> Netzwerk Einstellungs Element konfiguriert die Optionen für das Senden von e-Mails in der .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: a146874acc21f52507b37b1751c648792e23c8bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158850"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="237d4-103">\<mailSettings>-Element (Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="237d4-103">\<mailSettings> Element (Network Settings)</span></span>

<span data-ttu-id="237d4-104">Konfiguriert E-Mail-Sendeoptionen.</span><span class="sxs-lookup"><span data-stu-id="237d4-104">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="237d4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="237d4-105">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="237d4-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="237d4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="237d4-107">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="237d4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="237d4-108">Attribute</span><span class="sxs-lookup"><span data-stu-id="237d4-108">Attributes</span></span>  

 <span data-ttu-id="237d4-109">Keine</span><span class="sxs-lookup"><span data-stu-id="237d4-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="237d4-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="237d4-110">Child Elements</span></span>  
  
|<span data-ttu-id="237d4-111">attribute</span><span class="sxs-lookup"><span data-stu-id="237d4-111">Attribute</span></span>|<span data-ttu-id="237d4-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="237d4-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="237d4-113">\<smtp>-Element (Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="237d4-113">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="237d4-114">Konfiguriert die Optionen des Simple Mail-Transport Protokolls.</span><span class="sxs-lookup"><span data-stu-id="237d4-114">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="237d4-115">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="237d4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="237d4-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="237d4-116">**Element**</span></span>|<span data-ttu-id="237d4-117">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="237d4-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="237d4-118">\<system.Net>-Element (Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="237d4-118">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="237d4-119">Enthält Einstellungen, die festlegen, wie Verbindungen zwischen .NET Framework und dem Netzwerk hergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="237d4-119">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="237d4-120">Beispiel</span><span class="sxs-lookup"><span data-stu-id="237d4-120">Example</span></span>  

 <span data-ttu-id="237d4-121">Im folgenden Beispiel werden die entsprechenden SMTP-Parameter zum Senden von e-Mails mit den standardmäßigen Netzwerk Anmelde Informationen angegeben.</span><span class="sxs-lookup"><span data-stu-id="237d4-121">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="237d4-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="237d4-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="237d4-123">Network Settings Schema (Schema für Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="237d4-123">Network Settings Schema</span></span>](index.md)
