---
title: "源文件和源程序 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "文件 [C++], source"
  - "程序 [C++], source"
  - "源文件, 在编译器中指定"
  - "源程序"
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 源文件和源程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

源程序可以分为一个或多个“源文件”或“翻译单元”。编译器的输入称为“翻译单元”。  
  
## 语法  
 *translation\-unit*:  
 *external\-declaration*  
  
 *translation\-unit external\-declaration*  
  
 *external\-declaration*:  
 *function\-definition*  
  
 *declaration*  
  
 [声明概述](../c-language/overview-of-declarations.md)提供了 `declaration` 非终止符的语法，并且《预处理器参考》解释了[翻译单元](../preprocessor/phases-of-translation.md)的处理方式。  
  
> [!NOTE]
>  有关 ANSI 语法约定的说明，请参阅 [C 语言语法摘要](../c-language/c-language-syntax-summary.md)的简介。  
  
 翻译单元的组件是包括函数定义和标识符声明的外部声明。  这些声明和定义可以位于源文件、头文件、库和程序需要的其他文件中。  必须编译每个翻译单元，并将生成的对象文件链接起来以生成程序。  
  
 A C“源程序”是指令、杂注、声明、定义、语句块和函数的集合。  若要成为 Microsoft C 程序的有效组件，每个组件必须具有本书中描述的语法，但它们可以按照程序中的任何顺序显示（受本书中概述的规则的限制）。  但是，这些组件在程序中的位置会影响变量和函数在程序中的使用方式。（有关详细信息，请参阅[生存期、范围、可见性和链接](../c-language/lifetime-scope-visibility-and-linkage.md)。\)  
  
 源文件无需包含可执行语句。  例如，您可能发现将变量的定义放置在一个源文件中，然后在使用这些变量的其他源文件中声明对这些变量的引用会很有用。  必要时，可通过此方法轻松查找和更新定义。  由于相同的原因，常量和宏通常会被归类为称为“包含文件”或“头文件”的独立文件中，可在源文件中将这些文件引用为所需文件。  有关[宏](../preprocessor/macros-c-cpp.md)和[包含文件](../preprocessor/hash-include-directive-c-cpp.md)的详细信息，请参阅《预处理器参考》。  
  
## 请参阅  
 [程序结构](../c-language/program-structure.md)