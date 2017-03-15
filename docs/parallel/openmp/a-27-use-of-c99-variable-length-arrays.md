---
title: "A.27   Use of C99 Variable Length Arrays | Microsoft Docs"
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
ms.assetid: 8e542701-39f9-4f28-ab3a-840e8e669723
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.27   Use of C99 Variable Length Arrays
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下面的示例在 `firstprivate` 指令 \(在 \(VLAs\)第 26 页\) 的[第2.7.2.2部分](../../parallel/openmp/2-7-2-2-firstprivate.md) 演示如何使用 C99 变长数组。  
  
> [!NOTE]
>  变长数组在 Visual C\+\+ 当前不支持。  
  
```  
void f(int m, int C[m][m])  
{  
    double v1[m];  
    ...  
    #pragma omp parallel firstprivate(C, v1)  
    ...  
}  
```