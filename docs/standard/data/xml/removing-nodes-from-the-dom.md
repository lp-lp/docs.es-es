---
title: Cómo quitar nodos del DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec786564e6246f10e10d600f4822442884323557
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568464"
---
# <a name="removing-nodes-from-the-dom"></a>Cómo quitar nodos del DOM
Para quitar un nodo del Modelo de objetos de documento XML (DOM), utilice el método <xref:System.Xml.XmlNode.RemoveChild%2A> para quitar un nodo específico. Cuando se quita un nodo, el método quita el subárbol que pertenece al nodo que se está quitando; es decir, no se trata de un nodo hoja.  
  
 Para quitar varios nodos del DOM, utilice el método <xref:System.Xml.XmlNode.RemoveAll%2A> para quitar todos los atributos y nodos secundarios, si es preciso, del nodo actual.  
  
 Si está trabajando con <xref:System.Xml.XmlNamedNodeMap>, puede quitar un nodo con el método <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A>.  
  
 Para quitar atributos, vea [Cómo quitar atributos de un nodo de elementos en el DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Vea también  
 [Document Object Model (DOM) para XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
