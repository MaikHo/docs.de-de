---
title: <system.codedom>-Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 6c35e24696be040788a0c44cbb100ebb35d37157
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149568"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="e372f-102">\<system.codedom>-Element</span><span class="sxs-lookup"><span data-stu-id="e372f-102">\<system.codedom> Element</span></span>

<span data-ttu-id="e372f-103">Gibt die Compilerkonfigurationseinstellungen für verfügbare Sprachanbieter an.</span><span class="sxs-lookup"><span data-stu-id="e372f-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a><span data-ttu-id="e372f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e372f-104">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e372f-105">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="e372f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e372f-106">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e372f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e372f-107">Attribute</span><span class="sxs-lookup"><span data-stu-id="e372f-107">Attributes</span></span>  

 <span data-ttu-id="e372f-108">Keine</span><span class="sxs-lookup"><span data-stu-id="e372f-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e372f-109">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e372f-109">Child Elements</span></span>  
  
|<span data-ttu-id="e372f-110">Element</span><span class="sxs-lookup"><span data-stu-id="e372f-110">Element</span></span>|<span data-ttu-id="e372f-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e372f-111">Description</span></span>|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="e372f-112">Container für Compilerkonfigurationselemente; enthält 0 (null) oder mehr- [\<compiler>](compiler-element.md) Elemente.</span><span class="sxs-lookup"><span data-stu-id="e372f-112">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e372f-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e372f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="e372f-114">Element</span><span class="sxs-lookup"><span data-stu-id="e372f-114">Element</span></span>|<span data-ttu-id="e372f-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e372f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="e372f-116">Das Stammelement in jeder von den Common Language Runtime- und .NET Framework-Anwendungen verwendeten Konfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="e372f-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e372f-117">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="e372f-117">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="e372f-118">.NET Framework Version 2,0</span><span class="sxs-lookup"><span data-stu-id="e372f-118">.NET Framework Version 2.0</span></span>  

 <span data-ttu-id="e372f-119">Das [\<system.codedom>](system-codedom-element.md) -Element enthält die Compilerkonfigurationseinstellungen für Sprachanbieter, die auf einem Computer installiert sind, zusätzlich zu den Standard Anbietern, die mit dem .NET Framework installiert werden, z <xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider> . b. und.</span><span class="sxs-lookup"><span data-stu-id="e372f-119">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="e372f-120">Das- [\<compilers>](compilers-element.md) Element enthält NULL oder mehr- [\<compiler>](compiler-element.md) Elemente.</span><span class="sxs-lookup"><span data-stu-id="e372f-120">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="e372f-121">Jedes- [\<compiler>](compiler-element.md) Element gibt die Compilerkonfigurationsattribute für einen bestimmten Sprachanbieter an.</span><span class="sxs-lookup"><span data-stu-id="e372f-121">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="e372f-122">Entwickler und Compileranbieter können der Computer Konfigurationsdatei (Machine.config) Konfigurationseinstellungen für eine neue <xref:System.CodeDom.Compiler.CodeDomProvider> Implementierung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e372f-122">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="e372f-123">Verwenden <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> Sie die-Methode, um die Standard Sprachanbieter und Sprachanbieter, die von den Compilerkonfigurationseinstellungen eines Computers identifiziert werden, Programm gesteuert aufzuzählen.</span><span class="sxs-lookup"><span data-stu-id="e372f-123">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e372f-124">In den .NET Framework Versionen 1,0 und 1,1 werden die von der .NET Framework bereitgestellten Standard Sprachanbieter im- [\<compilers>](compilers-element.md) Element identifiziert.</span><span class="sxs-lookup"><span data-stu-id="e372f-124">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="e372f-125">In der .NET Framework Version 2,0 werden die Standard Sprachanbieter nicht im-Element identifiziert [\<compilers>](compilers-element.md) , Sie können jedoch mit der-Methode aufgelistet werden <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> .</span><span class="sxs-lookup"><span data-stu-id="e372f-125">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="e372f-126">.NET Framework Versionen 1,0 und 1,1</span><span class="sxs-lookup"><span data-stu-id="e372f-126">.NET Framework Versions 1.0 and 1.1</span></span>  

 <span data-ttu-id="e372f-127">Das- [\<system.codedom>](system-codedom-element.md) Element enthält die Compilerkonfigurationseinstellungen für Sprachanbieter auf einem Computer.</span><span class="sxs-lookup"><span data-stu-id="e372f-127">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="e372f-128">Das- [\<compilers>](compilers-element.md) Element enthält NULL oder mehr- [\<compiler>](compiler-element.md) Elemente.</span><span class="sxs-lookup"><span data-stu-id="e372f-128">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="e372f-129">Jedes- [\<compiler>](compiler-element.md) Element gibt die Compilerkonfigurationsattribute für einen bestimmten Sprachanbieter an.</span><span class="sxs-lookup"><span data-stu-id="e372f-129">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="e372f-130">.NET Framework definiert die ursprünglichen Compilereinstellungen in der Computerkonfigurationsdatei (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e372f-130">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="e372f-131">Entwickler und Compileranbieter können Konfigurationseinstellungen für eine neue <xref:System.CodeDom.Compiler.CodeDomProvider>-Implementierung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e372f-131">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="e372f-132">Verwenden Sie die <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>-Methode, um Sprachanbieter und Compilerkonfigurationseinstellungen auf einem Computer programmgesteuert aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="e372f-132">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e372f-133">Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="e372f-133">Configuration File</span></span>  

 <span data-ttu-id="e372f-134">Dieses Element kann in der Computer Konfigurationsdatei und in der Anwendungs Konfigurationsdatei verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e372f-134">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e372f-135">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e372f-135">Example</span></span>  

 <span data-ttu-id="e372f-136">Das folgende Beispiel veranschaulicht eine typische Compilerkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="e372f-136">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=1.0.5000.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e372f-137">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e372f-137">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="e372f-138">Konfigurationsdateischema</span><span class="sxs-lookup"><span data-stu-id="e372f-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e372f-139">Schema für Compiler- und Sprachanbietereinstellungen</span><span class="sxs-lookup"><span data-stu-id="e372f-139">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e372f-140">\<compiler>-Element</span><span class="sxs-lookup"><span data-stu-id="e372f-140">\<compiler> Element</span></span>](compiler-element.md)
