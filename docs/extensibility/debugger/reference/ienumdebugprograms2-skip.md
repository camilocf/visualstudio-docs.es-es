---
title: "IEnumDebugPrograms2::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPrograms2::Skip"
helpviewer_keywords: 
  - "IEnumDebugPrograms2::Skip"
ms.assetid: b283858b-b375-4760-bfec-ab37de89958d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugPrograms2::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

saltos sobre el número especificado de elementos.  
  
## Sintaxis  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\]  Número de elementos que se van a omitir.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si `celt` es mayor que el número de elementos restantes; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Si `celt` especifica un valor mayor que el número de elementos restantes, la enumeración se establece al final y se devuelve `S_FALSE` .  
  
## Vea también  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)