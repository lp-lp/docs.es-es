---
title: Portabilidad a .NET Core - Análisis de las dependencias de terceros
description: Aprenda a analizar dependencias de terceros para portar su proyecto de .NET Framework a .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.openlocfilehash: a5affd8f1c493a87b2a4f7cd4096d168d404626a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216835"
---
# <a name="analyze-your-third-party-dependencies"></a>Análisis de las dependencias de terceros

Si está pensando en portar el código a .NET Core o .NET Standard, el primer paso del proceso de portabilidad consiste en analizar las dependencias de terceros. Las dependencias de terceros son [paquetes NuGet](#analyze-referenced-nuget-packages-on-your-project) o [DLL](#analyze-dependencies-that-arent-nuget-packages) a los que se hace referencia en el proyecto. Evalúe cada dependencia y desarrolle un plan de contingencia para las dependencias que no son compatibles con .NET Core. En este artículo se muestra cómo determinar si la dependencia es compatible con .NET Core.

## <a name="analyze-referenced-nuget-packages-in-your-project"></a>Analizar los paquetes NuGet a los que se hace referencia en el proyecto

Si va a hacer referencia a paquetes NuGet en el proyecto, debe comprobar si son compatibles con .NET Core.
Hay dos maneras de hacerlo:

* [Con la aplicación NuGet Package Explorer](#analyze-nuget-packages-using-nuget-package-explorer) (el método más fiable).
* [A través del sitio de nuget.org](#analyze-nuget-packages-using-nugetorg).

Después de analizar los paquetes, si no son compatibles con .NET Core y solo se centran en .NET Framework, puede comprobar si el [modo de compatibilidad de .NET Framework](#net-framework-compatibility-mode) le puede ayudar con el proceso de portabilidad.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analizar los paquetes NuGet con NuGet Package Explorer

Los paquetes NuGet son un conjunto de carpetas que contienen ensamblados específicos de plataforma, por lo que debe comprobar si hay una carpeta que contenga un ensamblado compatible dentro del paquete.

La manera más fácil de inspeccionar las carpetas de paquetes NuGet consiste en usar la herramienta [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer). Después de instalarla, siga estos pasos para ver los nombres de las carpetas:

1. Abra NuGet Package Explorer.
2. Haga clic en **Open package from online feed** (Abrir paquete desde fuente en línea).
3. Busque el nombre del paquete.
4. Seleccione el nombre del paquete en los resultados de la búsqueda y haga clic en **Open** (Abrir).
5. Expanda la carpeta *lib* de la derecha y examine los nombres de las carpetas.

Busque una carpeta que tenga cualquiera de estos nombres:

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Estos valores son los [monikers de la plataforma de destino (TFM)](../../standard/frameworks.md) que se asignan a las versiones de los perfiles de [.NET Standard](../../standard/net-standard.md), .NET Core y de la Biblioteca de clases portable (PCL) tradicional compatibles con .NET Core.

> [!IMPORTANT]
> Cuando examine los TFM compatibles con un paquete, tenga en cuenta que `netcoreapp*`, aunque sea compatible, es solo para los proyectos de .NET Core, y no para los proyectos de .NET Standard.
> Las bibliotecas que solo tienen como destino `netcoreapp*` (y no `netstandard*`) solo las pueden consumir otras aplicaciones de .NET Core.

También hay algunos TFM heredados utilizados en versiones preliminares de .NET Core que pueden ser compatibles:

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

Aunque es probable que estos TFM funcionen con el código, no hay ninguna garantía de compatibilidad. Los paquetes con estos TFM se crearon con paquetes de .NET Core de versión preliminar. Tome nota del momento en que se actualizan los paquetes mediante estos TFM para que se basen en .NET Standard (en el caso de que se actualicen).

> [!NOTE]
> Para usar un paquete destinado a una PCL tradicional o .NET Core de versión preliminar, debe usar el elemento de MSBuild `PackageTargetFallback` en el archivo del proyecto.
> Para más información sobre este elemento de MSBuild, vea [`PackageTargetFallback`](../tools/csproj.md#packagetargetfallback).

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analizar los paquetes NuGet mediante nuget.org

Como alternativa, en la sección **Dependencies** (Dependencias) de la página de un paquete de [nuget.org](https://www.nuget.org/) puede ver los TFM que admite cada paquete.

Aunque el uso del sitio es un método más sencillo para comprobar la compatibilidad, la información de las **dependencias** no está disponible en el sitio para todos los paquetes.

### <a name="net-framework-compatibility-mode"></a>Modo de compatibilidad de .NET Framework

Después de analizar los paquetes NuGet, puede que observe que solo tienen como destino .NET Framework, al igual que la mayoría de los paquetes NuGet.

A partir de .NET Standard 2.0 se ha introducido el modo de compatibilidad de .NET Framework. Este modo de compatibilidad permite que los proyectos de .NET Standard y .NET Core hagan referencia a bibliotecas de .NET Framework. La acción de hacer referencias a bibliotecas de .NET Framework no funciona para todos los proyectos; por ejemplo, si la biblioteca usa API de Windows Presentation Foundation (WPF) pero desbloquea muchos escenarios de portabilidad.

Al hacer referencia a paquetes NuGet que tienen como destino .NET Framework en el proyecto, como [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), recibirá una advertencia de reserva de paquete ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) parecida al ejemplo siguiente:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Esta advertencia se muestra cuando agrega el paquete y cada vez que compila para asegurarse de que prueba ese paquete con el proyecto. Si el proyecto funciona según lo previsto, puede suprimir la advertencia editando las propiedades del paquete en Visual Studio o editando manualmente el archivo del proyecto en su editor de código favorito.

Para suprimir la advertencia editando el archivo del proyecto, busque la entrada `PackageReference` del paquete del que quiere suprimir la advertencia y agregue el atributo `NoWarn`. El atributo `NoWarn` acepta una lista separada por comas de todos los identificadores de advertencia. En el ejemplo siguiente se muestra cómo suprimir la advertencia `NU1701` del paquete `Huitian.PowerCollections` editando manualmente el archivo del proyecto:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Para más información sobre cómo suprimir advertencias del compilador en Visual Studio, vea [Supresión de las advertencias para paquetes NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Qué hacer cuando su dependencia del paquete NuGet no se ejecuta en .NET Core

Si un paquete NuGet del que depende no se ejecuta en .NET Core, puede hacer lo siguiente:

1. Si el proyecto es de código abierto y está hospedado en algún lugar como GitHub, puede implicar directamente a los desarrolladores.
2. Puede ponerse en contacto directamente con el autor en [nuget.org](https://www.nuget.org/). Busque el paquete y haga clic en **Contact Owners** (Póngase en contacto con los propietarios) a la izquierda de la página del paquete.
3. Puede buscar otro paquete que se ejecute en .NET Core que efectúe la misma tarea que el paquete que estaba usando.
4. Puede intentar volver a escribir el código de lo que hacía el paquete usted mismo.
5. Puede eliminar la dependencia en el paquete mediante el cambio de la funcionalidad de la aplicación, al menos hasta que esté disponible una versión compatible del paquete.

No olvide que los mantenedores de los proyectos de código abierto y los publicadores de paquetes NuGet suelen ser voluntarios. Colaboran porque les importa un dominio determinado, lo hacen de forma gratuita y en muchas ocasiones tienen otro trabajo, por lo que debe ser consciente de ello al ponerse en contacto con ellos para solicitar soporte técnico de .NET Core.

Si no puede resolver el problema con ninguna de las sugerencias anteriores, puede que deba efectuar la portabilidad a .NET Core en otro momento.

Al equipo de .NET le gustaría saber qué bibliotecas son las más importantes para que sean compatibles con .NET Core. Puede enviar un correo electrónico a dotnet@microsoft.com indicando las bibliotecas que le gustaría usar.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analizar dependencias que no son paquetes NuGet

Puede que tenga una dependencia que no sea un paquete NuGet, como un archivo DLL, en el sistema de archivos. La única manera de determinar la portabilidad de esa dependencia consiste en ejecutar la herramienta [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport). La herramienta puede analizar ensamblados que tienen como destino .NET Framework e identificar API que no se pueden portar a otras plataformas de .NET, como .NET Core. Puede ejecutar la herramienta como una aplicación de consola o como [extensión de Visual Studio](../../standard/analyzers/portability-analyzer.md).

## <a name="next-steps"></a>Pasos siguientes

Si está realizando la portabilidad de una biblioteca, consulte [Porting your Libraries](libraries.md) (Portabilidad de las bibliotecas).
