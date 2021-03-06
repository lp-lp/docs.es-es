---
title: Biblioteca cliente de Data Services de WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 95ca3ab8768b59b52640cfd17d230a544a8b2052
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365519"
---
# <a name="wcf-data-services-client-library"></a>Biblioteca cliente de Data Services de WCF
Cualquier aplicación puede interactuar con un servicio de datos basado en [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] si puede enviar una solicitud HTTP y procesar la fuente de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] que devuelve un servicio de datos. Esta interoperabilidad permite tener acceso a los servicios basados en [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de una amplia gama de aplicaciones habilitadas para web. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] incluye bibliotecas de cliente que proporcionan una experiencia de programación más enriquecida cuando se usan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fuentes de distribución de .NET Framework o aplicaciones basadas en Silverlight.  
  
 Las dos clases principales de la biblioteca cliente son <xref:System.Data.Services.Client.DataServiceContext> y <xref:System.Data.Services.Client.DataServiceQuery%601>. La clase <xref:System.Data.Services.Client.DataServiceContext> encapsula las operaciones admitidas en un servicio de datos determinado. Los servicios de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] carecen de estado, pero no ocurre lo mismo con el contexto. Por lo tanto, puede usar el <xref:System.Data.Services.Client.DataServiceContext> clase para mantener el estado en el cliente entre las interacciones con el servicio de datos para admitir características como la administración de cambios. Esta clase también administra las identidades y realiza el seguimiento de los cambios. La clase <xref:System.Data.Services.Client.DataServiceQuery%601> representa una consulta en un conjunto de entidades concreto.  
  
 En esta sección se describe cómo usar las bibliotecas de cliente para obtener acceso a los datos de una aplicación cliente de .NET Framework y para cambiarlos. Para obtener más información sobre cómo usar el [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliotecas de cliente con una aplicación basada en Silverlight, vea [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016). Existen otras bibliotecas de cliente disponibles que permiten utilizar una [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de la fuente en otros tipos de aplicaciones. Para obtener más información, consulte el [SDK de OData](http://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>En esta sección  
 [Generar la biblioteca cliente del servicio de datos](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 Describe cómo generar una biblioteca de cliente y las clases de servicio de datos de cliente que se basan en [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fuentes de distribución.  
  
 [Consultar el servicio de datos](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 Describe cómo consultar un servicio de datos desde una aplicación basada en .NET Framework usando bibliotecas de cliente.  
  
 [Carga de contenido diferido](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 Describe cómo cargar contenido adicional no incluido en la respuesta de la consulta inicial.  
  
 [Actualización del servicio de datos](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 Describe cómo crear, modificar y eliminar entidades y relaciones usando bibliotecas de cliente.  
  
 [Operaciones asincrónicas](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 Describe los medios proporcionados por las bibliotecas de cliente para trabajar con un servicio de datos de manera asincrónica.  
  
 [Procesamiento por lotes de operaciones](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 Describe cómo enviar varias solicitudes al servicio de datos en un solo lote usando las bibliotecas de cliente.  
  
 [Enlace de datos a los controles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 Describe cómo enlazar controles a un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fuente devuelta por un servicio de datos.  
  
 [Operaciones de servicio de llamada](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 Describe cómo usar la biblioteca de cliente para llamar a operaciones de servicio.  
  
 [Administración del contexto del servicio de datos](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 Describe las opciones para administrar el comportamiento de la biblioteca cliente.  
  
 [Trabajo con datos binarios](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 Describe cómo obtener acceso y cambiar los datos binarios devueltos por el servicio de datos como un flujo de datos.  
  
## <a name="see-also"></a>Vea también  
 [Definir Servicios de datos de WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Introducción](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
