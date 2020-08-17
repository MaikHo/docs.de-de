---
title: Messen der Leistung mithilfe von EventCounters in .NET Core
description: In diesem Tutorial erfahren Sie, wie Sie die Leistung mithilfe von EventCounters messen.
ms.date: 08/07/2020
ms.topic: tutorial
ms.openlocfilehash: 7b4940e17d01e7ec5a50d11e3c818ecdec2d48cf
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024964"
---
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a><span data-ttu-id="d4141-103">Tutorial: Messen der Leistung mithilfe von EventCounters in .NET Core</span><span class="sxs-lookup"><span data-stu-id="d4141-103">Tutorial: Measure performance using EventCounters in .NET Core</span></span>

<span data-ttu-id="d4141-104">**Dieser Artikel gilt für: ✔️** .NET Core 3.0 SDK und neuere Versionen</span><span class="sxs-lookup"><span data-stu-id="d4141-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="d4141-105">In diesem Tutorial erfahren Sie, wie Sie mit <xref:System.Diagnostics.Tracing.EventCounter> die Leistung mit einer hohen Ereignishäufigkeit messen können.</span><span class="sxs-lookup"><span data-stu-id="d4141-105">In this tutorial, you'll learn how an <xref:System.Diagnostics.Tracing.EventCounter> can be used to measure performance with a high frequency of events.</span></span> <span data-ttu-id="d4141-106">Sie können die [verfügbaren Leistungsindikatoren](event-counters.md#available-counters) verwenden, die von verschiedenen offiziellen .NET Core-Paketen oder von Drittanbietern veröffentlicht werden, oder eigene Metriken für die Überwachung erstellen.</span><span class="sxs-lookup"><span data-stu-id="d4141-106">You can use the [available counters](event-counters.md#available-counters) published by various official .NET Core packages, third-party providers, or create your own metrics for monitoring.</span></span>

<span data-ttu-id="d4141-107">In diesem Lernprogramm lernen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="d4141-107">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="d4141-108">Implementieren einer <xref:System.Diagnostics.Tracing.EventSource>.</span><span class="sxs-lookup"><span data-stu-id="d4141-108">Implement an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>
> - <span data-ttu-id="d4141-109">Überwachen von Leistungsindikatoren mit [dotnet-counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="d4141-109">Monitor counters with [dotnet-counters](dotnet-counters.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4141-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d4141-110">Prerequisites</span></span>

<span data-ttu-id="d4141-111">Im Tutorial wird Folgendes verwendet:</span><span class="sxs-lookup"><span data-stu-id="d4141-111">The tutorial uses:</span></span>

- <span data-ttu-id="d4141-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) oder höher</span><span class="sxs-lookup"><span data-stu-id="d4141-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="d4141-113">[dotnet-counters](dotnet-counters.md) zum Überwachen von Ereignisleistungsindikatoren.</span><span class="sxs-lookup"><span data-stu-id="d4141-113">[dotnet-counters](dotnet-counters.md) to monitor event counters.</span></span>
- <span data-ttu-id="d4141-114">Eine [Beispieldebugziel](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)-App für die Diagnose.</span><span class="sxs-lookup"><span data-stu-id="d4141-114">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) app to diagnose.</span></span>

## <a name="get-the-source"></a><span data-ttu-id="d4141-115">Herunterladen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="d4141-115">Get the source</span></span>

<span data-ttu-id="d4141-116">Die Beispielanwendung wird als Grundlage für die Überwachung verwendet.</span><span class="sxs-lookup"><span data-stu-id="d4141-116">The sample application will be used as a basis for monitoring.</span></span> <span data-ttu-id="d4141-117">Das [ASP.NET Core-Beispielrepository](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) ist im Beispielbrowser verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d4141-117">The [sample ASP.NET Core repository](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) is available from the samples browser.</span></span> <span data-ttu-id="d4141-118">Sie laden die ZIP-Datei herunter, extrahieren Sie nach dem Download und öffnen sie in Ihrer bevorzugten IDE.</span><span class="sxs-lookup"><span data-stu-id="d4141-118">You download the zip file, extract it once downloaded, and open it in your favorite IDE.</span></span> <span data-ttu-id="d4141-119">Erstellen Sie die Anwendung, und führen Sie sie aus, um sicherzustellen, dass sie ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="d4141-119">Build and run the application to ensure that it works properly, then stop the application.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="d4141-120">Implementieren einer EventSource</span><span class="sxs-lookup"><span data-stu-id="d4141-120">Implement an EventSource</span></span>

<span data-ttu-id="d4141-121">Bei Ereignissen, die im Abstand von wenigen Millisekunden auftreten, sollte der Mehraufwand pro Ereignis gering sein (weniger als eine Millisekunde).</span><span class="sxs-lookup"><span data-stu-id="d4141-121">For events that happen every few milliseconds, you'll want the overhead per event to be low (less than a millisecond).</span></span> <span data-ttu-id="d4141-122">Andernfalls sind die Auswirkungen auf die Leistung erheblich.</span><span class="sxs-lookup"><span data-stu-id="d4141-122">Otherwise, the impact on performance will be significant.</span></span> <span data-ttu-id="d4141-123">Das Protokollieren eines Ereignisses bedeutet, dass Sie Daten auf einen Datenträger schreiben.</span><span class="sxs-lookup"><span data-stu-id="d4141-123">Logging an event means you're going to write something to disk.</span></span> <span data-ttu-id="d4141-124">Wenn der Datenträger nicht schnell genug ist, gehen die Ereignisse verloren.</span><span class="sxs-lookup"><span data-stu-id="d4141-124">If the disk is not fast enough, you will lose events.</span></span> <span data-ttu-id="d4141-125">Sie benötigen eine andere Lösung als eine Protokollierung des Ereignisses selbst.</span><span class="sxs-lookup"><span data-stu-id="d4141-125">You need a solution other than logging the event itself.</span></span>

<span data-ttu-id="d4141-126">Bei einer großen Anzahl von Ereignissen ist es auch nicht sinnvoll, ein Measure pro Ereignis zu kennen.</span><span class="sxs-lookup"><span data-stu-id="d4141-126">When dealing with a large number of events, knowing the measure per event is not useful either.</span></span> <span data-ttu-id="d4141-127">In den meisten Fällen benötigen Sie nur einige statistische Daten.</span><span class="sxs-lookup"><span data-stu-id="d4141-127">Most of the time all you need is just some statistics out of it.</span></span> <span data-ttu-id="d4141-128">Sie könnten also die Statistiken innerhalb des Prozesses selbst abrufen und dann ab und zu ein Ereignis schreiben, um die Statistiken zu melden. Auf diese Weise geht <xref:System.Diagnostics.Tracing.EventCounter> vor.</span><span class="sxs-lookup"><span data-stu-id="d4141-128">So you could get the statistics within the process itself and then write an event once in a while to report the statistics, that's what <xref:System.Diagnostics.Tracing.EventCounter> will do.</span></span>

<span data-ttu-id="d4141-129">Im Folgenden finden Sie ein Beispiel für die Implementierung einer <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d4141-129">Below is an example of how to implement an <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span></span> <span data-ttu-id="d4141-130">Erstellen Sie eine neue Datei mit dem Namen *MinimalEventCounterSource.cs*, und verwenden Sie den Codeausschnitt als Quelle:</span><span class="sxs-lookup"><span data-stu-id="d4141-130">Create a new file named *MinimalEventCounterSource.cs* and use the code snippet as its source:</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="d4141-131">Die Zeile <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> ist der <xref:System.Diagnostics.Tracing.EventSource>-Teil und nicht Teil von <xref:System.Diagnostics.Tracing.EventCounter>. Sie wurde geschrieben, um zu zeigen, dass Sie eine Meldung zusammen mit dem Ereignisindikator protokollieren können.</span><span class="sxs-lookup"><span data-stu-id="d4141-131">The <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> line is the <xref:System.Diagnostics.Tracing.EventSource> part and is not part of <xref:System.Diagnostics.Tracing.EventCounter>, it was written to show that you can log a message together with the event counter.</span></span>

## <a name="add-an-action-filter"></a><span data-ttu-id="d4141-132">Hinzufügen eines Aktionsfilters</span><span class="sxs-lookup"><span data-stu-id="d4141-132">Add an action filter</span></span>

<span data-ttu-id="d4141-133">Der Beispielquellcode ist ein ASP.NET Core-Projekt.</span><span class="sxs-lookup"><span data-stu-id="d4141-133">The sample source code is an ASP.NET Core project.</span></span> <span data-ttu-id="d4141-134">Sie können einen [Aktionsfilter](/aspnet/core/mvc/controllers/filters#action-filters) global hinzufügen, der die gesamte Anforderungszeit protokolliert.</span><span class="sxs-lookup"><span data-stu-id="d4141-134">You can add an [action filter](/aspnet/core/mvc/controllers/filters#action-filters) globally that will log the total request time.</span></span> <span data-ttu-id="d4141-135">Erstellen Sie eine neue Datei mit dem Namen *LogRequestTimeFilterAttribute.cs*, und verwenden Sie den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="d4141-135">Create a new file named *LogRequestTimeFilterAttribute.cs*, and use the following code:</span></span>

```csharp
using System.Diagnostics;
using Microsoft.AspNetCore.Http.Extensions;
using Microsoft.AspNetCore.Mvc.Filters;

namespace DiagnosticScenarios
{
    public class LogRequestTimeFilterAttribute : ActionFilterAttribute
    {
        readonly Stopwatch _stopwatch = new Stopwatch();

        public override void OnActionExecuting(ActionExecutingContext context) => _stopwatch.Start();

        public override void OnActionExecuted(ActionExecutedContext context)
        {
            _stopwatch.Stop();

            MinimalEventCounterSource.Log.Request(
                context.HttpContext.Request.GetDisplayUrl(), _stopwatch.ElapsedMilliseconds);
        }
    }
}
```

<span data-ttu-id="d4141-136">Der Aktionsfilter startet ein <xref:System.Diagnostics.Stopwatch>-Element, wenn die Anforderung beginnt, und beendet es, wenn die Anforderung abgeschlossen ist, wobei die verstrichene Zeit erfasst wird.</span><span class="sxs-lookup"><span data-stu-id="d4141-136">The action filter starts a <xref:System.Diagnostics.Stopwatch> as the request begins, and stops after it has completed, capturing the elapsed time.</span></span> <span data-ttu-id="d4141-137">Die Gesamtzahl der Millisekunden wird in der `MinimalEventCounterSource`-Singleton-Instanz protokolliert.</span><span class="sxs-lookup"><span data-stu-id="d4141-137">The total milliseconds is logged to the `MinimalEventCounterSource` singleton instance.</span></span> <span data-ttu-id="d4141-138">Damit dieser Filter angewendet werden kann, müssen Sie ihn der Filtersammlung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d4141-138">In order for this filter to be applied, you need to add it to the filters collection.</span></span> <span data-ttu-id="d4141-139">Aktualisieren Sie in der Datei *Startup.cs* die `ConfigureServices`-Methode so, dass dieser Filter einbezogen wird.</span><span class="sxs-lookup"><span data-stu-id="d4141-139">In the *Startup.cs* file, update the `ConfigureServices` method in include this filter.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a><span data-ttu-id="d4141-140">Überwachen des Ereignisleistungsindikators</span><span class="sxs-lookup"><span data-stu-id="d4141-140">Monitor event counter</span></span>

<span data-ttu-id="d4141-141">Erstellen und starten Sie die Anwendung mit der Implementierung für eine <xref:System.Diagnostics.Tracing.EventSource> und dem benutzerdefinierte Aktionsfilter.</span><span class="sxs-lookup"><span data-stu-id="d4141-141">With the implementation on an <xref:System.Diagnostics.Tracing.EventSource> and the custom action filter, build and launch the application.</span></span>
<span data-ttu-id="d4141-142">Sie haben die Metrik in <xref:System.Diagnostics.Tracing.EventCounter> protokolliert, aber wenn Sie nicht auf die dort enthaltenen Statistiken zugreifen, ist sie nicht hilfreich.</span><span class="sxs-lookup"><span data-stu-id="d4141-142">You logged the metric to the <xref:System.Diagnostics.Tracing.EventCounter>, but unless you access the statistics from of it, it is not useful.</span></span> <span data-ttu-id="d4141-143">Um die Statistiken abzurufen, müssen Sie <xref:System.Diagnostics.Tracing.EventCounter> aktivieren, indem Sie einen Timer erstellen, der so häufig für die Ereignisse ausgelöst wird, wie Sie möchten, sowie einen Listener, der die Ereignisse erfasst.</span><span class="sxs-lookup"><span data-stu-id="d4141-143">To get the statistics, you need to enable the <xref:System.Diagnostics.Tracing.EventCounter> by creating a timer that fires as frequently as you want the events, as well as a listener to capture the events.</span></span> <span data-ttu-id="d4141-144">Hierzu können Sie [dotnet-counters](dotnet-counters.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="d4141-144">To do that, you can use [dotnet-counters](dotnet-counters.md).</span></span>

<span data-ttu-id="d4141-145">Verwenden Sie den Befehl [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps), um eine Liste der .NET-Prozesse anzuzeigen, die überwacht werden können.</span><span class="sxs-lookup"><span data-stu-id="d4141-145">Use the [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) command to display a list of .NET processes that can be monitored.</span></span>

```console
dotnet-counters ps
```

<span data-ttu-id="d4141-146">Mit dem Prozessbezeichner aus der Ausgabe des Befehls `dotnet-counters ps` können Sie die Überwachung des Ereignisleistungsindikators mit dem folgenden `dotnet-counters monitor`-Befehl starten:</span><span class="sxs-lookup"><span data-stu-id="d4141-146">Using the process identifier from the output of the `dotnet-counters ps` command, you can start monitoring the event counter with the following `dotnet-counters monitor` command:</span></span>

```console
dotnet-counters monitor --process-id 2196 Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

<span data-ttu-id="d4141-147">Während der `dotnet-counters monitor`-Befehl ausgeführt wird, halten Sie <kbd>F5</kbd> im Browser gedrückt, um mit der Ausgabe fortlaufender Anforderungen an den `https://localhost:5001/api/values`-Endpunkt zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="d4141-147">While the `dotnet-counters monitor` command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="d4141-148">Beenden Sie den Vorgang nach einigen Sekunden durch Drücken von <kbd>q</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d4141-148">After a few seconds stop by pressing <kbd>q</kbd></span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Microsoft.AspNetCore.Hosting]
    Request Rate / 1 sec                               9
    Total Requests                                   134
[System.Runtime]
    CPU Usage (%)                                     13
[Sample.EventCounter.Minimal]
    Request Processing Time (ms)                      34.5
```

<span data-ttu-id="d4141-149">Der `dotnet-counters monitor`-Befehl eignet sich hervorragend für aktive Überwachung.</span><span class="sxs-lookup"><span data-stu-id="d4141-149">The `dotnet-counters monitor` command is great for active monitoring.</span></span> <span data-ttu-id="d4141-150">Möglicherweise möchten Sie diese Diagnosemetriken jedoch für die Nachverarbeitung und Analyse erfassen.</span><span class="sxs-lookup"><span data-stu-id="d4141-150">However, you may want to collect these diagnostic metrics for post processing and analysis.</span></span> <span data-ttu-id="d4141-151">Verwenden Sie dazu den Befehl `dotnet-counters collect`.</span><span class="sxs-lookup"><span data-stu-id="d4141-151">For that, use the `dotnet-counters collect` command.</span></span> <span data-ttu-id="d4141-152">Der `collect`-Schalterbefehl ähnelt dem `monitor`-Befehl, akzeptiert jedoch einige zusätzliche Parameter.</span><span class="sxs-lookup"><span data-stu-id="d4141-152">The `collect` switch command is similar to the `monitor` command, but accepts a few additional parameters.</span></span> <span data-ttu-id="d4141-153">Sie können den gewünschten Namen und das Format der Ausgabedatei angeben.</span><span class="sxs-lookup"><span data-stu-id="d4141-153">You can specify the desired output file name and format.</span></span> <span data-ttu-id="d4141-154">Verwenden Sie für eine JSON-Datei namens *diagnostics.json* den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="d4141-154">For a JSON file named *diagnostics.json* use the following command:</span></span>

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

<span data-ttu-id="d4141-155">Während der Befehl ausgeführt wird, halten Sie erneut <kbd>F5</kbd> im Browser gedrückt, um mit der Ausgabe fortlaufender Anforderungen an den `https://localhost:5001/api/values`-Endpunkt zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="d4141-155">Again, while the command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="d4141-156">Beenden Sie den Vorgang nach einigen Sekunden durch Drücken von <kbd>q</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d4141-156">After a few seconds stop by pressing <kbd>q</kbd>.</span></span> <span data-ttu-id="d4141-157">Die Datei *diagnostics.json* wird geschrieben.</span><span class="sxs-lookup"><span data-stu-id="d4141-157">The *diagnostics.json* file is written.</span></span> <span data-ttu-id="d4141-158">Die JSON-Datei, die geschrieben wird, verwendet keine Einzüge. Zur besseren Lesbarkeit werden die Informationen hier jedoch mit Einzug dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d4141-158">The JSON file that is written is not indented, however; for readability it is indented here.</span></span>

```json
{
  "TargetProcess": "DiagnosticScenarios",
  "StartTime": "8/5/2020 3:02:45 PM",
  "Events": [
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    }
  ]
}
```

## <a name="next-steps"></a><span data-ttu-id="d4141-159">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="d4141-159">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d4141-160">EventCounters</span><span class="sxs-lookup"><span data-stu-id="d4141-160">EventCounters</span></span>](event-counters.md)