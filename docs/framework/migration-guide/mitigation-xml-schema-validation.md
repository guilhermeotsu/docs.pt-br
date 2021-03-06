---
title: 'Mitigação: validação de esquema XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 99cc1eae08697909d89e5c1e46cd604c7da543bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457745"
---
# <a name="mitigation-xml-schema-validation"></a>Mitigação: validação de esquema XML
No .NET Framework 4.6, a validação de esquema XSD detectará uma violação da restrição exclusiva se uma chave composta for usada e uma chave estiver vazia.  
  
## <a name="impact"></a>Impacto  
 O impacto dessa alteração deve ser mínimo: com base na especificação do esquema, um erro de validação do esquema será esperado se `xsd:unique` for violado usando uma chave composta com uma chave vazia.  
  
## <a name="mitigation"></a>Atenuação  
 Se um erro de validação do esquema for detectado se uma chave composta tiver uma chave vazia, é um recurso configurável:  
  
- Começando com os aplicativos que se destinam ao .NET Framework 4.6, a detecção do erro de validação do esquema é habilitada por padrão; no entanto, é possível recusá-la para que o erro de validação do esquema não seja detectado.  
  
- Em aplicativos que são executados no .NET Framework 4.6, mas se destinam ao .NET Framework 4.5.2 e versões anteriores, um erro de validação do esquema não é detectado por padrão; no entanto, é possível aceitá-lo para que o erro de validação do esquema seja detectado.  
  
 Esse comportamento pode ser configurado usando a classe <xref:System.AppContext> para definir o valor da opção `System.Xml.IgnoreEmptyKeySequences`. Como o valor padrão da opção é `false` (sequências de chaves vazias não são ignoradas), os aplicativos que se destinam ao .NET Framework 4.6 podem recusar o comportamento usando o seguinte código para definir o valor da opção como `true`:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 Para aplicativos que se destinam ao .NET Framework 4.5.2 e às versões anteriores, porque o valor padrão da opção é `true` (sequências de chaves vazias são ignoradas), é possível garantir que uma chave composta com uma chave vazia gere um erro de validação do esquema usando o código a seguir para definir o valor da opção como `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Confira também

- [Compatibilidade de aplicativos](application-compatibility.md)
