---
title: noalias
ms.date: 07/07/2020
f1_keywords:
- noalias_cpp
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
ms.openlocfilehash: 70c1f4e8bfa426e858014a78febc424b473a89ae
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127870"
---
# `noalias`

**Microsoft 专用**

**`noalias`** 表示函数调用不会修改或引用可见全局状态，而只会修改指针参数（第一级间接寻址）*直接*指向的内存。

如果将函数注释为 **`noalias`** ，则优化器可以假定仅参数本身，并且仅在函数内引用或修改指针参数的第一级间接寻址。

**`noalias`** 批注仅适用于带批注的函数的主体。 将函数标记为 **`__declspec(noalias)`** 不会影响函数所返回的指针的别名。

对于可能会影响别名的其他注释，请参阅 [`__declspec(restrict)`](../cpp/restrict.md) 。

## <a name="example"></a>示例

下面的示例演示如何使用 **`__declspec(noalias)`** 。

当 `multiply` 批注访问内存的函数时 **`__declspec(noalias)`** ，它会告知编译器此函数不会修改全局状态，除非通过其参数列表中的指针。

```C
// declspec_noalias.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1/k++;
    return a;
}

__declspec(noalias) void multiply(float * a, float * b, float * c)
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

## <a name="see-also"></a>另请参阅

[`__declspec`](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[`__declspec(restrict)`](../cpp/restrict.md)
