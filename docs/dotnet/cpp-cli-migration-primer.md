---
title: "C++/CLI 迁移入门 | Microsoft Docs"
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
helpviewer_keywords: 
  - "C++/CLI 版本 2"
  - "C++/CLI 版本 2, 托管扩展"
  - "C++ 托管扩展, 升级语法"
  - "迁移 [C++], C++/CLI 版本 2"
  - "升级 Visual C++ 应用程序, 将 C++ 托管扩展到 Visual C++ 2005 语法"
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++/CLI 迁移入门
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这是将 Visual C\+\+ 程序从 C\+\+ 托管扩展迁移到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 的指南。  关于语法更改的检查表摘要，请参见 [\(NOTINBUILD\)Managed Extensions for C\+\+ Syntax Upgrade Checklist](http://msdn.microsoft.com/zh-cn/edbded88-7ef3-4757-bd9d-b8f48ac2aada)。  
  
 C\+\+\/CLI 将动态组件编程范例扩展到 ISO\-C\+\+ 标准语言。  新语言为托管扩展提供了许多重要改进。  本节提供了 C\+\+ 托管扩展语言功能和它们到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 的映射（如果存在这样的映射）的枚举列表，并指出了不存在映射的结构。  
  
## 本节内容  
 [更改概要 \(C\+\+\/CLI\)](../dotnet/outline-of-changes-cpp-cli.md)  
 一个用于快速参考的高级大纲，提供了五个常规类别下的更改的列表。  
  
 [语言关键字 \(C\+\+\/CLI\)](../dotnet/language-keywords-cpp-cli.md)  
 讨论语言关键字的变化，包括删除双下划线以及引入上下文关键字和空格分隔的关键字。  
  
 [托管类型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)  
 查看常规类型系统 \(CTS\) 的声明中的语法更改 — 这包括类、数组（包括参数数组）、枚举等的声明中的更改。  
  
 [类或接口中的成员声明 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)  
 显示涉及类成员（如标量属性、索引属性、运算符、委托和事件）的更改。  
  
 [值类型及其行为 \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 重点讨论值类型以及内部指针和钉住指针的新系列。  还讨论若干重大语义更改，例如隐式装箱的引入、装箱的值类型的不变性，以及对值类内部的默认构造函数的支持的移除。  
  
 [常规语言更改](../dotnet/general-language-changes-cpp-cli.md)  
 详细讨论诸如对强制转换表示法、字符串行为的支持等语义的更改，以及 ISO\-C\+\+ 和 C\+\+\/CLI 之间的语义更改。  
  
## 请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)   
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)