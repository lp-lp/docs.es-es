---
title: public (Referencia de C#)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 9bef5d076d9ab84aa15e2cdec2d176db8d1ac82b
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960249"
---
# <a name="public-c-reference"></a>public (Referencia de C#)
La palabra clave `public` es un modificador de acceso para tipos y miembros de tipo. El acceso público es el nivel de acceso más permisivo. No hay ninguna restricción para el acceso a miembros públicos, como en este ejemplo:  
  
```csharp  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 Vea [Modificadores de acceso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) y [Niveles de accesibilidad](../../../csharp/language-reference/keywords/accessibility-levels.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se declaran dos clases, `PointTest` y `MainClass`. Se obtiene acceso a los miembros públicos `x` e `y` de `PointTest` directamente desde `MainClass`.  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 Si cambia el nivel de acceso `public` a [private](../../../csharp/language-reference/keywords/private.md) o [protected](../../../csharp/language-reference/keywords/protected.md), obtendrá el siguiente mensaje de error:  
  
 'PointTest.y' no es accesible debido a su nivel de protección.  
  
## <a name="c-language-specification"></a>Especificación del lenguaje C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Referencia de C#](../../../csharp/language-reference/index.md)  
 [Guía de programación de C#](../../../csharp/programming-guide/index.md)  
 [Modificadores de acceso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Palabras clave de C#](../../../csharp/language-reference/keywords/index.md)  
 [Modificadores de acceso](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Niveles de accesibilidad](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
