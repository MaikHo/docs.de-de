---
title: Widening and Narrowing Conversions
ms.date: 07/20/2015
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
ms.openlocfilehash: c0e10f5593ce5c81002233516444e415571541f3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058533"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Erweiternde und eingrenzende Konvertierungen (Visual Basic)

Ein wichtiger Aspekt bei einer Typkonvertierung ist, ob das Ergebnis der Konvertierung innerhalb des Bereichs des Ziel Datentyps liegt.  
  
 Eine *erweiternde Konvertierung* ändert einen Wert in einen Datentyp, der einen möglichen Wert der ursprünglichen Daten zulässt.  Erweiternde Konvertierungen behalten den Quellwert bei, können jedoch seine Darstellung ändern. Dies tritt auf, wenn Sie von einem ganzzahligen Typ in `Decimal` oder von `Char` in konvertieren `String` .  
  
 Eine *einschränkende* Konvertierung ändert einen Wert in einen Datentyp, der möglicherweise nicht in der Lage ist, alle möglichen Werte zu speichern. Beispielsweise wird ein Bruchteil-Wert gerundet, wenn er in einen ganzzahligen Typ konvertiert wird, und ein numerischer Typ, der in konvertiert wird, `Boolean` wird auf `True` oder reduziert `False` .  
  
## <a name="widening-conversions"></a>Erweiterungskonvertierungen  

 In der folgenden Tabelle sind die standarderweiternde Konvertierungen aufgeführt.  
  
|Datentyp|Wird zu den Datentypen <sup>1</sup> erweitert.|  
|---|---|  
|[SByte](../../../language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Short](../../../language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Integer](../../../language-reference/data-types/integer-data-type.md)|`Integer`, `Long` , `Decimal` , `Single` , `Double` <sup>2</sup>|  
|[UInteger](../../../language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long` , `ULong` , `Decimal` , `Single` , `Double` <sup>2</sup>|  
|[Long](../../../language-reference/data-types/long-data-type.md)|`Long`, `Decimal` , `Single` , `Double` <sup>2</sup>|  
|[ULong](../../../language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal` , `Single` , `Double` <sup>2</sup>|  
|[Decimal](../../../language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single` , `Double` <sup>2</sup>|  
|[Single](../../../language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../language-reference/data-types/double-data-type.md)|`Double`|  
|Beliebiger Enumerationstyp[(](../../../language-reference/statements/enum-statement.md)Enumeration)|Der zugrunde liegende ganzzahlige Typ und alle Typen, auf die sich der zugrunde liegende Typ ausdehnt.|  
|[Char](../../../language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char`-Array|`Char` Array `String`|  
|Beliebiger Typ|[Object](../../../language-reference/data-types/object-data-type.md)|  
|Abgeleiteter Typ|Jeder Basistyp, von dem er abgeleitet ist <sup>3</sup>.|  
|Beliebiger Typ|Jede Schnittstelle, die Sie implementiert.|  
|[Schweigen](../../../language-reference/nothing.md)|Jeder Datentyp oder Objekttyp.|  
  
 <sup>1</sup> definitionsgemäß wird jeder Datentyp zu sich selbst erweitert.  
  
 <sup>2</sup> Konvertierungen von `Integer` , `UInteger` , `Long` , `ULong` , oder `Decimal` zu oder können zu einem `Single` `Double` Genauigkeits Verlust führen, jedoch nie in der Größe. In diesem Sinne entstehen keine Informationsverluste.  
  
 <sup>3</sup> es mag überraschend erscheinen, dass eine Konvertierung von einem abgeleiteten Typ in einen seiner Basis Typen erweitert wird. Die Begründung ist, dass der abgeleitete Typ alle Member des Basistyps enthält, sodass er als Instanz des Basistyps qualifiziert ist. In umgekehrter Richtung enthält der Basistyp keine neuen Member, die vom abgeleiteten Typ definiert werden.  
  
 Erweiternde Konvertierungen sind immer zur Laufzeit erfolgreich und verursachen niemals Datenverluste. Sie können Sie immer implizit ausführen, unabhängig davon, ob die [Option Strict-Anweisung](../../../language-reference/statements/option-strict-statement.md) den Schalter für die Typüberprüfung auf oder festgelegt hat `On` `Off` .  
  
## <a name="narrowing-conversions"></a>Eingrenzungskonvertierungen  

 Die standardeinschränkenden Konvertierungen umfassen Folgendes:  
  
- Die umgekehrten Richtungen der erweiternden Konvertierungen in der vorangehenden Tabelle (mit der Ausnahme, dass jeder Typ zu sich selbst umvergrößert wird)  
  
- Konvertierungen in beide Richtungen zwischen [booleschen](../../../language-reference/data-types/boolean-data-type.md) Werten und beliebigen numerischen Typen  
  
- Konvertierungen eines beliebigen numerischen Typs in einen beliebigen enumerierten Typ ( `Enum` )  
  
- Konvertierungen in beide Richtungen zwischen [Zeichen](../../../language-reference/data-types/string-data-type.md) folgen und numerischen Typen, `Boolean` oder [Datum](../../../language-reference/data-types/date-data-type.md)  
  
- Konvertierungen von einem Datentyp oder Objekttyp in einen von ihm abgeleiteten Typ  
  
 Einschränkende Konvertierungen sind zur Laufzeit nicht immer erfolgreich und können fehlschlagen oder Datenverluste verursachen. Ein Fehler tritt auf, wenn der Ziel Datentyp den konvertierten Wert nicht empfangen kann. Beispielsweise kann eine numerische Konvertierung zu einem Überlauf führen. Der Compiler gestattet Ihnen nicht, einschränkende Konvertierungen implizit auszuführen, es sei denn, die [Option Strict-Anweisung](../../../language-reference/statements/option-strict-statement.md) legt den Schalter für die Typüberprüfung auf fest `Off` .  
  
> [!NOTE]
> Der einschränkende Konvertierungs Fehler wird für Konvertierungen von Elementen in einer Auflistung `For Each…Next` in die Schleifen Steuerungs Variable unterdrückt. Weitere Informationen und Beispiele finden Sie im Abschnitt "einschränkende Konvertierungen" unter [for each... Next-Anweisung](../../../language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Verwendung von einschränkenden Konvertierungen  

 Sie verwenden eine einschränkende Konvertierung, wenn Sie wissen, dass der Quellwert ohne Fehler oder Datenverlust in den Ziel Datentyp konvertiert werden kann. Wenn Sie z. b. über ein verfügen, `String` das entweder "true" oder "false" enthält, können Sie das- `CBool` Schlüsselwort verwenden, um es in zu konvertieren `Boolean` .  
  
## <a name="exceptions-during-conversion"></a>Ausnahmen während der Konvertierung  

 Da erweiternde Konvertierungen immer erfolgreich sind, lösen Sie keine Ausnahmen aus. Einschränkende Konvertierungen, wenn Sie fehlschlagen, lösen in der Regel die folgenden Ausnahmen aus:  
  
- <xref:System.InvalidCastException> –, wenn zwischen den beiden Typen keine Konvertierung definiert ist.  
  
- <xref:System.OverflowException> – (nur ganzzahlige Typen), wenn der konvertierte Wert für den Zieltyp zu groß ist  
  
 Wenn eine Klasse oder Struktur eine [CType-Funktion](../../../language-reference/functions/ctype-function.md) definiert, die als Konvertierungs Operator für diese Klasse oder Struktur fungieren soll, `CType` kann eine beliebige Ausnahme auslösen, die Sie als geeignet erachtet. Darüber hinaus `CType` können Visual Basic Funktionen oder .NET Framework Methoden aufgerufen werden, die wiederum eine Vielzahl von Ausnahmen auslösen können.  
  
## <a name="changes-during-reference-type-conversions"></a>Änderungen bei Verweistyp Konvertierungen  

 Bei einer Konvertierung von einem *Verweistyp* wird nur der Zeiger auf den Wert kopiert. Der Wert selbst wird weder kopiert noch auf irgendeine Weise geändert. Das einzige, was geändert werden kann, ist der Datentyp der Variablen, die den Zeiger enthält. Im folgenden Beispiel wird der Datentyp von der abgeleiteten Klasse in seine Basisklasse konvertiert, aber das Objekt, auf das beide Variablen nun zeigen, ist unverändert.  
  
```vb  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>Siehe auch

- [Datentypen](index.md)
- [Typkonvertierung in Visual Basic](type-conversions.md)
- [Implizite und explizite Konvertierungen](implicit-and-explicit-conversions.md)
- [Konvertierungen zwischen Zeichenfolgen und anderen Typen](conversions-between-strings-and-other-types.md)
- [Gewusst wie: Konvertieren eines Objekts in einen anderen Typ in Visual Basic](how-to-convert-an-object-to-another-type.md)
- [Arraykonvertierungen](array-conversions.md)
- [Datentypen](../../../language-reference/data-types/index.md)
- [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)
