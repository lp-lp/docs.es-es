---
title: 'Cómo: Especificar el comportamiento de relleno de una escala de tiempo que ha llegado al final de su período de actividad'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 947be09140dc2d1d5e130ccb74472d8dce3408cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563485"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Cómo: Especificar el comportamiento de relleno de una escala de tiempo que ha llegado al final de su período de actividad
Este ejemplo muestra cómo especificar el <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> para las inactivas <xref:System.Windows.Media.Animation.Timeline> de una propiedad animada.  
  
## <a name="example"></a>Ejemplo  
 El <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propiedad de un <xref:System.Windows.Media.Animation.Timeline> determina lo que ocurre en el valor de una propiedad animada cuando no se está animando, es decir, cuando la <xref:System.Windows.Media.Animation.Timeline> está inactivo pero su elemento primario <xref:System.Windows.Media.Animation.Timeline> está dentro de su activo o período de espera. ¿Por ejemplo, una propiedad animada permanece en su extremo valor después de la animación finaliza o no se restablecerá el valor tenía antes de comenzar la animación?  
  
 En el ejemplo siguiente se usa un <xref:System.Windows.Media.Animation.DoubleAnimation> para animar la <xref:System.Windows.FrameworkElement.Width%2A> de dos rectángulos. Cada rectángulo usa otra <xref:System.Windows.Media.Animation.Timeline> objeto.  
  
 Una <xref:System.Windows.Media.Animation.Timeline> tiene un <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> que se establece en <xref:System.Windows.Media.Animation.FillBehavior.Stop>, lo que hace que el ancho del rectángulo va a revertir a su no animadas valor cuando el <xref:System.Windows.Media.Animation.Timeline> finaliza. El otro <xref:System.Windows.Media.Animation.Timeline> tiene un <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, lo que hace que el ancho permanezca en su extremo valor cuando el <xref:System.Windows.Media.Animation.Timeline> finaliza.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Para obtener un ejemplo completo, vea [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [Información general sobre animaciones](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animación y temporización](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Temas "Cómo..."](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
