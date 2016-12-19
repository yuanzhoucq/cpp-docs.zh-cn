---
title: "allocator_suballoc 类 | Microsoft Docs"
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
  - "allocators::allocator_suballoc"
  - "allocator_suballoc"
  - "stdext.allocators.allocator_suballoc"
  - "allocators/stdext::allocators::allocator_suballoc"
  - "stdext::allocators::allocator_suballoc"
  - "allocators/stdext::allocator_suballoc"
  - "allocators.allocator_suballoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_suballoc 类"
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
caps.latest.revision: 16
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# allocator_suballoc 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一个对象，用于管理存储分配和释放的对象类型的 `Type` 使用类型的缓存 [cache\_suballoc](../standard-library/cache-suballoc-class.md)。  
  
## 语法  
  
```  
template <class Type>  
    class allocator_suballoc;  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`Type`|由分配器分配元素类型。|  
  
## 备注  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) 宏将传递的此类作为 `name` 以下语句中的参数︰ `ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`  
  
## 要求  
 **标头：**\<allocators\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)