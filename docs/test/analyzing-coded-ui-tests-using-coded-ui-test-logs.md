---
title: Analizar pruebas de IU codificadas usando los registros de pruebas de IU codificadas | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e795873-1d4b-4a13-a52a-a411d87fb759
caps.latest.revision: 13
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 5f32c2bc9f289a69a5ef9e7acfc1a973017fec0f
ms.contentlocale: es-es
ms.lasthandoff: 05/13/2017

---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analizar pruebas de IU codificadas usando los registros de pruebas de IU codificadas
Los registros de pruebas de IU programadas filtran y guardan información importante sobre las series de pruebas de IU programadas.  
  
 **Requisitos**  
  
-   Visual Studio Enterprise  
  
## <a name="why-should-i-do-this"></a>¿Por qué debo hacerlo?  
 Los registros se muestran en un formato que permite depurar problemas rápidamente.  
  
## <a name="how-do-i-do-this"></a>¿Cómo lo hago?  
  
### <a name="step-1-enable-logging"></a>Paso 1: habilitar el registro  
 Según su escenario, use uno de los siguientes métodos para habilitar el registro.  
  
-   .NET Framework versión 4 de destino sin archivo App.config en el proyecto de prueba  
  
    -   Abra el archivo **QTAgent32_40.exe.config**.  
  
         De forma predeterminada, este archivo se encuentra en **\<Letra de disco:>\Archivos de programa (x86)\Microsoft Visual Studio 12.0\Common7\IDE**.  
  
         Modifique el valor de EqtTraceLevel para que tenga el nivel de registro que quiera.  
  
         Guarde el archivo.  
  
-   .NET Framework versión 4.5 de destino sin archivo App.config en el proyecto de prueba  
  
    -   Abra el archivo **QTAgent32.exe.config**.  
  
         De forma predeterminada, este archivo se encuentra en **\<Letra de disco:>\Archivos de programa (x86)\Microsoft Visual Studio 12.0\Common7\IDE**.  
  
         Modifique el valor de EqtTraceLevel para que tenga el nivel de registro que quiera.  
  
         Guarde el archivo.  
  
-   Archivo App.config en el proyecto de prueba  
  
    -   Abra el archivo App.config en el proyecto.  
  
         Agregue el siguiente código bajo el nodo de configuración:  
  
         `<system.diagnostics>     <switches>       <add name="EqtTraceLevel" value="4" />     </switches>  </system.diagnostics>`  
  
-   Habilitar el registro desde el propio código de prueba  
  
    -   <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState.AllActionSnapshot;  
  
### <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Paso 2: ejecutar la prueba de interfaz de usuario codificada y ver el registro  
 Cuando ejecute una prueba de IU codificada una vez realizadas las modificaciones en el archivo **QTAgent32.exe.config**, verá que hay un vínculo de salida en los resultados del Explorador de pruebas. Los archivos de registro no solo se generan cuando la prueba produzca un error, sino también para las pruebas correctas cuando el nivel de seguimiento sea "detallado".  
  
1.  En el menú **PRUEBA**, seleccione **Ventanas** y después elija **Explorador de pruebas**.  
  
2.  En el menú **COMPILAR**, elija **Compilar solución**.  
  
3.  En el Explorador de pruebas, seleccione la prueba de IU codificada que quiera ejecutar, abra el menú contextual y después elija **Ejecutar pruebas seleccionadas**.  
  
     Las pruebas automatizadas se ejecutarán e indicarán si se superaron o no.  
  
    > [!TIP]
    >  Para ver el Explorador de pruebas desde el **Menú de prueba**, señale **Ventanas** y después elija **Explorador de pruebas**.  
  
4.  Elija el vínculo **Resultado** en el Explorador de pruebas.  
  
     ![Vínculo de resultados del Explorador de pruebas](../test/media/cuit_htmlactionlog1.png "CUIT_HTMLActionLog1")  
  
     Con esto se muestra el resultado de la prueba que incluirá un vínculo al registro de acciones.  
  
     ![Vínculos de salida y resultados de prueba de IU programada](../test/media/cuit_htmlactionlog2.png "CUIT_HTMLActionLog2")  
  
5.  Elija el vínculo UITestActionLog.html.  
  
     El registro se muestra en el explorador web.  
  
     ![Archivo de registro de prueba de IU codificada](../test/media/cuit_htmlactionlog3.png "CUIT_HTMLActionLog3")  
  
## <a name="q--a"></a>Preguntas y respuestas  
  
### <a name="q-what-happened-to-the-enablehtmllogger-key"></a>P: ¿Qué sucedió con la clave EnableHtmlLogger?  
 En versiones anteriores de Visual Studio, había dos opciones de configuración adicionales para habilitar el registrador Html en Prueba de IU codificada:  
  
```  
  
<add key="EnableHtmlLogger" value="true"/>  
  
<add key="EnableSnapshotInfo" value="true"/>  
  
```  
  
 Estas dos opciones están desusadas desde Visual Studio 2012. EqtTraceLevel es la única opción que se debe modificar para habilitar HtmlLogger.  
  
## <a name="see-also"></a>Vea también  
 [Usar UI Automation para probar el código](../test/use-ui-automation-to-test-your-code.md)   
 [Cómo: Ejecutar pruebas desde Microsoft Visual Studio](http://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
