---
title: 编译器警告 （等级 1） C4838
ms.date: 11/04/2016
f1_keywords:
- C4838
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
ms.openlocfilehash: dcb7062c751320a9f9c612b42caf6d018047d8d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532959"
---
# <a name="compiler-warning-level-1-c4838"></a>编译器警告 （等级 1） C4838

从 type_1 转换为 type_2 需要收缩转换

使用聚合或列表初始化时找到的隐式收缩转换。

C 语言允许隐式收缩转换中赋值和初始化，并且 c + + 遵循叠，即使意外收缩是很多代码错误的原因。 若要使代码更加安全，标准 c + + 时，需要一条诊断消息初始化列表中将发生收缩转换。 在 Visual c + +，在诊断处于[编译器错误 C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md)时使用支持从 Visual Studio 2015 中的统一初始化语法。 编译器将生成警告 C4838 时使用的列表或通过 Visual Studio 2013 支持聚合初始化语法。

当你知道目标中可以容纳转换后的值的可能范围时，收缩转换可以是可行。 在这种情况下，您知道个以上的编译器执行的操作。 如果您有意进行收缩转换，使你的意图显式使用静态强制转换。 否则，此警告消息几乎总是指示在代码中存在 bug。 可以通过确保您初始化的对象具有足够大以处理输入的类型来修复此错误。

下面的示例生成 C4838，并演示一种方法修复此错误：

```
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