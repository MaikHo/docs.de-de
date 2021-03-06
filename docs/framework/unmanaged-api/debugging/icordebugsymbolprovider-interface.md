---
title: ICorDebugSymbolProvider-Schnittstelle
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: 25faad4f4bc67b57c339bc63d1a18ab4d275cd71
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379342"
---
# <a name="icordebugsymbolprovider-interface"></a>ICorDebugSymbolProvider-Schnittstelle
Stellt Methoden bereit, die zum Abrufen von Debugsymbolinformationen verwendet werden können.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetAssemblyImageBytes-Methode](icordebugsymbolprovider-getassemblyimagebytes-method.md)|Liest Daten aus einer zusammengeführten Assembly, wenn eine relative virtuelle Adresse (RVA) in der zusammengeführten Assembly angegeben ist.|  
|[GetAssemblyImageMetadata-Methode](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|Gibt die Metadaten aus einer zusammengeführten Assembly zurück.|  
|[GetCodeRange-Methode](icordebugsymbolprovider-getcoderange-method.md)|Ruft die Startadresse und Größe einer Methode ab, wenn eine relative virtuelle Adresse (RVA) in der Methode angegeben ist.|  
|[GetInstanceFieldSymbols-Methode](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|Ruft die Instanzenfeldsymbole ab, die einer TypeSpec-Signatur entsprechen.|  
|[GetMergedAssemblyRecords-Methode](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|Ruft die Symboldatensätze für alle zusammengeführten Assemblys ab.|  
|[GetMethodLocalSymbols-Methode](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|Ruft die lokalen Symbole einer Methode ab, wenn die relative virtuelle Adresse (RVA) der Methode angegeben ist.|  
|[GetMethodParameterSymbols-Methode](icordebugsymbolprovider-getmethodparametersymbols-method.md)|Ruft die Parametersymbole einer Methode ab, wenn die relative virtuelle Adresse (RVA) der Methode angegeben ist.|  
|[GetMethodProps-Methode](icordebugsymbolprovider-getmethodprops-method.md)|Gibt Informationen zu Methodeneigenschaften wie das Metadatentoken der Methode und Informationen zu den generischen Parametern der Methode zurück, wenn eine relative virtuelle Adresse (RVA) in der Methode angegeben ist.|  
|[GetObjectSize-Methode](icordebugsymbolprovider-getobjectsize-method.md)|Gibt die Objektgröße eines Objekts basierend auf seiner TypeSpec-Signatur zurück.|  
|[GetStaticFieldSymbols-Methode](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|Ruft die statischen Feldsymbole ab, die einer TypeSpec-Signatur entsprechen.|  
|[GetTypeProps-Methode](icordebugsymbolprovider-gettypeprops-method.md)|Gibt anhand einer relativen virtuellen Adresse (RVA) in einem VTable Informationen zu den Eigenschaften eines Typs wie die Anzahl der Signaturen der generischen Parameter zurück.|  
  
## <a name="remarks"></a>Hinweise  
  
> [!NOTE]
> Diese Schnittstelle ist nur in Verbindung mit .NET Native verfügbar. Wenn Sie diese Schnittstelle für ICorDebug-Szenarien außerhalb von .NET Native implementieren, ignoriert die Common Language Runtime diese Schnittstelle.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework Versionen:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- [Debugschnittstellen](debugging-interfaces.md)
- [Debuggen](index.md)
