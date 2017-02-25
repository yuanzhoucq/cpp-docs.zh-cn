---
title: "cache_chunklist 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "allocators/stdext::cache_chunklist"
  - "stdext.cache_chunklist"
  - "stdext::cache_chunklist"
  - "cache_chunklist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cache_chunklist 类"
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# cache_chunklist 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义分配和释放一种大小的内存块的 [块分配程序](../standard-library/allocators-header.md)。  
  
## 语法  
  
```  
template <std::size_t Sz, std::size_t Nelts = 20> class cache_chunklist  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`Sz`|元素的数目将数组赋的。|  
  
## 备注  
 此模板类使用 `operator new` 块，suballocating 原始分配的内存块分配存储区存储，并在必要时；，其内存块没有正在使用时，它存储在单独空闲列表的释放的存储区域每个区块的，使用 `operator delete` 释放块。  
  
 每个存储区保存 `Sz` 字节可用内存和指针与区块它所属的。  每个块包含 `Nelts` 的 `operator new` 和 `operator delete` 所需的存储区、三分球、int 和数据。  
  
### 构造函数  
  
|||  
|-|-|  
|[cache\_chunklist](../Topic/cache_chunklist::cache_chunklist.md)|构造 `cache_chunklist` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[分配](../Topic/cache_chunklist::allocate.md)|分配内存块。|  
|[释放](../Topic/cache_chunklist::deallocate.md)|从存储空间开头释放对象中的指定数字中的指定位置。|  
  
## 要求  
 **页眉：** \<分配程序\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)