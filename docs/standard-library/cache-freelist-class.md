---
title: "cache_freelist 类 | Microsoft Docs"
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
  - "stdext.cache_freelist"
  - "allocators/stdext::cache_freelist"
  - "stdext::cache_freelist"
  - "cache_freelist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cache_freelist 类"
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cache_freelist 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义 [阻止分配器](../standard-library/allocators-header.md) 的分配和释放内存块的一个大小。  
  
## 语法  
  
```  
template <std::size_t Sz, class Max> class cache_freelist  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`Sz`|要分配的数组中的元素数。|  
|`Max`|表示可用列表的最大大小的最大类。 这可能是 [max\_fixed\_size](../standard-library/max-fixed-size-class.md), ，[max\_none](../standard-library/max-none-class.md), ，[max\_unbounded](../standard-library/max-unbounded-class.md), ，或 [max\_variable\_size](../standard-library/max-variable-size-class.md)。|  
  
## 备注  
 Cache\_freelist 模板类维护一个可用大小的内存块的列表 `Sz`。 可用列表已满时它使用 `operator delete` 以释放内存块。 可用列表为空时它使用 `operator new` 分配新的内存块。 可用列表的最大大小由中传递的最大类的类 `Max` 参数。  
  
 每个内存块保留 `Sz` 字节的可用内存和数据， `operator new` 和 `operator delete` 要求。  
  
### 构造函数  
  
|||  
|-|-|  
|[cache\_freelist](../Topic/cache_freelist::cache_freelist.md)|构造 `cache_freelist` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[allocate](../Topic/cache_freelist::allocate.md)|分配内存块。|  
|[释放](../Topic/cache_freelist::deallocate.md)|从指定位置开始从存储中释放指定数量的的对象。|  
  
## 要求  
 **标头：**\<allocators\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)