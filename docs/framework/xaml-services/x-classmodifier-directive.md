---
title: x:ClassModifier (Directiva)
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: 67b53a63dbd6e1377d5684d64ed32b0374c84b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564383"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier (Directiva)
Modifica el comportamiento de compilación de XAML cuando `x:Class` también se proporciona. En concreto, en lugar de crear un parcial `class` que tiene un `Public` (valor predeterminado), nivel de acceso proporcionado `x:Class` se crea con un `NotPublic` nivel de acceso. Este comportamiento afecta al nivel de acceso para la clase en los ensamblados generados.  
  
## <a name="xaml-attribute-usage"></a>Uso de atributos XAML  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*NotPublic*|La cadena exacta debe pasar para especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> frente a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varía según el lenguaje de programación de código subyacente que usa. Vea la sección Comentarios.|  
  
## <a name="dependencies"></a>Dependencias  
 [x: Class](../../../docs/framework/xaml-services/x-class-directive.md) también se debe proporcionar en el mismo elemento, y ese elemento debe ser el elemento raíz en una página. Para obtener más información, consulte [ \[MS-XAML\] sección 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Comentarios  
 El valor de `x:ClassModifier` en los servicios XAML de .NET Framework uso varía según el lenguaje de programación. La cadena que se va a utilizar depende de cómo cada lenguaje implementa su <xref:System.CodeDom.Compiler.CodeDomProvider> y los convertidores de tipos que devuelve para definir los significados de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> y <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, y si ese idioma distingue mayúsculas de minúsculas.  
  
-   En C#, la cadena para pasar para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> es `internal`.  
  
-   Para Microsoft Visual Basic. NET, la cadena para pasar para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> es `Friend`.  
  
-   Para [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], ningún destino existe compatibles con la compilación XAML; por lo tanto, el valor para pasar no está especificado.  
  
 También puede especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` en C#, `Public` en Visual Basic); sin embargo, especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> con poca frecuencia se hace así porque <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ya es el comportamiento predeterminado.  
  
 Otros valores con el código de usuario equivalente-nivel de acceso de las restricciones, como `private` en C#, no son relevantes para `x:ClassModifier` porque no se admiten referencias de clase anidada en XAML y por lo tanto, la <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modificador tiene el mismo efecto.  
  
## <a name="security-notes"></a>Notas de seguridad  
 El nivel de acceso, tal y como declara en `x:ClassModifier` sigue estando sujeto a interpretación por marcos determinados y sus capacidades. WPF incluye funciones para cargar y crear instancias de tipos donde `x:ClassModifier` es `internal`, si se hace referencia a esa clase desde un recurso WPF a través de una referencia de URI de paquete. Como consecuencia de este caso y potencialmente otros similares implementado por otros marcos, no debe confiar exclusivamente en `x:ClassModifier` para bloquear la creación de instancias de todas las posibles intentos.  
  
## <a name="see-also"></a>Vea también  
 [x:Class (Directiva)](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Código subyacente y XAML en WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [x:FieldModifier (Directiva)](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [Seguridad (WPF)](../../../docs/framework/wpf/security-wpf.md)  
 [Tipos migrados de WPF a System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
