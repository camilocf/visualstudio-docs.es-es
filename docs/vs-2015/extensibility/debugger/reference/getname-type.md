---
title: GETNAME_TYPE | Microsoft Docs
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
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2607ddd84ead55ed627c72e1c9fd2ec3e280349f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815955"
---
# <a name="getnametype"></a>GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica el tipo de nombre de archivos que se va a recuperar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>Miembros  
 GN_NAME  
 Especifica un nombre descriptivo del documento o del contexto.  
  
 GN_FILENAME  
 Especifica la ruta de acceso completa del documento o del contexto.  
  
 GN_BASENAME  
 Especifica un nombre de archivo base en lugar de una ruta de acceso completa del documento o del contexto.  
  
 GN_MONIKERNAME  
 Especifica un nombre único del documento o el contexto en el formulario de un moniker.  
  
 GN_URL  
 Especifica un nombre de la dirección URL del documento o del contexto.  
  
 GN_TITLE  
 Especifica un título del documento, si existe alguno.  
  
 GN_STARTPAGEURL  
 Obtiene la dirección URL de página inicial para los procesos.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan como parámetros a la [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), y [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) métodos para especificar qué tipo de nombre para devolver.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)

