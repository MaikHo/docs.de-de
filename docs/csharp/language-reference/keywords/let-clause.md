---
description: let-Klausel – C#-Referenz
title: let-Klausel – C#-Referenz
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3767b9745cccd9802374a8100de19f286c9b55ea
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139592"
---
# <a name="let-clause-c-reference"></a>let-Klausel (C#-Referenz)

Bei einem Abfrageausdruck kann es manchmal nützlich sein, das Ergebnis eines Unterausdrucks zur Verwendung in nachfolgenden Klauseln zu speichern. Sie können hierzu das Schlüsselwort `let` verwenden, das eine neue Bereichsvariable erstellt und sie mit dem von Ihnen bereitgestellten Ergebnis des Ausdrucks initialisiert. Sobald die Bereichsvariable mit einem Wert initialisiert wurde, kann sie nicht mehr zum Speichern eines anderen Werts verwendet werden. Enthält die Bereichsvariable jedoch einen abfragbaren Typ, kann sie abgefragt werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird `let` auf zweierlei Weise verwendet:

1. Um einen aufzählbaren Typ zu erstellen, der selbst abgefragt werden kann.

2. Um es der Abfrage zu ermöglichen, `ToLower` nur ein Mal für die Bereichsvariable `word` aufzurufen. Ohne `let` müssten Sie `ToLower` in jedem Prädikat der `where`-Klausel aufrufen.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Siehe auch

- [C#-Referenz](../index.md)
- [Abfrageschlüsselwörter (LINQ)](query-keywords.md)
- [LINQ in C#](../../linq/index.md)
- [Language-Integrated Query (LINQ)](../../programming-guide/concepts/linq/index.md)
- [Behandeln von Ausnahmen in Abfrageausdrücken](../../linq/handle-exceptions-in-query-expressions.md)
