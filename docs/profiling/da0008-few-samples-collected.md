---
title: "DA0008: Pocos ejemplos recolectados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DATooFewSamples"
  - "vs.performance.8"
  - "vs.performance.DA0008"
  - "vs.performance.rules.DA0008"
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# DA0008: Pocos ejemplos recolectados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0008|  
|Categoría|Uso de Herramientas de generación de perfiles|  
|Método de generación de perfiles|Muestreo|  
|Mensaje|Solo se recolectó un reducido número de ejemplos.  Considere una ejecución más prolongada o una frecuencia de muestreo más rápida para obtener resultados más significativos.|  
|Tipo de regla|Información|  
  
## Motivo  
 Solo se recolectó un reducido número de ejemplos en la ejecución de generación de perfiles.  
  
## Descripción de la regla  
 Cuando se usa el método de muestreo, se debe recopilar un número estadísticamente significativo de muestras para garantizar que los datos representen el comportamiento real del programa.  Para minimizar los errores de muestreo, debe intentar recopilar al menos 1000 muestras del comportamiento de ejecución de las instrucciones de programa.  Si no recoge suficientes muestras, puede obtener datos erróneos al analizar los datos de generación de perfiles.  
  
## Cómo corregir infracciones  
 Considere la posibilidad de generar perfiles de una ejecución más prolongada de la aplicación o usar una velocidad de muestreo más rápida para obtener resultados estadísticamente significativos.  Para obtener más información sobre cómo cambiar la velocidad de muestreo en el IDE de Visual Studio, consulte [Cómo: Elegir eventos de muestreo](../Topic/How%20to:%20Choose%20Sampling%20Events.md).  Para obtener más información sobre cómo cambiar la velocidad de muestreo al usar la línea de comandos de las Herramientas de generación de perfiles, consulte [Timer](../profiling/timer.md) en la referencia [VSPerfCmd](../profiling/vsperfcmd.md).