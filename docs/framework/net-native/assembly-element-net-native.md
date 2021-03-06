---
title: <Assembly> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
ms.openlocfilehash: f3cf65b185b1db3289a0dbb785c2b91431951cc2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181075"
---
# <a name="assembly-element-net-native"></a>\<Elemento> de montagem (nativo de.NET)
Aplica a política de reflexão de runtime a todos os tipos em um assembly especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<Assembly Name="assembly_name"
          Activate="policy_setting"  
          Browse="policy_setting"  
          Dynamic="policy_setting"  
          Serialize="policy_setting"  
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Tipo de atributo|Descrição|  
|---------------|--------------------|-----------------|  
|`Name`|Geral|Atributo obrigatório. Especifica o nome simples de um assembly.|  
|`Activate`|Reflexão|Atributo opcional. Controla o acesso de runtime a construtores para habilitar a ativação de instâncias.|  
|`Browse`|Reflexão|Atributo opcional. Controla consultas para obter informações sobre os tipos no assembly ou para enumerá-los, mas não permite qualquer acesso dinâmico no tempo de execução.|  
|`Dynamic`|Reflexão|Atributo opcional. Controla o acesso a todos os tipos de membro ao runtime, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.|  
|`Serialize`|Serialização|Atributo opcional. Controla o acesso ao runtime para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.|  
|`DataContractSerializer`|Serialização|Atributo opcional. Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Serialização|Atributo opcional. Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Serialização|Atributo opcional. Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interoperabilidade|Atributo opcional. Política de controles de marshaling de tipos de referência para o Windows Runtime e COM.|  
|`MarshalDelegate`|Interoperabilidade|Atributo opcional. Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.|  
|`MarshalStructure`|Interoperabilidade|Atributo opcional. Controla a política de estruturas de marshaling para código nativo.|  
  
## <a name="name-attribute"></a>Atributo de nome  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*Assembly_name*|O nome simples do assembly, sem a extensão de arquivo. Este atributo corresponde à propriedade <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> . Por exemplo, o nome de um assembly denominado Extensions.dll é "Extensions".<br /><br /> Você também pode especificar a cadeia de caracteres literal `*Application*` para aplicar a política a todos os assemblies no pacote de aplicativos, sejam os assemblies carregados ou não. `*Application*` nunca aplica-se à política para assemblies .NET Framework.|  
  
## <a name="all-other-attributes"></a>Todos os outros atributos  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*policy_setting*|A configuração a ser aplicada a este tipo de política para todos os tipos no assembly. Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`. Para obter mais informações, consulte [Configurações da política da diretiva de runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Espaço de nome>](namespace-element-net-native.md)|Aplica a política de reflexão de tempo de execução a todos os tipos em um namespace filho.|  
|[\<Tipo>](type-element-net-native.md)|Aplica a política de reflexão a um tipo.|  
|[\<>de Digitação](typeinstantiation-element-net-native.md)|Aplica a política de reflexão a um tipo genérico construído.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de aplicação](application-element-net-native.md)|Serve como um contêiner para os tipos amplos de aplicativos cujos metadados estão disponíveis para reflexão no tempo de execução. O [ \<elemento Application>](application-element-net-native.md) pode ter `<Assembly>` zero, um ou mais elementos.|  
|[\<>da biblioteca](library-element-net-native.md)|Define o assembly que contém tipos e membros de tipo cujos metadados estão disponíveis para reflexão em tempo de execução. O [ \<](library-element-net-native.md) elemento>Biblioteca pode `<Assembly>` ter zero ou um elemento.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `<Assembly>` define a política de runtime para todos os tipos em um assembly. Ele difere do elemento [ \<>biblioteca,](library-element-net-native.md) que especifica uma biblioteca, mas depende de seus elementos infantis para definir a política de reflexão em tempo de execução. O elemento `<Assembly>` aplica-se a todos os tipos em um assembly, a menos que eles sejam substituídos por um elemento filho.  
  
 O exemplo a seguir mostra como é possível aplicar a política em runtime a todos os tipos em assemblies no pacote do aplicativo atribuindo o atributo `Name` a um valor de “*Application\*”. O `<Assembly>` elemento deve ser filho do [ \<elemento Application>.](application-element-net-native.md)  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>  
```  
  
 Os atributos `Activate`, `Browse`, `Dynamic` e `Serialize` são todos opcionais. No entanto, o elemento `<Assembly>` deve conter pelo menos um desses atributos.  
  
## <a name="see-also"></a>Confira também

- [Configurações da política da diretiva de runtime](runtime-directive-policy-settings.md)
- [Referência do arquivo de configuração das diretivas de runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementos da diretiva de runtime](runtime-directive-elements.md)
