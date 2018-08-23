---
title: 限制 |Microsoft Docs
ms.custom: ''
ms.date: 02/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- restrict_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3eb361d0b92a3977547388ebfd612915431ec98
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463676"
---
# <a name="restrict"></a>restrict

**Microsoft 专用**

应用于函数声明或定义返回指针类型时**限制**告知编译器该函数返回一个对象，它不*别名*，也就是说，引用的任何其他指针。 这使编译器能够执行其他优化。

## <a name="syntax"></a>语法

> **__declspec(restrict)** *pointer_return_type* *function*();  
  
## <a name="remarks"></a>备注

编译器将传播 **__declspec(restrict)**。 例如，CRT`malloc`函数具有 **__declspec(restrict)** 修饰，因此，编译器假定指针初始化为内存位置的`malloc`还不是别名之前现有的指针。

编译器不会检查返回的指针不是实际使用别名。 开发人员负责确保程序没有别名使用标记的指针**限制 __declspec**修饰符。  
  
有关变量的类似语义，请参阅[__restrict](../cpp/extension-restrict.md)。
 
适用于锯齿函数内的另一个批注，请参阅[__declspec(noalias)](../cpp/noalias.md)。
  
璝惠**限制**关键字是 C++ AMP 中，请参阅[限制 (C++ AMP)](../cpp/restrict-cpp-amp.md)。  
 
## <a name="example"></a>示例  

下面的示例演示如何使用 **__declspec(restrict)**。

当 **__declspec(restrict)** 应用于函数，返回一个指针，这将告知编译器的返回值指向的内存不使用别名。 在此示例中，指针`mempool`和`memptr`是全局的因此编译器不能确保它们引用的内存不使用别名。 但是，在中使用`ma`和其调用方`init`内存不是否则所引用的程序，因此将返回方式 **__decslpec(restrict)** 用于帮助优化程序。 它类似于 CRT 标头如修饰的分配函数如何`malloc`通过使用 **__declspec(restrict)** 以指示它们始终返回不能有别名的现有指针的内存。

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
 [关键字](../cpp/keywords-cpp.md)  
 [__declspec](../cpp/declspec.md)  
 [__declspec(noalias)](../cpp/noalias.md)  
