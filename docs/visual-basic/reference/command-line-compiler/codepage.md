---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 383b6adae94c27efdd236de31ddfa8d16a6d4648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648533"
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
Especifica la página de códigos que se va a utilizar para todos los archivos de código fuente en la compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>Argumentos  
  
|Término|Definición|  
|---|---|  
|`id`|Requerido. El compilador utiliza la página de códigos especificada por `id` para interpretar la codificación de los archivos de origen.|  
  
## <a name="remarks"></a>Comentarios  
 Para compilar código fuente guardado con una codificación específica, puede usar `-codepage` para especificar la página de códigos que debe utilizarse. El `-codepage` opción se aplica a todos los archivos de código fuente de la compilación. Para obtener más información, consulte [codificación de caracteres en .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).  
  
 El `-codepage` opción no es necesaria si los archivos de código fuente se guardaron utilizando la página de códigos ANSI actual, Unicode o UTF-8 con una firma. Visual Studio guarda todos los archivos de código fuente con la página de códigos ANSI actual de forma predeterminada, a menos que el usuario especifique otra codificación en el **codificación** cuadro de diálogo. Visual Studio usa el **codificación** cuadro de diálogo para abrir archivos de código fuente guardados con una página de códigos diferente.  
  
> [!NOTE]
>  El `-codepage` opción no está disponible en el entorno de desarrollo de Visual Studio, que está disponible sólo cuando se compila desde la línea de comandos.  
  
## <a name="see-also"></a>Vea también  
 [Compilador de línea de comandos de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
