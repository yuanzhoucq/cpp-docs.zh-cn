---
title: "auto 关键字 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "auto"
  - "auto_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto 关键字"
  - "自动存储类, auto 关键字"
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto 关键字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`auto` 关键字是声明说明符。  但是，C\+\+ 标准为此关键字定义了初始和修订的含义。  在 [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)] 之前，`auto` 关键字在自动存储类中声明变量；即，具有局部生存期的变量。  从 [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)] 开始，`auto` 关键字声明其类型从其声明中的初始化表达式推导出的变量。  [\/Zc:auto&#91;\-&#93;](../build/reference/zc-auto-deduce-variable-type.md) 编译器选项控制 `auto` 关键字的意义。  
  
## 语法  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## 备注  
 `auto` 关键字的定义在 C\+\+ 编程语言中更改，但在 C 编程语言中未更改。  
  
 下列主题描述 `auto` 关键字和对应的编译器选项：  
  
-   [auto](../cpp/auto-cpp.md)描述了 `auto` 关键字的新定义。  
  
-   [auto 关键字（存储类说明符）](http://msdn.microsoft.com/zh-cn/c7d0cecf-393d-4058-a6e6-b39e31d9edb0)描述了 `auto` 关键字的原始定义。  
  
-   [\/Zc:auto（推导变量类型）](../build/reference/zc-auto-deduce-variable-type.md)描述了告知编译器要使用 `auto` 关键字的哪一定义的编译器选项。  
  
## 请参阅  
 [\(NOTINBUILD\)Storage\-Class Specifiers](http://msdn.microsoft.com/zh-cn/10b3d22d-cb40-450b-994b-08cf9a211b6c)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)