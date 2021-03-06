---
title: IMetaDataEmit2::SetGenericParamProps-Methode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: 8feba8e67f3a90dd48fd957065a9c166c204b87c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492732"
---
# <a name="imetadataemit2setgenericparamprops-method"></a>IMetaDataEmit2::SetGenericParamProps-Methode
Legt Eigenschaftswerte für die generische Parameterdefinition fest, auf die durch das angegebene Token verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a>Parameter  
 `gp`  
 in Das Token für die generische Parameterdefinition, für die Werte festgelegt werden sollen.  
  
 `dwParamFlags`  
 in Ein Wert der [CorGenericParamAttr](corgenericparamattr-enumeration.md) -Enumeration, der den Typ für den generischen Parameter beschreibt.  
  
 `szName`  
 [in] Optional. Der Name des Parameters, für den Werte festgelegt werden sollen.  
  
 `reserved`  
 [in] Für zukünftige Erweiterungen reserviert.  
  
 `rtkConstraints`  
 [in] Optional. Ein mit Null endendes Array von Typeinschränkungen. Array Elemente müssen ein- `mdTypeDef` ,- `mdTypeRef` oder- `mdTypeSpec` Metadatentoken sein.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** Cor. h  
  
 **Bibliothek:** Wird als Ressource in Mscoree. dll verwendet.  
  
 **.NET Framework Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen:

- [IMetaDataEmit2-Schnittstelle](imetadataemit2-interface.md)
- [IMetaDataEmit-Schnittstelle](imetadataemit-interface.md)
