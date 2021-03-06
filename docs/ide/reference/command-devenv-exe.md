---
title: -Command (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c21402c3b2b71372aaf170c68c65777eba4e95bf
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33703751"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
Ejecuta el comando especificado después de iniciar el entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Sintaxis

```cmd
devenv /command CommandName
```

## <a name="arguments"></a>Argumentos
 `CommandName` Obligatorio. Nombre completo de un comando de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o su alias, incluido entre comillas dobles. Para obtener más información sobre la sintaxis de comandos y de alias, consulte [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Comentarios
 Una vez completado el inicio, el IDE ejecuta el comando indicado. Si se usa este modificador, el IDE no muestra la página principal de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] al iniciarse.

 Si un complemento muestra un comando, puede utilizar este modificador para iniciar el complemento desde la línea de comandos. Para obtener más información, consulte [Cómo: Controlar complementos con el Administrador de complementos](http://msdn.microsoft.com/Library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).

## <a name="example"></a>Ejemplo
 Este ejemplo inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y ejecuta automáticamente la macro Open Favorite Files.

```cmd
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)