---
title: Como modificar o conteúdo das cordas - Guia C#
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: 8e9bbe76c689d3c3f9f238ca9dd95cc7fcf98b18
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389523"
---
# <a name="how-to-modify-string-contents-in-c"></a>Como modificar o conteúdo das strings em C\#

Este artigo demonstra várias técnicas para produzir um `string` modificando um `string` existente. Todas as técnicas demonstradas retornam o resultado das modificações como um novo objeto `string`. Para demonstrar isso claramente, todos os exemplos armazenam o resultado em uma nova variável. Em seguida, você pode examinar o `string` original e o `string` resultante da modificação quando você executa cada exemplo.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Há várias técnicas demonstradas neste artigo. Você pode substituir o texto existente. Você pode procurar padrões e substituir o texto correspondente com outro texto. Você pode tratar uma cadeia de caracteres como uma sequência de caracteres. Você também pode usar métodos de conveniência que removem o espaço em branco. Escolha as técnicas que mais combinam com o seu cenário.

## <a name="replace-text"></a>Substituir texto

O código a seguir cria uma nova cadeia de caracteres, substituindo o texto existente por um substituto.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

O código anterior demonstra essa propriedade *immutable* de cadeias de caracteres. Você pode ver no exemplo anterior que a cadeia de caracteres original, `source`, não é modificada. O método <xref:System.String.Replace%2A?displayProperty=nameWithType> cria uma nova `string` contendo as modificações.

O método <xref:System.String.Replace%2A> pode substituir cadeias de caracteres ou caracteres únicos. Em ambos os casos, todas as ocorrências do texto pesquisado são substituídas.  O exemplo a seguir substitui todos os caracteres ' ' com '\_':

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

A cadeia de caracteres de origem não é alterada e uma nova cadeia de caracteres é retornada com a substituição.

## <a name="trim-white-space"></a>Cortar espaço em branco

Você pode usar os métodos <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType> e <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> para remover espaços em branco à esquerda ou à direita.  O código a seguir mostra um exemplo de cada um desses casos. A cadeia de caracteres de origem não é alterada; esses métodos retornam uma nova cadeia de caracteres com o conteúdo modificado.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Remover texto

Você pode remover texto de uma cadeia de caracteres usando o método <xref:System.String.Remove%2A?displayProperty=nameWithType>. Esse método remove um número de caracteres começando em um índice específico. O exemplo a seguir mostra como usar <xref:System.String.IndexOf%2A?displayProperty=nameWithType> seguido por <xref:System.String.Remove%2A> para remover texto de uma cadeia de caracteres:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Substituir padrões correspondentes

Você pode usar [expressões regulares](../../standard/base-types/regular-expressions.md) para substituir padrões correspondentes de texto com um novo texto, possivelmente definido por um padrão. O exemplo a seguir usa a classe <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> para localizar um padrão em uma cadeia de caracteres de origem e substituí-lo pela capitalização correta. O método <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> usa uma função que fornece a lógica de substituição como um de seus argumentos. Neste exemplo, essa função `LocalReplaceMatchCase` é uma **função local** declarada dentro do método de exemplo. `LocalReplaceMatchCase` usa a classe <xref:System.Text.StringBuilder?displayProperty=nameWithType> para criar a cadeia de caracteres de substituição com a capitalização correta.

Expressões regulares são mais úteis para localizar e substituir texto que segue um padrão, em vez de texto conhecido. Para obter mais informações, consulte [Como pesquisar strings](search-strings.md). O padrão de pesquisa "the\s" procura a palavra "the" seguida por um caractere de espaço em branco. Essa parte do padrão garante que isso não corresponda a "there" na cadeia de caracteres de origem. Para obter mais informações sobre elementos de linguagem de expressão regular, consulte [Linguagem de expressão regular – referência rápida](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

O método <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> retorna uma cadeia de caracteres imutável com o conteúdo no objeto <xref:System.Text.StringBuilder>.

## <a name="modifying-individual-characters"></a>Modificar caracteres individuais

Você pode produzir uma matriz de caracteres de uma cadeia de caracteres, modificar o conteúdo da matriz e, em seguida, criar uma nova cadeia de caracteres com base no conteúdo modificado da matriz.

O exemplo a seguir mostra como substituir um conjunto de caracteres em uma cadeia de caracteres. Primeiro, ele usa o método <xref:System.String.ToCharArray?displayProperty=nameWithType> para criar uma matriz de caracteres. Ele usa o método <xref:System.String.IndexOf%2A> para localizar o índice inicial da palavra "fox". Os próximos três caracteres são substituídos por uma palavra diferente. Por fim, uma nova cadeia de caracteres é construída com a matriz de caracteres atualizada.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="programmatically-build-up-string-content"></a>Programmaticamente construir conteúdo de string

Como as strings são imutáveis, os exemplos anteriores criam strings temporárias ou matrizes de caracteres. Em cenários de alto desempenho, pode ser desejável evitar essas alocações de pilhas. O .NET <xref:System.String.Create%2A?displayProperty=nameWithType> Core fornece um método que permite que você preencha programáticamente o conteúdo do caractere de uma string através de um retorno de chamada, evitando as alocações de strings temporárias intermediárias.

[!code-csharp[using string.Create to programmatically build the string content for a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Você pode modificar uma seqüência em um bloco fixo com código inseguro, mas é **fortemente** desencorajado a modificar o conteúdo da seqüência depois que uma string é criada. Fazer isso vai quebrar as coisas de maneiras imprevisíveis. Por exemplo, se alguém internar uma string que tenha o mesmo conteúdo que o seu, ele receberá sua cópia e não esperará que você esteja modificando sua seqüência.

Você pode experimentar essas amostras olhando para o código em nosso [repositório GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Ou então, você pode baixar os exemplos [como um arquivo zip](../../../samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Confira também

- [Expressões regulares do .NET Framework](../../standard/base-types/regular-expressions.md)
- [Linguagem de expressões regulares – referência rápida](../../standard/base-types/regular-expression-language-quick-reference.md)
