---
title: Crear consultas parametrizadas de TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fe77d3622e9c41d98ff89972e522bb25aae58b9d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756015"
---
# <a name="create-parameterized-tableadapter-queries"></a>Crear consultas parametrizadas de TableAdapter
Una consulta parametrizada devuelve datos que cumplen las condiciones de una cláusula WHERE dentro de la consulta. Por ejemplo, puede parametrizar una lista de clientes para mostrar solo los clientes de una determinada ciudad; para ello, agrega `WHERE City = @City` al final de la instrucción SQL que devuelve una lista de clientes.

 Crear consultas parametrizadas de TableAdapter en el **Diseñador de Dataset**. También puede crear en una aplicación de Windows con el **parametrizar origen de datos** comando el **datos** menú. El **parametrizar origen de datos** comando crea los controles del formulario donde los valores de parámetro de entrada y ejecutar la consulta.

> [!NOTE]
> Al construir una consulta parametrizada, utilice la notación de parámetro que es específica de código se escribe en la base de datos. Por ejemplo, orígenes de datos de Access y OleDb utilizan el signo de interrogación '?' para denotar los parámetros, por lo que la cláusula WHERE tendría un aspecto similar al siguiente: `WHERE City = ?`.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de la configuración activa o la edición que está usando. Para cambiar la configuración, vaya a la **herramientas** menú y seleccione **importar y exportar configuraciones**. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-parameterized-tableadapter-query"></a>Crear una consulta de TableAdapter parametrizada

#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Para crear una consulta parametrizada en el Diseñador de Dataset

-   Cree un nuevo TableAdapter y agregue una cláusula WHERE con los parámetros deseados a la instrucción SQL. Para obtener más información, consulte [crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).

     O bien

-   Agregue una consulta a un TableAdapter existente, y agregue una cláusula WHERE con los parámetros deseados a la instrucción SQL.

#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Para crear una consulta parametrizada durante el diseño de un formulario enlazado a datos

1.  Seleccione en el formulario un control que ya esté enlazado a un conjunto de datos. Para obtener más información, consulte [controla el enlace Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2.  En el **datos** menú, seleccione **Agregar consulta**.

3.  Completar la **generador de criterios de búsqueda** cuadro de diálogo, agregar una cláusula WHERE con los parámetros deseados a la instrucción SQL.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Para agregar una consulta a un formulario enlazado a datos existente

1.  Abra el formulario en el **Diseñador de Windows Forms**.

2.  En el **datos** menú, seleccione **Agregar consulta** o **etiquetas inteligentes de datos**.

    > [!NOTE]
    >  Si **Agregar consulta** no está disponible en el **datos** menú, seleccione un control en el formulario que muestra el origen de datos quiera agregar parametrización. Por ejemplo, si el formulario muestra datos en un control <xref:System.Windows.Forms.DataGridView>, selecciónelo. Si el formulario muestra datos en controles individuales, seleccione un control enlazado a datos.

3.  En el **tabla de origen de datos seleccione** área, seleccione la tabla a la que desea agregar parametrización.

4.  Escriba un nombre en el **nuevo nombre de consulta** cuadro Si va a crear una nueva consulta.

     O bien

     Seleccione una consulta en el **nombre de consulta existente** cuadro.

5.  En el **texto de la consulta** , escriba una consulta que toma parámetros.

6.  Seleccione **Aceptar**.

     Un control para el parámetro de entrada y un **carga** botón se agregan al formulario en un <xref:System.Windows.Forms.ToolStrip> control.

#### <a name="querying-for-null-values"></a>Consultar valores null
Parámetros de TableAdapter se pueden asignar valores null cuando desea consultar registros que no tienen ningún valor actual. Por ejemplo, considere la consulta siguiente que tiene un `ShippedDate` parámetro en su `WHERE` cláusula:

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

 Si se tratara de una consulta en un TableAdapter, podría consultar todos los pedidos que no se han enviado por el código siguiente:

 [!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
 [!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

 Para habilitar una consulta que acepte valores null:

1.  En el **Diseñador de Dataset**, seleccione la consulta de TableAdapter que debe aceptar los valores de parámetro null.

2.  En el **propiedades** ventana, seleccione **parámetros**, a continuación, haga clic en el botón de puntos suspensivos (**...** ) para abrir el **Editor de la colección de parámetros**.

3.  Seleccione el parámetro que permite valores null y establezca el **AllowDbNull** propiedad `true`.

## <a name="see-also"></a>Vea también

- [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)