---
title: "/Ox（完全优化） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.ToolOptimization"
  - "/ox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ox 编译器选项 [C++]"
  - "快速代码"
  - "完全优化"
  - "Ox 编译器选项 [C++]"
  - "-Ox 编译器选项 [C++]"
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# /Ox（完全优化）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 **\/Ox** 编译器选项可以优先选择生成执行速度更快的代码而不是大小更小的代码。  
  
## 语法  
  
```  
/Ox  
```  
  
## 备注  
 指定 **\/Ox** 编译器选项的作用与使用下列选项的作用相同：  
  
-   [\/Ob（内联函数展开）](../../build/reference/ob-inline-function-expansion.md)，其中选项参数为 2 \(**\/Ob2**\)  
  
-   [\/Og（全局优化）](../../build/reference/og-global-optimizations.md)  
  
-   [\/Oi（生成内部函数）](../../build/reference/oi-generate-intrinsic-functions.md)  
  
-   [\/Ot（代码速度优先）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)  
  
-   [\/Oy（框架指针省略）](../../build/reference/oy-frame-pointer-omission.md)  
  
 **\/Ox** 与下列各项互相排斥：  
  
-   [\/O1（最小化大小）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)  
  
-   [\/O2（最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)  
  
-   [\/Od（禁用（调试））](../../build/reference/od-disable-debug.md)  
  
 **\/Ox** 编译器选项还支持命名返回值优化，此优化可消除基于堆栈的返回值的复制构造函数和析构函数。  有关详细信息，请参阅[\/O1、\/O2（最小化大小、最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)。  
  
 如果您指定 **\/Oxs**，则可以取消 **\/Ox** 编译器选项，因为它结合了 **\/Ox** 编译器选项和 [\/Os（代码大小优先）](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)。  这些结合使用的选项有利于生成较小的代码大小。  
  
 通常，可指定 [\/O2（最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)来代替 **\/Ox**，指定 [\/O1（最小化大小）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)来代替 **\/Oxs**。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“优化”**属性页。  
  
4.  修改**“优化”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。  
  
## 请参阅  
 [\/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)