---
title: 'Entschärfung: Pfadtrennzeichen für ZipArchiveEntry.FullName'
description: In diesem Artikel erfahren Sie, wie sich das Pfadtrennzeichen für die Eigenschaft „ZipArchiveEntry.FullName“ ab den Apps geändert hat, die auf .NET Framework 4.6.1 ausgerichtet sind.
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 8cd6362038ce0548681f3d3b44724f3ef9ff62cb
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475293"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="f87ce-103">Entschärfung: Pfadtrennzeichen für ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="f87ce-103">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="f87ce-104">In allen Apps, die für .NET Framework 4.6.1 entwickelt wurden, ändert sich das in der Eigenschaft <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> verwendete Pfadtrennzeichen von einem umgekehrten Schrägstrich (\\) (Vorgängerversionen des .NET Framework) in einen einfachen Schrägstrich (/).</span><span class="sxs-lookup"><span data-stu-id="f87ce-104">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="f87ce-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>-Objekte werden durch Aufrufen einer der Überladungen der <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>-Methode erstellt.</span><span class="sxs-lookup"><span data-stu-id="f87ce-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="f87ce-106">Auswirkungen</span><span class="sxs-lookup"><span data-stu-id="f87ce-106">Impact</span></span>  
 <span data-ttu-id="f87ce-107">Die Änderung bringt die .NET-Implementierung in Einklang mit Abschnitt 4.4.17.1 der [ZIP-Dateiformatspezifikation](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) und ermöglicht es, dass ZIP-Archive auf Nicht-Windows-Systemen entpackt werden.</span><span class="sxs-lookup"><span data-stu-id="f87ce-107">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="f87ce-108">Beim Dekomprimieren einer ZIP-Datei, die für eine frühere Version des .NET Framework unter einem anderen als dem Windows-Betriebssystem – wie etwa macOS – erstellt wurde, bleibt die Verzeichnisstruktur nicht erhalten.</span><span class="sxs-lookup"><span data-stu-id="f87ce-108">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="f87ce-109">Beispielsweise werden unter macOS mehrere Dateien erstellt, für deren Dateinamen der Verzeichnispfad mit umgekehrten Schrägstrichzeichen (\\) und dem Dateinamen verkettet wird.</span><span class="sxs-lookup"><span data-stu-id="f87ce-109">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="f87ce-110">Im Ergebnis wird die Verzeichnisstruktur der dekomprimierten Dateien nicht beibehalten.</span><span class="sxs-lookup"><span data-stu-id="f87ce-110">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="f87ce-111">Die Auswirkungen dieser Änderungen auf ZIP-Dateien, die unter Windows durch die APIs im <xref:System.IO>-Namespace des .NET Framework dekomprimiert werden, sollten minimal sein, da diese APIs sowohl den einfachen Schrägstrich (/) als auch den umgekehrten Schrägstrich (\\) als Pfadtrennzeichen problemlos verarbeiten können.</span><span class="sxs-lookup"><span data-stu-id="f87ce-111">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="f87ce-112">Minderung</span><span class="sxs-lookup"><span data-stu-id="f87ce-112">Mitigation</span></span>  
 <span data-ttu-id="f87ce-113">Wenn dieses Verhalten nicht erwünscht ist, können Sie sich dagegen entscheiden, indem Sie dem Abschnitt [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) Ihrer Anwendungskonfigurationsdatei eine Konfigurationseinstellung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f87ce-113">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="f87ce-114">Im Folgenden sind sowohl der Abschnitt `<runtime>` als auch der Schalter zur Ablehnung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f87ce-114">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="f87ce-115">Dieses Verhalten kann auch für Apps aktiviert werden, die für eine frühere Version des .NET Framework entwickelt wurden, aber in .NET Framework 4.6.1 und höher ausgeführt werden. Dazu müssen Sie dem Abschnitt [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) der Anwendungskonfigurationsdatei nur eine Konfigurationseinstellung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f87ce-115">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="f87ce-116">Im Folgenden sind sowohl der Abschnitt `<runtime>` als auch der Schalter zur Annahme dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f87ce-116">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f87ce-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f87ce-117">See also</span></span>

- [<span data-ttu-id="f87ce-118">Anwendungskompatibilität</span><span class="sxs-lookup"><span data-stu-id="f87ce-118">Application compatibility</span></span>](application-compatibility.md)
