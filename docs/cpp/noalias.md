---
title: "noalias |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: noalias_cpp
dev_langs: C++
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92e96ce931ea5bc44e03a5803865daa66f960e92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="noalias"></a>noalias

**Microsoft 专用**

`noalias`意味着函数调用不会修改或引用可见全局状态且只会修改指向的内存*直接*指针参数 （第一级间接寻址）。

如果函数被批注为 `noalias`，则优化器可以假定除了参数本身以外，只在函数内引用或修改指针参数的第一级间接寻址。 可见全局状态是未在编译范围外定义或引用的所有数据的集合，因此不采用它们的地址。 编译作用域是所有的源文件 ([/LTCG （链接时间代码生成）](../build/reference/ltcg-link-time-code-generation.md)生成) 或单个源文件 (非**/LTCG**生成)。

## <a name="example"></a>示例

以下代码示例演示了使用 `__declspec(restrict)` 和 `__declspec(noalias)`。 通常情况下，内存返回从`malloc`是`restrict`因为 CRT 标头适当的修饰。

但是，在此示例中，指针`mempool`和`memptr`是全局性的因此编译器的内存不别名不保证。 使用 `__declspec(restrict)` 修饰返回指针的函数将通知编译器，返回值指向的内存不使用别名。

使用 `__declspec(noalias)` 修饰示例中访问内存的函数将通知编译器，此函数不会干扰全局状态，除非通过其参数列表中的指针。

```C
// declspec_noalias.c
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

[__declspec](../cpp/declspec.md)  
[关键字](../cpp/keywords-cpp.md)