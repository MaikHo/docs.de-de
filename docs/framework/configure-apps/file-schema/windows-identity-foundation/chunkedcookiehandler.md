---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: a321c10e04eca2c1a5204929966a1725e918cbdf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158525"
---
# \<chunkedCookieHandler>

<span data-ttu-id="92704-101">Konfiguriert den <xref:System.IdentityModel.Services.ChunkedCookieHandler> .</span><span class="sxs-lookup"><span data-stu-id="92704-101">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="92704-102">Dieses Element kann nur vorhanden sein, wenn das- `mode` Attribut des- `<cookieHandler>` Elements "Default" oder "Chunked" ist.</span><span class="sxs-lookup"><span data-stu-id="92704-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="92704-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="92704-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92704-104">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="92704-104">Attributes and Elements</span></span>  

 <span data-ttu-id="92704-105">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="92704-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92704-106">Attribute</span><span class="sxs-lookup"><span data-stu-id="92704-106">Attributes</span></span>  
  
|<span data-ttu-id="92704-107">attribute</span><span class="sxs-lookup"><span data-stu-id="92704-107">Attribute</span></span>|<span data-ttu-id="92704-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="92704-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92704-109">chunkSize</span><span class="sxs-lookup"><span data-stu-id="92704-109">chunkSize</span></span>|<span data-ttu-id="92704-110">Die maximale Größe der HTTP-Cookie-Daten für ein beliebiges HTTP-Cookie in Zeichen.</span><span class="sxs-lookup"><span data-stu-id="92704-110">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="92704-111">Beim Anpassen der Segmentgröße müssen Sie vorsichtig sein.</span><span class="sxs-lookup"><span data-stu-id="92704-111">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="92704-112">Webbrowser haben unterschiedliche Beschränkungen hinsichtlich der Größe von Cookies und der pro Domäne zulässigen Anzahl.</span><span class="sxs-lookup"><span data-stu-id="92704-112">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="92704-113">Die ursprüngliche Netscape-Spezifikation hat z. b. die folgenden Grenzwerte festgelegt: 300 Cookies Gesamt, 4096 Bytes pro Cookieheader (einschließlich Metadaten, nicht nur den Cookiewert) und 20 Cookies pro Domäne.</span><span class="sxs-lookup"><span data-stu-id="92704-113">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="92704-114">Der Standardwert ist „2000“.</span><span class="sxs-lookup"><span data-stu-id="92704-114">The default is 2000.</span></span> <span data-ttu-id="92704-115">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="92704-115">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92704-116">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="92704-116">Child Elements</span></span>  

 <span data-ttu-id="92704-117">Keine</span><span class="sxs-lookup"><span data-stu-id="92704-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92704-118">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="92704-118">Parent Elements</span></span>  
  
|<span data-ttu-id="92704-119">Element</span><span class="sxs-lookup"><span data-stu-id="92704-119">Element</span></span>|<span data-ttu-id="92704-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="92704-120">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="92704-121">Konfiguriert den <xref:System.IdentityModel.Services.CookieHandler> , den der <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) zum Lesen und Schreiben von Cookies verwendet.</span><span class="sxs-lookup"><span data-stu-id="92704-121">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92704-122">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="92704-122">Remarks</span></span>  

 <span data-ttu-id="92704-123">Wenn Sie einen angeben <xref:System.IdentityModel.Services.ChunkedCookieHandler> , indem Sie das- `mode` Attribut des- `<cookieHandler>` Elements auf "Default" oder "Chunked" festlegen, können Sie die Segmentgröße angeben, die der cookiehandler zum Lesen und Schreiben von Cookies verwendet, indem Sie ein untergeordnetes `<chunkedCookieHandler>` -Element einschließen und sein- `chunkSize` Attribut festlegen.</span><span class="sxs-lookup"><span data-stu-id="92704-123">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="92704-124">Wenn das- `<chunkedCookieHandler>` Element nicht vorhanden ist, wird die Standard Segmentgröße von 2000 Bytes verwendet.</span><span class="sxs-lookup"><span data-stu-id="92704-124">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="92704-125">Dieses Element kann nicht angegeben werden, wenn das- `mode` Attribut auf "Custom" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="92704-125">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="92704-126">Das- `<chunkedCookieHandler>` Element wird durch die- <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> Klasse dargestellt.</span><span class="sxs-lookup"><span data-stu-id="92704-126">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92704-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="92704-127">Example</span></span>  

 <span data-ttu-id="92704-128">Im folgenden Beispiel wird ein segmentierter cookiehandler konfiguriert, der Cookies in Blöcken von 3000 Bytes schreibt.</span><span class="sxs-lookup"><span data-stu-id="92704-128">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="92704-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="92704-129">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
