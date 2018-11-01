---
title: 编译器警告（等级 1 和等级 4）C4700
ms.date: 02/21/2018
f1_keywords:
- C4700
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
ms.openlocfilehash: fa3326bd5ab495dbc4c54130bb168422eb827dce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463214"
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>编译器警告（等级 1 和等级 4）C4700

> 未初始化的局部变量*名称*使用

本地变量*名称*已*使用*，即从阅读，它具有之前尚未分配值。 在 C 和 c + + 中，默认情况下不初始化局部变量。 未初始化的变量可以包含任何值，并使用会导致未定义的行为。 警告 C4700 几乎总是指示在程序中可能导致不可预知的结果或崩溃的 bug。

若要解决此问题，可以在声明时初始化的局部变量，或为它们赋值，在使用之前。 可以使用函数来初始化的变量，它传递作为引用参数，或当其地址传递作为指针参数。

## <a name="example"></a>示例

此示例生成 C4700 之前它们进行了初始化，并显示数值类型的垃圾回收可能会导致使用变量 t、 u 和 v。 变量 x、 y 和 z 是否会导致以下警告，因为它们在使用前初始化：

```cpp
// c4700.cpp
// compile by using: cl /EHsc /W4 c4700.cpp
#include <iostream>

// function takes an int reference to initialize
void initialize(int& i)
{
    i = 21;
}

int main()
{
    int s, t, u, v;   // Danger, uninitialized variables

    s = t + u + v;    // C4700: t, u, v used before initialization
    std::cout << "Value in s: " << s << std::endl;

    int w, x;         // Danger, uninitialized variables
    initialize(x);    // fix: call function to init x before use
    int y{10};        // fix: initialize y, z when declared
    int z{11};        // This C++11 syntax is recommended over int z = 11;

    w = x + y + z;    // Okay, all values initialized before use
    std::cout << "Value in w: " << w << std::endl;
}
```

此代码时运行、 t、 u 和 v 均未初始化，并为 s 的输出是不可预测：

```Output
Value in s: 37816963
Value in w: 42
```
