---
title: Seguimiento de eventos en Seguimiento de eventos para Windows
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 82de8ee74c12019f815adc63f2ca4441ad95d325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519511"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a>Seguimiento de eventos en Seguimiento de eventos para Windows
Este ejemplo muestra cómo habilitar el seguimiento en un servicio de flujo de trabajo de Windows Workflow Foundation (WF) y emitir los eventos de seguimiento de eventos de seguimiento para Windows (ETW). Para emitir registros de seguimiento de flujo de trabajo en ETW, el ejemplo utiliza el participante de seguimiento de ETW (<xref:System.Activities.Tracking.EtwTrackingParticipant>).  
  
 El flujo de trabajo del ejemplo recibe una solicitud, asigna el recíproco de los datos de entrada a la variable de entrada y devuelve el recíproco al cliente. Cuando los datos de entrada son 0, se produce una excepción no controlada de división por cero que causa la anulación del flujo de trabajo. Con el seguimiento habilitado, el registro de seguimiento de error se emite a ETW, lo que puede ayudar a solucionar el error posteriormente. El participante de seguimiento de ETW se configura con un perfil de seguimiento para suscribirse a registros de seguimiento. El perfil de seguimiento se define en el archivo Web.config y se proporciona al participante de seguimiento de ETW como un parámetro de configuración. El participante de seguimiento de ETW se configura en el archivo Web.config del servicio de flujo de trabajo y se aplica al servicio como un comportamiento del servicio. En este ejemplo, los eventos de seguimiento del registro de eventos se ven utilizando Visor de eventos.  
  
## <a name="workflow-tracking-details"></a>Detalles del seguimiento del flujo de trabajo  
 Windows Workflow Foundation proporciona una infraestructura de seguimiento para realizar el seguimiento de la ejecución de una instancia de flujo de trabajo. El tiempo de ejecución de seguimiento crea una instancia de flujo de trabajo para emitir eventos relacionados con el ciclo de vida de flujo de trabajo, eventos procedentes de actividades de flujo de trabajo y eventos personalizados. En la siguiente tabla se detallan los componentes primarios de la infraestructura de seguimiento.  
  
|Componente|Descripción|  
|---------------|-----------------|  
|Tiempo de ejecución de seguimiento|Proporciona la infraestructura para emitir registros de seguimiento.|  
|Participantes de seguimiento|Tiene acceso a los registros de seguimiento. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] se distribuye con un participante de seguimiento que escribe los eventos de seguimiento como eventos de Seguimiento de eventos para Windows (ETW).|  
|Perfil de seguimiento|Un mecanismo de filtrado que permite a un participante de seguimiento suscribirse a un subconjunto de los registros de seguimiento emitidos desde una instancia de flujo de trabajo.|  
  
 En la siguiente tabla se detallan los registros de seguimiento que emite el tiempo de ejecución del flujo de trabajo.  
  
|Registro de seguimiento|Descripción|  
|---------------------|-----------------|  
|Registros de seguimiento de instancia de flujo de trabajo.|Describe el ciclo de vida de la instancia de flujo de trabajo. Por ejemplo, se emite un registro de instancia cuando el flujo de trabajo se inicia o se completa.|  
|Registros de seguimiento de estado de actividad.|Describe la ejecución de la actividad. Estos registros indican el estado de una actividad de flujo de trabajo; por ejemplo, cuándo se programa una actividad, cuándo se completa o cuándo se produce un error.|  
|Registro de reanudación de marcadores.|Se emite siempre que se reanude un marcador en una instancia de flujo de trabajo.|  
|Registros de seguimiento personalizados.|Un autor del flujo de trabajo puede crear registros de seguimiento personalizados y emitirlos en la actividad personalizada.|  
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|Este registro se emite cuando una actividad programa otra actividad.|  
|<xref:System.Activities.Tracking.FaultPropagationRecord>|Este registro se emite cuando se propaga un error desde una actividad.|  
|<xref:System.Activities.Tracking.CancelRequestedRecord>|Este registro se emite cuando una actividad es cancelada por otra.|  
  
 El participante de seguimiento se suscribe un subconjunto de los registros de seguimiento emitidos utilizando perfiles de seguimiento. Un perfil de seguimiento contiene consultas de seguimiento que permiten suscribirse a un tipo de registro de seguimiento concreto. Los perfiles de seguimiento se pueden especificar mediante código o en la configuración.  
  
#### <a name="to-use-this-sample"></a>Para utilizar este ejemplo  
  
1.  Abra el archivo de solución EtwTrackingParticipantSample.sln con [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Para compilar la solución, presione Ctrl+MAYÚS+B.  
  
3.  Presione F5 para ejecutar la solución.  
  
     De forma predeterminada, el servicio está escuchando en el puerto 53797 (http://localhost:53797/SampleWorkflowService.xamlx).  
  
4.  Mediante [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], abra el cliente de prueba de WCF.  
  
     El cliente de prueba WCF (WcfTestClient.exe) se encuentra en la \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] carpeta de instalación > \Common7\IDE\ carpeta.  
  
     La carpeta de instalación predeterminada de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] es C:\Archivos de programa\Microsoft Visual Studio 10.0.  
  
5.  En el cliente de prueba WCF, seleccione **Agregar servicio** desde el **archivo** menú.  
  
     Agregue la dirección del punto de conexión en el cuadro de entrada. De manera predeterminada, es http://localhost:53797/SampleWorkflowService.xamlx.  
  
6.  Abra la aplicación Visor de eventos.  
  
     Antes de invocar el servicio, inicie el Visor de eventos desde el **iniciar** menú, seleccione **ejecutar** y escriba en `eventvwr.exe`. Asegúrese de que el registro de eventos escucha eventos de seguimiento emitidos desde el servicio de flujo de trabajo.  
  
7.  En la vista de árbol del Visor de eventos, navegue hasta **Visor de eventos**, **registros de aplicaciones y servicios**, y **Microsoft**. Haga clic en **Microsoft** y seleccione **vista** y, a continuación, **mostrar registros analíticos y depuración** para habilitar los registros analíticos y registros de depuración  
  
     Asegúrese de que el **mostrar registros analíticos y depuración** opción está activada.  
  
8.  En la vista de árbol en el Visor de eventos, navegue hasta **Visor de eventos**, **registros de aplicaciones y servicios**, **Microsoft**, **Windows**,  **Servidor de aplicaciones**. Haga clic en **analítico** y seleccione **Habilitar registro** para habilitar la **analítico** registro.  
  
9. Pruebe el servicio utilizando el cliente de pruebas de WCF haciendo doble clic en `GetData`.  
  
     De este modo, se abrirá el método `GetData`. La solicitud acepta un parámetro y se asegura de que el valor es 0, que es el valor predeterminado.  
  
     Haga clic en **invocar**.  
  
10. Observe los eventos emitidos desde el flujo de trabajo.  
  
     Cambie al Visor de eventos y navegue hasta **Visor de eventos**, **registros de aplicaciones y servicios**, **Microsoft**, **Windows**,  **Servidor de aplicaciones**. Haga clic en **analítico** y seleccione **actualizar**.  
  
     Los eventos de flujo de trabajo se muestran en el Visor de eventos. Observe que se muestran eventos de ejecución de flujo de trabajo y que uno de ellos es una excepción no controlada que se corresponde con el error en el flujo de trabajo. También, se emite un evento de advertencia desde la actividad de flujo de trabajo, que indica que la actividad está produciendo un error.  
  
11. Repita los pasos 9 y 10 con una entrada de datos distinta de 0, para que no se produzca ningún error.  
  
 Los perfiles de seguimiento le permiten suscribirse a eventos emitidos por el tiempo de ejecución cuando cambia el estado de una instancia de flujo de trabajo. Dependiendo de sus requisitos de supervisión, puede crear un perfil muy general, que se suscribe a un conjunto pequeño de cambios de estado de alto nivel en un flujo de trabajo. Por otro lado, puede crear un perfil muy preciso cuyo resultado esté lo suficientemente enriquecido como para poder reconstruir la ejecución posteriormente. En el ejemplo se muestran los eventos emitidos desde el tiempo de ejecución del flujo de trabajo a ETW utilizando `HealthMonitoring Tracking Profile`, que emite un conjunto pequeño de eventos. Con el archivo Web.config, se proporciona también otro perfil que emite más eventos de seguimiento denominado `Troubleshooting Tracking Profile`. Cuando se instala [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], en el archivo Machine.config se configura un perfil predeterminado con un nombre vacío. La configuración de comportamiento de seguimiento de ETW utiliza este perfil cuando no se ha especificado ningún nombre del perfil ni tampoco uno vacío.  
  
 El perfil de seguimiento de supervisión de estado emite registros de instancia de flujo de trabajo y registros de propagación de error de actividad. Este perfil se crea agregando el siguiente perfil de seguimiento a un archivo de configuración Web.config.  
  
```xml  
<<tracking>  
      <profiles>  
        <trackingProfile name="HealthMonitoring Tracking Profile">  
          <workflow activityDefinitionId="*">  
            <workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="Started"/>  
                  <state name="Completed"/>  
                  <state name="Aborted"/>  
                  <state name="UnhandledException"/>  
                </states>  
            </workflowInstanceQuery>  
           </workflowInstanceQueries>  
            <faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
            </faultPropagationQueries>  
          </workflow>  
        </trackingProfile>  
       </profiles>  
</tracking>  
```  
  
 El perfil se puede modificar cambiando la configuración `EtwTrackingParticipant` del siguiente modo.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
#### <a name="to-clean-up-optional"></a>Para realizar la limpieza (Opcional)  
  
1.  Abra el Visor de eventos.  
  
2.  Vaya a **Visor de eventos**, **registros de aplicaciones y servicios**, **Microsoft**, **Windows**, **aplicación Aplicaciones de servidor**. Haga clic en **analítico** y seleccione **Deshabilitar registro**.  
  
3.  Vaya a **Visor de eventos**, **registros de aplicaciones y servicios**, **Microsoft**, **Windows**, **aplicación Aplicaciones de servidor**. Haga clic en **analítico** y seleccione **Vaciar registro**.  
  
4.  Elija la **borrar** opción para borrar los eventos.  
  
## <a name="known-issue"></a>Problema conocido  
  
> [!NOTE]
>  Existe un problema conocido en el Visor de eventos en virtud del cual el visor no puede descodificar eventos de ETW. Es posible que vea un mensaje de error similar el siguiente.  
>   
>  La descripción del Id. de evento \<id > de origen no se puede encontrar aplicaciones de servidor de aplicación de Microsoft Windows. El componente que genera este evento no está instalado en el equipo local, o bien la instalación está dañada. Puede instalar o reparar el componente en el equipo local.  
>   
>  Si encuentra este error, haga clic en actualizar en el panel de acciones. El evento debería descodificarse ahora correctamente.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a>Vea también  
 [Ejemplos de supervisión de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
