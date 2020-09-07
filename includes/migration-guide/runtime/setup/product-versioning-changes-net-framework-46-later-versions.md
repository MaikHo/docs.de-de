---
ms.openlocfilehash: 6a79f04af44f78313c4d5bb5c37dfad252d3024b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496114"
---
### <a name="product-versioning-changes-in-the-net-framework-46-and-later-versions"></a>Änderungen der Produktversionsverwaltung in .NET Framework 4.6 und höher

#### <a name="details"></a>Details

Die Produktversionsverwaltung wurde gegenüber früheren Releases von .NET Framework geändert, insbesondere gegenüber .NET Framework 4, 4.5, 4.5.1 und 4.5.2. Im Folgenden finden Sie die detaillierten Änderungen:<ul><li>Der Wert des <code>Version</code>-Eintrags im <code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full</code>-Schlüssel wurde für .NET Framework 4.6 und dessen Punktreleases in <code>4.6.xxxxx</code> und für .NET Framework 4.7 in und 4.7.1 in <code>4.7.xxxxx</code> geändert. In .NET Framework 4.5, 4.5.1 und 4.5.2 lautete das Format <code>4.5.xxxxx</code>.</li><li>Die Datei- und Produktversionsverwaltung für .NET Framework-Dateien wurde vom früheren Schema der Versionsverwaltung von 4.0.30319.x in 4.6.X.0 (für .NET Framework 4.6 und dessen Punktreleases) sowie in 4.7.X.0 (für .NET Framework 4.7 und 4.7.1) geändert. Sie können diese neuen Werte anzeigen, wenn Sie die Eigenschaften der Datei anzeigen, indem Sie mit der rechten Maustaste auf eine Datei klicken.</li><li>Die Attribute <xref:System.Reflection.AssemblyFileVersionAttribute> und <xref:System.Reflection.AssemblyInformationalVersionAttribute> für verwaltete Assemblys verfügen über Versionswerte im Format 4.6.X.0 für .NET Framework 4.6 und die zugehörigen Punktreleases sowie 4.7.X.0 für .NET Framework 4.7 und 4.7.1.</li><li>In .NET Framework 4.6, 4.6.1, 4.6.2, 4.7 und 4.7.1, gibt die <xref:System.Environment.Version?displayProperty=nameWithType>-Eigenschaft die korrigierte Versionszeichenfolge <code>4.0.30319.42000</code> zurück. In .NET Framework 4, 4.5, 4.5.1 und 4.5.2 gibt die Eigenschaft Versionszeichenfolgen im Format <code>4.0.30319.xxxxx</code> zurück (z.B. &quot;4.0.30319.18010&quot;). Es wird nicht empfohlen, eine neue Abhängigkeit von der Eigenschaft „Environment.Version“ im Anwendungscode zu verwenden.</li></ul>Weitere Informationen finden Sie unter [Vorgehensweise: Bestimmen der installierten .NET Framework-Versionen](~/docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

#### <a name="suggestion"></a>Vorschlag

Im Allgemeinen sollten Anwendungen von den empfohlenen Verfahren zum Erkennen solcher Faktoren, wie beispielsweise die Laufzeitversion von .NET Framework und das Installationsverzeichnis, abhängen:<ul><li>Wie Sie die Laufzeitversion von .NET Framework ermitteln, erfahren Sie unter [ Gewusst wie: Determine Which .NET Framework Versions Are Installed](~/docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) (Bestimmen der installierten .NET Framework-Versionen).</li><li>Um den Installationspfad für .NET Framework zu ermitteln, verwenden Sie den Wert des <code>InstallPath</code>-Eintrags im <code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full</code> Schlüssel.</li></ul> <blockquote> [!IMPORTANT] Der Name des Unterschlüssels ist <code>NET Framework Setup</code> und nicht <code>.NET Framework Setup</code>.</blockquote> <ul><li>Um den Verzeichnispfad für die .NET Framework Common Language Runtime zu bestimmen, rufen Sie die <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory?displayProperty=nameWithType>-Methode auf.</li><li>Um die CLR-Version zu erhalten, rufen Sie die <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion?displayProperty=nameWithType>-Methode auf. Für .NET Framework 4 und die dazugehörigen Punktreleases (.NET Framework 4.5, 4.5.1, 4.5.2 sowie .NET Framework 4.6, 4.6.1, 4.6.2, 4.7 und 4.7.1) wird die Zeichenfolge „v4.0.30319“ zurückgegeben.</li></ul>

| name    | Wert       |
|:--------|:------------|
| Bereich   |Gering|
|Version|4.6|
|Typ|Laufzeit|

#### <a name="affected-apis"></a>Betroffene APIs

Nicht über API-Analyse erkennbar.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
