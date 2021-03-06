---
title: Put_addressmapenabled | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f139e6d034fc3b738e345f385fbb8e8ad2150da4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915391"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Especifica si se debe usar la asignación de dirección para traducir las direcciones de símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 NewVal  
 [in] Establecido en `TRUE` para habilitar la traducción de símbolos, o `FALSE` a deshabilitar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Ejecutable procesadores posterior a la actualización a veces el archivo ejecutable. DIA contiene un mecanismo para admitir la traducción de símbolos para el nuevo diseño.  
  
 Cuando se carga un archivo PDB, se habilita la asignación de dirección almacenada en el archivo. Veces, sin embargo, cuando una aplicación cliente que necesite proporcionar su propio mapa de direcciones mediante una llamada a la [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método. Si el `set_addressMap` método se realiza correctamente, la aplicación cliente debe llamar a la `put_addressMapEnabled` método con un `NewVal` parámetro de `TRUE` para habilitar el uso de esa asignación de dirección.  
  
 Se puede recuperar el estado actual de la asignación de dirección está habilitada con una llamada a la [Get_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)