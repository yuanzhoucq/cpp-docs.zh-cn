---
title: "allocator_fixed_size 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "allocators/stdext::allocators::allocator_fixed_size"
  - "allocators::allocator_fixed_size"
  - "allocators/stdext::allocator_fixed_size"
  - "allocator_fixed_size"
  - "stdext::allocators::allocator_fixed_size"
  - "allocators.allocator_fixed_size"
  - "stdext.allocators.allocator_fixed_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_fixed_size 类"
ms.assetid: 138f3ef8-b0b3-49c3-9486-58f2213c172f
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# allocator_fixed_size 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述管理存储区分配和释放 `Type` 类型的对象使用一个使用 [max\_fixed\_size](../standard-library/max-fixed-size-class.md)缓存管理的长度的 [cache\_freelist](../standard-library/cache-freelist-class.md) 类型的对象。  
  
## 语法  
  
```  
template <class Type>  
    class allocator_fixed_size;  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`Type`|分配程序分配的元素类型。|  
  
## 备注  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) 宏传递此类为以下语句的参数：`name``ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_fixed_size<10>), SYNC_DEFAULT, allocator_fixed_size);`  
  
## 要求  
 **页眉：** \<分配程序\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)