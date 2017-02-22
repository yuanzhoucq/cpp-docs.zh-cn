---
title: "insert_iterator 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::insert_iterator"
  - "iterator/std::insert_iterator"
  - "std.insert_iterator"
  - "insert_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert_iterator 类"
  - "insert_iterator 类, 语法"
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# insert_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述满足输出迭代器要求的迭代器适配器。  它是将元素插入到序列而不是覆盖，因此不同于 C\+\+ 序列和关联容器的迭代器所提供的覆盖语义，它可以提供不同的语义。  `insert_iterator` 类会针对要适配的容器类型进行模板化。  
  
## 语法  
  
```  
template <class Container> class insert_iterator;  
```  
  
#### 参数  
 `Container`  
 要通过 `insert_iterator` 将元素插入其中的容器类型。  
  
## 备注  
 **Container** 类型的容器必须满足可变大小容器的要求，并具有一个双实际参数插入成员函数，其中，形式参数分别为 **Container::iterator** 类型和 **Container::value\_type** 类型，将返回 **Container::iterator** 类型。  标准模板库序列和排序关联容器符合这些要求，可以进行适配以便用于 `insert_iterator`。  对于关联容器，位置参数将被当做提示来处理，有可能会提高或降低性能，具体取决于该提示的好坏。  `insert_iterator` 必须使用其容器进行初始化。  
  
### 构造函数  
  
|||  
|-|-|  
|[insert\_iterator](../Topic/insert_iterator::insert_iterator.md)|构造一个 `insert_iterator`，以便将元素插入到容器中的指定位置。|  
  
### Typedef  
  
|||  
|-|-|  
|[container\_type](../Topic/insert_iterator::container_type.md)|一种类型，代表要对其执行泛型插入的容器。|  
|[reference](../Topic/insert_iterator::reference.md)|一种类型，此类型提供对关联容器所控制序列中的元素的引用。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\*](../Topic/insert_iterator::operator*.md)|解引用运算符，用于实现泛型插入的输出迭代器表达式 \*`i` \= `x`。|  
|[operator\+\+](../Topic/insert_iterator::operator++.md)|将 `insert_iterator` 递增到下一个可用来存储值的位置。|  
|[operator\=](../Topic/insert_iterator::operator=.md)|赋值运算符，用于实现泛型插入的输出迭代器表达式 \*`i` \= `x`。|  
  
## 要求  
 **标头**：\<iterator\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)