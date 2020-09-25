---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 0a8cc60226b13552d47faec3a156ed1f59acacb9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181400"
---
# \<pnrpPeerResolver>

<span data-ttu-id="a6bfd-101">Gibt an, dass der PNRP (Peer Name Resolution-Protokoll)-Resolver als Resolver verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a6bfd-101">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="a6bfd-102">Dieses Element ist optional, da das PNRP der Standardresolver ist.</span><span class="sxs-lookup"><span data-stu-id="a6bfd-102">This element is optional because PNRP is the default resolver.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="a6bfd-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="a6bfd-103">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6bfd-104">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a6bfd-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a6bfd-105">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a6bfd-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6bfd-106">Attribute</span><span class="sxs-lookup"><span data-stu-id="a6bfd-106">Attributes</span></span>  
  
|<span data-ttu-id="a6bfd-107">attribute</span><span class="sxs-lookup"><span data-stu-id="a6bfd-107">Attribute</span></span>|<span data-ttu-id="a6bfd-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a6bfd-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6bfd-109">resolverType</span><span class="sxs-lookup"><span data-stu-id="a6bfd-109">resolverType</span></span>|<span data-ttu-id="a6bfd-110">Eine Zeichenfolge, die den zu verwendenden Resolver angibt.</span><span class="sxs-lookup"><span data-stu-id="a6bfd-110">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="a6bfd-111">Dieses Attribut ist optional.</span><span class="sxs-lookup"><span data-stu-id="a6bfd-111">This attribute is optional.</span></span> <span data-ttu-id="a6bfd-112">Wenn es nicht festgelegt wurde oder eine leere Zeichenfolge angegeben wurde, wird das PNRP verwendet.</span><span class="sxs-lookup"><span data-stu-id="a6bfd-112">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6bfd-113">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a6bfd-113">Child Elements</span></span>  

 <span data-ttu-id="a6bfd-114">Keine</span><span class="sxs-lookup"><span data-stu-id="a6bfd-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6bfd-115">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a6bfd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a6bfd-116">Element</span><span class="sxs-lookup"><span data-stu-id="a6bfd-116">Element</span></span>|<span data-ttu-id="a6bfd-117">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a6bfd-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="a6bfd-118">Definiert alle Bindungsmöglichkeiten der benutzerdefinierten Bindung.</span><span class="sxs-lookup"><span data-stu-id="a6bfd-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a6bfd-119">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a6bfd-119">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="a6bfd-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a6bfd-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a6bfd-121">Bindungen</span><span class="sxs-lookup"><span data-stu-id="a6bfd-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a6bfd-122">Erweitern von Bindungen</span><span class="sxs-lookup"><span data-stu-id="a6bfd-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a6bfd-123">Benutzerdefinierte Bindungen</span><span class="sxs-lookup"><span data-stu-id="a6bfd-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="a6bfd-124">Peerresolver</span><span class="sxs-lookup"><span data-stu-id="a6bfd-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
