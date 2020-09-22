---
title: <type1><typename> muss <methodname> für die Schnittstelle <interfacename> implementieren.
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 8bf8872277ec901e066a8b950aaf3e61babfcc48
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872107"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1>\<typename> muss \<methodname> für die Schnittstelle \<interfacename> implementieren.

Eine Klasse oder Struktur beansprucht, eine Schnittstelle zu implementieren, implementiert jedoch keine durch die Schnittstelle definierte Prozedur. Jeder Member der Schnittstelle muss implementiert werden.  
  
 **Fehler-ID:** BC30149  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1. Deklarieren Sie eine Prozedur mit dem gleichen Namen und der gleichen Signatur wie in der-Schnittstelle definiert. Stellen Sie sicher, dass Sie mindestens die- `End Function` oder- `End Sub` Anweisung einschließen.  
  
2. Fügen Sie eine- `Implements` Klausel am Ende der- `Function` oder-Anweisung hinzu `Sub` . Beispiel:  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Weitere Informationen

- [Implements-Anweisung](../statements/implements-statement.md)
- [Schnittstellen](../../programming-guide/language-features/interfaces/index.md)
