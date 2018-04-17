---
title: 程序和链接 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 04/09/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab24c552a150e5a14037d727c8d3428eb6bbf809
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="program-and-linkage--c"></a>程序和链接 （C++）

在 c + + 程序中，每个全局符号可以定义一次，即使该计划包括的多个翻译单元。 翻译单元组成实现文件 （.cpp、.hpp、.cxx 等） 和其中的直接或间接的所有标头。 程序包括链接在一起的一个或多个翻译单元。 

## <a name="linkage-vs-scope"></a>与作用域的链接

这一概念*链接*跨翻译单元是指作为一个整体 （例如变量、 类型名称和函数名称） 在程序中的全局符号的可见性。 这一概念*作用域*指如命名空间、 类或函数体块中声明的符号。 此类符号是仅在其中定义它们; 范围内可见链接的概念不适用于它们。

## <a name="external-vs-internal-linkage"></a>与内部链接的外部

非 const 全局变量和默认情况下的自由格式函数具有外部链接;它们是在程序中任何翻译单元中可见。 你可以通过显式声明它们作为重写此行为**静态**这就限制了对相同声明它们的翻译单元其可见性。 这种含义的**静态**不同于其含义时应用于局部变量。 变量声明为**const**默认情况下具有内部链接。

## <a name="extern-constexpr-linkage"></a>Extern constexpr 链接

在早期版本的 Visual Studio 中，编译器始终提供 constexpr 变量内部链接即使变量被标记为外部。 在 Visual Studio 2017 版本 15.5 中，新编译器开关 (/Zc:externConstexpr) 启用符合标准的正确行为。 这最终将成为默认设置。

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

如果标头文件包含变量的声明的 extern constexpr，它需要将标记为**__declspec （selectany)**才能正确组合其重复声明：

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="see-also"></a>另请参阅

 [基本概念](../cpp/basic-concepts-cpp.md)