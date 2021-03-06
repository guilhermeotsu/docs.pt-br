---
title: Criar um estilo para um controle
description: Saiba como criar e referenciar um estilo de controle no Windows Presentation Foundation e no .NET Core.
author: thraka
ms.author: adegeo
ms.date: 09/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2956dbf93a1d34feca31d3ab10536f5089010189
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "82071265"
---
# <a name="create-a-style-for-a-control-in-wpf"></a>Criar um estilo para um controle no WPF

Com o Windows Presentation Foundation (WPF), você pode personalizar a aparência de um controle existente com seu próprio estilo reutilizável. Os estilos podem ser aplicados globalmente ao seu aplicativo, janelas e páginas ou diretamente aos controles.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>Criar um estilo

Você pode considerar um <xref:System.Windows.Style> como uma maneira conveniente de aplicar um conjunto de valores de propriedade a um ou mais elementos. Você pode usar um estilo em qualquer elemento que derive de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> como um <xref:System.Windows.Window> ou um <xref:System.Windows.Controls.Button>.

A maneira mais comum de declarar um estilo é como um recurso na `Resources` seção em um arquivo XAML. Como os estilos são recursos, eles obedecem as mesmas regras de escopo que se aplicam a todos os recursos. Coloque simplesmente, em que você declara um estilo que afeta o local em que o estilo pode ser aplicado. Por exemplo, se você declarar o estilo no elemento raiz do arquivo XAML de definição de aplicativo, o estilo poderá ser usado em qualquer lugar em seu aplicativo.

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

Se você declarar o estilo em um dos arquivos XAML do aplicativo, o estilo poderá ser usado somente nesse arquivo XAML. Para obter mais informações sobre regras de escopo para recursos, consulte [Recursos de XAML](xaml-resources-define.md).

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

Um estilo é composto de `<Setter>` elementos filho que definem propriedades nos elementos aos quais o estilo é aplicado. No exemplo acima, observe que o estilo está definido para ser aplicado aos `TextBlock` tipos por meio `TargetType` do atributo. O <xref:System.Windows.Controls.Control.FontSize%2A> estilo definirá `15` como e <xref:System.Windows.Controls.Control.FontWeight%2A> como. `ExtraBold` `<Setter>` Adicione a cada propriedade o estilo é alterado.

## <a name="apply-a-style-implicitly"></a>Aplicar um estilo implicitamente

Uma <xref:System.Windows.Style> é uma maneira conveniente de aplicar um conjunto de valores de propriedade a mais de um elemento. Por exemplo, considere os seguintes <xref:System.Windows.Controls.TextBlock> elementos e sua aparência padrão em uma janela.

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![Captura de tela de exemplo de estilo](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

Você pode alterar a aparência padrão definindo propriedades, como <xref:System.Windows.Controls.Control.FontSize%2A> e <xref:System.Windows.Controls.Control.FontFamily%2A>, em cada <xref:System.Windows.Controls.TextBlock> elemento diretamente. No entanto, se você <xref:System.Windows.Controls.TextBlock> quiser que seus elementos compartilhem algumas propriedades, poderá <xref:System.Windows.Style> criar um `Resources` na seção do seu arquivo XAML, como mostrado aqui.

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

Quando você define o <xref:System.Windows.Style.TargetType%2A> de seu estilo como o <xref:System.Windows.Controls.TextBlock> tipo e omite o `x:Key` atributo, o estilo é aplicado a todos os <xref:System.Windows.Controls.TextBlock> elementos com escopo para o estilo, que geralmente é o próprio arquivo XAML.

Agora, <xref:System.Windows.Controls.TextBlock> os elementos são exibidos da seguinte maneira.

![Captura de tela de exemplo de estilo](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>Aplicar um estilo explicitamente

Se você adicionar um `x:Key` atributo com valor ao estilo, o estilo não será mais implicitamente aplicado a todos os elementos de <xref:System.Windows.Style.TargetType%2A>. Somente os elementos que referenciam explicitamente o estilo terão o estilo aplicado a eles.

Aqui está o estilo da seção anterior, mas declarado com o `x:Key` atributo.

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

Para aplicar o estilo, defina a <xref:System.Windows.FrameworkElement.Style%2A> Propriedade no elemento como o `x:Key` valor, usando uma extensão de [marcação StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md), como mostrado aqui.

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

Observe que o primeiro <xref:System.Windows.Controls.TextBlock> elemento tem o estilo aplicado a ele, enquanto o segundo elemento TextBlock permanece inalterado. O estilo implícito da seção anterior foi alterado para um estilo que declarou o `x:Key` atributo, ou seja, o único elemento afetado pelo estilo é aquele que referenciou o estilo diretamente.

![Captura de tela de exemplo de estilo](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "criar-a-estilo-explícito-TextBlock")

Quando um estilo é aplicado, explicitamente ou implicitamente, ele fica lacrado e não pode ser alterado. Se você quiser alterar um estilo que foi aplicado, crie um novo estilo para substituir o existente. Para obter mais informações, consulte a propriedade <xref:System.Windows.Style.IsSealed%2A>.

É possível criar um objeto que escolhe um estilo para aplicar com base na lógica personalizada. Para obter um exemplo, consulte o exemplo fornecido para <xref:System.Windows.Controls.StyleSelector> a classe.

## <a name="apply-a-style-programmatically"></a>Aplicar um estilo programaticamente

Para atribuir um estilo nomeado a um elemento programaticamente, obtenha o estilo da coleção de recursos e atribua-o à <xref:System.Windows.FrameworkElement.Style%2A> Propriedade do elemento. Os itens em uma coleção de recursos são do <xref:System.Object>tipo. Portanto, você deve converter o estilo recuperado em um <xref:System.Windows.Style?displayProperty=fullName> antes de atribuí-lo à `Style` propriedade. Por exemplo, o código a seguir define o estilo de `TextBlock` um `textblock1` nomeado para o estilo `TitleText`definido.

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>Estender um estilo

Talvez você queira que os <xref:System.Windows.Controls.TextBlock> dois elementos compartilhem alguns valores de propriedade, como <xref:System.Windows.Controls.Control.FontFamily%2A> o e o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>centralizado. Mas você também deseja que o texto **minhas imagens** tenha algumas propriedades adicionais. Você pode fazer isso criando um novo estilo com base no primeiro estilo, como mostrado aqui.

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

Esse `TextBlock` estilo agora está centralizado, usa `Comic Sans MS` uma fonte com um tamanho `26`de e a cor de primeiro plano definida <xref:System.Windows.Media.LinearGradientBrush> como a mostrada no exemplo. Observe que ele substitui o <xref:System.Windows.Controls.Control.FontSize%2A> valor do estilo base. Se houver mais de um <xref:System.Windows.Setter> apontando para a mesma propriedade em um <xref:System.Windows.Style>, o `Setter` que é declarado por último tem precedência.

O exemplo a seguir mostra <xref:System.Windows.Controls.TextBlock> como os elementos agora são:

![Bloco de Textcom estilo](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

Esse `TitleText` estilo estende o estilo que foi criado para o <xref:System.Windows.Controls.TextBlock> tipo, referenciado com `BasedOn="{StaticResource {x:Type TextBlock}}"`. Você também pode estender um estilo que tenha um `x:Key` usando o `x:Key` do estilo. Por exemplo, se houver um estilo chamado `Header1` e você quisesse estender esse estilo, você usaria. `BasedOn="{StaticResource Header1}"`

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Relação da propriedade TargetType e do atributo x:Key

Como mostrado anteriormente, definir a <xref:System.Windows.Style.TargetType%2A> Propriedade como `TextBlock` sem atribuir o estilo a `x:Key` faz com que o estilo seja aplicado a todos os <xref:System.Windows.Controls.TextBlock> elementos. Nesse caso, o `x:Key` é definido implicitamente como `{x:Type TextBlock}`. Isso significa que, se você definir explicitamente `x:Key` o valor para qualquer coisa `{x:Type TextBlock}`diferente de <xref:System.Windows.Style> , o não será `TextBlock` aplicado a todos os elementos automaticamente. Em vez disso, você deve aplicar o estilo (usando `x:Key` o valor) explicitamente `TextBlock` aos elementos. Se o seu estilo estiver na seção de recursos e você não definir `TargetType` a propriedade no seu estilo, você deverá definir o `x:Key` atributo.

Além de fornecer um valor padrão para o `x:Key`, a `TargetType` propriedade especifica o tipo ao qual as propriedades setter se aplicam. Se você não especificar um `TargetType`, deverá qualificar as propriedades em seus <xref:System.Windows.Setter> objetos com um nome de classe usando a sintaxe `Property="ClassName.Property"`. Por exemplo, em vez de `Property="FontSize"`configurar, você deve <xref:System.Windows.Setter.Property%2A> definir `"TextBlock.FontSize"` como `"Control.FontSize"`ou.

Observe também que muitos controles WPF consistem em uma combinação de outros controles WPF. Caso você crie um estilo que se aplica a todos os controles de um tipo, pode obter resultados inesperados. Por exemplo, se você criar um estilo que tenha como <xref:System.Windows.Controls.TextBlock> alvo o tipo <xref:System.Windows.Window>em um, o estilo será aplicado `TextBlock` a todos os controles na janela, mesmo `TextBlock` que o faça parte de outro controle, como <xref:System.Windows.Controls.ListBox>um.

## <a name="see-also"></a>Confira também

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [Visão geral dos recursos XAML](xaml-resources-define.md)
- [Visão geral do XAML (WPF & .NET Core)](xaml.md)
