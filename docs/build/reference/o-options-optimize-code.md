---
title: "/O 选项（优化代码） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.Optimization"
  - "/o"
  - "VC.Project.VCCLWCECompilerTool.Optimization"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器, 性能"
  - "性能, cle.exe 编译器"
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /O 选项（优化代码）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/O** 选项控制有助于创建具有最高速度或最小大小的代码的各种优化。  
  
-   [\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 为获得最小大小而优化代码。  
  
-   [\/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 为获得最高速度而优化代码。  
  
-   [\/Ob](../../build/reference/ob-inline-function-expansion.md) 控制内联函数展开。  
  
-   [\/Od](../../build/reference/od-disable-debug.md) 禁用优化，从而加快编译并简化调试。  
  
-   [\/Og](../../build/reference/og-global-optimizations.md) 启用全局优化。  
  
-   [\/Oi](../../build/reference/oi-generate-intrinsic-functions.md) 为适当的函数调用生成内部函数。  
  
-   [\/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) 通知编译器优选大小优化而非速度优化。  
  
-   [\/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)（默认设置）通知编译器优选速度优化而非大小优化。  
  
-   [\/Ox](../../build/reference/ox-full-optimization.md) 选择完全优化。  
  
-   [\/Oy](../../build/reference/oy-frame-pointer-omission.md) 取消在调用堆栈上创建框架指针，以更快地进行函数调用。  
  
## 备注  
 还可以将多个 **\/O** 选项组合到一个选项语句。  例如，`/Odi` 与 `/Od /Oi` 是相同的。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)