---
title: Telemetría del SDK de .NET Core
description: Descubra las características de telemetría del SDK de .NET Core que recopilan información de uso para el análisis, qué datos se recopilan y cómo deshabilitarlas.
author: richlander
ms.author: mairaw
ms.date: 06/20/2018
ms.openlocfilehash: f60a1eaa7b869676dfbb67529e7878ca9b9ca34a
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314882"
---
# <a name="net-core-sdk-telemetry"></a>Telemetría del SDK de .NET Core

El [SDK de .NET Core](index.md) incluye una [característica de telemetría](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) que recopila información de uso. Es importante que el equipo de .NET entienda cómo se usan las herramientas a fin de que se puedan mejorar. Para obtener más información, consulte [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/) (Lo que hemos aprendido de la telemetría del SDK de .NET Core).

Los datos recopilados son anónimos y se publican de forma agregada para que los usen Microsoft y la comunidad según la [licencia de atribución de Creative Commons](https://creativecommons.org/licenses/by/4.0/).

## <a name="scope"></a>Ámbito

El comando `dotnet` se usa para iniciar ambas aplicaciones y la CLI de .NET Core. El comando `dotnet` no recopila la telemetría por sí mismo. Los comandos de la CLI de .NET Core que se ejecutan mediante el comando `dotnet` son los que recopilan la telemetría.

La telemetría *no está habilitada* cuando se usa el comando `dotnet` por sí mismo, sin ningún comando asociado:

- `dotnet`
- `dotnet [path-to-app]`

La telemetría *está habilitada* cuando se usan los [comandos de la CLI de .NET Core](index.md), como:

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a>Cómo desactivar la característica

La característica de telemetría del SDK de .NET Core está habilitada de manera predeterminada. Puede desactivar la característica de telemetría si establece la variable de entorno `DOTNET_CLI_TELEMETRY_OPTOUT` en `1` o `true`.

## <a name="data-points"></a>Puntos de datos

La característica recopila los siguientes datos:

- Marca de tiempo de la invocación&#8224;
- Comando invocado (por ejemplo, “build”)&#8224;
- Dirección IP de tres octetos usada para determinar la ubicación geográfica&#8224;
- `ExitCode` del comando
- Ejecutor de pruebas (para los proyectos de prueba)
- Sistema operativo y versión&#8224;
- Si los id. de tiempo de ejecución están presentes en el nodo “runtimes”
- Versión del SDK de .NET Core&#8224;

&#8224;Esta métrica está publicada.

A partir del SDK de .NET Core 2.0, se recopilan nuevos puntos de datos:

- Opciones y argumentos del comando `dotnet`: solo se recopilan opciones y argumentos conocidos (no cadenas arbitrarias).
- Si el SDK se ejecuta en un contenedor.
- Marcos de trabajo de destino.
- Dirección MAC con hash: un id. único y anónimo criptográficamente (SHA256) para una máquina. Esta métrica no está publicada.
- Directorio de trabajo actual con hash.

La característica no recopila datos personales, como direcciones de correo electrónico o nombres de usuario. No examina el código ni extrae datos a nivel de proyecto confidenciales, como el nombre, el repositorio o el autor. Los datos se envían de forma segura a los servidores de Microsoft con tecnología de [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/), se conservan bajo acceso restringido y se publican bajo controles de seguridad estrictos de sistemas seguros de [Azure Storage](https://azure.microsoft.com/services/storage/).

El equipo de .NET quiere saber cómo se usan las herramientas y si funcionan correctamente, no qué va a compilar con las herramientas. Si sospecha que la telemetría recopila datos confidenciales o que los datos se están tratando de forma insegura o inapropiada, [informe de un problema en los problemas del repositorio de dotnet/cli](https://github.com/dotnet/cli/issues) para que lo investiguemos.

## <a name="published-data"></a>Datos publicados

Los datos publicados están disponibles cada trimestre y se muestran en [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (Datos de uso del SDK de .NET Core). Las columnas de un archivo de datos son:

- Marca de tiempo
- Occurrences&#8224;
- Comando
- Geography&#8225;
- OSFamily
- RuntimeID
- OSVersion
- SDKVersion

&#8224;En la columna *Ocurrences* se muestra el número agregado de usos de ese comando para las métricas de esa fila durante ese día.

&#8225;Normalmente, en la columna *Geography* se muestra el nombre de un país. En algunos casos, el continente de Antártida aparece en esta columna, ya sea debido a los investigadores que usan .NET Core en la Antártida o a datos de ubicación incorrectos.

### <a name="example"></a>Ejemplo

| Marca de tiempo      | Occurrences | Comando | Geography | OSFamily | RuntimeID     | OSVersion | SDKVersion |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| 4/16/2017 0:00 | 8           | ejecutar     | Uganda    | Darwin   | osx.10.12-x64 | 10.12     | 1.0.1      |

### <a name="datasets"></a>Conjuntos de datos

[2016: tercer trimestre](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[2016: cuarto trimestre](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[2017: primer trimestre](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[2017: segundo trimestre](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)  
[2017: tercer trimestre](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)  
[2017: cuarto trimestre](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)  

Hay conjuntos de datos adicionales publicados con un formato de URL estándar. Reemplace `<YEAR>` con el año y `<QUARTER>` con el trimestre del año (use `1`, `2`, `3` o `4`). Los archivos están en formato de valores separados por tabulaciones (*TSV*).

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a>Licencia

La distribución de Microsoft de .NET Core cuenta con licencia en virtud del [CLUF DE LA BIBLIOTECA DE MICROSOFT .NET](https://aka.ms/dotnet-core-eula). Esta licencia incluye la sección “DATOS” para habilitar la telemetría (se muestra a continuación).

Los [paquetes NuGet de .NET](https://www.nuget.org/profiles/dotnetframework) usan la misma licencia, pero no permiten la telemetría (consulte [Ámbito](#scope)).

> 2. DATOS. El software puede recopilar información sobre el usuario y la utilización del software y, después, enviarla a Microsoft. Microsoft puede usarla para mejorar nuestros productos y servicios. Puede obtener más información sobre la recopilación y el uso de datos en la documentación de ayuda y la declaración de privacidad en http://go.microsoft.com/fwlink/?LinkId=528096. Al usar el software, se entiende que da su consentimiento para la realización de estas prácticas.

## <a name="disclosure"></a>Divulgación

El SDK de .NET Core muestra el texto siguiente cuando ejecuta por primera vez uno de los comandos de la [CLI de .NET Core](index.md) (por ejemplo, `dotnet restore`). El texto puede variar ligeramente según la versión del SDK que ejecute. Esta experiencia de "primera vista" es la forma en que Microsoft le notifica sobre la recopilación de datos.

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core: https://aka.ms/dotnet-docs
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. 
The data is anonymous and doesn't include command-line arguments. 
The data is collected by Microsoft and shared with the community. 
You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="see-also"></a>Vea también

[What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/) (Lo que hemos aprendido de la telemetría del SDK de .NET Core)  
[Telemetry reference source (dotnet/cli repo)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)(Origen de referencia de telemetría)  
[.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (Datos de uso del SDK de .NET Core)  
