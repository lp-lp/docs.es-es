---
title: Patrones de controles de UI Automation para clientes
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: d3ec88eb1054c4cc14f01320c85924c9ca346361
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398812"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Patrones de controles de UI Automation para clientes
> [!NOTE]
>  Esta documentación está dirigida a los desarrolladores de .NET Framework que quieran usar las clases [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] administradas definidas en el espacio de nombres <xref:System.Windows.Automation>. Para ver la información más reciente acerca de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: automatización de la interfaz de usuario](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tema es una introducción a los patrones de control para clientes de automatización de la interfaz de usuario. Incluye información que explica cómo un cliente de automatización de la interfaz de usuario puede usar los patrones de control para tener acceso a la información sobre [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 Los patrones de control proporcionan una manera de categorizar y exponer la funcionalidad de un control independientemente de su tipo o apariencia. Los clientes de automatización de la interfaz de usuario pueden examinar un <xref:System.Windows.Automation.AutomationElement> para determinar qué patrones de control son compatibles y estar seguros del comportamiento del control.  
  
 Para obtener una lista completa de los patrones de control, vea [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Obtener patrones de control  
 Los clientes recuperan un patrón de control de un <xref:System.Windows.Automation.AutomationElement> mediante una llamada a <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> o <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Los clientes pueden usar el método <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> o una propiedad `IsPatternAvailable` individual (por ejemplo, <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) para determinar si se admite un patrón o un grupo de patrones en el <xref:System.Windows.Automation.AutomationElement>. Sin embargo, resulta más eficaz intentar obtener el patrón de control y comprobar si hay una referencia `null` que comprobar las propiedades compatibles y recuperar el patrón de control, ya que se generan menos llamadas entre procesos.  
  
 En el siguiente ejemplo se muestra cómo obtener un patrón de control <xref:System.Windows.Automation.TextPattern> de un <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Recuperar propiedades en patrones de control  
 Para recuperar los valores de propiedad en los patrones de control, los clientes pueden llamar a <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> o <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> y convertir el objeto devuelto al tipo apropiado. Para obtener más información sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propiedades, consulte [propiedades de UI Automation para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
 Además de los métodos `GetPropertyValue` , los valores de propiedad se pueden recuperar mediante los descriptores de acceso de [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] para acceder a las propiedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] en un patrón.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Controles con patrones variables  
 Algunos tipos de controles admiten patrones diferentes en función de su estado o de la manera en la que se usan. Algunos ejemplos de controles que pueden tener patrones variables son las vistas de lista (miniaturas, mosaicos, iconos, lista, detalles), los gráficos de [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] (circulares, de líneas, de barras, valores de celda con fórmulas), el área de documento de [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)](Normal, Diseño Web, Esquema, Diseño de impresión, Vista previa de impresión) y las máscaras de [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] .  
  
 Los controles que implementan tipos de controles personalizados pueden tener cualquier conjunto de patrones de control que sea necesario para representar su funcionalidad.  
  
## <a name="see-also"></a>Vea también  
 [Patrones de control de Automatización de la interfaz de usuario](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)  
 [Patrón de texto de Automatización de la interfaz de usuario](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)  
 [Invocación de un control mediante Automatización de la interfaz de usuario](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [Obtención del estado de alternancia de una casilla mediante Automatización de la interfaz de usuario](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [Asignación de patrones de control para clientes de Automatización de la interfaz de usuario](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Ejemplo de texto de inserción de TextPattern](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [Ejemplo de selección y búsqueda de TextPattern](http://msdn.microsoft.com/library/0a3bca57-8b72-489d-a57c-da85b7a22c7f)  
 [Ejemplo de elemento de menú ExpandCollapsePattern y InvokePattern](http://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
