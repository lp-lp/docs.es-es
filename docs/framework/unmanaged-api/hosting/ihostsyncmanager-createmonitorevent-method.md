---
title: IHostSyncManager::CreateMonitorEvent (Método)
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d7cff23fc0b58d316ce19950a982249e84b79ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441957"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a>IHostSyncManager::CreateMonitorEvent (Método)
Crea un objeto de evento de restablecimiento automático supervisado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cookie`  
 [in] Cookie que se va a asociar con el objeto de evento.  
  
 `ppEvent`  
 [out] Un puntero a la dirección de un [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instancia o null si no se pudo crear el objeto de evento.  
  
## <a name="return-value"></a>Valor devuelto  
  
|HRESULT|Descripción|  
|-------------|-----------------|  
|S_OK|`CreateMonitorEvent` se devolvió correctamente.|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) no se han cargado en un proceso o el CLR está en un estado en el que no se puede ejecutar código administrado o procesar la llamada correctamente.|  
|HOST_E_TIMEOUT|La llamada agotó el tiempo de espera.|  
|HOST_E_NOT_OWNER|El llamador no posee el bloqueo.|  
|HOST_E_ABANDONED|Se canceló un evento mientras un subproceso bloqueado o fibra esperó en él.|  
|E_FAIL|Se ha producido un error catastrófico desconocido. Cuando un método devuelve E_FAIL, CLR ya no es utilizable dentro del proceso. Las llamadas posteriores a métodos de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|No había memoria suficiente disponible para crear el objeto de evento solicitado.|  
  
## <a name="remarks"></a>Comentarios  
 `CreateMonitorEvent` Devuelve un `IHostAutoEvent` que CLR usa en su implementación de los recursos administrados <xref:System.Threading.Monitor?displayProperty=nameWithType> tipo. Este método refleja el Win32 `CreateEvent` función, con un valor de `false` especificado para el `bManualReset` parámetro.  
  
 El host puede utilizar la cookie para determinar qué tarea está esperando en el monitor mediante una llamada a la [ICLRSyncManager:: GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** MSCorEE.h  
  
 **Biblioteca:** incluye como recurso en MSCorEE.dll  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ICLRSyncManager (interfaz)](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostAutoEvent (interfaz)](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [IHostSyncManager (interfaz)](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [Monitors](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db) (Clases Monitor)
