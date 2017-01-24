---
title: "&lt;set&gt; | Microsoft Docs"
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
  - "std.<set>"
  - "std::<set>"
  - "<set>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "set 标头"
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;set&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义容器模板类 set 和 multiset 及其支持的模板。  
  
## 语法  
  
```  
  
#include <set>  
  
```  
  
## 成员  
  
### 运算符  
  
|Set 版本|Multiset 版本|说明|  
|------------|-----------------|--------|  
|[operator\!\= \(set\)](../Topic/operator!=%20\(set\).md)|[operator\!\= \(multiset\)](../Topic/operator!=%20\(multiset\).md)|测试运算符左侧的 set 或 multiset 对象是否不等于右侧的 set 或 multiset 对象。|  
|[operator\< \(set\)](../Topic/operator%3C%20\(set\).md)|[operator\< \(multiset\)](../Topic/operator%3C%20\(multiset\).md)|测试运算符左侧的 set 或 multiset 对象是否小于右侧的 set 或 multiset 对象。|  
|[operator\<\= \(set\)](../Topic/operator%3C=%20\(set\).md)|[operator\<\= \(multiset\)](../Topic/operator%3C=%20\(multiset\).md)|测试运算符左侧的 set 或 multiset 对象是否小于或等于右侧的 set 或 multiset 对象。|  
|[operator\=\= \(set\)](../Topic/operator==%20\(set\).md)|[operator\=\= \(multiset\)](../Topic/operator==%20\(multiset\).md)|测试运算符左侧的 set 或 multiset 对象是否等于右侧的 set 或 multiset 对象。|  
|[operator\> \(set\)](../Topic/operator%3E%20\(set\).md)|[operator\> \(multiset\)](../Topic/operator%3E%20\(multiset\).md)|测试运算符左侧的 set 或 multiset 对象是否大于右侧的 set 或 multiset 对象。|  
|[operator\>\= \(set\)](../Topic/operator%3E=%20\(set\).md)|[operator\>\= \(multiset\)](../Topic/operator%3E=%20\(multiset\).md)|测试运算符左侧的 set 或 multiset 对象是否大于或等于右侧的 set 或 multiset 对象。|  
  
### 专用化模板函数  
  
|Set 版本|Multiset 版本|说明|  
|------------|-----------------|--------|  
|[swap \(set\)](../Topic/swap%20\(set\).md)|[swap \(multiset\)](../Topic/swap%20\(multiset\).md)|交换两个集或多个集的元素。|  
  
### 类  
  
|||  
|-|-|  
|[set 类](../standard-library/set-class.md)|用于存储和检索集合中的数据，此集合中包含的元素值是唯一的，并且用作数据自动排序所依据的关键字值。|  
|[multiset 类](../standard-library/multiset-class.md)|用于存储和检索集合中的数据，此集合中包含的元素值不必是唯一的，并且可用作数据自动排序所依据的关键字值。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)