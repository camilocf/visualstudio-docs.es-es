---
title: Usar el atributo DebuggerTypeProxy | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f7b404253c2425a64fd2a9ad4bb53943e033d8e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898842"
---
# <a name="using-debuggertypeproxy-attribute"></a>Utilizar el atributo DebuggerTypeProxy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DebuggerTypeProxyAttribute] (assetId:///T:System.Diagnostics.DebuggerTypeProxyAttribute?qualifyHint=False & autoUpgrade = True) especifica un servidor proxy, o suplente, para un tipo y cambia la manera en que el tipo se muestra en las ventanas del depurador. Cuando ve una variable que tiene un proxy, el proxy reemplaza al tipo original en el **mostrar**. En la ventana de las variables del depurador se muestran sólo los miembros públicos del tipo de servidor proxy. No se muestran los miembros privados.  
  
 Este atributo se puede aplicar a:  
  
- Estructuras  
  
- Clases  
  
- Ensamblados  
  
  Una clase de proxy de tipo debe tener un constructor que tome un argumento del tipo que el proxy reemplazará. El depurador crea una nueva instancia de la clase de proxy de tipo cada vez que necesita mostrar una variable del tipo de destino. Esto puede afectar al rendimiento. Por tanto, en el constructor no debe realizarse más trabajo del estrictamente necesario.  
  
  Para minimizar la reducción de rendimiento, el evaluador de expresiones no examina los atributos en el proxy de presentación del tipo, a menos que el usuario expanda el tipo haciendo clic en el símbolo + en la ventana del depurador o mediante <xref:System.Diagnostics.DebuggerBrowsableAttribute>. Por consiguiente, no se deben colocar atributos en el propio tipo de presentación. Los atributos pueden y deben utilizarse en el cuerpo del tipo de presentación.  
  
  Se recomienda que el proxy de tipo sea una clase anidada privada dentro de la clase que el atributo tiene como destino. De este modo, puede obtener acceso fácilmente a los miembros internos.  
  
  Si se utiliza <xref:System.Diagnostics.DebuggerTypeProxyAttribute> en el nivel de ensamblado, el parámetro `Target` especifica el tipo que reemplazará el proxy.  
  
  Para obtener un ejemplo de cómo utilizar este atributo junto con <xref:System.Diagnostics.DebuggerDisplayAttribute> y <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, consulte[utilizando el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## <a name="using-generics-with-debuggertypeproxy"></a>Utilizar genéricos con DebuggerTypeProxy  
 La compatibilidad con los genéricos es limitada. En C#, `DebuggerTypeProxy` solo acepta tipos abiertos. Un tipo abierto, también denominado tipo no construido, es un tipo genérico de cuyos parámetros de tipo no se han creado instancias con argumentos. No se admiten los tipos cerrados, también denominados tipos construidos.  
  
 La sintaxis de un tipo abierto tiene el siguiente aspecto:  
  
 `Namespace.TypeName<,>`  
  
 Si utiliza un tipo genérico como destino en `DebuggerTypeProxy`, debe utilizar esta sintaxis. El mecanismo `DebuggerTypeProxy` deduce los parámetros de tipo automáticamente.  
  
 Para obtener más información sobre los tipos abiertos y cerrados en C#, vea el [especificación del lenguaje C#](http://msdn.microsoft.com/library/e5d5a5cc-636b-4bff-b9c8-a8edc6207c22), abra la sección 20.5.2 tipos y cerrados.  
  
 Visual Basic no tiene sintaxis de tipos abiertos, por lo que no se puede hacer lo mismo en Visual Basic. En su lugar, debe utilizar una representación de cadena del nombre del tipo abierto.  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>Vea también  
 [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
  [Mejorar la depuración con los atributos de visualización del depurador](http://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)



