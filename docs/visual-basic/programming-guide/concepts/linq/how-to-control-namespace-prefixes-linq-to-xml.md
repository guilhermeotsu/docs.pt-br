---
title: 'Como: controlar prefixos de namespace (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 5ba415452a8671466c3a4c71a88731e5bd3cda60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348385"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a>Como: Controle prefixos de namespace (Visual Basic) (LINQ to XML)
Este tópico descreve como você pode controlar prefixos de namespace.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 Esse exemplo declara dois namespaces. Ele especifica que o namespace de `http://www.adventure-works.com` tem o prefixo `aw`e que o namespace `www.fourthcoffee.com` tem o prefixo de `fc`.  
  
### <a name="code"></a>Código  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
### <a name="comments"></a>Comentários  
 Este exemplo gera a seguinte saída:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de namespaces (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
