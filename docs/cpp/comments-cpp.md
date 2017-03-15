---
title: "C++ 注释 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "代码注释, C++"
  - "注释, C++ 代码"
  - "注释, 编制代码文档"
  - "空白, C++ 注释"
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 注释
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

注释是编译器忽略但对程序员有用的文本。  注释通常用于供将来的引用的说明编码。  该编译器将它们视为空白。  在测试中，可以使用注释让特定代码行处于非活动状态；但是 `#if`\/`#endif` 预处理器指令会因此更好地进行工作，因为您可以包围包含注释但不能嵌套注释的代码。  
  
 A C\+\+ 注释以下列方式之一进行编写：  
  
-   `/*` （斜杠、星号） 字符，其后跟任何字符 \(包括新行） 的序列，其后跟 `*/` 字符。  此语法与 ANSI C 相同。  
  
-   `//` \(两斜杠\) 字符，其后跟字符的任何序列。  如果新的行前面没有立即放入反斜杠，则该行终止注释的此窗体。  因此，它通常称为“单行注释”。  
  
 注释字符（`/*`、`*/` 和 `//`）在字符串末尾、字符串或注释中没有特殊含义。  注释使用第一个语法，因此不能套入。  
  
## 请参阅  
 [词法约定](../cpp/lexical-conventions.md)