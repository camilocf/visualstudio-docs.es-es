---
title: IEnumDebugObjects::Next | Microsoft Docs
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
- IEnumDebugObjects::Next
helpviewer_keywords:
- IEnumDebugObjects::Next method
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3b5b78b6cb592812cd7da15fa421ccfa10c0d7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923360"
---
# <a name="ienumdebugobjectsnext"></a>IEnumDebugObjects::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método devuelve el siguiente conjunto de elementos de la enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Next(  
   ULONG          celt,  
   IDebugObject** rgelt,  
   ULONG*         pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint           celt,  
   IDebugObject[] rgelt,  
   ref uint       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de elementos que se va a recuperar. También especifica el tamaño máximo de la `rgelt` matriz.  
  
 `rgelt`  
 [in, out] Matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) elementos que deben rellenarse.  
  
 `pceltFetched`  
 [out] Devuelve el número de elementos realmente devueltos en `rgelt`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si podrían devolverse un menor que el número solicitado de elementos; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

