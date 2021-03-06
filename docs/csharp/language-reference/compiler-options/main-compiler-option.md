---
title: -main (Opciones del compilador de C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 2df02200578979f9a613f43dc92cc9e7b0cb430e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212425"
---
# <a name="-main-c-compiler-options"></a>-main (Opciones del compilador de C#)
Esta opción especifica la clase que contiene el punto de entrada al programa si hay más de una clase que contenga un método **Main**.  
  
## <a name="syntax"></a>Sintaxis  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Argumentos  
 `class`  
 Tipo que contiene el método **Main**.  
  
## <a name="remarks"></a>Comentarios  
 Si la compilación incluye más de un tipo con un método [Main](../../../csharp/programming-guide/main-and-command-args/index.md), puede especificar el tipo que contiene el método **Main** que quiere usar como punto de entrada en el programa.  
  
 Esta opción se usa al compilar un archivo .exe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra la página **Propiedades** del proyecto.  
  
2.  Haga clic en la página de propiedades **Aplicación**.  
  
3.  Modifique la propiedad **Objeto de inicio**.  
  
     Para establecer esta opción del compilador mediante programación, vea <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
## <a name="example"></a>Ejemplo  
 Compile `t2.cs` y `t3.cs` y especifique que el método **Main** se encuentra en `Test2`:  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Administrar propiedades de soluciones y proyectos](/visualstudio/ide/managing-project-and-solution-properties)
