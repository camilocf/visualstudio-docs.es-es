---
title: "Cómo: migrar un lenguaje específico de dominio a una nueva versión | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 14
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 397efd1049ea52b2e7c67a46509d2a088c6fa488
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Cómo: Migrar lenguajes específicos de dominio a una nueva versión
Puede migrar proyectos que definen y utilizan los lenguajes específicos de dominio a [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] de la versión de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] que se distribuyó con [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
 Se proporciona una herramienta de migración como parte de [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. La herramienta convierte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyectos y soluciones que usan o definen herramientas DSL.  
  
 Debe ejecutar la herramienta de migración explícitamente: no se inicia automáticamente al abrir una solución en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. El documento de instrucciones detalladas y la herramienta se pueden encontrar en esta ruta de acceso:  
  
 **% Programa Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>Antes de migrar sus proyectos de DSL  
 La herramienta de migración modifica [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] archivos de proyecto (**.csproj**) y archivos de solución (**.sln**).  
  
#### <a name="to-prepare-projects-for-migration"></a>Para preparar los proyectos para la migración.  
  
-   Asegúrese de que el **.csproj** y **.sln** se pueden escribir archivos. Si ya están bajo control de código fuente, asegúrese de que están desprotegidos.  
  
-   Haga una copia de las carpetas que desea migrar.  
  
## <a name="migrating-a-collection-of-projects"></a>Migración de una colección de proyectos  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Migrar proyectos DSL y soluciones a Visual Studio 2010  
  
1.  Inicie la herramienta de migración de DSL.  
  
    -   Puede haga doble clic en la herramienta en el Explorador de Windows (o el Explorador de archivos) o iniciar la herramienta desde un símbolo del sistema. La herramienta se encuentra en esta ubicación:  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  Elija la carpeta que contiene las soluciones y proyectos que se va a convertir.  
  
    -   Escriba la ruta de acceso en el cuadro en la parte superior de la herramienta o haga clic en **examinar**.  
  
     La herramienta de migración muestra un árbol de proyectos que definir o usar DSL. El árbol incluye todos los proyectos que usa el **Microsoft.VisualStudio.Modeling.Sdk** o **TextTemplating** ensamblados.  
  
3.  Revise el árbol de proyectos y desactive los proyectos que no desea convertir.  
  
    -   Seleccione un proyecto o solución para ver una lista de cambios que realizará la herramienta.  
  
        > [!NOTE]
        >  Las casillas de verificación que aparecen junto a los nombres de carpetas no tienen ningún efecto. Debe expandir las carpetas para inspeccionar los proyectos y soluciones.  
  
4.  Convertir los proyectos.  
  
    1.  Haga clic en **convertir**.  
  
         Antes de cada archivo de proyecto se convierte una copia de *proyecto***.csproj** se guarda como *proyecto***. vs2008.csproj**  
  
         Una copia de cada *solución***.sln** se guarda como *solución***. vs2008.sln**  
  
    2.  Investigue las conversiones con errores que se notifican.  
  
         Errores se notifican en la ventana de texto. Además, la vista de árbol muestra un indicador rojo en cada nodo que no ha podido convertir. Puede hacer clic en el nodo para obtener más información acerca de dicho error.  
  
5.  **Transformar todas las plantillas** en soluciones que contengan correctamente convertir proyectos.  
  
    1.  Abra la solución.  
  
    2.  Haga clic en el **Transformar todas las plantillas** botón en el encabezado del explorador de soluciones.  
  
        > [!NOTE]
        >  Puede realizar este paso innecesario. Para obtener más información, consulte [cómo automatizar Transformar todas las plantillas](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
6.  Actualice el código personalizado en los proyectos convertidos.  
  
    -   Intente generar los proyectos e investigar los errores.  
  
    -   Probar su diseñador.  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vea también  
 [Blogs relacionados](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

