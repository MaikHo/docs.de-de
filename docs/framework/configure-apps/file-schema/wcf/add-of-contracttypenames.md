---
title: <add> von <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 69a0bbbc8774251dbdc062875bb06453f355c882
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149139"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="67aee-102">\<add> von \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="67aee-102">\<add> of \<contractTypeNames></span></span>

<span data-ttu-id="67aee-103">Ein Konfigurationselement, das den Vertragsnamen der Dienste angibt, nach denen gesucht wird, sowie die Kriterien, die normalerweise beim Suchen nach einem Dienst verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="67aee-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="67aee-104">Wenn mehr als ein Vertragsname angegeben wird, antworten nur Dienstendpunkte, die ALLEN Verträgen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="67aee-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="67aee-105">Beachten Sie, dass ein Endpunkt in Windows Communication Foundation (WCF) nur einen Vertrag unterstützen kann.</span><span class="sxs-lookup"><span data-stu-id="67aee-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="67aee-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="67aee-106">Syntax</span></span>  
  
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
              <add name="String" namespace="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67aee-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="67aee-107">Attributes and Elements</span></span>  

 <span data-ttu-id="67aee-108">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="67aee-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67aee-109">Attribute</span><span class="sxs-lookup"><span data-stu-id="67aee-109">Attributes</span></span>  
  
|<span data-ttu-id="67aee-110">attribute</span><span class="sxs-lookup"><span data-stu-id="67aee-110">Attribute</span></span>|<span data-ttu-id="67aee-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="67aee-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67aee-112">name</span><span class="sxs-lookup"><span data-stu-id="67aee-112">name</span></span>|<span data-ttu-id="67aee-113">Eine Zeichenfolge, die den Namen des Vertragstyps angibt.</span><span class="sxs-lookup"><span data-stu-id="67aee-113">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="67aee-114">Namespace</span><span class="sxs-lookup"><span data-stu-id="67aee-114">namespace</span></span>|<span data-ttu-id="67aee-115">Eine Zeichenfolge, die den Namespace des Vertragstyps angibt.</span><span class="sxs-lookup"><span data-stu-id="67aee-115">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67aee-116">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="67aee-116">Child Elements</span></span>  

 <span data-ttu-id="67aee-117">Keine</span><span class="sxs-lookup"><span data-stu-id="67aee-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67aee-118">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="67aee-118">Parent Elements</span></span>  
  
|<span data-ttu-id="67aee-119">Element</span><span class="sxs-lookup"><span data-stu-id="67aee-119">Element</span></span>|<span data-ttu-id="67aee-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="67aee-120">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="67aee-121">Eine Auflistung von Vertragstypnamen.</span><span class="sxs-lookup"><span data-stu-id="67aee-121">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67aee-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="67aee-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
