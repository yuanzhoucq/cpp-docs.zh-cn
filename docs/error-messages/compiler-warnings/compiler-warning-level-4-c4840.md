---
title: 编译器警告（等级4） C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: 649083d66d0c7a0ef11c742e56cbfb70e2e9b75f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185199"
---
# <a name="compiler-warning-level-4-c4840"></a>编译器警告（等级4） C4840

> 类 "*type*" 作为可变参数函数的参数的不可移植使用

## <a name="remarks"></a>备注

传递给可变参数函数的类或结构必须是完全复制。 传递此类对象时，编译器只是执行按位复制，不会调用构造函数或析构函数。

从 Visual Studio 2017 开始提供此警告。

## <a name="example"></a>示例

下面的示例生成 C4840，并演示如何修复此问题：

```cpp
// C4840.cpp
// compile by using: cl /EHsc /W4 C4840.cpp
#include <stdio.h>

int main()
{
    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);

    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                       // as an argument to a variadic function
    // To correct the error, you can perform a static cast
    // to convert the object before passing it:
    printf("%i\n", static_cast<int>(s));
}
```

对于使用 `CStringW`生成和管理的字符串，提供的 `operator LPCWSTR()` 应用于将 `CStringW` 对象强制转换为格式字符串所需的 C 样式字符串指针：

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
