---
title: Nachrichtensicherheit über einen Benutzernamenclient
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 9bcac0e45d44270d27a4cf04677e967a80e94b90
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550201"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="58dc4-102">Nachrichtensicherheit über einen Benutzernamenclient</span><span class="sxs-lookup"><span data-stu-id="58dc4-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="58dc4-103">Die folgende Abbildung zeigt einen Windows Communication Foundation (WCF)-Dienst und einen Client, der mithilfe der Sicherheit auf Nachrichten Ebene gesichert wird.</span><span class="sxs-lookup"><span data-stu-id="58dc4-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="58dc4-104">Der Dienst wird über ein X.509-Zertifikat authentifiziert.</span><span class="sxs-lookup"><span data-stu-id="58dc4-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="58dc4-105">Der Client wird über den Benutzernamen und das Kennwort authentifiziert.</span><span class="sxs-lookup"><span data-stu-id="58dc4-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="58dc4-106">Eine Beispielanwendung finden Sie unter [Message Security User Name](../samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="58dc4-106">For a sample application, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="58dc4-107">![Nachrichtensicherheit durch Benutzernamenauthentifizierung](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1b10a61-7e1d-42b5-B1AF-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="58dc4-107">![Message security using username authentication](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="58dc4-108">Merkmal</span><span class="sxs-lookup"><span data-stu-id="58dc4-108">Characteristic</span></span>|<span data-ttu-id="58dc4-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="58dc4-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="58dc4-110">Sicherheitsmodus</span><span class="sxs-lookup"><span data-stu-id="58dc4-110">Security Mode</span></span>|<span data-ttu-id="58dc4-111">Nachricht</span><span class="sxs-lookup"><span data-stu-id="58dc4-111">Message</span></span>|  
|<span data-ttu-id="58dc4-112">Interoperabilität</span><span class="sxs-lookup"><span data-stu-id="58dc4-112">Interoperability</span></span>|<span data-ttu-id="58dc4-113">Nur Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="58dc4-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="58dc4-114">Authentifizierung (Server)</span><span class="sxs-lookup"><span data-stu-id="58dc4-114">Authentication (Server)</span></span>|<span data-ttu-id="58dc4-115">Für die erste Aushandlung ist eine Serverauthentifizierung erforderlich</span><span class="sxs-lookup"><span data-stu-id="58dc4-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="58dc4-116">Authentifizierung (Client)</span><span class="sxs-lookup"><span data-stu-id="58dc4-116">Authentication (Client)</span></span>|<span data-ttu-id="58dc4-117">Benutzername/Kennwort</span><span class="sxs-lookup"><span data-stu-id="58dc4-117">User name/password</span></span>|  
|<span data-ttu-id="58dc4-118">Integrität</span><span class="sxs-lookup"><span data-stu-id="58dc4-118">Integrity</span></span>|<span data-ttu-id="58dc4-119">Ja, mit freigegebenem Sicherheitskontext</span><span class="sxs-lookup"><span data-stu-id="58dc4-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="58dc4-120">Vertraulichkeit</span><span class="sxs-lookup"><span data-stu-id="58dc4-120">Confidentiality</span></span>|<span data-ttu-id="58dc4-121">Ja, mit freigegebenem Sicherheitskontext</span><span class="sxs-lookup"><span data-stu-id="58dc4-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="58dc4-122">Transport</span><span class="sxs-lookup"><span data-stu-id="58dc4-122">Transport</span></span>|<span data-ttu-id="58dc4-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="58dc4-123">HTTP</span></span>|  
|<span data-ttu-id="58dc4-124">Bindung</span><span class="sxs-lookup"><span data-stu-id="58dc4-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="58dc4-125">Dienst</span><span class="sxs-lookup"><span data-stu-id="58dc4-125">Service</span></span>  
 <span data-ttu-id="58dc4-126">Der folgende Code und die folgende Konfiguration werden unabhängig voneinander ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="58dc4-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="58dc4-127">Führen Sie eines der folgenden Verfahren aus:</span><span class="sxs-lookup"><span data-stu-id="58dc4-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="58dc4-128">Erstellen Sie einen separaten Dienst, indem Sie den Code ohne Konfiguration verwenden.</span><span class="sxs-lookup"><span data-stu-id="58dc4-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="58dc4-129">Erstellen Sie mit der angegebenen Konfiguration einen Dienst, aber definieren Sie keine Endpunkte.</span><span class="sxs-lookup"><span data-stu-id="58dc4-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="58dc4-130">Code</span><span class="sxs-lookup"><span data-stu-id="58dc4-130">Code</span></span>  
 <span data-ttu-id="58dc4-131">Im folgenden Code wird gezeigt, wie ein Dienstendpunkt, der Nachrichtensicherheit verwendet, erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="58dc4-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="58dc4-132">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="58dc4-132">Configuration</span></span>  
 <span data-ttu-id="58dc4-133">Die folgende Konfiguration kann statt des Codes verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="58dc4-133">The following configuration can be used instead of the code:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"
                                storeLocation="LocalMachine"  
                                storeName="My"
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="58dc4-134">Client</span><span class="sxs-lookup"><span data-stu-id="58dc4-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="58dc4-135">Code</span><span class="sxs-lookup"><span data-stu-id="58dc4-135">Code</span></span>  
 <span data-ttu-id="58dc4-136">Der folgende Code erstellt den Client.</span><span class="sxs-lookup"><span data-stu-id="58dc4-136">The following code creates the client.</span></span> <span data-ttu-id="58dc4-137">Die Bindung bezieht sich auf den Nachrichtensicherheitsmodus, und der Clientanmeldeinformationstyp wird auf `UserName` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="58dc4-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="58dc4-138">Der Benutzername und das Kennwort können nur mit Code (nicht konfigurierbar) angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="58dc4-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="58dc4-139">Der Code zum Zurückgeben des Benutzernamens und des Kennworts ist hier nicht gezeigt, da dies auf Anwendungsebene erfolgen muss.</span><span class="sxs-lookup"><span data-stu-id="58dc4-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="58dc4-140">Verwenden Sie z. B. ein Windows Forms-Dialogfeld, um vom Benutzer Daten abzufragen.</span><span class="sxs-lookup"><span data-stu-id="58dc4-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="58dc4-141">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="58dc4-141">Configuration</span></span>  
 <span data-ttu-id="58dc4-142">Der folgende Code dient zum Konfigurieren des Clients.</span><span class="sxs-lookup"><span data-stu-id="58dc4-142">The following code configures the client.</span></span> <span data-ttu-id="58dc4-143">Die Bindung bezieht sich auf den Nachrichtensicherheitsmodus, und der Clientanmeldeinformationstyp wird auf `UserName` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="58dc4-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="58dc4-144">Der Benutzername und das Kennwort können nur mit Code (nicht konfigurierbar) angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="58dc4-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58dc4-145">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="58dc4-145">See also</span></span>

- [<span data-ttu-id="58dc4-146">Sicherheitsübersicht</span><span class="sxs-lookup"><span data-stu-id="58dc4-146">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="58dc4-147">Nachrichtensicherheit – Benutzername</span><span class="sxs-lookup"><span data-stu-id="58dc4-147">Message Security User Name</span></span>](../samples/message-security-user-name.md)
- [<span data-ttu-id="58dc4-148">Dienstidentität und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="58dc4-148">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [\<identity>](../../configure-apps/file-schema/wcf/identity.md)
- <span data-ttu-id="58dc4-149">[Sicherheitsmodell für Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="58dc4-149">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
