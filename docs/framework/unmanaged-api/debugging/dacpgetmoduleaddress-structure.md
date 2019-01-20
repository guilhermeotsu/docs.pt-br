---
title: Estrutura DacpGetModuleAddress
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ca9ce04e9a4770d46f88e10785f4dafd044c9212
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416261"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="566a0-102">Estrutura DacpGetModuleAddress</span><span class="sxs-lookup"><span data-stu-id="566a0-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="566a0-103">Define o contêiner para uma solicitação de endereço do módulo.</span><span class="sxs-lookup"><span data-stu-id="566a0-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="566a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="566a0-104">Syntax</span></span>

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="566a0-105">Membros</span><span class="sxs-lookup"><span data-stu-id="566a0-105">Members</span></span>

| <span data-ttu-id="566a0-106">Membro</span><span class="sxs-lookup"><span data-stu-id="566a0-106">Member</span></span>      | <span data-ttu-id="566a0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="566a0-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="566a0-108">O ponteiro para o módulo.</span><span class="sxs-lookup"><span data-stu-id="566a0-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="566a0-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="566a0-109">Methods</span></span>

| <span data-ttu-id="566a0-110">Método</span><span class="sxs-lookup"><span data-stu-id="566a0-110">Method</span></span>                                                                                               | <span data-ttu-id="566a0-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="566a0-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="566a0-112">Solicitação</span><span class="sxs-lookup"><span data-stu-id="566a0-112">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="566a0-113">Executa uma solicitação para preencher a estrutura da estrutura de determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="566a0-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="566a0-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="566a0-114">Remarks</span></span>

<span data-ttu-id="566a0-115">Essa estrutura reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="566a0-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="566a0-116">Para usá-lo, definir a estrutura conforme especificado acima, onde `CLRDATA_ADDRESS` é um inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="566a0-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="566a0-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="566a0-117">Requirements</span></span>
<span data-ttu-id="566a0-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="566a0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="566a0-119">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="566a0-119">**Header:** None</span></span>  
<span data-ttu-id="566a0-120">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="566a0-120">**Library:** None</span></span>  
<span data-ttu-id="566a0-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="566a0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="566a0-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="566a0-122">See Also</span></span>
- [<span data-ttu-id="566a0-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="566a0-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="566a0-124">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="566a0-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)