---
title: 'Cómo: Crear una variable de objeto que no haga referencia a ninguna instancia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: bf918b762261e1dd1fc4161a10203f3d0067e454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649729"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Cómo: Crear una variable de objeto que no haga referencia a ninguna instancia (Visual Basic)
Puede desasociar una variable de objeto de cualquier instancia del objeto si se establece en [nada](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Al desasociar una variable de objeto de cualquier instancia de objeto  
  
-   Establezca la variable en `Nothing` en una instrucción de asignación.  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Programación sólida  
 Si el código intenta obtener acceso a un miembro de una variable de objeto que se ha establecido en `Nothing`, un <xref:System.NullReferenceException> se produce. Si establece una variable de objeto en `Nothing` con frecuencia, o si es posible que no se ha inicializado la variable, es una buena idea incluir accesos a los miembros de un `Try...Catch...Finally` bloque.  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Si usa una variable de objeto para los objetos que contienen datos confidenciales o importantes, puede establecer la variable `Nothing` cuando no activamente tratar con uno de esos objetos. Esto reduce la posibilidad de que código malintencionado obtenga acceso a los datos.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.NullReferenceException>  
 [Variables de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Asignación de variables de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [Try...Catch...Finally (instrucción)](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Solución de problemas de excepciones: System.NullReferenceException](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
