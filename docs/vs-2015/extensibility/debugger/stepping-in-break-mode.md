---
title: Ejecución paso a paso en modo de interrupción | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ac13b201534289cdb161980716bbfdeda7b969e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240609"
---
# <a name="stepping-in-break-mode"></a>Escalonado en modo de interrupción
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El siguiente describe el proceso que se produce cuando el depurador está en modo de interrupción y debe recorrer el código:  
  
## <a name="stepping-process"></a>Proceso de ejecución paso a paso  
  
1.  Llame a [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) con [STEPKIND](../../extensibility/debugger/reference/stepkind.md) y [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumentos al ejecutar un paso.  
  
2.  Cuando finalice el paso, enviar un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como un evento de detención.  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)

