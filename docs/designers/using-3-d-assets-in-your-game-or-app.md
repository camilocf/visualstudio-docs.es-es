---
title: "Usar activos 3D en un juego o una aplicaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.ImageContentTask.ContentOutput"
  - "VC.Project.MeshContentTask.ContentOutput"
  - "VC.Project.ImageContentTask.GeneratePremultipliedAlpha"
  - "VC.Project.ImageContentTask.Compress"
  - "VC.Project.ShaderGraphContentTask.ContentOutput"
  - "VC.Project.ImageContentTask.GenerateMips"
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
caps.latest.revision: 17
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 17
---
# Usar activos 3D en un juego o una aplicaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este artículo se describe cómo se puede utilizar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para procesar activos 3D e incluirlos en las compilaciones.  
  
 Después de usar las herramientas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para crear activos 3D, el paso siguiente consiste en utilizarlos en la aplicación.  Pero antes de poder usarlos, los activos tienen que transformarse en un formato que DirectX pueda entender.  Para ayudarle a transformar los activos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona personalizaciones de compilación para cada clase de activo que puede generar.  Para incluir los activos en la compilación, basta con configurar el proyecto para que use las personalizaciones de compilación, agregar los activos al proyecto y configurar los activos para que usen la personalización de compilación correcta.  Después, puede cargar los activos en la aplicación y usarlos creando y rellenando los recursos de DirectX igual que haría en cualquier otra aplicación DirectX.  
  
## Configurar el proyecto  
 Para poder implementar los activos 3D como parte de la compilación, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tiene que conocer las clases de activos que se desea implementar.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ya conoce muchos tipos de archivo comunes, pero puesto que solo ciertas clases de aplicaciones utilizan activos 3D, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no supone que un proyecto compilará estas clases de archivos.  Puede indicar a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que la aplicación utiliza estas clases de activos mediante las *personalizaciones de compilación* \(archivos que indican a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cómo procesar los distintos tipos de archivos de una manera útil\) proporcionadas para cada clase de activo.  Como estas personalizaciones se aplican por proyecto, basta con agregar las personalizaciones adecuadas al proyecto.  
  
#### Para agregar las personalizaciones de compilación al proyecto  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Dependencias de compilación**, **Personalizaciones de compilación**.  Aparece el cuadro de diálogo **Archivos de personalizaciones de compilación de Visual C\+\+**.  
  
2.  En **Archivos de personalizaciones de compilación disponibles**, active las casillas correspondientes a los tipos de activo que desea usar en el proyecto, como se describe en esta tabla:  
  
    |Tipo de activo|Nombre de personalización de compilación|  
    |--------------------|----------------------------------------------|  
    |Texturas e imágenes|**ImageContentTask\(.targets, .props\)**|  
    |Modelos 3D|**MeshContentTask\(.targets, .props\)**|  
    |Sombreadores|**ShaderGraphContentTask\(.targets, .props\)**|  
  
3.  Elija el botón **Aceptar**.  
  
## Incluir activos en la compilación  
 Ahora que el proyecto sabe cuáles son las diferentes clases de activos 3D que desea usar, el paso siguiente consiste en indicarle qué archivos son activos 3D y de qué clases de activos se tratan.  
  
#### Para agregar un activo a la compilación  
  
1.  En el **Explorador de soluciones**, en el proyecto, abra el menú contextual de un activo y, a continuación, elija **Propiedades**.  Aparece el cuadro de diálogo **Página de propiedades** del activo.  
  
2.  Asegúrese de que las propiedades **Configuración** y **Plataforma** se establecen en los valores a los que desea que se apliquen los cambios.  
  
3.  En **Propiedades de configuración**, elija **General** y, en la cuadrícula de propiedades, en **General**, establezca la propiedad **Tipo de elemento** en el tipo de elemento de canalización de contenido adecuado.  Por ejemplo, para un archivo de imagen o de textura, elija **Canalización de contenido de la imagen**.  
  
    > [!IMPORTANT]
    >  De forma predeterminada, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supone que muchas clases de archivos de imagen se deben categorizar mediante el tipo de elemento **Imagen** que está integrado en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Por tanto, debe cambiar la propiedad **Tipo de elemento** de cada imagen que desea que procese la canalización de contenido de la imagen.  Otros tipos de archivos de código fuente de canalización de contenido para los modelos 3D y los gráficos del sombreador visual toman el valor predeterminado del **Tipo de elemento** correcto.  
  
4.  Elija el botón **Aceptar**.  
  
 Estos son los tres tipos de elemento de canalización de contenido y los tipos de archivo de código fuente y de salida asociados.  
  
|Tipo de elemento|Tipos de archivo de código fuente|Formato del archivo de salida|  
|----------------------|---------------------------------------|-----------------------------------|  
|**Canalización de contenido de la imagen**|Portable Network Graphics \(.png\)<br /><br /> JPEG \(.jpg, .jpeg, .jpe, .jfif\)<br /><br /> DirectDraw Surface \(.dds\)<br /><br /> Formato de intercambio de gráficos \(.gif\)<br /><br /> Mapa de bits \(.bmp, .dib\)<br /><br /> Formato de archivo de imagen etiquetado \(.tif, .tiff\)<br /><br /> Targa \(.tga\)|DirectDraw Surface \(.dds\)|  
|**Canalización de contenido de mallas**|Archivo de intercambio FBX de Autodesk \(.fbx\)<br /><br /> Archivo DAE de Collada \(.dae\)<br /><br /> Archivo OBJ de Wavefront \(.obj\)|Archivo 3D de malla \(.cmo\)|  
|**Canalización de contenido del sombreador**|Gráfico de sombreador visual \(.dgsl\)|Resultado del sombreador compilado \(.cso\)|  
  
## Configurar las propiedades de la canalización de contenido de activos  
 Se pueden establecer las propiedades de la canalización de contenido de cada archivo de activo para que se compile de una manera determinada.  
  
#### Para configurar las propiedades de la canalización de contenido  
  
1.  En el **Explorador de soluciones**, en el proyecto, abra el menú contextual del archivo de activos y, a continuación, elija **Propiedades**.  Aparece el cuadro de diálogo **Página de propiedades** del activo.  
  
2.  Asegúrese de que las propiedades **Configuración** y **Plataforma** se establecen en los valores a los que desea que se apliquen los cambios.  
  
3.  En **Propiedades de configuración**, elija el nodo de canalización de contenido \(por ejemplo, **Canalización de contenido de la imagen** para los activos de textura e imagen\) y, a continuación, en la cuadrícula de propiedades, establezca las propiedades en los valores adecuados.  Por ejemplo, para generar los mapas MIP para un activo de textura en tiempo de compilación, establezca la propiedad de **Generar Mips** en **Sí**.  
  
4.  Elija el botón **Aceptar**.  
  
### Configuración de la canalización de contenido de imagen  
 Cuando se utiliza la herramienta de canalización de contenido de la imagen para compilar un activo de textura, se puede comprimir la textura de varias maneras, indicar si se deben generar niveles de MIP en tiempo de compilación y cambiar el nombre del archivo de salida.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|**Comprimir**|Especifica el tipo de compresión que se utiliza para el archivo de salida.<br /><br /> Las opciones disponibles son:<br /><br /> -   **Sin compresión**<br />-   **Compresión BC1\_UNORM**<br />-   **Compresión BC1\_UNORM\_SRGB**<br />-   **Compresión BC2\_UNORM**<br />-   **Compresión BC2\_UNORM\_SRGB**<br />-   **Compresión BC3\_UNORM**<br />-   **Compresión BC3\_UNORM\_SRGB**<br />-   **Compresión BC4\_UNORM**<br />-   **Compresión BC4\_SNORM**<br />-   **Compresión BC5\_UNORM**<br />-   **Compresión BC5\_SNORM**<br />-   **Compresión BC6H\_UF16**<br />-   **Compresión BC6H\_SF16**<br />-   **Compresión BC7\_UNORM**<br />-   **Compresión BC7\_UNORM\_SRGB**<br /><br /> Para más detalles sobre los formatos de compresión admitidos en diferentes versiones de DirectX, vea la [guía de programación de DXGI](http://go.microsoft.com/fwlink/p/?LinkId=246265).|  
|Convertir a formato alpha premultiplicado|**Sí** para convertir la imagen al formato alpha premultiplicado en el archivo de salida, de lo contrario, **No**.  Solo se cambia el archivo de salida, la imagen original no se cambia.|  
|**Generar Mips**|**Sí** para generar una cadena completa de mapas MIP en tiempo de compilación e incluirla en el archivo de salida; de lo contrario, **No**.  Si es **No** y el archivo de código fuente ya contiene una cadena de mapas MIP, el archivo de salida tendrá una cadena de mapas MIP; de lo contrario, el archivo de salida no tendrá ninguna cadena de mapas MIP.|  
|**Salida de contenido**|Especifica el nombre del archivo de salida. **Important:**  Cambiar la extensión del nombre del archivo de salida no tiene ningún efecto sobre el formato del archivo.|  
  
### Configuración de la canalización de contenido de mallas  
 Cuando se utiliza la herramienta de canalización de contenido de mallas para compilar un activo de malla, se puede cambiar el nombre del archivo de salida.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|**Salida de contenido**|Especifica el nombre del archivo de salida. **Important:**  Cambiar la extensión del nombre del archivo de salida no tiene ningún efecto sobre el formato del archivo.|  
  
### Configuración de la canalización de contenido del sombreador  
 Cuando se utiliza la herramienta de canalización de contenido del sombreador para compilar un activo de sombreador, se puede cambiar el nombre del archivo de salida.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|**Salida de contenido**|Especifica el nombre del archivo de salida. **Important:**  Cambiar la extensión del nombre del archivo de salida no tiene ningún efecto sobre el formato del archivo.|  
  
## Cargar y usar activos 3D en tiempo de ejecución  
  
### Utilizar texturas e imágenes  
 Direct3D proporciona funciones para crear recursos de textura.  En Direct3D 11, la biblioteca de utilidades D3DX11 proporciona funciones adicionales para crear recursos de texturas y vistas de recursos de textura directamente a partir de archivos de imagen.  Para más detalles sobre cómo crear un recurso de textura en Direct3D 11, vea el tema sobre [texturas](http://go.microsoft.com/fwlink/p/?LinkID=246267).  Para más detalles sobre cómo usar la biblioteca D3DX11 para crear un recurso de textura o una vista de recursos de textura a partir de un archivo de imagen, vea el procedimiento para [iniciar una textura a partir de un archivo](http://go.microsoft.com/fwlink/p/?LinkId=246268).  
  
### Utilizar modelos 3D  
 Direct3D 11 no proporciona funciones para crear recursos a partir de modelos 3D.  En su lugar, tiene que escribir código que lea el archivo del modelo 3D y cree búferes de vértices y de índices que representen el modelo 3D y cualquier recurso que requiera el modelo, como texturas o sombreadores.  
  
### Utilizar sombreadores  
 Direct3D proporciona funciones para crear recursos de sombreador y enlazarlos a la canalización programable de gráficos.  Para más información sobre cómo crear un recurso de sombreador en Direct3D y enlazarlo a la canalización, vea la [guía de programación de HLSL](http://go.microsoft.com/fwlink/p/?LinkID=261521).  
  
 En la canalización programable de gráficos, cada fase de la canalización debe aportar a la siguiente fase de la canalización un resultado con formato de forma que se pueda entender.  Puesto que el Diseñador de sombras solo puede crear sombreadores de píxeles, esto significa que depende de la aplicación el garantizar que los datos que recibe están en el formato que se espera.  Hay varias fases del sombreador programables que tienen lugar antes que el sombreador de píxeles y que realizan transformaciones geométricas: el sombreador de vértices, el sombreador de casco, el sombreador de dominios y el sombreador de geometría.  La fase de teselación no programable también tiene lugar antes que el sombreador de píxeles.  Independientemente de cuál de estas fases preceda directamente al sombreador de píxeles, debe facilitar su resultado en este formato:  
  
```hlsl  
  
struct PixelShaderInput  
{  
    float4 pos : SV_POSITION;  
    float4 diffuse : COLOR;  
    float2 uv : TEXCOORD0;  
    float3 worldNorm : TEXCOORD1;  
    float3 worldPos : TEXCOORD2;  
    float3 toEye : TEXCOORD3;  
    float4 tangent : TEXCOORD4;  
    float3 normal : TEXCOORD5;  
};  
```  
  
 En función de los nodos del Diseñador de sombras que use en el sombreador, puede que tenga que proporcionar también datos adicionales en el formato adecuado según estas definiciones:  
  
```  
  
Texture2D Texture1 : register( t0 );  
Texture2D Texture2 : register( t1 );  
Texture2D Texture3 : register( t2 );  
Texture2D Texture4 : register( t3 );  
Texture2D Texture5 : register( t4 );  
Texture2D Texture6 : register( t5 );  
Texture2D Texture7 : register( t6 );  
Texture2D Texture8 : register( t7 );  
  
TextureCube CubeTexture1 : register( t8 );  
TextureCube CubeTexture2 : register( t9 );  
TextureCube CubeTexture3 : register( t10 );  
TextureCube CubeTexture4 : register( t11 );  
TextureCube CubeTexture5 : register( t12 );  
TextureCube CubeTexture6 : register( t13 );  
TextureCube CubeTexture7 : register( t14 );  
TextureCube CubeTexture8 : register( t15 );  
  
SamplerState TexSampler : register( s0 );  
  
cbuffer MaterialVars : register (b0)  
{  
    float4 MaterialAmbient;  
    float4 MaterialDiffuse;  
    float4 MaterialSpecular;  
    float4 MaterialEmissive;  
    float MaterialSpecularPower;  
};  
  
cbuffer LightVars : register (b1)  
{  
    float4 AmbientLight;  
    float4 LightColor[4];  
    float4 LightAttenuation[4];  
    float3 LightDirection[4];  
    float LightSpecularIntensity[4];  
    uint IsPointLight[4];  
    uint ActiveLights;  
}  
  
cbuffer ObjectVars : register(b2)  
{  
    float4x4 LocalToWorld4x4;  
    float4x4 LocalToProjected4x4;  
    float4x4 WorldToLocal4x4;  
    float4x4 WorldToView4x4;  
    float4x4 UVTransform4x4;  
    float3 EyePosition;  
};  
  
cbuffer MiscVars : register(b3)  
{  
    float ViewportWidth;  
    float ViewportHeight;  
    float Time;  
};  
```  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Cómo: Exportar una textura que contiene mapas MIP](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Describe cómo utilizar la canalización de contenido de la imagen para exportar una textura que contiene mapas MIP calculados previamente.|  
|[Cómo: Exportar una textura que tiene valores alfa previamente multiplicados](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Describe cómo utilizar la canalización de contenido de imagen para exportar una textura que contiene valores alfa multiplicados previamente.|  
|[Cómo: Exportar una textura para usarla con aplicaciones de Direct2D o Javascipt](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Describe cómo utilizar la canalización de contenido de la imagen para exportar una textura que se puede utilizar en una aplicación de Direct2D o JavaScript.|  
|[Trabajar con activos 3D para juegos y aplicaciones](../designers/working-with-3-d-assets-for-games-and-apps.md)|Describe las herramientas de edición que proporciona Visual Studio para crear y manipular activos 3D, que incluyen texturas e imágenes, modelos 3D y sombreadores.|  
|[Cómo: Exportar un sombreador](../designers/how-to-export-a-shader.md)|Describe cómo exportar un sombreador desde el Diseñador de sombras.|