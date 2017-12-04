---
title: "ICorProfilerInfo2::GetObjectGeneration, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetObjectGeneration
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e90139f96638dbb1a183f98e754838ff52424fc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="1bbfd-102">ICorProfilerInfo2::GetObjectGeneration, méthode</span><span class="sxs-lookup"><span data-stu-id="1bbfd-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="1bbfd-103">Obtient le segment du segment de mémoire qui contient l’objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="1bbfd-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bbfd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bbfd-104">Syntax</span></span>  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bbfd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1bbfd-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="1bbfd-106">[in] L’ID de l’objet.</span><span class="sxs-lookup"><span data-stu-id="1bbfd-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="1bbfd-107">[out] Un pointeur vers un [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure qui décrit une plage (autrement dit, un bloc) de mémoire dans la génération qui subit le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1bbfd-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="1bbfd-108">Cette plage contient l’objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="1bbfd-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bbfd-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="1bbfd-109">Remarks</span></span>  
 <span data-ttu-id="1bbfd-110">Le `GetObjectGeneration` méthode peut être appelée à partir de tout rappel de profileur, à condition que le garbage collection n’est pas en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1bbfd-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="1bbfd-111">Autrement dit, il peut être appelé à partir de tout rappel, à l’exception de ceux qui interviennent entre [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) et [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="1bbfd-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bbfd-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1bbfd-112">Requirements</span></span>  
 <span data-ttu-id="1bbfd-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bbfd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bbfd-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1bbfd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1bbfd-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bbfd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bbfd-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bbfd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bbfd-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bbfd-117">See Also</span></span>  
 [<span data-ttu-id="1bbfd-118">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="1bbfd-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="1bbfd-119">ICorProfilerInfo2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="1bbfd-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)