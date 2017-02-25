---
title: "max_variable_size 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::max_variable_size"
  - "allocators/stdext::max_variable_size"
  - "stdext.max_variable_size"
  - "max_variable_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_variable_size 类"
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# max_variable_size 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 [最多可有类](../standard-library/allocators-header.md) 对象，用于限制 [freelist](../standard-library/freelist-class.md) 是大致的数量成正比的最大长度的对象分配内存块。  
  
## 语法  
  
```  
class max_variable_size  
```  
  
### 构造函数  
  
|||  
|-|-|  
|[max\_variable\_size](../Topic/max_variable_size::max_variable_size.md)|构造 `max_variable_size` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[分配](../Topic/max_variable_size::allocated.md)|分配的内存块的计数递增。|  
|[释放](../Topic/max_variable_size::deallocated.md)|递减的计数分配内存块。|  
|[全部](../Topic/max_variable_size::full.md)|返回一个值，指定是否应将更多的内存块添加到可用的列表。|  
|[发布](../Topic/max_variable_size::released.md)|递减的计数的内存块上可用的列表。|  
|[保存](../Topic/max_variable_size::saved.md)|可用列表上的内存块的计数递增。|  
  
## 要求  
 **标头：**\<allocators\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)