---
title: volatile (C++)
ms.date: 05/07/2019
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: 841b2e1e4ffbec87a170c45be8ad0cd0f831a0ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371903"
---
# <a name="volatile-c"></a>volatile (C++)

可用于声明可在程序中由硬件修改的对象的类型限定符。

## <a name="syntax"></a>语法

```
volatile declarator ;
```

## <a name="remarks"></a>备注

可以使用[/volatile](../build/reference/volatile-volatile-keyword-interpretation.md)编译器开关修改编译器解释此关键字的方式。

Visual Studio 根据目标体系结构的不同对**易失性**关键字的解释不同。 对于 ARM，如果未指定 **/易失性**编译器选项，编译器将执行，就像指定**了 /volatile：iso 一**样。 对于 ARM 以外的体系结构，如果未指定 **/易失性**编译器选项，编译器将执行，就像指定**了 /volatile：ms;** 因此，对于 ARM 以外的体系结构，我们强烈建议您指定 **/volatile：iso**，并在处理跨线程共享的内存时使用显式同步基元和编译器内部函数。

可以使用**易失性**限定符提供对异步进程（如中断处理程序）使用的内存位置的访问。

当在也具有[__restrict](../cpp/extension-restrict.md)关键字的变量上使用**易失性**时，**易失性**优先。

如果**结构**成员标记为**易失性**，则**挥发性**将传播到整个结构。 如果结构的长度不能使用一个指令在当前体系结构上复制，则该结构上可能会完全失去**易失性**。

如果以下条件之一为 true，**则 volatile**关键字可能对字段没有影响：

- 可变字段的长度超过可使用一条指令在当前体系结构上复制的最大大小。

- 最外层包含**结构**的长度（或者如果它是可能嵌套**结构**的成员）超过了使用一个指令可在当前体系结构上复制的最大大小。

尽管处理器不重新排序不可缓存的内存访问，但不可缓存的变量必须标记为**易失性**，以确保编译器不会重新排序内存访问。

在某些优化中，声明为**易失性**的对象不会使用，因为它们的值可以随时更改。  系统始终在请求易失性对象时读取该对象的当前值，即使以前的指令要求从同一对象中提供值也是如此。  此外，对象的值在赋值时立即写入。

## <a name="iso-compliant"></a>符合 ISO

如果您熟悉 C# 易失性关键字，或者熟悉早期版本中的 Microsoft C++ 编译器 （MSVC） 中的**易失性**行为，请注意，C++11 ISO 标准**易失性**关键字不同，在指定[/volatile：iso](../build/reference/volatile-volatile-keyword-interpretation.md)编译器选项时，MSVC 中支持该关键字。 （对于 ARM，默认情况下将指定它。） C++11 ISO 标准代码中的**易失性**关键字仅用于硬件访问;不要将其用于线程间通信。 对于线程间通信，请使用[C++标准库中](../standard-library/cpp-standard-library-reference.md)的[\<std：atomic T>](../standard-library/atomic.md)等机制。

## <a name="end-of-iso-compliant"></a>符合 ISO 的末尾

**微软特定**

当使用 **/volatile：ms**编译器选项时（默认情况下，当 ARM 以外的体系结构被定位时）编译器生成额外的代码，以保持对易失性对象的引用之间的排序，此外还保持对其他全局对象的引用的排序。 具体而言：

- 对可变对象进行写入（也称为可变编写）具有“发布”语义；也就是说，对指令序列中的可变对象进行写入之前发生的全局或静态对象的引用将在已编译的库中写入可变对象之前发生。

- 对可变对象进行读取（也称为可变读取）具有“获取”语义；也就是说，对指令序列中的可变对象进行读取之前发生的全局或静态对象的引用将在已编译的库中读取可变对象之前发生。

这使得易失性对象可用于多线程应用程序中的内存锁和释放。

> [!NOTE]
> 当它依赖于使用 **/volatile：ms**编译器选项时提供的增强保证时，代码是不可移植的。

**结束微软特定**

## <a name="see-also"></a>另请参阅

[Keywords](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[固定和可变指针](../cpp/const-and-volatile-pointers.md)
