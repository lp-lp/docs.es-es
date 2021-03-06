---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1906710ef10634187782f9355146dfa7ccb7748
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653408"
---
# <a name="-optioncompare"></a>-optioncompare
Especifica la forma en que se realizan las comparaciones de cadenas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>Comentarios  
 Puede especificar `-optioncompare` en uno de dos formas: `-optioncompare:binary` usar comparaciones de cadenas binarias y `-optioncompare:text` usar comparaciones de cadenas de texto. De forma predeterminada, el compilador utiliza `-optioncompare:binary`.  
  
 En Microsoft Windows, la página de códigos actual determina el criterio de ordenación binario. Un criterio de ordenación binario típico es como sigue:  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Las comparaciones de cadenas basadas en el texto se basan en un criterio de ordenación de texto entre mayúsculas y minúsculas determinado por la configuración regional del sistema. Un criterio de ordenación de texto habitual es como sigue:  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Para establecer - optioncompare en el IDE de Visual Studio  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**. En el menú **Proyecto**, haga clic en **Propiedades**.   
  
2.  Haga clic en la pestaña **Compilar**.  
  
3.  Modifique el valor en el **Option Compare** cuadro.  
  
### <a name="to-set--optioncompare-programmatically"></a>Para establecer - optioncompare mediante programación  
  
-   Vea [Option Compare (instrucción)](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="example"></a>Ejemplo  
 El siguiente código compila `ProjFile.vb` y utiliza comparaciones de cadenas binarias.  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>Vea también  
 [Compilador de línea de comandos de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Líneas de comandos de compilación de ejemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Compare (instrucción)](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Valores predeterminados de Visual Basic, Proyectos, Opciones (Cuadro de diálogo)](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
