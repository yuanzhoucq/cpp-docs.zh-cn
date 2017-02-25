---
title: "forward_iterator_tag 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.forward_iterator_tag"
  - "forward_iterator_tag"
  - "std::forward_iterator_tag"
  - "xutility/std::forward_iterator_tag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "forward_iterator_tag 类"
  - "forward_iterator_tag 结构"
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# forward_iterator_tag 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对 **iterator\_category** 函数的返回类型表示向前迭代器的类。  
  
## 语法  
  
```  
  
   struct forward_iterator_tag  
: public input_iterator_tag {};  
```  
  
## 备注  
 类别选择算法类标记为使用编译标记。  模板函数需要发现与其迭代器参数最具体的类，以便能够使用最高效的算法在编译时。  对于 `Iterator`类型，必须定义了每个迭代器 `iterator_traits`\<`Iterator`\>**::iterator\_category** 是描绘迭代器的行为的最具体的类标记。  
  
 类型与 **迭代器**\<**Iter**\>**::iterator\_categoryIter**，在描述可以服务作为向前迭代器的对象时。  
  
## 示例  
 为有关如何参见 [iterator\_traits](../standard-library/iterator-traits-struct.md) 或 [random\_access\_iterator\_tag](../standard-library/random-access-iterator-tag-struct.md) 使用 **iterator\_tag**。  
  
## 要求  
 **头文件：** \<iterator\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [input\_iterator\_tag 结构](../standard-library/input-iterator-tag-struct.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)