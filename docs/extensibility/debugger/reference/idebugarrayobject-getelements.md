---
title: IDebugArrayObject::GetElements | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7693c4ed3442cf86a0e310a6e2dd6d75655fcb69
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904731"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Obtiene un enumerador de todos los elementos de la matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) objeto que permite enumerar sobre todos los elementos.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Como alternativa, use el [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) y [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) métodos para recorrer en iteración los elementos.  
  
## <a name="see-also"></a>Vea también  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)