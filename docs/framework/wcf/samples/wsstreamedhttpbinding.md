---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: b0a4c316957a002f7541d230f96299e3f43ef778
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807181"
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
El ejemplo muestra cómo crear un enlace diseñado para admitir escenarios de transmisión por secuencias cuando se usa el transporte HTTP.  
  
> [!NOTE]
>  El procedimiento de instalación y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 Los pasos para crear y configurar un nuevo enlace estándar son como sigue.  
  
1.  Crear un nuevo enlace estándar  
  
     Los enlaces estándar en Windows Communication Foundation (WCF), como basicHttpBinding y netTcpBinding configuran los transportes subyacentes y la pila de canal para los requisitos específicos. En este ejemplo, `WSStreamedHttpBinding` configura la pila del canal para permitir el vertido. De forma predeterminada, la seguridad del WS y la mensajería de confianza no se agregan a la pila del canal porque ambas características no se admiten en el vertido. El nuevo enlace se implementa en la clase `WSStreamedHttpBinding` que deriva de <xref:System.ServiceModel.Channels.Binding>. El `WSStreamedHttpBinding` contiene los siguientes elementos de enlace: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, y <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. La clase proporciona un método `CreateBindingElements()` para configurar la pila de enlace resultante, como se muestra en el código muestra siguiente.  
  
    ```  
    public override BindingElementCollection CreateBindingElements()  
    {  
         // return collection of BindingElements  
         BindingElementCollection bindingElements = new BindingElementCollection();  
  
        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by  
        // the message encoder, and finally the transport at the end  
        if (flowTransactions)  
        {  
            bindingElements.Add(transactionFlow);  
        }  
        bindingElements.Add(textEncoding);  
  
        // add transport (http or https)  
        bindingElements.Add(transport);  
        return bindingElements.Clone();  
    }  
    ```  
  
2.  Añadir la compatibilidad de configuración  
  
     Para exponer el transporte a través de la configuración, el ejemplo implementa dos clases más, `WSStreamedHttpBindingConfigurationElement` y `WSStreamedHttpBindingSection`. La clase `WSStreamedHttpBindingSection` es un <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> que expone `WSStreamedHttpBinding` en el sistema de configuración de WCF. El volumen de la implementación se delega a `WSStreamedHttpBindingConfigurationElement`, lo cual deriva de <xref:System.ServiceModel.Configuration.StandardBindingElement>. La clase `WSStreamedHttpBindingConfigurationElement` tiene propiedades que corresponden a las propiedades de `WSStreamedHttpBinding`y funciones para asignar cada elemento de configuración a un enlace.  
  
     Registre este controlador con el sistema de configuración, agregando la siguiente sección al archivo de configuración pertinente.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <extensions>  
          <bindingExtensions>  
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </bindingExtensions>  
        </extensions>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     A continuación, se puede hacer referencia al controlador desde la sección de configuración de serviceModel.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint  
                    address="https://localhost/servicemodelsamples/service.svc"  
                    bindingConfiguration="Binding"  
                    binding="wsStreamedHttpBinding"  
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Configurar, compilar y ejecutar el ejemplo  
  
1.  Instale [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 mediante el siguiente comando.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Asegúrese de que ha llevado a cabo los pasos enumerados en [procedimiento de instalación de un solo uso para los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Asegúrese de que ha llevado a cabo la [instrucciones de instalación de certificado de servidor de Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4.  Para compilar la solución, siga las instrucciones que aparecen en [compilar los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Para ejecutar el ejemplo en una configuración de varios equipos, siga las instrucciones de [ejecutando los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
6.  Cuando se muestre la ventana de cliente, escriba "Sample.txt." Debería encontrar una "Copy of Sample.txt" en su directorio.  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>Servicio de muestra WSStreamedHttpBinding   
 El servicio del ejemplo que utiliza `WSStreamedHttpBinding` se encuentra en el subdirectorio del servicio. La implementación de `OperationContract` utiliza `MemoryStream` para recuperar primero todos los datos de la secuencia de entrada antes de devolver `MemoryStream`. El servicio de muestra está hospedado en Internet Information Services (IIS).  
  
```  
[ServiceContract]  
public interface IStreamedEchoService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
}  
  
public class StreamedEchoService : IStreamedEchoService  
{  
    public Stream Echo(Stream data)  
    {  
        MemoryStream dataStorage = new MemoryStream();  
        byte[] byteArray = new byte[8192];  
        int bytesRead = data.Read(byteArray, 0, 8192);  
        while (bytesRead > 0)  
        {  
            dataStorage.Write(byteArray, 0, bytesRead);  
            bytesRead = data.Read(byteArray, 0, 8192);  
        }  
        data.Close();  
        dataStorage.Seek(0, SeekOrigin.Begin);  
  
        return dataStorage;  
    }  
}  
```  
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a>Cliente de muestra WSStreamedHttpBinding   
 El cliente que se utiliza para interactuar con el servicio mediante `WSStreamedHttpBinding` se encuentra en el subdirectorio del cliente. Dado que el certificado utilizado en este ejemplo es un certificado de prueba creado con Makecert.exe, una alerta de seguridad se muestra cuando se intenta acceder a una dirección HTTPS en el explorador como https://localhost/servicemodelsamples/service.svc. Para permitir que el cliente de WCF para que funcione con un certificado de prueba en su lugar, se ha añadido código adicional al cliente para suprimir la alerta de seguridad. El código y la clase que lo acompaña no son necesarios cuando se usan certificados de producción.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
## <a name="see-also"></a>Vea también
