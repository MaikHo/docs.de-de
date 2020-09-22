---
ms.openlocfilehash: 18718ebc934e0175c20411055b8c0a90ef6b175f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539472"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="702b7-101">Globalisierungs-APIs verwenden ICU-Bibliotheken unter Windows</span><span class="sxs-lookup"><span data-stu-id="702b7-101">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="702b7-102">.NET 5.0 und höhere Versionen verwenden bei der Ausführung unter dem Windows 10-Update vom Mai 2019 oder später [ICU](http://site.icu-project.org/home)-Bibliotheken (International Components for Unicode, internationale Komponenten für Unicode) für die Globalisierungsfunktionalität.</span><span class="sxs-lookup"><span data-stu-id="702b7-102">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="702b7-103">Änderungsbeschreibung</span><span class="sxs-lookup"><span data-stu-id="702b7-103">Change description</span></span>

<span data-ttu-id="702b7-104">Zuvor wurden in .NET-Bibliotheken [NLS](/windows/win32/intl/national-language-support)-APIs (National Language Support, Unterstützung der nationalen Sprache) für die Globalisierungsfunktionalität verwendet.</span><span class="sxs-lookup"><span data-stu-id="702b7-104">Previously, .NET libraries used [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality.</span></span> <span data-ttu-id="702b7-105">Beispielsweise wurden NLS-Funktionen verwendet, um Kulturdaten wie z. B. Datums- und Uhrzeitformat-Muster abzurufen, Zeichenfolgen zu vergleichen und Groß-/Kleinschreibung von Zeichenfolgen gemäß der entsprechenden Kultur auszuführen.</span><span class="sxs-lookup"><span data-stu-id="702b7-105">For example, NLS functions were used to get culture data, such as date and time format patterns, compare strings, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="702b7-106">Ab .NET 5.0 verwenden .NET-Bibliotheken [ICU](http://site.icu-project.org/home)-Globalisierungs-APIs, wenn eine App unter dem Windows 10-Update vom Mai 2019 oder später ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="702b7-106">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs.</span></span> <span data-ttu-id="702b7-107">Das Windows 10-Update von Mai 2019 und spätere Versionen werden mit der nativen ICU-Bibliothek ausgeliefert.</span><span class="sxs-lookup"><span data-stu-id="702b7-107">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="702b7-108">Wenn die .NET-Runtime ICU nicht laden kann, verwendet sie stattdessen NLS.</span><span class="sxs-lookup"><span data-stu-id="702b7-108">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

<span data-ttu-id="702b7-109">Diese Änderung wurde aus zwei Gründen eingeführt:</span><span class="sxs-lookup"><span data-stu-id="702b7-109">This change was introduced for two reasons:</span></span>

- <span data-ttu-id="702b7-110">Apps haben auf verschiedenen Plattformen einschließlich Linux, macOS und Windows das gleiche Globalisierungsverhalten.</span><span class="sxs-lookup"><span data-stu-id="702b7-110">Apps have the same globalization behavior across platforms, including Linux, macOS, and Windows.</span></span>
- <span data-ttu-id="702b7-111">Apps können das Globalisierungsverhalten steuern, indem sie benutzerdefinierte ICU-Bibliotheken verwenden.</span><span class="sxs-lookup"><span data-stu-id="702b7-111">Apps can control globalization behavior by using custom ICU libraries.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="702b7-112">Eingeführt in Version</span><span class="sxs-lookup"><span data-stu-id="702b7-112">Version introduced</span></span>

<span data-ttu-id="702b7-113">.NET 5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="702b7-113">.NET 5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="702b7-114">Empfohlene Aktion</span><span class="sxs-lookup"><span data-stu-id="702b7-114">Recommended action</span></span>

<span data-ttu-id="702b7-115">Auf der Seite des Entwicklers ist keine Aktion erforderlich.</span><span class="sxs-lookup"><span data-stu-id="702b7-115">No action is required on the part of the developer.</span></span> <span data-ttu-id="702b7-116">Wenn Sie jedoch weiterhin NLS-Globalisierungs-APIs verwenden möchten, können Sie einen [Runtimeschalter festlegen](../../../../docs/core/run-time-config/globalization.md#nls), um zu diesem Verhalten zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="702b7-116">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../../docs/core/run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="702b7-117">Weitere Informationen zu den verfügbaren Schaltern finden Sie im Artikel [.NET-Globalisierung und ICU](../../../../docs/standard/globalization-localization/globalization-icu.md).</span><span class="sxs-lookup"><span data-stu-id="702b7-117">For more information about the available switches, see the [.NET globalization and ICU](../../../../docs/standard/globalization-localization/globalization-icu.md) article.</span></span>

#### <a name="category"></a><span data-ttu-id="702b7-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="702b7-118">Category</span></span>

<span data-ttu-id="702b7-119">Globalisierung</span><span class="sxs-lookup"><span data-stu-id="702b7-119">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="702b7-120">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="702b7-120">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="702b7-121">Die meisten Typen im <xref:System.Globalization?displayProperty=fullName>-Namespace</span><span class="sxs-lookup"><span data-stu-id="702b7-121">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`

-->
