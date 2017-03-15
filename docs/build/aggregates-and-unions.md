---
title: "聚合和联合 | Microsoft Docs"
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
  - "聚合 [C++], 和联合"
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 聚合和联合
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

其他类型（如数组、结构和联合）都具有较严格的对齐要求，以确保对聚合和联合实现一致的存储与数据检索。  以下是数组、结构和联合的定义：  
  
 数组  
 包含相邻数据对象的有序组。  每个对象称为一个元素。  数组中所有元素的大小和数据类型都相同。  
  
 结构  
 包含数据对象的有序组。  与数组的元素不同，结构中的数据对象可以具有不同的数据类型和大小。  结构中的每个数据对象称为一个成员。  
  
 Union  
 可保存任何命名成员集的对象。  命名集的成员可以是任何类型。  为联合分配的存储区等于该联合的最大成员所需的存储区，再加上对齐所需的所有空白。  
  
 下表所示为强烈建议的联合和结构标量成员的对齐方式。  
  
||||  
|-|-|-|  
|标量类型|C 数据类型|要求的对齐方式|  
|**INT8**|`char`|Byte|  
|**UINT8**|`unsigned char`|Byte|  
|**INT16**|**short**|Word|  
|**UINT16**|**unsigned short**|Word|  
|**INT32**|**int、long**|Doubleword|  
|**UINT32**|**unsigned int、unsigned long**|Doubleword|  
|**INT64**|`__int64`|Quadword|  
|**UINT64**|**unsigned \_\_int64**|Quadword|  
|**FP32（单精度）**|**float**|Doubleword|  
|**FP64（双精度）**|**double**|Quadword|  
|**POINTER**|**\***|Quadword|  
|`__m64`|**struct \_\_m64**|Quadword|  
|`__m128`|**struct \_\_m128**|Octaword|  
  
 适用以下聚合对齐规则：  
  
-   数组的对齐方式与数组中某个元素的对齐方式相同。  
  
-   结构或联合开始处的对齐方式是所有单个成员的最大对齐方式。  结构或联合中的每个成员必须位于其正确的对齐位置，如前面表中所定义的那样，而这可能需要进行隐式内部填充（由前面的成员决定）。  
  
-   结构大小必须是其对齐的整数倍，这可能需要在最后一个成员之后进行填充。  由于结构和联合能以数组进行分组，因此结构或联合的每个数组元素必须按照前面定义的正确对齐方式开始和结束。  
  
-   只要遵循前面的规则，就可以使用超出对齐要求的方式将数据对齐。  
  
-   由于大小方面的原因，单个编译器可能会调整结构的封装方式。  例如，[\/Zp（结构成员对齐）](../build/reference/zp-struct-member-alignment.md) 就允许调整结构的封装方式。  
  
## 请参阅  
 [类型和存储](../build/types-and-storage.md)