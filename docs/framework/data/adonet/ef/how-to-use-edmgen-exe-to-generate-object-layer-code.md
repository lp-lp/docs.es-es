---
title: 'Cómo: Usar EdmGen.exe para generar código de capa de objeto'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: cd919f382096af6ff3e5e27225619767f3922ff0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761095"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Cómo: Usar EdmGen.exe para generar código de capa de objeto
Este tema muestra cómo utilizar el [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) herramienta para generar el código de capa de objeto basados en el archivo CSDL.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Para generar código del nivel de objeto para el modelo School en un proyecto de Visual Basic utilizando EdmGen.exe  
  
1.  Cree la base de datos School. Para obtener más información, consulte [crear la base de datos de ejemplo School](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Genere el modelo School u obtenga el archivo School.csdl. Para obtener más información, consulte [Cómo: usar EdmGen.exe para generar los archivos de asignación y modelo](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  En el símbolo del sistema, ejecute el comando siguiente sin los saltos de línea:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>Para generar código del nivel de objeto para el modelo School en un proyecto de C# utilizando EdmGen.exe  
  
1.  Cree la base de datos School. Para obtener más información, consulte [crear la base de datos de ejemplo School](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Genere el modelo School u obtenga el archivo School.csdl. Para obtener más información, consulte [Cómo: usar EdmGen.exe para generar los archivos de asignación y modelo](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  En el símbolo del sistema, ejecute el comando siguiente sin los saltos de línea:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Modelado y asignación](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Cómo: configurar manualmente un proyecto de Entity Framework](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [Herramientas de Entity Data Model de ADO.NET](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [Cómo: generar previamente las vistas para mejorar el rendimiento de las consultas](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [Uso de EdmGen.exe para generar los archivos de asignación y de modelo](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
