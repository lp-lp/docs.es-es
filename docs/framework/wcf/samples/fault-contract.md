---
title: "Contrato de error | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Contrato de error
El ejemplo de Contrato de error muestra cómo comunicar información de error de un servicio a un cliente.  El ejemplo está basado en [Introducción:](../../../../docs/framework/wcf/samples/getting-started-sample.md), con algún código adicional agregado al servicio para convertir una excepción interna en un error.  El cliente intenta realizar la división por cero para forzar una condición de error en el servicio.  
  
> [!NOTE]
>  El procedimiento de instalación y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.  
  
 El contrato de la calculadora se ha modificado para incluir <xref:System.ServiceModel.FaultContractAttribute> como se muestra en el código muestra siguiente.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 El atributo <xref:System.ServiceModel.FaultContractAttribute> indica que la operación `Divide` puede devolver un error de tipo `MathFault`.  Un error puede ser de cualquier tipo que pueda serializarse.  En este caso, `MathFault` es un contrato de datos, como sigue:  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
  
```  
  
 El método `Divide` produce una excepción <xref:System.ServiceModel.FaultException%601> cuando se fuerza una división por cero como se muestra en el código muestra siguiente.  Esta excepción produce un error que se envía al cliente.  
  
```  
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 El código de cliente fuerza un error solicitando una división por cero.  Al ejecutar el ejemplo, las solicitudes y respuestas de la operación se muestran en la ventana de la consola del cliente.  Se puede ver la división por cero mientras se crea un informe con el error.  Presione ENTRAR en la ventana de cliente para cerrar el cliente.  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 El cliente realiza esta acción y detecta la excepción adecuada`FaultException<MathFault>`:  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 De forma predeterminada, los detalles de excepciones inesperadas no se envían al cliente para evitar que los detalles de la implementación de servicio escapen al límite seguro del servicio.  `FaultContract` proporciona una manera de describir errores en un contrato y de marcar determinados tipos de excepciones como adecuados para la transmisión al cliente.  `FaultException<T>` proporciona el mecanismo en tiempo de ejecución para enviar errores a los consumidores.  
  
 Sin embargo, es útil para ver los detalles internos de un error del servicio al depurar.  Para desactivar el comportamiento seguro previamente descrito, puede indicar que los detalles de cada excepción no controlada en el servidor deberían estar incluidos en el error que se envía al cliente.  Esto se logra estableciendo <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> en `true`.  Puede establecerlo en el código en la configuración, tal y como se muestra en el ejemplo siguiente.  
  
```  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Más allá, el comportamiento debe estar asociado al servicio estableciendo el atributo `behaviorConfiguration` del servicio en el archivo de configuración en "CalculatorServiceBehavior."  
  
 Para detectar tales errores en el cliente, se debe detectar el <xref:System.ServiceModel.FaultException> no genérico.  
  
 Este comportamiento se debería utilizar solo para los propósitos de depuración y no estar habilitado nunca en producción.  
  
### Configurar, compilar y ejecutar el ejemplo  
  
1.  Asegúrese de realizar el procedimiento de [Procedimiento de instalación única para los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar el código C\# o Visual Basic .NET Edition de la solución, siga las instrucciones de [Compilación de los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para ejecutar el ejemplo en una configuración con un único equipo o con varios, siga las instrucciones de [Ejecución de los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo.  Compruebe el siguiente directorio \(predeterminado\) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si no existe este directorio, vaya a la página de [ejemplos de Windows Communication Foundation \(WCF\) y Windows Workflow Foundation \(WF\) Samples para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los ejemplos de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] y [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## Vea también