---
title: Get_farreturn | Microsoft Docs
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
- IDiaSymbol::get_farReturn method
ms.assetid: 141df0e9-f4d9-4330-a043-5d9ea865257f
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8adb02b4fdc17a1abf223cfb5287a36c232db279
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859153"
---
# <a name="idiasymbolgetfarreturn"></a>IDiaSymbol::get_farReturn
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una marca que especifica si la función contiene un extremo devuelto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_farReturn(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pFlag`  
 [in] Devuelve `TRUE` si la función utiliza un retorno lejano, en caso contrario, devuelve `FALSE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|Dia2.h|  
|Versión:|SDK de DIA v8.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



