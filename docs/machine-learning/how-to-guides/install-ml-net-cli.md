---
title: Como instalar a ferramenta da CLI (Interface de Linha de Comando) do ML.NET
description: Saiba como instalar, atualizar, fazer downgrade e desinstalar a ferramenta CLI (Command-Line Interface, interface de linha de comando) ML.NET.
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 9f678c7117d32bf817139951db7eef2c3d0f5eb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848633"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>Como instalar a ferramenta da CLI (Interface de Linha de Comando) do ML.NET

Saiba como instalar o ML.NET CLI (interface de linha de comando) no Windows, Mac ou Linux.

O ML.NET CLI gera boa qualidade ML.NET modelos e código-fonte usando aprendizado automático de máquina (AutoML) e um conjunto de dados de treinamento.

> [!NOTE]
> Este tópico refere-se à CLI do ML.NET e ao AutoML do ML.NET, que estão atualmente em Versão Prévia. O material pode estar sujeito a alterações.

## <a name="pre-requisites"></a>Pré-requisitos

- [SDK do .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- (Opcional) [Visual Studio 2017 ou 2019](https://visualstudio.microsoft.com/vs/)

Você pode executar os projetos de código C# gerados com o Visual Studio pressionando a `F5` tecla ou com `dotnet run` (.NET Core CLI).

Nota: Se depois de instalar [o .NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) o `dotnet tool` comando não estiver funcionando, faça login no Windows e faça login novamente.

## <a name="install"></a>Instalar

A CLI do ML.NET é instalada como qualquer outra Ferramenta Global do dotnet. Você usa o comando da CLI do .NET Core `dotnet tool install`.

O exemplo a seguir mostra como instalar a CLI do ML.NET no local de feed do NuGet padrão:

```dotnetcli
dotnet tool install -g mlnet
```

Se a ferramenta não puder ser instalada (ou seja, não estiver disponível no feed do NuGet padrão), mensagens de erro serão exibidas. Verifique se os feeds esperados estão sendo verificados.

Se a instalação for bem-sucedida, será exibida uma mensagem mostrando o comando usado para chamar a ferramenta e a versão instalada, de maneira semelhante ao seguinte exemplo:

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Você pode confirmar que a instalação foi bem-sucedida digitando o seguinte comando:

```console
mlnet
```

Você deve ver a ajuda para os comandos disponíveis para a ferramenta mlnet como o comando 'auto-train'.

## <a name="install-a-specific-release-version"></a>Instalar uma versão de liberação específica

Se estiver tentando instalar uma versão de pré-lançamento ou uma versão específica da ferramenta, especifique a [estrutura](../../standard/frameworks.md) usando o seguinte formato:

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

Você também poderá verificar se o pacote está instalado corretamente digitando o seguinte comando:

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>Desinstalar o pacote da CLI

Digite o seguinte comando para desinstalar o pacote do seu computador local:

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>Atualizar o pacote da CLI

Digite o seguinte comando para atualizar o pacote do seu computador local:

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>Configurar sugestões da CLI (preenchimento automático baseado em guia)

Como a CLI do ML.NET baseia-se em `System.CommandLine`, ela tem suporte interno para o preenchimento de guia.

Um exemplo de como o preenchimento automático de guia funciona é mostrado na animação a seguir:

![image](./media/cli-tab-completion.gif)

O "preenchimento automático baseado em guia" (sugestões de parâmetro) funciona em *Windows PowerShell* e *bash do macOS/Linux*, mas não funciona no *CMD do Windows*.

Para habilitá-lo, na versão prévia atual, o usuário final deve executar algumas etapas uma vez por shell, descritas abaixo. Depois que isso for feito, os preenchimentos vão funcionar para todos os aplicativos escritos usando `System.CommandLine`, como a CLI do ML.NET.

No computador em que você deseja habilitar o preenchimento, você precisará fazer duas coisas.

1. Instalar a ferramenta global `dotnet-suggest` executando o seguinte comando:

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. Adicionar o script de shim apropriado ao seu perfil de shell. Talvez você precise criar um arquivo de perfil de shell. O script de shim vai encaminhar solicitações de conclusão do seu shell para a ferramenta `dotnet-suggest`, que delega ao aplicativo baseado em `System.CommandLine` apropriado.

    - Para o bash, adicione o conteúdo de [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) a `~/.bash_profile`.

    - Para o PowerShell, adicione o conteúdo do [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) a seu perfil do PowerShell. Você pode encontrar o caminho esperado para seu perfil do PowerShell executando o comando a seguir em seu console:

    ```console
    echo $profile
    ```

(Para outros shells, [procure](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) ou abra um [problema](https://github.com/dotnet/System.CommandLine/issues).)

## <a name="installation-directory"></a>Diretório de instalação

A CLI do ML.NET pode ser instalada no diretório padrão ou em um local específico. Os diretórios padrão são:

| Sistema operacional          | Caminho                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Esses locais são adicionados ao caminho do usuário quando o SDK é executado pela primeira vez e, portanto, as Ferramentas Globais instaladas nesses locais podem ser chamadas diretamente.

Observação: as Ferramentas Globais são específicas ao usuário e não globais no computador. Ser específico ao usuário significa que não é possível instalar uma Ferramenta Global que esteja disponível para todos os usuários do computador. A ferramenta só fica disponível para cada perfil de usuário no qual a ferramenta foi instalada.

As Ferramentas Globais também podem ser instaladas em um diretório específico. Quando elas forem instaladas em um diretório específico, o usuário precisará garantir que o comando esteja disponível, incluindo o diretório no caminho, chamando o comando com o diretório especificado ou chamando a ferramenta no diretório especificado.
Nesse caso, a CLI do .NET Core não adiciona esse local automaticamente à variável de ambiente PATH.

## <a name="see-also"></a>Confira também

- [ML.NET visão geral da CLI](../automate-training-with-cli.md)
- [Tutorial: Analise o sentimento com o ML.NET CLI](../tutorials/sentiment-analysis-cli.md)
- [Guia de referência de comando auto-train da CLI do ML.NET](../reference/ml-net-cli-reference.md)
- [Telemetria na CLI do ML.NET](../resources/ml-net-cli-telemetry.md)
