---
title: Referencia a un SDK de un proyecto de MSBuild| Microsoft Docs
ms.custom: 
ms.date: 01/25/2018
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: jeffkl
ms.author: jeffkl
manager: angerlic
ms.workload:
- multiple
ms.openlocfilehash: 28027b21d3f562e3eda94dc91de16ddb38362d3c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-use-msbuild-project-sdks"></a>Uso de los SDK de proyecto de MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 15.0 introdujo el concepto de "SDK de proyecto", que simplifica el uso de kits de desarrollo de software que requieren la importación de propiedades y destinos.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```  
  
Durante la evaluación del proyecto, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] agrega importaciones implícitas en la parte superior e inferior del proyecto:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>  
```  

## <a name="referencing-a-project-sdk"></a>Referencia a un SDK de proyecto
 Hay tres maneras de hacer referencia a un SDK de proyecto

1. Use el atributo `Sdk` en el elemento `<Project/>`:
    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```
    Una importación implícita se agrega a la parte superior e inferior del proyecto, según se explicó anteriormente.  El formato del atributo `Sdk` es `Name[/Version]`, donde Version es opcional.  Por ejemplo, puede especificar `My.Custom.Sdk/1.2.3`.

2. Use el elemento `<Sdk/>` de nivel superior:
    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```
   Una importación implícita se agrega a la parte superior e inferior del proyecto, según se explicó anteriormente.  El atributo `Version` no es necesario.

3. Use el elemento `<Import/>` en cualquier parte de su proyecto:
    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```
   La inclusión explícita de las importaciones en el proyecto permite ejercer un control total sobre el orden.

   Al usar el elemento `<Import/>`, puede especificar también un atributo `Version` opcional.  Por ejemplo, puede especificar `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Resolución de los SDK de proyecto
Al evaluar la importación, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] resuelve dinámicamente la ruta de acceso al SDK del proyecto basándose en el nombre y la versión especificada.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] también tiene una lista de resoluciones de SDK registradas que son complementos que ubican los SDK de proyecto en el equipo.  Entre estos complementos se incluyen los siguientes:

1. Una resolución basada en NuGet que consulta las fuentes de paquetes configuradas para los paquetes NuGet que coinciden con el identificador y la versión del SDK especificado.<br/>
   Esta resolución solo está activa si ha especificado una versión opcional y se puede utilizar para cualquier SDK de proyecto personalizado.  
2. Una resolución de CLI de .NET que resuelve los SDK que se instalan con la CLI de .NET.<br/>
   Esta resolución busca SDK de proyecto como `Microsoft.NET.Sdk` y `Microsoft.NET.Sdk.Web` que forman parte del producto.
3. Una resolución predeterminada que resuelve los SDK que se instalaron con MSBuild.

La resolución del SDK basado en NuGet admite la especificación de una versión en su [global.json](https://docs.microsoft.com/en-us/dotnet/core/tools/global-json) que le permite controlar la versión del SDK de proyecto en un solo lugar en lugar de en cada proyecto individual:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```
Durante una compilación, solo se puede usar una versión de cada SDK de proyecto.  Si está haciendo referencia a dos versiones diferentes del mismo SDK de proyecto, MSBuild emitirá una advertencia.  Se recomienda **no** especificar una versión en sus proyectos si se especifica una versión en su `global.json`.  

## <a name="see-also"></a>Vea también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Personalizar una compilación](../msbuild/customize-your-build.md)   