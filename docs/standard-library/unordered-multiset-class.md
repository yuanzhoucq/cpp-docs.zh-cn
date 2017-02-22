---
title: "unordered_multiset 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1::unordered_multiset"
  - "std::tr1::unordered_multiset"
  - "unordered_multiset"
  - "std.tr1.unordered_multiset"
  - "unordered_set/std::tr1::unordered_multiset"
  - "tr1.unordered_multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unordered_multiset 类"
  - "unordered_multiset 类 [TR1]"
ms.assetid: 70c8dfc5-492a-4af2-84f5-1aa9cb04b71c
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# unordered_multiset 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述用于控制 `const Key` 类型的变长元素序列的对象。  序列由哈希函数弱排序，哈希函数将此序列分区到称为存储桶的有序序列集中。  在每个存储桶中，比较函数将确定任一元素对是否具有等效顺序。  每个元素同时用作排序键和值。  序列以允许查找、插入和移除任意元素的方式表示，并包含与序列中的元素数量无关的多个操作（常量时间），至少在所有存储桶长度大致相等时如此。  在最坏情况下，当所有元素位于一个存储桶中时，操作数量与序列中的元素数量成比例（线性时间）。  此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。  
  
## 语法  
  
```  
template<class Key,  
    class Hash = std::hash<Key>,  
    class Pred = std::equal_to<Key>,  
    class Alloc = std::allocator<Key> >  
    class unordered_multiset;  
```  
  
#### 参数  
  
|||  
|-|-|  
|参数|说明|  
|`Key`|键类型。|  
|`Hash`|哈希函数对象类型。|  
|`Pred`|相等比较函数对象类型。|  
|`Alloc`|分配器类。|  
  
## 成员  
  
|||  
|-|-|  
|类型定义|说明|  
|[unordered\_multiset::allocator\_type](../Topic/unordered_multiset::allocator_type.md)|用于管理存储的分配器的类型。|  
|[unordered\_multiset::const\_iterator](../Topic/unordered_multiset::const_iterator.md)|受控序列的常量迭代器的类型。|  
|[unordered\_multiset::const\_local\_iterator](../Topic/unordered_multiset::const_local_iterator.md)|受控序列的常量存储桶迭代器的类型。|  
|[unordered\_multiset::const\_pointer](../Topic/unordered_multiset::const_pointer.md)|元素的常量指针的类型。|  
|[unordered\_multiset::const\_reference](../Topic/unordered_multiset::const_reference.md)|元素的常量引用的类型。|  
|[unordered\_multiset::difference\_type](../Topic/unordered_multiset::difference_type.md)|两个元素间的带符号距离的类型。|  
|[unordered\_multiset::hasher](../Topic/unordered_multiset::hasher.md)|哈希函数的类型。|  
|[unordered\_multiset::iterator](../Topic/unordered_multiset::iterator.md)|受控序列的迭代器的类型。|  
|[unordered\_multiset::key\_equal](../Topic/unordered_multiset::key_equal.md)|比较函数的类型。|  
|[unordered\_multiset::key\_type](../Topic/unordered_multiset::key_type.md)|排序键的类型。|  
|[unordered\_multiset::local\_iterator](../Topic/unordered_multiset::local_iterator.md)|受控序列的存储桶迭代器的类型。|  
|[unordered\_multiset::pointer](../Topic/unordered_multiset::pointer.md)|元素的指针的类型。|  
|[unordered\_multiset::reference](../Topic/unordered_multiset::reference.md)|元素的引用的类型。|  
|[unordered\_multiset::size\_type](../Topic/unordered_multiset::size_type.md)|两个元素间的无符号距离的类型。|  
|[unordered\_multiset::value\_type](../Topic/unordered_multiset::value_type.md)|元素的类型。|  
  
|||  
|-|-|  
|成员函数|说明|  
|[unordered\_multiset::begin](../Topic/unordered_multiset::begin.md)|指定受控序列的开头。|  
|[unordered\_multiset::bucket](../Topic/unordered_multiset::bucket.md)|获取键值的存储桶编号。|  
|[unordered\_multiset::bucket\_count](../Topic/unordered_multiset::bucket_count.md)|获取存储桶数。|  
|[unordered\_multiset::bucket\_size](../Topic/unordered_multiset::bucket_size.md)|获取存储桶的大小。|  
|[unordered\_multiset::cbegin](../Topic/unordered_multiset::cbegin.md)|指定受控序列的开头。|  
|[unordered\_multiset::cend](../Topic/unordered_multiset::cend.md)|指定受控序列的末尾。|  
|[unordered\_multiset::clear](../Topic/unordered_multiset::clear.md)|移除所有元素。|  
|[unordered\_multiset::count](../Topic/unordered_multiset::count.md)|查找与指定键匹配的元素数。|  
|[unordered\_multiset::emplace](../Topic/unordered_multiset::emplace.md)|添加就地构造的元素。|  
|[unordered\_multiset::emplace\_hint](../Topic/unordered_multiset::emplace_hint.md)|添加就地构造的元素，附带提示。|  
|[unordered\_multiset::empty](../Topic/unordered_multiset::empty.md)|测试元素是否存在。|  
|[unordered\_multiset::end](../Topic/unordered_multiset::end.md)|指定受控序列的末尾。|  
|[unordered\_multiset::equal\_range](../Topic/unordered_multiset::equal_range.md)|查找与指定键匹配的范围。|  
|[unordered\_multiset::erase](../Topic/unordered_multiset::erase.md)|移除指定位置处的元素。|  
|[unordered\_multiset::find](../Topic/unordered_multiset::find.md)|查找与指定键匹配的元素。|  
|[unordered\_multiset::get\_allocator](../Topic/unordered_multiset::get_allocator.md)|获取存储的分配器对象。|  
|[unordered\_multiset::hash\_function](../Topic/unordered_multiset::hash_function.md)|获取存储的哈希函数对象。|  
|[unordered\_multiset::insert](../Topic/unordered_multiset::insert.md)|添加元素。|  
|[unordered\_multiset::key\_eq](../Topic/unordered_multiset::key_eq.md)|获取存储的比较函数对象。|  
|[unordered\_multiset::load\_factor](../Topic/unordered_multiset::load_factor.md)|对每个存储桶的平均元素数进行计数。|  
|[unordered\_multiset::max\_bucket\_count](../Topic/unordered_multiset::max_bucket_count.md)|获取最大的存储桶数。|  
|[unordered\_multiset::max\_load\_factor](../Topic/unordered_multiset::max_load_factor.md)|获取或设置每个存储桶的最多元素数。|  
|[unordered\_multiset::max\_size](../Topic/unordered_multiset::max_size.md)|获取受控序列的最大大小。|  
|[unordered\_multiset::rehash](../Topic/unordered_multiset::rehash.md)|重新生成哈希表。|  
|[unordered\_multiset::size](../Topic/unordered_multiset::size.md)|对元素数进行计数。|  
|[unordered\_multiset::swap](../Topic/unordered_multiset::swap.md)|交换两个容器的内容。|  
|[unordered\_multiset::unordered\_multiset](../Topic/unordered_multiset::unordered_multiset.md)|构造容器对象。|  
  
|||  
|-|-|  
|运算符|说明|  
|[unordered\_multiset::operator\=](../Topic/unordered_multiset::operator=.md)|复制哈希表。|  
  
## 备注  
 对象通过调用两个存储对象，即一个 [unordered\_multiset::key\_equal](../Topic/unordered_multiset::key_equal.md) 类型的比较函数对象和一个 [unordered\_multiset::hasher](../Topic/unordered_multiset::hasher.md) 类型的哈希函数对象，对它控制的序列进行排序。  可以通过调用成员函数 [unordered\_multiset::key\_eq](../Topic/unordered_multiset::key_eq.md)`()` 访问第一个存储对象；通过调用成员函数 [unordered\_multiset::hash\_function](../Topic/unordered_multiset::hash_function.md)`()` 访问第二个存储对象。  具体而言，对于所有 `Key` 类型的值 `X` 和 `Y`，`key_eq()(X, Y)` 调用将仅在两个参数值拥有等效顺序时返回 true；`hash_function()(keyval)` 调用将生成 `size_t` 类型的值的分布。  与模板类 [unordered\_set 类](../standard-library/unordered-set-class.md) 不同，模板类 `unordered_multiset` 的对象不确保 `key_eq()(X, Y)` 对于受控序列的任意两个元素始终为 false。（键不需要唯一。）  
  
 此对象还存储最大加载因子，用于指定每个存储桶的元素的最大所需平均数量。  如果插入元素导致 [unordered\_multiset::load\_factor](../Topic/unordered_multiset::load_factor.md)`()` 超出最大加载因子，容器将增加存储桶的数量并根据需要重新生成哈希表。  
  
 受控序列中元素的实际顺序取决于哈希函数、比较函数、插入顺序、最大加载因子和存储桶的当前数量。  通常无法预测受控序列中的元素顺序。  但是，可以始终确保具有等效顺序的任何元素子集在受控序列中相邻。  
  
 对象通过 [unordered\_multiset::allocator\_type](../Topic/unordered_multiset::allocator_type.md) 类型的存储分配器对象为其控制的序列分配并释放存储。  此分配器对象必须与 `allocator` 模板类的对象的外部接口相同。  请注意，已分配容器对象时，不复制存储的分配器对象。  
  
## 要求  
 **标头：**\<unordered\_set\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<unordered\_set\>](../standard-library/unordered-set.md)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)