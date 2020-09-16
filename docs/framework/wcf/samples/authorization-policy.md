---
title: Autorisierungsrichtlinie
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: a789faae1f6224512f9a8a9ab084c8a82e4a2b87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553661"
---
# <a name="authorization-policy"></a><span data-ttu-id="40908-102">Autorisierungsrichtlinie</span><span class="sxs-lookup"><span data-stu-id="40908-102">Authorization Policy</span></span>

<span data-ttu-id="40908-103">Dieses Beispiel veranschaulicht, wie eine benutzerdefinierte Anspruchsautorisierungsrichtlinie und ein zugeordneter benutzerdefinierter Dienstautorisierungs-Manager implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="40908-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="40908-104">Das ist nützlich, wenn der Dienst anspruchsbasierte Zugriffsüberprüfungen an Dienstvorgängen vornimmt und vor den Zugriffsüberprüfungen dem Aufrufer bestimmte Rechte gewährt.</span><span class="sxs-lookup"><span data-stu-id="40908-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="40908-105">Dieses Beispiel zeigt sowohl den Prozess zum Hinzufügen von Ansprüchen als auch den Prozess zum Durchführen einer Zugriffsüberprüfung anhand des finalisierten Satzes von Ansprüchen.</span><span class="sxs-lookup"><span data-stu-id="40908-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="40908-106">Alle Anwendungsnachrichten zwischen dem Client und dem Server werden signiert und verschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="40908-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="40908-107">Standardmäßig werden mit der `wsHttpBinding`-Bindung ein vom Client angegebener Benutzername und ein Kennwort zum Anmelden an einem gültigen Windows NT-Konto verwendet.</span><span class="sxs-lookup"><span data-stu-id="40908-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="40908-108">Dieses Beispiel zeigt, wie ein benutzerdefinierter <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> genutzt wird, um den Client zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="40908-108">This sample demonstrates how to utilize a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to authenticate the client.</span></span> <span data-ttu-id="40908-109">Außerdem zeigt dieses Beispiel die Clientauthentifizierung beim Dienst mit einem X.509-Zertifikat.</span><span class="sxs-lookup"><span data-stu-id="40908-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="40908-110">Dieses Beispiel zeigt eine Implementierung von <xref:System.IdentityModel.Policy.IAuthorizationPolicy> und <xref:System.ServiceModel.ServiceAuthorizationManager>, das zwischen ihnen bestimmten Benutzern Zugriff auf bestimmte Methoden des Diensts gewährt.</span><span class="sxs-lookup"><span data-stu-id="40908-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="40908-111">Dieses Beispiel basiert auf dem [Benutzernamen der Nachrichten Sicherheit](message-security-user-name.md), zeigt jedoch, wie eine Anspruchs Transformation durchgeführt wird, bevor <xref:System.ServiceModel.ServiceAuthorizationManager> aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="40908-111">This sample is based on the [Message Security User Name](message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="40908-112">Die Setupprozedur und die Buildanweisungen für dieses Beispiel befinden sich am Ende dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="40908-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="40908-113">Insgesamt demonstriert dieses Beispiel Folgendes:</span><span class="sxs-lookup"><span data-stu-id="40908-113">In summary, this sample demonstrates how:</span></span>

- <span data-ttu-id="40908-114">Der Client kann mit einem Benutzernamen und einem Kennwort authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="40908-114">The client can be authenticated using a user name-password.</span></span>

- <span data-ttu-id="40908-115">Der Client kann mit einem X.509-Zertifikat authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="40908-115">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="40908-116">Der Server überprüft die Clientanmeldeinformationen mithilfe eines benutzerdefinierten `UsernamePassword`-Validierungssteuerelements.</span><span class="sxs-lookup"><span data-stu-id="40908-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

- <span data-ttu-id="40908-117">Der Server wird mit dem X.509-Zertifikat des Servers authentifiziert.</span><span class="sxs-lookup"><span data-stu-id="40908-117">The server is authenticated using the server's X.509 certificate.</span></span>

- <span data-ttu-id="40908-118">Der Server kann <xref:System.ServiceModel.ServiceAuthorizationManager> verwenden, um den Zugriff auf bestimmte Methoden im Dienst zu steuern.</span><span class="sxs-lookup"><span data-stu-id="40908-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

- <span data-ttu-id="40908-119">So wird <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementiert.</span><span class="sxs-lookup"><span data-stu-id="40908-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="40908-120">Der Dienst macht zwei Endpunkte für die Kommunikation mit dem Dienst verfügbar, die mithilfe der Konfigurationsdatei App.config definiert werden. Jeder Endpunkt besteht aus einer Adresse, einer Bindung und einem Vertrag.</span><span class="sxs-lookup"><span data-stu-id="40908-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="40908-121">Die eine Bindung wird mit einer normalen `wsHttpBinding`-Bindung konfiguriert, die WS-Security und Clientbenutzernamenauthentifizierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="40908-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="40908-122">Die andere Bindung wird mit einer normalen `wsHttpBinding`-Bindung konfiguriert, die WS-Security und Clientzertifikatauthentifizierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="40908-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="40908-123">Der [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) gibt an, dass die Benutzer Anmelde Informationen für die Dienst Authentifizierung verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="40908-123">The [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="40908-124">Das Serverzertifikat muss den gleichen Wert für die- `SubjectName` Eigenschaft wie das- `findValue` Attribut in der enthalten [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="40908-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <!-- configure base address provided by host -->
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service"/>
        </baseAddresses>
      </host>
      <!-- use base address provided by host, provide two endpoints -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <endpoint address="certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding2"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
    <message clientCredentialType="UserName" />
        </security>
      </binding>
      <!-- X509 certificate binding -->
      <binding name="Binding2">
        <security mode="Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior" >
        <serviceDebug includeExceptionDetailInFaults ="true" />
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to specify authentication constraints on client certificates.
          -->
          <clientCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
        <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
          <!--
          The serviceAuthorization behavior allows one to specify custom authorization policies.
          -->
          <authorizationPolicies>
            <add policyType="Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary" />
          </authorizationPolicies>
        </serviceAuthorization>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

<span data-ttu-id="40908-125">Jede Clientendpunktkonfiguration besteht aus einem Konfigurationsnamen, einer absoluten Adresse für den Dienstendpunkt, der Bindung und dem Vertrag.</span><span class="sxs-lookup"><span data-stu-id="40908-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="40908-126">Die Client Bindung wird mit dem entsprechenden Sicherheitsmodus konfiguriert, wie in diesem Fall in und gemäß den Angaben in angegeben [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `clientCredentialType` [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="40908-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
            address="http://localhost:8001/servicemodelsamples/service/username"
    binding="wsHttpBinding"
    bindingConfiguration="Binding1"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" >
      </endpoint>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
                        address="http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
            bindingConfiguration="Binding2"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
        <!-- X509 certificate binding -->
        <binding name="Binding2">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
    </wsHttpBinding>
    </bindings>

    <behaviors>
      <behavior name="ClientCertificateBehavior">
        <clientCredentials>
          <serviceCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust
            means that if the certificate
            is in the user's Trusted People store, then it will be
            trusted without performing a
            validation of the certificate's issuer chain. This setting
            is used here for convenience so that the
            sample can be run without having to have certificates
            issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust.
            The security implications of this
            setting should be carefully considered before using
            PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode = "PeerOrChainTrust" />
          </serviceCertificate>
        </clientCredentials>
      </behavior>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="40908-127">Für den benutzernamenbasierten Endpunkt legt die Clientimplementierung den zu verwendenden Benutzernamen und das Kennwort fest.</span><span class="sxs-lookup"><span data-stu-id="40908-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

```csharp
// Create a client with Username endpoint configuration
CalculatorClient client1 = new CalculatorClient("Username");

client1.ClientCredentials.UserName.UserName = "test1";
client1.ClientCredentials.UserName.Password = "1tset";

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client1.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client1.Close();
```

<span data-ttu-id="40908-128">Für den zertifikatbasierten Endpunkt legt die Clientimplementierung das zu verwendende Clientzertifikat fest.</span><span class="sxs-lookup"><span data-stu-id="40908-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client2 = new CalculatorClient("Certificate");

client2.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client2.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client2.Close();
```

<span data-ttu-id="40908-129">In diesem Beispiel wird ein benutzerdefinierter <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> verwendet, um Benutzernamen und Kennwörter zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="40908-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="40908-130">Das Beispiel implementiert `MyCustomUserNamePasswordValidator`, das von <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> abgeleitet ist.</span><span class="sxs-lookup"><span data-stu-id="40908-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="40908-131">Weitere Informationen zu <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> finden Sie in der Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="40908-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="40908-132">Um die Integration mit dem <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> zu demonstrieren, implementiert dieses benutzerdefinierte Validierungssteuerelement-Beispiel die <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>-Methode zum Entgegennehmen von Kombinationen aus Benutzername und Kennwort, wobei der Benutzername wie im folgenden Code gezeigt mit dem Kennwort übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="40908-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

```csharp
public class MyCustomUserNamePasswordValidator : UserNamePasswordValidator
{
  // This method validates users. It allows in two users,
  // test1 and test2 with passwords 1tset and 2tset respectively.
  // This code is for illustration purposes only and
  // MUST NOT be used in a production environment because it
  // is NOT secure.
  public override void Validate(string userName, string password)
  {
    if (null == userName || null == password)
    {
      throw new ArgumentNullException();
    }

    if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
    {
      throw new SecurityTokenException("Unknown Username or Password");
    }
  }
}
```

<span data-ttu-id="40908-133">Nachdem das Validierungssteuerelement im Dienstcode implementiert ist, muss der Diensthost über die zu verwendende Validierungssteuerelementinstanz informiert werden.</span><span class="sxs-lookup"><span data-stu-id="40908-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="40908-134">Dies erfolgt mithilfe des folgenden Codes:</span><span class="sxs-lookup"><span data-stu-id="40908-134">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="40908-135">Oder Sie können das gleiche in der Konfiguration vornehmen:</span><span class="sxs-lookup"><span data-stu-id="40908-135">Or you can do the same thing in configuration:</span></span>

```xml
<behavior>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

<span data-ttu-id="40908-136">Windows Communication Foundation (WCF) bietet ein umfangreiches Anspruchs basiertes Modell zum Durchführen von Zugriffs Überprüfungen.</span><span class="sxs-lookup"><span data-stu-id="40908-136">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="40908-137">Das <xref:System.ServiceModel.ServiceAuthorizationManager>-Objekt wird verwendet, um die Zugriffsüberprüfung durchzuführen und zu bestimmen, ob die dem Client zugeordneten Ansprüche die Anforderungen erfüllen, die für den Zugriff auf die Dienstmethode erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="40908-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="40908-138">Zu Demonstrationszwecken wird in diesem Beispiel eine Implementierung von veranschaulicht, <xref:System.ServiceModel.ServiceAuthorizationManager> die die <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> -Methode implementiert, um dem Benutzer den Zugriff auf Methoden auf der Grundlage von Ansprüchen des Typs zu ermöglichen, `http://example.com/claims/allowedoperation` deren Wert der Aktions-URI des Vorgangs ist, der aufgerufen werden darf.</span><span class="sxs-lookup"><span data-stu-id="40908-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type `http://example.com/claims/allowedoperation` whose value is the Action URI of the operation that is allowed to be called.</span></span>

```csharp
public class MyServiceAuthorizationManager : ServiceAuthorizationManager
{
  protected override bool CheckAccessCore(OperationContext operationContext)
  {
    string action = operationContext.RequestContext.RequestMessage.Headers.Action;
    Console.WriteLine("action: {0}", action);
    foreach(ClaimSet cs in operationContext.ServiceSecurityContext.AuthorizationContext.ClaimSets)
    {
      if ( cs.Issuer == ClaimSet.System )
      {
        foreach (Claim c in cs.FindClaims("http://example.com/claims/allowedoperation", Rights.PossessProperty))
        {
          Console.WriteLine("resource: {0}", c.Resource.ToString());
          if (action == c.Resource.ToString())
            return true;
        }
      }
    }
    return false;
  }
}
```

<span data-ttu-id="40908-139">Wenn der benutzerdefinierte <xref:System.ServiceModel.ServiceAuthorizationManager> implementiert ist, muss der Diensthost über den zu verwendenden <xref:System.ServiceModel.ServiceAuthorizationManager> informiert werden.</span><span class="sxs-lookup"><span data-stu-id="40908-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="40908-140">Dies wird wie im folgenden Code gezeigt durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="40908-140">This is done as shown in the following code.</span></span>

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="40908-141">Die primäre <xref:System.IdentityModel.Policy.IAuthorizationPolicy>-Methode, die implementiert werden soll, ist die <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29>-Methode.</span><span class="sxs-lookup"><span data-stu-id="40908-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

```csharp
public class MyAuthorizationPolicy : IAuthorizationPolicy
{
    string id;

    public MyAuthorizationPolicy()
    {
    id =  Guid.NewGuid().ToString();
    }

    public bool Evaluate(EvaluationContext evaluationContext,
                                            ref object state)
    {
        bool bRet = false;
        CustomAuthState customstate = null;

        if (state == null)
        {
            customstate = new CustomAuthState();
            state = customstate;
        }
        else
            customstate = (CustomAuthState)state;
        Console.WriteLine("In Evaluate");
        if (!customstate.ClaimsAdded)
        {
           IList<Claim> claims = new List<Claim>();

           foreach (ClaimSet cs in evaluationContext.ClaimSets)
              foreach (Claim c in cs.FindClaims(ClaimTypes.Name,
                                         Rights.PossessProperty))
                  foreach (string s in
                        GetAllowedOpList(c.Resource.ToString()))
                  {
                       claims.Add(new
               Claim("http://example.com/claims/allowedoperation",
                                    s, Rights.PossessProperty));
                            Console.WriteLine("Claim added {0}", s);
                      }
                   evaluationContext.AddClaimSet(this,
                           new DefaultClaimSet(this.Issuer,claims));
                   customstate.ClaimsAdded = true;
                   bRet = true;
                }
         else
         {
              bRet = true;
         }
         return bRet;
     }
...
}
```

<span data-ttu-id="40908-142">Der oben aufgeführte Code zeigt, wie die <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29>-Methode prüft, dass keine neuen Ansprüche hinzugefügt wurden, die sich auf die Verarbeitung auswirken, und bestimmte Ansprüche hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="40908-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="40908-143">Die Ansprüche, die zulässig sind, werden aus der `GetAllowedOpList`-Methode abgerufen, die so implementiert ist, dass sie eine Liste der Vorgänge zurückgibt, die der Benutzer ausführen darf.</span><span class="sxs-lookup"><span data-stu-id="40908-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="40908-144">Die Autorisierungsrichtlinie fügt Ansprüche zum Zugreifen auf den jeweiligen Vorgang hinzu.</span><span class="sxs-lookup"><span data-stu-id="40908-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="40908-145">Dies wird später vom <xref:System.ServiceModel.ServiceAuthorizationManager> verwendet, um Zugriffsprüfungsentscheidungen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="40908-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="40908-146">Wenn der benutzerdefinierte <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementiert ist, muss der Diensthost über die zu verwendenden Autorisierungsrichtlinien informiert werden.</span><span class="sxs-lookup"><span data-stu-id="40908-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="40908-147">Wenn Sie das Beispiel ausführen, werden die Anforderungen und Antworten für den Vorgang im Clientkonsolenfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="40908-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="40908-148">Der Client ruft erfolgreich die Add-, Subtract- und Multiple-Methoden auf und erhält beim Versuch, die Divide-Methode aufzurufen, eine Nachricht vom Typ "Zugriff verweigert".</span><span class="sxs-lookup"><span data-stu-id="40908-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="40908-149">Drücken Sie im Clientfenster die EINGABETASTE, um den Client zu schließen.</span><span class="sxs-lookup"><span data-stu-id="40908-149">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="40908-150">Setupbatchdatei</span><span class="sxs-lookup"><span data-stu-id="40908-150">Setup Batch File</span></span>

<span data-ttu-id="40908-151">Mit der in diesem Beispiel enthaltenen Batchdatei Setup.bat können Sie den Server mit relevanten Zertifikaten zum Ausführen einer selbst gehosteten Anwendung konfigurieren, die serverzertifikatbasierte Sicherheit erfordert.</span><span class="sxs-lookup"><span data-stu-id="40908-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="40908-152">Nachfolgend erhalten Sie einen kurzen Überblick über die verschiedenen Abschnitte der Batchdateien, damit Sie sie so ändern können, dass sie in der entsprechenden Konfiguration ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="40908-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="40908-153">Erstellen des Serverzertifikats.</span><span class="sxs-lookup"><span data-stu-id="40908-153">Creating the server certificate.</span></span>

    <span data-ttu-id="40908-154">Mit den folgenden Zeilen aus der Batchdatei "Setup.bat" wird das zu verwendende Serverzertifikat erstellt.</span><span class="sxs-lookup"><span data-stu-id="40908-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="40908-155">Die Variable %SERVER_NAME% gibt den Servernamen an.</span><span class="sxs-lookup"><span data-stu-id="40908-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="40908-156">Ändern Sie diese Variable, und geben Sie Ihren eigenen Servernamen an.</span><span class="sxs-lookup"><span data-stu-id="40908-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="40908-157">Der Standardwert ist localhost.</span><span class="sxs-lookup"><span data-stu-id="40908-157">The default value is localhost.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="40908-158">Installieren des Serverzertifikats in den Clientspeicher für vertrauenswürdige Zertifikate.</span><span class="sxs-lookup"><span data-stu-id="40908-158">Installing the server certificate into client's trusted certificate store.</span></span>

    <span data-ttu-id="40908-159">Mit den folgenden Zeilen in der Batchdatei Setup.bat wird das Serverzertifikat in den Clientspeicher für vertrauenswürdige Personen kopiert.</span><span class="sxs-lookup"><span data-stu-id="40908-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="40908-160">Dieser Schritt ist erforderlich, da von Makecert.exe generierten Zertifikaten nicht implizit vom Clientsystem vertraut wird.</span><span class="sxs-lookup"><span data-stu-id="40908-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="40908-161">Wenn Sie bereits über ein Zertifikat verfügen, dass von einem vertrauenswürdigen Clientstammzertifikat abstammt (z. B. ein von Microsoft ausgegebenes Zertifikat), ist dieser Schritt zum Auffüllen des Clientzertifikatspeichers mit dem Serverzertifikat nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="40908-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="40908-162">Erstellen des Clientzertifikats.</span><span class="sxs-lookup"><span data-stu-id="40908-162">Creating the client certificate.</span></span>

    <span data-ttu-id="40908-163">Die folgenden Zeilen aus der Batchdatei Setup.bat erstellen das zu verwendende Clientzertifikat.</span><span class="sxs-lookup"><span data-stu-id="40908-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="40908-164">Die Variable %USER_NAME% gibt den Servernamen an.</span><span class="sxs-lookup"><span data-stu-id="40908-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="40908-165">Dieser Wert wird auf "test1" festgelegt, da dies der Name ist, nach dem die `IAuthorizationPolicy` sucht.</span><span class="sxs-lookup"><span data-stu-id="40908-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="40908-166">Wenn Sie den Wert  von % USER_NAME% ändern, müssen Sie in der `IAuthorizationPolicy.Evaluate`-Methode den entsprechenden Wert ändern.</span><span class="sxs-lookup"><span data-stu-id="40908-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

    <span data-ttu-id="40908-167">Das Zertifikat wird im persönlichen Speicher unterhalb von CurrentUser gespeichert.</span><span class="sxs-lookup"><span data-stu-id="40908-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="40908-168">Installieren des Clientzertifikats in den Serverspeicher für vertrauenswürdige Zertifikate.</span><span class="sxs-lookup"><span data-stu-id="40908-168">Installing the client certificate into server's trusted certificate store.</span></span>

    <span data-ttu-id="40908-169">Die folgenden Zeilen in der Batchdatei Setup.bat kopieren das Clientzertifikat in den Speicher für vertrauenswürdige Personen.</span><span class="sxs-lookup"><span data-stu-id="40908-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="40908-170">Dieser Schritt ist erforderlich, da von "Makecert.exe" generierten Zertifikaten nicht implizit vom Serversystem vertraut wird.</span><span class="sxs-lookup"><span data-stu-id="40908-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="40908-171">Wenn Sie bereits über ein Zertifikat verfügen, das von einem vertrauenswürdigen Stammzertifikat abstammt (z. B. ein von Microsoft ausgegebenes Zertifikat), ist dieser Schritt zum Auffüllen des Serverzertifikatspeichers mit dem Clientzertifikat nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="40908-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="40908-172">So richten Sie das Beispiel ein und erstellen es</span><span class="sxs-lookup"><span data-stu-id="40908-172">To set up and build the sample</span></span>

1. <span data-ttu-id="40908-173">Befolgen Sie die Anweisungen unter Erstellen [der Windows Communication Foundation Beispiele](building-the-samples.md), um die Lösung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="40908-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="40908-174">Um das Beispiel in einer Konfiguration mit einem einzigen Computer oder computerübergreifend auszuführen, befolgen Sie die folgenden Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="40908-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="40908-175">Wenn Sie zur Neugenerierung der Konfiguration für dieses Beispiel die Datei Svcutil.exe verwenden, müssen Sie den Endpunktnamen in der Clientkonfiguration so ändern, dass er mit dem Clientcode übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="40908-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="40908-176">So führen Sie das Beispiel auf demselben Computer aus</span><span class="sxs-lookup"><span data-stu-id="40908-176">To run the sample on the same computer</span></span>

1. <span data-ttu-id="40908-177">Öffnen Sie Developer-Eingabeaufforderung für Visual Studio mit Administratorrechten, und führen Sie *Setup.bat* aus dem Beispiel Installationsordner aus.</span><span class="sxs-lookup"><span data-stu-id="40908-177">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="40908-178">Hiermit werden alle Zertifikate installiert, die zum Ausführen des Beispiels erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="40908-178">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="40908-179">Die Setup.bat Batchdatei ist für die Ausführung von Developer-Eingabeaufforderung für Visual Studio konzipiert.</span><span class="sxs-lookup"><span data-stu-id="40908-179">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="40908-180">Die PATH-Umgebungsvariable, die in Developer-Eingabeaufforderung für Visual Studio festgelegt ist, verweist auf das Verzeichnis, das ausführbare Dateien enthält, die vom *Setup.bat* Skript benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="40908-180">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="40908-181">Starten Sie Service.exe aus " *service\bin*".</span><span class="sxs-lookup"><span data-stu-id="40908-181">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="40908-182">Starten Sie Client.exe aus " *\client\bin*".</span><span class="sxs-lookup"><span data-stu-id="40908-182">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="40908-183">In der Clientkonsolenanwendung wird Clientaktivität angezeigt.</span><span class="sxs-lookup"><span data-stu-id="40908-183">Client activity is displayed on the client console application.</span></span>

<span data-ttu-id="40908-184">Wenn der Client und der Dienst nicht kommunizieren können, finden Sie unter [Tipps zur Problembehandlung für WCF-Beispiele](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="40908-184">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="40908-185">So führen Sie das Beispiel computerübergreifend aus</span><span class="sxs-lookup"><span data-stu-id="40908-185">To run the sample across computers</span></span>

1. <span data-ttu-id="40908-186">Erstellen Sie auf dem Dienstcomputer ein Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="40908-186">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="40908-187">Kopieren Sie die Dienst Programmdateien aus " *" \service\bin "* " in das Verzeichnis auf dem Dienstcomputer.</span><span class="sxs-lookup"><span data-stu-id="40908-187">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="40908-188">Kopieren Sie außerdem die Dateien Setup.bat, Cleanup.bat, GetComputerName.vbs und ImportClientCert.bat auf den Dienstcomputer.</span><span class="sxs-lookup"><span data-stu-id="40908-188">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="40908-189">Erstellen Sie auf dem Clientcomputer ein Verzeichnis für die Clientbinärdateien.</span><span class="sxs-lookup"><span data-stu-id="40908-189">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="40908-190">Kopieren Sie die Clientprogrammdateien in das Clientverzeichnis auf dem Clientcomputer.</span><span class="sxs-lookup"><span data-stu-id="40908-190">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="40908-191">Kopieren Sie die Dateien Setup.bat, Cleanup.bat und ImportServiceCert.bat ebenfalls auf den Client.</span><span class="sxs-lookup"><span data-stu-id="40908-191">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="40908-192">Führen Sie auf dem-Server `setup.bat service` in Developer-Eingabeaufforderung für Visual Studio, das mit Administratorrechten geöffnet ist, aus.</span><span class="sxs-lookup"><span data-stu-id="40908-192">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="40908-193">Wenn Sie `setup.bat` mit dem- `service` Argument ausführen, wird ein Dienst Zertifikat mit dem voll qualifizierten Domänen Namen des Computers erstellt und in die Datei *Service. CER*exportiert.</span><span class="sxs-lookup"><span data-stu-id="40908-193">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="40908-194">Bearbeiten Sie *Service.exe.config* , um den neuen Zertifikat Namen (im-Attribut im) widerzuspiegeln, der mit dem `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) voll qualifizierten Domänen Namen des Computers identisch ist.</span><span class="sxs-lookup"><span data-stu-id="40908-194">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="40908-195">Ändern Sie auch den **Computernamen** im- \<service> / \<baseAddresses> Element von localhost in den voll qualifizierten Namen Ihres Dienst Computers.</span><span class="sxs-lookup"><span data-stu-id="40908-195">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="40908-196">Kopieren Sie die Datei *Service. CER* aus dem Dienst Verzeichnis in das Client Verzeichnis auf dem Client Computer.</span><span class="sxs-lookup"><span data-stu-id="40908-196">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="40908-197">Führen Sie auf dem Client `setup.bat client` in Developer-Eingabeaufforderung für Visual Studio, das mit Administratorrechten geöffnet ist, aus.</span><span class="sxs-lookup"><span data-stu-id="40908-197">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="40908-198">Wenn `setup.bat` Sie mit dem- `client` Argument ausführen, wird ein Client Zertifikat mit dem Namen **test1** erstellt und das Client Zertifikat in eine Datei mit dem Namen *Client. CER*exportiert.</span><span class="sxs-lookup"><span data-stu-id="40908-198">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="40908-199">Ändern Sie in der *Client.exe.config* -Datei auf dem Client Computer den Wert für die Adresse des Endpunkts, sodass er mit der neuen Adresse Ihres Dienstanbieter identisch ist.</span><span class="sxs-lookup"><span data-stu-id="40908-199">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="40908-200">Ersetzen Sie hierzu **localhost** durch den voll qualifizierten Domänen Namen des Servers.</span><span class="sxs-lookup"><span data-stu-id="40908-200">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="40908-201">Kopieren Sie die Datei Client.cer aus dem Clientverzeichnis in das Dienstverzeichnis auf dem Server.</span><span class="sxs-lookup"><span data-stu-id="40908-201">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="40908-202">Führen Sie auf dem Client *ImportServiceCert.bat* in Developer-Eingabeaufforderung für Visual Studio aus, das mit Administratorrechten geöffnet wurde.</span><span class="sxs-lookup"><span data-stu-id="40908-202">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="40908-203">Dadurch wird das Dienst Zertifikat aus der Datei "Service. cer" in den Speicher " **CurrentUser-treudpeople** " importiert.</span><span class="sxs-lookup"><span data-stu-id="40908-203">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="40908-204">Führen Sie auf dem-Server *ImportClientCert.bat* in Developer-Eingabeaufforderung für Visual Studio aus, das mit Administratorrechten geöffnet wurde.</span><span class="sxs-lookup"><span data-stu-id="40908-204">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="40908-205">Dadurch wird das Client Zertifikat aus der CER-Datei des Clients in den **LocalMachine-Trust dpeople-** Speicher importiert.</span><span class="sxs-lookup"><span data-stu-id="40908-205">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="40908-206">Starten Sie auf dem Servercomputer Service.exe in einem Eingabeaufforderungsfenster.</span><span class="sxs-lookup"><span data-stu-id="40908-206">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="40908-207">Starten Sie auf dem Clientcomputer Client.exe in einem Eingabeaufforderungsfenster.</span><span class="sxs-lookup"><span data-stu-id="40908-207">On the client computer, launch Client.exe from a command prompt window.</span></span>

    <span data-ttu-id="40908-208">Wenn der Client und der Dienst nicht kommunizieren können, finden Sie unter [Tipps zur Problembehandlung für WCF-Beispiele](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="40908-208">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="40908-209">Nach dem Beispiel bereinigen</span><span class="sxs-lookup"><span data-stu-id="40908-209">Clean up after the sample</span></span>

<span data-ttu-id="40908-210">Wenn Sie das Beispiel nach dem Beispiel bereinigen möchten, führen Sie *Cleanup.bat* im Ordner Samples aus, wenn Sie die Ausführung des Beispiels abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="40908-210">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="40908-211">Dadurch werden die Server- und Clientzertifikate aus dem Zertifikatspeicher entfernt.</span><span class="sxs-lookup"><span data-stu-id="40908-211">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="40908-212">Wenn dieses Beispiel computerübergreifend ausgeführt wird, entfernt dieses Skript keine Dienstzertifikate auf einem Client.</span><span class="sxs-lookup"><span data-stu-id="40908-212">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="40908-213">Wenn Sie WCF-Beispiele ausgeführt haben, die Zertifikate Computer übergreifend verwenden, stellen Sie sicher, dass Sie die Dienst Zertifikate löschen, die im Speicher CurrentUser-treudpeople installiert wurden.</span><span class="sxs-lookup"><span data-stu-id="40908-213">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="40908-214">Verwenden Sie dazu den folgenden Befehl: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Beispiel: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="40908-214">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
