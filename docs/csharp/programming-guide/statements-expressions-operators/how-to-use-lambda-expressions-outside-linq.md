---
title: 'Cómo: Usar expresiones lambda fuera de LINQ (Guía de programación de C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: a7b7d25adab7ce1fc777b3bdbe581666ab952413
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959726"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Cómo: Usar expresiones lambda fuera de LINQ (Guía de programación de C#)
Las expresiones lambda no están limitadas a las consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Se pueden usar en cualquier lugar en que se espere un valor de delegado, es decir, dondequiera que se puede usar un método anónimo. En el ejemplo siguiente se muestra cómo usar una expresión lambda en un controlador de eventos de Windows Forms. Observe que los tipos de las entradas (<xref:System.Object> y <xref:System.Windows.Forms.MouseEventArgs>) los deduce el compilador y no tienen que especificarse explícitamente en los parámetros de entrada lambda.  
  
## <a name="example"></a>Ejemplo  
  
```  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Métodos anónimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [LINQ (Language Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
