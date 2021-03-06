---
title: ICorProfilerInfo::GetClassIDInfo-Methode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
ms.openlocfilehash: 4fbee938ae86b338f2beb0b48feeee46f144a4a0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498491"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a>ICorProfilerInfo::GetClassIDInfo-Methode
Ruft das übergeordnete Modul und das Metadatentoken für die angegebene Klasse ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a>Parameter  
 `classId`  
 in Die ID der Klasse, für die die Informationen zu erhalten sind.  
  
 `pModuleId`  
 vorgenommen Ein Zeiger auf die ID des übergeordneten Moduls der-Klasse.  
  
 `pTypeDefToken`  
 vorgenommen Ein Zeiger auf das Metadatentoken für die-Klasse.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Profiler-Code kann [ICorProfilerInfo:: GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) aufrufen, um eine Metadatenschnittstelle für ein bestimmtes Modul zu erhalten. Das Metadatentoken, das an den Speicherort zurückgegeben wird, auf den durch `pTypeDefToken` verwiesen wird, kann anschließend für den Zugriff auf die Metadaten für die Klasse verwendet werden.  
  
 Verwenden Sie [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md), um weitere Informationen zu generischen Typen zu erhalten.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen:

- [ICorProfilerInfo-Schnittstelle](icorprofilerinfo-interface.md)
