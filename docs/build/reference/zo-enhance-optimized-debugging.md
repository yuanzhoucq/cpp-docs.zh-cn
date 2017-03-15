---
title: "/Zo（增强优化调试） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "-Zo"
  - "/Zo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zo 编译器选项 [C++]"
  - "Zo 编译器选项 [C++]"
  - "-Zo 编译器选项 [C++]"
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /Zo（增强优化调试）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在非调试生成中为优化代码生成增强调试信息。  
  
## 语法  
  
```cpp  
/Zo[-]  
```  
  
## 备注  
 **\/Zo**编译器开关为优化代码生成增强的调试信息。  优化可能为本地变量、代码重新排序、向量化循环和内联函数调用使用寄存器。  这些优化可能会掩盖的源代码和编译的对象代码之间的关系。  **\/Zo** 开关通知编译器为本地变量和内联函数生成附加调试信息。  当您在 Visual Studio 调试器中逐步通过优化代码时，可以使用它查看**自动**、**本地**和**监视**窗口中的变量。  它还启用堆栈跟踪以在 WinDBG 调试器中显示内联的函数。  当[\/Od](../../build/reference/od-disable-debug.md)被指定时，已禁用优化的调试构建 \(**\/Zo**\) 不需要生成其他调试信息。  使用**\/Zo**开关来调试启用优化的发布配置。  有关优化开关的详细信息，请参阅 [\/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)。  使用 **\/Zi** 或 **\/Z7** 指定调试信息时，默认在 Visual Studio 2015 中启用 **\/Zo** 选项。  指定**\/Zo\-**以显式禁用此编译器选项。  
  
 **\/Zo**开关也可在 Visual Studio 2013 Update 3 中使用，它可以替换先前未记录的**\/d2Zi\+**开关。  
  
### 在 Visual Studio 中设置 \/Zo 编译器选项  
  
1.  打开项目的“属性页”对话框。  有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  依次选择**“配置属性”**、**“C\/C\+\+”**文件夹。  
  
3.  选择“命令行”属性页。  
  
4.  修改**附加选项**属性以包含 `/Zo`，然后选择**确定**。  
  
### 以编程方式设置此编译器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [\/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)   
 [\/Z7、\/Zi、\/ZI（调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)   
 [编辑并继续](../Topic/Edit%20and%20Continue.md)