---
title: CorPropertyAttr (Enumeración)
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 263981708af2e40bd3690a3cd344156488eed0dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442684"
---
# <a name="corpropertyattr-enumeration"></a>CorPropertyAttr (Enumeración)
Contiene valores que describen los metadatos de una propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|`prSpecialName`|Especifica que la propiedad es especial, y que su nombre describe cómo.|  
|`prReservedMask`|Reservado para uso interno por common language runtime.|  
|`prRTSpecialName`|Especifica que los metadatos de common language runtime API internas deben comprobar la codificación del nombre de la propiedad.|  
|`prHasDefault`|Especifica que la propiedad tiene un valor predeterminado.|  
|`prUnused`|Sin usar.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorHdr.h  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones para metadatos](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
