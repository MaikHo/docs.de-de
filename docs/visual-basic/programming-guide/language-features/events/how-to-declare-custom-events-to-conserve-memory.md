---
title: 'Vorgehensweise: Deklarieren von benutzerdefinierten Ereignissen zum Einsparen von Arbeitsspeicher'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 78934e3e5ae7d5a3f5867c99a9f1db760c65ecbf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075121"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Gewusst wie: Deklarieren von benutzerdefinierten Ereignissen, um Speicherplatz zu sparen (Visual Basic)

Es gibt verschiedene Situationen, in denen es wichtig ist, dass eine Anwendung die Speicherauslastung niedrig hält. Benutzerdefinierte Ereignisse ermöglichen es der Anwendung, Arbeitsspeicher nur für die Ereignisse zu verwenden, die Sie verarbeitet.  
  
 Wenn eine Klasse ein Ereignis deklariert, ordnet der Compiler standardmäßig Speicher für ein Feld zu, um die Ereignis Informationen zu speichern. Wenn eine Klasse über viele nicht verwendete Ereignisse verfügt, nehmen Sie unnötigerweise Speicherplatz in Anspruch.  
  
 Anstatt die Standard Implementierung von Ereignissen zu verwenden, die Visual Basic bereitstellt, können Sie benutzerdefinierte Ereignisse verwenden, um die Speicherauslastung sorgfältiger zu verwalten.  
  
## <a name="example"></a>Beispiel  

 In diesem Beispiel verwendet die-Klasse eine Instanz der- <xref:System.ComponentModel.EventHandlerList> Klasse, die im- `Events` Feld gespeichert ist, um Informationen über die verwendeten Ereignisse zu speichern. Die- <xref:System.ComponentModel.EventHandlerList> Klasse ist eine optimierte Listen Klasse, die Delegaten enthalten soll.  
  
 Alle Ereignisse in der-Klasse verwenden das- `Events` Feld, um nachzuverfolgen, welche Methoden die einzelnen Ereignisse verarbeiten.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>Siehe auch

- <xref:System.ComponentModel.EventHandlerList>
- [Ereignisse](index.md)
- [Vorgehensweise: Deklarieren von benutzerdefinierten Ereignissen, um eine Blockierung zu vermeiden](how-to-declare-custom-events-to-avoid-blocking.md)
