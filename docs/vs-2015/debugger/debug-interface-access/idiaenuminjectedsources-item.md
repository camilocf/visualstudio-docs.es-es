---
title: Idiaenuminjectedsources | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ed1f8a82a6ef88a20a51d6bdfca64f9d362b114
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865081"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un origen insertado por medio de un índice.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 índice  
 [in] Índice de la [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) objeto va a recuperar. El índice es el intervalo de 0 a `count`-1, donde `count` devuelto por la [Idiaenuminjectedsources](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) método.  
  
 injectedSource  
 [out] Devuelve un [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) objeto que representa el origen insertado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)



