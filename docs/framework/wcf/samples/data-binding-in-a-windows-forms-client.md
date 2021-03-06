---
title: Enlace de datos en un cliente de Windows Forms
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: 38991390f2d0dd272b8d07041b61e6cf16db0cae
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804383"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Enlace de datos en un cliente de Windows Forms
Este ejemplo muestra cómo enlazar a los datos devueltos por un servicio de Windows Communication Foundation (WCF) en una aplicación de formularios Windows Forms.  
  
> [!NOTE]
>  El procedimiento de configuración y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.  
  
 Este ejemplo muestra un servicio que implementa un contrato que define un patrón de comunicación de solicitud y respuesta. El ejemplo consta de un cliente de aplicación de Windows Forms (.exe) y un servicio WCF hospedado por Internet Information Services (IIS).  
  
 El contrato se define mediante la interfaz `IWeatherService`, que expone una operación denominada `GetWeatherData`. Esta operación acepta una matriz de ciudades y devuelve una matriz de objetos `WeatherData` que representan la temperatura alta y baja prevista para una ciudad.  
  
 El enlace de datos se produce en el cliente de la aplicación de Windows Forms. Un `DataGridView`, se define en el Diseñador de Windows Forms, que es una representación gráfica de los datos.  También se crea un objeto `BindingSource` con nombre intermedio. El origen de datos de `BindingSource` se establece en la matriz de datos que devuelve el servicio. La finalidad de `BindingSource` es proporcionar una capa de direccionamiento indirecto entre los datos y la vista de datos. Toda interacción con los datos, como navegación, ordenación, filtrado y actualización, se lleva a cabo mediante llamadas al componente `BindingSource`. Para lograr el enlace de datos `DataGridView`, el `datasource` del `DataGridView` está establecido en el objeto `BindingSource`. A continuación, todos los datos devueltos desde el servicio WCF se muestra gráficamente al usuario.  Cada vez que el usuario hace clic en el botón, se actualizan los datos devueltos automáticamente en el objeto `DataGridView` enlazado a datos.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Configurar, compilar y ejecutar el ejemplo  
  
1.  Asegúrese de que ha llevado a cabo la [procedimiento de instalación de un solo uso para los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar el código C# o Visual Basic .NET Edition de la solución, siga las instrucciones de [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para ejecutar el ejemplo en una configuración de equipo único o de varios, siga las instrucciones de [ejecutando los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a>Vea también
