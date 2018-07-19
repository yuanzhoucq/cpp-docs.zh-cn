---
title: Private 子句 A.24 示例 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f90a5b49-81ff-4746-ae03-37bbd33f6c08
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f8d07f2d95b565077f5dfd78fdc4ff6edf30216
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691383"
---
# <a name="a24---example-of-the-private-clause"></a>A.24   private 子句的示例
`private`子句 ([部分 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)第 25 页上) 的并行区域仅会影响区域的词法范围，不能为区域的动态范围。  因此，在下面的示例中，使用该变量的任何内`for`例程中的循环*f*的私有副本是指，而在使用情况例程*g*引用全局。  
  
```  
int a;  
  
void f(int n)   
{  
    a = 0;  
  
    #pragma omp parallel for private(a)  
    for (int i=1; i<n; i++)   
    {  
        a = i;  
        g(i, n);  
        d(a);     // Private copy of "a"  
        ...  
    }  
    ...  
  
void g(int k, int n)   
{  
    h(k,a); // The global "a", not the private "a" in f  
}  
```