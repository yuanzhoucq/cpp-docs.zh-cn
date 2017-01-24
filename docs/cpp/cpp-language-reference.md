---
title: "C++ 语言参考 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "index-page "
f1_keywords: 
  - "c++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++, 语言参考"
  - "语言参考"
  - "语言参考, Visual C++"
  - "Visual C++, 语言参考"
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 语言参考
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本参考将介绍在 Microsoft Visual C\+\+ 中实现的 C\+\+ 编程语言。  本文的结构基于 Margaret Ellis 和 Bjarne Stroustrup 撰写的《C\+\+ 参考手册注解》和 ANSI\/ISO C\+\+ 国际标准 \(ISO\/IEC FDIS 14882\)。  本文涵盖了 C\+\+ 语言功能的 Microsoft 专用实现。  
  
 请参阅下面的表以快速查找关键字或运算符：  
  
-   [C\+\+ 关键字](../cpp/keywords-cpp.md)  
  
-   [C\+\+ 运算符](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
  
## 本节内容  
 [词法约定](../cpp/lexical-conventions.md)  
 C\+\+ 程序的基本词法元素：标记、注释、运算符、关键字、标点符号、文本。  此外，还有文件转换、运算符优先级别\/关联性。  
  
 [基本概念](../cpp/basic-concepts-cpp.md)  
 范围、链接、程序启动和终止、存储类以及类型。  
  
 [标准转换](../cpp/standard-conversions.md)  
 内置类型或“基础”类型之间的类型转换。  此外，算术转换和指针、引用与成员指针类型之间的转换。  
  
 [运算符、优先级别和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
 C\+\+ 中的运算符。  
  
 [表达式](../cpp/expressions-cpp.md)  
 表达式的类型、表达式的语义、有关运算符的参考主题、强制转换和强制转换运算符、运行时类型信息。  
  
 [Lambda 表达式](../cpp/lambda-expressions-in-cpp.md)  
 隐式定义函数对象类和构造该类类型的函数对象的编程技术。  
  
 [语句](../cpp/statements-cpp.md)  
 表达式、null、复合、选择、迭代、跳转和声明语句。  
  
 [声明](../misc/declarations.md)  
 存储类说明符、函数定义、初始化、枚举、类、结构和联合声明以及 typedef 声明。  此外，还有内联函数、常量关键字、命名空间。  
  
 [声明符](http://msdn.microsoft.com/zh-cn/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838)  
 用于命名对象、类型或函数的声明语句的一部分。  抽象声明符、类型名称，初始值设定项、函数声明和定义、数组、引用。  
  
 [类、结构和联合](../cpp/classes-and-structs-cpp.md)  
 介绍类、结构和联合。  此外，还介绍成员函数、数据成员、位域、this 指针和嵌套类。  
  
 [派生类](../cpp/inheritance-cpp.md)  
 单一继承和多重继承、虚函数、多个基类、抽象类、范围规则。  此外，还有 \_\_super 和 \_\_interface 关键字。  
  
 [成员访问控制](../cpp/member-access-control-cpp.md)  
 控制对类成员的访问：public、private 和 protected 关键字。  友元函数和友元类。  
  
 [特殊成员函数](../misc/special-member-functions-cpp.md)  
 类类型独有的特殊函数：构造函数、析构函数、转换函数、赋值运算符、运算符新建函数和运算符删除函数。  
  
 [重载](../misc/overloading-cpp.md)  
 重载函数、声明匹配、参数匹配。  此外，还有重载运算符、运算符重载规则。  
  
 [异常处理](../cpp/exception-handling-in-visual-cpp.md)  
 C\+\+ 异常处理、结构化异常处理 \(SEH\)、编写异常处理语句所使用的关键字。  
  
 [断言和用户提供的消息](../cpp/assertion-and-user-supplied-messages-cpp.md)  
 `#error` 指令、`static_assert` 关键字、`assert` 宏。  
  
 [模板](../cpp/templates-cpp.md)  
 模板规范、函数模板、类模板、类型名称关键字、模板与  宏以及模板和智能指针。  
  
 [事件处理](../cpp/event-handling.md)  
 声明事件和事件处理程序。  
  
 [Microsoft 专用的修饰符](../cpp/microsoft-specific-modifiers.md)  
 Microsoft C\+\+ 专用修饰符。  内存寻址、调用约定、裸函数、扩展的存储类特性 \(\_\_declspec\)、\_\_w64。  
  
 [内联汇编程序](../assembler/inline/inline-assembler.md)  
 在 \_\_asm 块中使用汇编语言和 C\+\+。  
  
 [编译器 COM 支持](../cpp/compiler-com-support.md)  
 有关用于支持 COM 类型的 Microsoft 专用类和全局函数的参考。  
  
 [Microsoft 扩展](../cpp/microsoft-extensions.md)  
 Microsoft 的 C\+\+ 扩展。  
  
 [非标准行为](../cpp/nonstandard-behavior.md)  
 有关 Visual C\+\+ 编译器的非标准行为的信息。  
  
## 相关章节  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)  
 有关使用 Visual C\+\+ 来以公共语言运行时为目标的参考材料。  
  
 [C\/C\+\+ 生成参考](../build/reference/c-cpp-building-reference.md)  
 编译器选项、链接器选项和其他生成工具。  
  
 [C\/C\+\+ 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)  
 有关杂注、预处理器指令、预定义宏和预处理器的参考材料。  
  
 [Visual C\+\+ 库](http://msdn.microsoft.com/zh-cn/fec23c40-10c0-4857-9cdc-33a3b99b30ae)  
 指向各种 Visual C\+\+ 库的参考起始页的链接的列表。  
  
## 请参阅  
 [C 语言参考](../c-language/c-language-reference.md)