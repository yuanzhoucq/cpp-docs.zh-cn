---
title: "allocator_unbounded 类 | Microsoft Docs"
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
  - "stdext::allocators::allocator_unbounded"
  - "allocator_unbounded"
  - "allocators/stdext::allocator_unbounded"
  - "allocators::allocator_unbounded"
  - "allocators/stdext::allocators::allocator_unbounded"
  - "allocators.allocator_unbounded"
  - "stdext.allocators.allocator_unbounded"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_unbounded 类"
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
caps.latest.revision: 17
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# allocator_unbounded 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述管理存储区分配和释放 `Type` 类型的对象使用一个使用 [max\_unbounded](../standard-library/max-unbounded-class.md)缓存管理的长度的 [cache\_freelist](../standard-library/cache-freelist-class.md) 类型的对象。  
  
## 语法  
  
```  
template <class Type>  
    class allocator_unbounded;  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`Type`|分配程序分配的元素类型。|  
  
## 备注  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) 宏传递此类为以下语句的参数：`name` `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`  
  
## 要求  
 **页眉：** \<分配程序\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)