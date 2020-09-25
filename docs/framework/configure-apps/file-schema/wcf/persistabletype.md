---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 6425b21fe50865beb7bb2876ea478b415fbe3944
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181517"
---
# \<persistableType>

<span data-ttu-id="e0604-101">Gibt alle dauerhaften Typen an.</span><span class="sxs-lookup"><span data-stu-id="e0604-101">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="e0604-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0604-102">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="type"></a><span data-ttu-id="e0604-103">Typ</span><span class="sxs-lookup"><span data-stu-id="e0604-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0604-104">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="e0604-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e0604-105">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e0604-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0604-106">Attribute</span><span class="sxs-lookup"><span data-stu-id="e0604-106">Attributes</span></span>  
  
|<span data-ttu-id="e0604-107">attribute</span><span class="sxs-lookup"><span data-stu-id="e0604-107">Attribute</span></span>|<span data-ttu-id="e0604-108">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="e0604-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0604-109">id</span><span class="sxs-lookup"><span data-stu-id="e0604-109">id</span></span>|<span data-ttu-id="e0604-110">Ein erforderliches Attribut, das eine Zeichenfolge enthält, die einen eindeutigen Bezeichner für einen dauerhaften Typ angibt.</span><span class="sxs-lookup"><span data-stu-id="e0604-110">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="e0604-111">name</span><span class="sxs-lookup"><span data-stu-id="e0604-111">name</span></span>|<span data-ttu-id="e0604-112">Ein optionales Attribut, das eine Zeichenfolge enthält, die den Namen des dauerhaften Typs angibt.</span><span class="sxs-lookup"><span data-stu-id="e0604-112">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0604-113">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e0604-113">Child Elements</span></span>  

 <span data-ttu-id="e0604-114">Keine</span><span class="sxs-lookup"><span data-stu-id="e0604-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0604-115">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e0604-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e0604-116">Element</span><span class="sxs-lookup"><span data-stu-id="e0604-116">Element</span></span>|<span data-ttu-id="e0604-117">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e0604-117">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="e0604-118">Eine Auflistung von `persistableType`-Elementen.</span><span class="sxs-lookup"><span data-stu-id="e0604-118">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0604-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e0604-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="e0604-120">Integration in com+-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="e0604-120">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="e0604-121">Vorgehensweise: Konfigurieren von COM+-Diensteinstellungen</span><span class="sxs-lookup"><span data-stu-id="e0604-121">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
