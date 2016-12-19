---
title: "A.20   Binding of barrier Directives | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.20   Binding of barrier Directives
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指令的绑定规则要求 **障碍** 指令绑定到最接近的封闭 `parallel` 指令。  有关指令绑定的更多信息，请参见在第 32 页的 [第2.8部分](../../parallel/openmp/2-8-directive-binding.md) 。  
  
 在下面的示例中，调用从 *主* 到 *sub2* 是兼容的，因为 **障碍** \(在 *sub3*\) 绑定到 *sub2 的*并行区域。  ，因为 **障碍** 绑定到子例程 *sub2，的*并行区域调用从 *主* 到 *sub1* 兼容。  调用从 *主* 到 *sub3* 是兼容的，因为 **障碍** 不绑定到任何并行区域并且忽略。  另外请注意 **障碍** 在为封闭并行区域仅同步。 *sub1*创建的线程并不是所有的线程团队。  
  
```  
int main()  
{  
    sub1(2);  
    sub2(2);  
    sub3(2);  
}  
  
void sub1(int n)  
{  
    int i;  
    #pragma omp parallel private(i) shared(n)  
    {  
        #pragma omp for  
        for (i=0; i<n; i++)  
            sub2(i);  
    }  
}  
  
void sub2(int k)  
{  
     #pragma omp parallel shared(k)  
     sub3(k);  
}  
  
void sub3(int n)  
{  
    work(n);  
    #pragma omp barrier  
    work(n);  
}  
```