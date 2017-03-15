---
title: "/FA、/Fa（列出文件） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.AssemblerListingLocation"
  - "VC.Project.VCCLCompilerTool.ConfigureASMListing"
  - "VC.Project.VCCLWCECompilerTool.AssemblerOutput"
  - "VC.Project.VCCLCompilerTool.AssemblerListingLocation"
  - "/fa"
  - "VC.Project.VCCLCompilerTool.AssemblerOutput"
  - "VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FA 编译器选项 [C++]"
  - "仅列出程序集"
  - "FA 编译器选项 [C++]"
  - "-FA 编译器选项 [C++]"
  - "列出文件类型"
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /FA、/Fa（列出文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建包含程序集代码的清单文件。  
  
## 语法  
  
```  
/FA[c|s|u]  
/Fapathname  
```  
  
## 备注  
 参数控制源代码和机器码的生成以及清单文件的扩展名。  
  
 下表描述 **\/FA** 的各种不同的值。  可为 **\/FA** 指定多个值。  例如，可以指定 **\/FAsu**。  
  
|选项|清单内容和文件扩展名|  
|--------|----------------|  
|**\/FA**|程序集代码；.asm|  
|**\/FAc**|机器码和程序集代码；.cod|  
|**\/FAs**|源代码和程序集代码；.asm<br /><br /> 如果指定了 **\/FAcs**，则文件扩展名将为 .cod|  
|**\/FAu**|导致用 UTF\-8 格式和字节顺序标记创建输出文件。  默认情况下，文件编码为 ANSI，但是如果您希望清单文件在所有系统中均正确显示，或者如果要使用 Unicode 源代码文件作为编译器的输入，则请使用 **\/FAu**。<br /><br /> 如果指定了 **\/FAsu**，并且源代码文件使用 UTF\-8 之外的 Unicode 编码，则 .asm 文件中的代码行可能无法正确显示。|  
  
 默认情况下，清单文件获取与源文件相同的基名称。  使用 **\/Fa** 选项可以更改清单文件的名称和在其中创建清单文件的目录。  
  
|\/Fa 用法|结果|  
|-------------|--------|  
|**\/Fa**|为编译中的每个源代码文件创建一个 *source\_file*.asm。|  
|**\/Fa** *filename*|将 *filename*.asm 放到当前目录中。  仅在编译单个源代码文件时有效。|  
|**\/Fa** *filename.extension*|将 *filename.extension* 放到当前目录中。  仅在编译单个源代码文件时有效。|  
|**\/Fa** *directory*\\|为编译中的每个源代码文件创建一个 *source\_file*.asm，并将其放到指定的*directory*中。  请注意必须有后缀反斜杠。  只允许使用当前磁盘上的路径。|  
|**\/Fa** *directory*\\*filename*|将 *文件名filename.asm 放到指定的* `directory` 中。  仅在编译单个源代码文件时有效。|  
|**\/Fa** *directory*\\*filename.extension*|*filename.extension*在指定的`directory`中。  仅在编译单个源代码文件时有效。|  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“输出文件”**属性页。  
  
4.  修改**“ASM 列表位置”**\(**\/Fa**\) 或**“汇编输出”**\(**\/FA**\) 属性（必须在**“命令行”**属性页的**“附加选项”**框中指定 **\/FAu**）。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>。  若要指定 **\/FAu**，请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 示例  
 下列命令行产生名为 HELLO.cod 的组合源代码和机器码清单：  
  
```  
CL /FAcs HELLO.CPP  
```  
  
## 请参阅  
 [输出文件 \(\/F\) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)