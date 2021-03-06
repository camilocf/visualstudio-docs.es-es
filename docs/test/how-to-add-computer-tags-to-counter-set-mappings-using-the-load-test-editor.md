---
title: Adición de etiquetas de equipo a asignaciones de conjuntos de contadores para pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, counter set mappings, computer tags
ms.assetid: f52a73e1-036a-4b28-a6c8-848284bf4488
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 96ce122c78c20b741613ed45820f585236a0383b
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203672"
---
# <a name="how-to-add-computer-tags-to-counter-set-mappings-using-the-load-test-editor"></a>Adición de etiquetas de equipo a asignaciones de conjuntos de contadores con el editor de pruebas de carga

Las etiquetas de equipo permiten identificar un equipo con un nombre fácil de reconocer. Las etiquetas se muestran en el nodo **Asignaciones de conjuntos de contadores** del árbol en el Editor de pruebas de carga. Lo que es más importante, las etiquetas se muestran en los informes de Excel, que sirve de ayuda a las partes interesadas para identificar el rol que desempeña el equipo en la prueba de carga. Por ejemplo, "Servidor1 web en lab2" o "SQL Server2 en oficina Phoenix". Para más información, consulte [Informar de los resultados de las pruebas de carga para las comparaciones de pruebas o los análisis de tendencias](../test/compare-load-test-results.md).

## <a name="to-add-a-tag-to-a-computer"></a>Para agregar una etiqueta a un equipo

1.  Abra una prueba de carga.

2.  Elija el botón **Administrar conjuntos de contadores**.

     -O bien-

     Haga clic con el botón derecho en la carpeta **Conjuntos de contadores** del árbol de la prueba de carga y elija **Administrar conjuntos de contadores**.

     Se muestra el cuadro de diálogo **Administrar conjuntos de contadores**.

3.  (Opcional) En el cuadro de lista **Los conjuntos de contadores y equipos seleccionados se agregarán debajo de los siguientes parámetros de ejecución**, seleccione otro parámetro de ejecución.

    > [!NOTE]
    > Esto último sólo se aplica si se tiene más de un parámetro de ejecución en la prueba de carga.

4.  En **Conjuntos de contadores y equipos que se van a supervisar**, seleccione el equipo al que desea aplicar la etiqueta.

    > [!NOTE]
    > Para información sobre cómo agregar un equipo, consulte [Cómo: Administrar conjuntos de contadores](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

5.  En el cuadro de texto **Etiquetas de equipo**, escriba una etiqueta para asociarla al equipo. Por ejemplo, "MáquinaPruebas12 en lab3."

6.  Elija **Aceptar**.

## <a name="see-also"></a>Vea también

- [Analizar las infracciones de las reglas de umbral](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analizar los resultados de pruebas de carga con el analizador de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Especificar los conjuntos de contadores y las reglas de umbral para equipos en una prueba de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Cómo: Administrar conjuntos de contadores](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)