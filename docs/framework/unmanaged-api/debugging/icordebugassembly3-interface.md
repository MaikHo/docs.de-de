---
title: ICorDebugAssembly3-Schnittstelle
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 67707092c80b0e07aa284336c426aba09ff991af
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894825"
---
# <a name="icordebugassembly3-interface"></a>ICorDebugAssembly3-Schnittstelle
Erweitert logisch die ICorDebugAssembly-Schnittstelle zur Unterstützung der Container Assemblys und der darin enthaltenen Assemblys.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EnumerateContainedAssemblies-Methode](icordebugassembly3-enumeratecontainedassemblies-method.md)|Ruft einen Enumerator für die Assemblys ab, die in dieser Assembly enthalten sind.|  
|[GetContainerAssembly-Methode](icordebugassembly3-getcontainerassembly-method.md)|Gibt die Container-Assembly dieses `ICorDebugAssembly3`-Objekts aus.|  
  
## <a name="remarks"></a>Hinweise  
  
> [!NOTE]
> Diese Schnittstelle ist nur in Verbindung mit .NET Native verfügbar. Bei dem Versuch, `QueryInterface` aufzurufen, um einen Schnittstellenzeiger abzurufen, wird für ICorDebug-Szenarien außerhalb von .NET Native `E_NOINTERFACE` zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework Versionen:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen

- [Debugschnittstellen](debugging-interfaces.md)
- [Debuggen](index.md)
