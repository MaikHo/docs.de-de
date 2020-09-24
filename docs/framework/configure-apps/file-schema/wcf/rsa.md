---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 1698ce421b4dcefc6ab94206443d2d7bca47aca8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162282"
---
# \<rsa>

<span data-ttu-id="80e82-101">Ein sicherer WCF-Client, der mit dieser Identität eine Verbindung zu einem Endpunkt herstellt, stellt sicher, dass die vom Server bereitgestellten Ansprüche einen Anspruch beinhalten, der den zum Erstellen dieser Identität verwendeten öffentlichen RSA-Schlüssel enthält.</span><span class="sxs-lookup"><span data-stu-id="80e82-101">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="80e82-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="80e82-102">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80e82-103">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="80e82-103">Attributes and Elements</span></span>  

 <span data-ttu-id="80e82-104">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente sowie übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="80e82-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80e82-105">Attributes</span><span class="sxs-lookup"><span data-stu-id="80e82-105">Attributes</span></span>  
  
|<span data-ttu-id="80e82-106">attribute</span><span class="sxs-lookup"><span data-stu-id="80e82-106">Attribute</span></span>|<span data-ttu-id="80e82-107">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="80e82-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80e82-108">value</span><span class="sxs-lookup"><span data-stu-id="80e82-108">value</span></span>|<span data-ttu-id="80e82-109">Optionale Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="80e82-109">Optional String.</span></span> <span data-ttu-id="80e82-110">Der Wert des öffentlichen RSA-Schlüssels, der auf dem Client verglichen werden soll.</span><span class="sxs-lookup"><span data-stu-id="80e82-110">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80e82-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="80e82-111">Child Elements</span></span>  

 <span data-ttu-id="80e82-112">Keine</span><span class="sxs-lookup"><span data-stu-id="80e82-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80e82-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="80e82-113">Parent Elements</span></span>  
  
|<span data-ttu-id="80e82-114">Element</span><span class="sxs-lookup"><span data-stu-id="80e82-114">Element</span></span>|<span data-ttu-id="80e82-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="80e82-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="80e82-116">Gibt die Identität des Diensts für die Authentifizierung durch den Client an.</span><span class="sxs-lookup"><span data-stu-id="80e82-116">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80e82-117">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="80e82-117">Remarks</span></span>  

 <span data-ttu-id="80e82-118">Eine RSA-Prüfung ermöglicht Ihnen, die Authentifizierung speziell auf den RSA-Schlüssel eines einzigen Zertifikats zu beschränken oder einen eigenen RSA-Schlüsselwert zu generieren.</span><span class="sxs-lookup"><span data-stu-id="80e82-118">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="80e82-119">Dies ermöglicht eine strengere Authentifizierung eines bestimmten RSA-Schlüssels auf Kosten des Diensts, der nicht mehr mit vorhandenen Clients zusammenarbeitet, wenn sich der RSA-Schlüsselwert ändert.</span><span class="sxs-lookup"><span data-stu-id="80e82-119">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="80e82-120">Weitere Informationen zum Überprüfen eines Dienstanbieter mithilfe der Identität für einen Client finden Sie unter [Dienst Identität und Authentifizierung](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="80e82-120">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80e82-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="80e82-121">Example</span></span>  

 <span data-ttu-id="80e82-122">Der folgende Konfigurationscode gibt den Wert des öffentlichen Schlüssels eines für die Authentifizierung eines Servers verwendeten X.509-Zertifikats an.</span><span class="sxs-lookup"><span data-stu-id="80e82-122">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="80e82-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="80e82-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="80e82-124">Dienstidentität und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="80e82-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
