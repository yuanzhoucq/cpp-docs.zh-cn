---
title: "max_unbounded 类 | Microsoft Docs"
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
  - "allocators/stdext::max_unbounded"
  - "stdext::max_unbounded"
  - "stdext.max_unbounded"
  - "max_unbounded"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_unbounded 类"
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# max_unbounded 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 [最多可有类](../standard-library/allocators-header.md) 对象，它不会限制的最大长度 [freelist](../standard-library/freelist-class.md) 对象。  
  
## 语法  
  
```  
class max_unbounded  
```  
  
### 成员函数  
  
|||  
|-|-|  
|[分配](../Topic/max_unbounded::allocated.md)|分配的内存块的计数递增。|  
|[释放](../Topic/max_unbounded::deallocated.md)|递减的计数分配内存块。|  
|[全部](../Topic/max_unbounded::full.md)|返回一个值，指定是否应将更多的内存块添加到可用的列表。|  
|[发布](../Topic/max_unbounded::released.md)|递减的计数的内存块上可用的列表。|  
|[保存](../Topic/max_unbounded::saved.md)|可用列表上的内存块的计数递增。|  
  
## 要求  
 **标头：**\<allocators\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)