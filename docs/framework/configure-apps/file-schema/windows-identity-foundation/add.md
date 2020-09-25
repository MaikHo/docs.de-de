---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 2f37019fa0787f5c5553dbd3debc173ec0a047ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189954"
---
# \<add>

<span data-ttu-id="0eaf2-101">Fügt der tokenhandlerauflistung den angegebenen Sicherheitstokenhandler hinzu.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-101">Adds the specified security token handler to the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="0eaf2-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="0eaf2-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0eaf2-103">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="0eaf2-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0eaf2-104">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0eaf2-105">Attribute</span><span class="sxs-lookup"><span data-stu-id="0eaf2-105">Attributes</span></span>  
  
|<span data-ttu-id="0eaf2-106">attribute</span><span class="sxs-lookup"><span data-stu-id="0eaf2-106">Attribute</span></span>|<span data-ttu-id="0eaf2-107">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="0eaf2-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0eaf2-108">type</span><span class="sxs-lookup"><span data-stu-id="0eaf2-108">type</span></span>|<span data-ttu-id="0eaf2-109">Der CLR-Typname des tokenhandlers, der hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-109">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="0eaf2-110">Weitere Informationen zum Angeben des- `type` Attributs finden Sie unter [benutzerdefinierte Typverweise](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="0eaf2-110">For more information about how to specify the `type` attribute, see [Custom Type References](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0eaf2-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0eaf2-111">Child Elements</span></span>  
  
|<span data-ttu-id="0eaf2-112">Element</span><span class="sxs-lookup"><span data-stu-id="0eaf2-112">Element</span></span>|<span data-ttu-id="0eaf2-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0eaf2-113">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="0eaf2-114">Stellt die Konfiguration für die- <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Klasse, die- <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> Klasse oder eine abgeleitete Klasse einer dieser Klassen bereit.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-114">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|<span data-ttu-id="0eaf2-115">Stellt die Konfiguration für die- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> Klasse oder abgeleitete Klassen bereit.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="0eaf2-116">Stellt die Konfiguration für die- <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> Klasse oder abgeleitete Klassen bereit.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-116">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="0eaf2-117">Stellt eine optionale Konfiguration für die- <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> Klasse oder abgeleitete Klassen bereit.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-117">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0eaf2-118">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0eaf2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0eaf2-119">Element</span><span class="sxs-lookup"><span data-stu-id="0eaf2-119">Element</span></span>|<span data-ttu-id="0eaf2-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0eaf2-120">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="0eaf2-121">Gibt eine Auflistung von Sicherheitstokenhandlern an, die beim Endpunkt registriert sind.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-121">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eaf2-122">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="0eaf2-122">Remarks</span></span>  

 <span data-ttu-id="0eaf2-123">Das- `<add>` Element kann ein einzelnes untergeordnetes Element annehmen, das die Konfiguration für den Tokenhandler angibt.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-123">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="0eaf2-124">Dies hängt davon ab, ob die Handlerklasse, auf die über das-Attribut des-Elements verwiesen wird, `type` `<add>` Unterstützung für diese Funktion bietet</span><span class="sxs-lookup"><span data-stu-id="0eaf2-124">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="0eaf2-125">Tokenhandlerklassen, die diese Funktion bereitstellen, müssen einen Konstruktor verfügbar machen, der ein <xref:System.Xml.XmlElement> Objekt annimmt.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-125">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="0eaf2-126">Einige der integrierten sicherheitstokenhandlerklassen stellen diese Funktionalität bereit.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-126">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="0eaf2-127">Diese Klassen sind <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> und <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="0eaf2-127">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0eaf2-128">Die tokenhandlerauflistung kann nur einen einzelnen Handler eines beliebigen Typs enthalten.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-128">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="0eaf2-129">Dies bedeutet beispielsweise Folgendes: Wenn Sie einen von der-Klasse abgeleiteten Handler zur-Auflistung hinzufügen möchten <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , müssen Sie zuerst den, der <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> standardmäßig vorhanden ist, aus der-Auflistung entfernen.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-129">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="0eaf2-130">Sie können das- [\<remove>](remove.md) Element verwenden, um einen einzelnen Handler aus der Auflistung zu entfernen, oder das- [\<clear>](clear.md) Element verwenden, um alle Handler aus der Auflistung zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-130">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="0eaf2-131">Die Einstellungen, die für einen Handler angegeben werden, überschreiben die entsprechenden Einstellungen, die für die tokenhandlerauflistung unter dem [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) -Element angegeben sind [\<identityConfiguration>](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="0eaf2-131">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0eaf2-132">Beispiel</span><span class="sxs-lookup"><span data-stu-id="0eaf2-132">Example</span></span>  

 <span data-ttu-id="0eaf2-133">Der folgende XML-Code zeigt die Verwendung des `<add>` -Elements und des- `<remove>` Elements, um den standardsitzungstokenhandler durch einen benutzerdefinierten Sitzungs Token-Handler</span><span class="sxs-lookup"><span data-stu-id="0eaf2-133">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="0eaf2-134">Der XML-Code stammt aus dem `ClaimsAwareWebFarm` Beispiel.</span><span class="sxs-lookup"><span data-stu-id="0eaf2-134">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
