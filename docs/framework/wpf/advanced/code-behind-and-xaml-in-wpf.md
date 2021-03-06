---
title: Code-Behind e XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 32283d5b81bf92999a97711ded13a8b533ae3028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145339"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Code-behind e XAML no WPF
<a name="introduction"></a> Code-behind é um termo usado para descrever o código unido a objetos definidos com marcação quando uma página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é compilada com marcação. Este tópico descreve os requisitos para code-behind, bem como um mecanismo de código embutido alternativo para o código em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Este tópico contém as seguintes seções:  
  
- [Pré-requisitos](#Prerequisites)  
  
- [Code-Behind e a linguagem XAML](#codebehind_and_the_xaml_language)  
  
- [Code-behind, manipulador de eventos e requisitos de classe parcial no WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Código](#x_Code)  
  
- [Limitações de código embutido](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você leu a [Visão Geral XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) e tem algum conhecimento básico da CLR e programação orientada a objetos.  
  
<a name="codebehind_and_the_xaml_language"></a>
## <a name="code-behind-and-the-xaml-language"></a>Code-Behind e a linguagem XAML  
 A linguagem XAML inclui recursos de nível de linguagem que tornam possível associar arquivos de código com arquivos de marcação, do lado do arquivo de marcação. Especificamente, a linguagem XAML define os recursos de linguagem [Diretiva x:Class](../../../desktop-wpf/xaml-services/xclass-directive.md), [Diretiva x:Subclass](../../../desktop-wpf/xaml-services/xsubclass-directive.md) e [Diretiva x:ClassModifier](../../../desktop-wpf/xaml-services/xclassmodifier-directive.md). O modo exato como o código deve ser produzido e como a marcação e o código devem ser integrados não faz parte do que a linguagem XAML especifica. É deixado para as estruturas, como o WPF, determinarem como integrar o código, como usar a linguagem XAML nos modelos de aplicativo e programação e as ações de build ou outros tipos de suporte que são exigidos.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Code-behind, manipulador de eventos e requisitos de classe parcial no WPF  
  
- A classe parcial deve derivar do tipo que sustenta o elemento raiz.  
  
- Observe que, sob o comportamento padrão das ações de build de compilação de marcação, você pode deixar a derivação em branco na definição de classe parcial no lado da lógica. O resultado compilado assumirá o tipo de suporte da raiz da página para ser a base para a classe parcial, mesmo se não for especificado. No entanto, contar com esse comportamento não é uma prática recomendada.  
  
- Os manipuladores de eventos que você escreve no code-behind devem ser métodos de ocorrência e não podem ser métodos estáticos. Esses métodos devem ser definidos pela classe parcial dentro do namespace CLR identificado por `x:Class`. Você não pode qualificar o nome de um manipulador de eventos para instruir um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para procurar por um manipulador de eventos para fiação de evento em um escopo de classe diferente.  
  
- O manipulador deve corresponder ao delegado para o evento apropriado no sistema de tipo de suporte.  
  
- Para o idioma Microsoft Visual Basic especificamente, `Handles` você pode usar a palavra-chave específica do idioma para associar manipuladores [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]com instâncias e eventos na declaração do manipulador, em vez de anexar manipuladores com atributos em . No entanto, essa técnica tem algumas limitações, uma vez que a palavra-chave `Handles` não pode dar suporte a todos os recursos específicos do sistema de eventos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], como determinados cenários de evento roteado ou eventos anexados. Para obter detalhes, consulte [Visual Basic e manipulação de eventos WPF](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>
## <a name="xcode"></a>x:Code  
 [X:Code](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md) é um elemento de diretiva definido em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Um elemento de diretiva `x:Code` pode conter um código de programação embutido. O código que é definido como embutido pode interagir com o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na mesma página. O exemplo a seguir ilustra o código C# inline. Observe que o código `x:Code` está dentro do elemento e `<CDATA[`que o código deve ser cercado por ... `]]>` para escapar do conteúdo para XML, de modo que um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador (interpretando o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] esquema ou o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] esquema) não tente interpretar o conteúdo literalmente como XML.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>
## <a name="inline-code-limitations"></a>Limitações de código embutido  
 Considere evitar ou limitar o uso de código embutido. Em termos de arquitetura e filosofia de código, manter uma separação entre a marcação e o code-behind mantém as funções de designer e de desenvolvedor muito mais distintas. Em um nível mais técnico, o código que você escreve para o código embutido pode ser complicado de escrever, porque você está sempre escrevendo na classe parcial [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gerada e só pode usar os mapeamentos de namespace de XML padrão. Como você `using` não pode adicionar declarações, você deve qualificar totalmente muitas das chamadas de API que você faz. Os [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mapeamentos padrão incluem a maioria, mas não [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] todos os namespaces CLR que estão presentes nas assembléias; você terá que qualificar totalmente as chamadas para tipos e membros contidos nos outros namespaces da CLR. Você também não poderá definir nada além da classe parcial no código embutido e todas as entidades de código de usuário que você referencia devem existir como um membro ou uma variável na classe parcial gerada. Outros recursos específicos da linguagem de programação, como as macros ou `#ifdef` contra as variáveis globais ou de build, também não estão disponíveis. Para obter mais informações, consulte [x:Code Intrinsic XAML Type](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md) (Tipo intrínseco x:Code (XAML)).  
  
## <a name="see-also"></a>Confira também

- [Visão geral xaml (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Tipo intrínseco x:Code (XAML)](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)
- [Compilando um aplicativo WPF](../app-development/building-a-wpf-application-wpf.md)
- [Sintaxe XAML em detalhes](xaml-syntax-in-detail.md)
