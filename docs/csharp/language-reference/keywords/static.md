---
title: Modificador static – Referência de C#
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 771bcfdac4c4bf27c15da4bc374d804405317a78
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102054"
---
# <a name="static-c-reference"></a>static (Referência de C#)

Esta página `static` cobre a palavra-chave modificadora. A `static` palavra-chave também [`using static`](using-static.md) faz parte da diretiva.

Use o modificador `static` para declarar um membro estático que pertença ao próprio tipo, em vez de um objeto específico. O `static` modificador pode ser `static` usado para declarar classes. Em classes, interfaces e estruturas, você pode `static` adicionar o modificador a campos, métodos, propriedades, operadores, eventos e construtores. O `static` modificador não pode ser usado com indexadores ou finalizadores. Para obter mais informações, consulte [Classes Estáticas e Membros de Classe Estática](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example---static-class"></a>Exemplo - classe estática

A seguinte classe é declarada como `static` e contém apenas métodos `static`:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Uma declaração constante ou `static` de tipo é implicitamente um membro. Um `static` membro não pode ser referenciado através de uma instância. Em vez disso, é referenciado através do nome do tipo. Por exemplo, considere a seguinte classe:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Para consultar `static` o `x`membro, use o `MyBaseC.MyStruct.x`nome totalmente qualificado, a menos que o membro esteja acessível no mesmo escopo:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Embora uma instância de uma classe contenha uma cópia separada de todos os `static` campos de instância da classe, há apenas uma cópia de cada campo.

Não é possível usar [`this`](this.md) para `static` referenciar métodos ou acessórios de propriedade.

Se `static` a palavra-chave for aplicada a uma classe, `static`todos os membros da classe devem ser .

Classes, interfaces `static` e aulas `static` podem ter construtores. Um `static` construtor é chamado em algum momento entre quando o programa começa e a classe é instanciada.

> [!NOTE]
> A palavra-chave `static` tem utilizações mais limitadas do que no C++. Para comparar com a palavra-chave do C++, consulte [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static) (Classes de armazenamento (C++)).

Para `static` demonstrar os membros, considere uma classe que represente um funcionário da empresa. Suponha que a classe contém um método para contar funcionários e um campo para armazenar o número de funcionários. Tanto o método quanto o campo não pertencem a nenhuma instância de funcionário. Em vez disso, pertencem à classe de empregados como um todo. Eles devem ser `static` declarados como membros da classe.

## <a name="example---static-field-and-method"></a>Exemplo - campo e método estáticos

Este exemplo lê o nome e a ID de um novo funcionário, incrementa o contador de funcionário em um e exibe as informações do novo funcionário e do novo número de funcionários. Este programa lê o número atual de funcionários do teclado.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a>Exemplo - inicialização estática

Este exemplo mostra que você `static` pode inicializar um campo usando outro `static` campo que ainda não foi declarado. Os resultados serão indefinidos até que você `static` atribua explicitamente um valor ao campo.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [C# Palavras-chave](index.md)
- [Modificadores](index.md)
- [usando diretiva estática](using-static.md)
- [Classes static e membros de classes static](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
