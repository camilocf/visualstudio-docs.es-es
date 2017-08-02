---
title: "Registrar un Service1 de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de lenguaje [managed package framework], registrar"
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Registrar un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En el marco de trabajo de paquete administrado \(MPF\), el servicio de lenguaje es ofrecido por un VSPackage \(consulte [VSPackages](../../extensibility/internals/vspackages.md)\) y se registra con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] agregando entradas y claves del registro. Este proceso de registro se realiza parcialmente durante la instalación y parcialmente en tiempo de ejecución.  
  
## Registrar el servicio de lenguaje mediante atributos  
 Los siguientes atributos se usan para registrar un servicio de lenguaje.  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>  
  
 A continuación se explican estos atributos  
  
### ProvideServiceAttribute  
 Este atributo registra el servicio de lenguaje como un servicio.  
  
### Ejemplo  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideServiceAttribute(typeof(TestLanguageService),  
                             ServiceName = "Test Language Service")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### ProvideLanguageServiceAttribute  
 Este atributo registra el servicio de lenguaje concreto, como un servicio de lenguaje. Permite establecer las opciones que especifican las características que ofrece el servicio de lenguaje. En el ejemplo se muestra un subconjunto de las opciones que puede proporcionar un servicio de lenguaje. Para obtener el conjunto completo de opciones de servicio de lenguaje, consulte <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>.  
  
### Ejemplo  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),  
                             "Test Language",  
                             106,             // resource ID of localized language name  
                             CodeSense = true,             // Supports IntelliSense  
                             RequestStockColors = false,   // Supplies custom colors  
                             EnableCommenting = true,      // Supports commenting out code  
                             EnableAsyncCompletion = true  // Supports background parsing  
                             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### ProvideLanguageExtensionAttribute  
 Este atributo asocia el servicio de lenguaje con una extensión de archivo. Siempre que se carga un archivo con dicha extensión, en cualquier proyecto su servicio de lenguaje se inicia y utiliza para mostrar el contenido del archivo.  
  
### Ejemplo  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),  
                                       ".Testext")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### ProvideLanguageCodeExpansionAttribute  
 Este atributo registra una ubicación de código que se obtienen las plantillas de expansión o fragmento de código. Esta información se usa por el **Explorador de fragmentos de código** y el editor cuando se inserta un fragmento de código en el archivo de origen.  
  
### Ejemplo  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageCodeExpansionAttribute(  
             typeof(TestLanguageService),  
             "Test Language", // Name of language used as registry key.  
             106,           // Resource ID of localized name of language service.  
             "testlanguage",  // language key used in snippet templates.  
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index  
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +  
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### ProvideLanguageEditorOptionPageAttribute  
 Este atributo registra una página de propiedades que se mostrarán en el **opciones** cuadro de diálogo en el **Editor de texto** categoría. Utilice uno de estos atributos para cada página que se mostrará para el servicio de lenguaje. Si necesita organizar sus páginas en una estructura de árbol, utilice atributos adicionales para definir cada nodo del árbol.  
  
### Ejemplo  
 Este ejemplo muestra dos páginas de propiedades, **opciones** y **sangría**, y un nodo que contiene la segunda página de propiedades.  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Options",      // Registry key name for property page  
             "#242",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Advanced",     // Registry key name for node  
             "#243",         // Localized name of node  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             @"Advanced\Indenting",     // Registry key name for property page  
             "#244",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
## Ofrecer el servicio de lenguaje en tiempo de ejecución  
 Cuando se carga el paquete de idioma, debe indicar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que el servicio de lenguaje está listo. Para ello se proffering el servicio. Esto se hace en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> \(método\). Además, debe iniciar un temporizador que llama el servicio de lenguaje durante períodos de inactividad, por lo que pueden realizarse análisis de segundo plano. Este temporizador inactivo también se utiliza para actualizar las propiedades de documento si ha implementado alguna a través de la <xref:Microsoft.VisualStudio.Package.DocumentProperties> clase. Para admitir un temporizador, debe implementar el paquete de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> interfaz \(sólo el <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> método debe implementarse completamente; los métodos restantes pueden devolver valores predeterminados\).  
  
### Ejemplo  
 Este ejemplo muestra un enfoque típico para proffering un servicio y proporcionar un temporizador inactivo.  
  
```c#  
  
using System;  
using System.Runtime.InteropServices;  
using System.ComponentModel.Design;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.OLE.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,  
        AutoOutlining = true,  
        EnableCommenting = true,  
        MatchBraces = true,  
        ShowMatchingBrace = true)]  
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package  
  
    public class TestLanguagePackage : Package, IOleComponent  
    {  
        private uint m_componentID;  
  
        protected override void Initialize()  
        {  
            base.Initialize();  // required  
  
            // Proffer the service.  
            IServiceContainer serviceContainer = this as IServiceContainer;  
            TestLanguageService langService      = new TestLanguageService();  
            langService.SetSite(this);  
            serviceContainer.AddService(typeof(TestLanguageService),  
                                        langService,  
                                        true);  
  
            // Register a timer to call our language service during  
            // idle periods.  
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                       as IOleComponentManager;  
            if (m_componentID == 0 && mgr != null)  
            {  
                OLECRINFO[] crinfo = new OLECRINFO[1];  
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));  
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |  
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;  
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal     |  
                                              (uint)_OLECADVF.olecadvfRedrawOff |  
                                              (uint)_OLECADVF.olecadvfWarningsOff;  
                crinfo[0].uIdleTimeInterval = 1000;  
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);  
            }  
        }  
  
        protected override void Dispose(bool disposing)  
        {  
            if (m_componentID != 0)  
            {  
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                           as IOleComponentManager;  
                if (mgr != null)  
                {  
                    int hr = mgr.FRevokeComponent(m_componentID);  
                }  
                m_componentID = 0;  
            }  
  
            base.Dispose(disposing);  
        }  
  
        #region IOleComponent Members  
  
        public int FDoIdle(uint grfidlef)  
        {  
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;  
            // Use typeof(TestLanguageService) because we need to  
            // reference the GUID for our language service.  
            LanguageService service = GetService(typeof(TestLanguageService))  
                                      as LanguageService;  
            if (service != null)  
            {  
                service.OnIdle(bPeriodic);  
            }  
            return 0;  
        }  
  
        public int FContinueMessageLoop(uint uReason,  
                                        IntPtr pvLoopData,  
                                        MSG[] pMsgPeeked)  
        {  
            return 1;  
        }  
  
        public int FPreTranslateMessage(MSG[] pMsg)  
        {  
            return 0;  
        }  
  
        public int FQueryTerminate(int fPromptUser)  
        {  
            return 1;  
        }  
  
        public int FReserved1(uint dwReserved,  
                              uint message,  
                              IntPtr wParam,  
                              IntPtr lParam)  
        {  
            return 1;  
        }  
  
        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)  
        {  
            return IntPtr.Zero;  
        }  
  
        public void OnActivationChange(IOleComponent pic,  
                                       int fSameComponent,  
                                       OLECRINFO[] pcrinfo,  
                                       int fHostIsActivating,  
                                       OLECHOSTINFO[] pchostinfo,  
                                       uint dwReserved)  
        {  
        }  
  
        public void OnAppActivate(int fActive, uint dwOtherThreadID)  
        {  
        }  
  
        public void OnEnterState(uint uStateID, int fEnter)  
        {  
        }  
  
        public void OnLoseActivation()  
        {  
        }  
  
        public void Terminate()  
        {  
        }  
  
        #endregion  
    }  
}   
```