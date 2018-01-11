---
title: "A.9 使用单个指令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 11d41d62448d41d7a11ef747e65cc6ac47e4bd7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="a9---using-single-directives"></a>A.9   使用 single 指令
下面的示例演示`single`指令 ([部分 2.4.3](../../parallel/openmp/2-4-3-single-construct.md)在页上 15)。 在示例中，只有一个线程 (通常遇到的第一个线程`single`指令) 将打印进度消息。 用户必须对将执行的线程不进行任何假设`single`部分。 所有其他线程将跳过`single`部分，并在末尾的屏障处停止`single`构造。 如果其他线程可以转而无需等待的线程正在执行`single`部分中，`nowait`子句可以指定在`single`指令。  
  
```  
#pragma omp parallel  
{  
    #pragma omp single  
        printf_s("Beginning work1.\n");  
    work1();  
    #pragma omp single  
        printf_s("Finishing work1.\n");  
    #pragma omp single nowait  
        printf_s("Finished work1 and beginning work2.\n");  
    work2();  
}  
```