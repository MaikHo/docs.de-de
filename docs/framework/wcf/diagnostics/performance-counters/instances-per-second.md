---
title: Instanzen pro Sekunde
ms.date: 03/30/2017
ms.assetid: 74579397-1058-4278-80cf-2d00854a480f
ms.openlocfilehash: 9b78707f3815fd370d3398f1a7b422ee4bf2d369
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541225"
---
# <a name="instances-per-second"></a>Instanzen pro Sekunde
Indikatorname: Instances Created Per Second.  
  
## <a name="description"></a>BESCHREIBUNG  
 Die Gesamtzahl der in einer Sekunde erstellten Dienstinstanzen.  
  
 Dieser Leistungs Bewert ist vom Typ [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))des Leistungs Zählers, dessen Wert mit der folgenden Formel berechnet wird.  
  
 (N 1 - N 0)/( (D 1 - D 0)/F)
