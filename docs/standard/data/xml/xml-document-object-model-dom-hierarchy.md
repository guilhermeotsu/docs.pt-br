---
title: Hierarquia DOM (Document Object Model) XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: 1193d7631816fe9fbf7aa1984d79ef8e61d5da80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709966"
---
# <a name="xml-document-object-model-dom-hierarchy"></a>Hierarquia DOM (Document Object Model) XML
A ilustração a seguir mostra a hierarquia de classes para o DOM (Document Object Model) XML, com o nome do World Wide Web Consortium (W3C) entre parênteses junto com o nome da classe onde é relevante.  
  
 ![Modelo de Objeto do Documento XML &#40;hierarquia de&#41; DOM](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
Hierarquia DOM (Document Object Model) XML  
  
 As seguintes classes não herdam de **XmlNode**:  
  
- **XmlImplementation**  
  
- **XmlNamedNodeMap**  
  
- **XmlNodeList**  
  
- **XmlNodeChangedEventArgs**  
  
 A classe **XmlImplementation** é usada para criar um documento XML. Para saber mais, confira [Criação de documento XML](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 A classe **XmlNamedNodeMap** manipula um conjunto não ordenado de nós. Para saber mais, confira [Recuperação não ordenada de nós por nome ou índice](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 A classe **XmlNodeList** manipula uma lista ordenada de nós. Para saber mais, confira [Recuperação ordenada de nós por índice](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 A classe **XmlNodeChangedEventArgs** manipula os manipuladores de eventos registrados em **XmlDocument**. Para saber mais, confira [Manipulação de eventos em um documento XML usando XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 A classe **XmlLinkedNode** herda de **XmlNode**. Sua finalidade é substituir dois métodos de **XmlNode**: os métodos **PreviousSibling** e **NextSibling**. Esses métodos substituídos são então herdados e usados por **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference** e **XmlProcessingInstruction**, que são classes que têm irmãos anteriores e seguintes.  
  
## <a name="see-also"></a>Veja também

- [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
