---
title: Sicherheitsberechtigung für die Umleitung der Assemblybindung
description: Erfahren Sie mehr über die für die explizite Umleitung von Assemblybindungen in einer Anwendungs Konfigurationsdatei in .net erforderliche Sicherheits Berechtigung.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: 2de2c50f5adb9e9fa36ea015ef498e9953c83005
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165220"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="45cc1-103">Sicherheitsberechtigung für die Umleitung der Assemblybindung</span><span class="sxs-lookup"><span data-stu-id="45cc1-103">Assembly Binding Redirection Security Permission</span></span>

<span data-ttu-id="45cc1-104">Für die explizite Umleitung einer Assemblybindung in einer Anwendungskonfigurationsdatei ist eine Sicherheitsberechtigung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="45cc1-104">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="45cc1-105">Dies betrifft die Umleitung von .NET Framework-Assemblys und Assemblys von Drittanbietern.</span><span class="sxs-lookup"><span data-stu-id="45cc1-105">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="45cc1-106">Die Berechtigung wird erteilt, indem das-Flag auf festgelegt wird <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="45cc1-106">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="45cc1-107">Verwaltete Assemblys haben standardmäßig keine Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="45cc1-107">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="45cc1-108">Die Sicherheits Berechtigung wird Anwendungen gewährt, die in der vertrauenswürdigen Zone (dem lokalen Computer) und in der Intranetzone ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="45cc1-108">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="45cc1-109">Anwendungen, die in der Internet Zone ausgeführt werden, dürfen keine Umleitung der Assemblybindung durchführen.</span><span class="sxs-lookup"><span data-stu-id="45cc1-109">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="45cc1-110">Die Berechtigung ist nicht erforderlich, wenn die Assemblyumleitung in einer Herausgeber Richtlinien Datei durchgeführt wird, die vom Komponenten Verleger gesteuert wird, oder in der vom Administrator kontrollierten Computer Konfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="45cc1-110">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="45cc1-111">Allerdings ist die-Berechtigung erforderlich, damit eine Anwendung die Herausgeber Richtlinie mit dem- [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) Element in der Anwendungs Konfigurationsdatei explizit ignoriert.</span><span class="sxs-lookup"><span data-stu-id="45cc1-111">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="45cc1-112">In der folgenden Tabelle werden die Standard Sicherheitseinstellungen für das **bindingreumleitungen** -Flag aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="45cc1-112">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="45cc1-113">Zone</span><span class="sxs-lookup"><span data-stu-id="45cc1-113">Zone</span></span>|<span data-ttu-id="45cc1-114">Einstellung für das bindingreumgeleitet-Flag</span><span class="sxs-lookup"><span data-stu-id="45cc1-114">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="45cc1-115">Vertrauenswürdige Zone (lokaler Computer)</span><span class="sxs-lookup"><span data-stu-id="45cc1-115">Trusted Zone (local machine)</span></span>|<span data-ttu-id="45cc1-116">**ON**</span><span class="sxs-lookup"><span data-stu-id="45cc1-116">**ON**</span></span>|  
|<span data-ttu-id="45cc1-117">Intranetzone</span><span class="sxs-lookup"><span data-stu-id="45cc1-117">Intranet Zone</span></span>|<span data-ttu-id="45cc1-118">**ON**</span><span class="sxs-lookup"><span data-stu-id="45cc1-118">**ON**</span></span>|  
|<span data-ttu-id="45cc1-119">Internetzone</span><span class="sxs-lookup"><span data-stu-id="45cc1-119">Internet Zone</span></span>|<span data-ttu-id="45cc1-120">**OFF**</span><span class="sxs-lookup"><span data-stu-id="45cc1-120">**OFF**</span></span>|  
|<span data-ttu-id="45cc1-121">Nicht vertrauenswürdige Zonen</span><span class="sxs-lookup"><span data-stu-id="45cc1-121">Untrusted zones</span></span>|<span data-ttu-id="45cc1-122">**OFF**</span><span class="sxs-lookup"><span data-stu-id="45cc1-122">**OFF**</span></span>|  
  
 <span data-ttu-id="45cc1-123">Ein Administrator kann diese Sicherheitseinstellungen ändern, um bestimmte Szenarien auf einem bestimmten Computer zu unterstützen oder einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="45cc1-123">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="45cc1-124">Es gibt keine Tools zum Ändern der Einstellung für das **bindingreumleitungen** -Flag von der Standardeinstellung. ein Administrator muss die Security.config Datei manuell auf dem Computer eines Benutzers bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="45cc1-124">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45cc1-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="45cc1-125">See also</span></span>

- <span data-ttu-id="45cc1-126">[Herausgeberrichtliniendateien und parallele Ausführung](/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="45cc1-126">[Publisher Policy Files and Side-by-Side Execution](/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="45cc1-127">How to: Aktivieren und Deaktivieren der Bindungsumleitung</span><span class="sxs-lookup"><span data-stu-id="45cc1-127">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="45cc1-128">Parallele Ausführung</span><span class="sxs-lookup"><span data-stu-id="45cc1-128">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
