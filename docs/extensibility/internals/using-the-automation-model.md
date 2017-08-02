---
title: "Con el modelo de automatización | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 5655168e868e34befe83521a17b124c58be816b7
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-automation-model"></a>Con el modelo de automatización
Después de haber conectado el VSPackage a la automatización, puede obtener las propiedades y métodos llamando el <xref:EnvDTE.DTEClass.GetObject%2A>método en la <xref:EnvDTE._DTE>objeto, pasando una cadena que representa el objeto que desea recuperar.</xref:EnvDTE._DTE> </xref:EnvDTE.DTEClass.GetObject%2A>  
  
## <a name="obtaining-project-objects"></a>Obtener objetos de proyecto  
 Éstos son dos ejemplos de código que muestran cómo un consumidor de automatización Obtiene el proyecto de objetos de automatización. Para obtener información acerca de cómo obtener el objeto DTE, vea [Cómo: obtener referencias para los objetos DTE y DTE2](http://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb#  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp#  
void DoAutomation(void)  
{  
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.  
    pMyPkg = pDTE->GetObject("AcmeProjects");   
  
   // The '=' performs a Query Interface.  
   // Assumes pDTE is already available as a global.  
   // Use pMyPkg to access your projects object's properties and methods.  
}  
  
```  
  
 En este punto, puede usar los objetos de proyecto estándar que forman parte de un paquete VSPackage específico para bajar el modelo de jerarquía.  
  
 En el ejemplo de código siguiente se muestra cómo obtener un objeto personalizado que es una propiedad de un tipo de proyecto personalizadas.:  
  
```vb#  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 El código siguiente muestra los nombres de todas las propiedades en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno **General** opción la **herramientas** menú:  
  
```vb#  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:EnvDTE.DTEClass.GetObject%2A></xref:EnvDTE.DTEClass.GetObject%2A>