---
title: C++ 语言参考 |Microsoft 文档
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- language reference
- C++, language reference
- language reference, Visual C++
- Visual C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25315121d3004601914c5b8872b496e57acec99f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="c-language-reference"></a>C++ 语言参考
本参考将介绍在 Microsoft Visual C++ 中实现的 C++ 编程语言。 基于组织*C++ 参考手册批注 》* Margaret Ellis 和 Bjarne stroustrup 撰写和 ANSI/ISO C++ 国际标准 (ISO/IEC FDIS 14882)。 本文涵盖了 C++ 语言功能的 Microsoft 专用实现。  

有关现代 C++ 编程做法的概述，请参阅[欢迎回到 C++](welcome-back-to-cpp-modern-cpp.md)。
  
 请参阅下面的表以快速查找关键字或运算符：  
  
-   [C++ 关键字](../cpp/keywords-cpp.md)  
  
-   [C++ 运算符](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
  
## <a name="in-this-section"></a>本节内容  

 [词法约定](../cpp/lexical-conventions.md)  
 C++ 程序的基本词法元素：标记、注释、运算符、关键字、标点符号、文本。 此外，还有文件转换、运算符优先级别/关联性。  
  
 [基本概念](../cpp/basic-concepts-cpp.md)  
 范围、链接、程序启动和终止、存储类以及类型。  
  
 [标准转换](../cpp/standard-conversions.md)  
 内置类型或“基础”类型之间的类型转换。 此外，算术转换和指针、引用与成员指针类型之间的转换。  
  
 [运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
 C++ 中的运算符。  
  
 [表达式](../cpp/expressions-cpp.md)  
 表达式的类型、表达式的语义、有关运算符的参考主题、强制转换和强制转换运算符、运行时类型信息。  
  
 [Lambda 表达式](../cpp/lambda-expressions-in-cpp.md)  
 隐式定义函数对象类和构造该类类型的函数对象的编程技术。  
  
 [语句](../cpp/statements-cpp.md)  
 表达式、null、复合、选择、迭代、跳转和声明语句。  
  
 [声明和定义](declarations-and-definitions-cpp.md)  
 存储类说明符、函数定义、初始化、枚举、类、结构和联合声明以及 typedef 声明。 此外，还有内联函数、常量关键字、命名空间。  
  
 [声明符](http://msdn.microsoft.com/en-us/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838)  
 用于命名对象、类型或函数的声明语句的一部分。 抽象声明符、类型名称，初始值设定项、函数声明和定义、数组、引用。  
  
 [类、 结构和联合](../cpp/classes-and-structs-cpp.md)  
 介绍类、结构和联合。 此外，成员函数、 特殊成员函数、 数据成员、 位域、 this 指针和嵌套的类。  
  
 [派生的类](../cpp/inheritance-cpp.md)  
 单一继承和多重继承、虚函数、多个基类、抽象类、范围规则。 此外，还有 __super 和\__interface 关键字。  
  
 [成员访问控制](../cpp/member-access-control-cpp.md)  
 控制对类成员的访问：public、private 和 protected 关键字。 友元函数和友元类。  
  
 [重载](operator-overloading.md)  
 重载的运算符，运算符重载的规则。  
  
 [异常处理](../cpp/exception-handling-in-visual-cpp.md)  
 C++ 异常处理、结构化异常处理 (SEH)、编写异常处理语句所使用的关键字。  
  
 [断言和用户提供的消息](../cpp/assertion-and-user-supplied-messages-cpp.md)  
 `#error` 指令、`static_assert` 关键字、`assert` 宏。  
  
 [模板](../cpp/templates-cpp.md)  
 模板规范、函数模板、类模板、类型名称关键字、模板与宏、模板和智能指针。  
  
 [事件处理](../cpp/event-handling.md)  
 声明事件和事件处理程序。  
  
 [Microsoft 专用的修饰符](../cpp/microsoft-specific-modifiers.md)  
 Microsoft C++ 专用修饰符。 内存寻址、 调用约定、 裸函数、 扩展存储类特性 (__declspec)、 \__w64。  
  
 [内联汇编程序](../assembler/inline/inline-assembler.md)  
 在 __asm 块中使用汇编语言和 C++。  
  
 [编译器 COM 支持](../cpp/compiler-com-support.md)  
 有关用于支持 COM 类型的 Microsoft 专用类和全局函数的参考。  
  
 [Microsoft 扩展](../cpp/microsoft-extensions.md)  
 Microsoft 的 C++ 扩展。  
  
 [非标准行为](../cpp/nonstandard-behavior.md)  
 有关 Visual C++ 编译器的非标准行为的信息。  

 [欢迎回到 C++](welcome-back-to-cpp-modern-cpp.md)用于编写安全、 正确且高效程序做法现代 C++ 编程的概述。
  
## <a name="related-sections"></a>相关章节  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)  
 有关使用 Visual C++ 来以公共语言运行时为目标的参考材料。  
  
 [C/C++ 生成参考](../build/reference/c-cpp-building-reference.md)  
 编译器选项、链接器选项和其他生成工具。  
  
 [C/C++ 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)  
 有关杂注、预处理器指令、预定义宏和预处理器的参考材料。  
  
 [Visual C++ 库](../standard-library/cpp-standard-library-reference.md)  
 指向各种 Visual C++ 库的参考起始页的链接的列表。  
  
## <a name="see-also"></a>请参阅  
 [C 语言参考](../c-language/c-language-reference.md)