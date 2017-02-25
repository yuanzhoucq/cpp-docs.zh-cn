---
title: "/Oi（生成内部函数） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions"
  - "/oi"
  - "VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Oi 编译器选项 [C++]"
  - "生成内部函数编译器选项 [C++]"
  - "内部函数, 生成"
  - "Oi 编译器选项 [C++]"
  - "-Oi 编译器选项 [C++]"
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /Oi（生成内部函数）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用有助于应用程序更快运行的内部函数或其他特殊形式的函数替换某些函数调用。  
  
## 语法  
  
```  
/Oi[-]  
```  
  
## 备注  
 使用内部函数的程序比较快，因为它们没有函数调用系统开销。但是，由于创建了附加代码，它们可能比较大。  
  
 有关有内部形式的函数的更多信息，请参见 [内部](../../preprocessor/intrinsic.md)。  
  
 **\/Oi** 仅作为对编译器的请求，用于将某些函数调用替换为内部函数；为产生更好的性能，编译器可能会调用函数（而不会将该函数调用替换为内部函数）。  
  
 **x86 专用**  
  
 内部浮点函数不对输入值执行任何特殊检查，因此只在有限的输入范围内有效，且与同名库例程具有不同的异常处理和边界条件。  使用真正的内部形式意味着失去 IEEE 异常处理以及失去 `_matherr` 和 `errno` 功能；后者意味着失去 ANSI 一致性。  然而，内部形式可以显著提高浮点密集型程序的速度，而且对于很多程序来说，一致性问题几乎没有任何价值。  
  
 可以使用 [Za](../../build/reference/za-ze-disable-language-extensions.md) 编译器选项重写真正的内部浮点选项的生成。  在此情况下，函数将生成为库例程，后者将参数直接传递到浮点芯片，而不是将参数推送到程序堆栈。  
  
 **END x86 Specific**  
  
 还可以使用 [内部](../../preprocessor/intrinsic.md) 创建内部函数，或者使用 [函数](../../preprocessor/function-c-cpp.md) 显式强制函数调用。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“优化”**属性页。  
  
4.  修改**“启用内部函数”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>。  
  
## 请参阅  
 [\/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [编译器内部函数](../../intrinsics/compiler-intrinsics.md)