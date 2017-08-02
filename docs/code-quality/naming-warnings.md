---
title: "Advertencias sobre nomenclatura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.namingrules"
helpviewer_keywords: 
  - "advertencias de análisis de código administrado, advertencias de nomenclatura"
  - "advertencias de nomenclatura"
  - "advertencias, nomenclatura"
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Advertencias sobre nomenclatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las advertencias de nomenclatura son compatibles con el cumplimiento de las convenciones de nomenclatura de las Instrucciones de diseño de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## En esta sección  
  
|Regla|Descripción|  
|-----------|-----------------|  
|[CA1700: No nombrar valores de enumeración como 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Esta regla supone que un miembro de la enumeración con un nombre que contiene la palabra "reserved" no se utiliza actualmente pero hace de marcador de posición para que se pueda quitar o cambiar el nombre en una versión posterior.  Quitar o cambiar el nombre de un miembro es un cambio importante.|  
|[CA1713: Los eventos no deberían tener prefijos antes ni después](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|El nombre de un evento empieza por "Before" o "After".  Para nombrar los eventos relacionados que se provocan en una secuencia específica, utilice el tiempo presente o pasado para indicar la posición relativa en la secuencia de acciones.|  
|[CA1714: Las enumeraciones Flags deberían tener nombres en plural](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Una enumeración pública tiene el atributo System.FlagsAttribute y su nombre no termina en "s".  Los tipos marcados con FlagsAttribute tienen nombres en plural porque el atributo indica que se puede especificar más de un valor.|  
|[CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|El nombre de un identificador visible externamente contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.|  
|[CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Los identificadores de los espacios de nombres, miembros y parámetros no puede distinguirse sólo por mayúsculas o minúsculas porque los lenguajes que tienen como destino el Common Language Runtime no necesitan distinguir entre mayúsculas y minúsculas.|  
|[CA1715: Los identificadores deberían tener el prefijo correcto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|El nombre de una interfaz visible externamente no empieza por "I" mayúscula.  El nombre de un parámetro de tipo genérico en un tipo o método visibles externamente no empieza por "T" mayúscula.|  
|[CA1720: Los identificadores no deben contener nombres de tipo](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|El nombre de un parámetro en un miembro visible externamente contiene un nombre de tipo de datos o el nombre de un miembro visible externamente contiene un nombre de tipo de datos específico del lenguaje.|  
|[CA1722: Los identificadores no deberían tener el prefijo incorrecto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Por convención, sólo ciertos elementos de programación tienen nombres que comienzan con un prefijo concreto.|  
|[CA1711: Los identificadores no deberían tener el sufijo incorrecto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Por convención, los nombres de tipos que extienden determinados tipos base o que implementan algunas interfaces, o tipos derivados de estos tipos, deben terminar con unos sufijos reservados específicos.  Otros nombres de tipo no deben utilizar estos sufijos reservados.|  
|[CA1717: Solo las enumeraciones FlagsAttribute deberían tener nombres en plural](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Las convenciones de nomenclatura establecen que un nombre en plural para una enumeración indica que se pueden especificar varios valores de enumeración al mismo tiempo.|  
|[CA1725: Los nombres de parámetro deberían coincidir con la declaración base](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|El uso del mismo nombre para un parámetro en una jerarquía de reemplazo aumenta la utilidad de los reemplazos de método.  Cuando el nombre de un parámetro en un método derivado es distinto del nombre de la declaración base, puede resultar difícil determinar si el método es un reemplazo del método base o una nueva sobrecarga del método.|  
|[CA1719: Los nombres de parámetro no deberían coincidir con los nombres de miembro](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Un nombre de parámetro debe comunicar el significado del parámetro y un nombre de miembro debe comunicar el significado del miembro.  Sería un diseño extraño si éstos fueran los mismos.  Denominar un parámetro igual que el nombre del miembro no es intuitivo y dificulta el uso de la biblioteca.|  
|[CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Cada palabra en la cadena de recursos se divide en tokens basándose en el uso de mayúsculas y minúsculas.  La biblioteca de correctores ortográficos de Microsoft comprueba cada combinación de dos tokens contiguos.  Si la reconoce, la palabra genera una infracción de la regla.|  
|[CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Una cadena de recurso contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.|  
|[CA1724: Los nombres de tipo no deben coincidir con los espacios de nombres](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Los nombres de tipo no deben coincidir con los nombres de espacios de nombres definidos en la biblioteca de clases de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Infringir esta regla puede reducir la utilidad de la biblioteca.|  
|[CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Por convención, los nombres del identificador no contienen el carácter de subrayado \(\_\).  Esta regla comprueba espacios de nombres, tipos, miembros y parámetros.|  
|[CA1721: Los nombres de propiedades no deberían coincidir con los métodos Get](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|El nombre de un miembro público o protegido empieza por "Get" y en cualquier otro caso coincide con el nombre de una propiedad pública o protegida. “Get” los métodos y las propiedades deben tener nombres que distingan claramente su función.|  
|[CA1716: Los identificadores no deberían coincidir con palabras clave](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Un nombre de espacio de nombres o un nombre de tipo coinciden con una palabra clave reservada en un lenguaje de programación.  Los identificadores para los espacios de nombres y tipos no deberían coincidir con palabras clave definidas por los lenguajes que tienen como destino el Common Language Runtime.|  
|[CA1726: Utilizar términos preferidos](../code-quality/ca1726-use-preferred-terms.md)|El nombre de un identificador visible externamente incluye un término para el que existe un término alternativo más apropiado.  Alternativamente, el nombre incluye el término "Flag" o "Flags".|  
|[CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Por convención, los nombres de parámetro utilizan la convención Camel de uso de mayúsculas, mientras que los nombres de espacio de nombres, tipo y miembro utilizan la convención Pascal.|  
|[CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|El nombre de un identificador contiene varias palabras y al menos una de ellas parece ser una palabra compuesta en la que no se utilizan correctamente las mayúsculas y minúsculas.|  
|[CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Los nombres de los miembros de la enumeración no llevan el nombre de tipo como prefijo porque se espera que sean herramientas de desarrollo las que proporcionen la información de tipo.|  
|[CA1710: Los identificadores deberían tener el sufijo correcto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Por convención, los nombres de tipos que extienden determinados tipos base o que implementan algunas interfaces, o tipos derivados de estos tipos, tienen un sufijo asociado al tipo base o a la interfaz.|