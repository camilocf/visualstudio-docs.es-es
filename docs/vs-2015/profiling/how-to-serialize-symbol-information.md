---
title: 'Cómo: Serializar la información de símbolos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6c0e567131d36cbc7e805533f7d5acb9c5f3277
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256560"
---
# <a name="how-to-serialize-symbol-information"></a>Cómo: Serializar la información de símbolos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede serializar símbolos que debe tener para analizar la aplicación. La serialización de símbolos agrega símbolos al archivo .vsp. Al agregar información de símbolos al archivo .vsp, otras personas pueden analizar un informe de rendimiento sin tener acceso a los símbolos originales. Si no se serializan los símbolos, debe tener archivos .exe y .pdb originales instrumentados para analizar el archivo .vsp.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Para serializar información de símbolos automáticamente  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
     Se mostrará el cuadro de diálogo **Opciones**.  
  
2.  Haga clic en **Herramientas de rendimiento**.  
  
3.  En **Configuración general**, seleccione **Serializar información de símbolos automáticamente**.  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [Cómo: Guardar archivos del informe analizado](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556)



