---
title: Opciones, editor de texto, general
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4405e50a2bc264c88c073980da77fafbedf49cbe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830670"
---
# <a name="options-text-editor-general"></a>Opciones, editor de texto, general

Este cuadro de diálogo le permite cambiar la configuración global del editor de texto y el código de Visual Studio. Para tener acceso a este cuadro de diálogo, seleccione **Opciones** en el menú **Herramientas**, expanda la carpeta **Editor de texto** y, después, seleccione **General**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="settings"></a>Configuración

### <a name="drag-and-drop-text-editing"></a>Editar texto con arrastrar y colocar

Cuando está seleccionada, le permite mover texto seleccionándolo y arrastrándolo con el mouse a otra ubicación dentro del documento actual o en cualquier otro documento abierto.

### <a name="automatic-delimiter-highlighting"></a>Resaltar con el delimitador automático

Cuando está seleccionada, los caracteres de delimitador que separan los parámetros o los pares elemento-valor, así como las llaves coincidentes, se resaltan.

### <a name="track-changes"></a>Control de cambios

Cuando el editor de código está seleccionado, aparece una línea amarilla vertical en el margen de selección para marcar el código que ha cambiado desde que el archivo se guardó por última vez. Cuando guarda los cambios, las líneas verticales se convierten en color verde.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Detectar automáticamente codificación UTF-8 sin firma

De manera predeterminada, el editor detecta la codificación buscando marcas BOM o etiquetas del conjunto de caracteres. Si no se detecta ninguna en el documento actual, el editor de código intenta detectar automáticamente la codificación UTF-8 analizando las secuencias de bytes. Para deshabilitar la detección automática de la codificación, desactive esta opción.

## <a name="display"></a>Mostrar

### <a name="selection-margin"></a>Margen de selección

Cuando está seleccionada, muestra un margen vertical a lo largo del borde izquierdo del área de texto del editor. Puede hacer clic en este margen para seleccionar una línea de texto completa, o hacer clic y arrastrar para seleccionar líneas de texto consecutivas.

|Margen de selección activado|Margen de selección desactivado|
| - | - |
|![Captura de pantalla de HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif)|![Captura de pantalla de HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Margen del indicador

Cuando está seleccionada, muestra un margen vertical fuera del borde izquierdo del área de texto del editor. Cuando hace clic en este margen, aparecen un icono e información sobre herramientas relacionados con el texto. Por ejemplo, aparecen puntos de interrupción o accesos directos a la lista de tareas en el margen del indicador. La información del margen del indicador no se imprime.

### <a name="vertical-scroll-bar"></a>Barra de desplazamiento vertical

Cuando está seleccionada, muestra una barra de desplazamiento vertical que le permite desplazarse hacia arriba y hacia abajo para ver elementos que quedan fuera del área de visualización del editor. Si las barras de desplazamiento verticales no están disponibles, puede usar las teclas de dirección, la tecla Retroceder Página y la tecla Avanzar Página para desplazarse.

### <a name="horizontal-scroll-bar"></a>Barra de desplazamiento horizontal

Cuando está seleccionada, muestra una barra de desplazamiento horizontal que le permite desplazarse de lado a lado para ver elementos que quedan fuera del área de visualización del editor. Si las barras de desplazamiento horizontales no están disponibles, puede usar las teclas de dirección para desplazarse.

### <a name="highlight-current-line"></a>Resaltar línea actual

Cuando está seleccionada, muestra un cuadro gris alrededor de la línea de código donde se sitúa el cursor.

## <a name="see-also"></a>Vea también

- [Opciones, Editor de texto, Todos los lenguajes](../../ide/reference/options-text-editor-all-languages.md)
- [Opciones, editor de texto, todos los lenguajes, pestañas](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Opciones, editor de texto, extensión de archivo](../../ide/reference/options-text-editor-file-extension.md)
- [Identificar y personalizar métodos abreviados de teclado](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Personalizar el editor](../../ide/customizing-the-editor.md)
- [Usar IntelliSense](../../ide/using-intellisense.md)