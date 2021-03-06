---
title: Encabezados de dirección
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 276649c17a04822eb27eb4e3ed9cbe711b384edc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803795"
---
# <a name="address-headers"></a>Encabezados de dirección
El ejemplo de encabezados de dirección muestra cómo los clientes pueden pasar parámetros de referencia a un servicio mediante Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  El procedimiento de instalación y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.  
  
 La especificación del direccionamiento del WS define la noción de una referencia del punto de conexión como una manera de direccionar un punto de conexión de servicio Web determinado. En WCF, referencias de extremo se modelan utilizando la `EndpointAddress` class - `EndpointAddress` es el tipo del campo de dirección de la `ServiceEndpoint` clase.  
  
 La parte del modelo de referencia de punto de conexión es que cada referencia puede llevar algunos parámetros de referencia que agregan información de identificación excepcional. En WCF, estos parámetros de referencia se modelan como instancias de `AddressHeader` clase.  
  
 En este ejemplo, el cliente agrega un parámetro de referencia a `EndpointAddress` del extremo del cliente. El servicio busca este parámetro de referencia y utiliza su valor en la lógica de su operación del servicio "Hola".  
  
## <a name="client"></a>Cliente  
 Para que el cliente envíe un parámetro de referencia, debe agregar un `AddressHeader` a `EndpointAddress` de `ServiceEndpoint`. Dado que la clase `EndpointAddress` es inmutable, la modificación de una dirección del extremo se debe hacer utilizando la clase `EndpointAddressBuilder`. El código siguiente inicializa el cliente para enviar un parámetro de referencia como parte de su mensaje.  
  
```csharp   
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 El código crea un `EndpointAddressBuilder` utilizando el `EndpointAddress` original como un valor inicial. Agrega a continuación un encabezado de dirección creado recientemente; la llamada a `CreateAddressHeadercreates` un encabezado con un nombre determinado, espacio de nombres y valor. Aquí el valor es "John." Una vez agregado al generador el encabezado, el método `ToEndpointAddress()` convierte el generador (mutable) en una dirección del extremo (inmutable), la cual está asignada al campo de dirección del extremo del cliente.  
  
 Ahora cuando el cliente llama a `Console.WriteLine(client.Hello());`, el servicio puede obtener el valor de este parámetro de dirección, como se ha visto en el resultado del cliente.  
  
 `Hello, John`  
  
## <a name="server"></a>Servidor  
 La implementación de la operación del servicio`Hello()` utiliza el `OperationContext` actual para inspeccionar los valores de los encabezados en el mensaje entrante.  
  
```csharp   
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 El código produce iteraciones sobre todos los encabezados en el mensaje entrante, buscando encabezados que son parámetros de referencia con el nombre determinado y. Cuando se encuentra el parámetro, lee el valor del parámetro y lo almacena en la variante de "id.".  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Configurar, compilar y ejecutar el ejemplo  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a>Vea también
