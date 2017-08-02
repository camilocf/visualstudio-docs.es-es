---
title: "Agregar din&#225;micamente elementos de men&#250; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DYNAMICITEMSTART"
  - "elementos de menú, agregar dinámicamente"
  - "menús, agregar elementos dinámicos"
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 37
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 37
---
# Agregar din&#225;micamente elementos de men&#250;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede agregar elementos de menú en tiempo de ejecución mediante la especificación de la `DynamicItemStart` comando marca en una definición de botón de marcador de posición en el archivo de la tabla de comandos \(.vsct\) de Visual Studio, a continuación, definir \(en código\), el número de menú de elementos para mostrar y controlar los comandos. Cuando se carga el paquete VSPackage, el marcador de posición se reemplaza con los elementos de menú dinámico.  
  
 Visual Studio utiliza listas dinámicas de la **usadas recientemente** lista \(MRU\), que muestra los nombres de los documentos que se han abierto recientemente, y el **Windows** lista que muestra los nombres de las ventanas que están abiertas actualmente. El `DynamicItemStart` marca en una definición de comando Especifica que el comando es un marcador de posición hasta que se abre el VSPackage. Cuando se abre el paquete VSPackage, el marcador de posición se reemplaza con 0 o más comandos que se crean en tiempo de ejecución y se agrega a la lista dinámica. No puede ver la posición en el menú donde la lista dinámica aparece hasta que se abre el VSPackage. Para rellenar la lista dinámica, Visual Studio pide el VSPackage para buscar un comando con un identificador cuyos primeros caracteres son los mismos que el identificador del marcador de posición. Cuando Visual Studio se encuentra un comando, agrega el nombre del comando a la lista dinámica. A continuación, incrementa el identificador y busca otro comando coincidente agregar a la lista dinámica hasta que no haya comandos no hay más dinámicos.  
  
 Este tutorial muestra cómo establecer el proyecto de inicio en una solución de Visual Studio con un comando en el **el Explorador de soluciones** barra de herramientas. Utiliza un controlador de menú que tiene una lista desplegable dinámica de los proyectos de la solución activa. Para evitar que este comando que aparece cuando no hay ninguna solución está abierta o cuando la solución abierta tiene solo un proyecto, se carga el VSPackage sólo cuando tiene una solución de varios proyectos.  
  
 Para obtener más información acerca de los archivos .vsct, vea [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## Crear una extensión con un comando de menú  
  
1.  Cree un proyecto VSIX denominado `DynamicMenuItems`.  
  
2.  Cuando se abre el proyecto, agregue una plantilla de elemento de comando personalizado y asígnele el nombre **DynamicMenu**. Para obtener más información, consulta [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## Configuración de los elementos en el archivo .vsct  
 Para crear un controlador de menú con los elementos de menú dinámico en una barra de herramientas, especifique los siguientes elementos:  
  
-   De comandos dos grupos, uno que contiene el controlador del menú y otra que contiene los elementos de menú en la lista desplegable  
  
-   Un elemento de menú de tipo `MenuController`  
  
-   Dos botones, uno que actúa como marcador de posición para los elementos de menú y otro que proporciona el icono y la información sobre herramientas en la barra de herramientas.  
  
1.  En DynamicMenuPackage.vsct, defina los identificadores de comando. Vaya a la sección de símbolos y reemplace los elementos IDSymbol en la **guidDynamicMenuPackageCmdSet** GuidSymbol bloque. Debe definir elementos de IDSymbol para los dos grupos, el controlador del menú, el comando de marcador de posición y el comando de delimitador.  
  
    ```c#  
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">  
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />  
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />  
        <IDSymbol name="MyMenuController" value ="0x1030"/>  
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />  
        <!-- NOTE: The following command expands at run time to some number of ids.  
         Try not to place command ids after it (e.g. 0x0105, 0x0106).  
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->  
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />  
    </GuidSymbol>    
    ```  
  
2.  En la sección grupos, elimine los grupos existentes y agregue los dos grupos que acaba de definir:  
  
    ```  
    <Groups>  
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.   
             The 0x4000 priority adds this group after the group that contains the  
             Preview Selected Items button, which is normally at the far right of the toolbar. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />  
        </Group>  
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />  
        </Group>  
    </Groups>  
    ```  
  
     Agregue el MenuController. Establezca el indicador de comando DynamicVisibility, puesto que no siempre es visible. No se muestra el ButtonText.  
  
    ```  
    <Menus>  
        <!-- The MenuController to display on the Solution Explorer toolbar.  
             Place it in the ToolbarItemGroup.-->  
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />  
            <CommandFlag>DynamicVisibility</CommandFlag>  
            <Strings>  
               <ButtonText></ButtonText>  
           </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
3.  Agregue dos botones, uno como marcador de posición para los elementos de menú dinámico y otro como un delimitador para el MenuController.  
  
     El elemento primario del botón de marcador de posición es el **MyMenuControllerGroup**. Agregar marcadores de comando DynamicItemStart, DynamicVisibility y textoCambia el botón de marcador de posición. No se muestra el ButtonText.  
  
     El botón de anclaje contiene el icono y el texto de información sobre herramientas. El elemento primario del botón de anclaje es también el **MyMenuControllerGroup**. Agregar el indicador de comando NoShowOnMenuController para asegurarse de que el botón no aparece realmente en el menú desplegable de controlador y el indicador de comando FixMenuController para que sea el delimitador permanente.  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
    <Buttons>  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <CommandFlag>DynamicItemStart</CommandFlag>  
          <CommandFlag>DynamicVisibility</CommandFlag>  
          <CommandFlag>TextChanges</CommandFlag>  
          <!-- This text does not appear. -->  
          <Strings>  
            <ButtonText>Project</ButtonText>  
          </Strings>  
        </Button>  
  
        <!-- The anchor item to supply the icon/tooltip for the MenuController -->  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->  
          <Icon guid="guidImages" id="bmpPicArrows"/>  
          <!-- Do not show on the menu controller's drop down list-->  
          <CommandFlag>NoShowOnMenuController</CommandFlag>  
          <!-- Become the permanent anchor item for the menu controller -->  
          <CommandFlag>FixMenuController</CommandFlag>  
          <!-- The text that appears in the tooltip.-->  
          <Strings>  
            <ButtonText>Set Startup Project</ButtonText>  
          </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
4.  Agregar un icono al proyecto \(en la carpeta de recursos\) y, a continuación, agregue la referencia a ella en el archivo .vsct. En este tutorial, usamos el icono de las flechas que se incluye en la plantilla de proyecto.  
  
5.  Agregue una sección VisibilityConstraints fuera de la sección de comandos inmediatamente antes de la sección de símbolos. \(Puede recibir una advertencia si agrega después de símbolos\). En esta sección se asegura de que el controlador del menú aparece sólo cuando se carga una solución con varios proyectos.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## Implementar el comando de menú dinámico  
 Crear una clase de comando de menú dinámico que hereda de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. En esta implementación, el constructor especifica un predicado que se usará para la coincidencia de comandos. Debe invalidar el <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> método utilizar este predicado para establecer el <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> propiedad, que identifica el comando que se va a invocar.  
  
1.  Crear un nuevo archivo de clase en C\# con el nombre denominado DynamicItemMenuCommand.cs y agregue una clase denominada **DynamicItemMenuCommand** que hereda de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```c#  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Agregue las siguientes instrucciones using:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Agregue un campo privado para almacenar el predicado de coincidencia:  
  
    ```c#  
    private Predicate<int> matches;  
  
    ```  
  
4.  Agregue un constructor que hereda de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> constructor y especifica un controlador de comandos y un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> controlador. Agregar un predicado para hacer coincidir el comando:  
  
    ```c#  
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)  
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)  
    {  
        if (matches == null)  
        {  
            throw new ArgumentNullException("matches");  
        }  
  
        this.matches = matches;  
    }  
    ```  
  
5.  Invalidar el <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> método por lo que llama las coincidencias predicado y establece el <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> propiedad:  
  
    ```c#  
    public override bool DynamicItemMatch(int cmdId)  
    {  
        // Call the supplied predicate to test whether the given cmdId is a match.  
        // If it is, store the command id in MatchedCommandid   
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.  
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.  
        if (this.matches(cmdId))  
        {  
            this.MatchedCommandId = cmdId;  
            return true;  
        }  
  
        this.MatchedCommandId = 0;  
        return false;  
    }  
    ```  
  
## Agregar el comando  
 El constructor de DynamicMenu es donde se configura los comandos de menú, incluidos los elementos de menú y menús dinámicos.  
  
1.  En DynamicMenuPackageGuids.cs, agregue el GUID del conjunto de comandos y el identificador de comando:  
  
    ```c#  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  En el archivo DynamicMenu.cs, agregue las siguientes instrucciones using:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  En la clase DynamicMenu, agregue un campo privado **dte2**.  
  
    ```c#  
    private DTE2 dte2;  
    ```  
  
4.  Agregue un campo privado rootItemId:  
  
    ```c#  
    private int rootItemId = 0;  
    ```  
  
5.  En el constructor DynamicMenu, agregue el comando de menú. En la sección siguiente se define el controlador de comandos, el `BeforeQueryStatus` controlador de eventos y el predicado de la coincidencia.  
  
    ```c#  
    private DynamicMenu(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.   
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);  
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,  
                IsValidDynamicItem,  
                OnInvokedDynamicItem,  
                OnBeforeQueryStatusDynamicItem);  
                commandService.AddCommand(dynamicMenuCommand);  
                }  
  
        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));  
    }  
    ```  
  
## Implementación de los controladores  
 Para implementar elementos de menú dinámico en un controlador de menú, debe controlar el comando cuando se hace clic en un elemento dinámico. También debe implementar la lógica que establece el estado del elemento de menú. Agregue los controladores a la clase DynamicMenu.  
  
1.  Para implementar el **establecer el proyecto de inicio** de comandos, agregue el **OnInvokedDynamicItem** controlador de eventos. Busca el proyecto cuyo nombre es el mismo que el texto del comando que se ha invocado y establece como proyecto de inicio estableciendo su ruta de acceso absoluta el <xref:EnvDTE.SolutionBuild.StartupProjects%2A> propiedad.  
  
    ```c#  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don’t need to do anything  
        if (invokedCommand.Checked)  
            return;  
  
        // Find the project that corresponds to the command text and set it as the startup project  
        var projects = dte2.Solution.Projects;  
        foreach (Project proj in projects)  
        {  
            if (invokedCommand.Text.Equals(proj.Name))  
            {  
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;  
                return;  
            }  
        }  
    }  
    ```  
  
2.  Agregue el `OnBeforeQueryStatusDynamicItem` controlador de eventos. Este es el controlador llamado antes de un `QueryStatus` eventos. Determina si el elemento de menú es un elemento "real", es decir, no el elemento marcador de posición, y si el elemento ya está activado \(lo que significa que el proyecto ya está establecido como proyecto de inicio\).  
  
    ```c#  
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;  
        matchedCommand.Enabled = true;  
        matchedCommand.Visible = true;  
  
        // Find out whether the command ID is 0, which is the ID of the root item.  
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,  
         // and IsValidDynamicItem won't be called.  
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);  
  
        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.  
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);  
  
        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;  
  
        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;  
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));  
  
        // Check the command if it isn't checked already selected  
        matchedCommand.Checked = (matchedCommand.Text == startupProject);  
  
        // Clear the ID because we are done with this item.  
        matchedCommand.MatchedCommandId = 0;  
    }  
    ```  
  
## Implementar el predicado de coincidencia de Id. de comando  
  
1.  Ahora implemente el predicado de la coincidencia. Necesitamos determinar dos cosas: primero, si el identificador de comando es válido \(es mayor o igual que el identificador de comando declarado\) y el segundo, si especifica un proyecto posibles \(es menor que el número de proyectos de la solución\).  
  
    ```c#  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## Establecer el VSPackage cargar sólo cuando tiene una solución de varios proyectos  
 Dado que el **establecer el proyecto de inicio** comando no tiene sentido a menos que la solución activa tiene más de un proyecto, puede establecer el VSPackage para cargar automáticamente solo en ese caso. Utiliza <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> junto con el contexto de la interfaz de usuario <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. En el archivo DynamicMenuPackage.cs, agregue los siguientes atributos para la clase DynamicMenuPackage:  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## Probar el comando establecer el proyecto de inicio  
 Ahora puede probar su código.  
  
1.  Compile la solución y comience la depuración. Debe aparecer la instancia experimental.  
  
2.  En la instancia experimental, abra una solución que tenga más de un proyecto.  
  
     Debería ver el icono de flecha en el **el Explorador de soluciones** barra de herramientas. Al expandirlo, aparecerán los elementos de menú que representan los diferentes proyectos de la solución.  
  
3.  Cuando se protege con uno de los proyectos, se convierte en el proyecto de inicio.  
  
4.  Cuando se cierre la solución o abra una solución que tiene solo un proyecto, desaparecerá el icono de la barra de herramientas.  
  
## Vea también  
 [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)