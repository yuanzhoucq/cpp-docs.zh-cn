---
title: "&lt; 映射 &gt; | Microsoft Docs"
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
  - "std::<map>"
  - "std.<map>"
  - "<map>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "map 标头"
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; 映射 &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义容器模板类 map 和 multimap 及其支持的模板。  
  
## 语法  
  
```  
  
#include <map>  
  
```  
  
## 成员  
  
### 运算符  
  
|Map 版本|Multimap 版本|描述|  
|------------|-----------------|--------|  
|[operator\!\= \(map\)](../Topic/operator!=%20\(map\).md)|[operator\!\= \(multimap\)](../Topic/operator!=%20\(multimap\).md)|测试运算符左侧和右侧的 map 或 multimap 对象是否不相等。|  
|[operator\< \(map\)](../Topic/operator==%20\(map\).md)|[operator\< \(multimap\)](../Topic/operator==%20\(multimap\).md)|测试运算符左侧的 map 或 multimap 对象是否小于右侧的 map 或 multimap 对象。|  
|[operator\<\= \(map\)](../Topic/operator%3C%20\(map\).md)|[operator\<\= \(multimap\)](../Topic/operator%3C%20\(multimap\).md)|测试运算符左侧的 map 或 multimap 对象是否小于或等于右侧的 map 或 multimap 对象。|  
|[operator\=\= \(map\)](../Topic/operator%3C=%20\(map\).md)|[operator\=\= \(multimap\)](../Topic/operator%3C=%20\(multimap\).md)|测试运算符左侧和右侧的 map 或 multimap 对象是否相等。|  
|[operator\> \(map\)](../Topic/operator%3E%20\(map\).md)|[operator\> \(multimap\)](../Topic/operator%3E%20\(multimap\).md)|测试运算符左侧的 map 或 multimap 对象是否大于右侧的 map 或 multimap 对象。|  
|[operator\>\= \(map\)](../Topic/operator%3E=%20\(map\).md)|[operator\>\= \(multimap\)](../Topic/operator%3E=%20\(multimap\).md)|测试运算符左侧的 map 或 multimap 对象是否大于或等于右侧的 map 或 multimap 对象。|  
  
### 专用化模板函数  
  
|Map 版本|Multimap 版本|描述|  
|------------|-----------------|--------|  
|[swap \(map\)](../Topic/swap%20\(map\).md)|[swap \(multimap\)](../Topic/swap%20\(multimap\).md)|交换两个 map 或 multimap 的元素。|  
  
### 类  
  
|||  
|-|-|  
|[value\_compare 类](../standard-library/value-compare-class-map.md)|提供一个函数对象，它能通过比较其键的值来比较映射的元素，以确定其在映射中的相对顺序。|  
|[map 类](../standard-library/map-class.md)|用于存储和检索集合中的数据，此集合中每个元素都有用于自动排列数据的唯一键。|  
|[multimap 类](../standard-library/multimap-class.md)|用于存储和检索集合中的数据，此集合中每个元素都有一个用于自动排列数据的键，且这些键不需要具有唯一值。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)