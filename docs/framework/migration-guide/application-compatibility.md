---
title: Änderungen der Runtime und Neuausrichtung in .NET Framework
description: Hier erfahren Sie mehr über die Anwendungskompatibilität in .NET Framework und die Auswirkungen auf die Laufzeit und Neuzuweisungen von Änderungen bei der Migration zu einer anderen Version.
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: 26f36dd34c6c5ecae8fc5ab373ff60d9e56f8245
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475488"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="e67b3-103">Anwendungskompatibilität in .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e67b3-103">Application compatibility in the .NET Framework</span></span>

<span data-ttu-id="e67b3-104">Kompatibilität ist ein wichtiges Ziel jedes .NET-Release.</span><span class="sxs-lookup"><span data-stu-id="e67b3-104">Compatibility is an important goal of each .NET release.</span></span> <span data-ttu-id="e67b3-105">Durch die Kompatibilität wird sichergestellt, dass jede Version additiv ist. Frühere Versionen funktionieren also weiterhin.</span><span class="sxs-lookup"><span data-stu-id="e67b3-105">Compatibility ensures that each version is additive, so previous versions will continue to work.</span></span> <span data-ttu-id="e67b3-106">Andererseits können Änderungen an früheren Versionen (z. B. zur Leistungssteigerung, Beheben von Sicherheitsproblemen oder Fehlerbehebungen) zu Kompatibilitätsproblemen im vorhandenen Code oder Anwendungen führen, die unter einer späteren Version ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e67b3-106">On the other hand, changes to previous functionality (for example, to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span>

<span data-ttu-id="e67b3-107">Jede App wird wie folgt auf eine spezifische Version von .NET Framework ausgerichtet:</span><span class="sxs-lookup"><span data-stu-id="e67b3-107">Each app targets a specific version of the .NET Framework by:</span></span>

- <span data-ttu-id="e67b3-108">Definieren eines Zielframeworks in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e67b3-108">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="e67b3-109">Angeben des Zielframeworks in einer Projektdatei</span><span class="sxs-lookup"><span data-stu-id="e67b3-109">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="e67b3-110">Anwenden einer <xref:System.Runtime.Versioning.TargetFrameworkAttribute> auf dem Quellcode</span><span class="sxs-lookup"><span data-stu-id="e67b3-110">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="e67b3-111">Bei der Migration von einer Version von .NET Framework zu einer anderen gibt es zwei Arten von Änderungen, die Sie berücksichtigen sollten:</span><span class="sxs-lookup"><span data-stu-id="e67b3-111">When migrating from one version of the .NET Framework to another, there are two types of changes to consider:</span></span>

- [<span data-ttu-id="e67b3-112">Laufzeitänderungen</span><span class="sxs-lookup"><span data-stu-id="e67b3-112">Runtime changes</span></span>](#runtime-changes)
- [<span data-ttu-id="e67b3-113">Neuausrichtungsänderungen</span><span class="sxs-lookup"><span data-stu-id="e67b3-113">Retargeting changes</span></span>](#retargeting-changes)

## <a name="runtime-changes"></a><span data-ttu-id="e67b3-114">Laufzeitänderungen</span><span class="sxs-lookup"><span data-stu-id="e67b3-114">Runtime changes</span></span>

<span data-ttu-id="e67b3-115">Probleme mit der Runtime treten auf, wenn eine neue Runtime auf einem Computer platziert wird und sich das Verhalten einer App ändert.</span><span class="sxs-lookup"><span data-stu-id="e67b3-115">Runtime issues are those that arise when a new runtime is placed on a machine and an app's behavior changes.</span></span> <span data-ttu-id="e67b3-116">Wenn eine neuere Version als die Zielversion ausgeführt wird, nutzt .NET Framework ein *besonderes* Verhalten, um die ältere Zielversion zu imitieren.</span><span class="sxs-lookup"><span data-stu-id="e67b3-116">When running on a newer version than what was targeted, the .NET Framework uses *quirked* behavior to mimic the older targeted version.</span></span> <span data-ttu-id="e67b3-117">Die App wird in der neueren Version ausgeführt, fungiert jedoch, als würde sie in der älteren Version ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e67b3-117">The app runs on the newer version but acts as if it's running on the older version.</span></span> <span data-ttu-id="e67b3-118">Viele Kompatibilitätsprobleme zwischen den .NET Framework-Versionen werden durch dieses besondere Modell minimiert.</span><span class="sxs-lookup"><span data-stu-id="e67b3-118">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="e67b3-119">Wenn eine Binärdatei beispielsweise für .NET Framework 4.0 kompiliert wurde, aber auf einem Computer mit .NET Framework 4.5 oder höher ausgeführt wird, wird sie im .NET Framework 4.0-Kompatibilitätsmodus ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="e67b3-119">For example, if a binary was compiled for .NET Framework 4.0 but runs on a machine with .NET Framework 4.5 or later, it runs in .NET Framework 4.0 compatibility mode.</span></span> <span data-ttu-id="e67b3-120">Das heißt, dass viele der Änderungen der neueren Version sich nicht auf die Binärdatei auswirken.</span><span class="sxs-lookup"><span data-stu-id="e67b3-120">This means that many of the changes in the later version don't affect the binary.</span></span>

<span data-ttu-id="e67b3-121">Die Version von .NET Framework, für die eine Anwendung ausgerichtet ist, wird durch die Zielversion der Einstiegsassembly für die Anwendungsdomäne bestimmt, in der der Code ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e67b3-121">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code runs in.</span></span> <span data-ttu-id="e67b3-122">Alle zusätzlichen in dieser Anwendungsdomäne geladenen Assemblys sind für diese Version ausgelegt.</span><span class="sxs-lookup"><span data-stu-id="e67b3-122">All additional assemblies loaded in that application domain target that version.</span></span> <span data-ttu-id="e67b3-123">Beispielsweise entspricht die Zielversion bei einer ausführbaren Datei dem Kompatibilitätsmodus aller Assemblys, die in der Anwendungsdomäne ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e67b3-123">For example, in the case of an executable, the version that the executable targets is the compatibility mode all assemblies in that application domain run under.</span></span>

<span data-ttu-id="e67b3-124">Sie können eine Liste der Runtimeänderungen anzeigen, die für Ihre Umgebung gelten, indem Sie Ihre aktuelle .NET Framework-Zielversion und dann die Version auswählen, zu der Sie migrieren möchten:</span><span class="sxs-lookup"><span data-stu-id="e67b3-124">To see a list of runtime changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a><span data-ttu-id="e67b3-125">Neuausrichtungsänderungen</span><span class="sxs-lookup"><span data-stu-id="e67b3-125">Retargeting changes</span></span>

<span data-ttu-id="e67b3-126">Neuausrichtungsänderungen beziehen sich auf Änderungen, die auftreten, wenn eine Assembly für eine neuere Zielversion neu kompiliert wird.</span><span class="sxs-lookup"><span data-stu-id="e67b3-126">Retargeting changes are those that arise when an assembly is recompiled to target a newer version.</span></span> <span data-ttu-id="e67b3-127">Das Verwenden einer neuen Zielversion bedeutet, dass die Assembly die neuen Features verwendet und möglicherweise potenzielle Kompatibilitätsprobleme für alte Features auftreten.</span><span class="sxs-lookup"><span data-stu-id="e67b3-127">Targeting a newer version means the assembly opts into the new features as well as potential compatibility issues for old features.</span></span>

<span data-ttu-id="e67b3-128">Sie können eine Liste der Neuausrichtungsänderungen anzeigen, die für Ihre Umgebung gelten, indem Sie Ihre aktuelle .NET Framework-Zielversion und dann die Version auswählen, zu der Sie migrieren möchten:</span><span class="sxs-lookup"><span data-stu-id="e67b3-128">To see a list of retargeting changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a><span data-ttu-id="e67b3-129">Klassifizierung der Auswirkungen</span><span class="sxs-lookup"><span data-stu-id="e67b3-129">Impact classification</span></span>

<span data-ttu-id="e67b3-130">In den Artikeln, in denen die Runtime- und Neuausrichtungsänderungen beschrieben werden, z. B. unter [Neuausrichtungsänderungen für die Migration von 4.7.2 zu 4.8](retargeting/4.7.2-4.8.md), werden einzelne Elemente wie folgt nach ihren erwarteten Auswirkungen klassifiziert:</span><span class="sxs-lookup"><span data-stu-id="e67b3-130">In the topics that describe runtime and retargeting changes, for example, [Retargeting changes for migrating from 4.7.2 to 4.8](retargeting/4.7.2-4.8.md), individual items are classified by their expected impact as follows:</span></span>

<span data-ttu-id="e67b3-131">**Major**</span><span class="sxs-lookup"><span data-stu-id="e67b3-131">**Major**</span></span>\
<span data-ttu-id="e67b3-132">Eine wesentliche Änderung, die viele Apps beeinflusst oder erhebliche Änderungen des Codes erforderlich macht.</span><span class="sxs-lookup"><span data-stu-id="e67b3-132">A significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="e67b3-133">**Minor**</span><span class="sxs-lookup"><span data-stu-id="e67b3-133">**Minor**</span></span>\
<span data-ttu-id="e67b3-134">Eine Änderung, die eine kleine Anzahl von Apps beeinflusst oder geringfügige Änderungen des Codes erforderlich macht.</span><span class="sxs-lookup"><span data-stu-id="e67b3-134">A change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="e67b3-135">**Grenzfall**</span><span class="sxs-lookup"><span data-stu-id="e67b3-135">**Edge case**</span></span>\
<span data-ttu-id="e67b3-136">Eine Änderung, die nur Apps in sehr spezifischen Szenarien beeinflusst, die nicht üblich sind.</span><span class="sxs-lookup"><span data-stu-id="e67b3-136">A change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="e67b3-137">**Transparent**</span><span class="sxs-lookup"><span data-stu-id="e67b3-137">**Transparent**</span></span>\
<span data-ttu-id="e67b3-138">Eine Änderung, die keine nennenswerten Auswirkungen hat, die Entwickler oder Benutzer beachten müssten.</span><span class="sxs-lookup"><span data-stu-id="e67b3-138">A change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="e67b3-139">Die App sollte keine Änderung benötigen.</span><span class="sxs-lookup"><span data-stu-id="e67b3-139">The app should not require modification because of this change.</span></span>

## <a name="see-also"></a><span data-ttu-id="e67b3-140">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e67b3-140">See also</span></span>

- [<span data-ttu-id="e67b3-141">Versionen und Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="e67b3-141">Versions and dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="e67b3-142">Neuigkeiten</span><span class="sxs-lookup"><span data-stu-id="e67b3-142">What's new</span></span>](../whats-new/index.md)
- [<span data-ttu-id="e67b3-143">Veraltete Elemente</span><span class="sxs-lookup"><span data-stu-id="e67b3-143">What's obsolete</span></span>](../whats-new/whats-obsolete.md)
