---
title: Polígonos en GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
ms.openlocfilehash: 3ac6b9b651e65a45612cf2bd8ff17990c5cfba0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525852"
---
# <a name="polygons-in-gdi"></a>Polígonos en GDI+
Un polígono es una forma cerrada con tres o más líneas rectas. Por ejemplo, un triángulo es un polígono con tres lados, un rectángulo es un polígono con cuatro lados y un Pentágono es un polígono con cinco lados. La ilustración siguiente muestra varios polígonos.  
  
 ![Polígonos](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")  
  
## <a name="drawing-a-polygon"></a>Dibujar un polígono  
 Para dibujar un polígono, necesita un <xref:System.Drawing.Graphics> objeto, un <xref:System.Drawing.Pen> objeto y una matriz de <xref:System.Drawing.Point> (o <xref:System.Drawing.PointF>) objetos. El <xref:System.Drawing.Graphics> objeto proporciona el <xref:System.Drawing.Graphics.DrawPolygon%2A> método. El <xref:System.Drawing.Pen> objeto almacena atributos, como el ancho y color de la línea que se usa para representar el polígono y la matriz de <xref:System.Drawing.Point> objetos almacena los puntos que estén conectados mediante líneas rectas. El <xref:System.Drawing.Pen> objeto y la matriz de <xref:System.Drawing.Point> objetos se pasan como argumentos a la <xref:System.Drawing.Graphics.DrawPolygon%2A> método. En el ejemplo siguiente se dibuja un polígono de tres lados. Tenga en cuenta que hay sólo tres puntos en `myPointArray`: (0, 0), (50, 30) y (30, 60). El <xref:System.Drawing.Graphics.DrawPolygon%2A> método cierra automáticamente el polígono debe dibujar una línea desde (30, 60) hacia el punto inicial (0, 0).  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 En la siguiente ilustración se muestra el polígono.  
  
 ![Polígono](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Líneas, curvas y formas](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Crear un lápiz](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
