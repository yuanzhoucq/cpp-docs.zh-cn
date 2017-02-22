---
title: "&lt;hash_set&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<hash_set>"
  - "std.<hash_set>"
  - "std::<hash_set>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_set 标头"
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;hash_set&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  此标头已废弃不用。 替代项为 [\<unordered\_set\>](../standard-library/unordered-set.md)。  
  
 定义容器模板类 hash\_set 和 hash\_multiset 及其支持的模板。  
  
## 语法  
  
```  
  
#include <hash_set>  
  
```  
  
## 备注  
 在 Visual C\+\+ .NET 2003 中，[\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](#vclrfhash_set_header_file) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关更多信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### 运算符  
  
|Hash\_set 版本|Hash\_multiset 版本|说明|  
|------------------|-----------------------|--------|  
|[operator\!\= \(hash\_set\)](../Topic/operator!=%20\(hash_set\).md)|[operator\!\= \(hash\_multiset\)](../Topic/operator!=%20\(hash_multiset\).md)|测试运算符左侧的 hash\_set 或 hash\_multiset 对象是否不等于右侧的 hash\_set 或 hash\_multiset 对象。|  
|[operator\=\= \(hash\_set\)](http://msdn.microsoft.com/zh-cn/791b95bd-f917-4716-aea6-add50badbfac)|[operator\=\= \(hash\_multiset\)](http://msdn.microsoft.com/zh-cn/cfa9aa0c-d5f6-403a-9441-35c2a4cee0fb)|测试运算符左侧的 hash\_set 或 hash\_multiset 对象是否等于右侧的 hash\_set 或 hash\_multiset 对象。|  
  
### 专用化模板函数  
  
|Hash\_set 版本|Hash\_multiset 版本|描述|  
|------------------|-----------------------|--------|  
|[swap \(hash\_set\)](../Topic/swap%20\(hash_set\).md)|[swap \(hash\_multiset\)](../Topic/swap%20\(hash_multiset\).md)|交换两个 hash\_set 或 hash\_multiset 的元素。|  
  
### 类  
  
|||  
|-|-|  
|[hash\_compare 类](../standard-library/hash-compare-class.md)|描述了一个对象，任何哈希关联容器（hash\_map、hash\_multimap、hash\_set 或 hash\_multiset）都可将该对象用作默认的 **Traits** 参数对象，以对其所包含的元素进行排序和哈希处理。|  
|[hash\_set 类](../standard-library/hash-set-class.md)|用于存储和快速检索集合中的数据，此集合中包含的元素值是唯一的并且用作键值。|  
|[hash\_multiset 类](../standard-library/hash-multiset-class.md)|用于存储和快速检索集合中的数据，此集合中包含的元素值是唯一的并且用作键值。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)