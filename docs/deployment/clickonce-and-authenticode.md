---
title: "ClickOnce y Authenticode | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "archivos .pfx"
  - "implementación de ClickOnce, Authenticode"
  - "Authenticode, ClickOnce"
  - "implementación de ClickOnce, certificados"
  - "implementación de ClickOnce, seguridad"
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce y Authenticode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Authenticode* es una tecnología de Microsoft que usa una criptografía estándar del sector para firmar el código de una aplicación con certificados digitales que comprueban la autenticidad del publicador de la aplicación. Gracias al uso de Authenticode para la implementación de aplicaciones, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] reduce el riesgo de recibir un caballo de Troya. Un caballo de Troya es un virus u otro programa dañino creado por un tercero malintencionado y que aparenta ser un programa legítimo procedente de una fuente verificada y de confianza. La firma de implementaciones de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] con un certificado digital es un paso opcional para comprobar que los ensamblados y los archivos no se han alterado.  
  
 En las siguientes secciones se describen los distintos tipos de certificados digitales empleados en Authenticode, cómo se validan los certificados mediante entidades de certificación \(CA\), la función de la marca de tiempo en los certificados y los métodos de almacenamiento disponibles para los certificados.  
  
## Authenticode y la firma de código  
 Un *certificado digital* es un archivo que contiene un par de claves pública y privada criptográficas, junto con metadatos que describen el publicador para el que se emitió el certificado y la entidad que emitió el certificado.  
  
 Existen distintos tipos de certificados de Authenticode, cada uno de los cuales está configurado para distintos tipos de firma. Para las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], debe tener un certificado de Authenticode que sea válido para la firma de código. Si intenta iniciar sesión en una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] con otro tipo de certificado, como un certificado digital de correo electrónico, no funcionará. Para obtener más información, consulte [Introduction to Code Signing](http://go.microsoft.com/fwlink/?LinkId=179452) \(Introducción a la firma de código\).  
  
 Puede obtener un certificado de firma de código de tres maneras:  
  
-   Comprar un certificado a un proveedor de certificados.  
  
-   Recibir un certificado de un grupo de su organización que se encargue de crear certificados digitales.  
  
-   Generar su propio certificado con MakeCert.exe, que se incluye con [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
### Cómo ayuda a los usuarios el uso de entidades de certificación  
 Un certificado generado con la utilidad MakeCert.exe se suele denominar *SelfCert* o *certificado de prueba*. Este tipo de certificado funciona igual que un archivo .snk en .NET Framework. Consta solo de un par de claves criptográficas pública y privada y no contiene información comprobable del publicador. Puede usar los certificados SelfCert para implementar aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de gran confianza en una intranet. Pero cuando estas aplicaciones se ejecutan en un equipo cliente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las identificará como procedentes de un editor desconocido. De forma predeterminada, las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] firmadas con SelfCert e implementadas a través de Internet no pueden usar la implementación de aplicaciones de confianza.  
  
 Por el contrario, si recibe un certificado de una entidad de certificación \(CA\), como un proveedor de certificados o un departamento de su empresa, el certificado ofrece más seguridad a los usuarios. No solo identifica al publicador del software firmado, sino que verifica esa identidad comprobando la CA que lo firmó. Si la CA no es la entidad de certificación raíz, Authenticode también se volverá a “encadenar” a la entidad de certificación raíz para comprobar que la CA tiene autorización para emitir certificados. Para lograr una mayor seguridad, siempre que pueda debe usar un certificado emitido por una CA.  
  
 Para obtener más información sobre cómo generar certificados SelfCert, consulte [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md).  
  
### Marcas de tiempo  
 Los certificados usados para firmar aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] caducan una vez transcurrido un período determinado, que suele ser de doce meses. Para no tener que volver a firmar constantemente las aplicaciones con certificados nuevos, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] admite las marcas de tiempo. Al firmar una aplicación con una marca de tiempo, su certificado se seguirá aceptando incluso cuando haya caducado, siempre y cuando la marca de tiempo sea válida. De esta forma, las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que tengan certificados caducados y marcas de tiempo válidas se podrán descargar y ejecutar. Asimismo, las aplicaciones instaladas con certificados caducados podrán seguir descargando e instalando actualizaciones.  
  
 Para incluir una marca de tiempo en un servidor de aplicaciones, debe haber disponible un servidor de marca de tiempo. Para obtener información sobre cómo seleccionar un servidor de marca de tiempo, consulte [Cómo: Firmar aplicaciones y manifiestos de implementación](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### Actualizar certificados expirados  
 En las versiones anteriores de .NET Framework, la actualización de una aplicación cuyo certificado ha expirado podía hacer que la aplicación dejara de funcionar. Para resolver este problema, use uno de los métodos siguientes:  
  
-   Actualice .NET Framework a la versión 2.0 SP1 o a una versión posterior en Windows XP, o a la versión 3.5 o posterior en Windows Vista.  
  
-   Desinstale la aplicación e instale una versión nueva con un certificado válido.  
  
-   Cree un ensamblado de línea de comandos que actualice el certificado. En el [artículo de soporte técnico de Microsoft 925521](http://go.microsoft.com/fwlink/?LinkId=179454) encontrará información detallada sobre este proceso.  
  
### Almacenar certificados  
  
-   Puede almacenar los certificados como un archivo .pfx en el sistema de archivos o en un contenedor de claves. Un usuario de un dominio de Windows puede tener un determinado número de contenedores de claves. De forma predeterminada, MakeCert.exe almacenará los certificados en el contenedor de claves personales, a menos que especifique que se guarden en un archivo .pfx. Mage.exe y MageUI.exe, las herramientas de [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] que sirven para crear implementaciones de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], le permiten usar certificados almacenados en cualquier modo.  
  
## Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe \(Herramienta de generación y edición de manifiestos\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)