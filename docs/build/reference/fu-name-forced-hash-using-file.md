---
title: "/FU（命名强制 #using 文件） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.ForcedUsingFiles"
  - "/FU"
  - "VC.Project.VCNMakeTool.ForcedUsingAssemblies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FU 编译器选项 [C++]"
  - "FU 编译器选项 [C++]"
  - "-FU 编译器选项 [C++]"
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FU（命名强制 #using 文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

你可以使用一个编译器选项作为在源代码中将文件名传递到 [\#using 指令](../../preprocessor/hash-using-directive-cpp.md) 的另一种方法。  
  
## 语法  
  
```  
/FU file  
```  
  
## Arguments  
 `file`  
 指定要在此编译中引用的元数据文件。  
  
## 备注  
 \/FU 开关作为文件名。  若要指定多文件，请对每个使用 \/FU。  
  
 如果使用的是 [!INCLUDE[cppcli](../../build/reference/includes/cppcli_md.md)] 和引用元数据使用 [友元程序集](../../dotnet/friend-assemblies-cpp.md) 功能，因此不能使用 **\/FU**。  必须引用元数据通过代码使用 `#using`\- 具有 `[as friend]` 特性。  [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]\) 不支持友元程序集。  
  
 有关如何为公共语言运行时\(CLR\)创建程序集或模块的信息，请参见 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  有关如何在[!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]中生成查询的信息，请参见[生成应用程序和库](../Topic/Building%20apps%20and%20libraries%20\(C++-CX\).md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择**“高级”**属性页。  
  
4.  修改**“强制 \#using”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>。  
  
## 请参阅  
 [输出文件 \(\/F\) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)