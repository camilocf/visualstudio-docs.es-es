---
title: IDebugExceptionEvent2::PassToDebuggee | Documentos de Microsoft
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
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 564f4bc5d824c2493e84a90fbdf3400b800e5207
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850508"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica si se debe pasar la excepción el programa que se está depurando cuando se reanuda la ejecución, o si debe descartarse la excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fPass`  
 [in] Distinto de cero (`TRUE`) si la excepción se debe pasar el programa que se está depurando cuando se reanuda la ejecución, o cero (`FALSE`) si la excepción debe descartarse.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Llamar a este método no hace realmente que cualquier código que se ejecutará en el programa que se está depurando. La llamada consiste simplemente en establecer el estado de la ejecución de código siguiente. Por ejemplo, las llamadas a la [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) método puede devolver `S_OK` con el [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` campo establecido en `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 El IDE puede recibir el [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) evento y llamar a la [continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md) método. El motor de depuración (DE) debe tener un comportamiento predeterminado para controlar el caso si el `PassToDebuggee` no se llama al método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)

