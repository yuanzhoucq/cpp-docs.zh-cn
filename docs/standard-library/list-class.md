---
title: "list 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.list"
  - "list"
  - "std::list"
  - "list/std::list"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "list 类"
ms.assetid: d3707f4a-10fd-444f-b856-f9ca2077c1cd
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# list 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL 列表类是序列容器的一个模板类，用于将它们的元素保持为线性排列，并允许在序列的任何位置高效插入和删除。  序列存储为双向链接的元素列表，每个包含一些 *Type* 类型的成员。  
  
## 语法  
  
```cpp  
  
template <    class Type,     class Allocator=allocator<Type>  > class list  
```  
  
#### 参数  
 *类型*  
 要存储在列表中的元素数据类型。  
  
 `Allocator`  
 表示所存储分配器对象的类型，该分配器对象封装有关列表的内存分配和解除分配的详细信息。  这个参数的值是可选的，它的默认值是 **allocator**\<*Type*\>*。*  
  
## 备注  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。  当对任何元素的随机访问超出限制并且仅要求在序列的末尾插入或删除元素时，矢量应作为用于管理序列的首选容器。  当需要随机访问并且在序列起始处和末尾处插入和删除元素已到达极限时，应首选类 deque 容器进行操作。  
  
 列表成员函数 [merge](../Topic/list::merge.md)、[reverse](../Topic/list::reverse.md)、[unique](../Topic/list::unique.md)、[remove](../Topic/list::remove.md) 和 [remove\_if](../Topic/list::remove_if.md) 已针对对列表的操作进行了优化，它们可作为泛型对应函数的高性能替代函数。  
  
 当成员函数必须插入或删除列表中的元素时，将发生列表的重新分配。  在所有这类情况下，仅指向受控制序列被消除部分的迭代器或引用将变为无效。  
  
 包括 STL 标准标头 \<list\>，以定义 [container](../standard-library/stl-containers.md) 模板类列表和多个支持模板。  
  
### 构造函数  
  
|||  
|-|-|  
|[list](../Topic/list::list.md)|构造一个列表，它具有特定大小或它的元素具有特定值，或具有特定 `allocator` 或作为某个其他列表副本。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/list::allocator_type.md)|表示列表对象的 `allocator` 类的类型。|  
|[const\_iterator](../Topic/list::const_iterator.md)|提供可读取列表中 `const` 元素的双向迭代器的类型。|  
|[const\_pointer](../Topic/list::const_pointer.md)|提供指向列表中 `const` 元素的指针的类型。|  
|[const\_reference](../Topic/list::const_reference.md)|提供对存储于列表中供读取和执行 `const` 操作的 `const` 元素的引用的类型。|  
|[const\_reverse\_iterator](../Topic/list::const_reverse_iterator.md)|提供可读取列表中任何 `const` 元素的双向迭代器的类型。|  
|[difference\_type](../Topic/list::difference_type.md)|提供引用同一列表中的元素的两个迭代器之间的差异的类型。|  
|[iterator](../Topic/list::iterator.md)|提供可读取或修改列表中任何元素的双向迭代器的类型。|  
|[指针](../Topic/list::pointer.md)|提供指向列表中元素的指针的类型。|  
|[reference](../Topic/list::reference.md)|提供对存储于列表中供读取和执行 `const` 操作的 `const` 元素的引用的类型。|  
|[reverse\_iterator](../Topic/list::reverse_iterator.md)|提供可读取或修改反向列表中的元素的双向迭代器的类型。|  
|[size\_type](../Topic/list::size_type.md)|计算列表中元素的数目的类型。|  
|[value\_type](../Topic/list::value_type.md)|表示列表中存储的数据类型的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[assign](../Topic/list::assign.md)|将元素从列表中擦除并将一组新的元素复制到目标列表。|  
|[back](../Topic/list::back.md)|返回对列表中最后一个元素的引用。|  
|[begin](../Topic/list::begin.md)|返回发现列表中第一个元素的位置的迭代器。|  
|[list::cbegin](../Topic/list::cbegin.md)|返回发现列表中第一个元素的位置的常量迭代器。|  
|[list::cend](../Topic/list::cend.md)|返回发现一个列表中最后一个元素之后的位置的敞亮表达式。|  
|[list::clear](../Topic/list::clear.md)|消除列表中的全部元素。|  
|[list::crbegin](../Topic/list::crbegin.md)|返回发现反向列表中第一个元素的位置的常量迭代器。|  
|[list::crend](../Topic/list::crend.md)|返回用于发现反向列表中最后一个元素之后的位置的常量迭代器。|  
|[list::emplace](../Topic/list::emplace.md)|将构造的元素插入到列表中的指定位置。|  
|[list::emplace\_back](../Topic/list::emplace_back.md)|在列表的结尾处添加一个就地构造的元素。|  
|[list::emplace\_front](../Topic/list::emplace_front.md)|在列表的起始位置添加一个就地构造的元素。|  
|[empty](../Topic/list::empty.md)|测试列表是否为空。|  
|[end](../Topic/list::end.md)|返回用于发现列表中最后一个元素之后的位置的迭代器。|  
|[erase](../Topic/list::erase.md)|从列表中的指定位置移除一个或一系列元素。|  
|[front](../Topic/list::front.md)|返回对列表中第一个元素的引用。|  
|[get\_allocator](../Topic/list::get_allocator.md)|返回用于构造列表的 `allocator` 对象的一个副本。|  
|[insert](../Topic/list::insert.md)|将一个、几个或一系列元素插入列表中的指定位置。|  
|[max\_size](../Topic/list::max_size.md)|返回列表的最大长度。|  
|[merge](../Topic/list::merge.md)|将元素从参数列表移除，将它们插入目标列表，将新的组合元素集以升序或其他指定顺序排序。|  
|[pop\_back](../Topic/list::pop_back.md)|删除列表末尾的元素。|  
|[pop\_front](../Topic/list::pop_front.md)|删除列表起始处的一个元素。|  
|[push\_back](../Topic/list::push_back.md)|在列表的末尾添加元素。|  
|[push\_front](../Topic/list::push_front.md)|在列表的开头添加元素。|  
|[rbegin](../Topic/list::rbegin.md)|返回发现反向列表中第一个元素的位置的迭代器。|  
|[remove](../Topic/list::remove.md)|清除列表中与指定值匹配的元素。|  
|[remove\_if](../Topic/list::remove_if.md)|将满足指定谓词的元素从列表中消除。|  
|[rend](../Topic/list::rend.md)|返回发现反向列表中最后一个元素之后的位置的迭代器。|  
|[resize](../Topic/list::resize.md)|为列表指定新的大小。|  
|[reverse](../Topic/list::reverse.md)|反转列表中元素的顺序。|  
|[size](../Topic/list::size.md)|返回列表中元素的数目。|  
|[sort](../Topic/list::sort.md)|按升序或其他顺序关系排列列表中的元素。|  
|[splice](../Topic/list::splice.md)|将元素从参数列表中删除或将它们插入目标列表。|  
|[swap](../Topic/list::swap.md)|交换两个列表的元素。|  
|[unique](../Topic/list::unique.md)|从列表中删除满足某些其他二元谓词的相邻重复元素或相邻元素。|  
  
### 运算符  
  
|||  
|-|-|  
|[list::operator\=](../Topic/list::operator=.md)|用另一个列表的副本替换列表中的元素。|  
  
## 要求  
 **标头**：\<list\>  
  
## 请参阅  
 [\<list\>](../standard-library/list.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)