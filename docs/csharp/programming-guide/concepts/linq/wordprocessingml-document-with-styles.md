---
title: WordprocessingML-Dokumente mit Formatvorlagen
description: Dieses WordprocessingML-Beispieldokument enthält Absätze, die mit Formatvorlagen formatiert sind. Hier erfahren Sie mehr über die Dokumentteile, die auf Formatvorlagen beruhen.
ms.date: 07/20/2015
ms.assetid: 40e35de6-ac93-4bba-88ab-a018cbe93873
ms.openlocfilehash: b799c1bee95d7d638e6a3210b4876ff036e088eb
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302203"
---
# <a name="wordprocessingml-document-with-styles"></a>WordprocessingML-Dokumente mit Formatvorlagen
Kompliziertere WordprocessingML-Dokumente besitzen Absätze, die mit Formatvorlagen formatiert sind.  
  
 Im Folgenden finden Sie einige hilfreiche Hinweise zum Aufbau von WordprocessingML-Dokumenten. WordprocessingML-Dokumente werden in Paketen gespeichert. Die Pakete bestehen aus mehreren Teilen (der Begriff "Teil" hat im Zusammenhang mit Paketen eine explizite Bedeutung; ganz allgemein handelt es sich bei den Teilen um Dateien, die zu einem Paket zusammengezippt wurden). Wenn ein Dokument Absätze enthält, die mit Formatvorlagen formatiert sind, gibt es einen Dokumentteil, der die Absätze enthält, denen Formatvorlagen zugewiesen wurden. Außerdem gibt es einen Formatvorlagenteil, der die Formatvorlagen enthält, auf die das Dokument zurückgreift.  
  
 Beim Zugriff auf Pakete ist es wichtig, dass Sie dies über die Beziehungen zwischen den Teilen und nicht über einen beliebigen Pfad tun. Auf dieses Problem wird zwar im Tutorial „Bearbeiten von Inhalten in einem WordprocessingML-Dokument“ nicht eingegangen, die Beispielprogramme in diesem Tutorial zeigen aber die korrekte Herangehensweise.  
  
## <a name="a-document-that-uses-styles"></a>Ein Dokument mit Formatvorlagen  
 Das im Thema [Form von WordprocessingML-Dokumenten (C#)](./shape-of-wordprocessingml-documents.md) verwendete WordML-Beispiel ist ein sehr einfaches Beispiel. Das folgende Dokument ist komplizierter: Es weist Absätze auf, die mit Formatvorlagen formatiert wurden. Die einfachste Möglichkeit, den XML-Code zu sehen, der ein Office Open XML-Dokument ausmacht, besteht darin, das [Beispiel für die Ausgabe von Office Open-XML-Dokumentbausteinen (C#)](./example-that-outputs-office-open-xml-document-parts.md) auszuführen.  
  
 Im folgenden Dokument ist der erste Absatz mit der Formatvorlage `Heading1` formatiert worden. Eine Reihe von Absätzen sind mit der Standardformatvorlage formatiert worden. Einigen Absätzen wurde die Formatvorlage `Code` zugewiesen. Aufgrund dieser relativen Komplexität ist dieses Dokument für das Analysieren mit LINQ to XML interessanter.  
  
 In den Absätzen, die nicht mit der Standardformatvorlage formatiert sind, besitzen die Absatzelemente ein untergeordnetes Element mit dem Namen `w:pPr`, das wiederum ein untergeordnetes Element namens `w:pStyle` besitzt. Dieses Element verfügt über ein Attribut, `w:val`, das den Namen der Formatvorlage enthält. Wenn ein Absatz mit der Standardformatvorlage formatiert ist, bedeutet das, dass das Absatzelement kein untergeordnetes `w:p.Pr`-Element besitzt.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<w:document  
    xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:o="urn:schemas-microsoft-com:office:office"  
    xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
    xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
    xmlns:v="urn:schemas-microsoft-com:vml"  
    xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
    xmlns:w10="urn:schemas-microsoft-com:office:word"  
    xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
    xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Heading1" />  
      </w:pPr>  
      <w:r>  
        <w:t>Parsing WordprocessingML with LINQ to XML</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>The following example prints to the console.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>using System;</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>class Program {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    public static void </w:t>  
      </w:r>  
      <w:smartTag w:uri="urn:schemas-microsoft-com:office:smarttags" w:element="place">  
        <w:r w:rsidRPr="00876F34">  
          <w:t>Main</w:t>  
        </w:r>  
      </w:smartTag>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>(string[] args) {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">        Console.WriteLine("Hello World");</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    }</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>}</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>This example produces the following output:</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>Hello World</w:t>  
      </w:r>  
    </w:p>  
    <w:sectPr w:rsidR="00A75AE0" w:rsidSect="00A75AE0">  
      <w:pgSz w:w="12240" w:h="15840" />  
      <w:pgMar w:top="1440" w:right="1800" w:bottom="1440" w:left="1800" w:header="720" w:footer="720" w:gutter="0" />  
      <w:cols w:space="720" />  
      <w:docGrid w:linePitch="360" />  
    </w:sectPr>  
  </w:body>  
</w:document>  
```  
