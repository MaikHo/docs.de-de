---
title: <add>-Element für bypasslist (Netzwerkeinstellungen)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 927a43f352fd776d9e6ba52ebea6ba2a1ccd4d48
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149490"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="560c6-102">\<add>-Element für bypasslist (Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="560c6-102">\<add> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="560c6-103">Fügt der Proxy Umgehungs Liste eine IP-Adresse oder einen DNS-Namen hinzu.</span><span class="sxs-lookup"><span data-stu-id="560c6-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="560c6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="560c6-104">Syntax</span></span>  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="560c6-105">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="560c6-105">Attributes and Elements</span></span>  

 <span data-ttu-id="560c6-106">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="560c6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="560c6-107">Attribute</span><span class="sxs-lookup"><span data-stu-id="560c6-107">Attributes</span></span>  
  
|<span data-ttu-id="560c6-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="560c6-108">**Attribute**</span></span>|<span data-ttu-id="560c6-109">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="560c6-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="560c6-110">**address**</span><span class="sxs-lookup"><span data-stu-id="560c6-110">**address**</span></span>|<span data-ttu-id="560c6-111">Einen regulären Ausdruck, der eine IP-Adresse oder einen DNS-Namen beschreibt.</span><span class="sxs-lookup"><span data-stu-id="560c6-111">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="560c6-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="560c6-112">Child Elements</span></span>  

 <span data-ttu-id="560c6-113">Keine</span><span class="sxs-lookup"><span data-stu-id="560c6-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="560c6-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="560c6-114">Parent Elements</span></span>  
  
|<span data-ttu-id="560c6-115">**Element**</span><span class="sxs-lookup"><span data-stu-id="560c6-115">**Element**</span></span>|<span data-ttu-id="560c6-116">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="560c6-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="560c6-117">bypasslist</span><span class="sxs-lookup"><span data-stu-id="560c6-117">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="560c6-118">Stellt eine Reihe von regulären Ausdrücken bereit, die Adressen beschreiben, die keinen Proxy verwenden.</span><span class="sxs-lookup"><span data-stu-id="560c6-118">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="560c6-119">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="560c6-119">Remarks</span></span>  

 <span data-ttu-id="560c6-120">Das `add` -Element fügt reguläre Ausdrücke, die IP-Adressen oder DNS-Servernamen beschreiben, in die Liste der Adressen ein, die einen Proxy Server umgehen.</span><span class="sxs-lookup"><span data-stu-id="560c6-120">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="560c6-121">Der Wert des `address` -Attributs muss ein regulärer Ausdruck sein, der einen Satz von IP-Adressen oder Hostnamen beschreibt.</span><span class="sxs-lookup"><span data-stu-id="560c6-121">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="560c6-122">Sie sollten Vorsicht walten lassen, wenn Sie einen regulären Ausdruck für dieses Element angeben.</span><span class="sxs-lookup"><span data-stu-id="560c6-122">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="560c6-123">Der reguläre Ausdruck "[a-z] + \\ ..................................... \\</span><span class="sxs-lookup"><span data-stu-id="560c6-123">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="560c6-124">Um nur einen Host in der contoso.com-Domäne zu finden, verwenden Sie einen Anker ("$"): "[a-z] + \\ .. \\ .</span><span class="sxs-lookup"><span data-stu-id="560c6-124">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="560c6-125">Weitere Informationen zu regulären Ausdrücken finden Sie unter. [.NET Framework reguläre Ausdrücke](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="560c6-125">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="560c6-126">Konfigurationsdateien</span><span class="sxs-lookup"><span data-stu-id="560c6-126">Configuration Files</span></span>  

 <span data-ttu-id="560c6-127">Dieses Element kann in der Anwendungskonfigurationsdatei oder in der Computerkonfigurationsdatei ("Machine.config") verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="560c6-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="560c6-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="560c6-128">Example</span></span>  

 <span data-ttu-id="560c6-129">Im folgenden Beispiel werden der Umgehungs Liste zwei Adressen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="560c6-129">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="560c6-130">Der erste umgeht den Proxy für alle Server in der contoso.com-Domäne. mit dem zweiten wird der Proxy für alle Server umgangen, deren IP-Adresse mit 192,168 beginnt.</span><span class="sxs-lookup"><span data-stu-id="560c6-130">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="560c6-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="560c6-131">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="560c6-132">Network Settings Schema (Schema für Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="560c6-132">Network Settings Schema</span></span>](index.md)
