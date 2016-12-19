---
title: "/Qpar-report（自动并行化程序报告等级） | Microsoft Docs"
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
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qpar-report（自动并行化程序报告等级）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

启用编译器的[自动并行化](../../parallel/auto-parallelization-and-auto-vectorization.md)的报告功能，并在编译期间指定输出的提供相关信息的消息级别。  
  
## 语法  
  
```  
/Qpar-report:{1}{2}  
```  
  
## 备注  
 **\/Qpar\-report:1**  
 为并行化的循环输出提供相关信息的消息。  
  
 **\/Qpar\-report:2**  
 为并行化的循环和未并行化的循环输出提供相关信息的消息以及原因代码。  
  
 消息报告为 stdout。  如果未报告任何提供相关信息的消息，则该代码不包含任何循环，或者报告级别未设置为报告未并行化的循环。  有关原因代码和消息的详细信息，请参阅 [矢量化程序和并行化程序消息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。  
  
### 在 Visual Studio 中设置 \/Qpar\-report 编译器选项  
  
1.  在“解决方案资源管理器”中，打开项目的快捷菜单，然后选择“属性”。  
  
2.  在“属性页”对话框中的“C\/C\+\+”下，选择“命令行”。  
  
3.  在“附加选项”中，输入 `/Qpar-report:1` 或 `/Qpar-report:2`。  
  
### 以编程方式设置 \/Qpar\-report 编译器选项  
  
-   使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的代码示例。  
  
## 请参阅  
 [\/Q 选项（低级别操作）](../../build/reference/q-options-low-level-operations.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [“本机代码中的并行编程”](http://go.microsoft.com/fwlink/?LinkId=263662)