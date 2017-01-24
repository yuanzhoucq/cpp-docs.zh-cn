---
title: "/ASSEMBLYRESOURCE（嵌入托管资源） | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.EmbedManagedResourceFile"
  - "/ASSEMBLYRESOURCE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ASSEMBLYRESOURCE 链接器选项"
  - "程序集 [C++]"
  - "程序集 [C++], 链接资源文件"
  - "ASSEMBLYRESOURCE 链接器选项"
  - "-ASSEMBLYRESOURCE 链接器选项"
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ASSEMBLYRESOURCE（嵌入托管资源）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]  
```  
  
## 参数  
 *filename*  
 要在此程序集中嵌入的托管资源。  
  
 *name*  
 可选。  资源的逻辑名称；用于加载此资源的名称。  默认为文件的名称。  
  
 还可以指定该文件在程序集清单中是否应是私有的。  默认情况下，*name* 在程序集中是公共的。  
  
## 备注  
 使用 \/ASSEMBLYRESOURCE 选项在程序集中嵌入资源。  
  
 当用链接器创建时，资源在程序集中是公共的。  链接器不允许重命名程序集中的资源。  
  
 例如，如果 *filename* 是通过[资源文件生成器 \(Resgen.exe\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) 或在开发环境中创建的 .NET Framework 资源 \(.resources\) 文件，则可以用 **System.Resources** 命名空间中的成员访问它（有关更多信息，请参见 [System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx)）。  对于所有其他资源，请使用 **System.Reflection.Assembly** 类中的 **GetManifestResource**\* 方法在运行时访问资源。  
  
 其他影响程序集生成的链接器选项为：  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“输入”属性页。  
  
4.  修改**“嵌入托管资源文件”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)