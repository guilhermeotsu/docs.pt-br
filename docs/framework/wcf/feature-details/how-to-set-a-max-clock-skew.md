---
title: Como definir a precisão máxima do relógio
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 96afa61d32e1ba744c9f3dbbeeb7fb2e55157f4c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141651"
---
# <a name="how-to-set-a-max-clock-skew"></a>Como definir a precisão máxima do relógio
As funções de tempo crítico podem ser degradedas se as configurações de relógio em dois computadores forem diferentes. Para atenuar essa possibilidade, você pode definir a propriedade `MaxClockSkew` como um <xref:System.TimeSpan>. Essa propriedade está disponível em duas classes:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> Para uma conversa segura, as alterações na propriedade `MaxClockSkew` devem ser feitas quando o serviço ou o cliente é inicializado. Para fazer isso, você deve definir a propriedade no <xref:System.ServiceModel.Channels.SecurityBindingElement> retornado pela propriedade <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType>.  
  
 Para alterar a propriedade em uma das associações fornecidas pelo sistema, você deve encontrar o elemento de associação de segurança na coleção de associações e definir a propriedade `MaxClockSkew` como um novo valor. Duas classes derivam do <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Ao recuperar a associação de segurança da coleção, você deve converter em um desses tipos para definir corretamente a propriedade `MaxClockSkew`. O exemplo a seguir usa um <xref:System.ServiceModel.WSHttpBinding>, que usa o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Para obter uma lista que especifica qual tipo de associação de segurança usar em cada associação fornecida pelo sistema, consulte [associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Para criar uma associação personalizada com um novo valor de distorção de relógio no código  
  
> [!WARNING]
> Adicione referências aos seguintes namespaces em seu código: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>e <xref:System.ServiceModel.Security.Tokens>.  
  
1. Crie uma instância de uma classe de <xref:System.ServiceModel.WSHttpBinding> e defina seu modo de segurança como <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.  
  
2. Crie uma nova instância da classe <xref:System.ServiceModel.Channels.BindingElementCollection> chamando o método <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>.  
  
3. Use o método <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> da classe <xref:System.ServiceModel.Channels.BindingElementCollection> para localizar o elemento de associação de segurança.  
  
4. Ao usar o método <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A>, converta para o tipo real. O exemplo a seguir é convertido para o tipo de <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
5. Defina a propriedade <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> no elemento de associação de segurança.  
  
6. Crie um <xref:System.ServiceModel.ServiceHost> com um tipo de serviço e endereço base apropriados.  
  
7. Use o método <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> para adicionar um ponto de extremidade e incluir o <xref:System.ServiceModel.Channels.CustomBinding>.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a>Para definir o MaxClockSkew na configuração  
  
1. Crie uma [\<> CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) na seção do elemento [\<bindings >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) .  
  
2. Crie um elemento de [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) e defina o atributo `name` como um valor apropriado. O exemplo a seguir o define como `MaxClockSkewBinding`.  
  
3. Adicione um elemento Encoding. O exemplo a seguir adiciona um [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4. Adicione um elemento de [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) e defina o atributo `authenticationMode` como uma configuração apropriada. O exemplo a seguir define o atributo como `Kerberos` para especificar que o serviço usa a autenticação do Windows.  
  
5. Adicione um [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) e defina o atributo `maxClockSkew` como um valor na forma de `"##:##:##"`. O exemplo a seguir define como 7 minutos. Opcionalmente, adicione um [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) e defina o atributo `maxClockSkew` como uma configuração apropriada.  
  
6. Adicione um elemento Transport. O exemplo a seguir usa um [\<httpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7. Para uma conversa segura, as configurações de segurança devem ocorrer na inicialização no elemento [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) .  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
