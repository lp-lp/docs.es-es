---
title: 'Cómo: Crear un participante de persistencia personalizado'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: fcd96e41d8fc7b36f9dff5f10e9bc2d9034d79b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517246"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Cómo: Crear un participante de persistencia personalizado
El siguiente procedimiento describe los pasos para crear un participante de persistencia. Consulte la [participa en la persistencia](http://go.microsoft.com/fwlink/?LinkID=177735) ejemplo y [extensibilidad del almacén](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) tema para las implementaciones de ejemplo de participantes de persistencia.  
  
1.  Cree una clase que derive de la clase <xref:System.Activities.Persistence.PersistenceParticipant> o <xref:System.Activities.Persistence.PersistenceIOParticipant>. La clase PersistenceIOParticipant proporciona los mismos puntos de extensibilidad que la clase PersistenceParticipant además de poder participar en operaciones de E/S. Siga uno o varios de los pasos siguientes:  
  
2.  Implemente el método <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A>. El **CollectValues** método tiene dos parámetros de diccionario, uno para almacenar los valores de lectura/escritura y el otro para almacenar los valores de solo escritura (se usa después en consultas). En este método, debería rellenar estos diccionarios con datos que sean específicos de un participante de persistencia. Cada diccionario contiene el nombre del valor como clave y el propio valor como un objeto <xref:System.Runtime.DurableInstancing.InstanceValue>.  
  
     Los valores en el diccionario de readWriteValues se empaquetan como **InstanceValue** objetos. Los valores del diccionario de solo escritura se empaquetan como **InstanceValue** objetos con InstanceValueOptions.Optional y InstanceValueOption.WriteOnly establecidos. Cada **InstanceValue** proporcionada por el **CollectValues** implementaciones en todos los participantes de persistencia deben tener un nombre único.  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  Implemente el método <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A>. El **MapValues** método toma dos parámetros que son similares a los parámetros que el **CollectValues** método recibe. Todos los valores recopilan en el **CollectValues** fase se pasan a través de estos parámetros de diccionario. Los nuevos valores agregados por el **MapValues** fase se agregan a los valores de solo escritura.  El diccionario de solo escritura se usa para proporcionar datos a un origen externo no asociado directamente a valores de la instancia. Cada valor proporcionado por implementaciones de la **MapValues** método en todos los participantes de persistencia debe tener un nombre único.  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     El método <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> proporciona funcionalidad que <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> no ofrece; permite una dependencia de otro valor proporcionado por otro participante de persistencia que <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> no ha procesado todavía.  
  
4.  Implemente el **PublishValues** método. El **PublishValues** método recibe un diccionario que contiene todos los valores cargados desde el almacén de persistencia.  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  Implemente el **BeginOnSave** método si el participante es un participante de E/S de persistencia. A este método se llama durante una operación de almacenamiento. En este método, debería realizar adjunto de E/S para la persistencia (almacenamiento) instancias de flujo de trabajo.  Si el host está usando una transacción para el comando de persistencia correspondiente, se proporciona la misma transacción en Transaction.Current.  Además, PersistenceIOParticipants puede anunciar un requisito de coherencia transaccional, en cuyo caso el host crea una transacción para el episodio de persistencia si, por el contrario, no se usara uno.  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  Implemente el **BeginOnLoad** método si el participante es un participante de E/S de persistencia. A este método se llama durante una operación de carga. En este método, debería realizar adjunto de E/S para la carga de instancias de flujo de trabajo. Si el host está usando una transacción para el comando de persistencia correspondiente, se proporciona la misma transacción en Transaction.Current. Además, los participantes de E/S de persistencia pueden anunciar un requisito de coherencia transaccional, en cuyo caso el host crea una transacción para el episodio de persistencia si no lo contrario se usara uno.  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
