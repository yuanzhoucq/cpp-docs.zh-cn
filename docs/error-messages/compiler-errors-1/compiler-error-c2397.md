---
title: 编译器错误 C2397 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- C2397
dev_langs:
- C++
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3e76384ca2509663398fd7abd7badfd4057e8c3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115094"
---
# <a name="compiler-error-c2397"></a>编译器错误 C2397

从 type_1 转换为 type_2 需要收缩转换

使用统一初始化时找到的隐式收缩转换。

C 语言允许隐式收缩转换中赋值和初始化，并且 c + + 遵循叠，即使意外收缩是很多代码错误的原因。 若要使代码更加安全，标准 c + + 时，需要一条诊断消息初始化列表中将发生收缩转换。 在 Visual c + +，诊断是编译器错误 C2397 时在 Visual Studio 2015 中使用统一初始化支持语法开头。 编译器将生成[编译器警告 （等级 1） C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md)时使用的列表或通过 Visual Studio 2013 支持聚合初始化语法。

当你知道目标中可以容纳转换后的值的可能范围时，收缩转换可以是可行。 在这种情况下，您知道个以上的编译器执行的操作。 如果您有意进行收缩转换，使你的意图显式使用静态强制转换。 否则，此错误消息几乎总是指示在代码中存在错误。 可以通过确保您初始化的对象具有足够大以处理输入的类型来修复此错误。

下面的示例生成 C2397，并演示一种方法修复此错误：

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