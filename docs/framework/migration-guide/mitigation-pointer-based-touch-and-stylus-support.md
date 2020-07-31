---
title: 'Entschärfung: Zeigerbasierte Touch- und Stiftunterstützung'
description: Hier erfahren Sie mehr über die Auswirkungen auf das Aktivieren eines optionalen WPF-Touch-/Tablettstiftstapels für WPF-Apps, die auf .NET Framework 4.7 ausgerichtet sind.
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: d0c0effeaa727c615dddc3b92cdd34aafde65705
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475423"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="3a1d9-103">Entschärfung: Zeigerbasierte Touch- und Stiftunterstützung</span><span class="sxs-lookup"><span data-stu-id="3a1d9-103">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="3a1d9-104">WPF-Anwendungen mit der Zielplattform .NET Framework 4.7, die auf Windows-Systemen ab Windows 10 Creators Update ausgeführt werden, können einen optionalen `WM_POINTER`-basierten WPF-Touch/Stiftstapel aktivieren.</span><span class="sxs-lookup"><span data-stu-id="3a1d9-104">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="3a1d9-105">Auswirkungen</span><span class="sxs-lookup"><span data-stu-id="3a1d9-105">Impact</span></span>

<span data-ttu-id="3a1d9-106">Entwickler, die nicht explizit die zeigerbasierte Touch/Stift-Unterstützung aktivieren, sollten keine Änderung im WPF-Touch/Stift-Verhalten feststellen.</span><span class="sxs-lookup"><span data-stu-id="3a1d9-106">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="3a1d9-107">Im Folgenden sind die aktuell bekannten Probleme beim optionalen `WM_POINTER`-basierten Touch/Stift-Stapel aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="3a1d9-107">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="3a1d9-108">Keine Unterstützung für Freihand in Echtzeit.</span><span class="sxs-lookup"><span data-stu-id="3a1d9-108">No support for real-time inking.</span></span>

   <span data-ttu-id="3a1d9-109">Zwar funktionieren Freihand- und Stift-Plug-Ins nach wie vor, sie werden aber im Benutzeroberflächen-Thread verarbeitet, was zu schlechter Leistung führen kann.</span><span class="sxs-lookup"><span data-stu-id="3a1d9-109">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="3a1d9-110">Verhaltensänderungen aufgrund der Verlagerung von Touch/Stift-Ereignissen zu Mausereignissen.</span><span class="sxs-lookup"><span data-stu-id="3a1d9-110">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="3a1d9-111">Die Bearbeitung verhält sich möglicherweise anders.</span><span class="sxs-lookup"><span data-stu-id="3a1d9-111">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="3a1d9-112">Drag/Drop zeigt keine angemessene Rückmeldung bei Toucheingaben.</span><span class="sxs-lookup"><span data-stu-id="3a1d9-112">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="3a1d9-113">(Dies betrifft keine Stifteingaben.)</span><span class="sxs-lookup"><span data-stu-id="3a1d9-113">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="3a1d9-114">Drag/Drop kann für Touch/Stift-Ereignisse nicht mehr ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="3a1d9-114">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="3a1d9-115">Dadurch kann es vorkommen, dass die Anwendung nicht reagiert, bis die Mauseingabe erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="3a1d9-115">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="3a1d9-116">Stattdessen sollten Entwickler Drag & Drop über Mausereignisse einleiten.</span><span class="sxs-lookup"><span data-stu-id="3a1d9-116">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="3a1d9-117">Entscheidung für die WM_POINTER-basierte Touch/Stift-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="3a1d9-117">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="3a1d9-118">Entwickler, die diesen Stapel aktivieren möchten, können der *app.config*-Datei ihrer Anwendung Folgendes hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="3a1d9-118">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="3a1d9-119">Das Entfernen dieses Eintrags oder das Festlegen seines Werts auf `false` deaktiviert diesen optionalen Stapel.</span><span class="sxs-lookup"><span data-stu-id="3a1d9-119">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a1d9-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3a1d9-120">See also</span></span>

- [<span data-ttu-id="3a1d9-121">Anwendungskompatibilität</span><span class="sxs-lookup"><span data-stu-id="3a1d9-121">Application compatibility</span></span>](application-compatibility.md)
