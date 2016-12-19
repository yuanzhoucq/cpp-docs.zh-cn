---
title: "concurrent_vector 类 | Microsoft Docs"
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
  - "concurrent_vector/Concurrency::concurrent_vector"
  - "concurrent_vector/concurrency::concurrent_vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_vector 类"
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
caps.latest.revision: 21
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# concurrent_vector 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`concurrent_vector` 类是允许对任意元素进行随机访问的序列容器类。  它实现并发安全追加，元素访问、迭代器访问和迭代器遍历操作。  
  
## 语法  
  
```  
template<  
   typename _Ty,  
   class _Ax  
>  
class concurrent_vector: protected details::_Allocator_base<_Ty, _Ax>, private details::_Concurrent_vector_base_v4;  
```  
  
#### 参数  
 `_Ty`  
 要存储在向量中的元素的数据类型。  
  
 `_Ax`  
 表示存储分配器对象的类型，该对象封装有关为并行向量分配和解除分配内存的详细信息。  该参数是可选的并且默认值为 `allocator<``_Ty``>`。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|`allocator_type`|表示适用于并发向量的分配器类的类型。|  
|`const_iterator`|提供可读取并发向量中 `const` 元素的随机访问迭代器的类型。|  
|`const_pointer`|提供指向并发向量中 `const` 元素的指针的类型。|  
|`const_reference`|提供对存储在并发向量中的 `const` 元素的引用从而读取和执行 `const` 操作的类型。|  
|`const_reverse_iterator`|提供可读取并发向量中任意 `const` 元素的随机访问迭代器的类型。|  
|`difference_type`|提供并发向量中两个元素之间符号距离的类型。|  
|`iterator`|提供可读取并发向量中任意元素的随机访问迭代器的类型。  使用迭代器修改元素不是并发安全操作。|  
|`pointer`|提供指向并发向量中元素的指针的类型。|  
|`reference`|提供对存储在并发向量中的元素的引用的类型。|  
|`reverse_iterator`|提供可读取反向并发向量中任意元素的随机访问迭代器的类型。  使用迭代器修改元素不是并发安全操作。|  
|`size_type`|计算并发向量中元素数量的类型。|  
|`value_type`|表示存储在并发中向量的数据类型的类型。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[concurrent\_vector::concurrent\_vector 构造函数](../Topic/concurrent_vector::concurrent_vector%20Constructor.md)|已重载。  构造并发向量。|  
|[concurrent\_vector::~concurrent\_vector 析构函数](../Topic/concurrent_vector::~concurrent_vector%20Destructor.md)|清除所有元素并销毁此并发向量。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[concurrent\_vector::assign 方法](../Topic/concurrent_vector::assign%20Method.md)|已重载。  清除并发向量的元素，并向它分配 `_Item` 的 `_N` 副本，或分配由迭代器范围 \[`_Begin`，`_End`\] 指定的值。  此方法不是并发安全方法。|  
|[concurrent\_vector::at 方法](../Topic/concurrent_vector::at%20Method.md)|已重载。  在并发矢量中的给定索引提供对元素的访问权限。  该方法对于读取操作是并发安全的，并且还增加向量，只要您确保值 `_Index` 小于并发向量的大小。|  
|[concurrent\_vector::back 方法](../Topic/concurrent_vector::back%20Method.md)|已重载。  返回对并发向量中最后一个元素的引用或 `const` 引用。  如果并发向量为空，则返回值未定义。  此方法是并发安全方法。|  
|[concurrent\_vector::begin 方法](../Topic/concurrent_vector::begin%20Method.md)|已重载。  返回指向并发向量开头的类型 `iterator` 或 `const_iterator` 的迭代器。  此方法是并发安全方法。|  
|[concurrent\_vector::capacity 方法](../Topic/concurrent_vector::capacity%20Method.md)|返回无需分配更多内存的情况下并发向量可增长到的最大大小。  此方法是并发安全方法。|  
|[concurrent\_vector::cbegin 方法](../Topic/concurrent_vector::cbegin%20Method.md)|返回指向并发向量开头的类型 `const_iterator` 的迭代器。  此方法是并发安全方法。|  
|[concurrent\_vector::cend 方法](../Topic/concurrent_vector::cend%20Method.md)|返回指向并发向量末尾的类型 `const_iterator` 的迭代器。  此方法是并发安全方法。|  
|[concurrent\_vector::clear 方法](../Topic/concurrent_vector::clear%20Method.md)|清除并发向量中的所有元素。  此方法不是并发安全方法。|  
|[concurrent\_vector::crbegin 方法](../Topic/concurrent_vector::crbegin%20Method.md)|返回指向并发向量开头的类型 `const_reverse_iterator` 的迭代器。  此方法是并发安全方法。|  
|[concurrent\_vector::crend 方法](../Topic/concurrent_vector::crend%20Method.md)|返回指向并发向量末尾的类型 `const_reverse_iterator` 的迭代器。  此方法是并发安全方法。|  
|[concurrent\_vector::empty 方法](../Topic/concurrent_vector::empty%20Method.md)|测试在调用此方法时并发向量是否为空。  此方法是并发安全方法。|  
|[concurrent\_vector::end 方法](../Topic/concurrent_vector::end%20Method.md)|已重载。  返回指向并发向量末尾的类型 `iterator` 或 `const_iterator` 的迭代器。  此方法是并发安全方法。|  
|[concurrent\_vector::front 方法](../Topic/concurrent_vector::front%20Method.md)|已重载。  返回对并发向量中第一个元素的引用或 `const` 引用。  如果并发向量为空，则返回值未定义。  此方法是并发安全方法。|  
|[concurrent\_vector::get\_allocator 方法](../Topic/concurrent_vector::get_allocator%20Method.md)|返回用于构造并发向量的分配器副本。  此方法是并发安全方法。|  
|[concurrent\_vector::grow\_by 方法](../Topic/concurrent_vector::grow_by%20Method.md)|已重载。  通过 `_Delta` 元素增大此并发向量。  此方法是并发安全方法。|  
|[concurrent\_vector::grow\_to\_at\_least 方法](../Topic/concurrent_vector::grow_to_at_least%20Method.md)|增大此并发向量，直到它至少具有 `_N` 元素。  此方法是并发安全方法。|  
|[concurrent\_vector::max\_size 方法](../Topic/concurrent_vector::max_size%20Method.md)|返回并发向量可以保存的最大元素数。  此方法是并发安全方法。|  
|[concurrent\_vector::push\_back 方法](../Topic/concurrent_vector::push_back%20Method.md)|已重载。  将指定项追加到并发向量的末尾。  此方法是并发安全方法。|  
|[concurrent\_vector::rbegin 方法](../Topic/concurrent_vector::rbegin%20Method.md)|已重载。  返回指向并发向量开头的类型 `reverse_iterator` 或 `const_reverse_iterator` 的迭代器。  此方法是并发安全方法。|  
|[concurrent\_vector::rend 方法](../Topic/concurrent_vector::rend%20Method.md)|已重载。  返回指向并发向量末尾的类型 `reverse_iterator` 或 `const_reverse_iterator` 的迭代器。  此方法是并发安全方法。|  
|[concurrent\_vector::reserve 方法](../Topic/concurrent_vector::reserve%20Method.md)|分配足够的空间来增加并发向量以调整 `_N` 的大小，而无需以后分配更多内存。  此方法不是并发安全方法。|  
|[concurrent\_vector::resize 方法](../Topic/concurrent_vector::resize%20Method.md)|已重载。  将并发向量的大小更改为所需大小，根据需要删除或添加元素。  此方法不是并发安全方法。|  
|[concurrent\_vector::shrink\_to\_fit 方法](../Topic/concurrent_vector::shrink_to_fit%20Method.md)|压缩并发向量的内部表示法，以减少碎片并优化使用内存。  此方法不是并发安全方法。|  
|[concurrent\_vector::size 方法](../Topic/concurrent_vector::size%20Method.md)|返回并发向量中的元素数。  此方法是并发安全方法。|  
|[concurrent\_vector::swap 方法](../Topic/concurrent_vector::swap%20Method.md)|交换两个并发向量的内容。  此方法不是并发安全方法。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[concurrent\_vector::operatorOperator](../Topic/concurrent_vector::operatorOperator.md)|已重载。  在并发矢量中的给定索引提供对元素的访问权限。  该方法对于读取操作是并发安全的，并且还增加向量，只要您确保值 `_Index` 小于并发向量的大小。|  
|[concurrent\_vector::operator\= 运算符](../Topic/concurrent_vector::operator=%20Operator.md)|已重载。  将另一 `concurrent_vector` 对象的内容分配到此对象中。  此方法不是并发安全方法。|  
  
## 备注  
 有关 `concurrent_vector` 类的详细信息，请参见 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 继承层次结构  
 `_Concurrent_vector_base_v4`  
  
 `_Allocator_base`  
  
 `concurrent_vector`  
  
## 要求  
 **标头：**concurrent\_vector.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)