---
title: "/analyze（代码分析） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.EnablePREfast"
  - "/analyze"
  - "VC.Project.VCCLCompilerTool.PREfastAdditionalOptions"
  - "VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/analyze 编译器选项 [C++]"
  - "analyze 编译器选项 [C++]"
  - "-C 编译器选项 [C++]"
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# /analyze（代码分析）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

启用代码分析和控制选项。  
  
## 语法  
  
```  
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only]  
```  
  
## 参数  
 \/analyze  
 在默认模式下打开分析。  分析输出转到**“输出”**窗口（与其他错误信息类似）。  使用 **\/analyze\-** 显式关闭分析。  
  
 \/analyze:WX\-  
 使用 **\/WX** 进行编译时，指定 **\/analyze:WX\-** 意味着代码分析警告不会被视为错误。  有关详细信息，请参阅 [\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won（警告等级）](../../build/reference/compiler-option-warning-level.md)。  
  
 \/analyze:log `filename`  
 将详细的分析器结果作为 XML 写入由 `filename` 指定的文件。  
  
 \/analyze:quiet  
 关闭对**“输出”**窗口的分析器输出。  
  
 \/analyze:stacksize `number`  
 用于此选项的 `number` 参数指定为其生成警告 [C6262](../Topic/C6262.md) 的堆栈帧的大小（以字节为单位）。  如果未指定此参数，则默认情况下堆栈帧的大小为 16KB。  
  
 \/analyze:max\_paths `number`  
 用于此选项的 `number` 参数指定要分析的代码路径的最大数目。  如果未指定此参数，则默认情况下此数目为 256。  值越大，执行的检查越彻底，但分析时间可能会更长。  
  
 \/analyze:only  
 通常，编译器在运行分析器后会生成代码并执行更多语法检查。  **\/analyze:only** 选项将关闭此代码生成传递；这会使分析速度变得更快，但不会发出可能已由编译器的代码生成传递发现的编译错误和警告。  如果程序存在代码生成错误，则分析结果可能不可靠；因此，建议你只有在代码已传递代码生成语法检查且没有错误时才使用此选项。  
  
## 备注  
 有关更多信息，请参见[C\/C\+\+ 代码分析概述](../Topic/Code%20Analysis%20for%20C-C++%20Overview.md)和[C\/C\+\+ 代码分析警告](../Topic/Code%20Analysis%20for%20C-C++%20Warnings.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“代码分析”**节点。  
  
4.  选择**“常规”**属性页。  
  
5.  修改一个或多个**“代码分析”**属性。  
  
### 以编程方式设置此编译器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)