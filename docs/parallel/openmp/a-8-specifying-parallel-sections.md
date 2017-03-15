---
title: "A.8   Specifying Parallel Sections | Microsoft Docs"
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
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.8   Specifying Parallel Sections
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在下面的示例中， \(对于第 14 页\) 的 [第2.4.2部分](../../parallel/openmp/2-4-2-sections-construct.md) 函数 *X 轴*、 *Y 轴*和 *Z 轴* 可以同时执行。  第一个 `section` 指令是可选的。  请注意所有 `section` 指令需要显示 `parallel``sections` 构造的词法范围。  
  
```  
#pragma omp parallel sections  
{  
    #pragma omp section  
        xaxis();  
    #pragma omp section  
        yaxis();  
    #pragma omp section  
        zaxis();  
}  
```