---
title: 编译器警告 （等级 3） C4839
ms.date: 09/13/2018
f1_keywords:
- C4839
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
ms.openlocfilehash: 09b6e5b8dc984b35df7de96f5cf8610f2b0f16af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401522"
---
# <a name="compiler-warning-level-3-c4839"></a>编译器警告 （等级 3） C4839

> 类的非标准用法*类型*作为可变参数函数的参数

类或结构传递给 variadic 函数如`printf`必须完全可复制。 传递此类对象时，编译器只是执行按位复制，不会调用构造函数或析构函数。

此警告是 Visual Studio 2017 中的开始提供。

## <a name="example"></a>示例

下面的示例生成 C4839:

```cpp
// C4839.cpp
// compile by using: cl /EHsc /W3 C4839.cpp
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
}
```

若要更正错误，可调用一种成员函数，该函数返回可完全复制的类型，

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

对于字符串使用生成和管理`CStringW`，提供`operator LPCWSTR()`应该用于强制转换`CStringW`到所需的格式字符串的 C 指针的对象。

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```