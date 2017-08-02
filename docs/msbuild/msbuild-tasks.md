---
title: Tareas de MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
caps.latest.revision: 18
author: kempb
ms.author: kempb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: cde7cf37c372caff4faa9ec88ecc5958112f0c6f
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-tasks"></a>Tareas de MSBuild
Una plataforma de compilación debe ser capaz de ejecutar cualquier número de acciones durante el proceso de compilación. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] utiliza *tareas* para realizar estas acciones. Una tarea es una unidad de código ejecutable que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] utiliza para realizar operaciones de compilación atómicas.  
  
## <a name="task-logic"></a>Lógica de las tareas  
 El formato de archivo de proyecto XML [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] no puede ejecutar completamente operaciones de compilación por sí mismo, de modo que la lógica de la tarea debe implementarse fuera del archivo del proyecto.  
  
 La lógica de ejecución de una tarea se implementa como una clase de .NET que implementa la interfaz <xref:Microsoft.Build.Framework.ITask>, que se define en el espacio de nombres <xref:Microsoft.Build.Framework>.  
  
 La clase de tarea también define los parámetros de entrada y salida disponibles para la tarea en el archivo del proyecto. En el archivo del proyecto se puede acceder a todas las propiedades públicas configurables no estáticas y no abstractas expuestas por la clase de tarea si se coloca un atributo correspondiente con el mismo nombre en el elemento [Task](../msbuild/task-element-msbuild.md).  
  
 Puede escribir su propia tarea mediante la creación de una clase administrada que implementa la interfaz <xref:Microsoft.Build.Framework.ITask>. Para obtener más información, consulte [Escribir tareas](../msbuild/task-writing.md).  
  
## <a name="executing-a-task-from-a-project-file"></a>Ejecutar una tarea desde un archivo del proyecto  
 Antes de ejecutar una tarea en el archivo del proyecto, primero debe asignar el tipo en el ensamblado que implementa la tarea al nombre de tarea con el elemento [UsingTask](../msbuild/usingtask-element-msbuild.md). Esto permite a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] saber dónde buscar la lógica de ejecución de la tarea cuando la encuentre en el archivo del proyecto.  
  
 Para ejecutar una tarea en un archivo del proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], cree un elemento con el nombre de la tarea como elemento secundario de un elemento `Target`. Si una tarea acepta parámetros, estos se pasan como atributos del elemento.  
  
 Las listas y propiedades de elementos [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se pueden utilizar como parámetros. Por ejemplo, el siguiente código llama a la tarea `MakeDir` y establece el valor de la propiedad `Directories` del objeto `MakeDir` igual que el valor de la propiedad `BuildDir` declarada en el ejemplo anterior.  
  
```xml  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 Las tareas también pueden devolver información al archivo del proyecto, que se puede almacenar en elementos o propiedades para su uso posterior. Por ejemplo, el siguiente código llama a la tarea `Copy` y almacena la información de la propiedad de salida `CopiedFiles` en la lista de elementos `SuccessfullyCopiedFiles`.  
  
```xml  
<Target Name="CopyFiles">  
    <Copy  
        SourceFiles="@(MySourceFiles)"  
        DestinationFolder="@(MyDestFolder)">  
        <Output  
            TaskParameter="CopiedFiles"  
            ItemName="SuccessfullyCopiedFiles"/>  
     </Copy>  
</Target>  
```  
  
## <a name="included-tasks"></a>Tareas incluidas  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se distribuye con muchas tareas, como por ejemplo [Copy](../msbuild/copy-task.md), que copia archivos, [MakeDir](../msbuild/makedir-task.md), que crea directorios, y [Csc](../msbuild/csc-task.md), que compila archivos de código fuente [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. Para obtener una lista completa de tareas disponibles e información de uso, consulte [Referencia de tareas](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Tareas invalidadas  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] busca tareas en varias ubicaciones. La primera ubicación es en archivos con la extensión .OverrideTasks almacenados en los directorios de .NET Framework. Las tareas en estos archivos invalidan cualquier otra tarea con los mismos nombres, incluidas las tareas en el archivo del proyecto. La segunda ubicación es en archivos con la extensión .Tasks en los directorios de .NET Framework. Si la tarea no se encuentra en ninguna de estas ubicaciones, se utiliza la tarea en el archivo del proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md)   
 [Escribir tareas](../msbuild/task-writing.md)   
 [Tareas insertadas](../msbuild/msbuild-inline-tasks.md)