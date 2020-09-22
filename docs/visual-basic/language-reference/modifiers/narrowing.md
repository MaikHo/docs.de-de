---
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: 77515357ac9dc972992df09c471695aad13985c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867933"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)

Gibt an, dass ein Konvertierungs Operator ( `CType` ) eine Klasse oder Struktur in einen Typ konvertiert, der möglicherweise nicht in der Lage ist, einige der möglichen Werte der ursprünglichen Klasse oder Struktur zu speichern.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Umrechnen mit dem einschränkenden Schlüsselwort  

 Die Konvertierungs Prozedur muss `Public Shared` zusätzlich zu angeben `Narrowing` .  
  
 Einschränkende Konvertierungen sind zur Laufzeit nicht immer erfolgreich und können fehlschlagen oder Datenverluste verursachen. Beispiele hierfür `Long` sind `Integer` , `String` `Date` und ein Basistyp für einen abgeleiteten Typ. Diese letzte Konvertierung ist einschränkend, weil der Basistyp möglicherweise nicht alle Member des abgeleiteten Typs enthält und somit keine Instanz des abgeleiteten Typs ist.  
  
 Wenn `Option Strict` ist `On` , muss der Konsumierende Code `CType` für alle einschränkenden Konvertierungen verwenden.  
  
 Das `Narrowing` Schlüsselwort kann in diesem Kontext verwendet werden:  
  
 [Operator Statement](../statements/operator-statement.md)  
  
## <a name="see-also"></a>Weitere Informationen

- [Operator Statement](../statements/operator-statement.md)
- [Widening](widening.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Vorgehensweise: Definieren eines Operators](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType Function](../functions/ctype-function.md)
- [Option Strict-Anweisung](../statements/option-strict-statement.md)
