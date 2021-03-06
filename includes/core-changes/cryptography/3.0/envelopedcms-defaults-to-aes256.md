---
ms.openlocfilehash: b90991affe158286f535f3cc17232efd0b730fec
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274913"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>EnvelopedCms é padrão para criptografia AES-256

O algoritmo de criptografia simétrico padrão usado por `EnvelopedCms` foi alterado de TripleDES para AES-256.

#### <a name="change-description"></a>Descrição da alteração

Em versões do .NET <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> Core Preview 7 e anteriores, quando são usadas para criptografar dados sem especificar um algoritmo de criptografia simétrica através de uma sobrecarga de construtor, os dados foram criptografados com o algoritmo TripleDES/3DES/3DEA/DES3-EDE.

Começando com o pacote .NET Core 3.0 Preview 8 (via versão 4.6.0 do [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet), o algoritmo padrão foi alterado para AES-256 para modernização de algoritmos e para melhorar a segurança das opções padrão. Se um certificado de destinatário de mensagens tiver uma chave pública Diffie-Hellman <xref:System.Security.Cryptography.CryptographicException> (não CE), a operação de criptografia pode falhar devido a limitações na plataforma subjacente.

No código de amostra a seguir, os dados são criptografados com O TriploDES se estiver em execução no .NET Core 3.0 Preview 7 ou anterior. Se estiver sendo executado no .NET Core 3.0 Preview 8 ou posterior, ele será criptografado com a AES-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 8

#### <a name="recommended-action"></a>Ação recomendada

Se você for impactado negativamente pela alteração, você pode restaurar a criptografia TripleDES <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> especificando explicitamente o identificador <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>de algoritmo de criptografia em um construtor que inclui um parâmetro de tipo, como:

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>Categoria

Criptografia

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
