---
title: "IDiaSymbol::findInlineeLinesByRVA | Microsoft Docs"
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
ms.assetid: ac108db1-9dbf-4dc4-bf48-159ca8d3725c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::findInlineeLinesByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones que inline, directa o indirectamente, en este símbolo dentro de la dirección virtual relativa especificada \(RVA\).  
  
## Sintaxis  
  
```cpp#  
HRESULT findInlineeLinesByRVA (   
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parámetros  
 `rva`  
 \[in\] especifica la dirección como RVA.  
  
 `length`  
 \[in\] especifica el intervalo de direcciones, en número de bytes, para cubrir con esta consulta.  
  
 `ppResult`  
 \[out\] contiene un objeto de `IDiaEnumLineNumbers` que contiene la lista de números de línea se recuperen que.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)