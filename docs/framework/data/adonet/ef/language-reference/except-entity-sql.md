---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: fb7f8040e9e310798b003ad02614cd464e996389
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760211"
---
# <a name="except-entity-sql"></a>EXCEPT (Entity SQL)
Devuelve una colección de los valores distintos de la expresión de consulta situada a la izquierda del operando EXCEPT, que tampoco se devuelven en la expresión de consulta situada a la derecha del operando EXCEPT. Todas las expresiones deben ser del mismo tipo que `expression`o de un tipo base común o derivado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Argumentos  
 `expression`  
 Cualquier expresión de consulta válida que devuelva una colección para comparar con la colección que devuelve otra expresión de consulta.  
  
## <a name="return-value"></a>Valor devuelto  
 Colección del mismo tipo que `expression`o de un tipo base común o derivado.  
  
## <a name="remarks"></a>Comentarios  
 EXCEPT es uno de los operadores de conjuntos de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Todos los operadores de conjuntos de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se evalúan de izquierda a derecha. En la tabla siguiente se muestra la prioridad de los operadores de conjuntos de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
|Precedencia|Operadores|  
|----------------|---------------|  
|Máxima|INTERSECT|  
||UNION<br /><br /> UNION ALL|  
||EXCEPT|  
|Mínima|EXISTS<br /><br /> OVERLAPS<br /><br /> FLATTEN<br /><br /> SET|  
  
## <a name="example"></a>Ejemplo  
 La siguiente consulta de Entity SQL usa el operador EXCEPT para devolver una colección de valores distintos de dos expresiones de consulta. La consulta se basa en el modelo AdventureWorks Sales. Para compilar y ejecutar esta consulta, siga estos pasos:  
  
1.  Siga el procedimiento de [Cómo: Ejecutar una consulta que devuelve resultados StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Pase la consulta siguiente como argumento al método `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a>Vea también  
 [Referencia de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
