---
title: Palavra-chave contextual when – referência de C#
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712826"
---
# <a name="when-c-reference"></a>when (Referência de C#)

Você pode usar a palavra-chave contextual `when` para especificar uma condição de filtro em dois contextos:

- Na instrução `catch` de um bloco [try/catch](try-catch.md) ou [try/catch/finally](try-catch-finally.md).
- No rótulo `case` de uma instrução [switch](switch.md).

## <a name="when-in-a-catch-statement"></a>`when` em uma instrução `catch`

Começando com o C# 6, `when` pode ser usado em uma instrução `catch` para especificar uma condição que deve ser verdadeira para o manipulador para uma exceção específica a ser executada. Sua sintaxe é:

```csharp
catch (ExceptionType [e]) when (expr)
```

em que *expr* é uma expressão que é avaliada como um valor booliano. Se ele retornar `true`, o manipulador de exceção será executado, se `false`, não executará.

O exemplo a seguir usa a palavra-chave `when` para executar os manipuladores condicionalmente para um <xref:System.Net.Http.HttpRequestException> dependendo do texto da mensagem de exceção.

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a>`when` em uma instrução `switch`

Iniciando com C# 7.0, os rótulos `case` não precisam mais ser mutuamente exclusivos e a ordem na qual os rótulos `case` são exibidos em uma instrução `switch` pode determinar qual bloco de opção é executado. A palavra-chave `when` pode ser usada para especificar uma condição de filtro que faz com que seu rótulo case associado seja verdadeiro somente se a condição de filtro também for verdadeira. Sua sintaxe é:

```csharp
case (expr) when (when-condition):
```

em que *expr* é um padrão de constante ou padrão de tipo que é comparado com a expressão de correspondência e *when-condition* é qualquer expressão booliana.

O exemplo a seguir usa a palavra-chave `when` para testar os objetos `Shape` que têm uma área de zero, bem como para testar uma variedade de objetos `Shape` que têm uma área maior que zero.

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a>Confira também

- [Instrução switch](switch.md)
- [instruções try/catch](try-catch.md)
- [try/catch/finally statement](try-catch-finally.md)
