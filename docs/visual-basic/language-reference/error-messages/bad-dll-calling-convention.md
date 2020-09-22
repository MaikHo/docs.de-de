---
title: Fehlerhafte DLL-Aufrufkonvention
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: 0481bd5e4dfe7a24dff454d0754b519509fa967f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875733"
---
# <a name="bad-dll-calling-convention"></a>Fehlerhafte DLL-Aufrufkonvention

Argumente, die an eine Dynamic Link Library (dll) übergeben werden, müssen exakt mit den von der Routine erwarteten übereinstimmen. Aufruf Konventionen behandeln die Anzahl, den Typ und die Reihenfolge der Argumente. Das Programm ruft möglicherweise eine Routine in einer DLL auf, der der falsche Typ oder die falsche Anzahl von Argumenten übergeben wird.  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1. Stellen Sie sicher, dass alle Argument Typen mit denen übereinstimmen, die in der Deklaration der Routine, die Sie aufrufen, angegeben sind.  
  
2. Stellen Sie sicher, dass Sie die gleiche Anzahl von Argumenten übergeben, die in der Deklaration der Routine angegeben sind, die Sie aufrufen.  
  
3. Wenn die DLL-Routine Argumente als Wert erwartet, stellen Sie sicher, `ByVal` dass für diese Argumente in der Deklaration der Routine angegeben wird.  
  
## <a name="see-also"></a>Weitere Informationen

- [Fehlertypen](../../programming-guide/language-features/error-types.md)
- [Call-Anweisung](../statements/call-statement.md)
- [Declare Statement](../statements/declare-statement.md)
