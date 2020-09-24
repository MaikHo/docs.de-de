---
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: 281d9d7d7e51a837de4f86f85472815956a20319
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153910"
---
# \<declaredTypes>

<span data-ttu-id="b5261-101">Enthält die bekannten Typen, die der <xref:System.Runtime.Serialization.DataContractSerializer> bei der Deserialisierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="b5261-101">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="b5261-102">Weitere Informationen zu Daten Verträgen und bekannten Typen finden Sie unter [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="b5261-102">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="b5261-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5261-103">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="String ">
          <knownType type="String">
            <parameter index="Integer"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5261-104">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="b5261-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b5261-105">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b5261-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5261-106">Attribute</span><span class="sxs-lookup"><span data-stu-id="b5261-106">Attributes</span></span>  

 <span data-ttu-id="b5261-107">Keine</span><span class="sxs-lookup"><span data-stu-id="b5261-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b5261-108">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b5261-108">Child Elements</span></span>  
  
|<span data-ttu-id="b5261-109">Element</span><span class="sxs-lookup"><span data-stu-id="b5261-109">Element</span></span>|<span data-ttu-id="b5261-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b5261-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="b5261-111">Fügt Typen hinzu, die bekannte Typen erfordern.</span><span class="sxs-lookup"><span data-stu-id="b5261-111">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5261-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b5261-112">Parent Elements</span></span>  
  
|<span data-ttu-id="b5261-113">Element</span><span class="sxs-lookup"><span data-stu-id="b5261-113">Element</span></span>|<span data-ttu-id="b5261-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b5261-114">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="b5261-115">Enthält Konfigurationsdaten für den <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b5261-115">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5261-116">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="b5261-116">Remarks</span></span>  

 <span data-ttu-id="b5261-117">Weitere Informationen zu bekannten Typen finden Sie unter [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="b5261-117">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5261-118">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b5261-118">Example</span></span>  

 <span data-ttu-id="b5261-119">Der folgende XML-Code zeigt deklarierte Typen und bekannte Typen, die zu einem-Element hinzugefügt werden `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="b5261-119">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="b5261-120">Im Beispiel werden drei hinzugefügte Typen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b5261-120">The example shows three types being added.</span></span> <span data-ttu-id="b5261-121">Der erste ist ein benutzerdefinierter Typ mit dem Namen "Orders", der einen bekannten Typ mit dem Namen "Item" verwendet.</span><span class="sxs-lookup"><span data-stu-id="b5261-121">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="b5261-122">Der zweite deklarierte Typ ist <xref:System.Collections.Generic.List%601> und verwendet `Item` als bekannten Typ.</span><span class="sxs-lookup"><span data-stu-id="b5261-122">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="b5261-123">Der dritte deklarierte Typ ist <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="b5261-123">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="b5261-124">Der <xref:System.Collections.Generic.Dictionary%602>-Klassentyp ist ein generischer Typ mit zwei Typparametern.</span><span class="sxs-lookup"><span data-stu-id="b5261-124">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="b5261-125">Der erste stellt den Schlüssel dar und der zweite den Wert.</span><span class="sxs-lookup"><span data-stu-id="b5261-125">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="b5261-126">Im folgenden Beispiel wird ein <xref:System.Collections.Generic.List%601> des zweiten Typs (der Wert) zur Liste bekannter Typen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="b5261-126">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="b5261-127">Sie müssen das `index`-Attribut verwenden, um anzugeben, welcher Typparameter im bekannten Typ verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b5261-127">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="b5261-128">In diesem Fall wird der Werttyp über das Indexattribut angegeben, das auf "1" festgelegt ist (die Auflistung ist nullbasiert).</span><span class="sxs-lookup"><span data-stu-id="b5261-128">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
            <parameter index="1"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="b5261-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b5261-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="b5261-130">Bekannte Typen in Datenverträgen</span><span class="sxs-lookup"><span data-stu-id="b5261-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
