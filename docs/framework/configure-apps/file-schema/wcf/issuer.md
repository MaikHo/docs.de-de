---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 9e92bbcacf529a97e1ae936e93e38c98eab19cab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157264"
---
# \<issuer>

<span data-ttu-id="8965c-101">Gibt den Sicherheitstokendienst an, der Sicherheitstoken ausstellt.</span><span class="sxs-lookup"><span data-stu-id="8965c-101">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="8965c-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="8965c-102">Syntax</span></span>  
  
```xml  
<issuer address="Uri">
  <headers>
    <add name="String"
         namespace="String" />
  </headers>
  <identity>
    <certificate encodedValue="String" />
    <certificateReference findValue="String"
                          isChainIncluded="Boolean"
                          storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                          storeLocation="LocalMachine/CurrentUser"
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8965c-103">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="8965c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="8965c-104">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente sowie übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8965c-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8965c-105">Attributes</span><span class="sxs-lookup"><span data-stu-id="8965c-105">Attributes</span></span>  
  
|<span data-ttu-id="8965c-106">attribute</span><span class="sxs-lookup"><span data-stu-id="8965c-106">Attribute</span></span>|<span data-ttu-id="8965c-107">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="8965c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8965c-108">address</span><span class="sxs-lookup"><span data-stu-id="8965c-108">address</span></span>|<span data-ttu-id="8965c-109">Erforderliche Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="8965c-109">Required string.</span></span> <span data-ttu-id="8965c-110">Die URL des STS.</span><span class="sxs-lookup"><span data-stu-id="8965c-110">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8965c-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8965c-111">Child Elements</span></span>  
  
|<span data-ttu-id="8965c-112">Element</span><span class="sxs-lookup"><span data-stu-id="8965c-112">Element</span></span>|<span data-ttu-id="8965c-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8965c-113">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="8965c-114">Eine Auflistung mit Adressheadern für die Endpunkte, die vom Generator erstellt werden können.</span><span class="sxs-lookup"><span data-stu-id="8965c-114">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="8965c-115">Gibt bei Verwendung eines ausgestellten Tokens die Einstellungen an, mit denen der Client den Server authentifizieren kann.</span><span class="sxs-lookup"><span data-stu-id="8965c-115">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8965c-116">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8965c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8965c-117">Element</span><span class="sxs-lookup"><span data-stu-id="8965c-117">Element</span></span>|<span data-ttu-id="8965c-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8965c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="8965c-119">Definiert die Einstellungen für die Sicherheit auf Nachrichten Ebene für das- [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) Element.</span><span class="sxs-lookup"><span data-stu-id="8965c-119">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8965c-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8965c-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="8965c-121">Dienstidentität und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="8965c-121">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8965c-122">Verbund und ausgestellte Token</span><span class="sxs-lookup"><span data-stu-id="8965c-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8965c-123">Dienstidentität und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="8965c-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8965c-124">Verbund und ausgestellte Token</span><span class="sxs-lookup"><span data-stu-id="8965c-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8965c-125">Sicherheitsfunktionen mit benutzerdefinierten Bindungen</span><span class="sxs-lookup"><span data-stu-id="8965c-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="8965c-126">Verbund und ausgestellte Token</span><span class="sxs-lookup"><span data-stu-id="8965c-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
