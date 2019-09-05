---
title: ICorProfilerInfo10::ResumeRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.ResumeRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: cf599e5ded73b09d54c98dcd99f51b30c6a4ba82
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661199"
---
# <a name="icorprofilerinfo10resumeruntime-method"></a><span data-ttu-id="51cb2-102">Método ICorProfilerInfo10:: ResumeRuntime</span><span class="sxs-lookup"><span data-stu-id="51cb2-102">ICorProfilerInfo10::ResumeRuntime Method</span></span>

<span data-ttu-id="51cb2-103">Retoma o tempo de execução sem executar um GC.</span><span class="sxs-lookup"><span data-stu-id="51cb2-103">Resumes the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="51cb2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51cb2-104">Syntax</span></span>

```cpp
HRESULT ResumeRuntime();
```

## <a name="requirements"></a><span data-ttu-id="51cb2-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51cb2-105">Requirements</span></span>

<span data-ttu-id="51cb2-106">**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="51cb2-106">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="51cb2-107">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="51cb2-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="51cb2-108">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51cb2-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="51cb2-109">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51cb2-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="51cb2-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51cb2-110">See also</span></span>

- [<span data-ttu-id="51cb2-111">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="51cb2-111">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)