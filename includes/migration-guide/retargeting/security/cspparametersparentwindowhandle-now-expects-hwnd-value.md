---
ms.openlocfilehash: 4b5c886ad35afbbf0a68e03b3174ab9ea1f5524f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614514"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a><span data-ttu-id="3cdeb-101">CspParameters.ParentWindowHandle erwartet nun einen HWND-Wert</span><span class="sxs-lookup"><span data-stu-id="3cdeb-101">CspParameters.ParentWindowHandle now expects HWND value</span></span>

#### <a name="details"></a><span data-ttu-id="3cdeb-102">Details</span><span class="sxs-lookup"><span data-stu-id="3cdeb-102">Details</span></span>

<span data-ttu-id="3cdeb-103">Der <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle>-Wert, der in .NET Framework 2.0 eingeführt wurde, ermöglicht einer Anwendung die Registrierung eines Handlewerts für das übergeordnete Fenster, sodass jedes Benutzeroberflächenelement, das auf den Schlüssel zugreifen muss (wie etwa eine PIN-Eingabeaufforderung oder ein Zustimmungsdialogfeld), als untergeordnetes modales Fenster des angegebenen Fensters geöffnet wird. Für eine Windows Forms-App, deren Zielplattform .NET Framework 4.7 oder höher ist, kann die Eigenschaft <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> beispielsweise mit dem folgenden Code festgelegt werden:</span><span class="sxs-lookup"><span data-stu-id="3cdeb-103">The <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> value, introduced in .NET Framework 2.0, allows an application to register a parent window handle value such that any UI required to access the key (such as a PIN prompt or consent dialog) opens as a modal child to the specified window.Starting with apps that target the .NET Framework 4.7, a Windows Forms application can set the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> property with code like the following:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="3cdeb-104">In früheren Versionen von .NET Framework wurde erwartet, dass der Wert ein <xref:System.IntPtr?displayProperty=fullName>-Objekt ist, das einen Speicherort im Arbeitsspeicher darstellt, an dem sich der [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND)-Wert befindet.</span><span class="sxs-lookup"><span data-stu-id="3cdeb-104">In previous versions of the .NET Framework, the value was expected to be an <xref:System.IntPtr?displayProperty=fullName> representing a location in memory where the [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) value resided.</span></span> <span data-ttu-id="3cdeb-105">Das Festlegen der Eigenschaft auf form.Handle hatte unter Windows 7 und früheren Versionen keine Auswirkungen, unter Windows 8 und höheren Versionen resultiert dies jedoch in der Fehlermeldung &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>: The parameter is incorrect.&quot; (CryptographicException: Der Parameter ist falsch.).</span><span class="sxs-lookup"><span data-stu-id="3cdeb-105">Setting the property to form.Handle on Windows 7 and earlier versions had no effect, but on Windows 8 and later versions, it results in a &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>: The parameter is incorrect.&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3cdeb-106">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="3cdeb-106">Suggestion</span></span>

<span data-ttu-id="3cdeb-107">Für Apps mit der Zielplattform .NET Framework 4.7 oder höher, die eine übergeordnete Fensterbeziehung registrieren sollen, wird die Verwendung eines vereinfachten Formulars wie dem folgenden empfohlen:</span><span class="sxs-lookup"><span data-stu-id="3cdeb-107">Applications targeting .NET Framework 4.7 or higher wishing to register a parent window relationship are encouraged to use the simplified form:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="3cdeb-108">Einige Benutzer haben erkannt, dass der richtige zu übergebende Wert die Adresse eines Speicherorts im Arbeitsspeicher war, der den Wert `form.Handle` enthielt. Benutzer können sich gegen dieses geänderte Verhalten entscheiden, indem sie die AppContext-Option `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` auf `true` festlegen. Dies kann</span><span class="sxs-lookup"><span data-stu-id="3cdeb-108">Users who had identified that the correct value to pass was the address of a memory location which held the value `form.Handle` can opt out of the behavior change by setting the AppContext switch `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` to `true`:</span></span>

- <span data-ttu-id="3cdeb-109">durch programmgesteuertes Festlegen von Kompatibilitätsoptionen für AppContext, wie [hier](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46) beschrieben wird,</span><span class="sxs-lookup"><span data-stu-id="3cdeb-109">By programmatically setting compat switches on the AppContext, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="3cdeb-110">Durch Hinzufügen der folgenden Zeile zum Abschnitt `<runtime>` der app.config-Datei:</span><span class="sxs-lookup"><span data-stu-id="3cdeb-110">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<runtime>
 <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
</runtime>
```

<span data-ttu-id="3cdeb-111">Benutzer, die sich umgekehrt für das neue Verhalten der Laufzeit von .NET Framework 4.7 entscheiden, können die AppContext-Option auf `false` festlegen, wenn die Anwendung in älteren Versionen von .NET Framework geladen wird.</span><span class="sxs-lookup"><span data-stu-id="3cdeb-111">Conversely, users who wish to opt in to the new behavior on the .NET Framework 4.7 runtime when the application loads under older .NET Framework versions can set the AppContext switch to `false`.</span></span>

| <span data-ttu-id="3cdeb-112">name</span><span class="sxs-lookup"><span data-stu-id="3cdeb-112">Name</span></span>    | <span data-ttu-id="3cdeb-113">Wert</span><span class="sxs-lookup"><span data-stu-id="3cdeb-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3cdeb-114">Bereich</span><span class="sxs-lookup"><span data-stu-id="3cdeb-114">Scope</span></span>   | <span data-ttu-id="3cdeb-115">Gering</span><span class="sxs-lookup"><span data-stu-id="3cdeb-115">Minor</span></span>       |
| <span data-ttu-id="3cdeb-116">Version</span><span class="sxs-lookup"><span data-stu-id="3cdeb-116">Version</span></span> | <span data-ttu-id="3cdeb-117">4.7</span><span class="sxs-lookup"><span data-stu-id="3cdeb-117">4.7</span></span>         |
| <span data-ttu-id="3cdeb-118">Typ</span><span class="sxs-lookup"><span data-stu-id="3cdeb-118">Type</span></span>    | <span data-ttu-id="3cdeb-119">Neuzuweisung</span><span class="sxs-lookup"><span data-stu-id="3cdeb-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3cdeb-120">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="3cdeb-120">Affected APIs</span></span>

- <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType>
