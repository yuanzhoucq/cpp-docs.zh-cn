---
title: "allocator_newdel 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "allocators::allocator_newdel"
  - "allocators/stdext::allocators::allocator_newdel"
  - "stdext.allocators.allocator_newdel"
  - "allocators/stdext::allocator_newdel"
  - "allocator_newdel"
  - "stdext::allocators::allocator_newdel"
  - "allocators.allocator_newdel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_newdel 类"
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# allocator_newdel 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

实现使用 `operator delete` 释放内存块和 `operator new` 分配存储区分配的一个程序。  
  
## 语法  
  
```  
template <class Type>  
    class allocator_newdel;  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`Type`|分配程序分配的元素类型。|  
  
## 备注  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) 宏传递此类为以下语句的参数：`name``ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`  
  
## 要求  
 **页眉：** \<分配程序\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)