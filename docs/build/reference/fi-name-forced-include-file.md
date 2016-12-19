---
title: "/FI（命名强制包含文件） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCNMakeTool.ForcedIncludes"
  - "VC.Project.VCCLCompilerTool.ForcedIncludeFiles"
  - "VC.Project.VCCLWCECompilerTool.ForcedIncludeFiles"
  - "/fi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FI 编译器选项 [C++]"
  - "FI 编译器选项 [C++]"
  - "-FI 编译器选项 [C++]"
  - "预处理头文件编译器选项 [C++]"
ms.assetid: 07e79577-8152-4df9-a64c-aae08c603397
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FI（命名强制包含文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选项使预处理器处理指定的头文件。  
  
## 语法  
  
```  
/FI[ ]pathname  
```  
  
## 备注  
 此选项的作用与在命令行上、CL 环境变量中或命令文件中指定源文件，并同时在每个源文件的第一行上的 `#include` 指令中用双引号指定该头文件相同。  如果使用多个 **\/FI** 选项，将按 CL 处理文件的顺序来包含这些文件。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“高级”**属性页。  
  
4.  修改**“强制包含”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedIncludeFiles%2A>。  
  
## 请参阅  
 [输出文件 \(\/F\) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)