---
title: "A.9   Using single Directives | Microsoft Docs"
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
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.9   Using single Directives
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下面的示例演示 `single` 指令 \(在第 15 页\) 的[第2.4.3部分](../../parallel/openmp/2-4-3-single-construct.md) 。  在此示例中，只有一个线程 \(最常用 `single` 指令\) 的第一个线程进度消息打印。  用户不能使线程上执行 `single` 部分的任何假设。  其他线程将跳过 `single` 部分和停止在关卡在 `single` 构造结束时。  如果其他线程可以执行，而不必等待执行 `single` 部分的线程， `nowait` 子句。 `single` 指令中指定。  
  
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