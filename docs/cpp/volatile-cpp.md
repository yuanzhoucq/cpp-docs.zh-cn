---
title: "易失性 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: volatile_cpp
dev_langs: C++
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
caps.latest.revision: "43"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 02560da98c583281cc05921f2e924a12f41688c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="volatile-c"></a>volatile (C++)
可用于声明可在程序中由硬件修改的对象的类型限定符。  
  
## <a name="syntax"></a>语法  
  
```  
  
volatile declarator ;  
```  
  
## <a name="remarks"></a>备注  
 你可以使用[/易失性](../build/reference/volatile-volatile-keyword-interpretation.md)编译器开关来修改编译器解释此关键字的方式。  
  
 Visual Studio 根据目标体系结构以不同的方式解释 `volatile` 关键字。 对于 ARM，如果没有**/易失性**指定编译器选项，编译器将执行就像**/volatile:iso**指定。 对于 ARM，如果没有之外的体系结构**/易失性**指定编译器选项，编译器将执行就像**/volatile: ms**指定; 因此，对于体系结构之外强 ARM 我们你指定的建议**/volatile:iso**，并在处理跨线程共享的内存时使用显式同步基元和编译器内部函数。  
  
 您可以使用 `volatile` 限定符来提供对异步过程（如中断处理程序）使用的内存位置的访问权。  
  
 当`volatile`还具有的变量上使用[__restrict](../cpp/extension-restrict.md)关键字，`volatile`优先。  
  
 如果将 `struct` 成员标记为 `volatile`，则 `volatile` 将传播到整个结构。 如果结构不具有可通过使用指令在当前体系结构上复制的长度，则该结构上可能完全丢失 `volatile`。  
  
 如果满足下列条件之一，则 `volatile` 关键字可能对字段不起作用：  
  
-   可变字段的长度超过可使用一条指令在当前体系结构上复制的最大大小。  
  
-   最外层包含 `struct` 的长度 - 或如果它是可能嵌套的 `struct` 的成员 - 超过可使用一条指令在当前体系结构上复制的最大大小。  
  
 尽管处理器不会对不可缓存的内存访问重新排序，但必须将不可缓存的变量标记为 `volatile` 以保证此编译器不会对内存访问重新排序。  
  
 对象声明为`volatile`由于其值可以更改在任何时间不使用中的某些优化。  系统始终读取可变对象的当前值所请求，即使以前的指令要求从同一对象的值。  此外，在分配上立即写入对象的值。  
  
## <a name="iso-compliant"></a>符合 ISO  
 如果您是熟悉 C# volatile 关键字，或熟悉的行为`volatile`在 Visual c + + 的早期版本，请注意，C + + 11 ISO 标准`volatile`关键字是不同，在 Visual Studio 中支持时[/易失性： iso](../build/reference/volatile-volatile-keyword-interpretation.md)指定编译器选项。 （对于 ARM，默认情况下将指定它。） C++11 ISO 标准代码中的 `volatile` 关键字仅用于硬件访问；请不要将其用于线程间通信。 对于线程间通信使用机制例如[std::atomic\<T >](../standard-library/atomic.md)从[c + + 标准库](../standard-library/cpp-standard-library-reference.md)。  
  
## <a name="end-of-iso-compliant"></a>符合 ISO 的末尾  
  
## <a name="microsoft-specific"></a>Microsoft 专用  
 当**/volatile: ms**使用编译器选项时-默认情况下，在面向 ARM 之外的体系结构时-编译器会生成额外代码来维护对可变对象还维护的引用之间的排序对其他全局对象的引用的排序。 具体而言：  
  
-   对可变对象进行写入（也称为可变编写）具有“发布”语义；也就是说，对指令序列中的可变对象进行写入之前发生的全局或静态对象的引用将在已编译的库中写入可变对象之前发生。  
  
-   对可变对象进行读取（也称为可变读取）具有“获取”语义；也就是说，对指令序列中的可变对象进行读取之前发生的全局或静态对象的引用将在已编译的库中读取可变对象之前发生。  
  
 这使可变对象要用于内存锁和多线程应用程序中的版本。  
  
> [!NOTE]
>  当它依赖于具有时提供的增强保证**/volatile: ms**编译器选项时，代码是不可移植。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [const](../cpp/const-cpp.md)   
 [固定和可变指针](../cpp/const-and-volatile-pointers.md)