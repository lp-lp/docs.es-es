---
title: "C&#243;mo utilizar el proveedor de funciones del administrador de autorizaci&#243;n de ASP.NET con un servicio | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# C&#243;mo utilizar el proveedor de funciones del administrador de autorizaci&#243;n de ASP.NET con un servicio
Cuando [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hospeda un servicio web, se puede integrar el administrador de autorización en la aplicación para autorizar el servicio.  El administrador de autorización permite a los desarrolladores de aplicaciones definir operaciones individuales que, a su vez, pueden agruparse para formar tareas.  Un administrador puede autorizar funciones que realicen tareas específicas u operaciones individuales.  El administrador de autorización proporciona una herramienta de administración, como complemento de Microsoft Management Console \(MMC\), para administrar funciones, tareas, operaciones y usuarios.  Los administradores configuran un almacén de directivas del administrador de autorización en un archivo XML, en Active Directory, o en un almacén de Active Directory Application Mode \(ADAM\).  
  
 El administrador de autorización se integra en la aplicación mediante la configuración del [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proveedor de funciones del administrador de autorización de la aplicación [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] que hospeda el servicio web.  Al igual que otros proveedores de funciones [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], el proveedor de funciones [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] del administrador de autorización se configura mediante el elemento \<`providers`\>.  
  
 El siguiente ejemplo de código forma parte del archivo de configuración de un servicio web que integra el administrador de autorización en la aplicación.  
  
```  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"   
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la integración de un proveedor de funciones de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] con una aplicación [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] consulte [Cómo: Utilizar el proveedor de funciones ASP.NET con un servicio](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] cómo usar el administrador de autorización con [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consulte [Cómo usar el administrador de autorización \(AzMan\) con ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=71303).  
  
## Vea también  
 [Cómo: Utilizar el proveedor de funciones ASP.NET con un servicio](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)