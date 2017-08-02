---
title: Solucionar problemas de referencias rotas | Microsoft Docs
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
ms.assetid: 00a9ade9-652e-40de-8ada-85f63cd183ee
caps.latest.revision: 15
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 61a074110e0a3730c971c319f98498324868067d
ms.contentlocale: es-es
ms.lasthandoff: 05/30/2017

---
# Solucionar problemas de referencias rotas
<a id="troubleshoot-broken-references" class="xliff"></a>
Si la aplicación intenta usar una referencia rota, se genera un error de excepción. La incapacidad de encontrar el componente al que se hace referencia es el desencadenador principal del error, pero hay varias situaciones en las que se puede considerar una referencia como rota. Estas instancias se muestran en la siguiente lista:  

-   La ruta de acceso de referencia del proyecto es incorrecta o está incompleta.  

-   Se ha eliminado el archivo al que se hace referencia.  

-   Se ha cambiado el nombre del archivo al que se hace referencia.  

-   Se ha producido un error en la conexión de red o en la autenticación.  

-   Se hace referencia a un componente COM que no está instalado en el equipo.  

 A continuación se ofrecen soluciones a estos problemas.  

> [!NOTE]
>  Se hace referencia a los archivos de los ensamblados mediante rutas de acceso absolutas en el archivo del proyecto. Por tanto, es posible que a los usuarios que trabajan en un entorno de varios desarrolladores les falte un ensamblado al que se hace referencia en su entorno local. Para evitar estos errores, en estos casos es mejor agregar referencias entre proyectos. Para más información, vea [Programar con ensamblados](/dotnet/framework/app-domains/programming-with-assemblies).

## La ruta de acceso de referencia es incorrecta
<a id="reference-path-is-incorrect" class="xliff"></a>  
 Si los proyectos se comparten en equipos diferentes, es posible que no se encuentren algunas referencias cuando un componente se encuentra en un directorio diferente en cada equipo. Las referencias se almacenan con el nombre del archivo de componente (por ejemplo, MyComponent). Cuando se agrega una referencia a un proyecto, la ubicación de la carpeta del archivo de componente (por ejemplo, C:\MyComponents\\) se anexa a la propiedad del proyecto **ReferencePath**.  

 Cuando se abre el proyecto, intenta encontrar estos archivos de componente a los que se hace referencia mediante una búsqueda en los directorios de la ruta de acceso de referencia. Si el proyecto se abre en un equipo que almacena el componente en otro directorio, por ejemplo, D:\MyComponents\\, no se puede encontrar la referencia y aparece un error en la lista de tareas.  

 Para corregir este problema, puede eliminar la referencia rota y después reemplazarla mediante el cuadro de diálogo Agregar referencia. Otra solución es usar el elemento **Reference Path** (Ruta de acceso de referencia) en las páginas de propiedades del proyecto y modificar las carpetas de la lista para que apunten a las ubicaciones correctas. La propiedad **Reference Path** se guarda para cada usuario en cada equipo. Por tanto, si modifica la ruta de acceso de referencia, esto no afecta a otros usuarios del proyecto.  

> [!TIP]
>  Las referencias entre proyectos no tienen estos problemas. Por este motivo, úselas en lugar de las referencias de archivo, si es posible.  

#### Para reparar una referencia de proyecto rota mediante la corrección de la ruta de acceso de referencia
<a id="to-fix-a-broken-project-reference-by-correcting-the-reference-path" class="xliff"></a>  

1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y haga clic en **Propiedades**.  

2.  Aparece el **Diseñador de proyectos**.  

3.  Si usa Visual Basic, seleccione la página **Referencias** y haga clic en el botón **Rutas de acceso de referencia**. En el cuadro de diálogo **Rutas de acceso de referencia**, escriba la ruta de acceso de la carpeta que contiene el elemento al que quiere hacer referencia en el campo **Carpeta** y luego haga clic en el botón **Agregar carpeta**.  

     O bien  

     Si usa Visual C#, seleccione la página **Rutas de acceso de referencia**. En el campo **Carpeta**, escriba la ruta de acceso de la carpeta que contiene el elemento al que quiere hacer referencia y luego haga clic en el botón **Agregar carpeta**.  

## Se ha eliminado el archivo al que se hace referencia
<a id="referenced-file-has-been-deleted" class="xliff"></a>  
 Es posible que el archivo al que se hace referencia se haya eliminado y ya no exista en la unidad.  

#### Para reparar una referencia de proyecto rota de un archivo que ya no existe en la unidad
<a id="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive" class="xliff"></a>  

-   Elimine la referencia.  

-   Si la referencia existe en otra ubicación del equipo, léala desde esa ubicación.  

## Se ha cambiado el nombre del archivo al que se hace referencia
<a id="referenced-file-has-been-renamed" class="xliff"></a>  
 Es posible que se haya cambiado el nombre del archivo al que se hace referencia.  

#### Para reparar una referencia rota de un archivo al que se le ha cambiado el nombre
<a id="to-fix-a-broken-reference-for-a-file-that-has-been-renamed" class="xliff"></a>  

-   Elimine la referencia y después agregue una referencia al archivo al que se le ha cambiado el nombre.  

-   Si la referencia existe en otra ubicación del equipo, tiene que leerla desde esa ubicación.

## Se ha producido un error en la conexión de red o en la autenticación
<a id="network-connection-or-authentication-has-failed" class="xliff"></a>  
 Puede haber varias causas por las que no se pueda tener acceso a los archivos, por ejemplo, una conexión de red o una autenticación incorrectas. Cada causa puede tener un único medio de recuperación; por ejemplo, es posible que tenga que ponerse en contacto con el administrador local para acceder a los recursos necesarios. No obstante, siempre hay la opción de eliminar la referencia y corregir el código en el que se usaba esa referencia.

## No se ha instalado el componente COM en el equipo
<a id="com-component-is-not-installed-on-computer" class="xliff"></a>  
 Si un usuario ha agregado una referencia a un componente COM y un segundo usuario intenta ejecutar el código en un equipo que no tenga este componente instalado, el segundo usuario recibirá un error que indica que la referencia está rota. Si se instala el componente en el segundo equipo, se corregirá el error. Para obtener más información sobre cómo usar referencias a componentes COM en los proyectos, consulte [Interoperabilidad COM en aplicaciones .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).  

## Vea también
<a id="see-also" class="xliff"></a>  
 [Página Referencias, Diseñador de proyectos (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)   
