---
title: "Configuraci&#243;n del proyecto para una configuraci&#243;n de depuraci&#243;n de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCDebugSettings.WebBrowser.DebuggerType"
  - "VC.Project.IVCGPUDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.SymbolPath"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationCommand"
  - "VC.Project.IVCRemoteDebugPageObject.WorkingDirectory"
  - "VC.Project.VCDebugSettings.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.SQLDebugging"
  - "VC.Project.IVCRemoteDebugPageObject.Remote"
  - "VC.Project.IVCGPUDebugPageObject.CommandArguments"
  - "VC.Project.VCDebugSettings.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.SQLDebugging"
  - "VC.Project.IVCWebSvcDebugPageObject.HttpUrl"
  - "VC.Project.IVCLocalDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunCommand"
  - "VC.Project.IVCGPUDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCWebSvcDebugPageObject.DebuggerType"
  - "VC.Project.IVCRemoteDebugPageObject.CommandArguments"
  - "VC.Project.IVCRemoteDebugPageObject.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteMachine"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter"
  - "VC.Project.IVCGPUDebugPageObject.RemoteConnection"
  - "VC.Project.VCDebugSettings.PDBPath"
  - "VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory"
  - "VC.Project.VCDebugSettings.SQLDebugging"
  - "VC.Project.VCDebugSettings.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ShimCommand"
  - "VC.Project.IVCLocalDebugPageObject.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCLocalDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationArguments"
  - "VC.Project.IVCLocalDebugPageObject.Environment"
  - "VC.Project.IVCGPUDebugPageObject.DeploymentDirectory"
  - "VC.Project.IVCLocalDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.Environment"
  - "VC.Project.IVCGPUDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCLocalDebugPageObject.DebuggerType"
  - "VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl"
  - "VC.Project.IVCWebSvcDebugPageObject.SQLDebugging"
  - "VC.Project.IVCGPUDebugPageObject.AcceleratorType"
  - "VC.Project.IVCGPUDebugPageObject.Environment"
  - "VC.Project.VCDebugSettings.RemoteMachine"
  - "VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy"
  - "VC.Project.VCDebugSettings.WorkingDirectory"
  - "vs.debug.builds"
  - "VC.Project.VCDebugSettings.Attach"
  - "VC.Project.VCDebugSettings.HttpUrl"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptMode"
  - "VC.Project.IVCGPUDebugPageObject.Attach"
  - "VC.Project.IVCRemoteDebugPageObject.AdditionalFiles"
  - "VC.Project.IVCGPUDebugPageObject.Command"
  - "VC.Project.VCDebugSettings.Remote"
  - "VC.Project.IVCRemoteDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.EnvironmentMerge"
  - "VC.Project.IVCGPUDebugPageObject.MachineName"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - ".pdb (archivos), depurar la configuración del proyecto de compilación"
  - "/DEBUG (opción del vinculador)"
  - "/MAP (opción del vinculador)"
  - "/MAPINFO (opción del vinculador)"
  - "/PDB (opción del vinculador)"
  - "/PDBSTRIPPED (opción del vinculador)"
  - "/Z7 (opción del compilador) [C++]"
  - "/Zd (opción del compilador) [C++]"
  - "/ZI (opción del compilador) [C++]"
  - "compilaciones de depuración, configuración del proyecto"
  - "configuraciones de depuración, C++"
  - "DEBUG (opción del vinculador)"
  - "-DEBUG (opción del vinculador)"
  - "depurar [C++], configuración del depurador"
  - "MAP (opción del vinculador)"
  - "-MAP (opción del vinculador)"
  - "archivos de asignaciones, configuración del proyecto"
  - "MAPINFO (opción del vinculador)"
  - "-MAPINFO (opción del vinculador)"
  - "pdb (archivos), depurar la configuración del proyecto de compilación"
  - "PDB (opción del vinculador)"
  - "-PDB (opción del vinculador)"
  - "PDBSTRIPPED (opción del vinculador)"
  - "-PDBSTRIPPED (opción del vinculador)"
  - "configuraciones del proyecto, depuración"
  - "configuración de proyectos [Visual Studio]"
  - "configuración de proyectos [Visual Studio], configuraciones de depuración"
  - "proyectos [Visual Studio], configuraciones de depuración"
  - "Z7 (opción del compilador) [C++]"
  - "-Z7 (opción del compilador) [C++]"
  - "Zd (opción del compilador) [C++]"
  - "-Zd (opción del compilador) [C++]"
  - "ZI (opción del compilador) [C++]"
  - "-Zl (opción del compilador) [C++]"
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
caps.latest.revision: 49
caps.handback.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Configuraci&#243;n del proyecto para una configuraci&#243;n de depuraci&#243;n de C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Es posible cambiar la configuración del proyecto para la configuración de depuración de C o Visual C\+\+ en el cuadro de diálogo **Páginas de propiedades**, como se describe en [Cómo: Establecer configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md).  En las siguientes tablas se muestra dónde encontrar los valores relacionados con el depurador en el cuadro de diálogo **Páginas de propiedades**.  
  
> [!WARNING]
>  La configuración del proyecto de depuración en la categoría **Propiedades de configuración y depuración** para los componentes y aplicaciones de la Tienda Windows programados en C\+\+ es diferente.  Vea [Iniciar una sesión de depuración \(VB, C\#, C\+\+ y XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) en el Centro de desarrollo de Windows.  
  
 Especifique el depurador que va a utilizar en el cuadro de lista **Depurador para iniciar**.  La opción determinará qué propiedades serán visibles.  
  
 Cada vez que guarda la solución, la configuración de depuración se escribe y se guarda automáticamente en un archivo "de usuario" \(.vcxproj.user\).  
  
### Carpeta Propiedades de configuración \(categoría Depuración\)  
  
|**Configuración**|**Descripción**|  
|-----------------------|---------------------|  
|**Depurador para iniciar**|Especifica el depurador que se va a ejecutar, con las opciones siguientes:<br /><br /> -   **Depurador local de Windows**<br />-   **Depurador remoto de Windows**<br />-   **Depurador de explorador web**<br />-   **Depurador de servicio Web**|  
|**Comando** \(Depurador local de Windows\)|Especifica el comando usado para iniciar el programa que se está depurando en el equipo local.|  
|**Comando remoto** \(Depurador remoto de Windows\)|La ruta de acceso al archivo .exe en el equipo remoto.  Escriba la ruta de acceso como lo haría en el equipo remoto.|  
|**Argumentos de comandos** \(Depurador local de Windows y Depurador remoto de Windows\)|-   Especifica los argumentos del comando especificado anteriormente.<br /><br /> Puede utilizar los siguientes operadores de redirección en este cuadro:<br /><br /> \< `file`<br /> Lee stdin del archivo.<br /><br /> \> `file`<br /> Escribe stdout en el archivo.<br /><br /> \>\> `file`<br /> Agrega stdout al archivo.<br /><br /> 2\> `file`<br /> Escribe stderr en el archivo.<br /><br /> 2\>\> `file`<br /> Agrega stderr al archivo.<br /><br /> 2\> &1<br /> Envía el resultado de stderr \(2\) a la misma posición que stdout \(1\).<br /><br /> 1\> &2<br /> Envía el resultado de stdout \(1\) a la misma posición que stderr \(2\).<br /><br /> En la mayoría de los casos, estos operadores solo pueden utilizarse en aplicaciones de consola.|  
|**Directorio de trabajo**|Especifica el directorio de trabajo del programa que se está depurando en relación con el directorio del proyecto en el que se encuentra el archivo EXE.  Si lo deja en blanco, el directorio de trabajo será el directorio del proyecto.  Para la depuración remota, el directorio del proyecto estará en el servidor remoto.|  
|**Asociar** \(Depurador local de Windows y Depurador remoto de Windows\)|Especifica si se debe iniciar o asociar a la aplicación.  La configuración predeterminada es No.|  
|**Nombre de servidor remoto** \(Depurador remoto de Windows\)|Especifica el nombre de un equipo \(que no es el suyo\) en el que desea depurar una aplicación.<br /><br /> La macro de compilación RemoteMachine está establecida en el valor de esta propiedad; para obtener más información, vea [Macros para propiedades y comandos de compilación](/visual-cpp/ide/common-macros-for-build-commands-and-properties).|  
|**Conexión** \(Depurador remoto de Windows\)|Permite intercambiar entre los tipos de conexión estándar y sin autenticación para la depuración remota.  Especifique el nombre de un equipo remoto en el cuadro **Nombre de servidor remoto**.  Entre los tipos de conexión se incluyen los siguientes:<br /><br /> -   **Remoto con autenticación de Windows**<br />-   **Remoto sin autenticación \(únicamente nativo\)**<br /><br /> **Nota** La depuración sin autenticación puede dejar el equipo remoto expuesto a infracciones de seguridad.  El modo de autenticación de Windows es más seguro.<br /><br /> Para obtener más información, vea [Instalación de la depuración remota](../debugger/remote-debugging.md).|  
|**Dirección URL HTTP** \(Depurador de servicio Web y Depurador de explorador web\)|Especifica la dirección URL en la que se encuentra el proyecto que se depura.|  
|**Tipo de depurador**|Especifica el tipo de depurador que se va a utilizar: **Solo nativo**, **Solo administrado**, **Solo GPU**, **Mixto**, **Automático** \(valor predeterminado\) o **Script**.<br /><br /> -   **Solo nativo** es para código de C\+\+ no administrado.<br />-   **Solo administrado** es para código que se ejecuta bajo Common Language Runtime \(código administrado\).<br />-   **Mixto** invoca depuradores para código administrado y no administrado.<br />-   **Automático** determina el tipo de depurador en función de la información del compilador y del archivo EXE.<br />-   **Script** invoca a un depurador para los scripts.<br />-   **Solo GPU** es para el código de C\+\+ AMP que se ejecuta en un dispositivo GPU o en el rasterizador de referencia de DirectX.  Vea [Depurar código de GPU](../debugger/debugging-gpu-code.md).|  
|**Entorno** \(Depurador local de Windows\)|Especifica las variables de entorno del programa que se depura.  Use sintaxis de variable de entorno estándar \(por ejemplo, `PATH="%SystemRoot%\..."`\).  Estas variables reemplazan el entorno del sistema o se combinan con este, en función de la configuración **Combinar entorno**.  Cuando se hace clic en la columna de configuración, aparece "Editar…".  Haga clic en ese vínculo para modificar las variables de entorno.|  
|**Combinar entorno** \(Depurador local de Windows\)|Determina si las variables especificadas en el cuadro **Entorno** se combinarán con el entorno definido por el sistema operativo.  La configuración predeterminada es Sí.|  
|**Depuración de SQL** \(todos menos el Depurador de clúster MPI\)|Habilita la depuración de procedimientos SQL desde la aplicación de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  La configuración predeterminada es No.|  
|**Tipo de acelerador de depuración** \(solo depuración de GPU\)|Especifica el dispositivo GPU que se debe usar para la depuración.  La instalación de controladores de dispositivo para dispositivos GPU compatibles agregará opciones adicionales.  La configuración predeterminada es "GPU \- Emulador de software".|  
|**Comportamiento de interrupción predeterminado de GPU** \(solo para la depuración de GPU\)|Especifica si se debe generar un evento de punto de interrupción para cada subproceso de una deformación SIMD.  La configuración predeterminada consiste en generar el evento de punto de interrupción una sola vez por deformación.|  
|**Acelerador predeterminado de AMP** \(solo depuración de GPU\)|Especifica el acelerador predeterminado de AMP al depurar código de GPU.  Elija **Acelerador de software WARP** para investigar si un problema está provocado por el hardware o por un controlador en lugar de por el código.|  
|**Directorio de implementación** \(Depurador remoto de Windows\)|Especifica la ruta de acceso en el equipo remoto en la que se copiará el resultado del proyecto antes del lanzamiento.  La ruta de acceso puede ser un recurso compartido de red en el equipo remoto, o bien una ruta de acceso a una carpeta del equipo remoto.  La configuración predeterminada está vacía, lo que significa que el resultado del proyecto no se copia en un recurso compartido de red.  Para habilitar la implementación de los archivos, también debe activar la casilla **Implementar** en el cuadro de diálogo Administrador de configuración.  Para obtener más información, vea [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md).|  
|**Archivos adicionales para implementar** \(Depurador remoto de Windows\)|Si se establece la propiedad Directorio de implementación, será una lista delimitada por punto y coma de archivos adicionales que se deben copiar en el directorio de implementación.  La configuración predeterminada está vacía, lo que significa que no se copia ningún archivo adicional en el directorio de implementación.  Para habilitar la implementación de los archivos, también debe activar la casilla **Implementar** en el cuadro de diálogo Administrador de configuración.  Para obtener más información, vea [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md).|  
|**Implementar bibliotecas de depuración en tiempo de ejecución de Visual C\+\+** \(Depurador remoto de Windows\)|Si se establece la propiedad Directorio de implementación, especifica si las bibliotecas de tiempo de ejecución de depuración de Visual C\+\+ de la plataforma actual se deben copiar en el recurso compartido de red.  El valor predeterminado es Sí.|  
  
### Carpeta C\/C\+\+ \(categoría General\)  
  
|Configuración|Descripción|  
|-------------------|-----------------|  
|**Formato de la información de depuración** \([\/Z7, \/Zd, Zi, \/ZI](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\)|Especifica el tipo de información de depuración que se va a crear para el proyecto.<br /><br /> La opción predeterminada \(\/ZI\) crea una base de datos de programa \(PDB\) en formato compatible con Editar y continuar.  Para obtener más información, vea [\/Z7, \/Zd, \/Zi, \/ZI \(Formato de la información de depuración\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
### Carpeta C\/C\+\+ \(categoría Optimización\)  
  
|Configuración|Descripción|  
|-------------------|-----------------|  
|**Optimización**|Especifica si el compilador debe optimizar el código que produce.  La optimización cambia el código que se ejecuta.  El código optimizado ya no coincide con el código fuente.  Por tanto, la depuración resulta complicada.<br /><br /> La opción predeterminada **Deshabilitado \(\/0d\)** suprime la optimización.  Puede desarrollar con la optimización desactivada y activarla posteriormente cuando cree la versión de producción del código.|  
  
### Carpeta Vinculador \(categoría Depuración\)  
  
|Configuración|Descripción|  
|-------------------|-----------------|  
|**Generar información de depuración** \([\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info)\)|Indica al vinculador que incluya información de depuración, que tendrá el formato especificado mediante \/Z7, \/Zd, Zi o \/ZI.|  
|**Generar archivo de base de datos de programas** \([\/PDB:name](/visual-cpp/build/reference/pdb-use-program-database)\)|Especifique el nombre de un archivo PDB en este cuadro.  Debe seleccionar ZI o \/Zi en Formato de la información de depuración.|  
|**Quitar símbolos privados** \([\/PDBSTRIPPED:filename](/visual-cpp/build/reference/pdbstripped-strip-private-symbols)\)|Especifique el nombre de un archivo PDB en este cuadro si no desea incluir símbolos privados en dicho archivo.  Esta opción crea un segundo archivo de base de datos de programa \(PDB\) al generar la imagen de un programa con cualquiera de las opciones del compilador o el vinculador que generan archivos PDB, como \/DEBUG, \/Z7 o \/Zd.  O \/Zi.  En este segundo archivo PDB se omiten los símbolos que no se desea suministrar a los clientes.  Para obtener más información, vea [\/PDBSTRIPPED \(Quitar símbolos privados\)](/visual-cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Generar archivo de asignaciones** \([\/MAP](/visual-cpp/build/reference/map-generate-mapfile)\)|Indica al vinculador que genere un archivo de asignaciones durante la vinculación.  La configuración predeterminada es No.  Para obtener más información, vea [\/MAP \(Generar archivo de asignaciones\)](/visual-cpp/build/reference/map-generate-mapfile).|  
|**Nombre de archivo de asignaciones** \([\/MAP:](/visual-cpp/build/reference/map-generate-mapfile)*nombre*\)|Si elige Generar archivo de asignaciones, puede especificar el archivo de asignaciones en este cuadro.  Para obtener más información, vea [\/MAP \(Generar archivo de asignaciones\)](/visual-cpp/build/reference/map-generate-mapfile).|  
|**Exportaciones de asignaciones** \([\/MAPINFO:EXPORTS](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|Incluye las funciones exportadas en el archivo de asignaciones.  La configuración predeterminada es No.  Para obtener más información, vea [\/MAPINFO \(Incluir información en el archivo de asignaciones\)](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Ensamblado depurable** \([\/ASSEMBLYDEBUG](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|Especifica la configuración de la opción \/ASSEMBLYDEBUG del vinculador.  Los valores posibles son los siguientes:<br /><br /> -   **No se emitió el atributo Debuggable**.<br />-   **Seguimiento de runtime y deshabilitar optimizaciones \(\/ASSEMBLYDEBUG\)**.  Esta es la configuración predeterminada.<br />-   **No realizar seguimiento del motor en tiempo de ejecución ni habilitar optimizaciones \(\/ASSEMBLYDEBUG:DISABLE\)**.<br />-   **\<Heredar de primario o valores predeterminados del proyecto\>**.<br />-   Para obtener más información, vea [\/ASSEMBLYDEBUG \(Agregar DebuggableAttribute\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Puede cambiar esta configuración en la carpeta Propiedades de configuración \(categoría Depuración\) mediante programación a través de la interfaz de Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings.  Para obtener más información, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## Vea también  
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Creación y administración de proyectos de Visual C\+\+](/visual-cpp/ide/creating-and-managing-visual-cpp-projects)   
 [\/ASSEMBLYDEBUG \(Agregar DebuggableAttribute\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Macros para propiedades y comandos de compilación](/visual-cpp/ide/common-macros-for-build-commands-and-properties)