---
title: "sync_per_container 类 | Microsoft Docs"
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
  - "stdext.sync_per_container"
  - "sync_per_container"
  - "stdext::sync_per_container"
  - "allocators/stdext::sync_per_container"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sync_per_container 类"
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sync_per_container 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

说明为每个分配程序对象提供一个单独的缓存对象的 [同步筛选器](../standard-library/allocators-header.md)。  
  
## 语法  
  
```  
template <class Cache> class sync_per_container  
    : public Cache  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`Cache`|缓存类型与同步筛选器。  这可以是 [cache\_chunklist](../standard-library/cache-chunklist-class.md)、[cache\_freelist](../standard-library/cache-freelist-class.md)或 [cache\_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
### 成员函数  
  
|||  
|-|-|  
|[equals](../Topic/sync_per_container::equals.md)|比较是否相等来缓存。|  
  
## 要求  
 **页眉：** \<分配程序\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)