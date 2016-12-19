---
title: "output_iterator_tag 结构 | Microsoft Docs"
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
  - "std::output_iterator_tag"
  - "output_iterator_tag"
  - "xutility/std::output_iterator_tag"
  - "std.output_iterator_tag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "output_iterator_tag 类"
  - "output_iterator_tag 结构"
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# output_iterator_tag 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一种为代表输出迭代器的 **iterator\_category** 函数提供返回类型的类。  
  
## 语法  
  
```  
  
struct output_iterator_tag {};  
  
```  
  
## 备注  
 类别标记类的用法与编译算法选择的标记。 模板函数需要查找其迭代器参数的最特定类别，以便它可以在编译时使用最高效的算法。 类型的每个迭代器 `Iterator`, ，`iterator_traits`\<`Iterator`\>**:: iterator\_category** 必须定义的最具体的类别标记，用于描述迭代器的行为。  
  
 类型等同于 **迭代器**\<**Iter**\>**:: iterator\_category** 时 **Iter** 描述一个对象来充当输出迭代器。  
  
 此标记不基于参数化 `value_type` 或 `difference_type` 迭代器，与其他迭代器标记，因为输出迭代器没有任何一个 `value_type` 或 `difference_type`。  
  
## 示例  
 请参阅 [iterator\_traits](../standard-library/iterator-traits-struct.md) 或 [random\_access\_iterator\_tag](../standard-library/random-access-iterator-tag-struct.md) 以举例说明如何使用 **iterator\_tag**s。  
  
## 要求  
 **标头：**\<iterator\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)