---
title: "&lt;Package&gt; (Elemento, Arranque) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<package> (elemento) [arranque]"
ms.assetid: ecd06658-ad02-4440-bccd-88437b7fb816
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# &lt;Package&gt; (Elemento, Arranque)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento `Package` es el elemento XML de nivel superior dentro de un archivo de paquete.  
  
## Sintaxis  
  
```  
<Package  
    Culture  
    Name  
    LicenseAgreement  
>  
    <InstallChecks>  
        <AssemblyCheck   
            Property  
            Name  
            PublicKeyToken  
            Version  
            Language  
            ProcessorArchitecture  
        />  
        <RegistryCheck  
            Property  
            Key  
            Value  
        />  
        <ExternalCheck   
            PackageFile  
            Property  
            Arguments  
            Log  
        />  
        <FileCheck   
            Property  
            FileName  
            SearchPath  
            SpecialFolder  
            SearchDepth  
        />  
        <MsiProductCheck   
            Property  
            Product  
            Feature  
        />  
        <RegistryFileCheck   
            Property  
            Key  
            Value  
            File  
            SearchDepth  
        />  
    </InstallChecks>  
  
    <Commands  
        Reboot  
    >  
        <Command  
            PackageFile  
            Arguments  
            EstimatedInstallSeconds  
            EstimatedDiskBytes  
            EstimatedTempBytes  
            Log  
        >  
            <InstallConditions>  
                <BypassIf   
                    Property  
                    Compare  
                    Value  
                    Schedule  
                />  
                <FailIf   
                    Property  
                    Compare  
                    Value  
                    String  
                    Schedule  
                />  
            </InstallConditions>  
            <ExitCodes>  
                <ExitCode   
                    Value  
                    Result  
                    String  
                />  
            </ExitCodes>  
        </Command>  
    </Commands>  
  
    <PackageFiles  
        CopyAllComponents  
    >  
        <PackageFile   
            Name  
            Path  
            HomeSite  
            PublicKey  
        />  
    </PackageFiles>  
  
    <Strings>  
        <String  
            Name  
        >  
        </String>  
    </Strings>  
  
    <Schedules>  
        <Schedule  
            Name  
        >  
           <BuildList />  
           <BeforePackage />  
           <AfterPackage />  
        </Schedule>  
    </Schedules>  
</Package>  
```  
  
## Elementos y atributos  
 Se requiere el elemento `Package`.  Tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Culture`|Obligatorio.  Define la referencia cultural para este paquete, que determina el idioma que se va a utilizar.  Este atributo es una clave del elemento `Strings`, que muestra las cadenas específicas de la referencia cultural para los nombres del producto y los mensajes de error durante la instalación.|  
|`Name`|Obligatorio.  El nombre del paquete que se muestra al desarrollador dentro de una herramienta como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Este atributo es una clave del elemento `Strings`, que debe contener un elemento `String` en el que las propiedades `Name` y `Culture` están establecidas para coincidir con las propiedades `Name` y `Culture` de `Package`.|  
|`LicenseAgreement`|Opcional.  Especifica el nombre del archivo en el paquete de distribución que contiene el Contrato de licencia para el usuario final \(CLUF\).  Este archivo puede ser de texto sin formato \(.txt\) o formato de texto enriquecido.  \(.rtf\)|  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra un archivo de paquete completo para la redistribución de [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.rtf"  
>  
  
    <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
    </PackageFiles>  
  
    <!-- Defines a localizable string table for error messages-->  
    <Strings>  
        <String Name="DisplayName">.NET Framework 2.0</String>  
        <String Name="Culture">en</String>  
        <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>  
        <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>  
        <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>  
        <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>  
        <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>  
        <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>  
        <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>  
        <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>  
        <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>  
        <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>  
        <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>  
    </Strings>  
  
</Package>  
```  
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)