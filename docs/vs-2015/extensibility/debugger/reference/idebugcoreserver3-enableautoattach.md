---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
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
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e15d24220e4a646017a7e04cb5a0cfdc03f593eb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862728"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Habilita la asociación automática para los motores de depuración especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rgguidSpecificEngines`  
 [in] Matriz de GUID para cada motor de depuración que se va a marcar como asociar en automático.  
  
 `celtSpecificEngines`  
 [in] El número de motores especificado en `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] La dirección URL de inicio a usar al adjuntar en automático.  
  
 `pbstrSessionID`  
 [out] Identificador de la sesión que estaba conectado a la automática.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error. Un código de error es `E_AUTO_ATTACH_NOT_REGISTERED`, lo que indica que el generador de clases auto-attach no se ha registrado.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se inicia un programa asociado con la dirección URL especificada, los motores de depuración especificado se inicia automáticamente y se adjuntan.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

