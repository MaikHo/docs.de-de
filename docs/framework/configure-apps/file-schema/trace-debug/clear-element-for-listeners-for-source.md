---
title: <clear> -Element für <listeners> für <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: d3e76496c82b508feabf8a46cf7bce7e3d54e8cf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149282"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="99588-102">\<clear> -Element für \<listeners> für \<source></span><span class="sxs-lookup"><span data-stu-id="99588-102">\<clear> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="99588-103">Löscht die `Listeners`-Sammlung für eine Ablaufverfolgungsquelle.</span><span class="sxs-lookup"><span data-stu-id="99588-103">Clears the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="99588-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="99588-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99588-105">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="99588-105">Attributes and Elements</span></span>  

 <span data-ttu-id="99588-106">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="99588-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99588-107">Attribute</span><span class="sxs-lookup"><span data-stu-id="99588-107">Attributes</span></span>  

 <span data-ttu-id="99588-108">Keine</span><span class="sxs-lookup"><span data-stu-id="99588-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99588-109">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="99588-109">Child Elements</span></span>  

 <span data-ttu-id="99588-110">Keine</span><span class="sxs-lookup"><span data-stu-id="99588-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99588-111">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="99588-111">Parent Elements</span></span>  
  
|<span data-ttu-id="99588-112">Element</span><span class="sxs-lookup"><span data-stu-id="99588-112">Element</span></span>|<span data-ttu-id="99588-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="99588-113">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="99588-114">Das Stammelement in jeder von den Common Language Runtime- und .NET Framework-Anwendungen verwendeten Konfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="99588-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="99588-115">Gibt Ablaufverfolgungslistener an, die Meldungen sammeln, speichern und weiterleiten sowie die Ebene, für die ein Ablaufverfolgungsschalter festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="99588-115">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="99588-116">Enthält die Ablaufverfolgungsquellen, die die Ablaufverfolgungsmeldungen initiieren.</span><span class="sxs-lookup"><span data-stu-id="99588-116">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="99588-117">Gibt eine Ablaufverfolgungsquelle an, die die Ablaufverfolgungsmeldungen initiiert.</span><span class="sxs-lookup"><span data-stu-id="99588-117">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="99588-118">Gibt Listener an, die Nachrichten erfassen, speichern und weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="99588-118">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99588-119">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="99588-119">Remarks</span></span>  

 <span data-ttu-id="99588-120">Das- `<clear>` Element entfernt alle Listener aus der-Auflistung `Listeners` für eine Ablauf Verfolgungs Quelle, einschließlich der <xref:System.Diagnostics.DefaultTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="99588-120">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="99588-121">Sie können das- `<clear>` Element verwenden, bevor Sie das- `<add>` Element verwenden, um sicher zu sein, dass keine anderen aktiven Listener in der Auflistung vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="99588-121">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="99588-122">Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="99588-122">Configuration File</span></span>  

 <span data-ttu-id="99588-123">Dieses Element kann in der Computer Konfigurationsdatei (Machine.config) und in der Anwendungs Konfigurationsdatei verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="99588-123">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99588-124">Beispiel</span><span class="sxs-lookup"><span data-stu-id="99588-124">Example</span></span>  

 <span data-ttu-id="99588-125">Im folgenden Beispiel wird gezeigt, wie das `<clear>` -Element verwendet wird, bevor die `<add>` -Elemente zum Hinzufügen der Listener `console` und der-Auflistung `textListener` `Listeners` für die Ablauf Verfolgungs Quelle `TraceSourceApp` verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="99588-125">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="99588-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="99588-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="99588-127">Schema für Ablaufverfolgungs- und Debugeinstellungen</span><span class="sxs-lookup"><span data-stu-id="99588-127">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="99588-128">Ablaufverfolgungslistener</span><span class="sxs-lookup"><span data-stu-id="99588-128">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
