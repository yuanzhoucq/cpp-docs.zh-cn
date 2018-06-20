---
title: 程序和链接 （c + +） |Microsoft 文档
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
ms.openlocfilehash: 2dba8698461636e292771fc1e5a4f5ac0a633e73
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238664"
---
# <a name="program-and-linkage-c"></a>程序和链接 (C++)

在 c + + 程序中，*符号*，例如变量或函数名称中，可以声明为任意次数，在其范围内，但它可以仅一次定义。 这是一个定义规则 (ODR)。 A*声明*引入了 （或重新引入） 到该程序的名称。 A*定义*引入了一个名称并且，当变量，显式初始化该变量。 A*函数定义*签名和函数体组成。

这些是声明：

```cpp
int i;
int f(int x);
```

这些是定义：

```cpp
int i{42};
int f(int x){ return x * i; }
```

程序包括一个或多个*翻译单元*。 翻译单元由实现文件 （.cpp、.cxx 等） 和所有标头 （.h、.hpp 等），它包括直接或间接组成。 每个翻译单元独立编译的编译器，此后链接器将已编译的翻译单元合并到单个*程序*。 ODR 规则冲突的情况通常显示为链接器错误时相同的名称在不同的翻译单元中具有两个不同的定义。

一般情况下，使变量在多个文件中可见的最好办法是将其放入标头文件并添加 #include 指令要求声明每个.cpp 文件中。 通过添加*include 防护*围绕标头内容中，确保仅一次定义它声明的名称。

但是，在某些情况下可能需要声明全局变量或.cpp 文件中的类。 在这些情况下，你将需要某种方式告知编译器和链接器对象的名称将应用到一个文件，只需或所有文件。

## <a name="linkage-vs-scope"></a>与作用域的链接

这一概念*链接*跨翻译单元是指作为一个整体 （例如变量、 类型名称和函数名称） 在程序中的全局符号的可见性。 这一概念*作用域*指如命名空间、 类或函数体块中声明的符号。 此类符号是仅在其中定义它们; 范围内可见链接的概念不适用于它们。 

## <a name="external-vs-internal-linkage"></a>与内部链接的外部

A*释放函数*是函数，定义在全局或命名空间范围。 非 const 全局变量和默认情况下的自由格式函数具有*外部链接*; 它们是在程序中任何翻译单元中可见。 因此，没有任何其他全局对象 （变量、 类定义等） 可以具有该名称。 具有的符号*内部链接*或*没有链接*仅在声明它的翻译单元内可见。 当名称具有内部链接时，相同的名称可能存在于另一个翻译单元中。 变量声明的类定义或函数体都没有链接。 

你可以强制执行全局名称通过显式声明其作为具有内部链接**静态**。 这就限制了对相同的翻译单元在其中声明其可见性。 请注意，在此上下文中，**静态**比时应用于局部变量不同的含义。

默认情况下，以下对象具有内部链接：
- const 对象
- constexpr 对象
- typedefs
- 命名空间范围内的静态对象

若要为 const 对象外部链接，将其声明为**extern**并将其分配一个值：

```cpp
extern const int value = 42;
```

请参阅[extern](extern-cpp.md)有关详细信息。

## <a name="see-also"></a>请参阅

 [基本概念](../cpp/basic-concepts-cpp.md)