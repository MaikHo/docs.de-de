---
title: <authentication> of- <clientCertificate> Element
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 13296dbc2b3bc8836770197a1549586c841b4635
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201602"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="0dfa3-102">\<authentication> of- \<clientCertificate> Element</span><span class="sxs-lookup"><span data-stu-id="0dfa3-102">\<authentication> of \<clientCertificate> Element</span></span>

<span data-ttu-id="0dfa3-103">Gibt die Authentifizierungsverhalten für Clientzertifikate an, die von einem Dienst verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="0dfa3-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0dfa3-104">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0dfa3-105">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="0dfa3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0dfa3-106">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente sowie übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0dfa3-107">Attributes</span><span class="sxs-lookup"><span data-stu-id="0dfa3-107">Attributes</span></span>  
  
|<span data-ttu-id="0dfa3-108">attribute</span><span class="sxs-lookup"><span data-stu-id="0dfa3-108">Attribute</span></span>|<span data-ttu-id="0dfa3-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0dfa3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0dfa3-110">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="0dfa3-110">customCertificateValidatorType</span></span>|<span data-ttu-id="0dfa3-111">Optionale Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-111">Optional string.</span></span> <span data-ttu-id="0dfa3-112">Ein Typ und eine Assembly, die zum Überprüfen eines benutzerdefinierten Typs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="0dfa3-113">Das Attribut muss festgelegt werden, wenn für `certificateValidationMode` der Wert `Custom` festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="0dfa3-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="0dfa3-114">certificateValidationMode</span></span>|<span data-ttu-id="0dfa3-115">Optionale Enumeration.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-115">Optional enumeration.</span></span> <span data-ttu-id="0dfa3-116">Gibt einen der für die Prüfung von Anmeldeinformationen verwendeten Modi an.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-116">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="0dfa3-117">Dieses Attribut ist vom Typ <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-117">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="0dfa3-118">Wenn dies auf <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType> festgelegt wurde, muss auch ein `customCertificateValidator` bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-118">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="0dfa3-119">Der Standardwert ist <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-119">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="0dfa3-120">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="0dfa3-120">includeWindowsGroups</span></span>|<span data-ttu-id="0dfa3-121">Optionaler boolescher Wert.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-121">Optional Boolean.</span></span> <span data-ttu-id="0dfa3-122">Gibt an, ob Windows-Gruppen im Sicherheitskontext enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-122">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="0dfa3-123">Wird dieses Attribut auf `true` festgelegt, hat dies Auswirkungen auf die Leistung, da dabei eine vollständige Gruppenerweiterung durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-123">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="0dfa3-124">Legen Sie dieses Attribut auf `false` fest, wenn Sie die Liste der Gruppen, zu denen ein Benutzer gehört, nicht angeben müssen.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-124">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="0dfa3-125">mapclientcertifieretowindowsaccount</span><span class="sxs-lookup"><span data-stu-id="0dfa3-125">mapClientCertificateToWindowsAccount</span></span>|<span data-ttu-id="0dfa3-126">Boolesch.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-126">Boolean.</span></span> <span data-ttu-id="0dfa3-127">Gibt an, ob der Client mithilfe des Zertifikats einer Windows-Identität zugeordnet werden kann.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-127">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="0dfa3-128">Active Directory muss dafür aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-128">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="0dfa3-129">revocationMode</span><span class="sxs-lookup"><span data-stu-id="0dfa3-129">revocationMode</span></span>|<span data-ttu-id="0dfa3-130">Optionale Enumeration.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-130">Optional enumeration.</span></span> <span data-ttu-id="0dfa3-131">Einer der Modi zum Prüfen auf eine Liste gesperrter Zertifikate.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-131">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="0dfa3-132">Der Standardwert lautet `Online`.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-132">The default is `Online`.</span></span> <span data-ttu-id="0dfa3-133">Dieser Wert wird ignoriert, wenn HTTP-Transportsicherheit verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-133">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="0dfa3-134">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="0dfa3-134">trustedStoreLocation</span></span>|<span data-ttu-id="0dfa3-135">Optionale Enumeration.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-135">Optional enumeration.</span></span> <span data-ttu-id="0dfa3-136">Einer der beiden Systemspeicherorte: `LocalMachine` oder `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="0dfa3-137">Dieser Wert wird verwendet, wenn ein Dienstzertifikat mit dem Client ausgehandelt wird.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-137">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="0dfa3-138">Die Überprüfung wird für den Speicher für **Vertrauenswürdige Personen** am angegebenen Speicherort durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-138">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="0dfa3-139">Der Standardwert lautet `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-139">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="0dfa3-140">customCertificateValidatorType-Attribut</span><span class="sxs-lookup"><span data-stu-id="0dfa3-140">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="0dfa3-141">Wert</span><span class="sxs-lookup"><span data-stu-id="0dfa3-141">Value</span></span>|<span data-ttu-id="0dfa3-142">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="0dfa3-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0dfa3-143">String</span><span class="sxs-lookup"><span data-stu-id="0dfa3-143">String</span></span>|<span data-ttu-id="0dfa3-144">Gibt den vollständigen Typnamen und die Assembly sowie weitere Daten zum Suchen des Typs an.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-144">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="0dfa3-145">certificateValidationMode-Attribut</span><span class="sxs-lookup"><span data-stu-id="0dfa3-145">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="0dfa3-146">Wert</span><span class="sxs-lookup"><span data-stu-id="0dfa3-146">Value</span></span>|<span data-ttu-id="0dfa3-147">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0dfa3-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0dfa3-148">Enumeration</span><span class="sxs-lookup"><span data-stu-id="0dfa3-148">Enumeration</span></span>|<span data-ttu-id="0dfa3-149">Einer der folgenden Werte: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-149">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="0dfa3-150">Weitere Informationen finden Sie unter [Arbeiten mit Zertifikaten](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0dfa3-150">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="0dfa3-151">revocationMode-Attribut</span><span class="sxs-lookup"><span data-stu-id="0dfa3-151">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="0dfa3-152">Wert</span><span class="sxs-lookup"><span data-stu-id="0dfa3-152">Value</span></span>|<span data-ttu-id="0dfa3-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0dfa3-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0dfa3-154">Enumeration</span><span class="sxs-lookup"><span data-stu-id="0dfa3-154">Enumeration</span></span>|<span data-ttu-id="0dfa3-155">Einer der folgenden Werte: NoCheck, Online, Offline.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-155">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="0dfa3-156">Weitere Informationen finden Sie unter [Arbeiten mit Zertifikaten](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0dfa3-156">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="0dfa3-157">trustedStoreLocation-Attribut</span><span class="sxs-lookup"><span data-stu-id="0dfa3-157">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="0dfa3-158">Wert</span><span class="sxs-lookup"><span data-stu-id="0dfa3-158">Value</span></span>|<span data-ttu-id="0dfa3-159">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0dfa3-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0dfa3-160">Enumeration</span><span class="sxs-lookup"><span data-stu-id="0dfa3-160">Enumeration</span></span>|<span data-ttu-id="0dfa3-161">Einer der folgenden Werte: `LocalMachine` oder `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-161">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="0dfa3-162">Der Standardwert lautet `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-162">The default is `CurrentUser`.</span></span> <span data-ttu-id="0dfa3-163">Wenn die Clientanwendung über ein Systemkonto ausgeführt wird, befindet sich das Zertifikat in der Regel in `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-163">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="0dfa3-164">Wenn die Clientanwendung über ein Benutzerkonto ausgeführt wird, befindet sich das Zertifikat in der Regel in `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-164">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0dfa3-165">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0dfa3-165">Child Elements</span></span>  

 <span data-ttu-id="0dfa3-166">Keine</span><span class="sxs-lookup"><span data-stu-id="0dfa3-166">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0dfa3-167">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0dfa3-167">Parent Elements</span></span>  
  
|<span data-ttu-id="0dfa3-168">Element</span><span class="sxs-lookup"><span data-stu-id="0dfa3-168">Element</span></span>|<span data-ttu-id="0dfa3-169">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0dfa3-169">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="0dfa3-170">Definiert ein X.509-Zertifikat, das zum Authentifizieren eines Clients bei einem Dienst verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-170">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0dfa3-171">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="0dfa3-171">Remarks</span></span>  

 <span data-ttu-id="0dfa3-172">Das `<authentication>`-Element entspricht der <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>-Klasse.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-172">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="0dfa3-173">Mit dem Element können Sie die Art der Clientauthentifizierung anpassen.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-173">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="0dfa3-174">Sie können als Wert für das `certificateValidationMode`-Attribut `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust` oder `Custom` festlegen.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-174">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="0dfa3-175">Standardmäßig ist die-Ebene auf festgelegt `ChainTrust` , wodurch angegeben wird, dass jedes Zertifikat in einer Hierarchie von Zertifikaten gefunden werden *root authority* muss, die in eine Stamm Zertifizierungsstelle am Anfang der Kette gelangen.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-175">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="0dfa3-176">Dies ist der sicherste Modus.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-176">This is the most secure mode.</span></span> <span data-ttu-id="0dfa3-177">Sie können auch den Wert `PeerOrChainTrust` verwenden, der vorgibt, dass neben den Zertifikaten in einer Vertrauenskette auch selbst ausgestellte Zertifikate (Peervertrauen) akzeptiert werden.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-177">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="0dfa3-178">Sie können diesen Wert beim Entwickeln und Debuggen von Clients und Diensten verwenden, da selbst ausgestellte Zertifikate nicht von einer vertrauenswürdigen Zertifizierungsstelle bezogen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-178">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="0dfa3-179">Verwenden Sie beim Bereitstellen eines Clients jedoch den Wert `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-179">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="0dfa3-180">Sie können den Wert auch auf `Custom` setzen.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-180">You can also set the value to `Custom`.</span></span> <span data-ttu-id="0dfa3-181">Wenn Sie den Wert `Custom` verwenden, müssen Sie für das `customCertificateValidatorType`-Attribut zudem ein Assembly und einen Typ, mit dem das Zertifikat überprüft wird, festlegen.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-181">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="0dfa3-182">Wenn Sie Ihre eigene Überprüfung erstellen möchten, müssen Sie die abstrakte <xref:System.IdentityModel.Selectors.X509CertificateValidator>-Klasse vererben.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-182">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="0dfa3-183">Weitere Informationen finden Sie unter Vorgehens [Weise: Erstellen eines Dienstanbieter, der ein benutzerdefiniertes zertifikatvalidator verwendet](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="0dfa3-183">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dfa3-184">Beispiel</span><span class="sxs-lookup"><span data-stu-id="0dfa3-184">Example</span></span>  

 <span data-ttu-id="0dfa3-185">Der folgende Code gibt ein X.509-Zertifikat und einen benutzerdefinierten Validierungstyp im `<authentication>`-Element an.</span><span class="sxs-lookup"><span data-stu-id="0dfa3-185">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="0dfa3-186">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0dfa3-186">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="0dfa3-187">Sicherheitsverhalten</span><span class="sxs-lookup"><span data-stu-id="0dfa3-187">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0dfa3-188">Vorgehensweise: Erstellen eines Diensts, der ein benutzerdefiniertes Zertifikatsvalidierungssteuerelement verwendet</span><span class="sxs-lookup"><span data-stu-id="0dfa3-188">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="0dfa3-189">Verwenden von Zertifikaten</span><span class="sxs-lookup"><span data-stu-id="0dfa3-189">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
