---
title: DateTime-und DateTimeOffset-Unterstützung in System. Text. JSON
description: Eine Übersicht über die Unterstützung von DateTime-und DateTimeOffset-Typen in der System. Text. JSON-Bibliothek.
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 182694a3d2df02d5e2c709e33a02bd9fa7d20383
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2019
ms.locfileid: "69973214"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a><span data-ttu-id="0614d-103">DateTime-und DateTimeOffset-Unterstützung in System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="0614d-103">DateTime and DateTimeOffset support in System.Text.Json</span></span>

<span data-ttu-id="0614d-104">Die System. Text. JSON-Bibliothek analysiert und schreibt <xref:System.DateTime> <xref:System.DateTimeOffset> Werte gemäß dem erweiterten ISO 8601:-2019-Profil.</span><span class="sxs-lookup"><span data-stu-id="0614d-104">The System.Text.Json library parses and writes <xref:System.DateTime> and <xref:System.DateTimeOffset> values according to the ISO 8601:-2019 extended profile.</span></span>
<span data-ttu-id="0614d-105">[Konverter](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) bieten benutzerdefinierte Unterstützung für das Serialisieren und Deserialisieren mit <xref:System.Text.Json.JsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0614d-105">[Converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) provide custom support for serializing and deserializing with <xref:System.Text.Json.JsonSerializer>.</span></span>

## <a name="support-for-the-iso-8601-12019-format"></a><span data-ttu-id="0614d-106">Unterstützung für das ISO 8601-1:2019-Format</span><span class="sxs-lookup"><span data-stu-id="0614d-106">Support for the ISO 8601-1:2019 format</span></span>

<span data-ttu-id="0614d-107">Die <xref:System.Text.Json.JsonSerializer>Typen <xref:System.Text.Json.Utf8JsonReader>, ,<xref:System.Text.Json.Utf8JsonWriter>und <xref:System.DateTimeOffset> analysieren und schreiben<xref:System.DateTime> -und-Textdarstellungen gemäß dem erweiterten Profil des ISO 8601-1:2019-Formats, z. b. 2019-07-26t16. <xref:System.Text.Json.JsonElement> : 59:57-05:00.</span><span class="sxs-lookup"><span data-stu-id="0614d-107">The <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>, and <xref:System.Text.Json.JsonElement> types parse and write <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations according to the extended profile of the ISO 8601-1:2019 format; for example, 2019-07-26T16:59:57-05:00.</span></span>

<span data-ttu-id="0614d-108"><xref:System.DateTime>- <xref:System.DateTimeOffset> und-Daten können mit <xref:System.Text.Json.JsonSerializer>serialisiert werden:</span><span class="sxs-lookup"><span data-stu-id="0614d-108"><xref:System.DateTime> and <xref:System.DateTimeOffset> data can be serialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/serializing-with-jsonserializer.cs)]

<span data-ttu-id="0614d-109">Die Deserialisierung kann auch mit <xref:System.Text.Json.JsonSerializer>erfolgen:</span><span class="sxs-lookup"><span data-stu-id="0614d-109">They can also be deserialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-valid.cs)]

<span data-ttu-id="0614d-110">Mit den Standardoptionen müssen <xref:System.DateTime> Eingabe <xref:System.DateTimeOffset> -und Textdarstellungen dem erweiterten ISO 8601-1:2019-Profil entsprechen.</span><span class="sxs-lookup"><span data-stu-id="0614d-110">With default options, input <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations must conform to the extended ISO 8601-1:2019 profile.</span></span>
<span data-ttu-id="0614d-111">Der Versuch, Darstellungen zu deserialisieren, die nicht dem Profil entsprechen <xref:System.Text.Json.JsonSerializer> , bewirkt, <xref:System.Text.Json.JsonException>dass Folgendes ausgelöst wird:</span><span class="sxs-lookup"><span data-stu-id="0614d-111">Attempting to deserialize representations that don't conform to the profile will cause <xref:System.Text.Json.JsonSerializer> to throw a <xref:System.Text.Json.JsonException>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-error.cs)]

<span data-ttu-id="0614d-112">Bietet strukturierten Zugriff auf den Inhalt einer JSON-Nutzlast, einschließlich <xref:System.DateTime> der- <xref:System.DateTimeOffset> und-Darstellungen. <xref:System.Text.Json.JsonDocument></span><span class="sxs-lookup"><span data-stu-id="0614d-112">The <xref:System.Text.Json.JsonDocument> provides structured access to the contents of a JSON payload, including <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span> <span data-ttu-id="0614d-113">Im folgenden Beispiel wird gezeigt, wie bei einer Sammlung von Temperaturen die Durchschnittstemperatur am Montag berechnet werden kann:</span><span class="sxs-lookup"><span data-stu-id="0614d-113">The example below shows how, when given a collection of temperatures, the average temperature on Mondays can be calculated:</span></span>

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-valid.cs)]

<span data-ttu-id="0614d-114">Wenn Sie versuchen, die durchschnittliche Temperatur bei einer Nutzlast mit nicht kompatiblen <xref:System.DateTime> Darstellungen zu berechnen <xref:System.Text.Json.JsonDocument> , wird eine <xref:System.FormatException>ausgelöst:</span><span class="sxs-lookup"><span data-stu-id="0614d-114">Attempting to compute the average temperature given a payload with non-compliant <xref:System.DateTime> representations will cause <xref:System.Text.Json.JsonDocument> to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-error.cs)]

<span data-ttu-id="0614d-115">Die Schreibvorgänge <xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTime> auf niedrigerer Ebene und <xref:System.DateTimeOffset> Daten:</span><span class="sxs-lookup"><span data-stu-id="0614d-115">The lower level <xref:System.Text.Json.Utf8JsonWriter> writes <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/writing-with-utf8jsonwriter.cs)]

<span data-ttu-id="0614d-116"><xref:System.Text.Json.Utf8JsonReader><xref:System.DateTime> analysiert und<xref:System.DateTimeOffset> Daten:</span><span class="sxs-lookup"><span data-stu-id="0614d-116"><xref:System.Text.Json.Utf8JsonReader> parses <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-valid.cs)]

<span data-ttu-id="0614d-117">Wenn Sie versuchen, nicht kompatible Formate mit <xref:System.Text.Json.Utf8JsonReader> zu lesen, wird eine <xref:System.FormatException>ausgelöst:</span><span class="sxs-lookup"><span data-stu-id="0614d-117">Attempting to read non-compliant formats with <xref:System.Text.Json.Utf8JsonReader> will cause it to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-error.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset-in-xrefsystemtextjsonjsonserializer"></a><span data-ttu-id="0614d-118">Benutzerdefinierte unter <xref:System.DateTime> Stützung <xref:System.DateTimeOffset> für und in<xref:System.Text.Json.JsonSerializer></span><span class="sxs-lookup"><span data-stu-id="0614d-118">Custom support for <xref:System.DateTime> and <xref:System.DateTimeOffset> in <xref:System.Text.Json.JsonSerializer></span></span>

<span data-ttu-id="0614d-119">Wenn Sie möchten, dass das Serialisierungsprogramm eine benutzerdefinierte Formatierung oder Formatierung durchführt, können Sie [benutzerdefinierte Konverter](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0)implementieren.</span><span class="sxs-lookup"><span data-stu-id="0614d-119">If you want the serializer to perform custom parsing or formatting, you can implement [custom converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).</span></span>
<span data-ttu-id="0614d-120">Hier sind einige Beispiele:</span><span class="sxs-lookup"><span data-stu-id="0614d-120">Here are a few examples:</span></span>

### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a><span data-ttu-id="0614d-121">Verwenden `DateTime(Offset).Parse` von und`DateTime(Offset).ToString`</span><span class="sxs-lookup"><span data-stu-id="0614d-121">Using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`</span></span>

<span data-ttu-id="0614d-122">Wenn Sie die Formate der Eingabe <xref:System.DateTime> -oder <xref:System.DateTimeOffset> Textdarstellungen nicht ermitteln können, können Sie die `DateTime(Offset).Parse` -Methode in der konverterleselogik verwenden.</span><span class="sxs-lookup"><span data-stu-id="0614d-122">If you can't determine the formats of your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations, you can use the `DateTime(Offset).Parse` method in your converter read logic.</span></span> <span data-ttu-id="0614d-123">Dies ermöglicht Ihnen die Verwendung von. Umfassende Unterstützung für das Auswerten verschiedener <xref:System.DateTime> -und <xref:System.DateTimeOffset> -Textformate, einschließlich nicht-ISO 8601-Zeichen folgen und ISO 8601-Formaten, die nicht dem erweiterten ISO 8601-1:2019-Profil entsprechen.</span><span class="sxs-lookup"><span data-stu-id="0614d-123">This allows you to use .NET's extensive support for parsing various <xref:System.DateTime> and <xref:System.DateTimeOffset> text formats, including non-ISO 8601 strings and ISO 8601 formats that don't conform to the extended ISO 8601-1:2019 profile.</span></span> <span data-ttu-id="0614d-124">Diese Vorgehensweise ist erheblich weniger leistungsfähig als die native Implementierung des Serialisierungsprogramms.</span><span class="sxs-lookup"><span data-stu-id="0614d-124">This approach is significantly less performant than using the serializer's native implementation.</span></span>

<span data-ttu-id="0614d-125">Zum Serialisieren können Sie die-Methode `DateTime(Offset).ToString` in der konverterschreiblogik verwenden.</span><span class="sxs-lookup"><span data-stu-id="0614d-125">For serializing, you can use the `DateTime(Offset).ToString` method in your converter write logic.</span></span> <span data-ttu-id="0614d-126">Dies ermöglicht es Ihnen, <xref:System.DateTime> mit <xref:System.DateTimeOffset> einem beliebigen [Standardformat für Datum und Uhrzeit](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)und den [benutzerdefinierten Datums-und Uhrzeit Formaten](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)zu schreiben und Werte zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="0614d-126">This allows you to write <xref:System.DateTime> and <xref:System.DateTimeOffset> values using any of the [standard date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), and the [custom date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span></span>
<span data-ttu-id="0614d-127">Dies ist auch bedeutend weniger leistungsfähiger als die systemeigene Implementierung des Serialisierungsprogramms.</span><span class="sxs-lookup"><span data-stu-id="0614d-127">This is also significantly less performant than using the serializer's native implementation.</span></span>

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <span data-ttu-id="0614d-128">Beim Implementieren <xref:System.Text.Json.Serialization.JsonConverter%601>von, `T` und <xref:System.DateTime>ist der `typeToConvert` -Parameter immer `typeof(DateTime)`.</span><span class="sxs-lookup"><span data-stu-id="0614d-128">When implementing <xref:System.Text.Json.Serialization.JsonConverter%601>, and `T` is <xref:System.DateTime>, the `typeToConvert` parameter will always be `typeof(DateTime)`.</span></span>
<span data-ttu-id="0614d-129">Der-Parameter ist nützlich für die Behandlung von polymorphen Fällen und bei der Verwendung `typeof(T)` von Generika, um die Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="0614d-129">The parameter is useful for handling polymorphic cases and when using generics to get `typeof(T)` in a performant way.</span></span>

### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><span data-ttu-id="0614d-130">Verwenden <xref:System.Buffers.Text.Utf8Parser> von und<xref:System.Buffers.Text.Utf8Formatter></span><span class="sxs-lookup"><span data-stu-id="0614d-130">Using <xref:System.Buffers.Text.Utf8Parser> and <xref:System.Buffers.Text.Utf8Formatter></span></span>

<span data-ttu-id="0614d-131">Sie können schnelle UTF-8-basierte Methoden zum Formatieren und formatieren in der Konverterlogik verwenden <xref:System.DateTime> , <xref:System.DateTimeOffset> Wenn Ihre Eingabe-oder Textdarstellungen mit einer der [standardmäßigen Format](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)Zeichenfolgen "R", "l", "O" oder "G" kompatibel sind, oder Sie möchten Schreiben Sie gemäß einem dieser Formate.</span><span class="sxs-lookup"><span data-stu-id="0614d-131">You can use fast UTF-8-based parsing and formatting methods in your converter logic if your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations are compliant with one of the "R", "l", "O", or "G" [standard date and time format Strings](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), or you want to write according to one of these formats.</span></span> <span data-ttu-id="0614d-132">Dies ist viel schneller als die `DateTime(Offset).Parse` Verwendung `DateTime(Offset).ToString`von und.</span><span class="sxs-lookup"><span data-stu-id="0614d-132">This is much faster than using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`.</span></span>

<span data-ttu-id="0614d-133">Dieses Beispiel zeigt einen benutzerdefinierten Konverter, der Werte gemäß <xref:System.DateTime> [dem Standardformat "R"](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier)serialisiert und deserialisiert:</span><span class="sxs-lookup"><span data-stu-id="0614d-133">This example shows a custom converter that serializes and deserializes <xref:System.DateTime> values according to [the "R" standard format](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span></span>

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> <span data-ttu-id="0614d-134">Das Standardformat "R" ist immer 29 Zeichen lang.</span><span class="sxs-lookup"><span data-stu-id="0614d-134">The "R" standard format will always be 29 characters long.</span></span>

### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a><span data-ttu-id="0614d-135">Verwenden `DateTime(Offset).Parse` von als Fall Back für die native Analyse des Serialisierungsprogramms</span><span class="sxs-lookup"><span data-stu-id="0614d-135">Using `DateTime(Offset).Parse` as a fallback to the serializer's native parsing</span></span>

<span data-ttu-id="0614d-136">Wenn Sie in der Regel davon <xref:System.DateTime> ausgehen <xref:System.DateTimeOffset> , dass die Eingabe oder die Daten dem erweiterten ISO 8601-1:2019-Profil entsprechen, können Sie die systemeigene Logik des Serialisierungsprogramms verwenden.</span><span class="sxs-lookup"><span data-stu-id="0614d-136">If you generally expect your input <xref:System.DateTime> or <xref:System.DateTimeOffset> data to conform to the extended ISO 8601-1:2019 profile, you can use the serializer's native parsing logic.</span></span> <span data-ttu-id="0614d-137">Sie können auch nur dann einen Fall Back Mechanismus implementieren.</span><span class="sxs-lookup"><span data-stu-id="0614d-137">You can also implement a fallback mechanism just in case.</span></span>
<span data-ttu-id="0614d-138">Dieses Beispiel zeigt, dass der Konverter die Daten mithilfe <xref:System.DateTime> <xref:System.DateTime.Parse(System.String)>von erfolgreich analysiert, <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>nachdem eine Textdarstellung mit nicht analysiert wurde.</span><span class="sxs-lookup"><span data-stu-id="0614d-138">This example shows that, after failing to parse a <xref:System.DateTime> text representation using <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, the converter successfully parses the data using <xref:System.DateTime.Parse(System.String)>.</span></span>

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example3/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a><span data-ttu-id="0614d-139">Das erweiterte ISO 8601-1:2019-Profil in "System. Text. JSON"</span><span class="sxs-lookup"><span data-stu-id="0614d-139">The extended ISO 8601-1:2019 profile in System.Text.Json</span></span>

### <a name="date-and-time-components"></a><span data-ttu-id="0614d-140">Datums-und Uhrzeit Komponenten</span><span class="sxs-lookup"><span data-stu-id="0614d-140">Date and time components</span></span>

<span data-ttu-id="0614d-141">Das in <xref:System.Text.Json> implementierte erweiterte ISO 8601-1:2019-Profil definiert die folgenden Komponenten für Datums-und Uhrzeit Darstellungen.</span><span class="sxs-lookup"><span data-stu-id="0614d-141">The extended ISO 8601-1:2019 profile implemented in <xref:System.Text.Json> defines the following components for date and time representations.</span></span> <span data-ttu-id="0614d-142">Diese Komponenten werden verwendet, um verschiedene Granularitätsebene zu definieren, die <xref:System.DateTime> bei <xref:System.DateTimeOffset> der Verarbeitung und Formatierung und Darstellungen unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="0614d-142">These components are used to define various levels of granularity supported when parsing and formatting <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span>

| <span data-ttu-id="0614d-143">Komponente</span><span class="sxs-lookup"><span data-stu-id="0614d-143">Component</span></span>       | <span data-ttu-id="0614d-144">Format</span><span class="sxs-lookup"><span data-stu-id="0614d-144">Format</span></span>                      | <span data-ttu-id="0614d-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0614d-145">Description</span></span>                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| <span data-ttu-id="0614d-146">Jahr</span><span class="sxs-lookup"><span data-stu-id="0614d-146">Year</span></span>            | <span data-ttu-id="0614d-147">"yyyy"</span><span class="sxs-lookup"><span data-stu-id="0614d-147">"yyyy"</span></span>                      | <span data-ttu-id="0614d-148">0001-9999</span><span class="sxs-lookup"><span data-stu-id="0614d-148">0001-9999</span></span>                                                                       |
| <span data-ttu-id="0614d-149">Monat</span><span class="sxs-lookup"><span data-stu-id="0614d-149">Month</span></span>           | <span data-ttu-id="0614d-150">"MM"</span><span class="sxs-lookup"><span data-stu-id="0614d-150">"MM"</span></span>                        | <span data-ttu-id="0614d-151">01-12</span><span class="sxs-lookup"><span data-stu-id="0614d-151">01-12</span></span>                                                                           |
| <span data-ttu-id="0614d-152">Day</span><span class="sxs-lookup"><span data-stu-id="0614d-152">Day</span></span>             | <span data-ttu-id="0614d-153">"dd"</span><span class="sxs-lookup"><span data-stu-id="0614d-153">"dd"</span></span>                        | <span data-ttu-id="0614d-154">01-28, 01-29, 01-30, 01-31 basierend auf Monat/Jahr</span><span class="sxs-lookup"><span data-stu-id="0614d-154">01-28, 01-29, 01-30, 01-31 based on month/year</span></span>                                  |
| <span data-ttu-id="0614d-155">Hour</span><span class="sxs-lookup"><span data-stu-id="0614d-155">Hour</span></span>            | <span data-ttu-id="0614d-156">"HH"</span><span class="sxs-lookup"><span data-stu-id="0614d-156">"HH"</span></span>                        | <span data-ttu-id="0614d-157">00-23</span><span class="sxs-lookup"><span data-stu-id="0614d-157">00-23</span></span>                                                                           |
| <span data-ttu-id="0614d-158">Minute</span><span class="sxs-lookup"><span data-stu-id="0614d-158">Minute</span></span>          | <span data-ttu-id="0614d-159">"mm"</span><span class="sxs-lookup"><span data-stu-id="0614d-159">"mm"</span></span>                        | <span data-ttu-id="0614d-160">00-59</span><span class="sxs-lookup"><span data-stu-id="0614d-160">00-59</span></span>                                                                           |
| <span data-ttu-id="0614d-161">Zweimal</span><span class="sxs-lookup"><span data-stu-id="0614d-161">Second</span></span>          | <span data-ttu-id="0614d-162">"ss"</span><span class="sxs-lookup"><span data-stu-id="0614d-162">"ss"</span></span>                        | <span data-ttu-id="0614d-163">00-59</span><span class="sxs-lookup"><span data-stu-id="0614d-163">00-59</span></span>                                                                           |
| <span data-ttu-id="0614d-164">Zweiter Bruchteil</span><span class="sxs-lookup"><span data-stu-id="0614d-164">Second fraction</span></span> | <span data-ttu-id="0614d-165">"FFFFFFF"</span><span class="sxs-lookup"><span data-stu-id="0614d-165">"FFFFFFF"</span></span>                   | <span data-ttu-id="0614d-166">Mindestens eine Ziffer, maximal 16 Ziffern</span><span class="sxs-lookup"><span data-stu-id="0614d-166">Minimum of one digit, maximum of 16 digits</span></span>                                      |
| <span data-ttu-id="0614d-167">Zeit Offset</span><span class="sxs-lookup"><span data-stu-id="0614d-167">Time offset</span></span>     | <span data-ttu-id="0614d-168">"K"</span><span class="sxs-lookup"><span data-stu-id="0614d-168">"K"</span></span>                         | <span data-ttu-id="0614d-169">Entweder "Z" oder "(' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="0614d-169">Either "Z" or "('+'/'-')HH':'mm"</span></span>                                                |
| <span data-ttu-id="0614d-170">Partielle Zeit</span><span class="sxs-lookup"><span data-stu-id="0614d-170">Partial time</span></span>    | <span data-ttu-id="0614d-171">"HH ': ' mm ': ' SS [fffffff]"</span><span class="sxs-lookup"><span data-stu-id="0614d-171">"HH':'mm':'ss[FFFFFFF]"</span></span>     | <span data-ttu-id="0614d-172">Zeit ohne UTC-Offset-Informationen</span><span class="sxs-lookup"><span data-stu-id="0614d-172">Time without UTC offset information</span></span>                                             |
| <span data-ttu-id="0614d-173">Vollständiges Datum</span><span class="sxs-lookup"><span data-stu-id="0614d-173">Full date</span></span>       | <span data-ttu-id="0614d-174">"yyyy'-' mm '-' dd"</span><span class="sxs-lookup"><span data-stu-id="0614d-174">"yyyy'-'MM'-'dd"</span></span>            | <span data-ttu-id="0614d-175">Kalenderdatum</span><span class="sxs-lookup"><span data-stu-id="0614d-175">Calendar date</span></span>                                                                   |
| <span data-ttu-id="0614d-176">Vollzeit</span><span class="sxs-lookup"><span data-stu-id="0614d-176">Full time</span></span>       | <span data-ttu-id="0614d-177">"Partielle Zeit ' K"</span><span class="sxs-lookup"><span data-stu-id="0614d-177">"'Partial time'K"</span></span>           | <span data-ttu-id="0614d-178">UTC der Tages-oder Ortszeit des Tages mit dem Zeit Offset zwischen Ortszeit und UTC</span><span class="sxs-lookup"><span data-stu-id="0614d-178">UTC of day or Local time of day with the time offset between local time and UTC</span></span> |
| <span data-ttu-id="0614d-179">Datum/Uhrzeit</span><span class="sxs-lookup"><span data-stu-id="0614d-179">Date time</span></span>       | <span data-ttu-id="0614d-180">"' Vollständiges Datum ' nicht ' ' voll Zeit '"</span><span class="sxs-lookup"><span data-stu-id="0614d-180">"'Full date''T''Full time'"</span></span> | <span data-ttu-id="0614d-181">Datum und Uhrzeit des Kalenders, z. b. 2019-07-26t16:59:57-05:00</span><span class="sxs-lookup"><span data-stu-id="0614d-181">Calendar date and time of day, e.g. 2019-07-26T16:59:57-05:00</span></span>                   |

### <a name="support-for-parsing"></a><span data-ttu-id="0614d-182">Unterstützung für die-Verarbeitung</span><span class="sxs-lookup"><span data-stu-id="0614d-182">Support for parsing</span></span>

<span data-ttu-id="0614d-183">Die folgenden Granularitätsebene sind für die-Verarbeitung definiert:</span><span class="sxs-lookup"><span data-stu-id="0614d-183">The following levels of granularity are defined for parsing:</span></span>

1. <span data-ttu-id="0614d-184">"Full Date"</span><span class="sxs-lookup"><span data-stu-id="0614d-184">'Full date'</span></span>
    1. <span data-ttu-id="0614d-185">"yyyy'-' mm '-' dd"</span><span class="sxs-lookup"><span data-stu-id="0614d-185">"yyyy'-'MM'-'dd"</span></span>

2. <span data-ttu-id="0614d-186">"' Full Date ' 't ' ' Hour ' ': ' ' Minute '"</span><span class="sxs-lookup"><span data-stu-id="0614d-186">"'Full date''T''Hour'':''Minute'"</span></span>
    1. <span data-ttu-id="0614d-187">"yyyy'-' mm'-' dd ' HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="0614d-187">"yyyy'-'MM'-'dd'T'HH':'mm"</span></span>

3. <span data-ttu-id="0614d-188">"' Vollständiges Datum ' ' ' partielle Zeit '"</span><span class="sxs-lookup"><span data-stu-id="0614d-188">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="0614d-189">"yyyy'-' mm'-' dd ' HH ': ' mm ': ' ss ' ([der sortierbare Format Bezeichner" s "](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="0614d-189">"yyyy'-'MM'-'dd'T'HH':'mm':'ss" ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>
    2. <span data-ttu-id="0614d-190">"yyyy'-' mm'-' dd ' HH ': ' mm ': ' ss '." FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="0614d-190">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

4. <span data-ttu-id="0614d-191">"' Full Date ' 't ' ' Time Hour ' ': ' ' Minute ' ' Zeit Offset '"</span><span class="sxs-lookup"><span data-stu-id="0614d-191">"'Full date''T''Time hour'':''Minute''Time offset'"</span></span>
    1. <span data-ttu-id="0614d-192">"yyyy'-' mm'-' dd ' HH ': ' MMZ '</span><span class="sxs-lookup"><span data-stu-id="0614d-192">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span></span>
    2. <span data-ttu-id="0614d-193">"yyyy'-' mm'-' dd ' HH ': ' mm (' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="0614d-193">"yyyy'-'MM'-'dd'T'HH':'mm('+'/'-')HH':'mm"</span></span>

5. <span data-ttu-id="0614d-194">"Datum/Uhrzeit"</span><span class="sxs-lookup"><span data-stu-id="0614d-194">'Date time'</span></span>
    1. <span data-ttu-id="0614d-195">"yyyy'-' mm'-' dd ' HH ': ' mm ': ' SSZ '</span><span class="sxs-lookup"><span data-stu-id="0614d-195">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>
    2. <span data-ttu-id="0614d-196">"yyyy'-' mm'-' dd ' HH ': ' mm ': ' ss '." Fffffffz "</span><span class="sxs-lookup"><span data-stu-id="0614d-196">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>
    3. <span data-ttu-id="0614d-197">"yyyy'-' mm'-' dd ' HH ': ' mm ': ' SS (' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="0614d-197">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>
    4. <span data-ttu-id="0614d-198">"yyyy'-' mm'-' dd ' HH ': ' mm ': ' ss '." Fffffff (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="0614d-198">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

<span data-ttu-id="0614d-199">Wenn Dezimaltrennzeichen für Sekunden vorhanden sind, muss mindestens eine Ziffer vorhanden sein. `2019-07-26T00:00:00.` ist nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="0614d-199">If there are decimal fractions for seconds, there must be at least one digit; `2019-07-26T00:00:00.` is not allowed.</span></span>
<span data-ttu-id="0614d-200">Bis zu 16 Dezimalstellen sind zulässig, es werden jedoch nur die ersten sieben analysiert.</span><span class="sxs-lookup"><span data-stu-id="0614d-200">While up to 16 fractional digits are allowed, only the first seven are parsed.</span></span> <span data-ttu-id="0614d-201">Alle über diese hinaus werden als null betrachtet.</span><span class="sxs-lookup"><span data-stu-id="0614d-201">Anything beyond that is considered a zero.</span></span>
<span data-ttu-id="0614d-202">Beispielsweise wird `2019-07-26T00:00:00.1234567890` so analysiert, als wäre `2019-07-26T00:00:00.1234567`es.</span><span class="sxs-lookup"><span data-stu-id="0614d-202">For example, `2019-07-26T00:00:00.1234567890` will be parsed as if it is `2019-07-26T00:00:00.1234567`.</span></span>
<span data-ttu-id="0614d-203">Dies soll mit der <xref:System.DateTime> Implementierung kompatibel bleiben, die auf diese Lösung beschränkt ist.</span><span class="sxs-lookup"><span data-stu-id="0614d-203">This is to stay compatible with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>

<span data-ttu-id="0614d-204">Schaltsekunden werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0614d-204">Leap seconds are not supported.</span></span>

### <a name="support-for-formatting"></a><span data-ttu-id="0614d-205">Unterstützung für Formatierung</span><span class="sxs-lookup"><span data-stu-id="0614d-205">Support for formatting</span></span>

<span data-ttu-id="0614d-206">Die folgenden Ebenen der Granularität sind für die Formatierung definiert:</span><span class="sxs-lookup"><span data-stu-id="0614d-206">The following levels of granularity are defined for formatting:</span></span>

1. <span data-ttu-id="0614d-207">"' Vollständiges Datum ' ' ' partielle Zeit '"</span><span class="sxs-lookup"><span data-stu-id="0614d-207">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="0614d-208">"yyyy'-' mm'-' dd ' HH ': ' mm ': ' ss ' ([der sortierbare Format Bezeichner" s "](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="0614d-208">"yyyy'-'MM'-'dd'T'HH':'mm':'ss"  ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>

        <span data-ttu-id="0614d-209">Wird verwendet, um <xref:System.DateTime> einen ohne Sekundenbruchteile und ohne Offset Informationen zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="0614d-209">Used to format a <xref:System.DateTime> without fractional seconds and without offset information.</span></span>

    2. <span data-ttu-id="0614d-210">"yyyy'-' mm'-' dd ' HH ': ' mm ': ' ss '." FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="0614d-210">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

        <span data-ttu-id="0614d-211">Wird verwendet, um <xref:System.DateTime> eine mit Sekundenbruchteilen, aber ohne Offset Informationen zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="0614d-211">Used to format a <xref:System.DateTime> with fractional seconds but without offset information.</span></span>

2. <span data-ttu-id="0614d-212">"Datum/Uhrzeit"</span><span class="sxs-lookup"><span data-stu-id="0614d-212">'Date time'</span></span>
    1. <span data-ttu-id="0614d-213">"yyyy'-' mm'-' dd ' HH ': ' mm ': ' SSZ '</span><span class="sxs-lookup"><span data-stu-id="0614d-213">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>

        <span data-ttu-id="0614d-214">Wird verwendet, um <xref:System.DateTime> eine <xref:System.DateTimeOffset> oder ohne Sekundenbruchteile zu formatieren, jedoch mit einem UTC-Offset.</span><span class="sxs-lookup"><span data-stu-id="0614d-214">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a UTC offset.</span></span>

    2. <span data-ttu-id="0614d-215">"yyyy'-' mm'-' dd ' HH ': ' mm ': ' ss '." Fffffffz "</span><span class="sxs-lookup"><span data-stu-id="0614d-215">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>

        <span data-ttu-id="0614d-216">Wird zum Formatieren <xref:System.DateTime> von <xref:System.DateTimeOffset> oder mit Sekundenbruchteilen und einem UTC-Offset verwendet.</span><span class="sxs-lookup"><span data-stu-id="0614d-216">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a UTC offset.</span></span>

    3. <span data-ttu-id="0614d-217">"yyyy'-' mm'-' dd ' HH ': ' mm ': ' SS (' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="0614d-217">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="0614d-218">Wird verwendet, um <xref:System.DateTime> eine <xref:System.DateTimeOffset> oder ohne Sekundenbruchteile zu formatieren, jedoch mit einem lokalen Offset.</span><span class="sxs-lookup"><span data-stu-id="0614d-218">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a local offset.</span></span>

    4. <span data-ttu-id="0614d-219">"yyyy'-' mm'-' dd ' HH ': ' mm ': ' ss '." Fffffff (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="0614d-219">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="0614d-220">Wird zum Formatieren <xref:System.DateTime> von <xref:System.DateTimeOffset> oder mit Sekundenbruchteilen und mit einem lokalen Offset verwendet.</span><span class="sxs-lookup"><span data-stu-id="0614d-220">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a local offset.</span></span>