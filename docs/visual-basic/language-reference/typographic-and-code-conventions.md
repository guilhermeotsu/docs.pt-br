---
title: Convenções tipográficas e de código
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: 4906c5ebadb7ce77f2d0e53b2fc5dbab69c5b41f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352710"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Convenções tipográficas e de código (Visual Basic)

Visual Basic documentação usa as seguintes convenções tipográficas e de código.  
  
## <a name="typographic-conventions"></a>Convenções tipográficas  
  
|Exemplo|Descrição|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Palavras-chave específicas de idioma e membros de tempo de execução têm letras maiúsculas iniciais e são formatadas conforme mostrado neste exemplo.|  
|**SmallProject**, **buttoncollection**|As palavras e frases que você instruíu a digitar são formatadas conforme mostrado neste exemplo.|  
|[Instrução Module](../../visual-basic/language-reference/statements/module-statement.md)|Os links nos quais você pode clicar para ir para outra página de ajuda são formatados, conforme mostrado neste exemplo.|  
|*Object*, *variablename*, `argumentList`|Os espaços reservados para as informações fornecidas são formatados conforme mostrado neste exemplo.|  
|[Shadows], [ *expressionlist* ]|Na sintaxe, os itens opcionais são colocados entre colchetes.|  
|{`Public` &#124; `Friend` &#124; `Private`}|Em sintaxe, quando você deve fazer uma escolha entre dois ou mais itens, os itens são colocados entre chaves e separados por barras verticais.<br /><br /> Você deve selecionar um, e apenas um, dos itens.|  
|[`Protected` &#124; `Friend`]|Em sintaxe, quando você tem a opção de selecionar entre dois ou mais itens, os itens são colocados entre colchetes e separados por barras verticais.<br /><br /> Você pode selecionar qualquer combinação de itens ou nenhum item.|  
|[{`ByVal` &#124; `ByRef`}]|Em sintaxe, quando você pode selecionar não mais de um item, mas também pode omitir os itens completamente, os itens são colocados entre colchetes entre chaves e separados por barras verticais.|  
|*MemberName*1, *MemberName*2, *MemberName*3|Várias instâncias do mesmo espaço reservado são diferenciadas por subscritos, conforme mostrado no exemplo.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNamen*|Na sintaxe, uma elipse (...) é usada para indicar um número indefinido de itens do tipo imediatamente na frente das reticências.<br /><br /> No código, as reticências significam código omitido para fins de clareza.|  
|ESC, ENTER|Os nomes de chave e as sequências de chave no teclado aparecem em letras maiúsculas.|  
|ALT+F1|Quando sinais de mais (+) aparecem entre nomes de chave, você deve manter uma tecla pressionada ao pressionar o outro. Por exemplo, ALT + F1 significa manter pressionada a tecla ALT enquanto pressiona a tecla F1.|  
  
## <a name="code-conventions"></a>Convenções de código  
  
|Exemplo|Descrição|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Exemplos de código aparecem em uma fonte de densidade fixa e são formatados conforme mostrado neste exemplo.|  
|A instrução anterior define o valor de `sampleString` como "Olá, mundo!"|Elementos de código em texto explicativo aparecem em uma fonte de densidade fixa, como mostrado neste exemplo.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Os comentários de código são introduzidos por um apóstrofo (') ou a palavra-chave REM.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Um espaço seguido por um sublinhado (_) no final de uma linha indica que a instrução continua na linha a seguir.|  
  
## <a name="see-also"></a>Consulte também

- [Referência da linguagem Visual Basic](../../visual-basic/language-reference/index.md)
- [Palavras-chave](../../visual-basic/language-reference/keywords/index.md)
- [Membros da Biblioteca de Runtime do Visual Basic](../../visual-basic/language-reference/runtime-library-members.md)
- [Visual Basic convenções de nomenclatura](../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Como quebrar e combinar instruções no código](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Comentários no Código](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
