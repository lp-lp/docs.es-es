---
title: 'Ejemplos de sintaxis de consultas basadas en métodos: Combinación (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: e061c5fea0a406169ba9de29d62192dbff6fb7f6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766028"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a>Ejemplos de sintaxis de consultas basadas en métodos: Combinación (LINQ to DataSet)
La combinación es una operación importante de las consultas dirigidas a orígenes de datos que no tienen relaciones navegables entre ellos, como las tablas de bases de datos relacionales. Una combinación de dos orígenes de datos es la asociación de objetos en un origen de datos con objetos que comparten un atributo común en el otro origen de datos. Para obtener más información, consulte [información general sobre operadores de consulta estándar](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 Los ejemplos de este tema muestran cómo usar el método<xref:System.Linq.Enumerable.Join%2A> para consultar <xref:System.Data.DataSet> usando la sintaxis de consulta basada en métodos.  
  
 El `FillDataSet` método que se usa en estos ejemplos se especifica en [cargar datos en un conjunto de datos](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 Los ejemplos de este tema utilizan las tablas Contact, Address, Product, SalesOrderHeader y SalesOrderDetail en la base de datos de ejemplo de AdventureWorks.  
  
 Los ejemplos de este tema usan los siguientes `using` / `Imports` instrucciones:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Para obtener más información, consulte [Cómo: crear un LINQ to DataSet proyecto en Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="join"></a>Join  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se realiza una combinación en las tablas `Contact` y `SalesOrderHeader`.  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se realiza una combinación en las tablas `Contact` y `SalesOrderHeader`, agrupando los resultados por id. de contacto.  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a>Vea también  
 [Carga de datos en un conjunto de datos](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [Ejemplos de LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Información general sobre operadores de consulta estándar](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 [Ejemplos de combinación](http://go.microsoft.com/fwlink/?LinkId=187357)  
 [Ejemplos de conjunto de datos](http://go.microsoft.com/fwlink/?LinkId=187358)
