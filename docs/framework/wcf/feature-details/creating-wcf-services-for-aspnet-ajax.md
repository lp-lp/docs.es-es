---
title: Creación de servicios WCF para AJAX de ASP.NET
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: c2d56380b626cd0eafc178b4db3584883b00a6bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492976"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Creación de servicios WCF para AJAX de ASP.NET
AJAX de ASP.NET de Microsoft le permite crear rápidamente páginas web para que la experiencia del usuario sea más satisfactoria gracias a elementos de la interfaz de usuario más familiares y receptivos. AJAX de ASP.NET proporciona bibliotecas de scripts de cliente que incorporan las tecnologías ECMAScript (JavaScript) y HTML dinámico (DHTML) para varios exploradores, y las integra en la plataforma de desarrollo para servidores de ASP.NET 2.0. Gracias a las características de AJAX de ASP.NET puede mejorar la experiencia del usuario y la eficacia de sus aplicaciones web.  
  
 AJAX de ASP.NET consta de bibliotecas de scripts de cliente y de componentes de servidor que se integran para proporcionar un marco de desarrollo robusto. Para tener acceso a un servicio desde una página ASP.NET: una vez que se agrega la URL de servicio al control del administrador de scripts de ASP.NET en la página, las operaciones de servicio se pueden invocar usando código JavaScript que tiene la misma apariencia que una llamada de función de JavaScript normal. Vea [Obtenga información acerca de ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=186475) sobre el uso de servicios Web en el marco de AJAX.  
  
 La mayoría de los servicios de Windows Communication Foundation (WCF) se pueden exponer como servicio compatible con AJAX de ASP.NET agregando un punto de conexión de AJAX de ASP.NET adecuado.  
  
 Si se utiliza Visual Studio, puede usar una plantilla precompilada para servicios WCF con AJAX habilitado, disponibles en la **Agregar nuevo elemento** cuadro de diálogo cuando se trabaja con sitios Web de ASP.NET o aplicaciones Web.  
  
 Si no está utilizando las plantillas Visual Studio, hay dos maneras de crear un punto de conexión de AJAX de ASP.NET:  
  
-   Cree el punto de conexión utilizando la activación de host dinámica sin utilizar ninguna configuración. Éste es el enfoque más básico si no se está muy familiarizado con el sistema de configuración de WCF. Para obtener más información, consulte [Cómo: agregar un punto de conexión sin configuración uso de AJAX de ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
-   Agregar un punto de conexión con AJAX habilitado a un servicio WCF mediante configuración. Para obtener más información, consulte [Cómo: usar la configuración para agregar un extremo de AJAX de ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
 El modelo de programación Web descrito en el [HTTP Web WCF Programming Model Overview](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) pueden utilizarse con servicios de AJAX de ASP.NET. De manera específica:  
  
-   Puede utilizar los atributos <xref:System.ServiceModel.Web.WebGetAttribute> y <xref:System.ServiceModel.Web.WebInvokeAttribute> para seleccionar entre los verbos HTTP GET y HTTP POST. Si se utiliza correctamente, esto podría mejorar significativamente el rendimiento de la aplicación. Para obtener más información, consulte [Cómo: elegir entre HTTP POST y HTTP GET solicitudes para los extremos de AJAX de ASP.NET](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).  
  
-   Puede usar las propiedades <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> y <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> para que su servicio devuelva datos XML en lugar de hacerlo en el formato Javascript Object Notation (JSON) predeterminado. Si hace esto con el marco de AJAX de ASP.NET, el cliente JavaScript va a recibir un objeto DOM XML.  
  
    > [!WARNING]
    >  La operación debe establecer el tipo de contenido en texto o xml para que funcione. De lo contrario, el cliente JavaScript recibirá una cadena que contiene el XML en vez de un objeto DOM XML.  
  
     A continuación se muestra un ejemplo de una operación que devuelve datos XML con el tipo de contenido establecido adecuadamente:  
  
    ```  
    [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]  
    public XElement GetData()  
    {  
    XElement x;  
    //Get some data here...  
  
    WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";      
    return x;  
    }  
    ```  
  
-   No se pueden cambiar otras propiedades de los atributos de las clases <xref:System.ServiceModel.Web.WebGetAttribute> y <xref:System.ServiceModel.Web.WebInvokeAttribute> si es necesaria la compatibilidad con AJAX de ASP.NET. Se pueden utilizar otros aspectos del modelo de programación web con tal de que no se infrinjan las convenciones de llamada de AJAX de ASP.NET.  
  
 Escenarios más avanzados requieren que se comprendan algunos detalles adicionales de compatibilidad de AJAX de WCF:  
  
-   Para entender cómo se transfieren datos entre un cliente de la página de AJAX y un servicio WCF con JavaScript y para obtener más información sobre cómo se asignan los tipos de .NET Framework en tipos de JavaScript, vea [compatibilidad con JSON y otros formatos de transferencia de datos](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).  
  
-   Para aprovecharse de las características de ASP.NET, como, por ejemplo, la autenticación basada en URL y obtener acceso a la información de sesión de ASP.NET, puede que desee habilitar el modo de compatibilidad de ASP.NET mediante configuración.  
  
 Incluso se pueden utilizar puntos de conexión de AJAX en WCF sin el marco de AJAX de ASP.NET. Si lo hace, es necesario entender la arquitectura de compatibilidad de AJAX en WCF. Para obtener una descripción de esta arquitectura, consulte [modelo de objetos de programación de WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Para obtener un ejemplo de código que muestra este enfoque, consulte el [servicio AJAX con JSON y XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="see-also"></a>Vea también  
 [Modelo de programación de web HTTP de WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Adición de un punto de conexión AJAX de ASP.NET sin usar la configuración](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
 [Uso de la configuración para agregar un punto de conexión AJAX de ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
 [Elección entre solicitudes HTTP POST y HTTP GET para puntos de conexión AJAX de ASP.NET](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
