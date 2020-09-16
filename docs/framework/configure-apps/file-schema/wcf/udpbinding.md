---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: b2ff39e1292cfaad1165e14e693acda2518477a6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559043"
---
# \<udpBinding>
<span data-ttu-id="a8690-101">Ein Konfigurationselement, das zum Konfigurieren der <xref:System.ServiceModel.UdpBinding>-Bindung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a8690-101">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="a8690-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="a8690-102">Syntax</span></span>  
  
```xml  
<udpBinding>
  <binding closeTimeout="TimeSpan"
           duplicateMessageHistoryLength="Integer"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxPendingMessagesTotalSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetransmitCount="Integer"
           multicastInterfaceId="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           timeToLive="TimeSpan">
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8690-103">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a8690-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a8690-104">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a8690-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8690-105">Attribute</span><span class="sxs-lookup"><span data-stu-id="a8690-105">Attributes</span></span>  
  
|<span data-ttu-id="a8690-106">attribute</span><span class="sxs-lookup"><span data-stu-id="a8690-106">Attribute</span></span>|<span data-ttu-id="a8690-107">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="a8690-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="a8690-108">Ein <xref:System.TimeSpan>-Wert, der das Zeitintervall für den Abschluss eines Schließvorgangs angibt.</span><span class="sxs-lookup"><span data-stu-id="a8690-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a8690-109">Dieser Wert muss größer oder gleich <xref:System.TimeSpan.Zero> sein.</span><span class="sxs-lookup"><span data-stu-id="a8690-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a8690-110">Der Standardwert ist 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a8690-110">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="a8690-111">Ein ganzzahliger Wert, der die doppelte Nachrichtenverlaufslänge angibt.</span><span class="sxs-lookup"><span data-stu-id="a8690-111">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="a8690-112">Eine ganze Zahl, die die maximale Speicherkapazität der Nachrichtenpuffer angibt, die Nachrichten aus dem Kanal empfangen.</span><span class="sxs-lookup"><span data-stu-id="a8690-112">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="a8690-113">Der Standardwert ist 524288 (0x80000) Bytes.</span><span class="sxs-lookup"><span data-stu-id="a8690-113">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="a8690-114">Eine ganze Zahl, die die maximale Größe eines Puffers in Bytes angibt, in dem Nachrichten gespeichert werden, während sie für einen mit dieser Bindung konfigurierten Endpunkt verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="a8690-114">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="a8690-115">Der Standardwert ist 65.536 Bytes.</span><span class="sxs-lookup"><span data-stu-id="a8690-115">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="a8690-116">Ein ganzzahliger Wert, der die maximale Anzahl von Nachrichten angibt, die empfangen, jedoch noch nicht aus der Eingangswarteschlange für eine einzelne Kanalinstanz entfernt wurden.</span><span class="sxs-lookup"><span data-stu-id="a8690-116">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="a8690-117">Eine positive ganze Zahl, die die maximale Nachrichtengröße in Bytes einschließlich Header definiert, die in einem für diese Bindung konfigurierten Kanal beim Nachrichtenempfang zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="a8690-117">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="a8690-118">Der Absender erhält einen SOAP-Fehler, wenn die Nachricht zu groß für den Empfänger ist.</span><span class="sxs-lookup"><span data-stu-id="a8690-118">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="a8690-119">Der Empfänger verwirft die Nachricht und erstellt einen Eintrag des Ereignisses im Ablaufverfolgungsprotokoll.</span><span class="sxs-lookup"><span data-stu-id="a8690-119">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="a8690-120">Der Standardwert ist 65.536 Bytes.</span><span class="sxs-lookup"><span data-stu-id="a8690-120">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="a8690-121">Ein ganzzahliger Wert, der die maximale Anzahl neu zu übermittelnder Nachrichten angibt.</span><span class="sxs-lookup"><span data-stu-id="a8690-121">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="a8690-122">Ein ganzzahliger Wert, der die ID der Multicastschnittstelle angibt.</span><span class="sxs-lookup"><span data-stu-id="a8690-122">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="a8690-123">Eine Zeichenfolge, die den Konfigurationsnamen der Bindung enthält.</span><span class="sxs-lookup"><span data-stu-id="a8690-123">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a8690-124">Dieser Wert sollte eindeutig sein, da er von der Bindung zur Identifizierung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a8690-124">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a8690-125">Ab .NET Framework 4 müssen Bindungen und Verhaltensweisen keinen Namen haben.</span><span class="sxs-lookup"><span data-stu-id="a8690-125">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a8690-126">Weitere Informationen zur Standardkonfiguration und zu den namenlosen Bindungen und Verhalten finden Sie unter [vereinfachte Konfiguration](../../../wcf/simplified-configuration.md) und [vereinfachte Konfiguration für WCF-Dienste](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a8690-126">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="a8690-127">Ein <xref:System.TimeSpan>-Wert, der das Zeitintervall für den Abschluss eines Öffnungsvorgangs angibt.</span><span class="sxs-lookup"><span data-stu-id="a8690-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a8690-128">Dieser Wert muss größer oder gleich <xref:System.TimeSpan.Zero> sein.</span><span class="sxs-lookup"><span data-stu-id="a8690-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a8690-129">Der Standardwert ist 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a8690-129">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="a8690-130">Ein <xref:System.TimeSpan>-Wert, der das Zeitintervall für den Abschluss eines Empfangsvorgangs angibt.</span><span class="sxs-lookup"><span data-stu-id="a8690-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a8690-131">Dieser Wert muss größer oder gleich <xref:System.TimeSpan.Zero> sein.</span><span class="sxs-lookup"><span data-stu-id="a8690-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a8690-132">Der Standardwert ist 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="a8690-132">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="a8690-133">Ein <xref:System.TimeSpan>-Wert, der das Zeitintervall für den Abschluss eines Sendevorgangs angibt.</span><span class="sxs-lookup"><span data-stu-id="a8690-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a8690-134">Dieser Wert muss größer oder gleich <xref:System.TimeSpan.Zero> sein.</span><span class="sxs-lookup"><span data-stu-id="a8690-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a8690-135">Der Standardwert ist 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a8690-135">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="a8690-136">Legt die Zeichensatzkodierung fest, die zum Ausgeben von Nachrichten über die Bindung verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a8690-136">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="a8690-137">Gültige Werte sind:</span><span class="sxs-lookup"><span data-stu-id="a8690-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a8690-138">-BigEndianUnicode: Unicode bigEndian-Codierung.</span><span class="sxs-lookup"><span data-stu-id="a8690-138">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="a8690-139">-Unicode: 16-Bit-Codierung.</span><span class="sxs-lookup"><span data-stu-id="a8690-139">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="a8690-140">-UTF8:8-Bit-Codierung</span><span class="sxs-lookup"><span data-stu-id="a8690-140">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="a8690-141">Der Standardwert ist UTF8.</span><span class="sxs-lookup"><span data-stu-id="a8690-141">The default is UTF8.</span></span> <span data-ttu-id="a8690-142">Dieses Attribut ist vom Typ <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="a8690-142">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="a8690-143">Ein Timespan-Wert, der die Gültigkeitsdauer für die Bindung angibt.</span><span class="sxs-lookup"><span data-stu-id="a8690-143">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8690-144">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a8690-144">Child Elements</span></span>  
  
|<span data-ttu-id="a8690-145">Element</span><span class="sxs-lookup"><span data-stu-id="a8690-145">Element</span></span>|<span data-ttu-id="a8690-146">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="a8690-146">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="a8690-147">Definiert die Beschränkungen der Komplexität von SOAP-Nachrichten, die von Endpunkten verarbeitet werden können, die mit dieser Bindung konfiguriert wurden.</span><span class="sxs-lookup"><span data-stu-id="a8690-147">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a8690-148">Dieses Element ist vom Typ <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a8690-148">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8690-149">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a8690-149">Parent Elements</span></span>  
  
|<span data-ttu-id="a8690-150">Element</span><span class="sxs-lookup"><span data-stu-id="a8690-150">Element</span></span>|<span data-ttu-id="a8690-151">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="a8690-151">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="a8690-152">Dieses Element enthält eine Auflistung von standardmäßigen und benutzerdefinierten Bindungen.</span><span class="sxs-lookup"><span data-stu-id="a8690-152">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8690-153">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a8690-153">Remarks</span></span>  
 <span data-ttu-id="a8690-154">UdpBinding ermöglicht WCF-Diensten die Kommunikation über den UDP-Transport.</span><span class="sxs-lookup"><span data-stu-id="a8690-154">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="a8690-155">Sie ermöglicht den Nachrichtenaustausch "Fire and Forget", bei dem ein Client eine Nachricht an einen Dienst sendet und keine Antwort zurückerwartet.</span><span class="sxs-lookup"><span data-stu-id="a8690-155">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8690-156">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a8690-156">Example</span></span>  
 <span data-ttu-id="a8690-157">Im folgenden Beispiel wird gezeigt, wie das <xref:System.ServiceModel.UdpBinding> mithilfe des <`udpBinding`>-Elements konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="a8690-157">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
```xml  
<udpBinding>
  <binding  closeTimeout="00:10:00"
            duplicateMessageHistoryLength="100"
            maxBufferPoolSize="100"
            maxPendingMessagesTotalSize="100000"
            maxReceivedMessageSize="65536"
            maxRetransmitCount="10"
            multicastInterfaceId="00000"
            name="myUdpBinding"
            openTimeout="00:10:00"
            receiveTimeout="00:10:00"
            sendTimeout="00:10:00"
            textEncoding="utf-8"
            timeToLive="00:10:00">
    <readerQuotas />
  </binding>
</udpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="a8690-158">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a8690-158">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="a8690-159">Bindungen</span><span class="sxs-lookup"><span data-stu-id="a8690-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a8690-160">Konfigurieren der vom System bereitgestellten Bindungen</span><span class="sxs-lookup"><span data-stu-id="a8690-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a8690-161">Verwenden von Bindungen, um Dienste und Clients zu konfigurieren</span><span class="sxs-lookup"><span data-stu-id="a8690-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
