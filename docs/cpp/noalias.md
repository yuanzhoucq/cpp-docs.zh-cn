---
title: noalias
ms.date: 02/09/2018
f1_keywords:
- noalias_cpp
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
ms.openlocfilehash: 2eceffd10f97615859918991320ceebf577d094c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447120"
---
# <a name="noalias"></a>noalias

**Microsoft 专用**

**noalias**意味着函数调用不会修改或引用可见全局状态且只会修改指向的内存*直接*指针参数 （第一级间接寻址）。

如果函数被批注作为**noalias**，则优化器假设，除了参数本身，仅第一级间接寻址指针参数的引用或修改在函数内。 可见全局状态是未在编译范围外定义或引用的所有数据的集合，因此不采用它们的地址。 编译范围是所有源文件 ([/LTCG （链接时间代码生成）](../build/reference/ltcg-link-time-code-generation.md)生成) 或单个源文件 (非 **/LTCG**生成)。

**Noalias**批注仅适用于带批注的函数的主体。 函数标记为 **__declspec(noalias)** 不会影响的函数返回的指针的别名。

可能会影响别名的另一个批注，请参阅[__declspec(restrict)](../cpp/restrict.md)。

## <a name="example"></a>示例

下面的示例演示如何使用 **__declspec(noalias)**。

当函数`multiply`访问内存进行批注 **__declspec(noalias)**，它会告知编译器该函数不会修改通过指针在它的参数列表中的全局状态除外。

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

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[__declspec(restrict)](../cpp/restrict.md)
