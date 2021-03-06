---
title: Función GetObjectText (referencia de API no administrada)
description: La función GetObjectText devuelve una representación textual de un objeto en la sintaxis MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2f0e766a3a310bdb58f7cbffd8d49404eb5e0b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459644"
---
# <a name="getobjecttext-function"></a>GetObjectText (función)
Devuelve una representación textual del objeto en la sintaxis de Managed Object Format (MOF).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>Parámetros

`vFunc`  
[in] Este parámetro no se utiliza.

`ptr`  
[in] Un puntero a un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instancia.

`lFlags`  
[in] Normalmente 0. Si `WBEM_FLAG_NO_FLAVORS` (o 0 x 1) se especifica, se incluyen sin información de propagación o flavor calificadores.

`pstrObjectText`   
[out] Un puntero a un `null` en la entrada. Devuelve un recién asignado `BSTR` que contiene una representación de la sintaxis MOF del objeto.  

## <a name="return-value"></a>Valor devuelto

Los siguientes valores devueltos por esta función se definen en el *WbemCli.h* archivo de encabezado, o bien puede definirlas como constantes en el código:

|Constante  |Valor  |Descripción  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0 x 80041001 | Ha habido un error general. |
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un parámetro no es válido. |
|`WBEM_E_OUT_OF_MEMORY` | 0 x 80041006 | No hay suficiente memoria disponible para completar la operación. |
|`WBEM_S_NO_ERROR` | 0 | La llamada de función tuvo éxito.  |
  
## <a name="remarks"></a>Comentarios

Esta función contiene una llamada a la [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx) método.

El texto MOF devuelto no contiene toda la información sobre el objeto, pero únicamente la información suficiente para que el compilador MOF poder volver a crear el objeto original. Por ejemplo, no propagados calificadores o propiedades de la clase primaria se incluyen.

El siguiente algoritmo se utiliza para reconstruir el texto de los parámetros de un método:

1. Se cambia la secuencia de parámetros en el orden de sus valores de identificador.
1. Parámetros que se especifican como `[in]` y `[out]` se combinan en un solo parámetro.
 
`pstrObjectText` debe ser un puntero a un `null` cuando se llama a la función; no debe apuntar a una cadena que es válida antes de la llamada al método, porque el puntero no se cancela la asignación.

## <a name="requirements"></a>Requisitos  
**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** WMINet_Utils.idl  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Vea también  
[WMI y contadores de rendimiento (referencia de API no administrada)](index.md)
