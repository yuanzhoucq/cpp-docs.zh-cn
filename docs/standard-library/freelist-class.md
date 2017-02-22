---
title: "freelist 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::freelist"
  - "freelist"
  - "stdext.freelist"
  - "allocators/stdext::freelist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "freelist 类"
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# freelist 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

管理存储区的列表。  
  
## 语法  
  
```  
template <std::size_t Sz, class Max> class freelist  
    : public Max  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`Sz`|元素的数目将数组赋的。|  
|`Max`|表示元素的最大次数最大类将存储在自由列表。  最大类可以是 [max\_none](../standard-library/max-none-class.md)[max\_unbounded](../standard-library/max-unbounded-class.md)[max\_fixed\_size](../standard-library/max-fixed-size-class.md)[max\_variable\_size](../standard-library/max-variable-size-class.md)、、或。|  
  
## 备注  
 此模板类管理 `Sz` 存储区具有最大范围列表类依赖列表的最大长度的传入 `Max`。  
  
### 构造函数  
  
|||  
|-|-|  
|[freelist](../Topic/freelist::freelist.md)|构造 `freelist` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[pop](../Topic/freelist::pop.md)|免从列表中移除的第一个存储区。|  
|[push](../Topic/freelist::push.md)|添加一个存储区添加到列表中。|  
  
## 要求  
 **页眉：** \<分配程序\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)