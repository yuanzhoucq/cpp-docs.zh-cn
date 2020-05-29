---
title: 编译器警告（等级3） C4839
ms.date: 09/13/2018
f1_keywords:
- C4839
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
ms.openlocfilehash: 2c238dc16359583bf55f7590d2ce7c0363d66df7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198570"
---
# <a name="compiler-warning-level-3-c4839"></a>编译器警告（等级3） C4839

> 类 "*type*" 作为可变参数函数的参数的非标准用法

传递给可变参数函数（如 `printf`）的类或结构必须是完全复制。 传递此类对象时，编译器只是执行按位复制，不会调用构造函数或析构函数。

从 Visual Studio 2017 开始提供此警告。

## <a name="example"></a>示例

下面的示例生成 C4839：

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

对于使用 `CStringW`生成和管理的字符串，提供的 `operator LPCWSTR()` 应用于将 `CStringW` 对象强制转换为格式字符串所需的 C 指针。

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
