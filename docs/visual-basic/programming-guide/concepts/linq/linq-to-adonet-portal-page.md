---
title: LINQ to ADO.NET (Página de portal)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 1f8985f6fa86ec906b4495fe15f2936af4270e79
ms.sourcegitcommit: 869b5832b667915ac4a5dd8c86b1109ed26b6c08
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332963"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (Página de portal)
[!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] permite consultar sobre cualquier objeto enumerable de [!INCLUDE[vstecado](~/includes/vstecado-md.md)] mediante el modelo de programación de [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].  
  
> [!NOTE]
>  La documentación de [!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] se encuentra en la sección ADO.NET del SDK de .NET Framework: [LINQ y ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec).  
  
 Existen tres tecnologías [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] de ADO.NET independientes: [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] y [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] proporciona consultas más ricas y optimizadas de <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] permite consultar directamente los esquemas de base de datos de SQL Server y [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] permite consultar un [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> es uno de los componentes más usados de [!INCLUDE[vstecado](~/includes/vstecado-md.md)], además de un elemento clave del modelo de programación desconectado en el que se basa [!INCLUDE[vstecado](~/includes/vstecado-md.md)]. En cambio, a pesar de su importancia, <xref:System.Data.DataSet> tiene funciones de consulta limitadas.  
  
 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] le permite compilar funciones de consulta más complejas en <xref:System.Data.DataSet> mediante la misma función de consulta disponible para muchos otros orígenes de datos.  
  
 Para más información, vea [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] proporciona una infraestructura en tiempo de ejecución para administrar los datos relacionales como objetos. En [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], el modelo de datos de una base de datos relacional se asigna a un modelo de objetos expresado en el lenguaje de programación del desarrollador. Cuando se ejecuta la aplicación, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] convierte a SQL las consultas integradas en el lenguaje en el modelo de objetos y las envía a la base de datos para su ejecución. Cuando la base de datos devuelve los resultados, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] los vuelve a convertir en objetos que se pueden manipular.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] incluye compatibilidad con los procedimientos almacenados y las funciones definidas por el usuario de la base de datos, además de con la herencia en el modelo de objetos.  
  
 Para más información, vea [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 A través de [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)], los datos relacionales se exponen como objetos en el entorno .NET. Esto hace de la capa de objetos un objetivo idóneo para la compatibilidad con [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], ya que permite a los programadores formular consultas en la base de datos con el lenguaje usado para compilar la lógica empresarial. Esta función se conoce como [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. Para más información, vea [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
## <a name="see-also"></a>Vea también  
 [LINQ y ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
