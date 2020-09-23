---
title: Der Name des vollständigen Betriebssystems konnte aufgrund eines internen Fehlers nicht abgerufen werden.
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 744d549b9313727af2feb82e45c24b729cae7262
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079086"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Der Name des vollständigen Betriebssystems konnte aufgrund eines internen Fehlers nicht abgerufen werden.

Der Name des vollständigen Betriebssystems konnte aufgrund eines internen Fehlers nicht abgerufen werden. Dies kann dadurch verursacht werden, dass WMI auf dem aktuellen Computer fehlt.  
  
 Beim Aufrufen der `My.Computer.Info.OSFullName` -Eigenschaft ist ein Fehler aufgetreten. Eine mögliche Ursache für diesen Fehler ist, wenn WMI (Windows-Verwaltungsinstrumentation, Windows Management Instrumentation) auf dem aktuellen Computer nicht installiert ist.  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1. Fügen Sie rund um den Aufruf der `Try...Catch` -Eigenschaft einen `My.Computer.Info.OSFullName` -Block hinzu.  
  
2. Weitere Informationen zu WMI und deren Installation finden Sie unter, und suchen Sie nach "Windows-Verwaltungsinstrumentation Core".  
  
## <a name="see-also"></a>Siehe auch

- [My. Computer. info. OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [Behandeln und Auslösen von Ausnahmen in .NET](../../standard/exceptions/index.md)
- [Try... Catch... Abschließend-Anweisung](../language-reference/statements/try-catch-finally-statement.md)
