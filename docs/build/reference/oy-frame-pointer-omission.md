---
title: "/Oy（框架指针省略） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.OmitFramePointers"
  - "/oy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Oy 编译器选项 [C++]"
  - "框架指针省略编译器选项 [C++]"
  - "省略框架指针"
  - "Oy 编译器选项 [C++]"
  - "-Oy 编译器选项 [C++]"
  - "堆栈帧指针编译器选项 [C++]"
  - "取消框架指针的创建"
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# /Oy（框架指针省略）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

禁止在调用堆栈上创建帧指针。  
  
## 语法  
  
```  
/Oy[-]  
```  
  
## 备注  
 此选项可以加快函数调用的速度，因为无需设置和移除任何框架指针。  它还可以使一个或多个寄存器（Intel 386 或更高版本上的 EBP）空闲出来，以便存储频繁使用的变量和子表达式。  
  
 **\/Oy** 启用框架指针省略，而 **\/Oy\-** 禁止省略。 **\/Oy** 仅在 x86 编译器中可用。  
  
 如果代码需要基于 EBP 进行寻址，可以在 **\/Ox** 选项后指定 **\/Oy–** 选项，或使用带“**y**”和 **off** 参数的 [optimize](../../preprocessor/optimize.md)，以便通过基于 EBP 的寻址获得最大程度的优化。  编译器可检测大部分需要基于 EBP 的寻址的情况（例如，使用 `_alloca` 和 `setjmp` 函数以及使用结构化异常处理的情况）。  
  
 [\/Ox（完全优化）](../../build/reference/ox-full-optimization.md) 和 [\/O1、\/O2（最小化大小、最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 选项表示 **\/Oy**。  在 **\/Ox**、**\/O1** 或 **\/O2** 选项后指定 **\/Oy–** 将禁用 **\/Oy**，无论它是显式还是隐式指定的。  
  
 **\/Oy** 编译器选项使得调试器更加难以使用，这是因为编译器取消显示帧指针信息。  如果指定 debug 编译器选项（[\/Z7、\/Zi、\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)），则建议你在任何其他优化编译器选项后指定 **\/Oy\-** 选项。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“优化”**属性页。  
  
4.  修改**“省略框架指针”**属性。  此属性仅添加或移除 **\/Oy** 选项。  如果要添加 **\/Oy\-** 选项，请单击**“命令行”**并修改**“附加选项”**。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>。  
  
## 请参阅  
 [\/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)