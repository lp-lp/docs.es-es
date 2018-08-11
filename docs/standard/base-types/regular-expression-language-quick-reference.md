---
title: Lenguaje de expresiones regulares - Referencia rápida
ms.date: 03/30/2017
ms.technology: dotnet-standard
f1_keywords:
- VS.RegularExpressionBuilder
helpviewer_keywords:
- regex cheat sheet
- parsing text with regular expressions, language elements
- searching with regular expressions, language elements
- pattern-matching with regular expressions, language elements
- regular expressions, language elements
- regular expressions [.NET Framework]
- cheat sheet
- .NET Framework regular expressions, language elements
ms.assetid: 930653a6-95d2-4697-9d5a-52d11bb6fd4c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc0c1ebdc4f774858916dcc8ec8db2ba386b7a88
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948610"
---
# <a name="regular-expression-language---quick-reference"></a>Lenguaje de expresiones regulares - Referencia rápida
<a name="top"></a> Una expresión regular es un patrón con el que el motor de expresiones regulares intenta buscar una coincidencia en el texto de entrada. Un modelo consta de uno o más literales de carácter, operadores o estructuras.  Para obtener una breve introducción, consulte [Expresiones regulares de .NET](../../../docs/standard/base-types/regular-expressions.md).  
  
 Cada sección de esta referencia rápida enumera una categoría determinada de caracteres, operadores y construcciones que puede usar para definir expresiones regulares:  
  
 [Escapes de carácter](#character_escapes)  
 [Clases de carácter](#character_classes)  
 [Delimitadores](#atomic_zerowidth_assertions)  
 [Construcciones de agrupamiento](#grouping_constructs)  
 [Cuantificadores](#quantifiers)  
 [Construcciones de referencia inversa](#backreference_constructs)  
 [Construcciones de alternancia](#alternation_constructs)  
 [Sustituciones](#substitutions)  
 [Opciones de expresiones regulares](#options)  
 [Construcciones misceláneas](#miscellaneous_constructs)  
  
 Esta información también se proporciona en dos formatos que se puede descargar e imprimir para facilitar su consulta:  
  
 [Descarga en formato Word (.docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Descarga en formato PDF (.pdf)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
<a name="character_escapes"></a>   
## <a name="character-escapes"></a>Escapes de carácter  
 El carácter de barra diagonal inversa (\\) en una expresión regular indica que el carácter que le sigue es un carácter especial (como se muestra en la tabla siguiente) o que se debe interpretar literalmente. Para más información, consulte [Escapes de carácter](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md).  
  
|Carácter de escape|Description|Modelo|Coincidencias|  
|-----------------------|-----------------|-------------|-------------|  
|`\a`|Coincide con un carácter de campana, \u0007.|`\a`|"\u0007" en "¡Error!" + '\u0007'|  
|`\b`|En una clase de caracteres, coincide con un retroceso, \u0008.|`[\b]{3,}`|"\b\b\b\b" en "\b\b\b\b"|  
|`\t`|Coincide con una tabulación, \u0009.|`(\w+)\t`|"artículo1\t", "artículo2\t" en "artículo1\tartículo2\t"|  
|`\r`|Coincide con un retorno de carro, \u000D. (`\r` no es equivalente al carácter de nueva línea, `\n`).|`\r\n(\w+)`|"\r\nEstas" en "\r\nEstas son\ndos líneas."|  
|`\v`|Coincide con una tabulación vertical, \u000B.|`[\v]{2,}`|"\v\v\v" en "\v\v\v"|  
|`\f`|Coincide con un avance de página, \u000C.|`[\f]{2,}`|"\f\f\f" en "\f\f\f"|  
|`\n`|Coincide con una nueva línea, \u000A.|`\r\n(\w+)`|"\r\nEstas" en "\r\nEstas son\ndos líneas."|  
|`\e`|Coincide con un escape, \u001B.|`\e`|"\x001B" en "\x001B"|  
|`\` *nnn*|Usa la representación octal para especificar un carácter (*nnn* consta de dos o tres dígitos).|`\w\040\w`|"a b", "c d" en<br /><br /> "a bc d"|  
|`\x` *nn*|Usa la representación hexadecimal para especificar un carácter (*nn* consta de exactamente dos dígitos).|`\w\x20\w`|"a b", "c d" en<br /><br /> "a bc d"|  
|`\c` *X*<br /><br /> `\c` *x*|Coincide con el carácter de control ASCII especificado por *X* o *x*, donde *X* o *x* es la letra del carácter de control.|`\cC`|"\x0003" en "\x0003" (Ctrl-C)|  
|`\u` *nnnn*|Coincide con un carácter Unicode usando la representación hexadecimal (exactamente cuatro dígitos, según representa *nnnn*).|`\w\u0020\w`|"a b", "c d" en<br /><br /> "a bc d"|  
|`\`|Cuando va seguido de un carácter que no se reconoce como un carácter de escape en esta y otras tablas de este tema, coincide con ese carácter. Por ejemplo, `\*` es igual que `\x2A`y `\.` es igual que `\x2E`. Esto permite que el motor de expresiones regulares elimine la ambigüedad de los elementos del lenguaje (como \* o ?) y los literales de carácter (representados por `\*` o `\?`).|`\d+[\+-x\*]\d+`|"2+2" y "3\*9" en "(2+2) \* 3\*9"|  
  
 [Volver al principio](#top)  
  
<a name="character_classes"></a>   
## <a name="character-classes"></a>Clases de caracteres  
 Una clase de caracteres coincide con cualquiera de un juego de caracteres. Las clases de caracteres incluyen los elementos del lenguaje enumerados en la tabla siguiente. Para obtener más información, consulta [Character Classes](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).  
  
|Clase de carácter|Description|Modelo|Coincidencias|  
|---------------------|-----------------|-------------|-------------|  
|`[` *grupo_caracteres* `]`|Coincide con cualquier carácter individual de *grupo_caracteres*. De forma predeterminada, la coincidencia distingue entre mayúsculas y minúsculas.|`[ae]`|"a" en "casa"<br /><br /> "a", "e" en "ave"|  
|`[^` *grupo_caracteres* `]`|Negación: coincide con cualquier carácter individual que no esté en *grupo_caracteres*. De forma predeterminada, los caracteres de *grupo_caracteres* distinguen entre mayúsculas y minúsculas.|`[^aei]`|"r", "n", "o" en "reino"|  
|`[` *first* `-` *last* `]`|Intervalo de caracteres: coincide con cualquier carácter individual en el intervalo de *primero* a *último*.|`[A-Z]`|"A", "B" en "AB123"|  
|`.`|Carácter comodín: coincide con cualquier carácter excepto con \n.<br /><br /> Para coincidir con un carácter de punto literal (. o `\u002E`), debe anteponerle el carácter de escape (`\.`).|`a.e`|"ave" en "llave"<br /><br /> "ate" en "yate"|  
|`\p{` *name* `}`|Coincide con cualquier carácter individual que pertenezca a la categoría general Unicode o al bloque con nombre especificado por *name*.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|"C", "L" en "City Lights"<br /><br /> "Д", "Ж" in "ДЖem"|  
|`\P{` *name* `}`|Coincide con cualquier carácter individual que no pertenezca a la categoría general Unicode o al bloque con nombre especificado por *name*.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|"i", "t", "y" en "City"<br /><br /> "e", "m" in "ДЖem"|  
|`\w`|Coincide con cualquier carácter de una palabra.|`\w`|"I", "D", "A", "1", "3" en "ID A1.3"|  
|`\W`|Coincide con cualquier carácter que no pertenezca a una palabra.|`\W`|" ", "." en "ID A1.3"|  
|`\s`|Coincide con cualquier carácter que sea un espacio en blanco.|`\w\s`|"D " en "ID A1.3"|  
|`\S`|Coincide con cualquier carácter que no sea un espacio en blanco.|`\s\S`|" _" en "int \__ctr"|  
|`\d`|Coincide con cualquier dígito decimal.|`\d`|"4" en "4 = IV"|  
|`\D`|Coincide con cualquier carácter que no sea un dígito decimal.|`\D`|" ", "=", " ", "I", "V" en "4 = IV"|  
  
 [Volver al principio](#top)  
  
<a name="atomic_zerowidth_assertions"></a>   
## <a name="anchors"></a>Delimitadores  
 Los delimitadores, o aserciones atómicas de ancho cero, hacen que una coincidencia tenga éxito o no dependiendo de la posición actual en la cadena, pero no hacen que el motor avance por la cadena ni consuma caracteres. Los metacaracteres enumerados en la tabla siguiente son delimitadores. Para obtener más información, consulta [Delimitadores](../../../docs/standard/base-types/anchors-in-regular-expressions.md).  
  
|Aserción|Description|Modelo|Coincidencias|  
|---------------|-----------------|-------------|-------------|  
|`^`|De forma predeterminada, la coincidencia debe comenzar al principio de la cadena; en el modo multilínea, debe comenzar al principio de la línea.|`^\d{3}`|"901" en<br /><br /> "901-333-"|  
|`$`|De forma predeterminada, la coincidencia se debe producir al final de la cadena o antes de `\n` al final de la cadena; en el modo multilínea, se debe producir antes del final de la línea o antes de `\n` al final de la línea.|`-\d{3}$`|"-333" en<br /><br /> "-901-333"|  
|`\A`|La coincidencia se debe producir al principio de la cadena.|`\A\d{3}`|"901" en<br /><br /> "901-333-"|  
|`\Z`|La coincidencia se debe producir al final de la cadena o antes de `\n` al final de la cadena.|`-\d{3}\Z`|"-333" en<br /><br /> "-901-333"|  
|`\z`|La coincidencia se debe producir al final de la cadena.|`-\d{3}\z`|"-333" en<br /><br /> "-901-333"|  
|`\G`|La coincidencia se debe producir en el punto en el que finalizó la coincidencia anterior.|`\G\(\d\)`|"(1)", "(3)", "(5)" en "(1)(3)(5)[7](9\)"|  
|`\b`|La coincidencia se debe producir en un límite entre un carácter `\w` (alfanumérico) y un carácter `\W` (no alfanumérico).|`\b\w+\s\w+\b`|"ellos ello", "ellos ellos" en "ellos ello ellos ellos"|  
|`\B`|La coincidencia no se debe producir en un límite `\b` .|`\Bfin\w*\b`|"finir", "finado" en "definir afinado refinado finalista"|  
  
 [Volver al principio](#top)  
  
<a name="grouping_constructs"></a>   
## <a name="grouping-constructs"></a>Construcciones de agrupamiento  
 Las construcciones de agrupamiento definen subexpresiones de una expresión regular y, normalmente, capturan subcadenas de una cadena de entrada. Las construcciones de agrupamiento incluyen los elementos del lenguaje enumerados en la tabla siguiente. Para obtener más información, consulta [Grouping Constructs](grouping-constructs-in-regular-expressions.md).  
  
|Construcción de agrupamiento|Description|Modelo|Coincidencias|  
|------------------------|-----------------|-------------|-------------|  
|`(` *subexpresión* `)`|Captura la subexpresión coincidente y le asigna un número ordinal basado en uno.|`(\w)\1`|"aa" en "aarón"|  
|`(?<` *name* `>` *subexpresión* `)`|Captura la subexpresión coincidente en un grupo con nombre.|`(?<double>\w)\k<double>`|"aa" en "aarón"|  
|`(?<` *nombre1* `-` *nombre2* `>` *subexpresión* `)`|Define una definición de grupo de equilibrio. Para obtener más información, consulte la sección "Definiciones de grupos de equilibrio" en [Grouping Constructs](grouping-constructs-in-regular-expressions.md).|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|"((1-3)\*(3-1))" en "3+2^((1-3)\*(3-1))"|  
|`(?:` *subexpresión* `)`|Define un grupo sin captura.|`Write(?:Line)?`|"WriteLine" en "Console.WriteLine()"<br /><br /> "Write" en "Console.Write(valor)"|  
|`(?imnsx-imnsx:` *subexpresión* `)`|Aplica o deshabilita las opciones especificadas dentro de *subexpresión*. Para obtener más información, consulta [Regular Expression Options](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|"A12xl", "A12XL" en "A12xl A12XL a12xl"|  
|`(?=` *subexpresión* `)`|Aserción de búsqueda anticipada positiva de ancho cero.|`\w+(?=\.)`|"es", "corría" y "hermoso" en "Él es. El perro corría. El sol está hermoso."|  
|`(?!` *subexpresión* `)`|Aserción de búsqueda anticipada negativa de ancho cero.|`\b(?!un)\w+\b`|"seguro", "usado" en "aseguro seguro unidad usado"|  
|`(?<=` *subexpresión* `)`|Aserción de búsqueda tardía positiva de ancho cero.|`(?<=19)\d{2}\b`|"99", "50", "05" en "1851 1999 1950 1905 2003"|  
|`(?<!` *subexpresión* `)`|Aserción de búsqueda tardía negativa de ancho cero.|`(?<!19)\d{2}\b`|"51", "03" en "1851 1999 1950 1905 2003"|  
|`(?>` *subexpresión* `)`|Subexpresión sin retroceso (o "expansiva").|`[13579](?>A+B+)`|"1ABB", "3ABB" y "5AB" en "1ABB 3ABBC 5AB 5AC"|  
  
 [Volver al principio](#top)  
  
<a name="quantifiers"></a>   
## <a name="quantifiers"></a>Cuantificadores  
 Un cuantificador especifica cuántas instancias del elemento anterior (que puede ser un carácter, un grupo o una clase de caracteres) debe haber en la cadena de entrada para que se encuentre una coincidencia. Los cuantificadores incluyen los elementos del lenguaje enumerados en la tabla siguiente. Para obtener más información, consulta [Quantifiers](quantifiers-in-regular-expressions.md).  
  
|Cuantificador|Description|Modelo|Coincidencias|  
|----------------|-----------------|-------------|-------------|  
|`*`|Coincide con el elemento anterior cero o más veces.|`\d*\.\d`|".0", "19.9", "219.9"|  
|`+`|Coincide con el elemento anterior una o más veces.|`"be+"`|"caí" en "caída", "be" en "bebé"|  
|`?`|Coincide con el elemento anterior cero veces o una vez.|`"rai?n"`|"rata", "raicilla"|  
|`{` *n* `}`|Coincide con el elemento anterior exactamente *n* veces.|`",\d{3}"`|",043" en "1,043.6", ",876", ",543", y ",210" en "9,876,543,210"|  
|`{` *n* `,}`|Coincide con el elemento anterior al menos *n* veces.|`"\d{2,}"`|"166", "29", "1930"|  
|`{` *n* `,` *m* `}`|Coincide con el elemento anterior al menos *n* veces, pero no más de *m* veces.|`"\d{3,5}"`|"166", "17668"<br /><br /> "19302" en "193024"|  
|`*?`|Coincide con el elemento anterior cero o más veces, pero el menor número de veces que sea posible.|`\d*?\.\d`|".0", "19.9", "219.9"|  
|`+?`|Coincide con el elemento anterior una o más veces, pero el menor número de veces que sea posible.|`"be+?"`|"be" en "bebida", "be" en "bebé"|  
|`??`|Coincide con el elemento anterior cero o una vez, pero el menor número de veces que sea posible.|`"rai??n"`|"rata", "raicilla"|  
|`{` *n* `}?`|Coincide con el elemento precedente exactamente *n* veces.|`",\d{3}?"`|",043" en "1,043.6", ",876", ",543", y ",210" en "9,876,543,210"|  
|`{` *n* `,}?`|Coincide con el elemento anterior al menos *n* veces, pero el menor número de veces posible.|`"\d{2,}?"`|"166", "29", "1930"|  
|`{` *n* `,` *m* `}?`|Coincide con el elemento anterior entre *n* y *m* veces, pero el menor número de veces posible.|`"\d{3,5}?"`|"166", "17668"<br /><br /> "193", "024" en "193024"|  
  
 [Volver al principio](#top)  
  
<a name="backreference_constructs"></a>   
## <a name="backreference-constructs"></a>Construcciones de referencia inversa  
 Una referencia inversa permite identificar una subexpresión coincidente previamente más adelante en la misma expresión regular. En la tabla siguiente se enumeran las construcciones de referencia inversa admitidas en las expresiones regulares de .NET. Para obtener más información, consulta [Backreference Constructs](backreference-constructs-in-regular-expressions.md).  
  
|Construcción de referencias inversas|Description|Modelo|Coincidencias|  
|-----------------------------|-----------------|-------------|-------------|  
|`\` *número*|Referencia inversa. Coincide con el valor de una subexpresión numerada.|`(\w)\1`|"aa" en "aarón"|  
|`\k<` *name* `>`|Referencia inversa con nombre Coincide con el valor de una expresión con nombre.|`(?<char>\w)\k<char>`|"aa" en "aarón"|  
  
 [Volver al principio](#top)  
  
<a name="alternation_constructs"></a>   
## <a name="alternation-constructs"></a>Construcciones de alternancia  
 Las estructuras de alternancia modifican una expresión regular para habilitar o no la coincidencia. Estas construcciones incluyen los elementos del lenguaje enumerados en la tabla siguiente. Para obtener más información, consulta [Alternation Constructs](alternation-constructs-in-regular-expressions.md).  
  
|Construcciones de alternancia|Description|Modelo|Coincidencias|  
|---------------------------|-----------------|-------------|-------------|  
|<code>&#124;</code>|Coincide con cualquier elemento separado por el carácter de barra vertical (*&#124;).|<code>th(e&#124;is&#124;at)</code>|"el", "este" en "este es el día. "|  
|`(?(` *expresión* `)` *sí* <code>&#124;</code> *no* `)`|Coincide con *sí* si el patrón de expresión regular designado por *expresión* coincide; de lo contrario, coincide con la parte opcional *no* . *expresión* se interpreta como una aserción de ancho cero.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|"A10", "910" en "A10 C103 910"|  
|`(?(` *nombre* `)` *sí* <code>&#124;</code> *no* `)`|Coincide con *sí* si *nombre*, un grupo de captura con nombre o numerado, tiene una coincidencia; de lo contrario, coincide con la parte opcional *no*.|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|Dogs.jpg, "Yiska playing.jpg" en "Dogs.jpg "Yiska playing.jpg""|  
  
 [Volver al principio](#top)  
  
<a name="substitutions"></a>   
## <a name="substitutions"></a>Sustituciones  
 Las sustituciones son elementos del lenguaje de expresiones regulares que se admiten en modelos de reemplazo. Para obtener más información, consulta [Substitutions](substitutions-in-regular-expressions.md). Los metacaracteres enumerados en la tabla siguiente son aserciones atómicas de ancho cero.  
  
|Carácter|Description|Modelo|Modelo de reemplazo|Cadena de entrada|Cadena de resultado|  
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|  
|`$` *número*|Sustituye la subcadena que coincide con el grupo *número*.|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|"one two"|"two one"|  
|`${` *name* `}`|Sustituye la subcadena que coincide con el grupo con nombre *nombre*.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|"one two"|"two one"|  
|`$$`|Sustituye un "$" literal.|`\b(\d+)\s?USD`|`$$$1`|"103 USD"|"$103"|  
|`$&`|Sustituye una copia de toda la coincidencia.|`\$?\d*\.?\d+`|`**$&**`|"$1.30"|"\*\*$1.30\*\*"|  
|<code>$`</code>|Sustituye todo el texto de la cadena de entrada delante de la coincidencia.|`B+`|<code>$`</code>|"AABBCC"|"AAAACC"|  
|`$'`|Sustituye todo el texto de la cadena de entrada detrás de la coincidencia.|`B+`|`$'`|"AABBCC"|"AACCCC"|  
|`$+`|Sustituye el último grupo capturado.|`B+(C+)`|`$+`|"AABBCCDD"|AACCDD|  
|`$_`|Sustituye toda la cadena de entrada.|`B+`|`$_`|"AABBCC"|"AAAABBCCCC"|  
  
 [Volver al principio](#top)  
  
<a name="options"></a>   
## <a name="regular-expression-options"></a>Opciones de expresiones regulares  
 Puede especificar opciones que controlen cómo debe interpretar el motor de expresiones regulares un patrón de expresión regular. Muchas de estas opciones pueden especificarse alineadas (en el patrón de expresión regular) o como una o más constantes de <xref:System.Text.RegularExpressions.RegexOptions> . Esta referencia rápida solo muestra las opciones alineadas. Para obtener más información sobre las opciones alineadas y <xref:System.Text.RegularExpressions.RegexOptions> , consulte el artículo [Regular Expression Options](regular-expression-options.md).  
  
 Puede especificar una opción alineada de dos formas:  
  
-   Con la [construcción miscelánea](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`, donde el signo menos (-) delante de una opción o un conjunto de opciones desactiva dichas opciones. Por ejemplo, `(?i-mn)` activa una coincidencia sin distinción entre mayúsculas y minúsculas (`i`), desactiva el modo multilínea (`m`) y desactiva las capturas de grupo sin nombre (`n`). La opción se aplica al patrón de expresión regular a partir del punto en el que esta se define y es efectiva hasta el final del patrón o hasta el punto en el que otro constructor invierte la opción.  
  
-   Con la [grouping construct](grouping-constructs-in-regular-expressions.md)`(?imnsx-imnsx:`*subexpresión*`)`, que define opciones solo para el grupo especificado.  
  
 El motor de expresiones regulares de .NET admite las siguientes opciones insertadas.  
  
|Opción|Description|Modelo|Coincidencias|  
|------------|-----------------|-------------|-------------|  
|`i`|Usa la coincidencia sin distinción entre mayúsculas y minúsculas.|`\b(?i)a(?-i)a\w+\b`|"aardvark", "aaaAuto" en "aardvark AAAuto aaaAuto Adam breakfast"|  
|`m`|Usa el modo multilínea. `^` y `$` coinciden con el principio y el final de una línea, en lugar del principio y el final de una cadena.|Para obtener un ejemplo, consulte la sección "Modo multilínea" en [Regular Expression Options](regular-expression-options.md).||  
|`n`|No se capturan grupos sin nombre.|Para obtener un ejemplo, consulte la sección "Solo capturas explícitas" en [Regular Expression Options](regular-expression-options.md).||  
|`s`|Usa el modo de una sola línea.|Para obtener un ejemplo, consulte la sección "Modo de una sola línea" en [Regular Expression Options](regular-expression-options.md).||  
|`x`|Se omite el espacio en blanco sin escape en el patrón de expresión regular.|`\b(?x) \d+ \s \w+`|"1 aardvark", "2 cats" en "1 aardvark 2 cats IV centurions"|  
  
 [Volver al principio](#top)  
  
<a name="miscellaneous_constructs"></a>   
## <a name="miscellaneous-constructs"></a>Construcciones misceláneas  
 Las estructuras misceláneas modifican un modelo de expresión regular o proporcionan información sobre él. En la tabla siguiente se enumeran las construcciones misceláneas admitidas por .NET. Para obtener más información, consulta [Miscellaneous Constructs](miscellaneous-constructs-in-regular-expressions.md).  
  
|Construcción|de esquema JSON|Ejemplo|  
|---------------|----------------|-------------|  
|`(?imnsx-imnsx)`|Establece o deshabilita opciones como la no distinción entre mayúsculas y minúsculas en medio de un patrón. Para más información, consulte [Opciones de expresiones regulares](regular-expression-options.md).|`\bA(?i)b\w+\b` coincide con "ABA", "Able" en "ABA Able Act"|  
|`(?#` *comentario* `)`|Comentario alineado. El comentario termina en el primer paréntesis de cierre.|`\bA(?#Matches words starting with A)\w+\b`|  
|`#` [hasta el final de la línea]|Comentario en modo X. El comentario comienza en un carácter `#` sin escape y continúa hasta el final de la línea.|`(?x)\bA\w+\b#Matches words starting with A`|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex>  
 [Expresiones regulares](regular-expressions.md)  
 [Clases de expresiones regulares](the-regular-expression-object-model.md)  
 [Ejemplos de expresiones regulares](regular-expression-examples.md)  
 [Expresiones regulares: referencia rápida (descarga en formato Word)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Expresiones regulares: referencia rápida (descarga en formato PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
