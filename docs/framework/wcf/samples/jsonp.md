---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 9002597ef662c78b6519ab0c04700cddf7ee3714
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804576"
---
# <a name="jsonp"></a>JSONP
En este ejemplo se muestra cómo admitir JSON con relleno (JSONP) en los servicios REST de WCF. JSONP es una convención usada para invocar scripts entre dominios generando las etiquetas de scripts en el documento actual. El resultado se devuelve en una función de devolución de llamada especificada. JSONP se basa en la idea de que etiquetas como `<script src="http://..." >` pueden evaluar los scripts desde cualquier dominio y el script que estas etiquetas recuperan se evalúa dentro de un ámbito en el que ya se pueden definir otras funciones.  
  
## <a name="demonstrates"></a>Demostraciones  
 Scripting a través de dominios con JSONP.  
  
## <a name="discussion"></a>Explicación  
 El ejemplo incluye una página web que agrega dinámicamente un bloque de script una vez representada la página en el explorador. Este bloque de script llama a un servicio REST de WCF que tiene una sola operación: `GetCustomer`. El servicio REST de WCF devuelve el nombre y la dirección de un cliente ajustados en un nombre de función de devolución de llamada. Cuando el servicio REST de WCF responde, se invoca la función de devolución de llamada en la página web con los datos del cliente y la función muestra los datos en la página web. El control ScriptManager de ASP.NET AJAX administra automáticamente la inyección de la etiqueta de script y la ejecución de la función de devolución de llamada. El patrón de uso es igual que el de todos los servidores proxy AJAX de ASP.NET, aunque incorpora una línea para habilitar JSONP, como se muestra en el siguiente código:  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 La página web puede llamar al servicio REST de WCF porque el servicio usa el objeto <xref:System.ServiceModel.Description.WebScriptEndpoint> con `crossDomainScriptAccessEnabled` establecido en `true`. Ambas configuraciones se realizan en el archivo Web.config bajo el \<system.serviceModel > elemento.  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 El ScriptManager administra la interacción con el servicio y oculta la complejidad de la implementación manual del acceso JSONP. Cuando `crossDomainScriptAccessEnabled` está establecido en `true` y el formato de respuesta para una operación es JSON, la infraestructura de WCF inspecciona el URI de la solicitud para un parámetro de cadena de consulta de devolución de llamada y ajusta la respuesta JSON con el valor de la cadena de consulta de devolución de llamada parámetro. En el ejemplo, la página web llama al servicio REST de WCF con el siguiente URI.  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 Dado que el parámetro de cadena de una consulta de devolución de llamada tiene el valor `JsonPCallback`, el servicio WCF devuelve una respuesta JSONP que se muestra en el siguiente ejemplo.  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 Esta respuesta JSONP incluye los datos del cliente con formato JSON, ajustados con el nombre de la función de devolución de llamada que la página web solicitó. El ScriptManager ejecutará esta devolución de llamada utilizando una etiqueta de script para lograr la solicitud a través de los dominios y, a continuación, pasará el resultado al controlador onSuccess que se pasó a la operación GetCustomer del proxy AJAX de ASP.NET.  
  
 El ejemplo consta de dos aplicaciones web ASP.NET: uno contiene simplemente un servicio WCF, y otro contiene la página Web .aspx, que llama al servicio. Al ejecutar la solución, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] hospedará los dos sitios web en puertos diferentes, con lo que se crea un entorno donde el servicio y cliente están en dominios distintos.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Para ejecutar el ejemplo  
  
1.  Abra la solución para obtener el ejemplo de JSONP.  
  
2.  Presione F5 para iniciar `http://localhost:26648/JSONPClientPage.aspx` en el explorador.  
  
3.  Tenga en cuenta que una vez cargada la página, las entradas de texto para "Nombre" y "Dirección" están rellenas con valores.  Estos valores se proporcionaron en una llamada al servicio WCF después de que el explorador terminó de representar la página.
