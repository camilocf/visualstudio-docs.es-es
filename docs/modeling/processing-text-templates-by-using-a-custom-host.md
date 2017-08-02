---
title: "Processing Text Templates by using a Custom Host | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, in application or VS extension"
  - "text templates, custom directive hosts"
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 33
---
# Processing Text Templates by using a Custom Host
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El proceso de *transformación de plantillas de texto* toma un archivo de *plantilla de texto* como entrada y produce un archivo de texto como salida.  Puede llamar al motor de transformación de texto desde una extensión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o desde una aplicación independiente que se ejecuta en un equipo donde está instalado [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Sin embargo, debe proporcionar un *host de plantillas de texto*.  Esta clase conecta la plantilla al entorno, localizando recursos como ensamblados y archivos de inclusión, y trabajando con los mensajes de error y resultado.  
  
> [!TIP]
>  Si está escribiendo una extensión o paquete que se ejecutará con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], considere la posibilidad de utilizar el servicio de plantillas de texto, en lugar de escribir su propio host.  Para obtener más información, vea [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
> [!NOTE]
>  No se recomienda utilizar las transformaciones de plantilla de texto en aplicaciones de servidor.  No se recomienda utilizar las transformaciones de plantilla de texto excepto en un subproceso único.  Esto se debe a que el motor de plantillas de texto vuelve a utilizar un AppDomain único para traducir, compilar y ejecutar plantillas.  El código traducido no es seguro para subprocesos.  El motor está diseñado para procesar archivos en serie, como se encuentran en un proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en tiempo de diseño.  
>   
>  Para aplicaciones en tiempo de ejecución, considere la posibilidad de utilizar plantillas de texto preprocesadas: vea [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Si la aplicación utiliza un conjunto de plantillas que se corrigen en tiempo de compilación, resulta más sencillo usar plantillas de texto preprocesadas.  También puede utilizar ese enfoque si la aplicación se va a ejecutar en un equipo donde no está instalado [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Para obtener más información, vea [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## Ejecutar una plantilla de texto en la aplicación  
 Para ejecutar una plantilla de texto, se llama al método ProcessTemplate de <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 La aplicación debe encontrar y proporcionar la plantilla y debe trabajar con el resultado.  
  
 En el parámetro `host`, debe proporcionar una clase que implemente <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>.  El motor lo vuelve a llamar.  
  
 El host debe poder registrar errores, resolver referencias a archivos de ensamblado e inclusión, proporciona un dominio de aplicación en el que se pueda ejecutar la plantilla, y llamar el procesador adecuado para cada directiva.  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> se define en **Microsoft.VisualStudio.TextTemplating.\*.0.dll** y <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> se define en **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0.dll**.  
  
## En esta sección  
 [Walkthrough: Creating a Custom Text Template Host](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 Muestra cómo crear un host de plantilla de texto personalizado que permita disponer de la funcionalidad de plantilla de texto fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Referencia  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## Secciones relacionadas  
 [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md)  
 Describe cómo funciona la transformación de texto y qué partes se pueden personalizar.  
  
 [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Proporciona información general sobre los procesadores de directivas de plantilla de texto.