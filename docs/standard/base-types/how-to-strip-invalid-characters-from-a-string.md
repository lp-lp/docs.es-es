---
title: 'Cómo: Quitar caracteres no válidos de una cadena'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66fe5dd1da148e8afd07ae69cec960438b53536a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567359"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Cómo: Quitar caracteres no válidos de una cadena
En el ejemplo siguiente se usa el método estático <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> para quitar caracteres no válidos de una cadena.  
  
## <a name="example"></a>Ejemplo  
 Puede usar el método `CleanInput` definido en este ejemplo para quitar caracteres potencialmente perjudiciales que se hayan escrito en un campo de texto que acepta datos del usuario. En este caso, `CleanInput` elimina todos los caracteres no alfanuméricos excepto puntos (.), símbolos de arroba (@) y guiones (-), y devuelve la cadena restante. Pero puede modificar el patrón de expresión regular para que elimine todos los caracteres que no deban incluirse en una cadena de entrada.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 El patrón de expresión regular `[^\w\.@-]` coincide con cualquier carácter que no sea un carácter de palabra, un punto, un símbolo @ o un guion. Un carácter de palabra es cualquier letra, dígito decimal o conector de puntuación, como un guion bajo. Cualquier carácter que coincida con este patrón se sustituye por <xref:System.String.Empty?displayProperty=nameWithType>, que es la cadena definida por el modelo de reemplazo. Para permitir caracteres adicionales en la entrada de usuario, agregue esos caracteres a la clase de caracteres en el patrón de la expresión regular. Por ejemplo, el patrón de expresión regular `[^\w\.@-\\%]`también permite un símbolo de porcentaje y una barra diagonal inversa en la cadena de entrada.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones regulares de .NET](../../../docs/standard/base-types/regular-expressions.md)
