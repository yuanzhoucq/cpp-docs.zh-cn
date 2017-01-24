---
title: "bidirectional_iterator_tag 结构 | Microsoft Docs"
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
  - "xutility/std::bidirectional_iterator_tag"
  - "std::bidirectional_iterator_tag"
  - "std.bidirectional_iterator_tag"
  - "bidirectional_iterator_tag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bidirectional_iterator_tag 类"
  - "bidirectional_iterator_tag 结构"
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# bidirectional_iterator_tag 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对 **iterator\_category** 函数的返回类型表示双向迭代器的类。  
  
## 语法  
  
```  
  
   struct bidirectional_iterator_tag  
: public forward_iterator_tag {};  
```  
  
## 备注  
 类别选择算法类标记为使用编译标记。  模板函数需要查找其迭代器参数最特定于类别，因此，它能够使用最高效的算法在编译时。  对于 `Iterator` 类型的每个迭代器，必须定义 `iterator_traits`\<`Iterator`\>::**iterator\_category** 是描绘迭代器的行为的最具体的类标记。  
  
 类型与 **迭代器**\<**Iter**\>或**iterator\_category**，在 **Iter** 描述可以服务作为一双向迭代器的一个对象。  
  
## 示例  
 该示例说明如何使用 `bidirectional_iterator_tag`。参见 [random\_access\_iterator\_tag](../standard-library/random-access-iterator-tag-struct.md)  
  
## 要求  
 **头文件：** \<iterator\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [forward\_iterator\_tag 结构](../standard-library/forward-iterator-tag-struct.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)