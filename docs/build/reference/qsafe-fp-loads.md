---
title: "/Qsafe_fp_loads | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 2b2ce52d-ba57-4bd3-a739-47a7f8bfaba9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qsafe_fp_loads
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将整数移动指令用于浮点值，并禁用特定浮点加载优化。  
  
## 语法  
  
```  
/Qsafe_fp_loads  
```  
  
## 备注  
 **\/Qsafe\_fp\_loads** 仅可在面向 x86 的编译器中使用；它不是在针对x64或ARM编译器。  
  
 **\/Qsafe\_fp\_loads**强制编译器使用整数移动指令代替浮点移动指令移动内存和MMX寄存器之间的数据。  此选项还禁用寄存器可在多个控件路径的浮点值的负载优化，则该值可能导致异常加载 ，例如，NaN 值加载。  
  
 此选项是被重写用[\/fp:except](../../build/reference/fp-specify-floating-point-behavior.md)。  **\/Qsafe\_fp\_loads** specifies a subset of the compiler behavior that's specified by **\/fp:except**指定的由指定的编译器行为的一个子集。  
  
 **\/Qsafe\_fp\_loads** 是不兼容 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 和 [\/fp:fast](../../build/reference/fp-specify-floating-point-behavior.md)。  有关浮点编译器选项的更多信息，请参见[\/fp（指定浮点行为）](../../build/reference/fp-specify-floating-point-behavior.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [\/Q 选项（低级别操作）](../../build/reference/q-options-low-level-operations.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)