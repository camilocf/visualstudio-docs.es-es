---
title: CONSTRUCTOR_ENUM | Microsoft Docs
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
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 032eb96110d6bd41173dfc1e48c5b777829691a9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876937"
---
# <a name="constructorenum"></a>CONSTRUCTOR_ENUM
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Selecciona distintos tipos de constructores.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
} CONSTRUCTOR_ENUM;  
```  
  
```csharp  
public enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
};  
```  
  
## <a name="members"></a>Miembros  
 crAll  
 Selecciona todos los constructores.  
  
 crNonStatic  
 Selecciona los constructores no estáticos.  
  
 crStatic  
 Selecciona los constructores estáticos.  
  
## <a name="remarks"></a>Comentarios  
 Se pasa como argumento a la [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)

