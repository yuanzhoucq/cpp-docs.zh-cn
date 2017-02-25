---
title: "uses_allocator 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "future/std::uses_allocator"
dev_langs: 
  - "C++"
ms.assetid: c418f002-62e9-4806-b70c-41c663cae583
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# uses_allocator 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

总是应用的专用化。  
  
## 语法  
  
```  
template<class Ty, class Alloc>  
struct uses_allocator<promise<Ty>, Alloc> : true_type;  
template<class Ty, class Alloc>  
struct uses_allocator<packaged_task<Ty>, Alloc> : true_type;  
```  
  
## 要求  
 **标头:** future  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)