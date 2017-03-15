---
title: "/ASSEMBLYLINKRESOURCE（链接到 .NET Framework 资源） | Microsoft Docs"
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
  - "/ASSEMBLYLINKRESOURCE"
  - "VC.Project.VCLinkerTool.AssemblyLinkResource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ASSEMBLYLINKRESOURCE 链接器选项"
  - "ASSEMBLYLINKRESOURCE 链接器选项"
  - "-ASSEMBLYLINKRESOURCE 链接器选项"
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ASSEMBLYLINKRESOURCE（链接到 .NET Framework 资源）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ASSEMBLYLINKRESOURCE:filename  
```  
  
## 备注  
 其中：  
  
 *filename*  
 要从程序集链接的 .NET Framework 资源文件。  
  
## 备注  
 \/ASSEMBLYLINKRESOURCE 选项创建指向输出文件中的 .NET Framework 资源的链接；资源文件不会放入输出文件中。  [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) 在输出文件中嵌入资源文件。  
  
 当用链接器创建时，链接的资源在程序集中是公共的。  
  
 \/ASSEMBLYLINKRESOURCE 要求编译包括 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md)；[\/LN](../../build/reference/ln-create-msil-module.md) 或 [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) 不允许与 \/ASSEMBLYLINKRESOURCE 一起使用。  
  
 如果 *filename* 是由 [Resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) 或在开发环境中（举例）创建的 .NET Framework 资源文件，则可以通过 **System.Resources** 命名空间中的成员访问它。  有关更多信息，请参见 [System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx)。  对于所有其他资源，请使用 **System.Reflection.Assembly** 类中的 **GetManifestResource**\* 方法在运行时访问资源。  
  
 *filename* 可以为任何文件格式。  例如，您可能想将本机 DLL 设置为程序集的一部分，以便可将其安装到全局程序集缓存中，并且可从程序集中的托管代码访问它。  
  
 其他影响程序集生成的链接器选项为：  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  将该选项键入**“附加选项”**框中。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)