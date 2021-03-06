---
title: 'Cómo: Utilizar Svcutil.exe para descargar los documentos de metadatos'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: a8872bbf04e688906fb0229e3d8215fb92cdbc3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492403"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Cómo: Utilizar Svcutil.exe para descargar los documentos de metadatos
Puede utilizar Svcutil.exe para descargar metadatos de los servicios en ejecución y para guardar los metadatos en archivos locales. Para los esquemas HTTP y la dirección URL de HTTPS, Svcutil.exe intenta recuperar metadatos mediante WS-MetadataExchange y [detección de servicios Web XML](http://go.microsoft.com/fwlink/?LinkId=94950). Para todos los otros esquemas de URL, Svcutil.exe utiliza sólo WS-MetadataExchange.  
  
 De forma predeterminada, Svcutil.exe utiliza los enlaces definidos en la clase <xref:System.ServiceModel.Description.MetadataExchangeBindings>. Para configurar el enlace utilizado para WS-MetadataExchange, debe definir un extremo de cliente en el archivo de configuración para Svcutil.exe (svcutil.exe.config) que utiliza el contrato `IMetadataExchange` y que tiene el mismo nombre que el esquema del Identificador uniforme de recursos (URI) de la dirección del extremo de metadatos.  
  
> [!CAUTION]
>  Al ejecutar Svcutil.exe para obtener los metadatos de un servicio que expone dos servicios diferentes contratos que cada una contiene una operación con el mismo nombre, Svcutil.exe muestra un error que dice, "No se puede obtener los metadatos de..." Por ejemplo, si tiene un servicio que expone un contrato de servicio denominado ICarService que tiene una operación Get (Car c) y el mismo servicio expone un contrato de servicio denominado IBookService que tiene una operación Get (Book b). Para solucionar este problema, realice una de las operaciones siguientes:  
>   
>  -   Cambie el nombre de una de las operaciones.  
> -   Establezca el <xref:System.ServiceModel.OperationContractAttribute.Name%2A> en un nombre distinto.  
> -   Establezca el espacio de nombres de una de las operaciones en un espacio de nombres distinto mediante la propiedad <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.  
  
### <a name="to-download-metadata-using-svcutilexe"></a>Para descargar metadatos mediante Svcutil.exe  
  
1.  Busque la herramienta Svcutil.exe en la ubicación siguiente:  
  
     C:\Archivos de programa\Microsoft SDKs\Windows\v1.0.\bin  
  
2.  En el símbolo del sistema, inicie la herramienta mediante el formato siguiente.  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Debe especificar la opción `/t:metadata` para descargar los metadatos. De lo contrario, se generan el código de cliente y la configuración.  
  
3.  El <`url`> especifica el argumento de la dirección URL a un extremo de servicio que proporciona metadatos o a un documento de metadatos hospedado en línea. El <`epr`> argumento especifica la ruta de acceso a un archivo XML que contiene un WS-Addressing `EndpointAddress` para un extremo de servicio que admite WS-MetadataExchange.  
  
 Para obtener más opciones sobre cómo usar esta herramienta para su descarga de metadatos, vea [la herramienta de utilidad de metadatos de ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Ejemplo  
 El comando siguiente descarga los documentos de metadatos de un servicio en ejecución.  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Vea también  
 [Herramienta de utilidad de metadatos de ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
