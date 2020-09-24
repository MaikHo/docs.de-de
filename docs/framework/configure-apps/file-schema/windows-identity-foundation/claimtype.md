---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 1b5427210142c70c31c5f736c9b5e281dca53f33
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150868"
---
# \<claimType>

<span data-ttu-id="54d89-101">Gibt einen einzelnen optionalen oder erforderlichen Anspruch für eingehende Sicherheits Token an.</span><span class="sxs-lookup"><span data-stu-id="54d89-101">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="54d89-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="54d89-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54d89-103">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="54d89-103">Attributes and Elements</span></span>  

 <span data-ttu-id="54d89-104">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="54d89-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54d89-105">Attribute</span><span class="sxs-lookup"><span data-stu-id="54d89-105">Attributes</span></span>  
  
|<span data-ttu-id="54d89-106">attribute</span><span class="sxs-lookup"><span data-stu-id="54d89-106">Attribute</span></span>|<span data-ttu-id="54d89-107">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="54d89-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54d89-108">type</span><span class="sxs-lookup"><span data-stu-id="54d89-108">type</span></span>|<span data-ttu-id="54d89-109">Der Anspruchstyp.</span><span class="sxs-lookup"><span data-stu-id="54d89-109">The claim type.</span></span> <span data-ttu-id="54d89-110">In der Regel ein URI.</span><span class="sxs-lookup"><span data-stu-id="54d89-110">Typically a URI.</span></span> <span data-ttu-id="54d89-111">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="54d89-111">Required.</span></span>|  
|<span data-ttu-id="54d89-112">Optional</span><span class="sxs-lookup"><span data-stu-id="54d89-112">optional</span></span>|<span data-ttu-id="54d89-113">Ein boolescher Wert, der angibt, ob der Anspruchstyp optional ist.</span><span class="sxs-lookup"><span data-stu-id="54d89-113">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="54d89-114">Dies ist optional.</span><span class="sxs-lookup"><span data-stu-id="54d89-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54d89-115">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="54d89-115">Child Elements</span></span>  

 <span data-ttu-id="54d89-116">Keine</span><span class="sxs-lookup"><span data-stu-id="54d89-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54d89-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="54d89-117">Parent Elements</span></span>  
  
|<span data-ttu-id="54d89-118">Element</span><span class="sxs-lookup"><span data-stu-id="54d89-118">Element</span></span>|<span data-ttu-id="54d89-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="54d89-119">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="54d89-120">Gibt den Satz erforderlicher Ansprüche für eingehende Sicherheits Token an.</span><span class="sxs-lookup"><span data-stu-id="54d89-120">Specifies the set of required claims for incoming security tokens.</span></span>|
