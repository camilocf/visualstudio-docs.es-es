---
title: IDebugThread2::Resume | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86402ceed6050b95e27df059d662e377c007aa67
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863352"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Reanuda la ejecución de un subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwSuspendCount`  
 [out] Devuelve el recuento de suspensión después de la operación de reanudación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cada llamada a este método disminuye el recuento de suspensión hasta que llega a 0 en ese momento, realmente se reanuda la ejecución. Este recuento de suspensión se muestra en el **subprocesos** ventana de depuración.  
  
 Para cada llamada a este método, debe haber una llamada anterior a la [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) método. El recuento de suspensión determina cuántas veces el `IDebugThread2::Suspend` hasta ahora ha llamado al método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)

