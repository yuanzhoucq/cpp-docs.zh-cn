---
title: "显示不正确的工作共享指令的嵌套的 A.19 示例 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 906e900d-9259-44d6-a095-c1ba9135d269
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8a3f8a4e1ca62a77c16dafedd0921ca842d7a048
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="a19---examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19   显示工作共享指令的不正确嵌套的示例
本部分中的示例阐释了指令的嵌套规则。 指令嵌套的详细信息，请参阅[部分 2.9](../../parallel/openmp/2-9-directive-nesting.md)在页上 33。  
  
 下面的示例是不符合因为内部和外部`for`指令嵌套的并将绑定到相同`parallel`指令：  
  
```  
void wrong1(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
      int i, j;  
      #pragma omp for  
      for (i=0; i<n; i++) {  
          #pragma omp for  
              for (j=0; j<n; j++)  
                 work(i, j);  
     }  
   }  
}  
```  
  
 前面中的以下动态嵌套的版本也是示例的不符合要求的：  
  
```  
void wrong2(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++)  
        work1(i, n);  
  }  
}  
  
void work1(int i, int n)  
{  
  int j;  
  #pragma omp for  
    for (j=0; j<n; j++)  
      work2(i, j);  
}  
```  
  
 下面的示例是不符合因为`for`和`single`嵌套指令，以及如何它们绑定到同一并行区域：  
  
```  
void wrong3(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++) {  
        #pragma omp single  
          work(i);  
      }  
  }  
}  
```  
  
 下面的示例是不符合因为`barrier`内`for`可能会导致死锁：  
  
```  
void wrong4(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++) {  
        work1(i);  
        #pragma omp barrier  
        work2(i);  
      }  
  }  
}  
```  
  
 下面的示例是不符合因为`barrier`导致死锁，因为，一次只有一个线程可以进入临界区：  
  
```  
void wrong5()  
{  
  #pragma omp parallel  
  {  
    #pragma omp critical  
    {  
       work1();  
       #pragma omp barrier  
       work2();  
    }  
  }  
}  
```  
  
 下面的示例是不符合因为`barrier`导致死锁，因为，只有一个线程执行`single`部分：  
  
```  
void wrong6()  
{  
  #pragma omp parallel  
  {  
    setup();  
    #pragma omp single  
    {  
      work1();  
      #pragma omp barrier  
      work2();  
    }  
    finish();  
  }  
}  
```