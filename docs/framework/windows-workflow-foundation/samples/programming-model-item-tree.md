---
title: Programar el árbol de elementos de modelo
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: c5bbbba4f599801c5bffdbd19e14295ff239dfcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516479"
---
# <a name="programming-model-item-tree"></a>Programar el árbol de elementos de modelo
Este ejemplo muestra cómo navegar hasta el <xref:System.Activities.Presentation.Model.ModelItem> árbol utilizando el enlace de datos declarativo de la vista de árbol de Windows Presentation Foundation (WPF).  
  
## <a name="sample-details"></a>Detalles del ejemplo  
 El árbol <xref:System.Activities.Presentation.Model.ModelItem> es la abstracción que usa la infraestructura de [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] para mostrar los datos sobre la instancia subyacente que se está editando. La siguiente ilustración describe los diferentes niveles de infraestructura dentro de [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].  
  
 ![Arquitectura del Diseñador de flujo de trabajo](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")  
  
 Un objeto <xref:System.Activities.Presentation.Model.ModelItem> consta de un puntero al valor subyacente, así como de una colección de objetos <xref:System.Activities.Presentation.Model.ModelProperty>. Un objeto <xref:System.Activities.Presentation.Model.ModelProperty> a su vez consta de datos como el nombre y tipo de la propiedad, y un puntero al valor que, a su vez, es otro objeto <xref:System.Activities.Presentation.Model.ModelItem>. Se utiliza un convertidor de valores para manipular algunos de los objetos <xref:System.Activities.Presentation.Model.ModelItem> que devuelve <xref:System.Activities.Presentation.Model.ModelProperty> para que aparezcan correctamente en la vista de árbol. A continuación, el ejemplo muestra cómo programar de manera imperativa en el árbol <xref:System.Activities.Presentation.Model.ModelItem> utilizando la sintaxis imperativa, tal y como se puede ver en el siguiente ejemplo.  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
```  
  
#### <a name="to-use-this-sample"></a>Para utilizar este ejemplo  
  
1.  Abra la solución ProgrammingModelItemTree.sln en [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Compile la solución seleccionando **generar solución** desde el **generar** menú.  
  
3.  Presione F5 para ejecutar la aplicación. A continuación se muestra el formulario de [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)].  
  
4.  Haga clic en el **Load WF** botón para cargar el <xref:System.Activities.Presentation.Model.ModelItem> y enlazarla a la vista de árbol.  
  
5.  Al hacer clic en el **Change Model Item Tree** botón ejecuta el código anterior para agregar un elemento en el árbol y establecer una propiedad.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Data.IValueConverter>
