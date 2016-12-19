---
title: "语言关键字 (C++/CLI) | Microsoft Docs"
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
  - "关键字 [C++]"
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 语言关键字 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，有几个语言关键字已发生更改。  
  
 在新的 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 语法中，从所有关键字中移除了作为前缀的双下划线（有一个例外：仍保留 `__identifier`）。  例如，属性现在被声明为 `property`，而不是 `__property`。  
  
 在托管扩展中使用双下划线前缀，主要有两个原因：  
  
-   它是提供 ISO\-C\+\+ 标准的本地扩展的一致方法。  托管扩展设计的一个主要目标是不引入与标准语言不兼容的内容，例如新关键字和新标记。  从很大程度上说，正是这个原因，促成了对托管引用类型的对象的声明使用指针语法的选择。  
  
-   使用双下划线，除了它的一致性方面外，还可以合理地保证不会破坏语言用户的现有基本代码。  这是托管扩展设计的第二个主要目标。  
  
 尽管移除了双下划线，但 Microsoft 仍然会保证一致性。  但是，对 CLR 动态对象模型的支持代表一种新的功能强大的程序设计范例。  对此新设计规范的支持要求其自身要有高级别的关键字和标记。  在对新范例进行集成并支持标准语言的同时，我们在努力提供此新范例的一流表达式。  新的语法设计可为这两个完全不同的对象模型提供一流的程序设计体验。  
  
 同样，我们也关心尽可能提高这些新语言关键字的非侵害性。  这已通过使用上下文关键字和空格分隔的关键字来实现。  在了解实际的新语言语法之前，让我们先来搞清楚这两种特殊关键字的风格。  
  
 上下文关键字在特定的程序上下文中有特殊的含义。  例如，在常规程序内，将 `sealed` 视为普通标识符。  但是，当它出现在托管引用类类型的声明部分中时，将其视为该类声明的上下文中的关键字。  这会尽量减轻在语言中引入新关键字可能造成的侵害性影响，我们感觉这对具有现有基本代码的用户来说非常重要。  同时，它使得使用新功能的用户可以获得附加语言功能的一流体验 — 这正是托管扩展所缺少的。  有关如何使用 `sealed` 的示例，请参见[托管类类型的声明](../dotnet/declaration-of-a-managed-class-type.md)。  
  
 空格分隔的关键字（如 `value class`）是上下文关键字的一种特例。  它用由空格分隔的上下文修饰符对现有关键字配对。  对被视为一个单独的单元，而不是两个单独的关键字。  
  
## 请参阅  
 [C\+\+\/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)   
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)