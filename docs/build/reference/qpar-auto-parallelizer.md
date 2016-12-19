---
title: "/Qpar（自动并行化程序） | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration"
dev_langs: 
  - "C++"
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qpar（自动并行化程序）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使编译器的 [Auto\-Parallelizer](../../parallel/auto-parallelization-and-auto-vectorization.md) 功能会自动并行化代码中的循环。  
  
## 语法  
  
```  
/Qpar  
```  
  
## 备注  
 当编译器自动对循环进行并行化代码，它在多个处理器内核之间分布的计算。  循环并行化仅当编译器确定它是以合法的方式执行，并且并行化会提高性能。  
  
 `#pragma loop()` 指令可帮助您优化程序并行化的循环。  有关详细信息，请参阅[循环](../../preprocessor/loop.md)。  
  
 有关如何启用"自动 parallelizer 的输出消息的信息，请参见 [\/Qpar\-report（自动并行化程序报告等级）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)。  
  
### 若要在 Visual Studio 中设置\/Qpar 编译器选项  
  
1.  在**“解决方案资源管理器”**中，打开项目的快捷菜单，然后选择**“属性”**。  
  
2.  在 属性页 对话框中，在 C\/C\+\+下，选择命令行。  
  
3.  在 附加选项 框中，输入 `/Qpar`。  
  
### 以编程方式设置 \/Qpar 编译器选项  
  
-   （请使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的代码实例。）  
  
## 请参阅  
 [\/Q 选项（低级别操作）](../../build/reference/q-options-low-level-operations.md)   
 [\/Qpar\-report（自动并行化程序报告等级）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [\#pragma loop\(\)](../../preprocessor/loop.md)   
 [本机代码中的并行编程](http://go.microsoft.com/fwlink/?LinkId=263662)