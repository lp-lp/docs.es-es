---
title: '&lt;código&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 9ec9d23f1f62358dc272f9764f88e3bb2ba41f78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599757"
---
# <a name="ltcodegt-visual-basic"></a>&lt;código&gt; (Visual Basic)
Indica que el texto de varias líneas de código.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `content`  
 Texto que se va a marcar como código.  
  
## <a name="remarks"></a>Comentarios  
 Use la `<code>` etiqueta para indicar varias líneas como código. Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) para indicar que el texto dentro de una descripción debe marcarse como código.  
  
 Compile con [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para procesar los comentarios de documentación a un archivo.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo se utiliza la \<código > etiqueta para incluir código de ejemplo para usar el `ID` campo.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a>Vea también  
 [Etiquetas XML para comentarios](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
