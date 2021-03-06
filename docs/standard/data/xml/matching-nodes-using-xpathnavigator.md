---
title: Coincidencia de nodos con XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94c0697eea13b49eacb7f4f9a6a37f7b5a774761
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569270"
---
# <a name="matching-nodes-using-xpathnavigator"></a>Coincidencia de nodos con XPathNavigator
La clase <xref:System.Xml.XPath.XPathNavigator> incluye el método <xref:System.Xml.XPath.XPathNavigator.Matches%2A> para determinar si un nodo coincide con una expresión XPath. El método <xref:System.Xml.XPath.XPathNavigator.Matches%2A> toma una expresión XPath como entrada y devuelve <xref:System.Boolean> que indica si el nodo actual coincide con la expresión XPath especificada o el objeto <xref:System.Xml.XPath.XPathExpression> compilado especificado.  
  
## <a name="matching-nodes"></a>Coincidencia de nodos  
 El método <xref:System.Xml.XPath.XPathNavigator.Matches%2A> devuelve `true` si el nodo actual coincide con la expresión XPath especificada. Por ejemplo, en el siguiente código de ejemplo, el método <xref:System.Xml.XPath.XPathNavigator.Matches%2A> devolverá `true` si el nodo actual es el elemento `b` y el elemento `b` tiene el atributo `c`.  
  
> [!NOTE]
>  El método <xref:System.Xml.XPath.XPathNavigator.Matches%2A> no cambia el estado de <xref:System.Xml.XPath.XPathNavigator>.  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Procesamiento de datos XML con el modelo de datos XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Seleccionar datos XML con XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Evaluación de expresiones XPath con XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Tipos de nodos reconocidos con consultas XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Espacios de nombres y consultas XPath](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Expresiones XPath compiladas](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
