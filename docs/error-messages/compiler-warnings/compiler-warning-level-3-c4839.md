---
title: 编译器警告 （等级 3） C4839 |Microsoft 文档
ms.date: 10/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4839
dev_langs:
- C++
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b72289eef03c56356865b0b62a999c417da570a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291952"
---
# <a name="compiler-warning-level-4-c4839"></a>编译器警告 （等级 4） C4839

> 类的非标准使用*类型*作为可变参数函数的自变量

在 Visual Studio 2017，类或结构，传递给可变参数函数如`printf`必须完全可复制。 传递此类对象时，编译器只是执行按位复制，不会调用构造函数或析构函数。

## <a name="example"></a>示例

下面的示例生成 C4839:

```cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called; 
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

若要更正错误，可调用一种成员函数，该函数返回可完全复制的类型，

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

或者执行静态强制转换，以在传递对象之前将其进行转换：

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

字符串所建立和管理使用`CStringW`，提供`operator LPCWSTR()`应该用于强制转换`CStringW`对象与预期的格式字符串由 C 指针。

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```