---
title: "/Qvec-report（自动矢量化程序报告等级） | Microsoft Docs"
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
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qvec-report（自动矢量化程序报告等级）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

启用编译器 [自动 Vectorizer](../../parallel/auto-parallelization-and-auto-vectorization.md) 的报告功能并为输出指定级别信息性消息在编译过程。  
  
## 语法  
  
```  
/Qvec-report:{1}{2}  
```  
  
## 备注  
 **\/Qvec\-report:1**  
 输出向量化的循环一个信息性消息。  
  
 **\/Qvec\-report:2**  
 与原因代码一起存放输出一个信息性消息向量化循环的和不向量化的循环。  
  
 有关原因代码和信息的详细信息，请参阅 [矢量化程序和并行化程序消息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。  
  
### 在 Visual Studio 中设置 \/Qvec\-report 编译器选项  
  
1.  在**“解决方案资源管理器”**中，打开项目的快捷菜单，然后选择**“属性”**。  
  
2.  在 属性页 对话框中，在 C\/C\+\+下，选择命令行。  
  
3.  在 **附加选项** 框中，输入 `/Qvec-report:1` 或 `/Qvec-report:2`。  
  
### 以编程方式设置 \/Qvec\-report 编译器选项  
  
-   （请使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的代码实例。）  
  
## 请参阅  
 [\/Q 选项（低级别操作）](../../build/reference/q-options-low-level-operations.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [本机代码的并行编程](http://go.microsoft.com/fwlink/?LinkId=263662)