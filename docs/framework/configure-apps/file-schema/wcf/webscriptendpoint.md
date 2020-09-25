---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: 5e3ca9c4a43432d7f5da6d8816b6a2b984851050
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177839"
---
# \<webScriptEndpoint>

<span data-ttu-id="2b7a5-101">Dieses Konfigurationselement definiert einen Standard Endpunkt mit einer Fixed- [\<webHttpBinding>](webhttpbinding.md) Bindung, die das-Verhalten automatisch hinzufügt [\<enableWebScript>](enablewebscript.md) .</span><span class="sxs-lookup"><span data-stu-id="2b7a5-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="2b7a5-102">Verwenden Sie diesen Endpunkt, wenn Sie einen Dienst schreiben, der von einer ASP.NET AJAX-Anwendung aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-102">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="2b7a5-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b7a5-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b7a5-104">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="2b7a5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="2b7a5-105">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b7a5-106">Attribute</span><span class="sxs-lookup"><span data-stu-id="2b7a5-106">Attributes</span></span>  
  
|<span data-ttu-id="2b7a5-107">attribute</span><span class="sxs-lookup"><span data-stu-id="2b7a5-107">Attribute</span></span>|<span data-ttu-id="2b7a5-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2b7a5-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b7a5-109">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="2b7a5-109">webEndpointType</span></span>|<span data-ttu-id="2b7a5-110">Eine Zeichenfolge, die den Typ des Endpunkts angibt.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-110">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b7a5-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2b7a5-111">Child Elements</span></span>  

 <span data-ttu-id="2b7a5-112">Keine</span><span class="sxs-lookup"><span data-stu-id="2b7a5-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b7a5-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2b7a5-113">Parent Elements</span></span>  
  
|<span data-ttu-id="2b7a5-114">Element</span><span class="sxs-lookup"><span data-stu-id="2b7a5-114">Element</span></span>|<span data-ttu-id="2b7a5-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2b7a5-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="2b7a5-116">Eine Auflistung von Standardendpunkten, bei denen es sich um vordefinierte Endpunkte handelt, für die eine oder mehrere Eigenschaften (Adresse, Bindung, Vertrag) fest vorgegeben sind.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b7a5-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2b7a5-117">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
