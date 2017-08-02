---
title: "Resolver ambig&#252;edad (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.Disambig"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Resolver ambigüedad (cuadro de diálogo)"
  - "depurador, cuadro de diálogo Resolver ambigüedad"
  - "depurar [C++], resolver ambigüedad"
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Resolver ambig&#252;edad (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El cuadro de diálogo `Resolve Ambiguity` aparece cuando el depurador no puede elegir qué ubicación va a mostrar.  Por ejemplo, si utiliza plantillas de C\+\+, puede crear varias funciones a partir de una única plantilla de función.  Si el depurador se detiene en una ubicación del código fuente de la plantilla, y elige `Go To Disassembly`, el depurador ofrece varias opciones.  Cada función creada a partir de la plantilla tiene su propio código de desensamblado, y el depurador no sabe qué código es el que debe mostrar.  El cuadro de diálogo `Resolve Ambiguity` permite seleccionar la ubicación deseada en una lista con todas las ubicaciones correspondientes.  
  
 `Choose the specific location`  
 Enumera todas las ubicaciones correspondientes del comando.  
  
 `Address`  
 Muestra las direcciones de memoria de cada función.  
  
 `Function`  
 Muestra el nombre de cada función.  
  
 `Module`  
 Muestra el módulo \(EXE o DLL\) que contiene el código objeto de la función.  
  
## Vea también  
 [Expresiones en el depurador](../debugger/expressions-in-the-debugger.md)