---
title: Función GetPropertyQualifierSet (referencia de API no administrada)
description: La función GetPropertyQualifierSet recupera el calificador establecido para una propiedad.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2951733211737f06cd737b20bd1537277be1be1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461482"
---
# <a name="getpropertyqualifierset-function"></a>GetPropertyQualifierSet (función)
Recupera el calificador establecido para una propiedad determinada.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>Parámetros

`vFunc`  
[in] Este parámetro no se utiliza.

`ptr`  
[in] Un puntero a un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instancia.

`wszMethod`  
[in] El nombre de propiedad. `wszProperty` debe apuntar a válido `LPCWSTR`. 

`ppQualSet`  
[out] Recibe el puntero de interfaz que permite el acceso a los calificadores de la propiedad. El valor de `ppQualSet` no puede ser `null`. Si se produce un error, no se devuelve un nuevo objeto y el puntero se establece para que apunte a `null`. 

## <a name="return-value"></a>Valor devuelto

Los siguientes valores devueltos por esta función se definen en el *WbemCli.h* archivo de encabezado, o bien puede definirlas como constantes en el código:

|Constante  |Valor  |Descripción  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0 x 80041001 | Ha habido un error general. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | El método especificado no existe. |
|`WBEM_E_OUT_OF_MEMORY` | 0 x 80041006 | No hay suficiente memoria disponible para completar la operación. |
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un parámetro es `null`. |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | La función intenta obtener calificadores de una propiedad del sistema. |
|`WBEM_S_NO_ERROR` | 0 | La llamada de función tuvo éxito.  |
  
## <a name="remarks"></a>Comentarios

Esta función contiene una llamada a la [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) método. 

Una llamada a esta función solo se admite si el objeto actual es una definición de clase CIM. No está disponible para la manipulación de los métodos [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters que apuntan a las instancias CIM.

Dado que cada método puede tener sus propio calificadores, el [IWbemQualifierSet puntero](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) permite al llamador agregar, editar o eliminar estos calificadores.

Como propiedades del sistema no tengan ningún calificador, la función devuelve `WBEM_E_SYSTEM_PROPERTY` si se intenta obtener un [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) puntero para una propiedad del sistema.

## <a name="requirements"></a>Requisitos  
**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** WMINet_Utils.idl  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Vea también  
[WMI y contadores de rendimiento (referencia de API no administrada)](index.md)
