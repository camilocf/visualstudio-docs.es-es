---
title: IDebugProcessEx2::Attach | Microsoft Docs
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
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 118b86193d9241744d5faae3719ad53a593537f4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830542"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método informa al proceso que una sesión es ahora el proceso de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pSession`  
 [in] Un valor que identifica de forma única la sesión que se asocia a este proceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La interfaz pasa `pSession` se trata solo como una cookie, un valor que identifica el Administrador de depuración de sesión asocia a este proceso; ninguno de los métodos en la interfaz proporcionado son funcional.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)

