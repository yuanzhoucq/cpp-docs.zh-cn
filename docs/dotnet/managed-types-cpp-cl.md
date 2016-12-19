---
title: "托管类型 (C++/CL) | Microsoft Docs"
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
  - "__gc 类型"
  - "类型 [C++], CLR"
ms.assetid: 1ddd114e-be02-4de7-a4dd-a2d72ad8ff81
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 托管类型 (C++/CL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，托管类型的声明的语法和这些类型的对象的创建与使用发生了明显的更改。  这样可以提升它们在 ISO\-C\+\+ 类型系统内的集成。  在下列子节中详细介绍这些更改。  
  
## 本节内容  
 [托管类类型的声明](../dotnet/declaration-of-a-managed-class-type.md)  
 讨论如何声明托管 `class`、`struct` 或 `interface`。  
  
 [CLR 引用类对象的声明](../dotnet/declaration-of-a-clr-reference-class-object.md)  
 讨论如何使用跟踪句柄声明引用类类型对象。  
  
 [CLR 数组的声明](../dotnet/declaration-of-a-clr-array.md)  
 解释如何声明和初始化数组。  
  
 [以构造函数初始化顺序进行更改](../dotnet/changes-in-constructor-initialization-order.md)  
 讨论类构造函数初始化顺序中的重要变化。  
  
 [析构函数语义的更改](../dotnet/changes-in-destructor-semantics.md)  
 讨论非确定终止（`Finalize` 与 `Dispose`）、引用对象的后果和显式 `Finalize` 的使用。  
  
 **注意：**为了将委托与类中的事件成员一起在 [类或接口中的成员声明 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md) 的常规主题中进行说明，对委托的讨论已推迟到 [委托和事件](../dotnet/delegates-and-events.md)。  
  
## 请参阅  
 [C\+\+\/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)   
 [类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md)   
 [数组](../windows/arrays-cpp-component-extensions.md)