---
title: "Buscar posibles problemas mediante analizadores de mapas de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vs.progression.codemapanalyzers"
helpviewer_keywords: 
  - "análisis de código, gráficos de dependencias"
  - "gráficos de dependencias, análisis de código"
  - "documentos de gráfico, análisis"
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 11
author: "alexhomer1"
ms.author: "ahomer"
manager: "douge"
caps.handback.revision: 11
---
# Buscar posibles problemas mediante analizadores de mapas de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ejecute analizadores en mapas de código para identificar código demasiado complejo o que sea necesario mejorar. Por ejemplo, puede usar estos analizadores:  
  
|**Para buscar código que incluya**|**Examine estas áreas para ver si:**|  
|----------------------------------------|------------------------------------------|  
|Bucles o dependencias circulares|Puede simplificarlos y ver si puede interrumpir estos ciclos.|  
|Demasiadas dependencias|Están realizando demasiadas funciones o determinan el impacto de cambiar estas áreas. En un mapa de código correcto, aparecerá un número mínimo de dependencias. Para que el código resulte más fácil de mantener, cambiar, probar y reutilizar, piense si puede refactorizar estas áreas para definirlas de forma más nítida o si puede combinar el código que realiza funciones similares.|  
|Ninguna dependencia|Son necesarias o si debe quitar este código.|  
  
## Analizar mapas de código  
  
1.  En la barra de herramientas del mapa, elija **Diseño**, **Analizadores** y, después, el analizador que desea ejecutar:  
  
    |**Analizador**|**Para identificar nodos que**|  
    |--------------------|------------------------------------|  
    |**Analizador de referencias circulares**|Tienen dependencias circulares entre sí. **Note:**  Las dependencias circulares que se encuentran en el grupo **Genéricos** no se muestran en el mapa al expandir el grupo.|  
    |**Buscar analizador de concentradores**|Se encuentran entre el 25 % de los nodos con mayor número de conexiones.<br /><br /> **Para ocultar el resto de nodos del mapa**<br /><br /> -   Abra el menú contextual del mapa, elija **Avanzadas**, **Seleccione**, **Ocultar no seleccionados**.<br />     El mapa oculta los nodos no seleccionados y el analizador identifica los nuevos nodos como concentradores.|  
    |**Analizador de nodos a los que no se hace referencia**|No tienen referencias de otros nodos. **Caution:**  Compruebe cada uno de estos casos antes de asumir que el código no se usa. Ciertas dependencias, como las dependencias XAML y las dependencias de tiempo de ejecución, no se encuentran de forma estática en el código.|  
  
 Los analizadores de mapa de código continuarán ejecutándose después de aplicarlos. Si cambia el mapa, los analizadores aplicados volverán a procesar automáticamente el mapa actualizado. Para detener la ejecución de un analizador, en la barra de herramientas del mapa, elija **Diseño**, **Analizadores**. Desactive el analizador seleccionado.  
  
> [!TIP]
>  Si tiene un mapa muy grade y ejecuta el analizador, podría producirse una excepción de memoria. Si esto ocurre, edite el mapa para reducir su ámbito o genere uno más pequeño y, después, ejecute el analizador.  
  
## Vea también  
 [Asignar dependencias de sus soluciones](../modeling/map-dependencies-across-your-solutions.md)   
 [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)