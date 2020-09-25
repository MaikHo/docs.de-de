---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 08ca8a2bfcf5b905152f7e64a45cbae4992a7b78
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192372"
---
# \<defaultPorts>

<span data-ttu-id="ebb0d-101">Eine Auflistung von Standardports mit den Standardkommunikationsendpunkten, die von der Clientanwendung überwacht werden.</span><span class="sxs-lookup"><span data-stu-id="ebb0d-101">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="ebb0d-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="ebb0d-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebb0d-103">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="ebb0d-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ebb0d-104">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ebb0d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebb0d-105">Attribute</span><span class="sxs-lookup"><span data-stu-id="ebb0d-105">Attributes</span></span>  

 <span data-ttu-id="ebb0d-106">Keine</span><span class="sxs-lookup"><span data-stu-id="ebb0d-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ebb0d-107">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ebb0d-107">Child Elements</span></span>  
  
|<span data-ttu-id="ebb0d-108">Element</span><span class="sxs-lookup"><span data-stu-id="ebb0d-108">Element</span></span>|<span data-ttu-id="ebb0d-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ebb0d-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ebb0d-110">\<add> von \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="ebb0d-110">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="ebb0d-111">Ein Standardkommunikationsendpunkt, den die Clientanwendung überwacht.</span><span class="sxs-lookup"><span data-stu-id="ebb0d-111">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ebb0d-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ebb0d-112">Parent Elements</span></span>  
  
|<span data-ttu-id="ebb0d-113">Element</span><span class="sxs-lookup"><span data-stu-id="ebb0d-113">Element</span></span>|<span data-ttu-id="ebb0d-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ebb0d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="ebb0d-115">Eine Liste von Standardports.</span><span class="sxs-lookup"><span data-stu-id="ebb0d-115">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ebb0d-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ebb0d-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
