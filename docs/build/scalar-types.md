---
title: "标量类型 | Microsoft Docs"
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
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 标量类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

尽管可从任何对齐方式发出数据访问，但建议将数据在其自然边界上对齐，以避免性能损失（或更多损失）。  枚举为常数整数，视为 32 位整数。  下表介绍类型定义及其属于使用以下对齐值的对齐方式时的推荐存储区大小：  
  
-   Byte － 8 位  
  
-   Word － 16 位  
  
-   Double Word － 32 位  
  
-   Quad Word － 64 位  
  
-   Octa Word － 128 位  
  
|||||  
|-|-|-|-|  
|标量类型|C 数据类型|存储区大小（以字节为单位）|推荐对齐方式|  
|**INT8**|`char`|1|Byte|  
|**UINT8**|`unsigned char`|1|Byte|  
|**INT16**|**short**|2|Word|  
|**UINT16**|**unsigned short**|2|Word|  
|**INT32**|**int、long**|4|Doubleword|  
|**UINT32**|**unsigned int、unsigned long**|4|Doubleword|  
|**INT64**|`__int64`|8|Quadword|  
|**UINT64**|**unsigned \_\_int64**|8|Quadword|  
|**FP32（单精度）**|**float**|4|Doubleword|  
|**FP64（双精度）**|**double**|8|Quadword|  
|**POINTER**|**\***|8|Quadword|  
|`__m64`|**struct \_\_m64**|8|Quadword|  
|`__m128`|**struct \_\_m128**|16|Octaword|  
  
## 请参阅  
 [类型和存储](../build/types-and-storage.md)