---
title: 'Cómo: Enlazar controles de formularios Windows Forms a valores de base de datos DBNull'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: c8c942b872b23bc6ff0a6f254b952189f9e62dbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530320"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Cómo: Enlazar controles de formularios Windows Forms a valores de base de datos DBNull
Cuando enlaza los controles de Windows Forms a un origen de datos y ese origen devuelve un valor <xref:System.DBNull>, puede sustituir un valor adecuado sin controlar, dar formato o analizar eventos. La propiedad <xref:System.Windows.Forms.Binding.NullValue%2A> convertirá <xref:System.DBNull> en un objeto especificado al dar formato o analizar los valores de origen de datos.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo enlazar un valor <xref:System.DBNull> en dos situaciones diferentes. En la primera se muestra cómo establecer <xref:System.Windows.Forms.Binding.NullValue%2A> para una propiedad de cadena y la segunda muestra cómo establecer <xref:System.Windows.Forms.Binding.NullValue%2A> para una propiedad de imagen.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 Los tipos de la propiedad enlazada y la propiedad <xref:System.Windows.Forms.Binding.NullValue%2A> debe ser iguales. De lo contrario, se producirá un error y no se procesará ningún valor <xref:System.Windows.Forms.Binding.NullValue%2A>. En esta situación, no tendrá lugar ninguna excepción.  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Referencias a los ensamblados System, System.Data, System.Drawing y System.Windows.Forms.  
  
 Para obtener información acerca de cómo compilar este ejemplo desde la línea de comandos de Visual Basic o Visual C#, vea [compilar desde la línea de comandos](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) o [Command-Line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). También puede compilar este ejemplo en Visual Studio pegando el código en un nuevo proyecto.  Consulte también [Cómo: Compilar y ejecutar un ejemplo de código completo de Windows Forms en Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Vea también  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Cómo: Controlar errores y excepciones que se producen con el enlace de datos](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 [Cómo: Enlazar un control de Windows Forms a un tipo](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
