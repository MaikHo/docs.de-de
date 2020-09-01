---
description: break-Anweisung – C#-Referenz
title: break-Anweisung – C#-Referenz
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 7fd05889f684f7a2282de8222e1195898dead5b9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134743"
---
# <a name="break-c-reference"></a>break (C#-Referenz)

Die `break`-Anweisung beendet die Ausführung der nächsten einschließenden Schleife oder [switch](./switch.md)-Anweisung, in der sie angezeigt wird. Das Steuerelement wird an die Anweisung übergeben, die auf die beendete Anweisung folgt, falls vorhanden.

## <a name="example"></a>Beispiel

In diesem Beispiel enthält die Bedingungsanweisung einen Indikator, der normalerweise zum Zählen von 1 bis 100 verwendet wird. Allerdings beendet die `break`-Anweisung die Schleife nach 4 Durchgängen.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Beispiel

In diesem Beispiel wird die Verwendung von `break` in einer [switch](./switch.md)-Anweisung veranschaulicht.

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Bei Eingabe von `4` sähe die Ausgabe wie folgt aus:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a>Beispiel

In diesem Beispiel wird die `break`-Anweisung verwendet, um aus einer inneren geschachtelten Schleife auszubrechen und die Steuerung an die äußere Schleife zurückzugeben. Die Steuerung wird _nur_ auf der nächsthöheren Ebene in den geschachtelten Schleifen zurückgegeben.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Beispiel

In diesem Beispiel wird die `break`-Anweisung nur verwendet, um während jeder Iteration der Schleife aus dem aktuellen Branch auszubrechen. Die-Schleife selbst ist nicht von den Instanzen von `break` betroffen, die zur geschachtelten [switch](./switch.md)-Anweisung gehören.

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a>C#-Sprachspezifikation

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Siehe auch

- [C#-Referenz](../index.md)
- [C#-Programmierhandbuch](../../programming-guide/index.md)
- [C#-Schlüsselwörter](./index.md)
- [switch](./switch.md)
