---
title: 'Cómo: ejecutar un procedimiento almacenado que no devuelve ningún valor | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- ExecuteNonQuery method
- stored procedures, creating
- stored procedures, executing
ms.assetid: 8a929e96-2cf5-43a5-b5b7-c0a5a397bbc5
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 38dea599c0c3247c3dd2e3e1d1ca8bb02315cfc5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263099"
---
# <a name="how-to-execute-a-stored-procedure-that-returns-no-value"></a>Cómo: Ejecutar un procedimiento almacenado que no devuelve valores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para ejecutar un procedimiento almacenado que no devuelve ningún valor, puede ejecutar una consulta de TableAdapter que está configurada para ejecutar un procedimiento almacenado (por ejemplo, `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 Si la aplicación no usa los TableAdapters, llame a la `ExecuteNonQuery` método en un objeto de comando, estableciendo su `CommandType` propiedad <xref:System.Data.CommandType>. ("Objeto de comando" hace referencia a un comando específico para el [.NET Framework Data Provider](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) usando la aplicación. Por ejemplo, si la aplicación está utilizando el proveedor de datos de .NET Framework para SQL Server, el objeto de comando sería <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Los ejemplos siguientes muestran cómo ejecutar procedimientos almacenados que no devuelven ningún valor de una base de datos mediante TableAdapters u objetos de comando. Para obtener más información sobre cómo realizar consultas con TableAdapters y comandos, consulte [llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-stored-procedures-that-return-no-values-using-a-tableadapter"></a>Ejecutar procedimientos almacenados que no devuelven ningún valor utilizando un TableAdapter  
 En este ejemplo se muestra cómo crear una consulta de TableAdapter con el [editar TableAdapters](../data-tools/editing-tableadapters.md), y, a continuación, se proporciona información acerca de cómo declarar una instancia del TableAdapter y ejecutar la consulta.  
  
#### <a name="to-create-a-stored-procedure-that-returns-no-value-using-a-tableadapter"></a>Para crear un procedimiento almacenado que no devuelve ningún valor mediante un TableAdapter  
  
1.  Abrir un conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Si ya tiene uno, cree un TableAdapter. Para obtener más información sobre la creación de los TableAdapters, vea [crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Si ya tiene una consulta en el TableAdapter que utiliza un procedimiento almacenado que no devuelve ningún valor, omita el siguiente procedimiento, "para"declarar una instancia del TableAdapter y ejecutar la consulta. En caso contrario, continúe con el paso 4 para crear una nueva consulta que no devuelve ningún valor.  
  
4.  Haga clic en el TableAdapter que desee y use el menú contextual para agregar una consulta.  
  
     El **TableAdapter Query Configuration Wizard** se abre.  
  
5.  Seleccione **utilice el procedimiento almacenado existente**y, a continuación, haga clic en **siguiente**.  
  
6.  Seleccione un procedimiento almacenado en la lista desplegable y, a continuación, haga clic en **siguiente**.  
  
7.  Seleccione la opción para devolver **ningún valor**y, a continuación, haga clic en **siguiente**.  
  
8.  Proporcione un nombre para la consulta.  
  
9. Haga clic en **siguiente**, o **finalizar** para completar el asistente; la consulta se agrega al objeto TableAdapter.  
  
10. Compilar el proyecto.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Para declarar una instancia del TableAdapter y ejecutar la consulta  
  
1.  Declare una instancia del TableAdapter que contiene la consulta que desea ejecutar.  
  
    -   Para crear una instancia mediante herramientas de tiempo de diseño, arrastre el TableAdapter que desee desde la **cuadro de herramientas**. (Componentes del proyecto aparecen ahora en el **cuadro de herramientas** bajo un encabezado que coincida con el nombre del proyecto.) Si el TableAdapter no aparece en el **cuadro de herramientas**, a continuación, es posible que deba compilar el proyecto.  
  
         O bien  
  
    -   Para crear una instancia en el código, reemplace el código siguiente con los nombres de su <xref:System.Data.DataSet> y un TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Los TableAdapters no se encuentran dentro de sus clases de conjunto de datos asociado. Cada conjunto de datos tiene una colección correspondiente de TableAdapters en su propio espacio de nombres. Por ejemplo, si tiene un conjunto de datos denominado `SalesDataSet`, a continuación, podría haber un `SalesDataSetTableAdapters` espacio de nombres que contiene sus TableAdapters.  
  
2.  Llame a la consulta como llamaría a cualquier otro método en el código. La consulta es un método del TableAdapter. Reemplace el código siguiente con los nombres de su TableAdapter y consulta. También necesitará pasar los parámetros requeridos por la consulta. Si no está seguro de si la consulta requiere parámetros, o qué parámetros requiere, a continuación, compruebe IntelliSense para la firma necesaria de la consulta. Dependiendo de si la consulta toma parámetros o no, el código tendría un aspecto similar a uno de los ejemplos siguientes:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     El código completo para declarar una instancia del TableAdapter y ejecutar la consulta debe ser similar al siguiente:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-stored-procedures-that-return-no-value-using-a-command-object"></a>Ejecutar procedimientos almacenados que no devuelven ningún valor mediante un objeto de comando  
 El ejemplo siguiente muestra cómo crear un comando y ejecutar un procedimiento almacenado que no devuelve ningún valor. Para obtener información sobre cómo establecer y obtener los valores de parámetro para un comando, consulte [How to: Set y obtener los parámetros para objetos de comando](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Este ejemplo se usa el <xref:System.Data.SqlClient.SqlCommand> de objetos y requiere:  
  
-   Las referencias a la <xref:System>, <xref:System.Data>, y <xref:System.Xml> espacios de nombres.  
  
#### <a name="to-execute-a-stored-procedure-that-returns-no-value-using-a-datacommand"></a>Para ejecutar un procedimiento almacenado que no devuelve ningún valor mediante un DataCommand  
  
-   Agregue el código siguiente a un método que desea ejecutar el procedimiento almacenado de. Llame a la `ExecuteNonQuery` método de un comando para no devolver ningún valor (por ejemplo, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#15)]
     [!code-vb[VbRaddataFillingAndExecuting#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#15)]  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 La aplicación requiere permiso para tener acceso a la base de datos y ejecutar la instrucción SQL.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [Cómo: crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Cómo: editar consultas de TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Cómo: rellenar un conjunto de datos](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Cómo: establecer y obtener parámetros de objetos de comando](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)