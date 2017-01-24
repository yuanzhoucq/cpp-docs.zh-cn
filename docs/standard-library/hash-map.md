---
title: "&lt;hash_map&gt; | Microsoft Docs"
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
  - "std.<hash_map>"
  - "<hash_map>"
  - "std::<hash_map>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_map 标头"
ms.assetid: 0765708a-a668-42a2-9800-654c857bdcc2
caps.latest.revision: 27
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;hash_map&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  此标头已废弃不用。 替代项为 [\<unordered\_map\>](../standard-library/unordered-map.md)。  
  
 定义容器模板类 hash\_map 和 hash\_multimap 及其支持的模板。  
  
 在 Visual C\+\+ .NET 2003 中，[\<hash\_map\>](#vclrfhash_map_header_file) 和 [\<hash\_set\>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关更多信息，请参见[stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
## 语法  
  
```  
  
#include <hash_map>  
  
```  
  
### 运算符  
  
|Hash\_map 版本|Hash\_multimap 版本|描述|  
|------------------|-----------------------|--------|  
|[operator\!\= \(hash\_map\)](../Topic/operator!=%20\(hash_map\).md)|[operator\!\= \(hash\_multimap\)](../Topic/operator!=%20\(hash_multimap\).md)|测试运算符左侧和右侧的 hash\_map 或 hash\_multimap 对象是否不相等。|  
|[operator\=\= \(hash\_map\)](http://msdn.microsoft.com/zh-cn/f933cb1c-934d-43f5-aa9e-0b325eb95b85)|[operator\=\= \(hash\_multimap\)](http://msdn.microsoft.com/zh-cn/3fa378b1-0250-4e3f-a130-dc14103fc5e9)|测试运算符左侧和右侧的 hash\_map 或 hash\_multimap 对象是否相等。|  
  
### 专用化模板函数  
  
|Hash\_map 版本|Hash\_multimap 版本|描述|  
|------------------|-----------------------|--------|  
|[swap \(hash\_map\)](../Topic/hash_map::swap.md)|[swap \(hash\_multimap\)](../Topic/hash_multimap::swap.md)|交换两个 hash\_map 或 hash\_multimap 的元素。|  
  
### 类  
  
|||  
|-|-|  
|[hash\_compare 类](../standard-library/hash-compare-class.md)|描述了一个对象，任何哈希关联容器（hash\_map、hash\_multimap、hash\_set 或 hash\_multiset）都可将该对象用作默认的 **Traits** 参数对象，以对其所包含的元素进行排序和哈希处理。|  
|[value\_compare 类](../standard-library/value-compare-class.md)|提供一个函数对象，该对象能通过比较 hash\_map 元素的键值来比较这些元素，以确定其在 hash\_map 中的相对顺序。|  
|[hash\_map 类](../standard-library/hash-map-class.md)|用于存储和快速检索集合中的数据，集合中的每个元素都是具有排序键和关联数据值的元素对，而排序键的值是唯一的。|  
|[hash\_multimap 类](../standard-library/hash-multimap-class.md)|用于存储和快速检索集合中的数据，集合中的每个元素都是具有排序键和关联数据值的元素对，而排序键的值不需要具有唯一性。|  
  
## 要求  
 **标头：**\<hash\_map\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)