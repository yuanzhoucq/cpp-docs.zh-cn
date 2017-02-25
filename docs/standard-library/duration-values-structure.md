---
title: "duration_values 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::duration_values"
dev_langs: 
  - "C++"
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# duration_values 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为 [持续时间](../standard-library/duration-class.md) 模板参数 `Rep`提供特定值。  
  
## 语法  
  
```  
template<class Rep>  
   struct duration_values;  
```  
  
## 成员  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[duration\_values::max 方法](../Topic/duration_values::max%20Method.md)|静态的。  为类型 `Rep`指定了上限值。|  
|[duration\_values::min 方法](../Topic/duration_values::min%20Method.md)|静态的。  为类型 `Rep`指定了下限值。|  
|[duration\_values::zero 方法](../Topic/duration_values::zero%20Method.md)|静态的。  返回 `Rep(0)`。|  
  
## 要求  
 **Header:** chrono  
  
 **Namespace:** std::chrono  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)