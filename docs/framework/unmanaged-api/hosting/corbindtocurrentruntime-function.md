---
title: Função CorBindToCurrentRuntime
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
ms.openlocfilehash: 348ca9d157a668dcd180076475f1fe9861197174
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616652"
---
# <a name="corbindtocurrentruntime-function"></a>Função CorBindToCurrentRuntime
Carrega o Common Language Runtime (CLR) em um processo usando as informações de versão armazenadas em um arquivo XML. O formato do arquivo XML é modelado após o arquivo de configuração de aplicativo padrão. Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../configure-apps/file-schema/index.md).  
  
 Essa função foi preterida no .NET Framework 4. Consulte [carregando o Common Language Runtime em um processo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pwszFileName`  
 no O nome de um arquivo de configuração de aplicativo que especifica a versão do CLR a ser carregada. Se o nome do arquivo não for totalmente qualificado, supõe-se que esteja no mesmo diretório que o executável que faz a chamada.  
  
 A versão do tempo de execução a ser carregada é descrita pelo atributo Version no elemento [ \< requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) do arquivo de configuração.  
  
 Se nenhuma versão for especificada ou se o `<requiredRuntime>` elemento não puder ser encontrado, a versão mais recente do CLR instalada no computador será carregada.  
  
 `rclsid`  
 no O `CLSID` da coclass que implementa a interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [ICLRRuntimeHost](iclrruntimehost-interface.md) . Os valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 no O `IID` da interface que você está solicitando. Os valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 fora O ponteiro de interface retornado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** MSCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Função CorBindToRuntime](corbindtoruntime-function.md)
- [Função CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md)
- [Função CorBindToRuntimeEx](corbindtoruntimeex-function.md)
- [Função CorBindToRuntimeHost](corbindtoruntimehost-function.md)
- [Interface ICorRuntimeHost](icorruntimehost-interface.md)
- [Funções de hospedagem CLR reprovadas](deprecated-clr-hosting-functions.md)
