---
title: <connectionManagement>-Element (Netzwerkeinstellungen)
description: Das <connectionManagement> Netzwerk Einstellungs Element gibt die maximale Anzahl von Verbindungen mit einem Netzwerk Host in der .NET Framework an.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 52b780c739a00cb53694b547ee1a33c1b5d98c86
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167313"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="7f544-103">\<connectionManagement>-Element (Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="7f544-103">\<connectionManagement> Element (Network Settings)</span></span>

<span data-ttu-id="7f544-104">Gibt die maximale Anzahl von Verbindungen mit einem Netzwerkhost an.</span><span class="sxs-lookup"><span data-stu-id="7f544-104">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="7f544-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f544-105">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f544-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7f544-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7f544-107">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="7f544-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f544-108">Attribute</span><span class="sxs-lookup"><span data-stu-id="7f544-108">Attributes</span></span>  

 <span data-ttu-id="7f544-109">Keine</span><span class="sxs-lookup"><span data-stu-id="7f544-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7f544-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7f544-110">Child Elements</span></span>  
  
|<span data-ttu-id="7f544-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="7f544-111">**Element**</span></span>|<span data-ttu-id="7f544-112">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="7f544-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7f544-113">add</span><span class="sxs-lookup"><span data-stu-id="7f544-113">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="7f544-114">Fügt der Verbindungsverwaltungsliste eine IP-Adresse oder einen DNS-Namen hinzu.</span><span class="sxs-lookup"><span data-stu-id="7f544-114">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="7f544-115">Löschen</span><span class="sxs-lookup"><span data-stu-id="7f544-115">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="7f544-116">Löscht die Verbindungs Verwaltungsliste.</span><span class="sxs-lookup"><span data-stu-id="7f544-116">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="7f544-117">remove</span><span class="sxs-lookup"><span data-stu-id="7f544-117">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="7f544-118">Entfernt eine IP-Adresse oder einen DNS-Namen aus der Verbindungs Verwaltungsliste.</span><span class="sxs-lookup"><span data-stu-id="7f544-118">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f544-119">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7f544-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7f544-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="7f544-120">**Element**</span></span>|<span data-ttu-id="7f544-121">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="7f544-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7f544-122">system.net</span><span class="sxs-lookup"><span data-stu-id="7f544-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="7f544-123">Enthält Einstellungen, die festlegen, wie Verbindungen zwischen .NET Framework und dem Netzwerk hergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="7f544-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f544-124">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="7f544-124">Remarks</span></span>  

 <span data-ttu-id="7f544-125">Das- `connectionManagement` Element definiert die maximale Anzahl von Verbindungen mit einem Server oder einer Gruppe von Servern.</span><span class="sxs-lookup"><span data-stu-id="7f544-125">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7f544-126">Konfigurationsdateien</span><span class="sxs-lookup"><span data-stu-id="7f544-126">Configuration Files</span></span>  

 <span data-ttu-id="7f544-127">Dieses Element kann in der Anwendungskonfigurationsdatei oder in der Computerkonfigurationsdatei ("Machine.config") verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7f544-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f544-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7f544-128">Example</span></span>  

 <span data-ttu-id="7f544-129">Im folgenden Beispiel wird eine Anwendung so konfiguriert, dass vier Verbindungen mit dem Server `www.contoso.com` und zwei Verbindungen mit allen anderen Servern verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7f544-129">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f544-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7f544-130">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="7f544-131">Network Settings Schema (Schema für Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="7f544-131">Network Settings Schema</span></span>](index.md)
