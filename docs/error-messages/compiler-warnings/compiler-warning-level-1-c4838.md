---
title: 编译器警告（等级1） C4838
ms.date: 11/04/2016
f1_keywords:
- C4838
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
ms.openlocfilehash: c3ddc861e5da271903372eac1ef1e8f6916e06df
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199363"
---
# <a name="compiler-warning-level-1-c4838"></a>编译器警告（等级1） C4838

从 "type_1" 转换到 "type_2" 需要收缩转换

使用聚合或列表初始化时发现隐式收缩转换。

C 语言允许在赋值和初始化中进行隐式收缩转换C++ ，并遵循这种方法，即使意外收缩是导致许多代码错误的原因。 为了使代码更加安全， C++在初始化列表中出现收缩转换时，标准需要诊断消息。 在 Visual C++Studio 2015 中，使用从 visual Studio 开始支持的统一初始化语法，在 visual Studio 中，诊断是[编译器错误 C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md) 。 当使用 Visual Studio 2013 支持的列表或聚合初始化语法时，编译器将生成警告 C4838。

如果知道目标中可以容纳转换后的值的可能范围，则可以进行收缩转换。 在这种情况下，您知道编译器的功能要多。 如果你有意进行收缩转换，则应使用静态强制转换使意图成为显式的。 否则，此警告消息几乎始终表示代码中有 bug。 您可以通过确保您初始化的对象具有足够大的类型来处理输入，从而修复此问题。

下面的示例生成 C4838，并显示修复此问题的一种方法：

```cpp
// C4838.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C4838.cpp

struct S1 {
    int m1;
    double m2, m3;
};

void function_C4838(double d1) {
    double ad[] = { 1, d1 }; // OK
    int ai[] = { 1, d1 };    // warning C4838
    S1 s11 = { 1, 2, d1 };   // OK
    S1 s12 { d1, 2, 3 };     // warning C4838
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838
}
```
