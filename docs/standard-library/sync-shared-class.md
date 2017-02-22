---
title: "sync_shared 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sync_shared"
  - "allocators/stdext::sync_shared"
  - "stdext.sync_shared"
  - "stdext::sync_shared"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sync_shared 类"
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# sync_shared 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

介绍[同步筛选器](../standard-library/allocators-header.md)，它使用互斥体来控制对所有分配器共享的缓存对象的访问。  
  
## 语法  
  
```  
template <class Cache> class sync_shared  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`Cache`|与同步筛选器相关联的缓存类型。 这可能是 [cache\_chunklist](../standard-library/cache-chunklist-class.md)、[cache\_freelist](../standard-library/cache-freelist-class.md) 或 [cache\_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
### 成员函数  
  
|||  
|-|-|  
|[allocate](../Topic/sync_shared::allocate.md)|分配内存块。|  
|[释放](../Topic/sync_shared::deallocate.md)|从指定位置开始从存储中释放指定数量的的对象。|  
|[等于](../Topic/sync_shared::equals.md)|比较两个缓存是否相等。|  
  
## 要求  
 **标头：**\<allocators\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)