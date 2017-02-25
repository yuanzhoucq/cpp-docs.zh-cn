---
title: "C 扩展的存储类特性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C]"
  - "扩展特性"
  - "扩展的存储类特性"
  - "存储类说明符, C 存储类"
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# C 扩展的存储类特性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 有关本主题的更多最新信息可以在 [\_\_declspec（C\+\+ 参考）](../cpp/declspec.md)下找到。  
  
 扩展的特性语法简化并标准化了特定于 Microsoft 的 C 语言扩展。  使用扩展的特性语法的存储类特性包括 thread、naked、dllimport 和 dllexport。  
  
 用于指定存储类信息的扩展特性语法使用 \_\_declspec 关键字，这指定给定类型的实例将与特定于 Microsoft 的存储类特性（thread、naked、dllimport 或 dllexport）一起存储。  其他存储类修饰符的示例包括 static 和 extern 关键字。  但是，这些关键字是 ANSI C 标准的一部分，因此未涵盖在扩展的特性语法中。  
  
## 语法  
 *storage\-class\-specifier*:  
 `__declspec` \( *extended\-decl\-modifier\-seq* \) \/\* Microsoft 专用 \*\/  
  
 *extended\-decl\-modifier\-seq*:  
 *extended\-decl\-modifier*  opt  
  
 *extended\-decl\-modifier\-seq extended\-decl\-modifier*  
  
 *extended\-decl\-modifier*:  
 **thread**  
  
 **naked**  
  
 **dllimport**  
  
 `dllexport`  
  
 空格可分隔声明修饰符。  请注意，*extended\-decl\-modifier\-seq* 可以为空：在此情况下，\_\_declspec 不起作用。  
  
 thread、naked、dllimport 和 dllexport 存储类特性仅为它们应用于的数据或函数的声明的属性；它们不重新定义函数自身的类型特性。  thread 特性只影响数据。  naked 特性仅影响函数。  dllimport 和 dllexport 特性影响函数和数据。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [声明和类型](../c-language/declarations-and-types.md)