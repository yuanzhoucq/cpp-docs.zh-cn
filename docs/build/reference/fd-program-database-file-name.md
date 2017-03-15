---
title: "/Fd（程序数据库文件名） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/FD"
  - "VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName"
  - "VC.Project.VCCLCompilerTool.ProgramDataBaseFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 文件, 创建"
  - "/FD 编译器选项 [C++]"
  - "FD 编译器选项 [C++]"
  - "-FD 编译器选项 [C++]"
  - "PDB 文件, 创建"
  - "程序数据库编译器选项 [C++]"
  - "程序数据库文件名 [C++]"
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /Fd（程序数据库文件名）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为由 [\/Z7、\/Zi、\/ZI（调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md) 创建的程序数据库 \(PDB\) 文件指定文件名。  
  
## 语法  
  
```  
/Fdpathname  
```  
  
## 备注  
 如果不使用 **\/Fd**，PDB 文件名默认为 VC`x`0.pdb.，其中 `x` 是所使用的 Visual C\+\+ 的主版本。  
  
 如果指定的路径名不包含文件名（路径以反斜杠结尾），编译器将在指定的目录中创建一个名为 VC`x`0.pdb 的 .pdb 文件  
  
 如果指定的文件名不包含扩展名，编译器将使用 .pdb 作为扩展名。  
  
 此选项还命名用于最小重新生成和增量编译的状态 \(.idb\) 文件。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“输出文件”**属性页。  
  
4.  修改**“程序数据库文件名”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>。  
  
## 示例  
 此命令行创建名为 PROG.pdb 的 .pdb 文件和名为 PROG.idb 的 .idb 文件：  
  
```  
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP  
```  
  
## 请参阅  
 [输出文件 \(\/F\) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)