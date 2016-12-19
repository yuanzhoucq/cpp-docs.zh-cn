---
title: "forward_list 类 | Microsoft Docs"
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
  - "std::forward_list"
  - "forward_list"
  - "forward_list/std::forward_list"
  - "std.forward_list"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "forward_list 类"
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
caps.latest.revision: 25
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# forward_list 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述用于控制变长元素序列的对象。  序列存储为节点的单向链接列表，其中每个节点都包含 `Type` 类型的成员。  
  
## 语法  
  
```  
template<  
    class Type,   
    class Allocator = allocator<Type>   
>  
class forward_list   
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`Type`|要存储在 forward\_list 中的元素数据类型。|  
|`Allocator`|存储的分配器对象，用于封装有关 forward\_list 的内存分配和解除分配的详细信息。  此参数可选。  默认值为 allocator\<`Type`\>。|  
  
## 备注  
 `forward_list` 对象通过 `Allocator` 类的存储对象（基于 [allocator 类](../standard-library/allocator-class.md)，通常称为`std::allocator)`）分配和释放它所控制序列的存储。  有关详细信息，请参阅[Allocators](../standard-library/allocators.md)。  分配器对象必须与 `allocator` 模板类的对象具有相同的外部接口。  
  
> [!NOTE]
>  分配容器对象时，不会复制存储的分配器对象。  
  
 通过 `forward_list` 擦除迭代器、指针和引用所控制序列的元素时，这些迭代器、指针和引用可能失效。  通过 `forward_list` 对受控序列执行插入和接合操作不会使迭代器失效。  
  
 调用 [forward\_list::insert\_after](../Topic/forward_list::insert_after.md)（它是可调用构造函数 `Type(const _Type&)` 的唯一成员函数）时，可能会添加受控序列。  `forward_list` 也可能调用移动构造函数。  如果此类表达式引发异常，则容器对象不插入任何新元素，并重新引发该异常。  因此，发生这类异常时，模板类 `forward_list` 的对象仍处于已知状态。  
  
### 构造函数  
  
|||  
|-|-|  
|[forward\_list](../Topic/forward_list::forward_list.md)|构造 `forward_list` 类型的对象。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/forward_list::allocator_type.md)|一种类型，用于表示转发列表对象的分配器类。|  
|[const\_iterator](../Topic/forward_list::const_iterator.md)|一种类型，用于为转发列表提供常量迭代器。|  
|[const\_pointer](../Topic/forward_list::const_pointer.md)|一种类型，用于提供指向转发列表中的 `const` 元素的指针。|  
|[const\_reference](../Topic/forward_list::const_reference.md)|一种类型，用于提供对转发列表中元素的常量引用。|  
|[difference\_type](../Topic/forward_list::difference_type.md)|一种有符号整数类型，可用于表示转发列表中某个范围类迭代器所指向元素之间的元素数目。|  
|[iterator](../Topic/forward_list::iterator.md)|一种类型，用于为转发列表提供迭代器。|  
|[指针](../Topic/forward_list::pointer.md)|一种类型，用于提供指向转发列表中元素的指针。|  
|[引用](../Topic/forward_list::reference.md)|一种类型，用于提供对转发列表中元素的引用。|  
|[size\_type](../Topic/forward_list::size_type.md)|一种类型，用于表示两个元素之间的无符号距离。|  
|[value\_type](../Topic/forward_list::value_type.md)|一种类型，用于表示转发列表中存储的元素的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[assign](../Topic/forward_list::assign.md)|清除转发列表中的元素，并将一组新的元素复制到目标转发列表。|  
|[before\_begin](../Topic/forward_list::before_begin.md)|返回寻址转发列表中第一个元素之前的位置的迭代器。|  
|[begin](../Topic/forward_list::begin.md)|返回寻址转发列表中第一个元素的迭代器。|  
|[cbefore\_begin](../Topic/forward_list::cbefore_begin.md)|返回寻址转发列表中第一个元素之前的位置的常量迭代器。|  
|[cbegin](../Topic/forward_list::cbegin.md)|返回寻址转发列表中第一个元素的常量迭代器。|  
|[cend](../Topic/forward_list::cend.md)|返回寻址转发列表中最后一个元素之后的位置的常量迭代器。|  
|[清除](../Topic/forward_list::clear.md)|清除转发列表中的所有元素。|  
|[emplace\_after](../Topic/forward_list::emplace_after.md)|在指定位置之后移动构造新元素。|  
|[emplace\_front](../Topic/forward_list::emplace_front.md)|在列表的起始位置添加一个就地构造的元素。|  
|[空](../Topic/forward_list::empty.md)|测试转发列表是否为空。|  
|[end](../Topic/forward_list::end.md)|返回寻址转发列表中最后一个元素之后的位置的迭代器。|  
|[erase\_after](../Topic/forward_list::erase_after.md)|删除转发列表中指定位置之后的元素。|  
|[front](../Topic/forward_list::front.md)|返回对转发列表中第一个元素的引用。|  
|[get\_allocator](../Topic/forward_list::get_allocator.md)|返回用于构造转发列表的分配器对象的一个副本。|  
|[insert\_after](../Topic/forward_list::insert_after.md)|在转发列表中的指定位置之后添加元素。|  
|[max\_size](../Topic/forward_list::max_size.md)|返回转发列表的最大长度。|  
|[合并](../Topic/forward_list::merge.md)|将元素从参数列表中删除，将它们插入目标转发列表，将新的组合元素集以升序或其他指定顺序排序。|  
|[pop\_front](../Topic/forward_list::pop_front.md)|删除转发列表起始处的一个元素。|  
|[push\_front](../Topic/forward_list::push_front.md)|在转发列表起始处添加一个元素。|  
|[remove](../Topic/forward_list::remove.md)|清除转发列表中与指定值匹配的元素。|  
|[remove\_if](../Topic/forward_list::remove_if.md)|将满足指定谓词的元素从转发列表中清除。|  
|[调整大小](../Topic/forward_list::resize.md)|为转发列表指定新的大小。|  
|[reverse](../Topic/forward_list::reverse.md)|颠倒转发列表中元素的顺序。|  
|[sort](../Topic/forward_list::sort.md)|按升序或按谓词指定的顺序排列元素。|  
|[splice\_after](../Topic/forward_list::splice_after.md)|重新联结节点间的链接。|  
|[swap](../Topic/forward_list::swap.md)|交换两个转发列表的元素。|  
|[unique](../Topic/forward_list::unique.md)|删除通过了指定测试的相邻元素。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../Topic/forward_list::operator=.md)|将转发列表的元素替换为另一个转发列表的副本。|  
  
## 要求  
 **标头：**\<forward\_list\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<forward\_list\>](../standard-library/forward-list.md)