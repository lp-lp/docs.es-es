---
title: ¿Qué es Windows Communication Foundation?
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: e49b393b9dd09a513066a6cb3612ad9f938e9adb
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807422"
---
# <a name="what-is-windows-communication-foundation"></a>¿Qué es Windows Communication Foundation?
Windows Communication Foundation (WCF) es un marco para generar aplicaciones orientadas a servicios. Usa WCF, puede enviar datos como mensajes asincrónicos de un extremo de servicio a otro. Un extremo de servicio puede formar parte de un servicio disponible continuamente hospedado por IIS, o puede ser un servicio hospedado en una aplicación. Un extremo puede ser un cliente de un servicio que solicita datos de un extremo de servicio. Los mensajes pueden ser tan simples como un carácter o una palabra que se envía como XML, o tan complejos como una secuencia de datos binarios. A continuación se indican unos cuantos escenarios de ejemplo:  
  
-   Un servicio seguro para procesar transacciones comerciales.  
  
-   Un servicio que proporciona datos actualizados a otras personas, como un informe sobre tráfico u otro servicio de supervisión.  
  
-   Un servicio de chat que permite a dos personas comunicarse o intercambiar datos en tiempo real.  
  
-   Una aplicación de panel que sondea los datos de uno o varios servicios y los muestra en una presentación lógica.  
  
-   Exponer un flujo de trabajo implementado utilizando Windows Workflow Foundation como un servicio WCF.  
  
-   Una aplicación de Silverlight para sondear un servicio en busca de las fuentes de datos más recientes.  
  
 Si bien era posible antes de que existiera WCF crear tales aplicaciones, WCF simplifica el desarrollo de los puntos de conexión más fácil que nunca. En resumen, WCF está diseñado para ofrecer un enfoque manejable para la creación de servicios Web y clientes de servicios Web.  
  
## <a name="features-of-wcf"></a>Características de WCF  
 WCF incluye el siguiente conjunto de características. Para obtener más información, consulte [detalles de las características WCF](../../../docs/framework/wcf/feature-details/index.md).  
  
-   **Orientación a servicios**  
  
     Una consecuencia del uso de estándares de WS es que WCF permite crear *orientadas a servicios* aplicaciones. SOA, la arquitectura orientada a servicios es el uso de servicios web para enviar y recibir datos. Los servicios tienen la ventaja general de estar débilmente acoplados entre una aplicación y otra en lugar de incluidos en el código. Una relación de acoplamiento débil implica que cualquier cliente creado en cualquier plataforma puede conectar con cualquier servicio siempre y cuando se cumplan los contratos esenciales.  
  
-   **Interoperabilidad**  
  
     WCF implementa los estándares del sector modernos para la interoperabilidad de servicios Web. Para obtener más información acerca de los estándares admitidos, consulte [interoperabilidad e integración](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md).  
  
-   **Varios patrones de mensajes**  
  
     Los mensajes se intercambian mediante uno de los distintos patrones. El más común es el de solicitud/respuesta, en que un extremo solicita datos de otro extremo. y el otro extremo responde. Existen otros patrones, como un mensaje unidireccional, en que un único extremo envía un mensaje sin esperar ninguna respuesta. Un patrón más complejo es el patrón de intercambio dúplex donde dos extremos establecen una conexión y envían datos hacia delante y hacia atrás, similar a un programa de mensajería instantánea. Para obtener más información sobre cómo implementar el intercambio de mensajes diferentes patrones de uso de WCF vea [contratos](../../../docs/framework/wcf/feature-details/contracts.md).  
  
-   **Metadatos de servicios**  
  
     WCF admite la publicación de servicio de metadatos utilizando los formatos especificados en los estándares del sector, como WSDL, esquemas XML y WS-Policy. Estos metadatos pueden utilizarse para generar y configurar automáticamente clientes para tener acceso a los servicios de WCF. Los metadatos se pueden publicar sobre HTTP y HTTPS, o utilizando el estándar Intercambio de metadatos de servicios web. Para obtener más información, consulte [metadatos](../../../docs/framework/wcf/feature-details/metadata.md).  
  
-   **Contratos de datos**  
  
     Dado que WCF se compila utilizando el [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], también incluye métodos con código sencillo para proporcionar los contratos que desea aplicar. Uno de los tipos de contrato universales es el contrato de datos. Básicamente, mientras se escribe el código del servicio usando Visual C# o Visual Basic, la forma más sencilla de controlar los datos consiste en crear clases que representan una entidad de datos con propiedades que pertenecen a la misma. WCF incluye un completo sistema para trabajar con datos de esta manera fácil. Cuando se han creado las clases que representan los datos, el servicio genera automáticamente los metadatos que permiten a los clientes ajustarse a los tipos de datos que se han diseñado. Para obtener más información, vea [usar contratos de datos](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
  
-   **Seguridad**  
  
     Es posible cifrar los mensajes para proteger la privacidad, así como obligar a los usuarios a que se autentiquen antes de permitirles recibir mensajes. La seguridad puede implementarse utilizando estándares conocidos como SSL o WS-SecureConversation. Para más información, consulte [Seguridad](../../../docs/framework/wcf/feature-details/security.md).  
  
-   **Varios transportes y codificaciones**  
  
     Los mensajes pueden enviarse con cualquiera de los protocolos y codificaciones integrados. Cuanto más frecuente de protocolo y codificación consiste en enviar texto codificado mensajes SOAP mediante el protocolo de transferencia de hipertexto (HTTP) para su uso en World Wide Web. Como alternativa, WCF le permite enviar mensajes a través de TCP, denominado canalizaciones o MSMQ. Estos mensajes pueden codificarse como texto o utilizando un formato binario optimizado.  Los datos binarios pueden enviarse de manera eficaz utilizando el estándar MTOM. Si ninguno de los transportes o codificaciones proporcionados satisface sus necesidades, puede crear uno personalizado. Para obtener más información acerca de los transportes y codificaciones admitidos por WCF vea [transportes](../../../docs/framework/wcf/feature-details/transports.md).  
  
-   **Mensajes confiables y en cola**  
  
     WCF admite intercambio de mensajes confiable usando sesiones confiables implementadas sobre mensajería WS-Reliable y mediante MSMQ. Para obtener más información sobre la compatibilidad de mensajería confiable y en cola en WCF, vea [colas y sesiones confiables](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).  
  
-   **Mensajes duraderos**  
  
     Un mensaje duradero es aquel que nunca se pierde debido a una interrupción de la comunicación. Los mensajes que forman parte de un patrón de mensajes duraderos siempre se guardan en una base de datos. Si se produce una interrupción, la base de datos le permite reanudar el intercambio de mensajes cuando se restablezca la conexión. También puede crear un mensaje duradero utilizando Windows Workflow Foundation (WF). Para obtener más información, consulte [servicios de flujo de trabajo](../../../docs/framework/wcf/feature-details/workflow-services.md).  
  
-   **Transacciones**  
  
     WCF también admite las transacciones que usan uno de los tres modelos de transacción: las transacciones WS-Atomic, las API del espacio de nombres <xref:System.Transactions> y Coordinador de transacciones distribuidas de Microsoft. Para obtener más información acerca de la transacción en WCF vea [transacciones](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md).  
  
-   **Compatibilidad con AJAX y REST**  
  
     REST es un ejemplo de una tecnología de la Web 2.0 en evolución. WCF se puede configurar para procesar datos XML "sin formato" que no se ajustan en un sobre SOAP. WCF también se puede extender para admitir formatos XML concretos, como ATOM (un estándar popular de RSS) e incluso formatos no XML, como JavaScript Object Notation (JSON).  
  
-   **Extensibilidad**  
  
     La arquitectura WCF tiene un número de puntos de extensibilidad. Si se necesita una función adicional, existen una serie de puntos de entrada que le permiten personalizar el comportamiento de un servicio. Para obtener más información sobre la extensibilidad disponible puntos, consulte [extensión de WCF](../../../docs/framework/wcf/extending/index.md).  
  
## <a name="wcf-integration-with-other-microsoft-technologies"></a>Integración de WCF con otras tecnologías de Microsoft  
 WCF es una plataforma flexible. Debido a esta flexibilidad extrema, WCF también se utiliza en varios otros productos de Microsoft. Si comprende los fundamentos de WCF, tendrá una ventaja inmediata si también utiliza cualquiera de estos productos.  
  
 La primera tecnología en adaptarse a WCF fue Windows Workflow Foundation (WF). Los flujos de trabajo simplifican el desarrollo de aplicaciones encapsulando los pasos del flujo de trabajo como "actividades". En la primera versión de Windows Workflow Foundation, un desarrollador tenía que crear un host para el flujo de trabajo. La próxima versión de Windows Workflow Foundation se integró con WCF. Esto permitió hospedar fácilmente en un servicio WCF; cualquier flujo de trabajo Puede hacerlo eligiendo WF/WCF automáticamente un tipo de proyecto en [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
 Microsoft BizTalk Server R2 también utiliza WCF como tecnología de comunicaciones. BizTalk está diseñado para recibir y transformar datos de un formato normalizado en otro. Los mensajes deben entregarse en su cuadro de mensajes central, donde es posible transformar el mensaje utilizando una asignación estricta o mediante una de las características de BizTalk, como su motor de flujo de trabajo. BizTalk ahora puede usar el adaptador de WCF línea de negocio (LOB) para entregar mensajes en el cuadro de mensaje.  
  
 Microsoft Silverlight es una plataforma para la creación de sofisticadas aplicaciones web interoperables que permiten a los desarrolladores crear sitios Web con uso intensivo de contenidos multimedia (como la transmisión de vídeo por secuencias). A partir de la versión 2, Silverlight incorpora WCF como tecnología de comunicaciones para conectar las aplicaciones de Silverlight a extremos WCF.  
  
 El [!INCLUDE[dublin](../../../includes/dublin-md.md)] servidor de aplicaciones se ha diseñado específicamente para implementar y administrar las aplicaciones que usan WCF para comunicarse. El [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] incluye sofisticadas opciones de configuración y herramientas diseñadas específicamente para aplicaciones habilitadas para WCF.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel>  
 [Conceptos básicos de Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)  
 [Arquitectura de Windows Communication Foundation](../../../docs/framework/wcf/architecture.md)  
 [Instrucciones y procedimientos recomendados](../../../docs/framework/wcf/guidelines-and-best-practices.md)  
 [Tutorial de introducción](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Guía de la documentación](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Programación básica de WCF](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Ejemplos de Windows Communication Foundation](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
