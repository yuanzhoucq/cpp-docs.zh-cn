---
title: "volatile (C++) | Microsoft Docs"
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
  - "volatile_cpp"
  - "volatile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "中断处理程序和 volatile 关键字"
  - "对象 [C++], volatile"
  - "volatile 关键字 [C++]"
  - "可变对象"
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
caps.latest.revision: 43
caps.handback.revision: 43
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# volatile (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用声明的类型限定符对象在程序中用硬件修改。  
  
## 语法  
  
```  
  
volatile declarator ;  
```  
  
## 备注  
 可以使用 [\/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) 编译器开关修改编译器如何解释此关键字。  
  
 Visual Studio 基于目标结构的不同说明 `volatile` 关键字。  对于ARM，如果 **\/volatile** 未指定编译器选项，编译器执行就把 **\/volatile:iso** 指定了。  除了 ARM 之外的体系结构，如果 **\/volatile** 未指定编译器选项，编译器执行就把 **\/volatile:ms** 指定的；因此，除了 ARM 之外，在处理在线程之间共享的内存时，为了体系结构强烈建议指定 **\/volatile:iso**，然后使用显式同步基元和编译器内部。  
  
 使用 `volatile` 限定符的用途之一是提供由异步进程使用内存位置，例如中断处理程序。  
  
 当 `volatile` 上使用变量时，也有[\_\_restrict](../cpp/extension-restrict.md) 关键字，  `volatile` 优先。  
  
 如果 `struct` 成员标记为 `volatile`，那么 `volatile` 会传播到所有的结构。  如果结构没有能够通过使用一个指令就被复制到当前体系结构的长度， `volatile` 在该结构上可能完全丢失。  
  
 如果满足以下条件之一，`volatile` 关键字可能不会对字段的效果：  
  
-   当可变字段的长度超过最大值时，可以用命令来拷贝当前的结构。  
  
-   最外面的包含 `struct`的长度 \(或可以嵌套 `struct`的成员\) ，超过最大值时可以通过命令来拷贝当前的结构。  
  
 尽管该处理器不重新排序非缓存内存存取，必须标记为不可缓存变量为指向保护的 `volatile` 编译器不重新排序内存存取。  
  
 已声明为 `volatile` 的对象不使用某些优化，因为它们的值可以随时更改。当被请求时系统始终读取不稳定对象的当前值，当请求时，即使前面的指令请求同一对象中的值。此外，立即编写该对象的值到赋值。  
  
## ISO\-compliant — 符合 ISO  
 如果您熟悉 [C\# volatile](../Topic/volatile%20\(C%23%20Reference\).md) 关键字或熟悉在 Visual C\+\+ 早期版本中 `volatile` 行为，请注意 C\+\+11 ISO 标准 `volatile` 关键字是不同的，当 [\/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) 编译器选项指定时 Visual Studio 是支持的。默认情况下 \(对于 ARM，它指定了\)。  在 C\+\+11 ISO 标准代码的 `volatile` 关键字是仅为硬件提供访问的，不要在内部线程间的通信使用它。  对于内部线程间的通信，请使用机制 ，例如 [C\+\+ 标准模板库](../standard-library/cpp-standard-library-reference.md)的 [std::atomic\<T\>](../standard-library/atomic.md)。  
  
## 符合 ISO 结束  
  
## Microsoft 专用  
 当 **\/volatile:ms** 编译器选项被使用时，默认值是体系结构目标而不是ARM，编译器生成额外的代码维护排序在对变量的对象的引用中，和维护的排序之外到其他全局对象的引用。  具体而言：  
  
-   编写可变对象（也叫编写的变量）具有”发布“语义；即，在编写编译二进制中的变量前，编写指令序列中的变量对象前全局或静态对象的引用将发生。  
  
-   读取可变对象（也叫读取的变量）具有”获取“语义；即，在读取编译二进制中的变量后，读取指令序列中的变量后内存全局态对象的引用将发生。  
  
 这使得可变对象能够被记忆锁使用，并且在多线程应用程序中释放。  
  
> [!NOTE]
>  当它依赖于提供增强的安全保护时，使用 **\/volatile:ms** 编译器选项时，代码是不可移植的。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [const](../cpp/const-cpp.md)   
 [固定和可变指针](../cpp/const-and-volatile-pointers.md)