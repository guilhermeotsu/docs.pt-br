---
title: 'Como: gravar mensagens de log'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 38570047db48e009aea2af376304430db1ec29f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352064"
---
# <a name="how-to-write-log-messages-visual-basic"></a>Como gravar mensagens de log (Visual Basic)

É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log informações sobre seu aplicativo. Este exemplo mostra como usar o método `My.Application.Log.WriteEntry` para registrar em log informações de rastreamento.

Para registrar informações de exceção em log, use o método `My.Application.Log.WriteException`; consulte [How to: Log Exceptions (Como registrar em log as exceções)](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

## <a name="example"></a>Exemplo

Este exemplo usa o método `My.Application.Log.WriteEntry` para gravar as informações de rastreamento.

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a>Segurança do .NET Framework

Certifique-se de que os dados gravados no log não incluem informações confidenciais como senhas de usuário. Para obter mais informações, consulte [Working with Application Logs (Trabalhando com logs de aplicativo)](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

## <a name="see-also"></a>Veja também

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Trabalhar com logs do aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Como: registrar exceções em log](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Passo a passo: determinar o local no qual My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Passo a passo: alterar o local no qual My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Passo a passo: filtrar a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
