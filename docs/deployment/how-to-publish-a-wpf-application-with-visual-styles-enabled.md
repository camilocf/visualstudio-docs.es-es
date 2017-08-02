---
title: "C&#243;mo: Publicar una aplicaci&#243;n WPF con estilos visuales habilitados | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 3
caps.handback.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
---
# C&#243;mo: Publicar una aplicaci&#243;n WPF con estilos visuales habilitados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los estilos visuales permiten cambiar el aspecto de los controles comunes en función del tema elegido por el usuario.  De forma predeterminada, los estilos visuales no están habilitados para las aplicaciones de Windows Presentation Foundation \(WPF\), por lo que es necesario habilitarlos manualmente.  Sin embargo, habilitar los estilos visuales para una aplicación WPF y publicar después la solución produce un error.  En este tema se describe cómo resolver este error y el proceso para publicar una aplicación WPF con estilos visuales habilitados.  Para obtener más información sobre los estilos visuales, vea [Visual Styles Overview](http://msdn.microsoft.com/es-es/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e).  Para obtener más información acerca del mensaje de error, vea [Solucionar problemas de errores específicos de las implementaciones de ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Para resolver el error y publicar la solución, debe realizar las tareas siguientes:  
  
-   [Publicar la solución sin estilos visuales habilitados](#BKMK_publishsolwovs).  
  
-   [Crear un archivo de manifiesto](#BKMK_CreateManifest).  
  
-   [Incrustar el archivo de manifiesto en el archivo ejecutable de la solución publicada](#BKMK_embedmanifest).  
  
-   [Firmar los manifiestos de aplicación e implementación](#BKMK_signappdeplyman).  
  
 A continuación, podrá mover los archivos publicados a la ubicación desde la que desea que los usuarios finales instalen la aplicación.  
  
##  <a name="BKMK_publishsolwovs"></a> Publicar la solución sin estilos visuales habilitados  
  
1.  Asegúrese de que el proyecto no tiene estilos visuales habilitados.  En primer lugar, compruebe si existe el XML siguiente en el archivo de manifiesto del proyecto.  A continuación, si el XML está presente, inclúyalo en una etiqueta de comentario.  
  
     Los estilos visuales están deshabilitados de manera predeterminada.  
  
    ```  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     Los procedimientos siguientes muestran cómo abrir el archivo de manifiesto asociado al proyecto.  
  
    ###### Para abrir el archivo de manifiesto en un proyecto de Visual Basic  
  
    1.  En la barra de menús, elija **Proyecto**, **Propiedades de** *ProjectName*, donde *ProjectName* es el nombre del proyecto de WPF.  
  
         Aparecerán las páginas de propiedades del proyecto de WPF.  
  
    2.  En la pestaña **Aplicación**, elija **Ver configuración de Windows**.  
  
         El archivo app.manifest se abrirá en el **Editor de código**.  
  
    ###### Para abrir el archivo de manifiesto en un proyecto de C\#  
  
    1.  En la barra de menús, elija **Proyecto**, **Propiedades de** *ProjectName*, donde *ProjectName* es el nombre del proyecto de WPF.  
  
         Aparecerán las páginas de propiedades del proyecto de WPF.  
  
    2.  En la pestaña **Aplicación**, anote el nombre que aparece en el campo de manifiesto.  Este es el nombre del manifiesto que está asociado al proyecto.  
  
        > [!NOTE]
        >  Si aparece **Incrustar manifiesto con configuración predeterminada** o **Crear aplicación sin manifiesto** en el campo de manifiesto, los estilos visuales no están habilitados.  Si el nombre de un archivo de manifiesto aparece en el campo de manifiesto, continúe con el paso siguiente de este procedimiento.  
  
    3.  En el **Explorador de soluciones**, elija **Mostrar todos los archivos** \(\).  
  
         Este botón muestra todos los elementos del proyecto, incluidos los que se han excluido y los que normalmente están ocultos.  El archivo de manifiesto aparece como un elemento de proyecto.  
  
2.  Compile y publique la solución.  Para obtener más información sobre cómo publicar la solución, vea [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
##  <a name="BKMK_CreateManifest"></a> Crear un archivo de manifiesto  
  
1.  Pegue el código siguiente en un archivo de Bloc de notas.  
  
     Este XML describe el ensamblado que contiene los controles que admiten estilos visuales.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  En Bloc de notas, haga clic en **Archivo** y, a continuación, en **Guardar como.**  
  
3.  En el cuadro de diálogo **Guardar como**, en la lista desplegable **Guardar como tipo**, seleccione **Todos los archivos**.  
  
4.  En el cuadro **Nombre de archivo**, asigne un nombre al archivo y anexe .manifest al final de dicho nombre.  Por ejemplo: themes.manifest.  
  
5.  Elija el botón **Examinar carpetas**, seleccione una carpeta y, a continuación, haga clic en **Guardar**.  
  
    > [!NOTE]
    >  Los procedimientos restantes dan por supuesto que el nombre de este archivo es themes.manifest y que el archivo se guardará en el directorio de C:\\temp del equipo.  
  
##  <a name="BKMK_embedmanifest"></a> Incrustar el archivo de manifiesto en el archivo ejecutable de la solución publicada  
  
1.  Abra el **Símbolo del sistema de Visual Studio**.  
  
     Para obtener más información sobre cómo abrir el **símbolo del sistema de Visual Studio**, vea [Símbolos del sistema](../Topic/Developer%20Command%20Prompt%20for%20Visual%20Studio.md).  
  
    > [!NOTE]
    >  Los pasos restantes realizan las suposiciones siguientes sobre la solución:  
    >   
    >  -   El nombre de la solución es MyWPFProject.  
    > -   La solución está ubicada en el directorio siguiente: `%UserProfile%\Documents\Visual Studio 2010\Projects\`.  
    >   
    >      La solución se publica en el directorio siguiente: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.  
    > -   La versión más reciente de los archivos de aplicación publicados se encuentra en el directorio siguiente: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
    >   
    >  No es necesario usar el nombre o las ubicaciones de directorio descritas anteriormente.  El nombre y las ubicaciones descritos anteriormente se utilizan únicamente para mostrar los pasos necesarios para publicar la solución.  
  
2.  En el símbolo del sistema, cambie la ruta de acceso al directorio que contiene la versión más reciente de los archivos de aplicación publicados.  En el ejemplo siguiente se muestra cómo.  
  
    ```  
    cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
    ```  
  
3.  En el símbolo del sistema, ejecute el comando siguiente para incrustar el archivo de manifiesto en el archivo ejecutable de la aplicación.  
  
    ```  
    mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy  
    ```  
  
##  <a name="BKMK_signappdeplyman"></a> Firmar los manifiestos de aplicación e implementación  
  
1.  En el símbolo del sistema, ejecute el comando siguiente para quitar la extensión `.deploy` del archivo ejecutable del directorio actual.  
  
    ```  
    ren MyWPFApp.exe.deploy MyWPFApp.exe  
    ```  
  
    > [!NOTE]
    >  Este ejemplo supone que solo un archivo tiene la extensión de archivo `.deploy`.  Asegúrese de cambiar el nombre de todos los archivos de este directorio que tengan la extensión de archivo `.deploy`.  
  
2.  En el símbolo del sistema, ejecute el comando siguiente para firmar el manifiesto de aplicación,  
  
    ```  
    mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  Este ejemplo supone que se firma el manifiesto usando el archivo `.pfx` del proyecto.  Si no va a firmar el manifiesto, puede omitir el parámetro `–cf` que se usa en este ejemplo.  Si va a firmar el manifiesto con un certificado que requiere una contraseña, especifique la opción `–password` \(`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`\).  
  
3.  En el símbolo del sistema, ejecute el comando siguiente para agregar la extensión `.deploy` al nombre del archivo al que cambió de nombre en un paso anterior de este procedimiento.  
  
    ```  
    ren MyWPFApp.exe MyWPFApp.exe.deploy  
    ```  
  
    > [!NOTE]
    >  Este ejemplo supone que solo un archivo tenía la extensión de archivo `.deploy`.  Asegúrese de cambiar el nombre de todos los archivos de este directorio que tuvieran previamente la extensión de nombre de archivo `.deploy`.  
  
4.  En el símbolo del sistema, ejecute el comando siguiente para firmar el manifiesto de implementación,  
  
    ```  
    mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  Este ejemplo supone que se firma el manifiesto usando el archivo `.pfx` del proyecto.  Si no va a firmar el manifiesto, puede omitir el parámetro `–cf` que se usa en este ejemplo.  Si va a firmar el manifiesto con un certificado que requiere una contraseña, especifique la opción `–password`, como en este ejemplo:`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`.  
  
 Después de realizar estos pasos, puede mover los archivos publicados a la ubicación desde la que desea que los usuarios finales instalen la aplicación.  Si tiene intención de actualizar la solución con frecuencia, puede mover estos comandos a un script y ejecutar este cada vez que publique una nueva versión.  
  
## Vea también  
 [Solucionar problemas de errores específicos de las implementaciones de ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Visual Styles Overview](http://msdn.microsoft.com/es-es/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Enabling Visual Styles](VS|Controls|~\controls\userex\cookbook.htm)   
 [Símbolos del sistema](../Topic/Developer%20Command%20Prompt%20for%20Visual%20Studio.md)