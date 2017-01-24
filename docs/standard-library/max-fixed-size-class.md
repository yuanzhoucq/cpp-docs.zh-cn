---
title: "max_fixed_size 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "allocators/stdext::max_fixed_size"
  - "max_fixed_size"
  - "stdext::max_fixed_size"
  - "stdext.max_fixed_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_fixed_size 类"
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# max_fixed_size 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一限制。[最大类](../standard-library/allocators-header.md) 对象固定的最大长度的 [freelist](../standard-library/freelist-class.md) 一个对象。  
  
## 语法  
  
```  
template <std::size_t Max> class max_fixed_size  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`Max`|在 `freelist`确定元素的最大数字存储的最大事类。|  
  
### 构造函数  
  
|||  
|-|-|  
|[max\_fixed\_size](../Topic/max_fixed_size::max_fixed_size.md)|构造 `max_fixed_size` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[分配](../Topic/max_fixed_size::allocated.md)|计数增加分配的存储区。|  
|[释放](../Topic/max_fixed_size::deallocated.md)|计数递减分配的存储区。|  
|[完全](../Topic/max_fixed_size::full.md)|返回值指定是否应添加更多存储区为免列表。|  
|[释放](../Topic/max_fixed_size::released.md)|计数递减在空闲列表的存储区。|  
|[保存](../Topic/max_fixed_size::saved.md)|在计数增加空闲列表的存储区。|  
  
## 要求  
 **页眉：** \<分配程序\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)