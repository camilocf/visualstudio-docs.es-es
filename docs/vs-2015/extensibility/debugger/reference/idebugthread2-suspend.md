---
title: IDebugThread2::Suspend | Microsoft Docs
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
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f413cd2b296fddb2057d85becbe11d39b4b29d75
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877561"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Suspende un subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwSuspendCount`  
 [out] Devuelve el recuento de suspensión después de la operación de suspensión.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cada llamada a este método aumenta el recuento de suspensión superior a 0. Este recuento de suspensión se muestra en el **subprocesos** ventana de depuración.  
  
 Para cada llamada a este método, debe haber una llamada posterior a la [reanudar](../../../extensibility/debugger/reference/idebugthread2-resume.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)

