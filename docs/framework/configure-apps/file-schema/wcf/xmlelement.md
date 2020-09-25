---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 0ab7fbd64cc92e940617f5334eeb16fcb3a50c4a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181231"
---
# \<xmlElement>

<span data-ttu-id="b33bf-101">Gibt ein XML-Element an, das bei der Anforderung eines Tokens im Textkörper an den Sicherheitstokendienst gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="b33bf-101">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="b33bf-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="b33bf-102">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b33bf-103">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="b33bf-103">Attributes and Elements</span></span>  

 <span data-ttu-id="b33bf-104">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b33bf-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b33bf-105">Attribute</span><span class="sxs-lookup"><span data-stu-id="b33bf-105">Attributes</span></span>  
  
|<span data-ttu-id="b33bf-106">attribute</span><span class="sxs-lookup"><span data-stu-id="b33bf-106">Attribute</span></span>|<span data-ttu-id="b33bf-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b33bf-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b33bf-108">xmlElement</span><span class="sxs-lookup"><span data-stu-id="b33bf-108">xmlElement</span></span>|<span data-ttu-id="b33bf-109">Eine Zeichenfolge, die ein XML-Element angibt, das bei der Anforderung eines Tokens im Textkörper an den Sicherheitstokendienst gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="b33bf-109">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b33bf-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b33bf-110">Child Elements</span></span>  

 <span data-ttu-id="b33bf-111">Keine</span><span class="sxs-lookup"><span data-stu-id="b33bf-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b33bf-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b33bf-112">Parent Elements</span></span>  
  
|<span data-ttu-id="b33bf-113">Element</span><span class="sxs-lookup"><span data-stu-id="b33bf-113">Element</span></span>|<span data-ttu-id="b33bf-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b33bf-114">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="b33bf-115">Eine Auflistung von Tokenanforderungsparametern.</span><span class="sxs-lookup"><span data-stu-id="b33bf-115">A collection of token request parameters.</span></span> <span data-ttu-id="b33bf-116">Jeder Parameter ist ein XML-Element.</span><span class="sxs-lookup"><span data-stu-id="b33bf-116">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b33bf-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b33bf-117">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="b33bf-118">Dienstidentität und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="b33bf-118">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b33bf-119">Verbund und ausgestellte Token</span><span class="sxs-lookup"><span data-stu-id="b33bf-119">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b33bf-120">Sicherheitsfunktionen mit benutzerdefinierten Bindungen</span><span class="sxs-lookup"><span data-stu-id="b33bf-120">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="b33bf-121">Verbund und ausgestellte Token</span><span class="sxs-lookup"><span data-stu-id="b33bf-121">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b33bf-122">Bindungen</span><span class="sxs-lookup"><span data-stu-id="b33bf-122">Bindings</span></span>](../../../wcf/bindings.md)
