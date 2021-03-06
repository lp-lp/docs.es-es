---
title: Información general sobre formas y dibujo básico en WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: adbf982da25ff445d277b7c1b5911217d9825c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566316"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Información general sobre formas y dibujo básico en WPF
Este tema proporciona información general sobre cómo dibujar con <xref:System.Windows.Shapes.Shape> objetos. A <xref:System.Windows.Shapes.Shape> es un tipo de <xref:System.Windows.UIElement> que le permite dibujar una forma en la pantalla. Dado que son elementos de interfaz de usuario, <xref:System.Windows.Shapes.Shape> objetos pueden utilizarse dentro de <xref:System.Windows.Controls.Panel> elementos y la mayoría de los controles.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ofrece varias capas de acceso a gráficos y servicios de representación. En la capa superior, <xref:System.Windows.Shapes.Shape> objetos son fáciles de utilizar y proporcionan numerosas características útiles, como diseño y participación en el [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sistema de eventos.  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a>Objetos Shape  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Proporciona una serie de listas para usar <xref:System.Windows.Shapes.Shape> objetos.  Todos los objetos de forma que se heredan de la <xref:System.Windows.Shapes.Shape> clase. Los objetos de formas disponibles incluyen <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, y <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Shapes.Shape> objetos comparten las siguientes propiedades comunes.  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A>: Describe cómo se pinta el contorno de la forma.  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describe el grosor del contorno de la forma.  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A>: Describe cómo se pinta el interior de la forma.  
  
-   Propiedades de datos para especificar coordenadas y vértices, medidos en píxeles independientes del dispositivo.  
  
 Dado que derivan de <xref:System.Windows.UIElement>, objetos de forma que se puedan usar dentro de paneles y la mayoría de los controles. El <xref:System.Windows.Controls.Canvas> panel es especialmente conveniente para crear dibujos complejos, ya que admite la posición absoluta de los objetos secundarios.  
  
 La <xref:System.Windows.Shapes.Line> clase le permite dibujar una línea entre dos puntos. En el ejemplo siguiente se muestran varias maneras de especificar coordenadas de línea y propiedades de trazo.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 La siguiente imagen muestra el representado <xref:System.Windows.Shapes.Line>.  
  
 ![Ilustración de línea](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Aunque la <xref:System.Windows.Shapes.Line> clase proporcionar un <xref:System.Windows.Shapes.Shape.Fill%2A> valor de la propiedad, no tiene ningún efecto porque un <xref:System.Windows.Shapes.Line> no tiene un área.  
  
 Otra forma común es la <xref:System.Windows.Shapes.Ellipse>.  Crear un <xref:System.Windows.Shapes.Ellipse> mediante la definición de la forma <xref:System.Windows.FrameworkElement.Width%2A> y <xref:System.Windows.FrameworkElement.Height%2A> propiedades. Para dibujar un círculo, especifique un <xref:System.Windows.Shapes.Ellipse> cuyo <xref:System.Windows.FrameworkElement.Width%2A> y <xref:System.Windows.FrameworkElement.Height%2A> valores son iguales.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 La siguiente imagen muestra un ejemplo de un representado <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Ilustración de elipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>Utilizar trazados y geometrías  
 La <xref:System.Windows.Shapes.Path> clase le permite dibujar curvas y formas complejas. Estas curvas y formas se describen mediante <xref:System.Windows.Media.Geometry> objetos. Para usar un <xref:System.Windows.Shapes.Path>, se crea un <xref:System.Windows.Media.Geometry> y usarla para definir la <xref:System.Windows.Shapes.Path> del objeto <xref:System.Windows.Shapes.Path.Data%2A> propiedad.  
  
 Hay una variedad de <xref:System.Windows.Media.Geometry> objetos que puede elegir. El <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, y <xref:System.Windows.Media.EllipseGeometry> las clases describen formas relativamente simples. Para crear formas más complejas o crear curvas, utilice un <xref:System.Windows.Media.PathGeometry>.  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry y PathSegments  
 <xref:System.Windows.Media.PathGeometry> los objetos se componen de uno o varios <xref:System.Windows.Media.PathFigure> objetos; cada <xref:System.Windows.Media.PathFigure> representa un diferentes "figura" o forma. Cada <xref:System.Windows.Media.PathFigure> propio consta de uno o varios <xref:System.Windows.Media.PathSegment> objetos, cada uno representa una parte conectada de la figura o forma. Tipos de segmentos incluyen lo siguiente: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, y <xref:System.Windows.Media.ArcSegment>.  
  
 En el ejemplo siguiente, un <xref:System.Windows.Shapes.Path> se utiliza para dibujar una curva Bézier cuadrática.  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 La siguiente imagen muestra la forma representada.  
  
 ![Ilustración de trayecto](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Para obtener más información acerca de <xref:System.Windows.Media.PathGeometry> y el otro <xref:System.Windows.Media.Geometry> las clases, consulte la [información general sobre geometría](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>Sintaxis abreviada de XAML  
 En [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], también puede usar una sintaxis abreviada especial para describir un <xref:System.Windows.Shapes.Path>. En el ejemplo siguiente, se utiliza la sintaxis abreviada para dibujar una forma compleja.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 La siguiente imagen muestra un representado <xref:System.Windows.Shapes.Path>.  
  
 ![Ilustración de trayecto](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")  
  
 El <xref:System.Windows.Shapes.Path.Data%2A> cadena de atributo empieza con el comando "moveto", indicado por M, que establece un punto de inicio para la ruta de acceso en el sistema de coordenadas de la <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Shapes.Path> parámetros de datos distinguen entre mayúsculas y minúsculas. La M mayúscula indica una ubicación absoluta para el nuevo punto actual. Una m minúscula indica coordenadas relativas. El primer segmento es una curva de Bézier cúbica que comienza en (100,200) y termina en (400,175), trazado con los dos puntos de control (100,25) y (400,350). Este segmento se indica mediante el comando C en el <xref:System.Windows.Shapes.Path.Data%2A> cadena de atributo. De nuevo, la C mayúscula indica una ruta de acceso absoluta; la c minúscula indicaría una ruta de acceso relativa.  
  
 El segundo segmento comienza con un comando H "lineto" horizontal absoluto, que especifica una línea trazada desde el punto de conexión del subtrazado anterior (400,175) hasta un nuevo punto de conexión (280,175). Dado que es un comando "lineto" horizontal, el valor especificado es un *x*-coordinar.  
  
 Para obtener la sintaxis de ruta de acceso completa, consulte la <xref:System.Windows.Shapes.Path.Data%2A> referencia y [crear una forma mediante una clase PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>Pintar formas  
 <xref:System.Windows.Media.Brush> los objetos se utilizan para pintar una forma <xref:System.Windows.Shapes.Shape.Stroke%2A> y <xref:System.Windows.Shapes.Shape.Fill%2A>. En el ejemplo siguiente, el trazo y relleno de un <xref:System.Windows.Shapes.Ellipse> se especifican. Tenga en cuenta que una entrada válida para las propiedades del pincel puede ser una palabra clave o el valor de color en formato hexadecimal. Para obtener más información sobre las palabras clave de color disponibles, vea Propiedades de la <xref:System.Windows.Media.Colors> clase en el <xref:System.Windows.Media> espacio de nombres.  
  
```  
<Canvas Background="LightGray">   
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 La siguiente imagen muestra el representado <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Una elipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Como alternativa, puede usar la sintaxis de elemento de propiedad que para crear explícitamente un <xref:System.Windows.Media.SolidColorBrush> objeto que se va a pintar la forma con un color sólido.  
  
```  
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"   
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 En la ilustración siguiente se muestra la forma representada.  
  
 ![Ilustración de SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 También puede pintar el trazo o relleno de una forma con degradados, imágenes, patrones y mucho más. Para obtener más información, consulte el [pintar con colores sólidos y degradados información general sobre](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>Formas extensibles  
 El <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, y <xref:System.Windows.Shapes.Rectangle> clases tienen una <xref:System.Windows.Shapes.Shape.Stretch%2A> propiedad. Esta propiedad determina cómo un <xref:System.Windows.Shapes.Shape> contenido del objeto (la forma que se dibuje) se expande para rellenar el <xref:System.Windows.Shapes.Shape> espacio de diseño del objeto. A <xref:System.Windows.Shapes.Shape> espacio de diseño del objeto es la cantidad de espacio el <xref:System.Windows.Shapes.Shape> está asignada por el sistema de diseño, debido a uno explícita <xref:System.Windows.FrameworkElement.Width%2A> y <xref:System.Windows.FrameworkElement.Height%2A> configuración o porque su <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> y <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> configuración. Para obtener información adicional sobre el diseño en Windows Presentation Foundation, vea [diseño](../../../../docs/framework/wpf/advanced/layout.md) información general.  
  
 La propiedad Stretch puede tener uno de los siguientes valores:  
  
-   <xref:System.Windows.Media.Stretch.None>: El <xref:System.Windows.Shapes.Shape> no se ajusta el contenido del objeto.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: La <xref:System.Windows.Shapes.Shape> contenido del objeto se expande para rellenar su espacio de diseño.  No se mantiene la relación de aspecto.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: La <xref:System.Windows.Shapes.Shape> contenido del objeto se ajusta tanto como sea posible para rellenar su espacio de diseño al tiempo que conserva su relación de aspecto original.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: La <xref:System.Windows.Shapes.Shape> contenido del objeto se expande para rellenar por completo su espacio de diseño al tiempo que conserva su relación de aspecto original.  
  
 Tenga en cuenta que, cuando un <xref:System.Windows.Shapes.Shape> se ajusta el contenido del objeto, el <xref:System.Windows.Shapes.Shape> se pinta el contorno del objeto después de la ampliación.  
  
 En el ejemplo siguiente, un <xref:System.Windows.Shapes.Polygon> se utiliza para dibujar un triángulo muy pequeño de (0,0) a (0,1) a (1,1). El <xref:System.Windows.Shapes.Polygon> del objeto <xref:System.Windows.FrameworkElement.Width%2A> y <xref:System.Windows.FrameworkElement.Height%2A> se establece en 100, y su propiedad stretch se establece en Fill. Como resultado, la <xref:System.Windows.Shapes.Polygon> contenido del objeto (el triángulo) se expande para rellenar el espacio más grande.  
  
```  
...  
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
...  
```  
  
```  
...  
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
...  
```  
  
<a name="transforms"></a>   
## <a name="transforming-shapes"></a>Transformar formas  
 La <xref:System.Windows.Media.Transform> clase proporciona los medios para transformar las formas en un plano bidimensional.  Los distintos tipos de transformación incluyen la rotación (<xref:System.Windows.Media.RotateTransform>), escala (<xref:System.Windows.Media.ScaleTransform>), el sesgado (<xref:System.Windows.Media.SkewTransform>) y traducción (<xref:System.Windows.Media.TranslateTransform>).  
  
 Una transformación común para aplicar a una forma es la rotación.  Para girar una forma, crear una <xref:System.Windows.Media.RotateTransform> y especifique su <xref:System.Windows.Media.RotateTransform.Angle%2A>. Un <xref:System.Windows.Media.RotateTransform.Angle%2A> de 45 gira el elemento 45 grados de las agujas del reloj; un ángulo de 90 gira el elemento 90 grados a la derecha; y así sucesivamente. Establecer el <xref:System.Windows.Media.RotateTransform.CenterX%2A> y <xref:System.Windows.Media.RotateTransform.CenterY%2A> propiedades si desea controlar el punto sobre el que se gira el elemento. Estos valores de propiedad se expresan en el espacio de coordenadas del elemento que se va a transformar. <xref:System.Windows.Media.RotateTransform.CenterX%2A> y <xref:System.Windows.Media.RotateTransform.CenterY%2A> tienen valores predeterminados de cero. Por último, aplique el <xref:System.Windows.Media.RotateTransform> al elemento. Si no desea que la transformación afecte al diseño, establezca la forma <xref:System.Windows.UIElement.RenderTransform%2A> propiedad.  
  
 En el ejemplo siguiente, un <xref:System.Windows.Media.RotateTransform> se utiliza para girar una forma 45 grados sobre la esquina de la forma superior izquierda (0,0).  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 En el ejemplo siguiente, otra forma se gira 45 grados, pero esta vez se gira alrededor del punto (25,50).  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 En la ilustración siguiente se muestran los resultados de aplicar las dos transformaciones.  
  
 ![Rotaciones de 45 grados con diferentes puntos centrales](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 En los ejemplos anteriores, se aplicó una única transformación a cada objeto de forma. Para aplicar varias transformaciones a una forma (o cualquier otro elemento de interfaz de usuario), utilice un <xref:System.Windows.Media.TransformGroup>.  
  
## <a name="see-also"></a>Vea también  
 [Imágenes y gráficos 2D](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Información general sobre el dibujo con colores sólidos y degradados](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Información general sobre geometría](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Tutorial: Mi primera aplicación de escritorio WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [Información general sobre animaciones](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
