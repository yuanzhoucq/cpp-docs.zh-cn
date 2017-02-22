---
title: "unordered_set 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.unordered_set"
  - "std::tr1::unordered_set"
  - "unordered_set/std::tr1::unordered_set"
  - "tr1::unordered_set"
  - "unordered_set"
  - "tr1.unordered_set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unordered_set 类"
  - "unordered_set 类 [TR1]"
ms.assetid: ac08084e-05a7-48c0-9ae4-d40c529922dd
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# unordered_set 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述用于控制 `const Key` 类型的变长元素序列的对象。  序列由哈希函数弱排序，哈希函数将此序列分区到称为存储桶的有序序列集中。  在每个存储桶中，比较函数将确定任一元素对是否具有等效顺序。  每个元素同时用作排序键和值。  序列以允许查找、插入和移除任意元素的方式表示，并包含与序列中的元素数量无关的多个操作（常量时间），至少在所有存储桶长度大致相等时如此。  在最坏情况下，当所有元素位于一个存储桶中时，操作数量与序列中的元素数量成比例（线性时间）。  此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。  
  
## 语法  
  
```  
template<class Key,  
    class Hash = std::hash<Key>,  
    class Pred = std::equal_to<Key>,  
    class Alloc = std::allocator<Key> >  
    class unordered_set;  
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
|[unordered\_set::allocator\_type](../Topic/unordered_set::allocator_type.md)|用于管理存储的分配器的类型。|  
|[unordered\_set::const\_iterator](../Topic/unordered_set::const_iterator.md)|受控序列的常量迭代器的类型。|  
|[unordered\_set::const\_local\_iterator](../Topic/unordered_set::const_local_iterator.md)|受控序列的常量存储桶迭代器的类型。|  
|[unordered\_set::const\_pointer](../Topic/unordered_set::const_pointer.md)|元素的常量指针的类型。|  
|[unordered\_set::const\_reference](../Topic/unordered_set::const_reference.md)|元素的常量引用的类型。|  
|[unordered\_set::difference\_type](../Topic/unordered_set::difference_type.md)|两个元素间的带符号距离的类型。|  
|[unordered\_set::hasher](../Topic/unordered_set::hasher.md)|哈希函数的类型。|  
|[unordered\_set::iterator](../Topic/unordered_set::iterator.md)|受控序列的迭代器的类型。|  
|[unordered\_set::key\_equal](../Topic/unordered_set::key_equal.md)|比较函数的类型。|  
|[unordered\_set::key\_type](../Topic/unordered_set::key_type.md)|排序键的类型。|  
|[unordered\_set::local\_iterator](../Topic/unordered_set::local_iterator.md)|受控序列的存储桶迭代器的类型。|  
|[unordered\_set::pointer](../Topic/unordered_set::pointer.md)|元素的指针的类型。|  
|[unordered\_set::reference](../Topic/unordered_set::reference.md)|元素的引用的类型。|  
|[unordered\_set::size\_type](../Topic/unordered_set::size_type.md)|两个元素间的无符号距离的类型。|  
|[unordered\_set::value\_type](../Topic/unordered_set::value_type.md)|元素的类型。|  
  
|||  
|-|-|  
|成员函数|说明|  
|[unordered\_set::begin](../Topic/unordered_set::begin.md)|指定受控序列的开头。|  
|[unordered\_set::bucket](../Topic/unordered_set::bucket.md)|获取键值的存储桶编号。|  
|[unordered\_set::bucket\_count](../Topic/unordered_set::bucket_count.md)|获取存储桶数。|  
|[unordered\_set::bucket\_size](../Topic/unordered_set::bucket_size.md)|获取存储桶的大小。|  
|[unordered\_set::cbegin](../Topic/unordered_set::cbegin.md)|指定受控序列的开头。|  
|[unordered\_set::cend](../Topic/unordered_set::cend.md)|指定受控序列的末尾。|  
|[unordered\_set::clear](../Topic/unordered_set::clear.md)|移除所有元素。|  
|[unordered\_set::count](../Topic/unordered_set::count.md)|查找与指定键匹配的元素数。|  
|[unordered\_set::emplace](../Topic/unordered_set::emplace.md)|添加就地构造的元素。|  
|[unordered\_set::emplace\_hint](../Topic/unordered_set::emplace_hint.md)|添加就地构造的元素，附带提示。|  
|[unordered\_set::empty](../Topic/unordered_set::empty.md)|测试元素是否存在。|  
|[unordered\_set::end](../Topic/unordered_set::end.md)|指定受控序列的末尾。|  
|[unordered\_set::equal\_range](../Topic/unordered_set::equal_range.md)|查找与指定键匹配的范围。|  
|[unordered\_set::erase](../Topic/unordered_set::erase.md)|移除指定位置处的元素。|  
|[unordered\_set::find](../Topic/unordered_set::find.md)|查找与指定键匹配的元素。|  
|[unordered\_set::get\_allocator](../Topic/unordered_set::get_allocator.md)|获取存储的分配器对象。|  
|[unordered\_set::hash\_function](../Topic/unordered_set::hash_function.md)|获取存储的哈希函数对象。|  
|[unordered\_set::insert](../Topic/unordered_set::insert.md)|添加元素。|  
|[unordered\_set::key\_eq](../Topic/unordered_set::key_eq.md)|获取存储的比较函数对象。|  
|[unordered\_set::load\_factor](../Topic/unordered_set::load_factor.md)|对每个存储桶的平均元素数进行计数。|  
|[unordered\_set::max\_bucket\_count](../Topic/unordered_set::max_bucket_count.md)|获取最大的存储桶数。|  
|[unordered\_set::max\_load\_factor](../Topic/unordered_set::max_load_factor.md)|获取或设置每个存储桶的最多元素数。|  
|[unordered\_set::max\_size](../Topic/unordered_set::max_size.md)|获取受控序列的最大大小。|  
|[unordered\_set::rehash](../Topic/unordered_set::rehash.md)|重新生成哈希表。|  
|[unordered\_set::size](../Topic/unordered_set::size.md)|对元素数进行计数。|  
|[unordered\_set::swap](../Topic/unordered_set::swap.md)|交换两个容器的内容。|  
|[unordered\_set::unordered\_set](../Topic/unordered_set::unordered_set.md)|构造容器对象。|  
  
|||  
|-|-|  
|运算符|说明|  
|[unordered\_set::operator\=](../Topic/unordered_set::operator=.md)|复制哈希表。|  
  
## 备注  
 对象通过调用两个存储对象，即一个 [unordered\_set::key\_equal](../Topic/unordered_set::key_equal.md) 类型的比较函数对象和一个 [unordered\_set::hasher](../Topic/unordered_set::hasher.md) 类型的哈希函数对象，对它控制的序列进行排序。  可以通过调用成员函数 [unordered\_set::key\_eq](../Topic/unordered_set::key_eq.md)`()` 访问第一个存储对象；通过调用成员函数 [unordered\_set::hash\_function](../Topic/unordered_set::hash_function.md)`()` 访问第二个存储对象。  具体而言，对于所有 `Key` 类型的值 `X` 和 `Y`，`key_eq()(X, Y)` 调用将仅在两个参数值拥有等效顺序时返回 true；`hash_function()(keyval)` 调用将生成 `size_t` 类型的值的分布。  与模板类 [unordered\_multiset 类](../standard-library/unordered-multiset-class.md) 不同，模板类 `unordered_set` 的对象可确保 `key_eq()(X, Y)` 对于受控序列的任意两个元素始终为 false。（键是唯一的。）  
  
 此对象还存储最大加载因子，用于指定每个存储桶的元素的最大所需平均数量。  如果插入元素导致 [unordered\_set::load\_factor](../Topic/unordered_set::load_factor.md)`()` 超出最大加载因子，容器将增加存储桶的数量并根据需要重新生成哈希表。  
  
 受控序列中元素的实际顺序取决于哈希函数、比较函数、插入顺序、最大加载因子和存储桶的当前数量。  通常无法预测受控序列中的元素顺序。  但是，可以始终确保具有等效顺序的任何元素子集在受控序列中相邻。  
  
 对象通过 [unordered\_set::allocator\_type](../Topic/unordered_set::allocator_type.md) 类型的存储分配器对象为其控制的序列分配并释放存储。  此分配器对象必须与 `allocator` 模板类的对象的外部接口相同。  请注意，已分配容器对象时，不复制存储的分配器对象。  
  
## 要求  
 **标头：**\<unordered\_set\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<unordered\_set\>](../standard-library/unordered-set.md)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)