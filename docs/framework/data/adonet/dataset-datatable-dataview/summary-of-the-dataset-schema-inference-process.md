---
title: Resumen del proceso de inferencia del esquema de DataSet
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 9bcc5ce1574eed60d2ef1aa35bdafe8c6050e44c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760276"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>Resumen del proceso de inferencia del esquema de DataSet
El proceso de inferencia determina en primer lugar, a partir del documento XML, qué elementos se inferirán como tablas. A partir del XML restante, el proceso de inferencia determina las columnas para dichas tablas. En el caso de las tablas anidadas, el proceso de inferencia genera objetos <xref:System.Data.DataRelation> y <xref:System.Data.ForeignKeyConstraint> anidados.  
  
 A continuación se resumen brevemente las reglas de inferencia:  
  
-   Los elementos que tienen atributos se deducen como tablas.  
  
-   Los elementos que tienen elementos secundarios se deducen como tablas.  
  
-   Los elementos que se repiten se deducen como una única tabla.  
  
-   Si el elemento de documento, o raíz, no tiene atributos y no se deduciría ningún elemento secundario como una columna, se deduce como un <xref:System.Data.DataSet>. De lo contrario, el elemento de documento se deducirá como una tabla.  
  
-   Los atributos se deducen como columnas.  
  
-   Los elementos que no tienen atributos o elementos secundarios, y que no se repiten, se deducen como columnas.  
  
-   Para los elementos que se deducen como tablas anidadas dentro de otros elementos que también se deducen como tablas, anidada **DataRelation** se crea entre las dos tablas. Una nueva columna de clave principal denominada **TableName_Id** se agrega a ambas tablas y utilizado por el **DataRelation**. A **ForeignKeyConstraint** se crea entre las dos tablas mediante la **TableName_Id** columna.  
  
-   Para los elementos que se deducen como tablas y que contienen texto pero no tengan elementos secundarios, una nueva columna denominada **TableName_Text** se crea para el texto de cada uno de los elementos. Si un elemento se deduce como una tabla y tiene texto, pero también tiene elementos secundarios, se pasa por alto el texto.  
  
## <a name="see-also"></a>Vea también  
 [Inferencia de una estructura relacional de un conjunto de datos a partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Carga de un conjunto de datos desde XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Carga de información del esquema de un conjunto de datos desde XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Usar XML en un conjunto de datos](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Objetos DataSet, DataTable y DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Proveedores administrados de ADO.NET y Centro para desarrolladores de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
