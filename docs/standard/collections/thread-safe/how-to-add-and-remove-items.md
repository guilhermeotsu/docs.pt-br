---
title: Como adicionar e remover itens de um ConcurrentDictionary
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
ms.openlocfilehash: 6e5204c5a71232ef9d1a050891e7fe6d92c375f2
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796113"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Como adicionar e remover itens de um ConcurrentDictionary

Este exemplo mostra como adicionar, recuperar, atualizar e remover itens de um <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>. Essa classe de coleção é uma implementação thread-safe. É recomendável usá-la sempre que vários threads possam estar tentando acessar os elementos simultaneamente.

<xref:System.Collections.Concurrent.ConcurrentDictionary%602> fornece vários métodos de conveniência que tornam desnecessário que o código verifique se uma chave existe antes de tentar adicionar ou remover dados. A tabela a seguir lista esses métodos de conveniência e descreve quando usá-los.

| Método | Use quando… |
|--|--|
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> | Você desejar adicionar um novo valor para uma chave especificada e, se a chave já existir, você desejar substituir seu valor. |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> | Você desejar recuperar o valor existente de uma chave especificada e, se a chave não existir, você desejar especificar um par chave/valor. |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A> | Você desejar adicionar, obter, atualizar ou remover um par chave/valor e, se a chave já existir ou se a tentativa falhar por qualquer motivo, você desejar executar alguma ação alternativa. |

## <a name="example"></a>Exemplo

O exemplo a seguir usa duas instâncias de <xref:System.Threading.Tasks.Task> para adicionar alguns elementos em um <xref:System.Collections.Concurrent.ConcurrentDictionary%602> simultaneamente e, em seguida, gera todo o conteúdo para mostrar que os elementos foram adicionados com êxito. O exemplo também mostra como usar os <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>métodos, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>e <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> para adicionar, atualizar e recuperar itens da coleção.

[!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
[!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]

<xref:System.Collections.Concurrent.ConcurrentDictionary%602> foi projetado para cenários multi-threaded. Você não precisa usar bloqueios em seu código para adicionar ou remover itens da coleção. No entanto, sempre é possível que um thread recupere um valor e que outro thread atualize imediatamente a coleção, dando um novo valor à mesma chave.

Além disso, embora todos os métodos de <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sejam thread-safe, nem todos os métodos são atômicos, especificamente <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> e <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>. O delegado do usuário que é passado para esses métodos é invocado fora do bloqueio interno do dicionário (isso é feito para impedir que um código desconhecido bloqueie todos os threads). Portanto, é possível que ocorra esta sequência de eventos:

1. chamadas <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>de _ThreadA_ , não localizam nenhum item e cria um novo item a ser adicionado `valueFactory` invocando o delegado.

1. _threadB_ chamadas <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> ThreadB simultaneamente, seu `valueFactory` delegado é invocado e chega ao bloqueio interno antes de _ThreadA_e, portanto, seu novo par chave-valor é adicionado ao dicionário.

1. a delegação _de usuário do ThreadA é_ concluída e o thread chega ao bloqueio, mas agora vê que o item já existe.

1. _ThreadA_ executa um "Get" e retorna os dados que foram adicionados anteriormente pelo _ThreadB_.

Portanto, não há garantia de que os dados retornados pelo <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> são os mesmos dados que foram criados pelo thread. `valueFactory` Uma sequência semelhante de eventos pode ocorrer quando <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> é chamado.

## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Coleções com segurança de thread](../../../../docs/standard/collections/thread-safe/index.md)
