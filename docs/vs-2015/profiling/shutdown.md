---
title: Apagar | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fcc2012f46311d51cfd7c50f28158a471b67e26
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269304"
---
# <a name="shutdown"></a>Apagar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **Apagar** espera a que termine o se desasocie cualquier proceso del que se generaron perfiles actualmente y, después, desactiva el generador de perfiles y cierra el archivo de datos de generación de perfiles. La opción **Apagar** debe ser el último comando de una ejecución de generación de perfiles.  
  
 Si no se especifica un parámetro de tiempo de espera, la opción **Apagar** esperará indefinidamente. Si se especifica un parámetro de tiempo de espera, la opción vuelve tras el número de segundos especificado sin desactivar el generador de perfiles ni cerrar el archivo de datos.  
  
 La opción **Apagar** debe ser la única especificada en la línea de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Timeout`  
 -   (Opcional) Si se especifica, la opción vuelve tras el número de segundos especificado sin desactivar el generador de perfiles ni cerrar el archivo de datos de generación de perfiles.  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)



