---
ms.openlocfilehash: becae23cd810623bbb33c693b707c2d4735aeece
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158457"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a>A substituição de sequências de bytes UTF-8 mal formados segue as diretrizes de Unicode

Quando a <xref:System.Text.UTF8Encoding> classe encontra uma sequência de bytes UTF-8 mal formada durante uma operação de transcodificação de byte para caractere, ela substitui essa sequência por um caractere ' ' (caractere de substituição U + FFFD) na cadeia de caracteres de saída. O .NET Core 3,0 é diferente das versões anteriores do .NET Core e do .NET Framework seguindo a prática recomendada de Unicode para executar essa substituição durante a operação de transcodificação.

Isso faz parte de um esforço maior para melhorar a manipulação de UTF-8 em todo o .NET, <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> incluindo <xref:System.Text.Rune?displayProperty=nameWithType> os novos e os tipos. O <xref:System.Text.UTF8Encoding> tipo recebeu uma melhor mecânica de tratamento de erros para que produza a saída consistente com os tipos introduzidos recentemente.

#### <a name="change-description"></a>Descrição da alteração

A partir do .NET Core 3,0, ao transcodificar bytes em caracteres, <xref:System.Text.UTF8Encoding> a classe executa a substituição de caracteres com base nas práticas recomendadas do Unicode. O mecanismo de substituição usado é descrito pelo [padrão Unicode, versão 12,0, seg. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) no título intitulado _U + FFFD substituição de subpartes do máximo_.

Esse comportamento se aplica _somente_ quando a sequência de bytes de entrada contém dados UTF-8 mal formados. Além disso, se <xref:System.Text.UTF8Encoding> a instância tiver sido construída `throwOnInvalidBytes: true`com, `UTF8Encoding` a instância continuará a gerar uma entrada inválida em vez de executar a substituição U + FFFD. Para obter mais informações sobre `UTF8Encoding` o construtor, <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>consulte.

A tabela a seguir ilustra o impacto dessa alteração com uma entrada de 3 bytes inválida:

| Entrada de 3 bytes formada incorretamente | Saída antes do .NET Core 3,0          | Saída a partir do .NET Core 3,0        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | `[ FFFD FFFD ]`(saída de 2 caracteres) | `[ FFFD FFFD FFFD ]`(saída de 3 caracteres) |

A saída de 3 caracteres é a saída preferida, de acordo com a _tabela 3-9_ do PDF padrão Unicode vinculado anteriormente.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Nenhuma ação é necessária na parte do desenvolvedor.

#### <a name="category"></a>Categoria

Bibliotecas principais do .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
