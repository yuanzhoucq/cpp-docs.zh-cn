---
title: 程序和链接 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 04/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9998e7ad9605d6d2e32bcaff6204fb09dcbca2a5
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405553"
---
# <a name="program-and-linkage-c"></a>程序和链接 (C++)

在 c + + 程序中，*符号*，例如变量或函数名称，可以声明为任意数量的内，其作用域内，但它只能定义一次。 这是一个定义规则 (ODR)。 一个*声明*引入了 （或重新引入） 到该程序的名称。 一个*定义*引入了一个名称，并在一个变量的情况下显式初始化它。 一个*函数定义*包括签名以及函数体。

以下是声明：

```cpp
int i;
int f(int x);
```

这些是定义：

```cpp
int i{42};
int f(int x){ return x * i; }
```

程序包括一个或多个*翻译单元*。 翻译单元包含实现文件 （.cpp、.cxx 等） 和所有标头 （.h、.hpp 等），它包括直接或间接。 每个翻译单元单独编译的编译器，其后链接器将已编译的翻译单元合并到单个*程序*。 ODR 规则冲突的情况通常显示为链接器错误时相同的名称不同的翻译单元中具有两个不同的定义。

一般情况下，使变量跨多个文件中可见的最好办法是将其放入标头文件并添加 #include 指令需要声明每个.cpp 文件中。 通过添加*include 防护*围绕标头内容，确保仅一次定义它声明了名称。

但是，在某些情况下可能需要声明全局变量或.cpp 文件中的类。 在这些情况下，您需要一种方法来告诉编译器和链接器应用只需对一个文件或所有文件的对象的名称。

## <a name="linkage-vs-scope"></a>与作用域的链接

这一概念*链接*在翻译单元是指全局符号 （如变量、 类型名称和函数名称） 在程序中作为一个整体的可见性。 这一概念*作用域*指的是如命名空间、 类或函数体块中声明的符号。 此类符号是仅在其中定义它们; 范围内可见链接的概念不适用于它们。 

## <a name="external-vs-internal-linkage"></a>外部与内部链接

一个*自由函数*是一个函数，定义在全局或命名空间范围。 非常量全局变量和自由函数默认情况下具有*外部链接*; 它们是在程序中任何翻译单元中可见。 因此，没有任何其他全局对象 （变量、 类定义等） 可以具有该名称。 具有的符号*内部链接*或*无链接*仅在声明它的翻译单元内可见。 当名称具有内部链接时，可能另一个翻译单元中存在相同的名称。 使用类定义声明的变量或函数体有无链接。 

你可以强制执行的全局名称，若要通过显式声明为具有内部链接**静态**。 这将限制为在其中声明同一个翻译单元其可见性。 请注意，在此上下文中，**静态**比时应用于局部变量不同的含义。

默认情况下，以下对象具有内部链接：
- const 对象
- constexpr 对象
- typedefs
- 命名空间范围内的静态对象

要为 const 对象外部链接，请将其声明为**extern**并将其分配一个值：

```cpp
extern const int value = 42;
```

请参阅[extern](extern-cpp.md)有关详细信息。

## <a name="see-also"></a>请参阅
 [基本概念](../cpp/basic-concepts-cpp.md)