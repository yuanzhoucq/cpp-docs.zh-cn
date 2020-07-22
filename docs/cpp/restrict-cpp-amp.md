---
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: b3464b758c6b66cdbd5015ee4b7c9d11eb2209dd
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404933"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

可将限制说明符应用于函数和 lambda 声明。 它会强制对函数中的代码以及使用 C++ Accelerated Massive Parallelism (C++ AMP) 运行时的应用程序中的函数的行为实施限制。

> [!NOTE]
> 有关 **__declspec**存储类属性中的**restrict**关键字的详细信息，请参阅[restrict](../cpp/restrict.md)。

**Restrict**子句采用以下形式：

|子句|说明|
|------------|-----------------|
|`restrict(cpu)`|函数可使用完整的 C++ 语言。 只有使用 restrict(cpu) 函数声明的其他函数功能可调用函数。|
|`restrict(amp)`|函数只能使用 C++ AMP 可为其加速的一部分 C++ 语言。|
|一系列 `restrict(cpu)` 和 `restrict(amp)`。|函数必须遵循 `restrict(cpu)` 和 `restrict(amp)`的限制。 函数可由使用 `restrict(cpu)`、`restrict(amp)`、`restrict(cpu, amp)` 或 `restrict(amp, cpu)` 声明的函数调用。<br /><br /> `restrict(A) restrict(B)` 形式可以编写为 `restrict(A,B)`。|

## <a name="remarks"></a>备注

**Restrict**关键字是上下文关键字。 限制说明符、`cpu` 和 `amp` 不是保留字。 说明符列表不可扩展。 没有**restrict**子句的函数与具有子句的函数相同 `restrict(cpu)` 。

包含 `restrict(amp)` 子句的函数具有以下限制：

- 函数只能调用具有 `restrict(amp)` 子句的函数。

- 函数必须可内联。

- 函数只能声明**int**、**无符号 int**、 **float**和**double**变量以及仅包含这些类型的类和结构。 还允许使用**bool** ，但如果在复合类型中使用，则它必须为4字节对齐。

- Lambda 函数无法通过引用捕获，并且无法捕获指针。

- 仅支持引用和单一间接指针作为局部变量、函数自变量和返回类型。

- 不允许使用以下项：

  - 递归。

  - 用[volatile](../cpp/volatile-cpp.md)关键字声明的变量。

  - 虚函数。

  - 指向函数的指针。

  - 指向成员函数的指针。

  - 结构中的指针。

  - 指向指针的指针。

  - **goto**语句。

  - Labeled 语句。

  - 请**尝试**、**捕获**或**抛**出语句。

  - 全局变量。

  - 静态变量。 请改用[Tile_static 关键字](../cpp/tile-static-keyword.md)。

  - **dynamic_cast**强制转换。

  - **Typeid**运算符。

  - asm 声明。

  - Varargs。

有关函数限制的讨论，请参阅[限制（amp）限制](/archive/blogs/nativeconcurrency/restrictamp-restrictions-part-0-of-n-introduction)。

## <a name="example"></a>示例

下面的示例演示如何使用 `restrict(amp)` 子句。

```cpp
void functionAmp() restrict(amp) {}
void functionNonAmp() {}

void callFunctions() restrict(amp)
{
    // int is allowed.
    int x;
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.
    // long long int y;

    // Calling an amp-restricted function is allowed.
    functionAmp();

    // Calling a non-amp-restricted function is not allowed.
    // functionNonAmp();
}
```

## <a name="see-also"></a>另请参阅

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)
