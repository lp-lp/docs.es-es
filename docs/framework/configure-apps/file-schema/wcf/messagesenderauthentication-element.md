---
title: '&lt;messageSenderAuthentication&gt; (elemento)'
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 898569796c65a7999583f4faba9f11a6172a5af8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750744"
---
# <a name="ltmessagesenderauthenticationgt-element"></a>&lt;messageSenderAuthentication&gt; (elemento)
Especifica las opciones de autenticación para los remitentes del mensaje punto a punto.  
  
 Para obtener más información acerca de la programación de punto a punto, vea [redes Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 \<system.ServiceModel>  
\<comportamientos >  
\<endpointBehaviors >  
\<comportamiento >  
\<clientCredentials >  
\<punto >  
\<messageSenderAuthentication >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|customCertificateValidatorType|Tipo y ensamblado utilizados para validar un tipo personalizado. Se debe establecer este atributo cuando `certificateValidationMode` está establecido en `Custom`.|  
|certifcateValidationMode|Especifica uno de los tres modos utilizados para validar las credenciales. Si se establece en `Custom`, también debe proporcionarse un `customCertificateValidator`.|  
|revocationMode|Uno de los modos utilizados para comprobar listas de certificados revocadas (CRL).|  
|trustedStoreLocation|Una de las dos ubicaciones de almacenamiento del sistema: `LocalMachine` o `CurrentUser`. Se utiliza este valor cuando un certificado del servicio se negocia al cliente. Validación se realiza contra el **personas de confianza** almacenar en la ubicación del almacén especificado.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>Atributo customCertificateValidatorType  
  
|Valor|Descripción|  
|-----------|-----------------|  
|String|Opcional. Especifica el nombre de tipo y el ensamblado y otros datos utilizados para buscar el tipo. Como mínimo, se requieren un espacio de nombres y un nombre de tipo. La información opcionales incluye: nombre de ensamblado, número de versión, referencia cultural y token de clave pública.|  
  
## <a name="certificatevalidationmode-attribute"></a>Atributo certificateValidationMode  
  
|Valor|Descripción|  
|-----------|-----------------|  
|Enumeración|Opcional. Uno de los siguientes valores: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`. De manera predeterminada, es `ChainTrust`. De manera predeterminada, es `ChainTrust`.<br /><br /> Para obtener más información, consulte [trabajar con certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>Atributo revocationMode  
  
|Valor|Descripción|  
|-----------|-----------------|  
|Enumeración|Uno de los siguientes valores: `NoCheck`, `Online`, `Offline`. De manera predeterminada, es `Online`.<br /><br /> Para obtener más información, consulte [trabajar con certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>Atributo trustedStoreLocation  
  
|Valor|Descripción|  
|-----------|-----------------|  
|Enumeración|Uno de los siguientes valores: `LocalMachine` o `CurrentUser`. De manera predeterminada, es `CurrentUser`. Si la aplicación cliente se está ejecutando bajo una cuenta del sistema, entonces el certificado está normalmente bajo `LocalMachine`. Si la aplicación cliente se está ejecutando en una cuenta de usuario, entonces el certificado se encuentra normalmente en `CurrentUser`. De manera predeterminada, es `CurrentUser`.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<punto >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Especifica una credencial utilizada para autenticar el cliente a un servicio del mismo nivel.|  
  
## <a name="remarks"></a>Comentarios  
 Se debe configurar este elemento si se elige la autenticación de mensajes. Para los canales de salida, cada mensaje se firma utilizando el certificado proporcionado por [ \<certificado >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md). Todos los mensajes, antes de ser entregados a la aplicación, se comprueban con la credencial de mensaje utilizando el validador especificado por el atributo `customCertificateValidatorType` de este elemento. El validador puede aceptar o rechazar la credencial.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente establece el modo de validación del remitente del mensaje en `PeerOrChainTrust`.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
      <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
        <messageSenderAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
       <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [Trabajo con certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Conexión de redes punto a punto](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Autenticación de mensajes del canal del mismo nivel](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Canal del mismo nivel de autenticación personalizada](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Protección de las aplicaciones de canal del mismo nivel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
