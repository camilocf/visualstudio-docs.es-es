---
title: "Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos de b&#250;squeda | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "enlace de datos, controles de usuario"
  - "LookupBindingPropertiesAttribute (clase), ejemplos"
  - "controles de usuario [Visual Basic], crear"
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos de b&#250;squeda
Cuando muestra datos en formularios Windows Forms, puede elegir controles existentes en el Cuadro de herramientas o puede crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar.  En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  Los controles que implementan <xref:System.ComponentModel.LookupBindingPropertiesAttribute> pueden contener tres propiedades que se pueden enlazar a los datos.  Tales controles son similares a <xref:System.Windows.Forms.ComboBox>.  
  
 Para obtener más información sobre la creación de controles, vea [Desarrollar controles de formularios Windows Forms en tiempo de diseño](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Al crear controles para el uso en escenarios de enlace de datos, necesita implementar uno de los atributos de enlace de datos siguientes:  
  
|Uso de atributo de enlace de datos|  
|----------------------------------------|  
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna \(o propiedad\) de datos.  Para obtener más información, vea [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas \(o tablas\) de datos.  Para obtener más información, vea [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos complejo](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas \(o tablas\) de datos pero que también necesiten presentar una única columna o propiedad.  \(Este proceso se describe en esta página del tutorial.\)|  
  
 Este tutorial crea un control de búsqueda que se enlaza a los datos de dos tablas.  En este ejemplo se utilizan las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.  El control de búsqueda se enlazará al campo `CustomerID` de la tabla `Orders`.  Utilizará este valor para buscar `CompanyName` en la tabla `Customers`.  
  
 Durante este tutorial aprenderá a:  
  
-   Crear una nueva **aplicación para Windows**.  
  
-   Agregue un nuevo **Control de usuario** a su proyecto.  
  
-   Diseñe visualmente el control de usuario.  
  
-   Implemente el atributo `LookupBindingProperty`.  
  
-   Cree un conjunto de datos con el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Establezca la columna **CustomerID** de la tabla **Orders** en la ventana **Orígenes de datos** para utilizar el nuevo control.  
  
-   Cree un formulario para mostrar los datos en el nuevo control.  
  
## Requisitos previos  
 Para poder completar este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind.  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear una aplicación para Windows  
 El primer paso es crear una **Aplicación para Windows**.  
  
#### Para crear el nuevo proyecto de Windows  
  
1.  En Visual Studio, en el menú **Archivo** cree un nuevo **Proyecto**.  
  
2.  Dé al proyecto el nombre LookupControlWalkthrough.  
  
3.  Seleccione **Aplicación para Windows** y haga clic en **Aceptar**.  Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     El proyecto **LookupControlWalkthrough** se crea y se agrega al **Explorador de soluciones**.  
  
## Agregar un control de usuario al proyecto  
 Este tutorial crea un control de búsqueda a partir de un **Control de usuario**, por lo que debe agregar un elemento **Control de usuario** al proyecto **LookupControlWalkthrough**.  
  
#### Para agregar un control de usuario al proyecto  
  
1.  En el menú **Proyecto**, elija **Agregar control de usuario**.  
  
2.  Escriba `LookupBox` en el área **Nombre** y haga clic en **Agregar**.  
  
     El control **LookupBox** se agrega al **Explorador de soluciones** y se abre en el diseñador.  
  
## Diseñar el control LookupBox  
  
#### Para diseñar el control LookupBox  
  
-   Arrastre un control <xref:System.Windows.Forms.ComboBox> del **Cuadro de herramientas** hasta la superficie de diseño del control del usuario.  
  
## Agregar el atributo de enlace de datos requerido  
 Para controles de búsqueda que admiten el enlace de datos, puede implementar <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### Para implementar el atributo LookupBindingProperties  
  
1.  Cambie el control **LookupBox** a vista de código.  \(En el menú **Ver**, elija **Código**.\)  
  
2.  Reemplace el código de `LookupBox` por lo siguiente:  
  
     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-cs[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]  
  
3.  En el menú **Compilar**, elija **Compilar solución**.  
  
## Crear un origen de datos de su base de datos  
 En este paso se crea un origen de datos utilizando el **Asistente para la configuración de orígenes de datos** basado en las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.  Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión.  Para obtener información sobre la configuración de la base de datos de ejemplo Northwind, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### Para crear el origen de datos  
  
1.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos**.  
  
2.  En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.  
  
5.  Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.  
  
6.  Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.  
  
7.  Expanda el nodo **Tables** en la página **Elija los objetos de base de datos**.  
  
8.  Seleccione las tablas `Customers` y `Orders` y, a continuación, haga clic en **Finalizar**.  
  
     **NorthwindDataSet** se agrega al proyecto y las tablas `Customers` y `Orders` aparecen en la ventana **Orígenes de datos**.  
  
## Establecer la columna CustomerID de la tabla Orders para utilizar el control LookupBox  
 Dentro de la ventana **Orígenes de datos** puede establecer el control que se va a crear antes de arrastrar elementos a un formulario.  
  
#### Para establecer la columna CustomerID para enlazarse al control LookupBox  
  
1.  Abra **Form1** en el diseñador.  
  
2.  Expanda el nodo **Customers** en la ventana **Orígenes de datos**.  
  
3.  Expanda el nodo **Orders** \(incluido en el nodo **Customers** debajo de la columna **Fax**\).  
  
4.  Haga clic en la flecha de lista desplegable en el nodo **Orders** y elija **Detalles** de la lista de control.  
  
5.  Haga clic en la flecha de lista desplegable en la columna **CustomerID** \(del nodo **Orders**\) y elija **Personalizar**.  
  
6.  Seleccione **LookupBox** de la lista de **Controles asociados** en el cuadro de diálogo **Opciones de personalización de la interfaz de usuario de datos**.  
  
7.  Haga clic en **Aceptar**.  
  
8.  Haga clic en la flecha de lista desplegable en la columna **CustomerID** y elija **LookupBox**.  
  
## Agregar controles al formulario  
 Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al **Form1**.  
  
#### Para crear controles enlazados en el Windows Form  
  
-   Arrastre el nodo **Orders** de la ventana **Orígenes de datos** al Windows Form y compruebe que se utiliza el control **LookupBox** para mostrar los datos de la columna `CustomerID`.  
  
## Enlazar el control para buscar CompanyName en la tabla Customers  
  
#### Para configurar los enlaces de búsqueda  
  
-   Seleccione el nodo **Customers** principal en la ventana **Orígenes de datos** y arrástrelo hacia el cuadro combinado del **CustomerIDLookupBox** en **Form1**.  
  
     Así configura el enlace de datos para mostrar el valor `CompanyName` de la tabla `Customers` a la vez que mantiene el valor `CustomerID` de la tabla `Orders`.  Para obtener más información, vea [Cómo: Crear tablas de búsqueda en aplicaciones de Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md).  
  
## Ejecutar la aplicación  
  
#### Para ejecutar la aplicación  
  
-   Presione F5 para ejecutar la aplicación.  
  
-   Navegue por algunos registros y compruebe que `CompanyName` aparece en el control `LookupBox`.  
  
## Vea también  
 [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)