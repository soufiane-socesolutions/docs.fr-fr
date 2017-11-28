---
title: "GetDemultiplexedStub (fonction) (référence des API non managées)"
description: "La fonction GetDemultiplexedStub crée un récepteur de redirecteur d’objet pour aider un client lors de la réception des appels asynchrones de la gestion de Windows."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetDemultiplexedStub
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetDemultiplexedStub
helpviewer_keywords: GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a81101acbf65546ea068e6b5a0e8d9045aaadc71
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="7f5ad-103">GetDemultiplexedStub (fonction)</span><span class="sxs-lookup"><span data-stu-id="7f5ad-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="7f5ad-104">Crée un récepteur de redirecteur d’objet pour aider un client lors de la réception des appels asynchrones de la gestion de Windows.</span><span class="sxs-lookup"><span data-stu-id="7f5ad-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7f5ad-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f5ad-105">Syntax</span></span>  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="7f5ad-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7f5ad-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="7f5ad-107">[in] Un pointeur à l’implémentation du client dans le processus de [IWbemObjectSink](https://msdn.microsoft.com/en-us/library/aa391787(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="7f5ad-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](https://msdn.microsoft.com/en-us/library/aa391787(v=vs.85).aspx).</span></span>

`isLocal`  
<span data-ttu-id="7f5ad-108">[in] Un indicateur qui indique si l’événement est locale (`true`) ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="7f5ad-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="7f5ad-109">[out] Un récepteur de redirecteur objet pour aider un client lors de la réception des appels asynchrones de la gestion de Windows.</span><span class="sxs-lookup"><span data-stu-id="7f5ad-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="7f5ad-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7f5ad-110">Return value</span></span>

<span data-ttu-id="7f5ad-111">Si la fonction réussit, la valeur de retour est `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="7f5ad-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="7f5ad-112">Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro.</span><span class="sxs-lookup"><span data-stu-id="7f5ad-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="7f5ad-113">Pour obtenir des informations d’erreur plus complètes, appelez le [GetErrorInfo](geterrorinfo.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="7f5ad-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="7f5ad-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7f5ad-114">Requirements</span></span>  
 <span data-ttu-id="7f5ad-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f5ad-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f5ad-116">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7f5ad-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7f5ad-117">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7f5ad-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f5ad-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f5ad-118">See also</span></span>  
[<span data-ttu-id="7f5ad-119">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="7f5ad-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)