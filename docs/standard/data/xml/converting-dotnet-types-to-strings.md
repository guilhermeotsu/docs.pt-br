---
title: Convertendo tipos do .NET Framework para cadeias de caracteres
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: a63e0175f6660967eb4aa678c6731d353e44e2d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711071"
---
# <a name="converting-net-framework-types-to-strings"></a>Convertendo tipos do .NET Framework para cadeias de caracteres
Se você deseja converter um tipo do .NET Framework em uma cadeia de caracteres, use o método **ToString**. O método **ToString** retorna uma representação de cadeia de caracteres do tipo passado. A tabela a seguir lista os tipos do.NET Framework que retorna uma cadeia de caracteres em um formato que mapeia a (XSD) de esquema XML as especificações.  
  
|Tipo de .NET Framework|Tipo cadeia de caracteres retornado|  
|-------------------------|--------------------------|  
|Boolean|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|Datetime|O formato é yyyy-MM-ddTHH:mm:sszzzzzz e seus subconjuntos.|  
|Timespan|O formato é PnYnMnTnHnMnS, por exemplo, `P2Y10M15DT10H30M20S` é uma duração de 2 anos, meses 10, 15 dias, 10hours, 30 minutos e 20 segundos.|  
  
## <a name="see-also"></a>Veja também

- [Conversão de tipos de dados XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [Convertendo cadeias de caracteres em tipos de dados do .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
