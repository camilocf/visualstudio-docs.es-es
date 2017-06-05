---
title: "atEnd (M&#233;todo, Enumerator de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "atEnd"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "atEnd (método)"
ms.assetid: 326808fb-9a0f-428e-aff1-b11b237913f1
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# atEnd (M&#233;todo, Enumerator de JavaScript)
Devuelve un valor booleano que indica si el enumerador está al final de la colección.  
  
> [!WARNING]
>  Este objeto solo es compatible con Internet Explorer.  
  
## Sintaxis  
  
```  
  
myEnum.atEnd()  
```  
  
## Comentarios  
 La referencia *myEnum* necesaria es cualquier objeto `Enumerator`.  
  
 El método `atEnd` devuelve **true** si el elemento actual es el último de la colección, si la colección está vacía o si el elemento actual está sin definir. En caso contrario, devuelve **false**.  
  
## Ejemplo  
 En el siguiente código, el método `atEnd` se usa para determinar si se ha alcanzado el final de una lista de unidades:  
  
```javascript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## Requisitos  
 Se admite en los siguientes modos de documento: Modo de interpretación, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10. No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
 **Se aplica a**: [Enumerator \(Objeto\)](../../javascript/reference/enumerator-object-javascript.md)  
  
## Vea también  
 [item \(Método, Enumerator\)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveFirst \(Método, Enumerator\)](../../javascript/reference/movefirst-method-enumerator-javascript.md)   
 [moveNext \(Método, Enumerator\)](../../javascript/reference/movenext-method-enumerator-javascript.md)   
 [Enumerator \(Objeto\)](../../javascript/reference/enumerator-object-javascript.md)