---
title: "atomic_flag 结构 | Microsoft Docs"
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
  - "atomic/std::atomic_flag"
dev_langs: 
  - "C++"
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
caps.latest.revision: 14
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atomic_flag 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述基本设置和清除 `bool` 标志的对象。  基本标记的操作通常是无锁的。  
  
## 语法  
  
```  
struct atomic_flag;  
```  
  
## 成员  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[atomic\_flag::clear 方法](../Topic/atomic_flag::clear%20Method.md)|将存储标志设置为 `false` 。|  
|[atomic\_flag::test\_and\_set 方法](../Topic/atomic_flag::test_and_set%20Method.md)|将存储标志设置为 `true` 并返回初始标志值。|  
  
## 备注  
 `atomic_flag` 对象可传递到非成员函数 [atomic\_flag\_clear](../Topic/atomic_flag_clear%20Function.md)、[atomic\_flag\_clear\_explicit](../Topic/atomic_flag_clear_explicit%20Function.md)、[atomic\_flag\_test\_and\_set](../Topic/atomic_flag_test_and_set%20Function.md)和 [atomic\_flag\_test\_and\_set\_explicit](../Topic/atomic_flag_test_and_set_explicit%20Function.md)。  使用值 `ATOMIC_FLAG_INIT`可将它们初始化。  
  
## 要求  
 **标头：**原子  
  
 **命名空间:** std  
  
## 请参阅  
 [\<atomic\>](../standard-library/atomic.md)