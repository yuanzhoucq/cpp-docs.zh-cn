---
title: "屏障指令的 A.20 绑定 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8d88c431753d918c05866324dd6436a091d6057a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="a20---binding-of-barrier-directives"></a>A.20   barrier 指令的绑定
指令绑定规则调用**屏障**指令以将绑定到最近的封闭`parallel`指令。 指令绑定的详细信息，请参阅[部分 2.8](../../parallel/openmp/2-8-directive-binding.md)在页上 32。  
  
 在下面的示例中，从调用*主要*到*sub2 报表*兼容因为**屏障**(在*sub3*) 将绑定到并行区域在*sub2 报表*。 从调用*主要*到*sub1*兼容因为**屏障**将绑定到在子例程的并行区域*sub2 报表*。  从调用*主要*到*sub3*兼容因为**屏障**不未将绑定到任何并行区域并将被忽略。 另请注意，**屏障**仅同步的封闭并行区域中的线程并不是所有在中创建的线程团队*sub1*。  
  
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