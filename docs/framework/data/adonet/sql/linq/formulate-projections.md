---
title: Formulieren von Projektionen
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: f0bc6dfcff7778ebc7156cbb039e13570c90467b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194400"
---
# <a name="formulate-projections"></a>Formulieren von Projektionen

In den folgenden Beispielen wird gezeigt `select` , wie die-Anweisung in c# und die- `Select` Anweisung in Visual Basic mit anderen Funktionen kombiniert werden können, um Abfrage Projektionen zu bilden.  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird die- `Select` Klausel in Visual Basic (- `select` Klausel in c#) verwendet, um eine Sequenz von Kontaktnamen für zurückzugeben `Customers` .  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird die- `Select` Klausel in Visual Basic ( `select` -Klausel in c#) und *Anonyme Typen* verwendet, um eine Sequenz von Kontaktnamen und Telefonnummern für zurückzugeben `Customers` .  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird die `Select` -Klausel in Visual Basic ( `select` -Klausel in c#) und *Anonyme Typen* verwendet, um eine Sequenz von Namen und Telefonnummern für Mitarbeiter zurückzugeben. Die `FirstName` `LastName` Felder und werden in einem einzelnen Feld ( `Name` ) kombiniert, und das `HomePhone` Feld wird `Phone` in der resultierenden Sequenz in umbenannt.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird die- `Select` Klausel in Visual Basic ( `select` -Klausel in c#) und *Anonyme Typen* verwendet, um eine Sequenz aller `ProductID` s und einen berechneten Wert mit dem Namen zurückzugeben `HalfPrice` . Dieser Wert wird auf den `UnitPrice`, geteilt durch 2, festgelegt.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird die `Select` -Klausel in Visual Basic ( `select` -Klausel in c#) und eine *bedingte-Anweisung* verwendet, um eine Sequenz von Produktname und Produktverfügbarkeit zurückzugeben.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird eine Visual Basic `Select` -Klausel ( `select` -Klausel in c#) und ein *bekannter Typ* (Name) verwendet, um eine Sequenz der Mitarbeiter Namen zurückzugeben.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird `Select` und `Where` in Visual Basic ( `select` und `where` in c#) verwendet, um eine *gefilterte Sequenz* von Kontaktnamen für Kunden in London zurückzugeben.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird eine `Select` -Klausel in Visual Basic ( `select` -Klausel in c#) und *Anonyme Typen* verwendet, um eine *geformte Teilmenge* der Daten zu Kunden zurückzugeben.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Beispiel  

 Im folgenden Beispiel werden geschachtelte Abfragen verwendet, um die folgenden Ergebnisse zurückzugeben:  
  
- Eine Sequenz aller Bestellungen und der entsprechenden `OrderID`s.  
  
- Eine Untersequenz der Elemente in der Bestellung, für die es einen Rabatt gibt.  
  
- Der gesparte Betrag, wenn die Lieferkosten nicht eingeschlossen werden.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Weitere Informationen

- [Abfrage Beispiele](query-examples.md)
