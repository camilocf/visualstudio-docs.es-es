---
title: "IDiaSectionContrib::get_notCached | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSectionContrib::get_notCached (método)"
ms.assetid: 5408ea53-f64c-431e-9f62-62819026b038
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSectionContrib::get_notCached
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una marca que indica si la sección no se puede almacenar en memoria caché.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_notCached (   
   BOOL* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve `TRUE` si la sección no se puede almacenar en memoria caché; de lo contrario, devuelve `FALSE`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)