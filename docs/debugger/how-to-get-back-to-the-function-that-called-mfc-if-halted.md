---
title: 'Cómo: volver a la función que llamó a MFC cuando está detenido | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da15793027eb643078771d33464258fea73fec9d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283397"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Cómo: Volver a la función que llamó a MFC cuando está detenido
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Si ha usado el **interrumpir** comando el **depurar** menú para detener el programa y ha terminado en MFC, y que el problema está en el código, puede usar la ventana Pila de llamadas para volver a la función. Para obtener más información, consulte [Cómo: utilizar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
 A veces el código puede interrumpir el bombeo de mensajes. En ese caso, no hay ningún código de usuario en la pila de llamadas. Para evitar este problema, puede usar los puntos de interrupción (posiblemente con condiciones y recuentos de visitas) en lugar de la **interrumpir** comando. Para obtener más información, consulte [puntos de interrupción y puntos de seguimiento](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Para navegar a la función desde la que se llamó a MFC  
  
-   Use la **pila de llamadas** ventana.  
  
## <a name="see-also"></a>Vea también  
 [Preguntas frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)