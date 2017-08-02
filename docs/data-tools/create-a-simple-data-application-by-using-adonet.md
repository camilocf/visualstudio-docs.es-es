---
title: "Tutorial: Crear una aplicaci&#243;n de datos sencilla mediante ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 42
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Crear una aplicaci&#243;n de datos sencilla mediante ADO.NET
Al crear una aplicación que manipula datos en una base de datos, se realizan tareas básicas como definir cadenas de conexión, insertar datos y ejecutar procedimientos almacenados.  Siguiendo este tema, puede detectar cómo interactuar con una base de datos dentro de una aplicación de formularios Windows Forms sencilla utilizando Visual C\# o Visual Basic y ADO.NET.  
  
> [!IMPORTANT]
>  Para mantener el código sencillo, no se incluye el control de excepciones listo para producción.  
  
 **En este tema**  
  
-   [Configurar la base de datos de ejemplo](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)  
  
-   [Crear los formularios y agregar controles](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)  
  
-   [Almacenar la cadena de conexión](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)  
  
-   [Recuperar la cadena de conexión](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)  
  
-   [Escribir el código para los formularios](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)  
  
-   [Probar la aplicación](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)  
  
## Requisitos previos  
 Para crear la aplicación, necesitará:  
  
-   Visual Studio 2012 con Update 1 o [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]  
  
-   SQL Server 2012 Express LocalDB  
  
-   La pequeña base de datos de ejemplo que se crea siguiendo los pasos descritos en [Tutorial: Crear una pequeña base de datos de ejemplo](../data-tools/create-a-sql-database-by-using-a-script.md).  
  
-   La cadena de conexión para la base de datos después de haberla configurado.  Puede buscar este valor si abre el **Explorador de objetos de SQL Server** y el menú contextual para la base de datos, elige **Propiedades** y después se desplaza a la propiedad **Cadena de conexión**.  
  
 En este tema se supone que está familiarizado con la funcionalidad básica del IDE de Visual Studio y puede crear una aplicación de Windows Forms, agregar formularios a ese proyecto, colocar botones y otros controles en los formularios, establecer las propiedades de estos controles y codificar eventos simples.  Si no está familiarizado con estas tareas, recomendamos que complete los [Introducción a Visual C\# y Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) antes de empezar este tema.  
  
##  <a name="BKMK_setupthesampledatabase"></a> Configurar la base de datos de ejemplo  
 La base de datos de ejemplo de este tutorial consta de las tablas Cliente y Pedidos.  Las tablas no contienen datos inicialmente, pero se agregarán cuando se ejecute la aplicación que se va a crear.  La base de datos también tiene cinco procedimientos almacenados simples.  El [Tutorial: Crear una pequeña base de datos de ejemplo](../data-tools/create-a-sql-database-by-using-a-script.md) contiene un script Transact\-SQL que crea las tablas, las claves primarias y externas, las restricciones y los procedimientos almacenados.  
  
##  <a name="BKMK_createtheformsandaddcontrols"></a> Crear los formularios y agregar controles  
  
1.  Cree un proyecto para una aplicación de formularios Windows Forms y, a continuación, asígnele el nombre `SimpleDataApp`.  
  
     Visual Studio crea el proyecto y varios archivos, incluido un formulario de Windows Forms vacío denominado Form1.  
  
2.  Agregue dos formularios Windows Forms al proyecto para que tenga tres formularios y después asígneles los siguientes nombres.  
  
    -   Navegación  
  
    -   NewCustomer  
  
    -   FillOrCancel  
  
3.  Para cada formulario, agregue los cuadros de texto, botones y otros controles que aparecen en las siguientes ilustraciones.  Para cada control, establezca las propiedades que se describen en las tablas.  
  
    > [!NOTE]
    >  El cuadro de grupo y los controles de etiquetas agregan claridad pero no se utilizan en el código.  
  
 **Formulario Navigation**  
  
 ![Cuadro de diálogo de navegación](../data-tools/media/simpleappnav.png "SimpleAppNav")  
  
|Controles del formulario Navigation|Propiedades|  
|-----------------------------------------|-----------------|  
|Botón|Nombre \= btnGoToAdd|  
|Botón|Nombre \= btnGoToFillOrCancel|  
|Botón|Nombre \= btnExit|  
  
 **Formulario NewCustomer**  
  
 ![Agregar un nuevo cliente y realizar un pedido](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")  
  
|Controles del formulario NewCustomer|Propiedades|  
|------------------------------------------|-----------------|  
|TextBox|Nombre \= txtCustomerName|  
|TextBox|Nombre \= txtCustomerID<br /><br /> De solo lectura \= True|  
|Botón|Nombre \= btnCreateAccount|  
|NumericUpDown|Posiciones decimales \= 0<br /><br /> Máximo \= 5000<br /><br /> Nombre \= numOrderAmount|  
|DateTimePicker|Formato \= Abreviado<br /><br /> Nombre \= dtpOrderDate|  
|Botón|Nombre \= btnPlaceOrder|  
|Botón|Nombre \= btnAddAnotherAccount|  
|Botón|Nombre \= btnAddFinish|  
  
 **Formulario FillOrCancel**  
  
 ![rellenar o cancelar pedidos](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")  
  
|Controles del formulario FillOrCancel|Propiedades|  
|-------------------------------------------|-----------------|  
|TextBox|Nombre \= txtOrderID|  
|Botón|Nombre \= btnFindByOrderID|  
|DateTimePicker|Formato \= Abreviado<br /><br /> Nombre \= dtpFillDate|  
|DataGridView|Nombre \= dgvCustomerOrders<br /><br /> De solo lectura \= True<br /><br /> Encabezados de filas visibles \= False|  
|Botón|Nombre \= btnCancelOrder|  
|Botón|Nombre \= btnFillOrder|  
|Botón|Nombre \= btnFinishUpdates|  
  
##  <a name="BKMK_storetheconnectionstring"></a> Almacenar la cadena de conexión  
 Cuando la aplicación intenta abrir una conexión a la base de datos, la aplicación debe tener acceso a la cadena de conexión.  Para evitar escribir la cadena manualmente en cada formulario, almacene la cadena en el archivo App.config del proyecto y cree un método que devuelva la cadena cuando se llama desde cualquier formulario de la aplicación.  
  
1.  Abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el panel izquierdo de la ventana **Propiedades**, elija la pestaña **Configuración**.  
  
3.  En la columna **Nombre**, escriba `connString`.  
  
4.  En la lista **Tipo**, elija **\(Cadena de conexión\)**.  
  
5.  En la lista **Ámbito**, elija **Aplicación**.  
  
6.  En la columna **Valor**, escriba la cadena de conexión y después guarde los cambios.  
  
##  <a name="BKMK_retrievetheconnectionstring"></a> Recuperar la cadena de conexión  
  
1.  En la barra de menús, elija **Proyecto**, **Agregar referencia** y, a continuación, agregue una referencia a System.Configuration.dll.  
  
2.  En la barra de menús, elija **Proyecto**, **Agregar clase** para agregar un archivo de clase al proyecto y después asigne el nombre `Utilidad` al archivo.  
  
     Visual Studio crea el archivo y lo muestra en el **Explorador de soluciones**.  
  
3.  En el archivo Utilidad, reemplace el código del marcador de posición por el siguiente código.  Observe que los comentarios numerados \(con el prefijo Util\-\) identifican las secciones del código.  La tabla que sigue al código llama a los puntos clave.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    //Util-1 More namespaces.  
    using System.Configuration;   
  
    namespace SimpleDataApp  
    {  
        internal class Utility  
        {  
  
            //Get the connection string from App config file.  
            internal static string GetConnectionString()  
            {  
                //Util-2 Assume failure.  
                string returnValue = null;  
  
                //Util-3 Look for the name in the connectionStrings section.  
                ConnectionStringSettings settings =  
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];  
  
                //If found, return the connection string.  
                if (settings != null)  
                    returnValue = settings.ConnectionString;  
  
                return returnValue;  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Linq  
    Imports System.Text  
    Imports System.Threading.Tasks  
    ' Util-1 More namespaces.  
    Imports System.Configuration  
  
    Namespace SimpleDataApp  
        Friend Class Utility  
  
            ' Get connection string from App config file.  
            Friend Shared Function GetConnectionString() As String  
  
                ' Util-2 Assume failure.  
                Dim returnValue As String = Nothing  
  
                ' Util-3 Look for the name in the connectionStrings section.  
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")  
  
                ' If found, return the connection string.  
                If settings IsNot Nothing Then  
                    returnValue = settings.ConnectionString  
                End If  
  
                Return returnValue  
            End Function  
        End Class  
    End Namespace  
    ```  
  
    |Comentario|Descripción|  
    |----------------|-----------------|  
    |Util\-1|Agregue el espacio de nombres System.Configuration.|  
    |Util\-2|Defina una variable, `returnValue`, e inicialícela en `null` \(C\#\) o en `Nothing` \(Visual Basic\).|  
    |Util\-3|Aunque escribiera `connString` como nombre de la cadena de conexión en la ventana **Propiedades**, debe especificar `"SimpleDataApp.Properties.Settings.connString"` \(C\#\) o `"SimpleDataApp.My.MySettings.connString"` \(Visual Basic\) en el código.|  
  
##  <a name="BKMK_writethecodefortheforms"></a> Escribir el código para los formularios  
 Esta sección contiene información general breve de lo que hace cada formulario y muestra el código que crean los formularios.  Los comentarios numerados identifican las secciones del código.  
  
### Formulario Navigation  
 El formulario Navigation se abre cuando se ejecuta la aplicación.  El botón **Agregar una cuenta** abre el formulario NewCustomer.  El botón **Rellenar o cancelar pedidos** abre el formulario FillOrCancel.  El botón **Salir** cierra la aplicación.  
  
#### Hacer que el formulario Navigation sea el formulario de inicio  
 Si usa C\#, en el **Explorador de soluciones**, abra Program.cs y después cambie la línea `Application.Run` a esta: `Application.Run(new Navigation());`  
  
 Si usa Visual Basic, en el **Explorador de soluciones**, abra la ventana **Propiedades**, elija la pestaña **Aplicación** y, a continuación, elija SimpleDataApp.Navigation en la lista **Formulario de inicio**.  
  
#### Cree controladores de eventos  
 Cree controladores de eventos Click vacíos para los tres botones del formulario.  Consulte [Cómo: Crear controladores de eventos predeterminados en el Diseñador de Windows Forms](http://msdn.microsoft.com/es-es/757bcc16-1dc2-4d68-b115-ac0f53f05c8d).  
  
#### Crear código para Navigation  
 En el formulario Navigation, reemplace el código existente con el código siguiente.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
  
namespace SimpleDataApp  
{  
    public partial class Navigation : Form  
    {  
        public Navigation()  
        {  
            InitializeComponent();  
        }  
  
        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        private void btnGoToAdd_Click(object sender, EventArgs e)  
        {  
            Form frm = new NewCustomer();  
            frm.Show();  
        }  
  
        //Open the FillorCancel form as a dialog box.  
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)  
        {  
            Form frm = new FillOrCancel();  
            frm.ShowDialog();  
        }  
  
        //Close the application, not just the Navigation form.  
        private void btnExit_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
  
Namespace SimpleDataApp  
    Partial Public Class Navigation  
        Inherits Form  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click  
            Dim frm As Form = New NewCustomer()  
            frm.Show()  
        End Sub  
  
        ' Open the FillorCancel form as a dialog box.  
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click  
            Dim frm As Form = New FillOrCancel()  
            frm.ShowDialog()  
        End Sub  
  
        ' Close the application, not just the Navigation form.  
        Private Sub btnExit_Click() Handles btnExit.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
  
```  
  
### Formulario NewCustomer  
 Cuando escribe un nombre de cliente y después elige el botón **Crear cuenta**, el formulario NewCustomer crea una cuenta de cliente y SQL Server devuelve un valor IDENTITY como el nuevo número de cuenta.  A continuación, realiza un pedido para la nueva cuenta especificando una cantidad y una fecha de pedido, y elige el botón **Realizar pedido**.  
  
#### Cree controladores de eventos  
 Cree un controlador de eventos Click vacío para cada botón del formulario.  
  
#### Crear código para NewCustomer  
 Agregue el siguiente código al formulario NewCustomer.  Recorra paso a paso cada bloque de código mediante los comentarios numerados y la tabla después del código.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//NC-1 More namespaces.  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class NewCustomer : Form  
    {  
        //NC-2 Storage for IDENTITY values returned from database.  
        private int parsedCustomerID;  
        private int orderID;  
  
        //NC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public NewCustomer()  
        {  
            InitializeComponent();  
        }  
  
        //NC-4 Create account.  
        private void btnCreateAccount_Click(object sender, EventArgs e)  
        {  
            //NC-5 Set up and run stored procedure only if Customer Name is present.  
            if (isCustomerName())  
            {  
  
                //NC-6 Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;  
  
                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));  
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;  
  
                //NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;  
  
                //NC-10 try-catch-finally  
                try  
                {  
                    //NC-11 Open the connection.  
                    conn.Open();  
  
                    //NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery();  
  
                    //NC-13 Customer ID is an IDENTITY value from the database.   
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;  
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);  
  
                }  
                catch  
                {  
                    //NC-14 A simple catch.  
  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.");  
                }  
                finally  
                {  
                    //NC-15 Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-16 Verify that Customer Name is present.  
        private bool isCustomerName()  
        {  
            if (txtCustomerName.Text == "")  
            {  
                MessageBox.Show("Please enter a name.");  
                return false;  
            }  
            else  
            {  
                return true;  
            }  
        }  
  
        //NC-17 Place order.  
        private void btnPlaceOrder_Click(object sender, EventArgs e)  
        {  
            //NC-18 Set up and run stored procedure only if required input is present.  
            if (isPlaceOrderReady())  
            {  
                // Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-19 Create SqlCommand and identify it as a stored procedure.  
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);  
                cmdNewOrder.CommandType = CommandType.StoredProcedure;  
  
                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;  
  
                //NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));  
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;  
  
                //NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));  
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;  
  
                //NC-23 @Status. For a new order, the status is always O (open)  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));  
                cmdNewOrder.Parameters["@Status"].Value = "O";  
  
                //NC-24 Add return value for stored procedure, which is the orderID.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));  
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;  
  
                //try – catch - finally  
                try  
                {  
                    //Open connection.  
                    conn.Open();  
  
                    //Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery();  
  
                    //NC-25 Display the order number.  
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;  
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("Order could not be placed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-26 Verify that order data is ready.  
        private bool isPlaceOrderReady()  
        {  
            // Verify that CustomerID is present.  
            if (txtCustomerID.Text == "")  
            {  
                MessageBox.Show("Please create customer account before placing order.");  
                return false;  
            }  
  
            // Verify that Amount isn't 0.   
            else if ((numOrderAmount.Value < 1))  
            {  
                MessageBox.Show("Please specify an order amount.");  
                return false;  
            }  
            else  
            {  
                // Order can be submitted.  
                return true;  
            }  
        }  
  
        //NC-27 Reset the form for another new account  
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)  
        {  
            this.ClearForm();  
        }  
  
        //NC-28 Clear values from controls  
        private void ClearForm()  
        {  
            txtCustomerName.Clear();  
            txtCustomerID.Clear();  
            dtpOrderDate.Value = DateTime.Now;  
            numOrderAmount.Value = 0;  
            this.parsedCustomerID = 0;  
        }  
  
        //NC-29 Close the form.  
        private void btnAddFinish_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
  
    }  
}  
  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' NC-1 More namespaces.  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class NewCustomer  
        Inherits Form  
  
        ' NC-2 Storage for IDENTITY values returned from database.  
        Private parsedCustomerID As Integer  
        Private orderID As Integer  
  
        ' NC-3 Specify a connection string.  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' NC-4 Create account.  
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click  
  
            ' NC-5 Set up and run stored procedure only if Customer Name is present.  
            If isCustomerName() Then  
  
                ' NC-6 Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure  
  
                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))  
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text  
  
                ' NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output  
  
                ' NC-10 try-catch-finally  
                Try  
                    ' NC-11 Open the connection.  
                    conn.Open()  
  
                    ' NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery()  
  
                    ' NC-13 Customer ID is an IDENTITY value from the database.   
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)  
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)  
  
                Catch  
                    ' NC-14 A simple catch.  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")  
                Finally  
                    ' NC-15 Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-16 Verify that Customer Name is present.  
        Private Function isCustomerName() As Boolean  
            If txtCustomerName.Text = "" Then  
                MessageBox.Show("Please enter a name.")  
                Return False  
            Else  
                Return True  
            End If  
        End Function  
  
        ' NC-17 Place order.  
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click  
  
            ' NC-18 Set up and run stored procedure only if necessary input is present.  
            If isPlaceOrderReady() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-19 Create SqlCommand and identify it as a stored procedure.  
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)  
                cmdNewOrder.CommandType = CommandType.StoredProcedure  
  
                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID  
  
                ' NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))  
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value  
  
                ' NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))  
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value  
  
                ' NC-23 @Status. For a new order, the status is always O (open).  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))  
                cmdNewOrder.Parameters("@Status").Value = "O"  
  
                ' NC-24 add return value for stored procedure, which is the orderID  
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))  
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue  
  
                ' try – catch - finally  
                Try  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery()  
  
                    ' NC-25 Display the order number.  
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)  
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")  
  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("Order could not not be placed.")  
  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-26 Verify that order data is ready.  
        Private Function isPlaceOrderReady() As Boolean  
  
            ' Verify that CustomerID is present.  
            If txtCustomerID.Text = "" Then  
                MessageBox.Show("Please create customer account before placing order.")  
                Return False  
  
                ' Verify that Amount isn't 0   
            ElseIf (numOrderAmount.Value < 1) Then  
  
                MessageBox.Show("Please specify an order amount.")  
                Return False  
            Else  
                ' Order can be submitted.  
                Return True  
            End If  
        End Function  
  
        ' NC-27 Reset the form for another new account.  
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click  
            Me.ClearForm()  
        End Sub  
  
        ' NC-28 Clear values from controls.  
        Private Sub ClearForm()  
            txtCustomerName.Clear()  
            txtCustomerID.Clear()  
            dtpOrderDate.Value = DateTime.Now  
            numOrderAmount.Value = 0  
            Me.parsedCustomerID = 0  
        End Sub  
  
        ' NC-29 Close the form.  
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click  
            Me.Close()  
        End Sub  
  
    End Class  
End Namespace  
```  
  
|Comentario|Descripción|  
|----------------|-----------------|  
|NC\-1|Agregue System.Data.SqlClient y System.Configuration a la lista de espacios de nombres.|  
|NC\-2|Declare las variables `parsedCustomerID` y `orderID`, que usará más adelante.|  
|NC\-3|Llame al método `GetConnectionString` para obtener una cadena de conexión del archivo App.config y almacene el valor en la variable de cadena `connstr`.|  
|NC\-4|Agregue código al controlador de eventos Click para el botón `btnCreateAccount`.|  
|NC\-5|Incluya la llamada a `isCustomerName` alrededor del código de evento Click, de modo que `uspNewCustomer` solo se ejecute si un nombre de cliente está presente.|  
|NC\-6|Cree un objeto `SqlConnection` \(`conn`\) y páselo en la cadena de conexión en `connstr`.|  
|NC\-7|Cree un objeto `SqlCommand`, `cmdNewCustomer`.<br /><br /> -   Especifique `Sales.uspNewCustomer` como el procedimiento almacenado para ejecutar.<br />-   Use la propiedad `CommandType` para especificar que el comando es un procedimiento almacenado.|  
|NC\-8|Agregue el parámetro de entrada `@CustomerName` del procedimiento almacenado.<br /><br /> -   Agregue el parámetro a la colección `Parameters`.<br />-   Use la enumeración SqlDbType para especificar el tipo de parámetro como nvarchar \(40\).<br />-   Especifique `txtCustomerName.Text` como el origen.|  
|NC\-9|Agregue el parámetro de salida del procedimiento almacenado.<br /><br /> -   Agregue el parámetro a la colección `Parameters`.<br />-   Use `ParameterDirection.Output` para identificar el parámetro como resultado.|  
|NC\-10|Agregue un bloque Try – Catch – Finally para abrir la conexión, ejecute el procedimiento almacenado, controle las excepciones y después cierre la conexión.|  
|NC\-11|Abra la conexión \(`conn`\) que creó en NC\-6.|  
|NC\-12|Use el método `cmdNewCustomer` de `ExecuteNonQuery` para ejecutar el procedimiento almacenado `Sales.uspNewCustomer`, que ejecuta una instrucción `INSERT`, no una consulta.|  
|NC\-13|El valor de `@CustomerID` se devuelve como un valor IDENTITY de la base de datos.  Debido a que es un entero, tendrá que convertirlo a una cadena para mostrarla en el cuadro de texto Id. de cliente.<br /><br /> -   Ha declarado `parsedCustomerID` en NC\-2.<br />-   Almacena el valor de `@CustomerID` en `parsedCustomerID` para su uso posterior.<br />-   Convierte el identificador de cliente devuelto en una cadena y lo inserta en `txtCustomerID.Text`.|  
|NC\-14|Para este ejemplo, agregue una cláusula catch sencilla sin calidad de producción.|  
|NC\-15|Cierre siempre una conexión cuando termine de utilizarla para que se pueda liberar al grupo de conexiones.  Consulte [Agrupación de conexiones de SQL Server \(ADO.NET\)](http://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|  
|NC\-16|Defina un método para comprobar que un nombre de cliente está presente.<br /><br /> -   Si el cuadro de texto está vacío, muestra un mensaje y devuelve `false`, porque un nombre es necesario para crear la cuenta.<br />-   Si el cuadro de texto no está vacío, devuelve `true`.|  
|NC\-17|Agregue código al controlador de eventos Click para el botón `btnPlaceOrder`.|  
|NC\-18|Incluya la llamada a `isPlaceOrderReady` alrededor del código de evento `btnPlaceOrder_Click`, de modo que `uspPlaceNewOrder` no se ejecute si la entrada no está presente.|  
|De NC\-19 a NC\-25|Estas secciones de código son similares al código que se ha agregado para el controlador de eventos `btnCreateAccount_Click`.<br /><br /> -   NC\-19.  Cree el objeto `SqlCommand`, `cmdNewOrder` y especifique `Sales.uspPlaceOrder` como el procedimiento almacenado.<br />-   De NC\-20 a NC\-23 son los parámetros de entrada para el procedimiento almacenado.<br />-   NC\-24.  `@RC` contendrá un valor devuelto que es el identificador de pedido generado a partir de la base de datos.  Esta dirección del parámetro se especifica como `ReturnValue`.<br />-   NC\-25.  Almacene el valor del identificador de pedido en la variable `orderID` que declaró en NC\-2 y muestre el valor en un cuadro de mensaje.|  
|NC\-26|Defina un método para comprobar que existe un identificador de cliente y que se ha especificado una cantidad en `numOrderAmount`.|  
|NC\-27|Llame al método `ClearForm` en el controlador de eventos Click `btnAddAnotherAccount`.|  
|NC\-28|Cree el método `ClearForm` para borrar valores del formulario si desea agregar otro cliente.|  
|NC\-29|Cierre el formulario NewCustomer y devuelva el foco al formulario Navigation.|  
  
### Formulario FillOrCancel  
 El formulario FillOrCancel ejecuta una consulta que devuelve un pedido cuando se escribe un identificador de pedido y se elige el botón **Buscar pedido**.  La fila devuelta aparece en una cuadrícula de datos de solo lectura.  Puede marcar el pedido como cancelado \(X\) si elige el botón **Cancelar pedido** o puede marcar el pedido como relleno \(F\) si elige el botón **Rellenar pedido**.  Si elige de nuevo el botón **Buscar pedido**, la fila actualizada aparece.  
  
#### Cree controladores de eventos  
 Cree controladores de eventos Click vacíos para los cuatro botones del formulario.  
  
#### Crear código para FillOrCancel  
 Agregue el siguiente código al formulario FillOrCancel.  Recorra paso a paso los bloques de código mediante los comentarios numerados y la tabla que sigue al código.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//FC-1 More namespaces.  
using System.Text.RegularExpressions;  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class FillOrCancel : Form  
    {  
        //FC-2 Storage for OrderID.  
        private int parsedOrderID;  
  
        //FC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public FillOrCancel()  
        {  
            InitializeComponent();  
        }  
  
        //FC-4 Find an order.  
        private void btnFindByOrderID_Click(object sender, EventArgs e)  
        {  
            //FC-5 Prepare the connection and the command  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Define a query string that has a parameter for orderID.  
                string sql = "select * from Sales.Orders where orderID = @orderID";  
  
                //Create a SqlCommand object.  
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);  
  
                //Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;  
  
                //try – catch - finally  
                try  
                {  
                    //FC-6 Run the command and display the results.  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the command by using SqlDataReader.  
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();  
  
                    //Create a data table to hold the retrieved data.  
                    DataTable dataTable = new DataTable();  
  
                    //Load the data from SqlDataReader into the data table.  
                    dataTable.Load(rdr);  
  
                    //Display the data from the datatable in the datagridview.  
                    this.dgvCustomerOrders.DataSource = dataTable;  
  
                    //Close the SqlDataReader.  
                    rdr.Close();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-7 Cancel an order.  
        private void btnCancelOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                // Create command and identify it as a stored procedure.  
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;  
  
                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                // try-catch-finally  
                try  
                {  
                    // Open the connection.  
                    conn.Open();  
  
                    // Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery();  
                }  
                // A simple catch.  
                catch  
                {  
                    MessageBox.Show("The cancel operation was not completed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-8 Fill an order.  
        private void btnFillOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Create command and identify it as a stored procedure.  
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);  
                cmdFillOrder.CommandType = CommandType.StoredProcedure;  
  
                // Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                //Add the second input parameter.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));  
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;  
  
                //try – catch - finally  
                try  
                {  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the cmdFillOrder command.  
                    cmdFillOrder.ExecuteNonQuery();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The fill operation was not completed.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-9 Verify that OrderID is ready.  
        private bool isOrderID()  
        {  
  
            //Check for input in the Order ID text box.  
            if (txtOrderID.Text == "")  
            {  
                MessageBox.Show("Please specify the Order ID.");  
                return false;  
            }  
  
            // Check for characters other than integers.  
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))  
            {  
               //Show message and clear input.  
                MessageBox.Show("Please specify integers only.");  
                txtOrderID.Clear();  
                return false;  
            }  
            else  
            {  
                //Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text);  
                return true;  
            }  
        }  
  
        //Close the form.  
        private void btnFinishUpdates_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' FC-1 More namespaces.  
Imports System.Text.RegularExpressions  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class FillOrCancel  
        Inherits Form  
        ' FC-2 Storage for OrderID  
        Private parsedOrderID As Integer  
  
        ' FC-3 Specify a connection string  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' FC-4 Find an order.  
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click  
  
            ' FC-5 Prepare the connection and the command.  
  
            If isOrderID() Then  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Define the query string that has a parameter for orderID.  
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"  
  
                ' Create a SqlCommand object.  
                Dim cmdOrderID As New SqlCommand(sql, conn)  
  
                ' Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' FC-6 Run the command and display the results.  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the command by using SqlDataReader.  
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()  
  
                    ' Create a data table to hold the retrieved data.  
                    Dim dataTable As New DataTable()  
  
                    ' Load the data from the SqlDataReader into the data table.  
                    dataTable.Load(rdr)  
  
                    ' Display the data from the data table in the datagridview.  
                    Me.dgvCustomerOrders.DataSource = dataTable  
  
                    ' Close the SqlDataReader.  
                    rdr.Close()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-7 Cancel an order.  
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create the command and identify it as a stored procedure.  
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The cancel operation was not completed.")  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-8 Fill an order.  
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create command and identify it as a stored procedure.  
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)  
                cmdFillOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' Add second input parameter.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))  
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdFillOrder command.   
                    cmdFillOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The fill operation was not completed.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-9 Verify that OrderID is ready.  
        Private Function isOrderID() As Boolean  
  
            ' Check for input in the Order ID text box.  
            If txtOrderID.Text = "" Then  
                MessageBox.Show("Please specify the Order ID.")  
                Return False  
  
                ' Check for characters other than integers.  
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then  
  
                ' Show message and clear input.  
                MessageBox.Show("Please specify integers only.")  
                txtOrderID.Clear()  
                Return False  
  
            Else  
                ' Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text)  
                Return True  
  
            End If  
        End Function  
  
        ' Close the form.  
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
|Comentario|Descripción|  
|----------------|-----------------|  
|FC\-1|Agregue System.Data.SqlClient, System.Configuration y System.Text.RegularExpressions a la lista de espacios de nombres.|  
|FC\-2|Declare la variable `parsedOrderID`.|  
|FC\-3|Llame al método `GetConnectionString` para obtener una cadena de conexión del archivo App.config y almacene el valor en la variable de cadena `connstr`.|  
|FC\-4|Agregue código al controlador de eventos Click para `btnFindOrderByID`.|  
|FC\-5|¿Le resulta familiar?  Estas tareas se requieren antes de intentar ejecutar una instrucción SQL o un procedimiento almacenado.<br /><br /> -   Cree un objeto SqlConnection.<br />-   Defina la instrucción SQL o especifique el nombre del procedimiento almacenado.  \(En este caso, ejecutará una instrucción `SELECT`.\)<br />-   Crear un objeto `SqlCommand`.<br />-   Defina los parámetros para la instrucción SQL o procedimiento almacenado.|  
|FC\-6|Este código usa `SqlDataReader` y `DataTable` para recuperar y mostrar el resultado de la consulta.<br /><br /> -   Abra la conexión.<br />-   Cree un SqlDataReader, `rdr`, mediante la ejecución del método `cmdOrderID` de `ExecuteReader`.<br />-   Cree un objeto `DataTable` para que contenga los datos recuperados.<br />-   Cargue los datos de `SqlDataReader` en el objeto `DataTable`.<br />-   Muestre los datos en el control DataGridView especificando `DataTable` como `DataSource` para el control DataGridView.<br />-   Cierre SqlDataReader.|  
|FC\-7|Agregue código al controlador de eventos Click para `btnCancelOrder`.  Este código ejecuta el procedimiento almacenado `Sales.uspCancelOrder`.|  
|FC\-8|Agregue código al controlador de eventos Click para `btnFillOrder`.  Este código ejecuta el procedimiento almacenado `Sales.uspFillOrder`.|  
|FC\-9|Cree un método para comprobar que `OrderID` está listo para poder enviarse como parámetro al objeto `SqlCommand`.<br /><br /> -   Asegúrese de que un identificador se ha escrito en `txtOrderID`.<br />-   Use `Regex.IsMatch` para definir una comprobación simple de caracteres no enteros.<br />-   Ha declarado la variable `parsedOrderID` en FC\-2.<br />-   Si la entrada es válida, convierta el texto en un entero y almacene el valor en la variable `parsedOrderID`.<br />-   Incluya el método `isOrderID` alrededor de los controladores de eventos Click `btnFindByOrderID`, `btnCancelOrder` y `btnFillOrder`.|  
  
##  <a name="BKMK_testyourapplication"></a> Probar la aplicación  
 Elija la tecla F5 para compilar y probar la aplicación después del código de cada controlador del evento Click y, a continuación, después de haber terminado la codificación.