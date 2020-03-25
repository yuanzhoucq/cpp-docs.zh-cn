---
title: 编译器错误 C2397
ms.date: 11/04/2016
f1_keywords:
- C2397
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
ms.openlocfilehash: 02a8bb09e0b22619bd61e6c4675057263a62a9d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206010"
---
# <a name="compiler-error-c2397"></a>编译器错误 C2397

从 "type_1" 转换到 "type_2" 需要收缩转换

使用统一初始化时发现隐式收缩转换。

C 语言允许在赋值和初始化中进行隐式收缩转换C++ ，并遵循这种方法，即使意外收缩是导致许多代码错误的原因。 为了使代码更加安全， C++在初始化列表中出现收缩转换时，标准需要诊断消息。 在 Visual C++Studio 2015 中，使用从 visual Studio 开始支持的统一初始化语法，在 visual Studio 中，诊断是编译器错误 C2397。 当使用 Visual Studio 2013 支持的列表或聚合初始化语法时，编译器将生成[编译器警告（等级1） C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) 。

如果知道目标中可以容纳转换后的值的可能范围，则可以进行收缩转换。 在这种情况下，您知道编译器的功能要多。 如果你有意进行收缩转换，则应使用静态强制转换使意图成为显式的。 否则，此错误消息几乎总是表明代码中存在 bug。 您可以通过确保您初始化的对象具有足够大的类型来处理输入，从而修复此问题。

下面的示例生成 C2397，并显示修复此问题的一种方法：

```
// C2397.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C2397.cpp
#include <vector>

struct S1 {
    int m1;
    double m2, m3;
};

void function_C2397(double d1) {
    char c1 { 127 };          // OK
    char c2 { 513 };          // error C2397

    std::vector<S1> vS1;
    vS1.push_back({ d1, 2, 3 }); // error C2397

    // Possible fix if you know d1 always fits in an int
    vS1.push_back({ static_cast<int>(d1), 2, 3 });
}
```
