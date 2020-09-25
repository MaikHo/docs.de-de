---
title: <cryptographySettings>-Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: 3c3513c05485550202f2fc5bcae1faabb0e75d47
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201810"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="b0fb8-102">\<cryptographySettings>-Element</span><span class="sxs-lookup"><span data-stu-id="b0fb8-102">\<cryptographySettings> Element</span></span>

<span data-ttu-id="b0fb8-103">Enthält Kryptografieeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="b0fb8-103">Contains cryptography settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**

## <a name="syntax"></a><span data-ttu-id="b0fb8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b0fb8-104">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0fb8-105">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="b0fb8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b0fb8-106">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b0fb8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0fb8-107">Attribute</span><span class="sxs-lookup"><span data-stu-id="b0fb8-107">Attributes</span></span>  

 <span data-ttu-id="b0fb8-108">Keine</span><span class="sxs-lookup"><span data-stu-id="b0fb8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b0fb8-109">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b0fb8-109">Child Elements</span></span>  
  
|<span data-ttu-id="b0fb8-110">Element</span><span class="sxs-lookup"><span data-stu-id="b0fb8-110">Element</span></span>|<span data-ttu-id="b0fb8-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b0fb8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoNameMapping>](cryptonamemapping-element.md)|<span data-ttu-id="b0fb8-112">Enthält die Zuordnung von Klassen zu den Anzeigenamen.</span><span class="sxs-lookup"><span data-stu-id="b0fb8-112">Contains mappings of classes to friendly names.</span></span>|  
|[\<oidMap>](oidmap-element.md)|<span data-ttu-id="b0fb8-113">Enthält ASN. 1 objektbezeichnermappings (OID) zu Klassen.</span><span class="sxs-lookup"><span data-stu-id="b0fb8-113">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0fb8-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b0fb8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b0fb8-115">Element</span><span class="sxs-lookup"><span data-stu-id="b0fb8-115">Element</span></span>|<span data-ttu-id="b0fb8-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b0fb8-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b0fb8-117">Das Stammelement in jeder von den Common Language Runtime- und .NET Framework-Anwendungen verwendeten Konfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="b0fb8-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="b0fb8-118">Enthält das- `cryptographySettings` Element.</span><span class="sxs-lookup"><span data-stu-id="b0fb8-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b0fb8-119">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b0fb8-119">Example</span></span>  

 <span data-ttu-id="b0fb8-120">Im folgenden Beispiel wird gezeigt, wie mit dem **\<cryptographySettings>** -Element kryptografienamenszuordnungen und OID-Zuordnungen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="b0fb8-120">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="b0fb8-121">In diesem Beispiel wird die Laufzeit so konfiguriert, dass <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> ein-Objekt zurückgibt, `MyHashClass` und die- `MyCryptoClass` Klasse wird dem Objekt Bezeichner 1.3.36.2.1 zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="b0fb8-121">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0fb8-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b0fb8-122">See also</span></span>

- [<span data-ttu-id="b0fb8-123">Konfigurationsdateischema</span><span class="sxs-lookup"><span data-stu-id="b0fb8-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b0fb8-124">Schema für Kryptografieeinstellungen</span><span class="sxs-lookup"><span data-stu-id="b0fb8-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b0fb8-125">Kryptografische Dienste</span><span class="sxs-lookup"><span data-stu-id="b0fb8-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
