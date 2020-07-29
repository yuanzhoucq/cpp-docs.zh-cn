---
title: restrict
ms.date: 02/09/2018
f1_keywords:
- restrict_cpp
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
ms.openlocfilehash: a0108cff3d6b98fd929b7888d2ad718e7b6b3a64
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213250"
---
# <a name="restrict"></a>restrict

**Microsoft 专用**

当应用于返回指针类型的函数声明或定义时， **`restrict`** 通知编译器该函数返回一个未*化名*为的对象，也就是说，由任何其他指针引用。 这允许编译器执行其他优化。

## <a name="syntax"></a>语法

> **`__declspec(restrict)`***pointer_return_type* *函数*（）;

## <a name="remarks"></a>备注

编译器传播 **`__declspec(restrict)`** 。 例如，CRT `malloc` 函数具有一个 **`__declspec(restrict)`** 修饰，因此，编译器假设通过以前的现有指针，初始化为的内存位置的指针 `malloc` 也不是别名。

编译器不会检查返回的指针是否确实有别名。 开发人员应负责确保程序不会为使用**限制 __declspec**修饰符标记的指针提供别名。

有关变量的类似语义，请参阅[__restrict](../cpp/extension-restrict.md)。

对于适用于函数内的别名的另一个批注，请参阅[__declspec （noalias）](../cpp/noalias.md)。

有关 **`restrict`** C++ AMP 中包含的关键字的信息，请参阅[restrict （C++ AMP）](../cpp/restrict-cpp-amp.md)。

## <a name="example"></a>示例

下面的示例演示如何使用 **`__declspec(restrict)`** 。

当 **`__declspec(restrict)`** 应用于返回指针的函数时，会告知编译器，返回值指向的内存未化名为别名。 在此示例中，指针 `mempool` 和 `memptr` 是全局的，因此编译器无法确保它们引用的内存不具有别名。 但是，在和其调用方内使用它们时，将 `ma` `init` 返回程序不引用的内存，因此 **__decslpec （限制）** 用于帮助优化器。 这类似于 CRT 标头如何通过使用来修饰分配函数（如）， `malloc` **`__declspec(restrict)`** 以指示它们始终返回无法由现有指针化名的内存。

```C
// declspec_restrict.c
// Compile with: cl /W4 declspec_restrict.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

__declspec(restrict) float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

__declspec(restrict) float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1f/k++;
    return a;
}

void multiply(float * a, float * b, float * c)
{
    int i, j, k;

    for (j=0; j<P; j++)
        for (i=0; i<M; i++)
            for (k=0; k<N; k++)
                c[i * P + j] =
                          a[i * N + k] *
                          b[k * P + j];
}

int main()
{
    float * a, * b, * c;

    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));

    if (!mempool)
    {
        puts("ERROR: Malloc returned null");
        exit(1);
    }

    memptr = mempool;
    a = init(M, N);
    b = init(N, P);
    c = init(M, P);

    multiply(a, b, c);
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[__declspec](../cpp/declspec.md)<br/>
[__declspec （noalias）](../cpp/noalias.md)
