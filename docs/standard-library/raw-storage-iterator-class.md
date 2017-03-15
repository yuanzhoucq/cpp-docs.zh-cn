---
title: "raw_storage_iterator 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::raw_storage_iterator"
  - "raw_storage_iterator"
  - "std.raw_storage_iterator"
  - "memory/std::raw_storage_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "raw_storage_iterator 类"
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# raw_storage_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一种所提供的适配器类，使算法能够将它们的结果存储到未初始化的内存中。  
  
## 语法  
  
```  
  
        template <class   
        OutputIterator,  
         class   
        Type>  
class raw_storage_iterator  
```  
  
#### 参数  
 `OutputIterator`  
 为正被存储的对象指定输出迭代器。  
  
 *类型*  
 正为其分配存储的对象的类型。  
  
## 备注  
 此类描述一个输出迭代器，该迭代器在它生成的序列中构造**“Type”**类型的对象。  类 `raw_storage_iterator`\<**ForwardIterator**, **Type**\> 的对象通过构造该对象时指定的 **ForwardIterator** 类的向前迭代器对象来访问存储。  对于类 **ForwardIterator** 的第一个对象，表达式 **&\*first** 必须为生成序列中的下一个对象（属于**“Type”**类型）指定未构造的存储。  
  
 在需要分隔内存分配和对象构造时使用此适配器类。  `raw_storage_iterator` 可用于将对象复制到未初始化的存储中，如使用 `malloc` 函数分配的内存。  
  
## 成员  
  
### 构造函数  
  
|||  
|-|-|  
|[raw\_storage\_iterator](../Topic/raw_storage_iterator::raw_storage_iterator.md)|使用指定的基础输出迭代器构造原始存储迭代器。|  
  
### Typedef  
  
|||  
|-|-|  
|[element\_type](../Topic/raw_storage_iterator::element_type.md)|提供一种类型，该类型描述要存储在原始存储迭代器中的元素。|  
|[iter\_type](../Topic/raw_storage_iterator::iter_type.md)|提供了一种类型，该类型描述原始存储迭代器所基于的迭代器。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\*](../Topic/raw_storage_iterator::operator*.md)|用于实现输出迭代器表达式 \*`ii` \= `x` 的取消引用运算符。|  
|[operator \=](../Topic/raw_storage_iterator::operator=.md)|用于实现原始存储迭代器表达式 \*`i` \= `x` 以便在内存中进行存储的赋值运算符。|  
|[operator\+\+](../Topic/raw_storage_iterator::operator++.md)|原始存储迭代器的前置递增和后置递增运算符。|  
  
## 要求  
 **标头：**\<memory\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)