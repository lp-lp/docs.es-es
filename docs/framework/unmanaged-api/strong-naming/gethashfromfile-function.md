---
title: GetHashFromFile (Función)
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f98f888280090bfa613acf6ae37bc60ab63c371e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456519"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile (Función)
Genera un hash sobre el contenido del archivo especificado.  
  
 Esta función está desusada. Use la [ICLRStrongName:: GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) método en su lugar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `szFilePath`  
 [in] El nombre del archivo para el hash.  
  
 `piHashAlg`  
 [entrada, salida] El algoritmo que se utilizará al generar el código hash. Los algoritmos válidos son los definidos por CryptoAPI de Win32. Si `piHashAlg` se establece en 0, el algoritmo predeterminado CALG_SHA-1 se utiliza.  
  
 `pbHash`  
 [out] Una matriz de bytes que contiene el código hash generado.  
  
 `cchHash`  
 [in] El tamaño máximo del búfer que `pbHash` apunta a.  
  
 `pchHash`  
 [out] El tamaño, en bytes, del devuelto `pbHash`.  
  
## <a name="remarks"></a>Comentarios  
 Esta función es el mismo que [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), salvo que la especificación del nombre de archivo es ANSI en lugar de Unicode.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** StrongName.h  
  
 **Biblioteca:** incluye como recurso en MsCorEE.dll  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [GetHashFromFile (método)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [GetHashFromFileW (método)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [ICLRStrongName (interfaz)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
