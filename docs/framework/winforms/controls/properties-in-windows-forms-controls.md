---
title: Propriedades de controles
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 82bfab15cef4946661a37d2d88fbe1b797f3d816
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741174"
---
# <a name="properties-in-windows-forms-controls"></a>Propriedades em controles dos Windows Forms
Um controle de Windows Forms herda muitas propriedades que formam a classe base <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Isso inclui propriedades como <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>e muitos outros. Para obter detalhes sobre as propriedades herdadas, consulte <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 Você pode substituir as propriedades herdadas em seu controle, bem como definir novas propriedades.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Definindo uma propriedade](defining-a-property-in-windows-forms-controls.md)  
 Mostra como implementar uma propriedade para um controle personalizado ou componente e mostra como integrar a propriedade ambiente no de design.  
  
 [Definindo valores padrão com os métodos ShouldSerialize e Reset](defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Mostra como definir valores de propriedade padrão para um controle ou componente personalizado.  
  
 [Eventos com propriedade alterada](property-changed-events.md)  
 Descreve como habilitar as notificações de alteração de propriedade quando um valor da propriedade for alterado.  
  
 [Como expor as propriedades de controles constituintes](how-to-expose-properties-of-constituent-controls.md)  
 Mostra como expor as propriedades de controles constituintes em um controle de composição o personalizado.  
  
 [Implementação do método em controles personalizados](method-implementation-in-custom-controls.md)  
 Descreve como implementar métodos de componentes e controles personalizados.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.UserControl>  
 Documenta a classe base para implementar controles de composição.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Documenta o atributo que especifica o <xref:System.ComponentModel.TypeConverter> a ser usado para um tipo de propriedade personalizada.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Documenta o atributo que especifica o <xref:System.Drawing.Design.UITypeEditor> a ser usado para uma propriedade personalizada.  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Atributos em controles dos Windows Forms](attributes-in-windows-forms-controls.md)  
 Descreve os atributos que você pode aplicar a propriedades ou outros membros de seus controles e componentes personalizados.  
  
 [Atributos de tempo de design para componentes](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))  
 Lista atributos de metadados para aplicar a componentes e controles para que eles sejam exibidos corretamente em tempo de design em designers visuais.  
  
 [Estendendo o suporte ao tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))  
 Descreve como implementar classes como editores e designers que oferecem suporte a tempo de design.
