---
title: "Herramienta de contrato primero | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Herramienta de contrato primero
Los contratos de servicio deben crearse a menudo desde servicios existentes.En [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], las clases de contrato de datos se pueden crear automáticamente a partir de servicios existentes mediante la herramienta de contrato primero.Para usar la herramienta de contrato primero, el archivo de definición de esquema XML \(XSD\) se debe descargar localmente; la herramienta no puede importar contratos de datos remotos a través de HTTP.  
  
 La herramienta de contrato primero está integrada en [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] como una tarea de compilación.Los archivos de código generados por la tarea de compilación se crean cada vez que se compila el proyecto, de modo que el proyecto pueda adoptar fácilmente los cambios en el contrato de servicio subyacente.  
  
 Entre los tipos de esquema que la herramienta de contrato primero puede importar se incluyen los siguientes:  
  
```  
<xsd:complexType>  
<xsd:simpleType>  
```  
  
 No se generarán tipos simples si son primitivos como `Int16` o `String`; no se generarán tipos complejos si son de tipo `Collection`.Los tipos tampoco se generarán si forman parte de otro `xsd:complexType`.En todos estos casos, se hará referencia a tipos existentes en el proyecto.  
  
## Agregar un contrato de datos a un proyecto  
 Antes de poder usar la herramienta de contrato primero, el contrato de servicio \(XSD\) se debe agregar al proyecto.En esta información general, se usará el contrato siguiente para mostrar las funciones de contrato primero.Esta definición de servicio es un pequeño subconjunto del contrato de servicio usado por la API de búsqueda de Bing.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="ServiceSchema"  
    targetNamespace="http://tempuri.org/ServiceSchema.xsd"  
    elementFormDefault="qualified"  
    xmlns="http://tempuri.org/ServiceSchema.xsd"  
    xmlns:mstns="http://tempuri.org/ServiceSchema.xsd"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema"  
>  
  <xs:complexType name="SearchRequest">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="1" name="Version" type="xs:string" default="2.2" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Market" type="xs:string" />  
      <xs:element minOccurs="0" maxOccurs="1" name="UILanguage" type="xs:string" />  
      <xs:element minOccurs="1" maxOccurs="1" name="Query" type="xs:string" />  
      <xs:element minOccurs="1" maxOccurs="1" name="AppId" type="xs:string" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Latitude" type="xs:double" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Longitude" type="xs:double" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Radius" type="xs:double" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:simpleType name="WebSearchOption">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="DisableHostCollapsing" />  
      <xs:enumeration value="DisableQueryAlterations" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
  
```  
  
 Para agregar el contrato de servicio anterior al proyecto, haga clic con el botón secundario en el proyecto y seleccione **Agregar nuevo…**.Seleccione Definición de esquema en el panel WCF del cuadro de diálogo Plantillas y asigne al nuevo archivo el nombre SampleContract.xsd.Copie y pegue el código anterior en la vista de código del nuevo archivo.  
  
## Configurar opciones de contrato primero  
 Las opciones de contrato primero se pueden configurar en el menú Propiedades de un proyecto de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].Para habilitar el desarrollo de contrato primero, active la casilla **Habilitar XSD como lenguaje de definición de tipos** en la página WCF de la ventana de propiedades del proyecto.  
  
 ![Opciones del proyecto WCF mostrando contrato primero](../../../docs/framework/wcf/media/contractfirstoptions.png "ContractFirstOptions")  
  
 Para configurar propiedades avanzadas, haga clic en el botón Avanzadas.  
  
 ![Propiedades avanzadas de contrato primero](../../../docs/framework/wcf/media/contractfirstadvanced.png "ContractFirstAdvanced")  
  
 Se pueden configurar las opciones avanzadas siguientes para la generación de código desde contratos.Los valores solo se pueden configurar para todos los archivos del proyecto; no se pueden configurar para archivos individuales en este momento.  
  
-   **Modo de serializador**: este valor determina qué serializador se usa para leer archivos de contrato de servicio.Cuando se selecciona **Serializador XML**, se deshabilitan las opciones **Tipos de colección** y **Volver a usar tipos**.Estas opciones se aplican solo al **Serializador de contrato de datos**.  
  
-   **Volver a usar tipos**: este valor especifica qué bibliotecas se usan para reutilizar tipos.Esta configuración solo se aplica si **Modo de serializador** se establece en **Serializador de contratos de datos**.  
  
-   **Tipo de colección**: este valor especifica el tipo completo o calificado con el nombre del ensamblado que se usará para el tipo de datos de la colección.Esta configuración solo se aplica si **Modo de serializador** se establece en **Serializador de contratos de datos**.  
  
-   **Tipo de diccionario**: este valor especifica el tipo completo o calificado con el nombre del ensamblado que se usará para el tipo de datos de diccionario.  
  
-   **EnableDataBinding**: este valor especifica si se va a implementar la interfaz <xref:System.ComponentModel.INotifyPropertyChanged> en todos los tipos de datos para implementar el enlace de datos.  
  
-   **ExcludedTypes**: este valor especifica la lista de tipos completos o calificados con el nombre del ensamblado que desea excluir de los ensamblados a los que se hace referencia.Esta configuración solo se aplica si **Modo de serializador** se establece en **Serializador de contratos de datos**.  
  
-   **GenerateInternalTypes**: este valor especifica si se van a generar clases marcadas como internas.Esta configuración solo se aplica si **Modo de serializador** se establece en **Serializador de contratos de datos**.  
  
-   **GenerateSerializableTypes**: este valor especifica si se van a generar clases con el atributo <xref:System.SerializableAttribute>.Esta configuración solo se aplica si **Modo de serializador** se establece en **Serializador de contratos de datos**.  
  
-   **ImportXMLTypes**: este valor especifica si se va a configurar el serializador de contrato de datos para aplicar el atributo <xref:System.SerializableAttribute> a clases sin el atributo <xref:System.Runtime.Serialization.DataContractAttribute>.Esta configuración solo se aplica si **Modo de serializador** se establece en **Serializador de contratos de datos**.  
  
-   **SupportFx35TypedDataSets**: este valor especifica si se va a proporcionar funcionalidad adicional para los conjuntos de datos con tipo creados para .Net Framework 3.5.Cuando **Modo de serializador** se establece en **Serializador XML**, la extensión <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> se agregará al importador del esquema XML cuando este valor se establezca en True.Cuando **Modo de serializador** se establece en **Serializador de contrato de datos**, el tipo <xref:System.DateTimeOffset> se excluirá de Referencias cuando este valor se establezca en False, de forma que siempre se genere [DateTimeOffset](assetId:///DateTimeOffset?qualifyHint=False&amp;autoUpgrade=True) para versiones anteriores de .NET Framework.  
  
-   **InputXsdFiles**: este valor especifica la lista de archivos de entrada.Cada archivo debe contener un esquema XML válido.  
  
-   **Language**: este valor especifica el lenguaje del código generado del contrato.El valor debe ser reconocible por <xref:System.CodeDom.Compiler.CodeDomProvider>.  
  
-   **NamespaceMappings**: este valor especifica las asignaciones de los espacios de nombres de destino XSD a espacios de nombres CLR.Cada asignación debe usar el formato siguiente:  
  
    ```xml  
    “<Schema Namespace>, <CLR Namespace>”  
    ```  
  
     El serializador XML solo acepta una asignación en el formato siguiente:  
  
    ```xml  
    “*, <CLR Namespace>”  
    ```  
  
-   **OutputDirectory**: este valor especifica el directorio donde se generarán los archivos de código.  
  
 Los valores se usarán para generar tipos de contrato de servicio a partir de los archivos de contrato de servicio cuando se compile el proyecto.  
  
## Mediante desarrollo de contrato primero  
 Después de agregar el contrato de servicio al proyecto y confirmar la configuración de compilación, compile el proyecto presionando **F6**.Los tipos definidos en el contrato de servicio estarán disponibles para su uso en el proyecto.  
  
 Para usar los tipos definidos en el contrato de servicio, agregue una referencia a `ContractTypes` en el espacio de nombres actual:  
  
```csharp  
using MyProjectNamespace.ContractTypes;  
```  
  
 Los tipos definidos en el contrato de servicio se podrán resolver en el proyecto, como se muestra a continuación.  
  
 ![Usar tipos derivados de un contrato de servicio](../../../docs/framework/wcf/media/contractfirsttypes.png "ContractFirstTypes")  
  
 Los tipos generados por la herramienta se crean en el archivo GeneratedXSDTypes.cs.El archivo se crea en el directorio \<directorio del proyecto\>\/obj\/\<configuración de compilación\>\/XSDGeneratedCode\/ de forma predeterminada.El esquema de ejemplo al principio de este tema se convierte como sigue:  
  
```scr  
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:4.0.30319.17330  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
namespace TestXSD3.ContractTypes  
{  
    using System.Xml.Serialization;  
  
    /// <remarks/>  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]  
    [System.SerializableAttribute()]  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.ComponentModel.DesignerCategoryAttribute("code")]  
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]  
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=true)]  
    public partial class SearchRequest  
    {  
  
        private string versionField;  
  
        private string marketField;  
  
        private string uILanguageField;  
  
        private string queryField;  
  
        private string appIdField;  
  
        private double latitudeField;  
  
        private bool latitudeFieldSpecified;  
  
        private double longitudeField;  
  
        private bool longitudeFieldSpecified;  
  
        private double radiusField;  
  
        private bool radiusFieldSpecified;  
  
        public SearchRequest()  
        {  
            this.versionField = "2.2";  
        }  
  
        /// <remarks/>  
        [System.ComponentModel.DefaultValueAttribute("2.2")]  
        public string Version  
        {  
            get  
            {  
                return this.versionField;  
            }  
            set  
            {  
                this.versionField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string Market  
        {  
            get  
            {  
                return this.marketField;  
            }  
            set  
            {  
                this.marketField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string UILanguage  
        {  
            get  
            {  
                return this.uILanguageField;  
            }  
            set  
            {  
                this.uILanguageField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string Query  
        {  
            get  
            {  
                return this.queryField;  
            }  
            set  
            {  
                this.queryField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string AppId  
        {  
            get  
            {  
                return this.appIdField;  
            }  
            set  
            {  
                this.appIdField = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Latitude  
        {  
            get  
            {  
                return this.latitudeField;  
            }  
            set  
            {  
                this.latitudeField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool LatitudeSpecified  
        {  
            get  
            {  
                return this.latitudeFieldSpecified;  
            }  
            set  
            {  
                this.latitudeFieldSpecified = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Longitude  
        {  
            get  
            {  
                return this.longitudeField;  
            }  
            set  
            {  
                this.longitudeField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool LongitudeSpecified  
        {  
            get  
            {  
                return this.longitudeFieldSpecified;  
            }  
            set  
            {  
                this.longitudeFieldSpecified = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Radius  
        {  
            get  
            {  
                return this.radiusField;  
            }  
            set  
            {  
                this.radiusField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool RadiusSpecified  
        {  
            get  
            {  
                return this.radiusFieldSpecified;  
            }  
            set  
            {  
                this.radiusFieldSpecified = value;  
            }  
        }  
    }  
  
    /// <remarks/>  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]  
    [System.SerializableAttribute()]  
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]  
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=false)]  
    public enum WebSearchOption  
    {  
  
        /// <remarks/>  
        DisableHostCollapsing,  
  
        /// <remarks/>  
        DisableQueryAlterations,  
    }  
}  
  
```  
  
## Errores y advertencias  
 Los errores y advertencias detectados al analizar el esquema XSD aparecerán como errores de compilación y advertencias.  
  
## Herencia de interfaz  
 No es posible usar la herencia de interfaz con el desarrollo de contrato primero; esto es coherente con el modo en el que las interfaces interactúan en otras operaciones.Para usar una interfaz que herede una interfaz base, use dos extremos independientes.El primer extremo usa el contrato heredado y el segundo implementa la interfaz base.