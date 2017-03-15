---
title: "cache_suballoc 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext.cache_suballoc"
  - "allocators/stdext::cache_suballoc"
  - "stdext::cache_suballoc"
  - "cache_suballoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cache_suballoc 类"
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# cache_suballoc 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义 [阻止分配器](../standard-library/allocators-header.md) 的分配和释放内存块的一个大小。  
  
## 语法  
  
```  
template <std::size_t Sz, size_t Nelts = 20> class cache_suballoc  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`Sz`|要分配的数组中的元素数。|  
  
## 备注  
 Cache\_suballoc 模板类将已释放的内存块存储在不受限制的长度，可用列表使用 `freelist<sizeof(Type), max_unbounded>`, ，并分配有一个更大块从 suballocates 内存块 `operator new` 时可用的列表为空。  
  
 每个区块保留 `Sz * Nelts` 字节的可用内存和数据， `operator new` 和 `operator delete` 要求。 永远不会释放已分配的块。  
  
### 构造函数  
  
|||  
|-|-|  
|[cache\_suballoc](../Topic/cache_suballoc::cache_suballoc.md)|构造 `cache_suballoc` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[allocate](../Topic/cache_suballoc::allocate.md)|分配内存块。|  
|[释放](../Topic/cache_suballoc::deallocate.md)|从指定位置开始从存储中释放指定数量的的对象。|  
  
## 要求  
 **标头：**\<allocators\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)