---
title: <smtp>-Element (Netzwerkeinstellungen)
description: Das <smtp> Netzwerk Einstellungs Element konfiguriert das Übermittlungs Format, die Übermittlungs Methode und die Absenderadresse für das Senden von e-Mail-Optionen in der .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 58f496b4a07f7d5531df897dd54bb6176111f1c4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178319"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="3b518-103">\<smtp>-Element (Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="3b518-103">\<smtp> Element (Network Settings)</span></span>

<span data-ttu-id="3b518-104">Konfiguriert das Übermittlungs Format, die Übermittlungs Methode und die Absenderadresse für das Senden von e-Mails.</span><span class="sxs-lookup"><span data-stu-id="3b518-104">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="3b518-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3b518-105">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b518-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="3b518-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3b518-107">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="3b518-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b518-108">Attribute</span><span class="sxs-lookup"><span data-stu-id="3b518-108">Attributes</span></span>  
  
|<span data-ttu-id="3b518-109">attribute</span><span class="sxs-lookup"><span data-stu-id="3b518-109">Attribute</span></span>|<span data-ttu-id="3b518-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3b518-110">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="3b518-111">Gibt das Übermittlungs Format für ausgehende e-Mails an.</span><span class="sxs-lookup"><span data-stu-id="3b518-111">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="3b518-112">Zulässige Werte sind "SevenBit" und "International".</span><span class="sxs-lookup"><span data-stu-id="3b518-112">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="3b518-113">Gibt die Übermittlungs Methode für e-Mails an.</span><span class="sxs-lookup"><span data-stu-id="3b518-113">Specifies the delivery method for emails.</span></span> <span data-ttu-id="3b518-114">Zulässige Werte sind Network, pickupdirectoriyfromiis und SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="3b518-114">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="3b518-115">Gibt die from-Adresse für ausgehende e-Mails an.</span><span class="sxs-lookup"><span data-stu-id="3b518-115">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b518-116">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3b518-116">Child Elements</span></span>  
  
|<span data-ttu-id="3b518-117">attribute</span><span class="sxs-lookup"><span data-stu-id="3b518-117">Attribute</span></span>|<span data-ttu-id="3b518-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3b518-118">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="3b518-119">Konfiguriert das lokale Verzeichnis für einen SMTP (Simple Mail Transport Protocol)-Server.</span><span class="sxs-lookup"><span data-stu-id="3b518-119">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="3b518-120">Konfiguriert die Netzwerkoptionen für einen externen SMTP-Server.</span><span class="sxs-lookup"><span data-stu-id="3b518-120">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3b518-121">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3b518-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3b518-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="3b518-122">**Element**</span></span>|<span data-ttu-id="3b518-123">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="3b518-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3b518-124">\<mailSettings>-Element (Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="3b518-124">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="3b518-125">Konfiguriert E-Mail-Sendeoptionen.</span><span class="sxs-lookup"><span data-stu-id="3b518-125">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3b518-126">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3b518-126">Example</span></span>  

 <span data-ttu-id="3b518-127">Im folgenden Beispiel werden die entsprechenden SMTP-Parameter zum Senden von e-Mails mit den standardmäßigen Netzwerk Anmelde Informationen angegeben.</span><span class="sxs-lookup"><span data-stu-id="3b518-127">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
  
## <a name="see-also"></a><span data-ttu-id="3b518-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3b518-128">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="3b518-129">Network Settings Schema (Schema für Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="3b518-129">Network Settings Schema</span></span>](index.md)
