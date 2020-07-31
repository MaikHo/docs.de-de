---
title: Erstellen eines Office Open-Quell-XML-Dokuments (C#)
description: Erstellen Sie in Microsoft Office ein XML-WordprocessingML-Dokument für die Verwendung im Zusammenhang mit C#-Tutorials. Für die Schritte in diesem Artikel wird Microsoft Office benötigt.
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: e6d6908ee6560218793454f3871705e74095f543
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103996"
---
# <a name="creating-the-source-office-open-xml-document-c"></a>Erstellen eines Office Open-Quell-XML-Dokuments (C#)

In diesem Thema wird das Erstellen des Office Open XML-WordprocessingML-Dokuments erläutert, das in den anderen Beispielen in diesem Lernprogramm verwendet wird. Wenn Sie diese Anweisungen befolgen, entspricht Ihre Ausgabe der Ausgabe im jeweiligen Beispiel.

Die Beispiele in diesem Lernprogramm funktionieren mit jedem gültigen WordprocessingML-Dokument.

Um das in diesem Tutorial verwendete Dokument erstellen zu können, muss bei Ihnen entweder Microsoft Office 2007 oder höher oder Microsoft Office 2003 mit dem Compatibility Pack für Microsoft Office 2007-Dateiformate installiert sein.

## <a name="creating-the-wordprocessingml-document"></a>Erstellen des WordprocessingML-Dokuments

#### <a name="to-create-the-wordprocessingml-document"></a>So erstellen Sie das WordprocessingML-Dokument

1. Erstellen Sie ein neues Microsoft Word-Dokument.

2. Fügen Sie in das neue Dokument den folgenden Text ein:

    ```text
    Parsing WordprocessingML with LINQ to XML

    The following example prints to the console.

    using System;

    class Program {
        public static void Main(string[] args) {
            Console.WriteLine("Hello World");
        }
    }

    This example produces the following output:

    Hello World
    ```

3. Formatieren Sie die erste Zeile mit der Formatvorlage "Überschrift 1".

4. Wählen Sie die Zeilen aus, die den C#-Code enthalten. Die erste Zeile beginnt mit dem `using`-Schlüsselwort. Die letzte Zeile ist die letzte schließende geschweifte Klammer. Formatieren Sie die Zeilen mit der Schriftart Courier. Formatieren Sie sie anschließend mit einer neuen Formatvorlage, und geben Sie der neuen Formatvorlage den Namen "Code".

5. Wählen Sie zum Schluss die gesamte Zeile aus, die die Ausgabe enthält, und formatieren Sie sie mit der `Code`-Formatvorlage.

6. Speichern Sie das Dokument, und nennen Sie es <legacyBold>SampleDoc.docx</legacyBold>.

    > [!NOTE]
    > Wenn Sie Microsoft Word 2003 verwenden, wählen Sie in der Dropdownliste **Dateityp** die Option **Word 2007-Dokument**.
