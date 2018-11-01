---
title: 编译器错误 C2603
ms.date: 11/04/2016
f1_keywords:
- C2603
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
ms.openlocfilehash: 5391aed09b7fd448a9d72ea7cc17cd5c26fc5f04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605754"
---
# <a name="compiler-error-c2603"></a>编译器错误 C2603

> '*函数*： 太多块范围静态对象构造函数/析构函数在函数中使用

在 Visual Studio 2015 之前, 的 Visual c + + 编译器的版本时，或者当[/zc: threadsafeinit-](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)编译器选项指定，则为 31 个可以在外部可见的内联函数中的静态对象的数量限制.

若要解决此问题，我们建议你采用较新版本的 Visual c + + 编译器工具集，或如果可能，删除 /zc: threadsafeinit-编译器选项。 如果这是不可能，请考虑将静态对象。 如果相同类型的对象，请考虑使用该类型的单个静态数组并引用所需的各个成员。

## <a name="example"></a>示例

下面的代码生成 C2603，并演示一种方法修复此错误：

```cpp
// C2603.cpp
// Compile by using: cl /W4 /c /Zc:threadSafeInit- C2603.cpp
struct C { C() {} };
extern inline void f1() {
    static C C01, C02, C03, C04, C05, C06, C07, C08, C09, C10;
    static C C11, C12, C13, C14, C15, C16, C17, C18, C19, C20;
    static C C21, C22, C23, C24, C25, C26, C27, C28, C29, C30, C31;
    static C C32;   // C2603 Comment this line out to avoid error
}
```
