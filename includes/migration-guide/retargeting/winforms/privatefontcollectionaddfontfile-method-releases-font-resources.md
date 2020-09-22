---
ms.openlocfilehash: 6ee290f6722480778381376f588e16877894f232
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606487"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a>PrivateFontCollection.AddFontFile-Methode gibt Schriftartenressourcen frei

#### <a name="details"></a>Details

In .NET Framework 4.7.1 und früheren Versionen gibt die <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType>-Klasse keine GDI+-Schriftartenressourcen frei, nachdem <xref:System.Drawing.Text.PrivateFontCollection> für <xref:System.Drawing.Font>-Objekte verworfen wird, die dieser Sammlung mit der <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)>-Methode hinzugefügt werden. In .NET Framework 4.7.2 oder höher gibt <xref:System.Drawing.Text.FontCollection.Dispose%2A> die GDI+-Schriftarten frei, die der Sammlung als Dateien hinzugefügt wurden.

#### <a name="suggestion"></a>Vorschlag

**Aktivieren oder Deaktivieren dieser Änderungen:** Damit eine Anwendung von diesen Änderungen profitieren kann, muss sie unter .NET Framework 4.7.2 oder höher ausgeführt werden. Die Anwendung kann von diesen Änderungen profitieren, wenn Sie Folgendes durchführen:

- Kompilieren Sie diese erneut, um .NET Framework 4.7.2 als Ziel zu verwenden. Diese Änderung wird standardmäßig für Windows Forms-Anwendungen aktiviert, die für .NET Framework 4.7.2 oder höher ausgelegt sind.
- Die Anwendung ist für .NET Framework 4.7.1 oder eine frühere Version ausgelegt und deaktiviert veraltete Verhaltensweisen der Barrierefreiheit, indem wie im folgenden Beispiel dargestellt folgender [AppContext-Schalter](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) zum Abschnitt `<runtime>` der Datei „app.config“ hinzugefügt und auf `false` festgelegt wird.

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

Bei Anwendungen, die für .NET Framework 4.7.2 oder höher ausgelegt sind und das Legacyverhalten beibehalten sollen, können Sie die Nichtfreigabe von Schriftartenressourcen aktivieren, indem dieser AppContext-Schalter ausdrücklich auf `true` festgelegt wird.

| name    | Wert       |
|:--------|:------------|
| Bereich   | Microsoft Edge        |
| Version | 4.7.2       |
| Typ    | Neuzuweisung |

#### <a name="affected-apis"></a>Betroffene APIs

- <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>
- <xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType>
