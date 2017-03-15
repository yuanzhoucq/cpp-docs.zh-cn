---
title: "2.7.2 Data-Sharing Attribute Clauses | Microsoft Docs"
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
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2 Data-Sharing Attribute Clauses
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

多个指令接受允许用户控制变量共享的属性该区域的持续时间的子句。  共享属性子句请仅适用于子句出现指令的词法区域的变量。  并非所有下列子句在所有指令允许。  适用于特定指令子句的列表描述了与指令。  
  
 如果变量是可见的，当并行或的工作划分构造遇到时，因此，该变量位于共享的属性未指定子句或 **threadprivate** 指令，则该变量共享。  在并行区域内的动态区域中声明的静态变量共享。  堆栈分配的内存 \(例如，使用 **malloc \(\)** 在 C 或 C\+\+ **新** 运算符 C\+\+ 中\) 共享。  ，但是， \(此内存的指针可私有或共享。\)与并行区域内的动态区域声明的自动存储持续时间的变量是私有的。  
  
 大多数子句接受 *变量参数* 列表，是逗号分隔列表的变量可见。  如果数据共享属性子句引用的变量具有从模板派生的类型，因此，不再对该变量在过程中，该行为不确定。  
  
 在指令子句中出现的所有变量必须是可见的。  子句可能会重复根据需要，但是，没有变量在多个子句中指定，除此之外，变量在 **firstprivate** 和 **lastprivate** 子句中指定。  
  
 以下各节介绍数据共享属性子句:  
  
-   **专用**，在第 25 页的 [第2.7.2.1部分](../../parallel/openmp/2-7-2-1-private.md) 。  
  
-   **firstprivate**，在第 26 页的 [第2.7.2.2部分](../../parallel/openmp/2-7-2-2-firstprivate.md) 。  
  
-   **lastprivate**，在第 27 页的 [第2.7.2.3部分](../../parallel/openmp/2-7-2-3-lastprivate.md) 。  
  
-   **共享**，在第 27 页的 [第2.7.2.4部分](../../parallel/openmp/2-7-2-4-shared.md) 。  
  
-   **默认**，在第 28 页的 [第2.7.2.5部分](../../parallel/openmp/2-7-2-5-default.md) 。  
  
-   **减少**，在第 28 页的 [第2.7.2.6部分](../../parallel/openmp/2-7-2-6-reduction.md) 。  
  
-   **copyin**，在第 31 页的 [第2.7.2.7部分](../../parallel/openmp/2-7-2-7-copyin.md) 。  
  
-   **copyprivate**，在第 32 页的 [第2.7.2.8部分](../../parallel/openmp/2-7-2-8-copyprivate.md) 。