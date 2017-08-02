---
title: "Generación de código y plantillas de texto T4 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: 82
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 5fe6da1276e74f5d7ad75096ae02df8fac3be159
ms.lasthandoff: 02/22/2017

---
# <a name="code-generation-and-t4-text-templates"></a>Generación de código y plantillas de texto T4
En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], *plantilla de texto T4* es una mezcla de bloques de texto y lógica de control que puede generar un archivo de texto. La lógica de control se escribe como fragmentos de código de programa en [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. En Visual Studio 2015 Update 2 y versiones posteriores, puede usar las características de la versión 6.0 de C# en las directivas de plantillas T4. El archivo generado puede ser texto de cualquier tipo, como una página web, un archivo de recursos o código fuente de programa en cualquier lenguaje.  
  
 Existen dos tipos de plantillas de texto T4:  
  
 **Las plantillas de texto T4 de tiempo de ejecución** (plantillas "preprocesadas") se ejecutan en la aplicación para generar cadenas de texto, normalmente como parte de la salida.  
 Por ejemplo, podría crear una plantilla para definir una página HTML:  
  
```  
<html><body>  
 The date and time now is: <#= DateTime.Now #>  
</body></html>  
```  
  
 Observe que la plantilla es similar a la salida generada. La similitud de la plantilla con la salida resultante le ayudará a evitar errores cuando quiera cambiarla.  
  
 Además, la plantilla contiene fragmentos de código de programa. Puede usar estos fragmentos para repetir secciones de texto, crear secciones condicionales y mostrar datos de la aplicación.  
  
 Para generar la salida, la aplicación llama a una función generada por la plantilla. Por ejemplo:  
  
```c#  
string webResponseText = new MyTemplate().TransformText();  
  
```  
  
 Puede ejecutar la aplicación en un equipo que no tiene [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalado.  
  
 Para crear una plantilla en tiempo de ejecución, agregue un archivo de **plantilla de texto preprocesada** al proyecto. Como alternativa, puede agregar un archivo de texto sin formato y establecer su propiedad **Herramienta personalizada** en **TextTemplatingFilePreprocessor**.  
  
 Para obtener más información, consulte [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Para obtener más información acerca de la sintaxis de plantillas, consulte [escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md).  
  
 **Plantillas de texto T4 de tiempo de diseño** se ejecutan en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para definir la parte del código fuente y otros recursos de la aplicación.  
 Por lo general, se usan varias plantillas que leen los datos de un único archivo de entrada o una única base de datos y se generan algunos de sus archivos `.cs`, `.vb`u otros archivos de código fuente. Cada plantilla genera un archivo. Se ejecutan dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 Por ejemplo, los datos de entrada podrían ser un archivo XML de datos de configuración. Siempre que edite el archivo XML durante el desarrollo, las plantillas de texto regenerarán parte del código de aplicación. Una de las plantillas podría parecerse al siguiente ejemplo:  
  
```  
<#@ output extension=".txt" #>  
<#@ assembly name="System.Xml" #>  
<#  
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.  
#>  
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>  
{  
  ... // More code here.   
}  
  
```  
  
 En función de los valores del archivo XML, el archivo `.cs` generado tendrá un aspecto similar al siguiente:  
  
```  
namespace Fabrikam.FirstJob  
{  
  ... // More code here.   
}  
```  
  
 A modo de ejemplo, la entrada podría ser un diagrama del flujo de trabajo de una actividad profesional. Si los usuarios cambian su flujo de trabajo profesional, o si empieza a trabajar con nuevos usuarios que tienen un flujo de trabajo diferente, es fácil regenerar el código para ajustarlo al nuevo modelo.  
  
 Las plantillas en tiempo de diseño permiten cambiar la configuración de manera más rápida y confiable cuando cambian los requisitos. Normalmente, la entrada se define en términos de requisitos empresariales, como en el ejemplo de flujo de trabajo. Esto permite analizar más fácilmente los cambios con los usuarios. Por tanto, las plantillas en tiempo de diseño son una herramienta útil en un proceso de desarrollo ágil.  
  
 Para crear una plantilla en tiempo de diseño, agregue un archivo de **plantilla de texto** al proyecto. Como alternativa, puede agregar un archivo de texto sin formato y establecer su propiedad **Herramienta personalizada** en **TextTemplatingFileGenerator**.  
  
 Para obtener más información, consulte [generación de código de tiempo de diseño mediante el uso de plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Para obtener más información acerca de la sintaxis de plantillas, consulte [escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  El término *modelo* se usa a veces para describir los datos que una o varias plantillas leen. El modelo puede tener cualquier formato y estar en cualquier tipo de archivo o base de datos. No tiene que ser un modelo UML ni un modelo de lenguaje específico de dominio. El término "modelo" solo indica que los datos se pueden definir en términos de conceptos de negocios, en lugar de parecerse al código.  
  
 El característica de transformación de plantillas de texto de denomina *T4*.  
  
## <a name="in-this-section"></a>En esta sección  
 [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md)  
 En cualquier aplicación que genere archivos de texto, las plantillas de texto precompiladas son un método sencillo y confiable para definir el texto. Sin embargo, este método no se puede usar para las plantillas de texto que cambian en tiempo de ejecución.  
  
 [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
 La generación de código y otros recursos a partir de un modelo permite actualizar la aplicación al actualizar el modelo.  
  
 [Generación de código en un proceso de compilación](../modeling/code-generation-in-a-build-process.md)  
 Si ha instalado [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK de modelado y visualización, puede asegurarse de que el software generado se mantiene actualizado con los cambios en el modelo.  
  
 [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)  
 Sintaxis de un archivo de plantilla de texto.  
  
 [Tutorial: Generar código mediante plantillas de texto](../modeling/walkthrough-generating-code-by-using-text-templates.md)  
 Demostración de una manera de usar la generación de código.  
  
 [Depurar una plantilla de texto T4](../modeling/debugging-a-t4-text-template.md)  
 Depuración de plantillas de texto y muestra de errores de plantilla de texto comunes.  
  
 [Generar archivos con la utilidad TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)  
 Herramienta de línea de comandos que puede usar para ejecutar transformaciones de plantilla de texto.  
  
 [Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)  
 Cómo escribir procesadores de directivas y hosts de plantillas personalizadas para sus propios orígenes de datos.  
  
## <a name="see-also"></a>Vea también  
 [Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)