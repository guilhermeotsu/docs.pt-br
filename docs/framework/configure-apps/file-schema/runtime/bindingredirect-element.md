---
title: Elemento <bindingRedirect>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: d96585b397f75dcb9fac7e7fce93799cc95e7c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154290"
---
# <a name="bindingredirect-element"></a>\<vinculaçãoRedirecionar> Elemento
Redireciona uma versão do assembly para outra.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<montagem>vinculante**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependente>de montagem**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<vinculaçãoRedirecionar>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`oldVersion`|Atributo obrigatório.<br /><br /> Especifica a versão do assembly que foi originalmente solicitada. O formato de um número de versão de montagem é *major.minor.build.revision*. Os valores válidos para cada parte desse número de versão estão entre 0 e 65535.<br /><br /> Você também pode especificar um intervalo de versões no seguinte formato:<br /><br /> *n.n.n.n - n.n.n.n*|  
|`newVersion`|Atributo obrigatório.<br /><br /> Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*<br /><br /> Esse valor pode especificar uma versão anterior do `oldVersion`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Nenhum||  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`assemblyBinding`|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`dependentAssembly`|Encapsula local do assembly e política de associação para cada assembly. Use um elemento dependentAssembly para cada assembly.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Ao criar um aplicativo .NET Framework com base em um assembly com nome forte, o aplicativo usará essa versão do assembly em tempo de execução por padrão, mesmo se uma nova versão estiver disponível. No entanto, você pode configurar o aplicativo para ser executado com base em uma versão mais nova do assembly. Para obter detalhes sobre como o tempo de execução usa esses arquivos para determinar qual versão de montagem usar, consulte [Como o Runtime localiza conjuntos](../../../deployment/how-the-runtime-locates-assemblies.md).  
  
 Você pode redirecionar mais de uma versão do assembly ao incluir vários elementos `bindingRedirect` em um elemento `dependentAssembly`. Você também pode redirecionar de uma versão mais recente para uma versão anterior do assembly.  
  
 O redirecionamento de associação de assembly explícito em um arquivo de configuração do aplicativo requer uma permissão de segurança. Isso se aplica ao redirecionamento de assemblies do .NET Framework e assemblies de terceiros. A permissão é <xref:System.Security.Permissions.SecurityPermissionFlag> concedida definindo a bandeira no <xref:System.Security.Permissions.SecurityPermission>. Para obter mais informações, consulte [A permissão de segurança de redirecionamento de vinculação do conjunto](../../assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como redirecionar uma versão do assembly para outra.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivo de configuração](../index.md)
- [Redirecionando versões de assembly](../../redirect-assembly-versions.md)
