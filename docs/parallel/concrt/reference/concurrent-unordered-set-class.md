---
title: "concurrent_unordered_set 类 | Microsoft Docs"
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
  - "concurrent_unordered_set/concurrency::concurrent_unordered_set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_unordered_set 类"
ms.assetid: c61f9a9a-4fd9-491a-9251-e300737ecf4b
caps.latest.revision: 12
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# concurrent_unordered_set 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`concurrent_unordered_set` 类是控制安全类型元素的长短不一序列的并发安全容器。   序列以某种方式显示，该方式支持并发安全追加、元素访问、迭代器访问和迭代器遍历操作。  
  
## 语法  
  
```  
template <  
   typename _Key_type,  
   typename _Hasher = std::tr1::hash<_Key_type>,  
   typename _Key_equality = std::equal_to<_Key_type>,  
   typename _Allocator_type = std::allocator<_Key_type>  
>  
, typename _Key_equality = std::equal_to<_Key_type>, typename _Allocator_type = std::allocator<_Key_type> > class concurrent_unordered_set : public details::_Concurrent_hash< details::_Concurrent_unordered_set_traits<_Key_type, details::_Hash_compare<_Key_type, _Hasher, _Key_equality>, _Allocator_type, false> >;  
```  
  
#### 参数  
 `_Key_type`  
 键类型。  
  
 `_Hasher`  
 哈希函数对象类型。  该参数是可选的并且默认值为 `std::tr1::hash<``_Key_type``>`。  
  
 `_Key_equality`  
 相等比较函数对象类型。  该参数是可选的并且默认值为 `std::equal_to<``_Key_type``>`。  
  
 `_Allocator_type`  
 表示存储分配器对象的类型，该对象封装有关为并发无序集合分配和解除分配内存的详细信息。  该参数是可选的并且默认值为 `std::allocator<``_Key_type``>`。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|描述|  
|--------|--------|  
|`allocator_type`|用于管理存储的分配器的类型。|  
|`const_iterator`|受控序列的常量迭代器的类型。|  
|`const_local_iterator`|受控序列的常量存储桶迭代器的类型。|  
|`const_pointer`|元素的常量指针的类型。|  
|`const_reference`|元素的常量引用的类型。|  
|`difference_type`|两个元素间的带符号距离的类型。|  
|`hasher`|哈希函数的类型。|  
|`iterator`|受控序列的迭代器的类型。|  
|`key_equal`|比较函数的类型。|  
|`key_type`|排序键的类型。|  
|`local_iterator`|受控序列的存储桶迭代器的类型。|  
|`pointer`|元素的指针的类型。|  
|`reference`|元素的引用的类型。|  
|`size_type`|两个元素间的无符号距离的类型。|  
|`value_type`|元素的类型。|  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[concurrent\_unordered\_set::concurrent\_unordered\_set 构造函数](../Topic/concurrent_unordered_set::concurrent_unordered_set%20Constructor.md)|已重载。  构造并发无序的集合。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[concurrent\_unordered\_set::hash\_function 方法](../Topic/concurrent_unordered_set::hash_function%20Method.md)|返回存储的哈希函数对象。|  
|[concurrent\_unordered\_set::insert 方法](../Topic/concurrent_unordered_set::insert%20Method.md)|已重载。  将元素添加到 `concurrent_unordered_set` 对象。|  
|[concurrent\_unordered\_set::key\_eq 方法](../Topic/concurrent_unordered_set::key_eq%20Method.md)|返回存储的相等比较函数对象。|  
|[concurrent\_unordered\_set::swap 方法](../Topic/concurrent_unordered_set::swap%20Method.md)|交换两个 `concurrent_unordered_set` 对象的内容。  此方法不是并发安全方法。|  
|[concurrent\_unordered\_set::unsafe\_erase 方法](../Topic/concurrent_unordered_set::unsafe_erase%20Method.md)|已重载。  移除指定位置处的 `concurrent_unordered_set` 元素。  此方法不是并发安全方法。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[concurrent\_unordered\_set::operator\= 运算符](../Topic/concurrent_unordered_set::operator=%20Operator.md)|已重载。  将另一 `concurrent_unordered_set` 对象的内容分配到此对象中。  此方法不是并发安全方法。|  
  
## 备注  
 有关 `concurrent_unordered_set` 类的详细信息，请参见 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 继承层次结构  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_set`  
  
## 要求  
 **头文件：**concurrent\_unordered\_set.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)