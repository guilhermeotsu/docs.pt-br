---
title: Método ICorProfilerCallback::RemotingServerReceivingMessage
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 6e045a99de9ad30516fd12a7b490e26c860bde7e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866007"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a>Método ICorProfilerCallback::RemotingServerReceivingMessage
Notifica o criador de perfil de que o processo recebeu uma invocação de método remoto ou uma solicitação de ativação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pCookie`  
 no Um valor que corresponderá com o valor fornecido em [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) sob estas condições:  
  
- Os cookies de GUID de comunicação remota estão ativos.  
  
- O canal tem sucesso ao transmitir a mensagem.  
  
- Os cookies de GUID estão ativos no processo do lado do cliente.  
  
 Isso permite um emparelhamento fácil de chamadas remotas e a criação de uma pilha de chamadas lógica.  
  
 `fIsAsync`  
 no Um valor que será `true` se a chamada for assíncrona; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Se a solicitação de mensagem for assíncrona, a solicitação poderá ser atendida por qualquer thread arbitrário.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
