---
title: 'Error: ASP.NET no está instalado | Microsoft Docs'
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
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35268c6867c5438f2f3d0c4c4f9e649451a21991
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220979"
---
# <a name="error-aspnet-not-installed"></a>Error: ASP.NET no está instalado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este error se produce si [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] no está correctamente instalado en el equipo en el que intenta depurar. Esto puede significar que nunca se instaló [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] o que se instaló [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] antes que IIS.  
  
### <a name="to-reinstall-aspnet"></a>Para reinstalar ASP.NET  
  
1.  Desde una ventana del símbolo del sistema, ejecute el siguiente comando:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     donde *versión* representa el número de versión de .NET Framework instalada en el equipo, por ejemplo, v1.0.370. Puede determinar la versión de .NET framework consultando el `\WINDOWS\Microsoft.NET\Framework` directory.  
  
    > [!NOTE]
    >  Con Windows Server 2003, puede instalar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] utilizando **agregar o quitar programas** en el Panel de Control.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



