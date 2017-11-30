---
title: "ICorDebugStepper::StepOut (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepOut
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b3ceca69b6b4710a3f1b8e1e9bdb4baf574119c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut (Método)
Hace que esta ICorDebugStepper paso a paso a través de un subproceso que lo contiene y que finalice cuando el marco actual devuelve el control al marco que realiza la llamada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Comentarios  
 Un `StepOut` operación se completará después de devolver normalmente desde el marco actual al marco que realiza la llamada.  
  
 Si `StepOut` se llama cuando en código no administrado, el paso finalizará cuando el marco actual devuelve el código administrado que lo llamó.  
  
 En la versión 2.0 de .NET Framework, no use `StepOut` con el STOP_UNMANAGED marca conjunto porque se producirá un error. (Use [ICorDebugStepper:: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) para establecer marcadores para la ejecución paso a paso.) Los depuradores de interoperabilidad deben salir del código nativo por sí mismos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]