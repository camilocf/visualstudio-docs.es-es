---
title: IDebugSymbolProviderDirect::GetCurrentModulesState | Microsoft Docs
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
- GetCurrentModulesState
- IDebugSymbolProviderDirect::GetCurrentModulesState
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20fbdad8263953caaea12ed102f6915de61fcb9d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933422"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesstate"></a>IDebugSymbolProviderDirect::GetCurrentModulesState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera información sobre el grupo de símbolos de los cuales el proveedor de símbolos es un miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetCurrentModulesState(  
    DWORD*          pState,  
    unsigned long * count  
);  
```  
  
```csharp  
int GetCurrentModulesState(  
    out uint pState,  
    out uint count  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pState`  
 [out] El estado del grupo del proveedor de símbolos.  
  
 `count`  
 [out] Número de módulos en el grupo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El estado cambia cada vez que un módulo se agrega o quita, el grupo de símbolos. Por lo tanto, este método puede utilizarse para detectar si se ha modificado un grupo de símbolos.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)

