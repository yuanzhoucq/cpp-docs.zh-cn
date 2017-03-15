---
title: "sync_none 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext.sync_none"
  - "sync_none"
  - "allocators/stdext::sync_none"
  - "stdext::sync_none"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sync_none 类"
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# sync_none 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述未同步提供的 [同步筛选器](../standard-library/allocators-header.md)。  
  
## 语法  
  
```  
template <class Cache> class sync_none  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`Cache`|缓存类型与同步筛选器。  这可以是 [cache\_chunklist](../standard-library/cache-chunklist-class.md)、[cache\_freelist](../standard-library/cache-freelist-class.md)或 [cache\_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
### 成员函数  
  
|||  
|-|-|  
|[分配](../Topic/sync_none::allocate.md)|分配内存块。|  
|[释放](../Topic/sync_none::deallocate.md)|从存储空间开头释放对象中的指定数字中的指定位置。|  
|[equals](../Topic/sync_none::equals.md)|比较是否相等来缓存。|  
  
## 要求  
 **页眉：** \<分配程序\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)