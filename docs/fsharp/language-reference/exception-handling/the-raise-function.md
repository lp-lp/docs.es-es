---
title: 'Excepciones: función raise (F#)'
description: "Obtenga información acerca de cómo se utiliza la función 'raise' de F # para indicar que hubo un error o una condición excepcional."
ms.date: 05/16/2016
ms.openlocfilehash: bad18bfbccd738a12e16a0e026ade22e96d4cfcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564768"
---
# <a name="exceptions-the-raise-function"></a>Excepciones: función raise

El `raise` función se utiliza para indicar que hubo un error o una condición excepcional. Información sobre el error se captura en un objeto de excepción.


## <a name="syntax"></a>Sintaxis

```fsharp
raise (expression)
```

## <a name="remarks"></a>Comentarios
El `raise` función genera un objeto de excepción e inicia una proceso de desenredo de pila. El proceso de desenredo de pila es administrado por common language runtime (CLR), por lo que el comportamiento de este proceso es el mismo como en cualquier otro lenguaje. NET. El proceso de desenredo de pila es una búsqueda de un controlador de excepciones que coincida con la excepción generada. La búsqueda comienza en el actual `try...with` expresión, si hay alguno. Cada modelo en el `with` se activa el bloque, en orden. Cuando se encuentra un controlador de excepción coincidente, la excepción se considera controlada; en caso contrario, se desenreda la pila y `with` se comprueban los bloques de la cadena de llamadas hasta que encuentra un controlador coincidente. Cualquier `finally` bloques que se encuentran en la cadena de llamadas también se ejecutan en la secuencia que se desenreda la pila.

El `raise` función es el equivalente de `throw` en C# o C++. Use `reraise` en un controlador de tipo catch para propagar la misma excepción por la cadena de llamadas.

Ejemplos de código siguientes muestran el uso de la `raise` función puede generar una excepción.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

El `raise` función también puede utilizarse para generar excepciones de. NET, tal como se muestra en el ejemplo siguiente.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a>Vea también
[Control de excepciones](index.md)

[Tipos de excepción](exception-types.md)

[Exceptions: The `try...with` Expression](the-try-with-expression.md) (Excepciones: la expresión `try...with`)

[Exceptions: The `try...finally` Expression](the-try-finally-expression.md) (Excepciones: la expresión `try...finally`)

[Exceptions: the `failwith` Function](the-failwith-function.md) (Excepciones: la función `failwith`)

[Exceptions: the `invalidArg` Function](the-invalidArg-function.md) (Excepciones: la función `invalidArg`)
