---
title: Long (Tipo de datos, Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 687c235be76ef522758658fd1c5fe0cb1dbeb414
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591371"
---
# <a name="long-data-type-visual-basic"></a>Tipo de datos Long (Visual Basic)

Contiene enteros de 64 bits (8 bytes) cuyo valor oscila -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807 con signo (9.2 … E + 18).  
  
## <a name="remarks"></a>Comentarios

 Use la `Long` tipo de datos para que contenga números enteros que son demasiado grandes para caber la `Integer` tipo de datos.  
  
 El valor predeterminado de `Long` es 0.

## <a name="literal-assignments"></a>Asignaciones de literales 

Puede declarar e inicializar un `Long` variable asignarle un decimal literal, un literal hexadecimal, un literal octal, o (a partir de Visual Basic de 2017) un literal binario. Si el literal entero está fuera del intervalo de `Long` (es decir, si es inferior a <xref:System.Int64.MinValue?displayProperty=nameWithType> o mayor que <xref:System.Int64.MaxValue?displayProperty=nameWithType>, se produce un error de compilación.

En el ejemplo siguiente, los enteros que equivalen a 4 294 967 296 que se representan como literales binarios, hexadecimales y decimales se asignan a valores `Long`.
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> Use el prefijo `&h` o `&H` para denotar un literal hexadecimal, el prefijo `&b` o `&B` para denotar un literal binario y el prefijo `&o` o `&O` para denotar un literal octal. Los literales decimales no tienen prefijo.

A partir de Visual Basic de 2017, también puede utilizar el carácter de subrayado, `_`, como un separador de dígitos para mejorar la legibilidad, como en el ejemplo siguiente se muestra.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

A partir de Visual Basic 15,5, también puede utilizar el carácter de subrayado (`_`) como separador inicial entre el prefijo y los dígitos hexadecimales, octales o binarios. Por ejemplo:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

También pueden incluir literales numéricos el `L` [escriba carácter](../../programming-guide\language-features\data-types/type-characters.md) para denotar el `Long` tipo de datos, como se muestra en el ejemplo siguiente.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Sugerencias de programación

-   **Consideraciones de interoperabilidad.** Si interactúa con componentes no se han escrito para .NET Framework, por ejemplo objetos de automatización o COM, recuerde que `Long` tiene un ancho de datos diferente (32 bits) en otros entornos. Al pasar un argumento de 32 bits a esos componentes, declárelo como `Integer` en lugar de `Long` en el código de Visual Basic.  
  
-   **De ampliación.** El `Long` tipo de datos se amplía a `Decimal`, `Single`, o `Double`. Esto significa que puede convertir un tipo de datos `Long` en cualquiera de estos tipos sin que se produzca un error <xref:System.OverflowException?displayProperty=nameWithType>.  
  
-   **Caracteres de tipo.** Al agregar el carácter de tipo literal `L` a un literal, el tipo de datos se convierte forzosamente en el tipo de datos `Long`. Si se agrega el carácter de tipo identificador `&` a cualquier identificador, se convierte forzosamente al tipo `Long`.  
  
-   **Tipo de Framework.** El tipo correspondiente en .NET Framework es la estructura <xref:System.Int64?displayProperty=nameWithType>.  

## <a name="see-also"></a>Vea también

<xref:System.Int64>
[Tipos de datos](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
[Tipo de datos entero](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
[Tipo de datos short](../../../visual-basic/language-reference/data-types/short-data-type.md)   
[Funciones de conversión de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
[Resumen de la conversión](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
[Uso eficiente de tipos de datos](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
