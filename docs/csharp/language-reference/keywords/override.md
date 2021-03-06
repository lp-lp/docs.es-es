---
title: override (Referencia de C#)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 8f692dfdf8bd34ddb62623d86ec3dadd2b8dead3
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199269"
---
# <a name="override-c-reference"></a>override (Referencia de C#)
El modificador `override` es necesario para ampliar o modificar la implementación abstracta o virtual de un método, propiedad, indexador o evento heredado.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, la clase `Square` debe proporcionar una implementación de invalidación de `Area` porque `Area` se hereda de la clase abstracta `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 Un método `override` proporciona una nueva implementación de un miembro que se hereda de una clase base. El método invalidado por una declaración `override` se conoce como método base invalidado. El método base invalidado debe tener la misma firma que el método `override`. Para obtener información sobre la herencia, vea [Herencia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 No se puede invalidar un método estático o no virtual. El método base invalidado debe ser `virtual`, `abstract` o `override`.  
  
 Una declaración `override` no puede cambiar la accesibilidad del método `virtual`. El método `override` y el método `virtual` deben tener el mismo [modificador de nivel de acceso](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 No se pueden usar los modificadores `new`, `static` o `virtual` para modificar un método `override`.  
  
 Una declaración de propiedad de invalidación debe especificar exactamente el mismo modificador de acceso, tipo y nombre que la propiedad heredada, y la propiedad invalidada debe ser `virtual`, `abstract` o `override`.  
  
 Para obtener más información sobre cómo usar la palabra clave `override`, vea [Control de versiones con las palabras clave Override y New](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) y [Saber cuándo usar las palabras clave Override y New (Guía de programación de C#)](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se define una clase base denominada `Employee` y una clase derivada denominada `SalesEmployee`. La clase `SalesEmployee` incluye una propiedad adicional, `salesbonus`, e invalida el método `CalculatePay` para tenerlo en cuenta.  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a>Especificación del lenguaje C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Referencia de C#](../../../csharp/language-reference/index.md)  
 [Guía de programación de C#](../../../csharp/programming-guide/index.md)  
 [Herencia](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Palabras clave de C#](../../../csharp/language-reference/keywords/index.md)  
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)
