---
title: "allocator_chunklist 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::allocators::allocator_chunklist"
  - "allocators::allocator_chunklist"
  - "allocators/stdext::allocator_chunklist"
  - "allocators.allocator_chunklist"
  - "allocators/stdext::allocators::allocator_chunklist"
  - "allocator_chunklist"
  - "stdext.allocators.allocator_chunklist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_chunklist 类"
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# allocator_chunklist 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述管理存储区分配和释放对象使用的 [cache\_chunklist](../standard-library/cache-chunklist-class.md)一缓存类型的对象。  
  
## 语法  
  
```  
template <class Type>  
    class allocator_chunklist;  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`Type`|分配程序分配的元素类型。|  
  
## 备注  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) 宏传递此类为以下语句的参数：`name``ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist``);`  
  
## 要求  
 **页眉：** \<分配程序\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)