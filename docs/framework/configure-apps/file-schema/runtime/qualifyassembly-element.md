---
title: '&lt;qualifyAssembly&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d08cfbde82f74dcf88ddadd844854bdfeb403935
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754267"
---
# <a name="ltqualifyassemblygt-element"></a>&lt;qualifyAssembly&gt; elemento
Especifica el nombre completo del ensamblado que debe cargarse dinámicamente cuando se utiliza un nombre parcial.  
  
 \<configuration>  
\<en tiempo de ejecución >  
\<assemblyBinding >  
\<qualifyAssembly >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`partialName`|Atributo necesario.<br /><br /> Especifica el nombre parcial del ensamblado tal y como aparece en el código.|  
|`fullName`|Atributo necesario.<br /><br /> Especifica el nombre completo del ensamblado tal y como aparece en la caché global de ensamblados.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`assemblyBinding`|Contiene información sobre la redirección de versiones de ensamblado y las ubicaciones de ensamblados.|  
|`configuration`|Elemento raíz de cada archivo de configuración usado por las aplicaciones de Common Language Runtime y .NET Framework.|  
|`runtime`|Contiene información del enlace del ensamblado y de la recolección de elementos no utilizados.|  
  
## <a name="remarks"></a>Comentarios  
 Llamar a la <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> método utilizando nombres de ensamblado parciales hace common language runtime buscar el ensamblado sólo en el directorio de base de la aplicación. Use la  **\<qualifyAssembly >** elemento en el archivo de configuración de aplicación para proporcionar la información de ensamblado completo (nombre, versión, referencia cultural y token de clave pública) y hacer que common language runtime buscar el ensamblado en la caché global de ensamblados.  
  
 El **fullName** atributo debe incluir los cuatro campos de identidad del ensamblado: nombre, versión, token de clave pública y referencia cultural. El **partialName** atributo parcialmente debe hacer referencia a un ensamblado. Debe especificar al menos el nombre del ensamblado texto (el caso más común), pero también puede incluir versión, token de clave pública, o referencia cultural (o cualquier combinación de las cuatro, pero no los cuatro). El **partialName** debe coincidir con el nombre especificado en la llamada. Por ejemplo, no se puede especificar `"math"` como el **partialName** atributo del archivo de configuración y llame `Assembly.Load("math, Version=3.3.3.3")` en el código.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se convierte de manera lógica la llamada `Assembly.Load("math")` en `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Vea también  
 [Esquema de la configuración de Common Language Runtime](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Cómo el motor en tiempo de ejecución ubica ensamblados](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [NIB: Referencias a ensamblados parciales](http://msdn.microsoft.com/library/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
