---
title: 编译器警告 （等级 1 和等级 4） C4700 |Microsoft 文档
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4700
dev_langs:
- C++
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 876ae98fb2fdea5a9d8bdaecb93b8c229213d329
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>编译器警告（等级 1 和等级 4）C4700

> 未初始化的局部变量*名称*使用

本地变量*名称*已*使用*，即从阅读，它具有之前被分配了值。 在 C 和 c + + 中，默认情况下不初始化本地变量。 未初始化的变量可以包含任何值，因而其使用会导致未定义的行为。 警告 C4700 几乎始终表示可能导致不可预知的结果或崩溃程序中存在 bug。

若要解决此问题，可以初始化本地变量，它们在声明时或在使用之前为它们分配一个值。 函数可用来初始化的变量传递作为引用参数，或当作为指针参数传递其地址。

## <a name="example"></a>示例

如果变量 t、 u 和 v 习惯之前它们进行了初始化，并显示可能会导致垃圾回收值的种类，此示例将生成 C4700。 变量 x、 y 和 z 是否会导致该警告，因为它们在使用前初始化：

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

此代码时运行、 t、 u 和 v 未初始化，并且 s 输出是不可预知：

```Output
Value in s: 37816963
Value in w: 42
```
