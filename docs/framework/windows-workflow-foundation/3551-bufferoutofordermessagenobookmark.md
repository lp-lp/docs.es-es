---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 89643edde5856688c762b0cf0d188bd4e7ba8a24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512237"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a>3551 - BufferOutOfOrderMessageNoBookmark
## <a name="properties"></a>Propiedades  
  
|||  
|-|-|  
|Id.|3551|  
|Palabras clave|WFServices|  
|Nivel|Información|  
|Canal|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Descripción  
 Indica que se ha producido un error en la reanudación de marcador. La operación de recepción almacenada en búfer se intentará de nuevo cuando la instancia del servicio esté lista para procesar esta operación en particular.  
  
## <a name="message"></a>Mensaje  
 La operación '%2' en la instancia del servicio '%1' no se puede realizar en este momento. Se intentará de nuevo cuando la instancia del servicio esté lista para procesar esta operación en particular.  
  
## <a name="details"></a>Detalles  
  
|Nombre del elemento de datos|Tipo del elemento de datos|Descripción|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:string|Nombre de la operación.|  
|ServiceInstanceId|xs:string|Identificador de la instancia del servicio.|  
|AppDomain|xs:string|La cadena devuelta por AppDomain.CurrentDomain.FriendlyName.|
