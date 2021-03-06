---
title: Método ICorProfilerInfo::GetAppDomainInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 0407b7057753f7fdee6ea6b1d05144b135b6378a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864083"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a>Método ICorProfilerInfo::GetAppDomainInfo
Aceita uma ID de domínio do aplicativo. Retorna um nome de domínio de aplicativo e a ID do processo que o contém.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `appDomainId`  
 no A ID do domínio do aplicativo.  
  
 `cchName`  
 no O comprimento, em caracteres, do `szName` buffer de retorno.  
  
 `pcchName`  
 fora Um ponteiro para o tamanho total do caractere do nome de domínio do aplicativo.  
  
 `szName`  
 fora Um buffer de caracteres largo fornecido pelo chamador. Quando o método retornar, `szName` conterá o nome de domínio do aplicativo completo ou parcial.  
  
 `pProcessId`  
 fora Um ponteiro para a ID do processo que contém o domínio do aplicativo.  
  
## <a name="remarks"></a>Comentários  
 Depois que esse método retornar, você deverá verificar se o buffer de `szName` era grande o suficiente para conter o nome completo do domínio do aplicativo. Para fazer isso, compare o valor que `pcchName` aponta com o valor do parâmetro `cchName`. Se `pcchName` apontar para um valor maior que `cchName`, aloque um buffer de `szName` maior, atualize `cchName` com o tamanho novo, maior e chame `GetAppDomainInfo` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetAppDomainInfo` com um buffer de `szName` de comprimento zero para obter o tamanho de buffer correto. Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chamar `GetAppDomainInfo` novamente.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Criação de perfil](index.md)
