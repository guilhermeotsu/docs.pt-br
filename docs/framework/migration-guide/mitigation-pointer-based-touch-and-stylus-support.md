---
title: 'Mitigação: suporte a toque e caneta com base em ponteiro'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 023c38f66611bd0022699d3f62d90c3923585012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77094469"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Mitigação: suporte a toque e caneta com base em ponteiro

Os aplicativos WPF que visam o .NET Framework 4.7 e estão sendo executados `WM_POINTER`no Windows a partir do Windows 10 Creators Update podem habilitar uma pilha de toque/caneta WPF baseada em opcionais.

## <a name="impact"></a>Impacto

Os desenvolvedores que não habilitarem explicitamente o suporte a toque/caneta com base em ponteiro não verão nenhuma alteração no comportamento de toque/caneta do WPF.

A seguir estão os problemas conhecidos no momento com a pilha de toque/caneta com base em `WM_POINTER` opcional:

- Não há suporte para escrita à tinta em tempo real.

   Embora os plug-ins de caneta e escrita à tinta ainda funcionem, eles são processados no thread da interface do usuário, o que pode levar a um desempenho ruim.

- Alterações de comportamento devido a alterações na promoção de eventos de toque/caneta para eventos de mouse.

  - A manipulação pode se comportar de maneira diferente.

  - Arrastar/soltar não mostrará comentários apropriados para entrada por toque. (Isso não afeta entrada de caneta).

  - Arrastar/soltar não pode mais ser iniciado em eventos de toque/caneta.

      Isso pode fazer com que o aplicativo pare de responder até que a entrada do mouse seja detectada. Em vez disso, os desenvolvedores devem iniciar a ação de arrastar e soltar usando eventos de mouse.

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a>Optar pelo suporte a toque/caneta com base em WM_POINTER

Os desenvolvedores que desejam habilitar essa pilha podem adicionar o seguinte ao arquivo *app.config* de seu aplicativo.

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Remover esta entrada ou definir seu valor como `false` desabilita essa pilha opcional.

## <a name="see-also"></a>Confira também

- [Compatibilidade de aplicativos](application-compatibility.md)
