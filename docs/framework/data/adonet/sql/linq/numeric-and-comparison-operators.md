---
title: Operadores numéricos y de comparación
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: a1ce13225d72b4286982434d52998a1913814abb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352186"
---
# <a name="numeric-and-comparison-operators"></a>Operadores numéricos y de comparación
Los operadores aritméticos y de comparación funcionan como cabía esperar en Common Language Runtime (CLR), con las siguientes excepciones:  
  
-   SQL no admite al operador de módulo en números de punto flotante.  
  
-   SQL no admite la aritmética no comprobada.  
  
-   Los operadores de incremento y decremento producen efectos no deseados cuando se utilizan en expresiones que no se pueden replicar en SQL y son, por tanto, incompatibles.  
  
## <a name="supported-operators"></a>Operadores compatibles  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] admite los operadores siguientes.  
  
-   Operadores aritméticos básicos:  
  
    -   `+`  
  
    -   `-` (resta)  
  
    -   `*`  
  
    -   `/`  
  
    -   División de enteros en Visual Basic (`\`)  
  
    -   `%` (Visual Basic `Mod`)  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` (negación unaria)  
  
-   Operadores de comparación básicos:  
  
    -   `=` en Visual Basic y `==` en C#  
  
    -   `<>` en Visual Basic y `!=` en C#  
  
    -   `Is/IsNot` en Visual Basic  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a>Vea también  
 [Tipos de datos y funciones](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [Operadores de C#](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [Operadores](../../../../../visual-basic/language-reference/operators/index.md)
