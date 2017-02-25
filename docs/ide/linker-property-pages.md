---
title: "“链接器”属性页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.RegisterOutput"
  - "VC.Project.VCLinkerTool.IgnoreImportLibrary"
  - "VC.Project.VCLinkerTool.UseLibraryDependencyInputs"
  - "VC.Project.VCLinkerTool.LinkLibraryDependencies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "按用户重定向"
  - "“链接器”属性页"
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# “链接器”属性页
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题论述**“常规”**链接器属性页上的下列属性：  
  
 **忽略导入库**  
 通知链接器不要尝试将任何从此生成产生的 .lib 输出链接到依赖项目中。  这允许项目系统处理生成时不产生 .lib 文件的 .dll 文件。  如果一个项目依赖另一个产生 DLL 的项目，项目系统将自动链接该子项目产生的 .lib 文件。  这对产生 COM DLL 或纯资源 DLL 的项目可能不是必需的，这些 DLL 没有任何具有特定意义的导出。  如果 DLL 没有导出，链接器将不生成 .lib 文件。  如果磁盘上不存在导出 .lib 文件，而项目系统通知链接器链接此（缺少的）DLL，链接将失败。  
  
 使用“忽略导入库”解决此问题。  当设置为 `Yes` 时，项目系统将忽略此 .lib 文件是否存在，并使依赖该项目的任何项目不链接到不存在的 .lib 文件。  
  
 若要以编程方式访问此属性，请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>。  
  
 **注册输出**  
 运行 regsvr32.exe \/s $\(TargetPath\)，它仅在 .dll 项目上有效。  对于 .exe 项目，忽略该属性。  如果要注册 .exe 输出，在配置上设置生成后事件，以执行已注册的 .exe 文件始终要求的自定义注册。  
  
 若要以编程方式访问此属性，请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>。  
  
 **每个用户的重定向**  
 传统上在 HKEY\_CLASSES\_ROOT \(HKCR\) 中完成 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中的注册。  要使用 [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)] 访问 HKCR，您必须在提升模式下运行 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  开发人员并非总是需要在提升模式下运行，但是仍必须进行注册。  每用户的重定向允许您无需在此模式下运行即可注册。  
  
 每用户的重定向会强制将针对 HKCR 的任何写入重定向到 HKEY\_CURRENT\_USER \(HKCU\)。  如果关闭每用户的重定向，则当程序尝试写入 HKCR 时可导致[项目生成错误 PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md)。  
  
 **链接库依赖项**  
 为您提供在依赖项目所生成的 .lib 文件中进行链接的选择。  您通常需要在 .lib 文件中进行链接。  
  
 你也可以通过提供文件名和相对路径来指定 .obj 文件，如 **..\\..\\MyLibProject\\MyObjFile.obj**。  如果 .obj 文件 \#includes 的源代码预编译标头，例如 pch.h，及 pch.obj 文件所在的文件夹与 **MyObjFile.obj**相似，那么你还必须添加 **pch.obj** 作为附加依赖项。  
  
 **使用库依赖项输入**  
 在一个大项目中，当依赖项目生成 .lib 文件时，增量链接是被禁用的。  如果有许多生成 .lib 文件的依赖项目，则生成应用程序会花很长时间。  当该属性设置为 `Yes` 时，项目系统在依赖项目所生成的 .lib 文件的 .obj 文件中进行链接，从而启用增量链接。  
  
 有关如何访问**“常规”**链接器属性页的信息，请参见[如何：用属性页指定项目属性](../misc/how-to-specify-project-properties-with-property-pages.md)。  
  
## 请参阅  
 [VC\+\+ Directories, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-cn/e027448b-c811-4c3d-8531-4325ad3f6e02)   
 [属性页](../ide/property-pages-visual-cpp.md)