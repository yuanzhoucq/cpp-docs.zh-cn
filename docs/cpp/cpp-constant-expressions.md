---
title: "C++ 常量表达式 | Microsoft Docs"
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
  - "常量表达式"
  - "常量表达式, 语法"
  - "表达式 [C++], 常量"
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 常量表达式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*常量*值是指不会更改的值。  C \+ \+ 提供了两个关键字，它们使你能够表达不打算修改对象的意图，还可让你实现该意图。  
  
 C\+\+ 需要常量表达式（计算结果为常量的表达式）以便声明：  
  
-   数组边界  
  
-   case 语句中的选择器  
  
-   位域长度规范  
  
-   枚举初始值设定项  
  
 常量表达式中合法的唯一操作数是：  
  
-   文本  
  
-   枚举常量  
  
-   声明为使用常量表达式初始化的常量的值  
  
-   `sizeof` 表达式  
  
 必须将非整型常量（显式或隐式）转换为常量表达式中合法的整型。  因此，以下代码是合法的：  
  
```  
const double Size = 11.0;  
char chArray[(int)Size];  
```  
  
 到整型的显式转换在常量表达式中是合法的；所有其他类型和派生类型是非法的（在用作 `sizeof` 运算符的操作数时除外）。  
  
 逗号运算符和赋值运算符不能用于常量表达式。  
  
## 请参阅  
 [表达式的类型](../cpp/types-of-expressions.md)