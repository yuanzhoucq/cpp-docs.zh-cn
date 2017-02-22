---
title: "内存管理：示例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++], 分配资源"
  - "数组 [C++], 内存管理"
  - "数据结构 [C++]"
  - "数据结构 [C++], 分配内存"
  - "示例 [MFC], 内存分配"
  - "帧分配"
  - "堆分配, 示例"
  - "内存分配 [C++], 数组"
  - "内存分配 [C++], 数据结构"
  - "内存分配 [C++], 示例"
  - "内存分配 [C++], 对象"
  - "MFC [C++], 内存管理"
  - "对象 [C++], 分配内存"
  - "对象 [C++], 内存分配"
  - "结构内存分配"
  - "类型 [C++], 内存分配"
ms.assetid: f10240f8-b698-4c83-9288-97a54318930b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 内存管理：示例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文介绍 MFC 如何对框架分配和堆分配三种典型的中的每个内存分配：  
  
-   [字节数组](#_core_allocation_of_an_array_of_bytes)  
  
-   [一个数据结构](#_core_allocation_of_a_data_structure)  
  
-   [一个对象。](#_core_allocation_of_an_object)  
  
##  <a name="_core_allocation_of_an_array_of_bytes"></a> 数组分配的字节  
  
#### 分配一个在框架的字节  
  
1.  定义数组如下面的代码所示。  删除数组，其内存将自动恢复，在数组变量退出其范围。  
  
     [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/CPP/memory-management-examples_1.cpp)]  
  
#### 分配一字节数组 \(或任何原始数据类型在堆\)  
  
1.  使用用本示例中显示的 **new** 数组语法的运算符：  
  
     [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/CPP/memory-management-examples_2.cpp)]  
  
#### 解除分配堆的数组  
  
1.  使用 **删除** 运算符为：  
  
     [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/CPP/memory-management-examples_3.cpp)]  
  
##  <a name="_core_allocation_of_a_data_structure"></a> 数据结构中分配  
  
#### 框架上分配一个数据结构。  
  
1.  定义结构变量：  
  
     [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/CPP/memory-management-examples_4.cpp)]  
  
     当退出其范围时，结构占用的内存回收。  
  
#### 分配堆的数据结构。  
  
1.  使用 **new** 分配堆和 **删除** 的数据结构释放它们，如下面的示例所示：  
  
     [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/CPP/memory-management-examples_5.cpp)]  
  
##  <a name="_core_allocation_of_an_object"></a> 对象的分配  
  
#### 框架上分配的对象  
  
1.  对象声明如下：  
  
     [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/CPP/memory-management-examples_6.cpp)]  
  
     对象时，其范围退出时，该对象的析构函数。自动调用。  
  
#### 分配堆上的对象  
  
1.  使用 **new** 运算符，返回指向对象的指针，此分配堆上的对象。  使用 **删除** 运算符来删除这些对象。  
  
     下面的示例假定 `CPerson` 堆和帧，构造函数不采用参数。  
  
     [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/CPP/memory-management-examples_7.cpp)]  
  
     如果 `CPerson` 构造函数的参数是指向 `char`，则框架分配的语句为：  
  
     [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/CPP/memory-management-examples_8.cpp)]  
  
     堆分配的语句为：  
  
     [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/CPP/memory-management-examples_9.cpp)]  
  
## 请参阅  
 [内存管理：堆分配](../mfc/memory-management-heap-allocation.md)