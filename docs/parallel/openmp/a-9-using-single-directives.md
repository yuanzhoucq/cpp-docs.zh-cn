---
title: A.9 使用单个指令 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc0e0e08b0b7bdea05bf4c627ae33cc42298c6dc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690376"
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