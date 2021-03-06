---
title: Archivos de respuesta de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83f8e5ad4522a47eaea978b14678fe134b4faa8e
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081597"
---
# <a name="msbuild-response-files"></a>Archivos de respuesta de MSBuild
Los archivos de respuesta (*.rsp*) son archivos de texto que contienen modificadores de línea de comandos de *MSBuild.exe*. Cada modificador puede estar en una línea independiente o todos los modificadores pueden aparecen en una sola línea. Las líneas de comentario van precedidas del símbolo **#**. El modificador **@** se usa para pasar otro archivo de respuesta a *MSBuild.exe*.  
  
## <a name="msbuildrsp"></a>MSBuild.rsp
El archivo de respuesta automática es un archivo *.rsp* especial que *MSBuild.exe* usa automáticamente al compilar un proyecto. Este archivo, *MSBuild.rsp*, debe estar en el mismo directorio que *MSBuild.exe*, de lo contrario, no se encuentra. Puede editar este archivo para especificar los modificadores de línea de comandos predeterminados para *MSBuild.exe*. Por ejemplo, si usa el mismo registrador cada vez que compila un proyecto, puede agregar el modificador **/logger** a *MSBuild.rsp* y *MSBuild.exe* usará el registrador cada vez que se compile un proyecto.  

## <a name="directorybuildrsp"></a>Directory.Build.rsp
En la versión 15.6 y posteriores, MSBuild busca en los directorios primarios del proyecto un archivo denominado *Directory.Build.rsp*.  Esto puede resultar útil en un repositorio de código fuente para proporcionar argumentos predeterminados durante las compilaciones de línea de comandos.  También se puede utilizar para especificar los argumentos de línea de comandos de las compilaciones hospedadas.

## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)