---
title: Barra de herramientas (Control, formularios Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: e21b31805eb0b840866313f16cc85ea33c84e515
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537130"
---
# <a name="toolbar-control-windows-forms"></a>Barra de herramientas (Control, formularios Windows Forms)
> [!NOTE]
>  El control <xref:System.Windows.Forms.ToolStrip> reemplaza y agrega funcionalidad al control `ToolBar`; sin embargo, el control `ToolBar` se conserva a efectos de compatibilidad con versiones anteriores y uso futuro, en su caso.  
  
 El control `ToolBar` de Windows Forms se usa en los formularios como una barra de controles que muestra una fila de menús desplegables y botones de mapa de bits que activan comandos. Por lo tanto, hacer clic en un botón de barra de herramientas equivale a elegir un comando de menú. Los botones pueden configurarse para que aparezcan y se comporten como botones de comando, menús desplegables o separadores. Normalmente, una barra de herramientas contiene botones y menús que se corresponden con los elementos de la estructura de menús de una aplicación y proporciona acceso rápido a las funciones y los comandos de una aplicación que se usan con más frecuencia.  
  
> [!NOTE]
>  La propiedad <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> del control `ToolBar` propiedad toma una instancia de la clase <xref:System.Windows.Forms.ContextMenu> como referencia. Tenga en cuenta la referencia que pasa al implementar esta clase de botón en las barras de herramientas de su aplicación, porque la propiedad aceptará cualquier objeto que herede de la clase <xref:System.Windows.Forms.Menu>.  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general del control ToolBar](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 Presenta los conceptos generales del control `ToolBar`, que permite diseñar barras de herramientas personalizadas con las que los usuarios pueden trabajar.  
  
 [Agregar botones a un control ToolBar](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 Describe cómo agregar botones a un control `ToolBar`.  
  
 [Definir un icono para un botón ToolBar](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 Describe cómo mostrar iconos dentro de los botones del control `ToolBar`.  
  
 [Cómo: Desencadenar eventos de menú para los botones de la barra de herramientas](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 Proporciona instrucciones sobre cómo escribir código para interpretar en que botón hace clic el usuario en un control `ToolBar`.  
  
 Consulte también [Cómo: definir un icono para un botón de barra de herramientas mediante el diseñador](http://msdn.microsoft.com/library/ms233659\(v=vs.110\)), [Cómo: agregar botones a un Control de barra de herramientas mediante el diseñador](http://msdn.microsoft.com/library/ms233650\(v=vs.110\)).  
  
## <a name="reference"></a>Referencia  
 Clase <xref:System.Windows.Forms.ToolBar>  
 Contiene información de referencia sobre la clase y sus miembros.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Controles que se usan en Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 Proporciona una lista completa de controles de Windows Forms, con vínculos a información sobre su uso.  
  
 [Control ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 Describe las barras de herramientas que pueden hospedar menús, controles y controles de usuario en aplicaciones de Windows Forms.
