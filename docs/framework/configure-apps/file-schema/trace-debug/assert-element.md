---
title: <assert>-Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: eb29701912a45a484b1716195b449e8a97d1d4b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149295"
---
# <a name="assert-element"></a><span data-ttu-id="e292a-102">\<assert>-Element</span><span class="sxs-lookup"><span data-stu-id="e292a-102">\<assert> Element</span></span>

<span data-ttu-id="e292a-103">Gibt an, ob ein Meldungsfeld angezeigt wird, wenn Sie die <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>-Methode aufrufen. Außerdem wird der Name der Datei angegeben, in die die Meldung geschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="e292a-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**

## <a name="syntax"></a><span data-ttu-id="e292a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e292a-104">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e292a-105">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="e292a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e292a-106">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e292a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e292a-107">Attribute</span><span class="sxs-lookup"><span data-stu-id="e292a-107">Attributes</span></span>  
  
|<span data-ttu-id="e292a-108">attribute</span><span class="sxs-lookup"><span data-stu-id="e292a-108">Attribute</span></span>|<span data-ttu-id="e292a-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e292a-109">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="e292a-110">Optionales Attribut.</span><span class="sxs-lookup"><span data-stu-id="e292a-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e292a-111">Gibt an, ob ein Meldungs Feld angezeigt werden soll, wenn die **Debug. Assert** -Methode als **false**ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="e292a-111">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="e292a-112">Optionales Attribut.</span><span class="sxs-lookup"><span data-stu-id="e292a-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e292a-113">Gibt den Namen der Datei an, in die die Nachricht geschrieben werden soll, wenn **Debug. Assert** als **false**ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="e292a-113">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="e292a-114">assertuiaktiviertes Attribut</span><span class="sxs-lookup"><span data-stu-id="e292a-114">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="e292a-115">Wert</span><span class="sxs-lookup"><span data-stu-id="e292a-115">Value</span></span>|<span data-ttu-id="e292a-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e292a-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="e292a-117">Zeigt das Meldungs Feld an.</span><span class="sxs-lookup"><span data-stu-id="e292a-117">Displays the message box.</span></span> <span data-ttu-id="e292a-118">Dies ist die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="e292a-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="e292a-119">Das Meldungs Feld wird nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e292a-119">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e292a-120">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e292a-120">Child Elements</span></span>  

 <span data-ttu-id="e292a-121">Keine</span><span class="sxs-lookup"><span data-stu-id="e292a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e292a-122">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e292a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e292a-123">Element</span><span class="sxs-lookup"><span data-stu-id="e292a-123">Element</span></span>|<span data-ttu-id="e292a-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e292a-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e292a-125">Das Stammelement in jeder von den Common Language Runtime- und .NET Framework-Anwendungen verwendeten Konfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="e292a-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e292a-126">Gibt Ablaufverfolgungslistener an, die Meldungen sammeln, speichern und weiterleiten sowie die Ebene, für die ein Ablaufverfolgungsschalter festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="e292a-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e292a-127">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="e292a-127">Remarks</span></span>  

 <span data-ttu-id="e292a-128">Beide Attribute im- **\<assert>** Element sind optional.</span><span class="sxs-lookup"><span data-stu-id="e292a-128">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="e292a-129">Sie können Meldungs Felder deaktivieren, ohne eine Datei anzugeben, in die die Nachrichten geschrieben werden sollen, oder Sie können eine Datei angeben, in die Nachrichten geschrieben werden, während die Nachrichten Felder aktiviert werden</span><span class="sxs-lookup"><span data-stu-id="e292a-129">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e292a-130">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e292a-130">Example</span></span>  

 <span data-ttu-id="e292a-131">Im folgenden Beispiel wird gezeigt, wie Sie das Anzeigen von Meldungs Feldern deaktivieren, wenn Sie **Debug. Assert** aufzurufen und die Nachrichten in schreiben `c:\log.txt` .</span><span class="sxs-lookup"><span data-stu-id="e292a-131">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e292a-132">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e292a-132">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="e292a-133">Schema für Ablaufverfolgungs- und Debugeinstellungen</span><span class="sxs-lookup"><span data-stu-id="e292a-133">Trace and Debug Settings Schema</span></span>](index.md)
