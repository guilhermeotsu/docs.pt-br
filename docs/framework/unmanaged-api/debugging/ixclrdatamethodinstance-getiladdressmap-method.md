---
title: Método IXCLRDataMethodInstance::GetILAddressMap
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 26c86af2c739532c96ce36c36561f8b8f089dd92
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416315"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="7933c-102">Método IXCLRDataMethodInstance::GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="7933c-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="7933c-103">Obtém a IL às informações de mapeamento de endereço.</span><span class="sxs-lookup"><span data-stu-id="7933c-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7933c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7933c-104">Syntax</span></span>

```
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

### <a name="parameters"></a><span data-ttu-id="7933c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7933c-105">Parameters</span></span>

<span data-ttu-id="7933c-106">`mapLen` [in] O comprimento da matriz de mapas fornecidos.</span><span class="sxs-lookup"><span data-stu-id="7933c-106">`mapLen` [in] The length of the provided maps array.</span></span>

<span data-ttu-id="7933c-107">`mapNeeded` [out] O número de entradas de mapa que o método precisa.</span><span class="sxs-lookup"><span data-stu-id="7933c-107">`mapNeeded` [out] The number of map entries that the method needs.</span></span>

<span data-ttu-id="7933c-108">`maps` [out, size_is(mapLen)] A matriz para armazenar as entradas de mapa.</span><span class="sxs-lookup"><span data-stu-id="7933c-108">`maps` [out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="7933c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7933c-109">Remarks</span></span>

<span data-ttu-id="7933c-110">O método fornecido é parte do `IXCLRDataMethodInstance` de interface e corresponde ao slot de 14 da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="7933c-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7933c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7933c-111">Requirements</span></span>

<span data-ttu-id="7933c-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7933c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7933c-113">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="7933c-113">**Header:** None</span></span>  
<span data-ttu-id="7933c-114">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="7933c-114">**Library:** None</span></span>  
<span data-ttu-id="7933c-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7933c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7933c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7933c-116">See Also</span></span>

- [<span data-ttu-id="7933c-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="7933c-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="7933c-118">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="7933c-118">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)