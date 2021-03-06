---
ms.openlocfilehash: 4529d8040fc08b5290ac46abd1ef752086ea3aeb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774295"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>Sobrecargas novas (ambíguas) do Dispatcher.Invoke podem resultar em comportamento diferente

|   |   |
|---|---|
|Detalhes|O .NET Framework 4.5 adiciona novas sobrecargas ao <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> que incluem um parâmetro do tipo <xref:System.Action>. Quando um código existente é recompilado, os compiladores podem resolver as chamadas aos métodos Dispatcher.Invoke que têm um parâmetro <xref:System.Delegate> como chamadas aos métodos Dispatcher.Invoke com um parâmetro <xref:System.Action>. Se uma chamada à sobrecarga do Dispatcher.Invoke com um parâmetro <xref:System.Delegate> for resolvida como uma chamada à sobrecarga do Dispatcher.Invoke com um parâmetro <xref:System.Action>, poderão ocorrer as seguintes diferenças no comportamento:<ul><li>Se ocorrer uma exceção, os eventos <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> e <xref:System.Windows.Threading.Dispatcher.UnhandledException> não serão gerados. Em vez disso, as exceções são tratadas pelo evento <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=name>.</li><li>Chamadas para alguns membros, como <xref:System.Windows.Threading.DispatcherOperation.Result>, são bloqueadas até que a operação seja concluída.</li></ul>|
|Sugestão|Para evitar ambiguidade (e possíveis diferenças no tratamento de exceções ou nos comportamentos de bloqueio), o código que chama o Dispatcher.Invoke pode passar um object[] vazio como um segundo parâmetro à chamada de Invoke para garantir a resolução da sobrecarga do método no .NET Framework 4.0.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType></li></ul>|
