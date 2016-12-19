---
title: "sync_per_thread 类 | Microsoft Docs"
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
  - "stdext::sync_per_thread"
  - "sync_per_thread"
  - "allocators/stdext::sync_per_thread"
  - "stdext.sync_per_thread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sync_per_thread 类"
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sync_per_thread 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

说明为每个线程提供一个单独的缓存对象的 [同步筛选器](../standard-library/allocators-header.md)。  
  
## 语法  
  
```  
template <class Cache> class sync_per_thread  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`Cache`|缓存类型与同步筛选器。  这可以是 [cache\_chunklist](../standard-library/cache-chunklist-class.md)、[cache\_freelist](../standard-library/cache-freelist-class.md)或 [cache\_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
## 备注  
 使用 `sync_per_thread` 的分配器可以比较相同，即使一个线程分配块不能从另一个线程释放。  当不应该将使用分配的存储区分配这些程序之一。一线程可见其他线程。  实际上这意味着使用这些分配程序之一的容器应当由单个线程只访问。  
  
### 成员函数  
  
|||  
|-|-|  
|[分配](../Topic/sync_per_thread::allocate.md)|分配内存块。|  
|[释放](../Topic/sync_per_thread::deallocate.md)|从存储空间开头释放对象中的指定数字中的指定位置。|  
|[equals](../Topic/sync_per_thread::equals.md)|比较是否相等来缓存。|  
  
## 要求  
 **页眉：** \<分配程序\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)