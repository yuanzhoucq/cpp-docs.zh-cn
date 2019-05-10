---
title: 编译器警告 （等级 C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: a757004659c1a9d2ce858cfae5ddfbc6c024d782
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360003"
---
# <a name="compiler-warning-level-4-c4840"></a>编译器警告 （等级 C4840

> 类的不可移植用法*类型*作为可变参数函数的参数

## <a name="remarks"></a>备注

传递给 variadic 函数的类或结构必须完全可复制。 传递此类对象时，编译器只是执行按位复制，不会调用构造函数或析构函数。

此警告是 Visual Studio 2017 中的开始提供。

## <a name="example"></a>示例

下面的示例生成 C4840 并演示如何修复此错误：

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

对于字符串使用生成和管理`CStringW`，提供`operator LPCWSTR()`应该用于强制转换`CStringW`到所需的格式字符串的 C 样式字符串指针的对象：

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```