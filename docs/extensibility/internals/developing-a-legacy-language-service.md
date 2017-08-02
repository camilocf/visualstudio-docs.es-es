---
title: "Desarrollar un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.vsip.LangServWiz.langtoks"
  - "vs.vsip.LangServWiz.welcome"
  - "vs.vsip.LangServWiz.langSpec"
  - "vs.vsip.LangServWiz.langInfo"
  - "vs.vsip.LangServWiz.langServOpts"
helpviewer_keywords: 
  - "Servicios de lenguaje, desarrollo"
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Desarrollar un servicio de lenguaje
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta sección contiene vínculos a temas que le ayudarán a crear un servicio de lenguaje heredado.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Se recomienda que comience a utilizar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## En esta sección  
 [Modelo de un servicio de lenguaje heredado](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Proporciona un modelo de un servicio de lenguaje mínimo para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor principal. Puede usar este modelo como guía para crear su propio servicio de lenguaje.  
  
 [Interfaces de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Describe los objetos necesarios para implementar un servicio de lenguaje y proporciona una lista de objetos adicionales que puede utilizar para proporcionar resaltado de sintaxis, los datos de método y otras características.  
  
 [Intercepción de comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Describe cómo insertar un filtro de comandos en el servicio de lenguaje para interceptar los comandos que de lo contrario podría administrar la vista de texto.  
  
 [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Proporciona información sobre cómo registrar el servicio de lenguaje utilizando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Soporte técnico de servicio de lenguaje para la depuración](../../extensibility/internals/language-service-support-for-debugging.md)  
 Describe cómo un servicio de lenguaje puede proporcionar características para admitir a un depurador.  
  
 [Lista de comprobación: Crear un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Proporciona instrucciones paso a paso para crear e integrar un servicio de lenguaje para el editor principal.  
  
## Secciones relacionadas  
 [Colores en un servicio de lenguaje heredado de sintaxis](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Describe cómo implementar el resaltado de sintaxis en el servicio de lenguaje.  
  
 [Finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Describe la finalización de instrucciones, el proceso por el que un servicio de lenguaje ayuda a los usuarios finalizar una palabra clave o el elemento que se haya iniciado escribiendo.  
  
 [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Describe cómo proporcionar sugerencias de método para métodos y funciones sobrecargadas.  
  
 [Cómo: proporcionar compatibilidad con texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Explica el propósito de una región de texto oculto y proporciona instrucciones sobre cómo implementar un área de texto oculto.  
  
 [Cómo: proporcionar soporte ampliado de esquematización en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Explica las dos opciones para amplían la compatibilidad de esquematización para el lenguaje más allá de admitir el *Contraer a definiciones* comando.