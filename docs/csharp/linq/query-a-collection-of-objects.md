---
title: Consultar uma coleção de objetos (LINQ em C#)
description: Saiba como consultar coleções usando LINQ em C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659800"
---
# <a name="query-a-collection-of-objects"></a>Consultar uma coleção de objetos

Este exemplo mostra como executar uma consulta simples em uma lista de objetos `Student`. Cada objeto `Student` contém algumas informações básicas sobre o aluno e uma lista que representa as pontuações do aluno em quatro provas.  
  
Este aplicativo serve como a estrutura para muitos outros exemplos nesta seção que usam as mesmas fontes de dados `students`.  
  
## <a name="example"></a>Exemplo

A consulta a seguir retorna os alunos que receberam uma pontuação de 90 ou mais em sua primeira prova.  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
Essa consulta é intencionalmente simples para que você possa testar. Por exemplo, você pode testar mais condições na cláusula `where` ou usar uma clausula `orderby` para classificar os resultados.  
  
## <a name="see-also"></a>Confira também

- [Consulta Integrada ao Idioma (LINQ)](index.md)
- [Interpolação de cadeias de caracteres](../language-reference/tokens/interpolated.md)
