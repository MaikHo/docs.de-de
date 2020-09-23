---
title: Optionale Parameter
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
ms.openlocfilehash: 73a51ab65a8ea4c38b6fd6737279fb19fb1cfe73
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071858"
---
# <a name="optional-parameters-visual-basic"></a>Optionale Parameter (Visual Basic)

Sie können angeben, dass ein Prozedurparameter optional ist und in Aufrufen der Prozedur kein Argument dafür bereitgestellt werden muss. *Optionale Parameter* werden durch das- `Optional` Schlüsselwort in der Prozedur Definition angegeben. Es gelten die folgenden Regeln:  
  
- Für jeden optionalen Parameter in der Prozedurdefinition muss ein Standardwert angegeben werden.  
  
- Der Standardwert für einen optionalen Parameter muss ein konstanter Ausdruck sein.  
  
- Jeder Parameter, der in der Prozedurdefinition auf einen optionalen Parameter folgt, muss ebenfalls optional sein.  
  
 Die folgende Syntax zeigt eine Prozedurdeklaration mit einem optionalen Parameter:  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a>Aufrufprozeduren mit optionalen Parametern  

 Wenn eine Prozedur mit einem optionalen Parameter aufgerufen wird, können Sie entscheiden, ob das Argument bereitgestellt werden soll. Wird das Argument nicht bereitgestellt, verwendet die Prozedur den für diesen Parameter deklarierten Standardwert.  
  
 Wenn Sie in der Argumentliste eines oder mehrere optionale Argumente auslassen, werden deren Positionen durch aufeinanderfolgende Kommas markiert. Im folgenden Beispielaufruf werden das erste und das vierte Argument bereitgestellt, das zweite und dritte jedoch nicht:  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 Im folgenden Beispiel wird die `MsgBox`-Funktion mehrmals aufgerufen. `MsgBox` besitzt einen erforderlichen Parameter und zwei optionale Parameter.  
  
 Beim ersten Aufruf von `MsgBox` werden alle drei Argumente in der Reihenfolge angegeben, in der sie von `MsgBox` definiert werden. Beim zweiten Aufruf wird nur das erforderliche Argument angegeben. Beim dritten und vierten Aufruf werden das erste und dritte Argument angegeben. Im dritten Aufruf geschieht dies über die Position, im vierten Aufruf über den Namen.  
  
 [!code-vb[VbVbcnProcedures#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#47)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a>Bestimmen, ob ein optionales Argument vorhanden ist  

 Prozeduren können zur Laufzeit nicht feststellen, ob ein bestimmtes Argument ausgelassen oder der Standardwert durch den Aufrufcode explizit bereitgestellt wurde. Wenn diese Unterscheidung wichtig ist, sollten Sie einen unwahrscheinlichen Standardwert festlegen. Im folgenden Verfahren wird der optionale-Parameter definiert `office` und der Standardwert überprüft, `QJZ` um festzustellen, ob er im-Befehl ausgelassen wurde:  
  
 [!code-vb[VbVbcnProcedures#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#46)]  
  
 Wenn es sich beim optionalen Parameter um einen Verweistyp wie `String` handelt, kann `Nothing` als Standardwert verwendet werden, sofern dieser kein zu erwartender Wert für das Argument ist.  
  
## <a name="optional-parameters-and-overloading"></a>Optionale Parameter und Überladen  

 Eine weitere Möglichkeit, eine Prozedur mit optionalen Parametern zu definieren, ist das Überladen. Wenn ein optionaler Parameter vorhanden ist, können Sie zwei überladene Versionen der Prozedur definieren, eine mit und eine ohne Parameter. Mit steigender Anzahl an optionalen Parametern wird dieses Konzept jedoch komplizierter. Allerdings hat es den Vorteil, dass Sie immer genau wissen, ob das aufrufende Programm jedes optionale Argument bereitgestellt hat.  
  
## <a name="see-also"></a>Siehe auch

- [Vorgehensweisen](./index.md)
- [Parameter und Argumente von Prozeduren](./procedure-parameters-and-arguments.md)
- [Übergeben von Argumenten als Wert und als Verweis](./passing-arguments-by-value-and-by-reference.md)
- [Übergeben von Argumenten nach Position und Name](./passing-arguments-by-position-and-by-name.md)
- [Parameterarrays](./parameter-arrays.md)
- [Prozedurüberladung](./procedure-overloading.md)
- [Optional](../../../language-reference/modifiers/optional.md)
- [ParamArray](../../../language-reference/modifiers/paramarray.md)
