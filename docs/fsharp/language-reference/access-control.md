---
title: Controle de acesso
description: Saiba como controlar o acesso a elementos de programação, como tipos, métodos e funções, na linguagem de F# programação.
ms.date: 05/16/2016
ms.openlocfilehash: fe204a883a440794fdd033c54d6d8d4fb68e0ce2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425106"
---
# <a name="access-control"></a>Controle de acesso

O *controle de acesso* refere-se à declaração de quais clientes podem usar determinados elementos do programa, como tipos, métodos e funções.

## <a name="basics-of-access-control"></a>Noções básicas do controle de acesso

No F#, os especificadores de controle de acesso `public`, `internal`e `private` podem ser aplicados a módulos, tipos, métodos, definições de valor, funções, propriedades e campos explícitos.

- `public` indica que a entidade pode ser acessada por todos os chamadores.

- `internal` indica que a entidade pode ser acessada somente do mesmo assembly.

- `private` indica que a entidade pode ser acessada somente do tipo ou módulo delimitador.

> [!NOTE]
> O especificador de acesso `protected` não é F#usado no, embora seja aceitável se você estiver usando tipos criados em linguagens que dão suporte a acesso `protected`. Portanto, se você substituir um método protegido, seu método permanecerá acessível somente dentro da classe e seus descendentes.

Em geral, o especificador é colocado na frente do nome da entidade, exceto quando um especificador `mutable` ou `inline` é usado, que aparece após o especificador de controle de acesso.

Se nenhum especificador de acesso for usado, o padrão será `public`, exceto para associações de `let` em um tipo, que são sempre `private` para o tipo.

As assinaturas F# no fornecem outro mecanismo para controlar o F# acesso aos elementos do programa. As assinaturas não são necessárias para o controle de acesso. Para saber mais, confira [Assinaturas](signature-files.md).

## <a name="rules-for-access-control"></a>Regras para controle de acesso

O controle de acesso está sujeito às seguintes regras:

- Declarações de herança (ou seja, o uso de `inherit` para especificar uma classe base para uma classe), declarações de interface (ou seja, especificar que uma classe implementa uma interface) e membros abstratos sempre têm a mesma acessibilidade que o tipo de delimitador. Portanto, um especificador de controle de acesso não pode ser usado nessas construções.

- A acessibilidade para casos individuais em uma união discriminada é determinada pela acessibilidade da união discriminada em si. Ou seja, um caso de União específico não é menos acessível do que a União em si.

- A acessibilidade para campos individuais de um tipo de registro é determinada pela acessibilidade do próprio registro. Ou seja, um rótulo de registro específico não é menos acessível do que o próprio registro.

## <a name="example"></a>Exemplo

O código a seguir ilustra o uso de especificadores de controle de acesso. Há dois arquivos no projeto, `Module1.fs` e `Module2.fs`. Cada arquivo é implicitamente um módulo. Portanto, há dois módulos, `Module1` e `Module2`. Um tipo privado e um tipo interno são definidos em `Module1`. O tipo particular não pode ser acessado a partir de `Module2`, mas o tipo interno pode.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

O código a seguir testa a acessibilidade dos tipos criados no `Module1.fs`.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Assinaturas](signature-files.md)
