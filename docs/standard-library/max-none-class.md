---
title: "max_none 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "max_none"
  - "stdext::max_none"
  - "stdext.max_none"
  - "allocators/stdext::max_none"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_none 类"
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# max_none 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 [最多可有类](../standard-library/allocators-header.md) 对象，用于限制 [freelist](../standard-library/freelist-class.md) 对象传递给最大长度为零。  
  
## 语法  
  
```  
template <std::size_t Max> class max_none  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`Max`|确定要在中存储的元素的最大数量的最大类 `freelist`。|  
  
### 成员函数  
  
|||  
|-|-|  
|[分配](../Topic/max_none::allocated.md)|分配的内存块的计数递增。|  
|[释放](../Topic/max_none::deallocated.md)|递减的计数分配内存块。|  
|[全部](../Topic/max_none::full.md)|返回一个值，指定是否应将更多的内存块添加到可用的列表。|  
|[发布](../Topic/max_none::released.md)|递减的计数的内存块上可用的列表。|  
|[保存](../Topic/max_none::saved.md)|可用列表上的内存块的计数递增。|  
  
## 要求  
 **标头：**\<allocators\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)