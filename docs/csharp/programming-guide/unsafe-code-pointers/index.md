---
title: 'Unsicherer Code und Zeiger: C#-Programmierhandbuch'
Description: Hier erfahren Sie mehr über unsicheren Code und Zeiger. C# unterstützt keine Zeiger, Sie können jedoch einen unsicheren Kontext definieren, in dem Zeiger mit dem Schlüsselwort unsafe verwendet werden können.
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 5684a97ed6f7b6632d8fe3d52747d9187c4b8cbc
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381774"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Unsicherer Code und Zeiger (C#-Programmierhandbuch)

Um Typsicherheit und Sicherheit zu gewährleisten, unterstützt C# standardmäßig keine Zeigerarithmetik. Sie können jedoch das [unsafe](../../language-reference/keywords/unsafe.md)-Schlüsselwort verwenden, um einen unsicheren Kontext zu definieren, in dem Zeiger verwendet werden können. Weitere Informationen über Zeiger finden Sie unter [Zeigertypen](pointer-types.md).  
  
> [!NOTE]
> In der Common Language Runtime (CLR) wird unsicherer Code als „nicht überprüfbarer Code“ bezeichnet. Unsicherer Code in C# ist nicht unbedingt gefährlich, es handelt sich dabei lediglich um einen Code, dessen Sicherheit nicht durch die CLR überprüft werden kann. Die CLR wird daher nur unsicheren Code ausführen, wenn sie sich in einer voll vertrauenswürdigen Assembly befindet. Wenn Sie unsicheren Code verwenden, liegt es in Ihrer Verantwortung, dafür zu sorgen, dass Ihr Code keine Sicherheitsrisiken oder Zeigerfehler enthält.  
  
## <a name="unsafe-code-overview"></a>Übersicht über unsicheren Code

Unsicherer Code verfügt über die folgenden Eigenschaften:

- Methoden, Typen und Codeblöcke können als unsicher definiert werden.

- In manchen Fällen kann unsicherer Code die Leistung einer Anwendung erhöhen, indem die Überprüfung von Arraygrenzen entfernt wird.

- Unsicherer Code ist erforderlich, wenn Sie native Funktionen aufrufen, die Zeiger erfordern.

- Die Verwendung von unsicherem Code führt zu Sicherheits- und Stabilitätsrisiken.

- Code, in dem unsichere Blöcke enthalten sind, muss mit der Compileroption [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) kompiliert werden.
  
## <a name="related-sections"></a>Verwandte Abschnitte

Weitere Informationen finden Sie unter:

- [Zeigertypen](pointer-types.md)

- [Fixed size buffers (Puffer fester Größe)](fixed-size-buffers.md)

## <a name="c-language-specification"></a>C#-Sprachspezifikation

Weitere Informationen finden Sie unter [Unsicherer Code](~/_csharplang/spec/unsafe-code.md) in der [C#-Sprachspezifikation](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Siehe auch

- [C#-Programmierhandbuch](../index.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
