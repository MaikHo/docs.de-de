---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 6e3f273af807eb362f005fef63246013ecc88581
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192242"
---
# \<discoveryClientSettings>

<span data-ttu-id="a4828-101">Enthält die Einstellungen, die von einer Anwendung benötigt werden, um am Dienstermittlungsprozess als Client teilzunehmen.</span><span class="sxs-lookup"><span data-stu-id="a4828-101">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="a4828-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4828-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4828-103">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a4828-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a4828-104">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a4828-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4828-105">Attribute</span><span class="sxs-lookup"><span data-stu-id="a4828-105">Attributes</span></span>  
  
|<span data-ttu-id="a4828-106">attribute</span><span class="sxs-lookup"><span data-stu-id="a4828-106">Attribute</span></span>|<span data-ttu-id="a4828-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a4828-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4828-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="a4828-108">discoveryEndpoint</span></span>|<span data-ttu-id="a4828-109">Eine Zeichenfolge mit dem Namen des Ermittlungsendpunkts, der einer Clientanwendung ermöglicht, automatisch nach einem sichtbaren Dienst zu suchen und zur Laufzeit dessen Adresse abzurufen.</span><span class="sxs-lookup"><span data-stu-id="a4828-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4828-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a4828-110">Child Elements</span></span>  
  
|<span data-ttu-id="a4828-111">Element</span><span class="sxs-lookup"><span data-stu-id="a4828-111">Element</span></span>|<span data-ttu-id="a4828-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a4828-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="a4828-113">Ein Konfigurationselement, das einen Kriteriensatz bereitstellt, der von einer Clientanwendung zum Suchen nach einem Ermittlungsdienst verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a4828-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="a4828-114">Kriterien können in Suchkriterien (nach welchen Diensten soll gesucht werden) und Beendigungskriterien für die Suche (wie lange soll die Suche dauern) gruppiert werden.</span><span class="sxs-lookup"><span data-stu-id="a4828-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4828-115">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a4828-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a4828-116">Element</span><span class="sxs-lookup"><span data-stu-id="a4828-116">Element</span></span>|<span data-ttu-id="a4828-117">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a4828-117">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="a4828-118">Definiert einen Standardendpunkt, der Informationen enthält, mit denen eine Anwendung als Clientprogramm aktiviert wird, das die Endpunktadresse zur Laufzeit dynamisch suchen kann.</span><span class="sxs-lookup"><span data-stu-id="a4828-118">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4828-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a4828-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
