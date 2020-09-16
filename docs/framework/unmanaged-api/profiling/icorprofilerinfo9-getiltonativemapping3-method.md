---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 14391a0fe046b44aedca1da2bc42c7d962e1a5e7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541277"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="798eb-102">ICorProfilerInfo9:: GetILToNativeMapping3-Methode</span><span class="sxs-lookup"><span data-stu-id="798eb-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="798eb-103">Gibt bei der Startadresse des systemeigenen Codes die nativen to Il-Mapping-Informationen für diese JIT-Version des Codes zurück.</span><span class="sxs-lookup"><span data-stu-id="798eb-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="798eb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="798eb-104">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a><span data-ttu-id="798eb-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="798eb-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="798eb-106">\[in] ein Zeiger auf den Anfang einer nativen Funktion.</span><span class="sxs-lookup"><span data-stu-id="798eb-106">\[in] A pointer to the start of a native function.</span></span>

- `cMap`

  <span data-ttu-id="798eb-107">\[in] die maximale Größe des `map` Arrays.</span><span class="sxs-lookup"><span data-stu-id="798eb-107">\[in] The maximum size of the `map` array.</span></span>

- `pcMap`

  <span data-ttu-id="798eb-108">\[out] die Gesamtzahl der verfügbaren COR_DEBUG_IL_TO_NATIVE_MAP Strukturen.</span><span class="sxs-lookup"><span data-stu-id="798eb-108">\[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

- `map`

  <span data-ttu-id="798eb-109">\[out] ein Array von [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) -Strukturen, von denen jede die Offsets angibt.</span><span class="sxs-lookup"><span data-stu-id="798eb-109">\[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="798eb-110">Nach Rückgabe der `GetILToNativeMapping3`-Methode enthält `map` einige oder alle `COR_DEBUG_IL_TO_NATIVE_MAP`-Strukturen.</span><span class="sxs-lookup"><span data-stu-id="798eb-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="798eb-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="798eb-111">Remarks</span></span>

<span data-ttu-id="798eb-112">Wenn die mehrstufige Kompilierung aktiviert ist, kann eine Methode mehr als einen nativen Code Körper aufweisen.</span><span class="sxs-lookup"><span data-stu-id="798eb-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="798eb-113">[ICorProfilerInfo9:: getnativecodestartadressen](icorprofilerinfo9-getnativecodestartaddresses-method.md) gibt die Start Adressen für alle systemeigenen Code Körper zurück.</span><span class="sxs-lookup"><span data-stu-id="798eb-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="798eb-114">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="798eb-114">Requirements</span></span>

<span data-ttu-id="798eb-115">**Plattformen:** Siehe [unterstützte .net Core-Betriebssysteme](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="798eb-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="798eb-116">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="798eb-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="798eb-117">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="798eb-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="798eb-118">**.NET Framework Versionen:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="798eb-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="798eb-119">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="798eb-119">See also</span></span>

- [<span data-ttu-id="798eb-120">ICorProfilerInfo9-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="798eb-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
