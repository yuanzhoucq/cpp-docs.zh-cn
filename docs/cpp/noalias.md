---
title: "noalias | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "noalias"
  - "noalias_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], noalias"
  - "noalias __declspec 关键字"
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# noalias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 `noalias` 意味着函数调用不会修改或引用可见全局状态且只会修改指针参数（第一级间接寻址）指向的 `directly` 内存。  
  
 如果函数被批注为 `noalias`，则优化器可以假定除了参数本身以外，只在函数内引用或修改指针参数的第一级间接寻址。  可见全局状态是未在编译范围外定义或引用的所有数据的集合，因此不采用它们的地址。  编译范围是所有源文件（[\/LTCG（链接时代码生成）](../build/reference/ltcg-link-time-code-generation.md) 生成）或单个源文件（非 **\/LTCG** 生成）。  
  
## 示例  
 以下代码示例演示了使用 `__declspec(restrict)` 和 `__declspec(noalias)`。  通常，从 `malloc` 返回的内存是 `restrict` 和 `noalias`，因为对 CRT 标头进行了适当的修饰。  
  
 但是，在此示例中，指针 `mempool` 和 `memptr`  是全局的，因此编译器不确保内存不使用别名。  使用 `__declspec(restrict)` 修饰返回指针的函数将通知编译器，返回值指向的内存不使用别名。  
  
 使用 `__declspec(noalias)` 修饰示例中访问内存的函数将通知编译器，此函数不会干扰全局状态，除非通过其参数列表中的指针。  
  
```  
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
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)