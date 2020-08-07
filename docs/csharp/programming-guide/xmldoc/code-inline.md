---
title: <c> – C#-Programmierhandbuch
description: Erfahren Sie mehr über das XML-Tag <c>. Dieses Tag kennzeichnet einzeiligen Text in einer Beschreibung als Code, während <code> indicates multiple lines.
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: 78e59e1df4b096782e0a97b6d12c21c843a1cb21
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382021"
---
# <a name="c-c-programming-guide"></a>\<c> (C#-Programmierhandbuch)

## <a name="syntax"></a>Syntax

```xml
<c>text</c>
```

## <a name="parameters"></a>Parameter

- `text`

  Der Text, der als Code angegeben werden soll.

## <a name="remarks"></a>Hinweise

Mit dem `<c>`-Tag kann angegeben werden, dass Text in einer Beschreibung als Code gekennzeichnet werden soll. Zum Angeben mehrerer Zeilen als Code wird [\<code>](./code.md) verwendet.

Kompilieren Sie mit [-doc](../../language-reference/compiler-options/doc-compiler-option.md), um Dokumentationskommentare zu einer Datei zu verarbeiten.

## <a name="example"></a>Beispiel

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Siehe auch

- [C#-Programmierhandbuch](../index.md)
- [Empfohlene Tags für Dokumentationskommentare](./recommended-tags-for-documentation-comments.md)
