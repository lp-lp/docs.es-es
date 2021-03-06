---
title: Anidamiento de TransactionScope dentro de un servicio
ms.date: 03/30/2017
ms.assetid: e7e1ba64-1384-4eba-add8-415636e2d6d0
ms.openlocfilehash: 9c556df417548ab348d1dd5bc642928ae68d8878
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518274"
---
# <a name="nesting-of-transactionscope-within-a-service"></a>Anidamiento de TransactionScope dentro de un servicio
Este ejemplo consiste en la ejecución de dos escenarios para mostrar cómo administrar instancias de actividad <xref:System.Activities.Statements.TransactionScope> dentro de un servicio. En primer lugar, la transacción se inicia utilizando la actividad <xref:System.Activities.Statements.TransactionScope> para crear una transacción en el cliente y <xref:System.ServiceModel.Activities.TransactedReceiveScope> para recibir y determinar la duración de la transacción en el servidor. El primer escenario dentro del servicio ejecuta una actividad <xref:System.Activities.Statements.TransactionScope> secundaria para mostrar el anidamiento de las actividades <xref:System.Activities.Statements.TransactionScope> dentro del servicio. El segundo escenario muestra cómo se respetan los tiempos de espera dentro de las actividades <xref:System.Activities.Statements.TransactionScope> anidadas.  
  
## <a name="client-application"></a>Aplicación de cliente  
 La aplicación cliente ejecuta un flujo de trabajo que inicia una actividad <xref:System.Activities.Statements.TransactionScope>, imprime el Id. de la transacción distribuida, envía un mensaje al servidor, pasa la transacción, recibe la respuesta, imprime de nuevo el Id. de la transacción distribuida y finaliza. Esto lo realiza una vez para cada escenario de servicio.  
  
## <a name="server-application"></a>Servidor de aplicaciones  
 El proyecto de servidor se hospeda en <xref:System.ServiceModel.Activities.WorkflowServiceHost>, que crea el extremo para escuchar el mensaje del cliente. El flujo de trabajo se centra en <xref:System.ServiceModel.Activities.TransactedReceiveScope>, que recibe la transacción de flujo del cliente, imprime el Id. de la transacción distribuida y, a continuación, ejecuta una segunda actividad <xref:System.Activities.Statements.TransactionScope>. En el primer escenario, la transacción se completa correctamente. En el segundo escenario, el cuerpo de la actividad <xref:System.Activities.Statements.TransactionScope> es un retraso de cinco segundos y el tiempo de espera para la transacción se establece en dos segundos. Cuando la transacción supera el tiempo de espera, se anula.  
  
#### <a name="to-run-the-sample"></a>Para ejecutar el ejemplo  
  
1.  Abra la solución TransactionServiceExample.sln en [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Para compilar la solución, presione CTRL + MAYÚS + B o seleccione **generar solución** desde el **generar** menú.  
  
3.  Una vez que la compilación finalice correctamente, haga clic en la solución y seleccione **Establecer proyectos de inicio**. En el cuadro de diálogo, seleccione **proyectos de inicio múltiples** y asegúrese de que la acción para ambos proyectos es **iniciar**.  
  
4.  Presione F5 o seleccione **Iniciar depuración** desde el **depurar** menú. Como alternativa, puede presionar CTRL + F5 o seleccione **iniciar sin depurar** desde el **depurar** menú para ejecutarlo sin depuración.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TRSComposability`
