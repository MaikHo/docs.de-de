---
title: <publisherPolicy>-Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
ms.openlocfilehash: bd6ab1123ef3f84f7e8a06b25ce48aed37e4bef7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195258"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="5d4e8-102">\<publisherPolicy>-Element</span><span class="sxs-lookup"><span data-stu-id="5d4e8-102">\<publisherPolicy> Element</span></span>

<span data-ttu-id="5d4e8-103">Gibt an, ob die Common Language Runtime die Herausgeberrichtlinie anwendet.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="5d4e8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5d4e8-104">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d4e8-105">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="5d4e8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5d4e8-106">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d4e8-107">Attribute</span><span class="sxs-lookup"><span data-stu-id="5d4e8-107">Attributes</span></span>  
  
|<span data-ttu-id="5d4e8-108">attribute</span><span class="sxs-lookup"><span data-stu-id="5d4e8-108">Attribute</span></span>|<span data-ttu-id="5d4e8-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5d4e8-109">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="5d4e8-110">Gibt an, ob Herausgeber Richtlinien angewendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-110">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="5d4e8-111">Attribut anwenden</span><span class="sxs-lookup"><span data-stu-id="5d4e8-111">apply Attribute</span></span>  
  
|<span data-ttu-id="5d4e8-112">Wert</span><span class="sxs-lookup"><span data-stu-id="5d4e8-112">Value</span></span>|<span data-ttu-id="5d4e8-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5d4e8-113">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="5d4e8-114">Wendet Herausgeber Richtlinien an.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-114">Applies publisher policy.</span></span> <span data-ttu-id="5d4e8-115">Dies ist die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-115">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="5d4e8-116">Die Herausgeber Richtlinie wird nicht angewendet.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-116">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d4e8-117">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5d4e8-117">Child Elements</span></span>  

<span data-ttu-id="5d4e8-118">Keine</span><span class="sxs-lookup"><span data-stu-id="5d4e8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d4e8-119">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5d4e8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5d4e8-120">Element</span><span class="sxs-lookup"><span data-stu-id="5d4e8-120">Element</span></span>|<span data-ttu-id="5d4e8-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5d4e8-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="5d4e8-122">Enthält Informationen über die Assemblyversionsumleitung und die Speicherorte von Assemblys.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="5d4e8-123">Das Stammelement in jeder von den Common Language Runtime- und .NET Framework-Anwendungen verwendeten Konfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="5d4e8-124">Kapselt die Bindungsrichtlinie und den Assemblyspeicherort für jede Assembly.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-124">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="5d4e8-125">Verwenden Sie ein- `<dependentAssembly>` Element für jede Assembly.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-125">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="5d4e8-126">Enthält Informationen über die Assemblybindung und die Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d4e8-127">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="5d4e8-127">Remarks</span></span>  

 <span data-ttu-id="5d4e8-128">Wenn ein Komponentenhersteller eine neue Version einer Assembly freigibt, kann der Hersteller eine Herausgeber Richtlinie einschließen, damit Anwendungen, die die alte Version verwenden, nun die neue Version verwenden.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-128">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="5d4e8-129">Um anzugeben, ob die Herausgeber Richtlinie für eine bestimmte Assembly angewendet werden soll, platzieren Sie das- **\<publisherPolicy>** Element im- **\<dependentAssembly>** Element.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-129">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="5d4e8-130">Die Standardeinstellung für das **Apply** -Attribut ist " **Yes**".</span><span class="sxs-lookup"><span data-stu-id="5d4e8-130">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="5d4e8-131">Wenn Sie das **Apply** -Attribut auf **No** festlegen, werden alle vorherigen **Yes** -Einstellungen für eine Assembly überschrieben.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-131">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="5d4e8-132">Die Berechtigung ist erforderlich, damit eine Anwendung die Herausgeber Richtlinie mit dem- [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) Element in der Anwendungs Konfigurationsdatei explizit ignoriert.</span><span class="sxs-lookup"><span data-stu-id="5d4e8-132">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="5d4e8-133">Die Berechtigung wird erteilt, indem das-Flag auf festgelegt wird <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="5d4e8-133">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="5d4e8-134">Weitere Informationen finden Sie unter [Sicherheits Berechtigung für die assemblybindungsumleitung](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="5d4e8-134">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d4e8-135">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5d4e8-135">Example</span></span>  

 <span data-ttu-id="5d4e8-136">Im folgenden Beispiel wird die Herausgeber Richtlinie für die Assembly deaktiviert `myAssembly` .</span><span class="sxs-lookup"><span data-stu-id="5d4e8-136">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d4e8-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5d4e8-137">See also</span></span>

- [<span data-ttu-id="5d4e8-138">Schema für Laufzeiteinstellungen</span><span class="sxs-lookup"><span data-stu-id="5d4e8-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5d4e8-139">Konfigurationsdateischema</span><span class="sxs-lookup"><span data-stu-id="5d4e8-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5d4e8-140">So sucht Common Language Runtime nach Assemblys</span><span class="sxs-lookup"><span data-stu-id="5d4e8-140">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="5d4e8-141">Umleiten von Assemblyversionen</span><span class="sxs-lookup"><span data-stu-id="5d4e8-141">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
