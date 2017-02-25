---
title: "multimap 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "multimap"
  - "std.multimap"
  - "map/std::multimap"
  - "std::multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multimap 类"
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# multimap 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

标准模板库多重映射类用于存储和检索集合中的数据，此集合中的每个元素均为包含数据值和排序键的元素对。  键值不需要唯一，用于自动排序数据。  可以直接更改多重映射中的元素值，但不能直接更改其关联键值。  必须先删除与旧元素关联的键值，才能插入与新元素关联的新键值。  
  
## 语法  
  
```  
template <  
   class Key,   
   class Type,   
   class Traits=less<Key>,   
   class Allocator=allocator<pair <const Key, Type> >   
> class multimap;  
```  
  
#### 参数  
 `Key`  
 要存储在多重映射中的键数据类型。  
  
 `Type`  
 要存储在多重映射中的元素数据类型。  
  
 `Traits`  
 一种提供函数对象的类型，该函数对象可将两个元素值作为排序键进行比较，以确定其在多重映射中的相对顺序。  默认值是二元谓词 `less<Key>`。  
  
 在 C\+\+ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。  有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 一种表示存储的分配器对象的类型，该分配器对象封装有关映射的内存分配和解除分配的详细信息。  此参数为可选参数，默认值为 `allocator<pair <const Key, Type> >`。  
  
## 备注  
 STL 多重映射类是：  
  
-   大小可变的关联容器，支持基于关联键值高效检索元素值。  
  
-   可逆，因为它提供双向迭代器来访问其元素。  
  
-   有序，因为它的元素在容器中根据指定的比较函数按键值排序。  
  
-   多个，它的元素不需要具有唯一键，因此一个键值可具有多个相关联的元素数据值。  
  
-   关联容器对，因为它的元素数据值与其键值不同。  
  
-   模板类，因为它提供的功能是一般性的功能，因此与作为元素或键包含的特定数据类型无关。  用于元素和键的数据类型作为类模板以及比较函数和分配器中的参数指定。  
  
 映射类提供的迭代器是双向迭代器，但类成员函数 [insert](../Topic/multimap::insert.md) 和 [multimap](../Topic/multimap::multimap.md) 具有将较弱输入迭代器作为模板参数的版本，较弱输入迭代器的功能要求比双向迭代器类保证的功能要求更少。  不同的迭代器概念形成一个系列，通过它们的功能优化相关联。  每个迭代器概念有它自己的一套要求，使用这些概念的算法必须根据迭代器类型提供的要求限制它们的假设。  可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。  这是最小的功能集，但足以按有意义的方式提供类成员函数的上下文中的迭代器范围 `[First, Last)`。  
  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。  关联容器针对查找、插入和移除操作进行了优化。  显式支持这些操作的成员函数较为高效，执行这些操作的时间与容器中元素数量的对数平均成比例。  插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。  
  
 当应用程序满足将值与其键关联的条件时，应选择多重映射作为关联容器。  此类结构的模型是关键字排序列表，这些关键字具有提供定义等的关联字符串值，并且并非始终唯一定义。  如果关键字经过唯一定义以使键唯一，则应选择映射作为容器。  另一方面，如果仅存储关键字列表，则应使用集作为正确容器。  如果允许关键字多次出现，则应使用多重集合作为适当的容器结构。  
  
 多重映射通过调用存储的 [key\_compare](../Topic/multimap::key_compare.md) 类型的函数对象，对它控制的序列进行排序。  此存储的对象是比较函数，可通过调用成员函数 [key\_comp](../Topic/multimap::key_comp.md) 访问。  通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。  这将导致在非等效元素之间进行排序。  在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。  二元谓词 `f(x,y)` 是包含两个参数对象（`x` 和 `y`）以及一个返回值（true 或 false）的函数对象。  如果二元谓词具有自反性、反对称性和传递性且等效可传递，对集进行的排序将为严格弱排序，其中两个对象 `x` 和 `y` 定义为在 `f(x,y)` 和 `f(y,x)` 均为 false 时等效。  如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。  
  
 在 C\+\+ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。  有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)  
  
## 成员  
  
### 构造函数  
  
|||  
|-|-|  
|[multimap](../Topic/multimap::multimap.md)|构造一个空的或者是其他某个 `multimap` 的全部或部分副本的 `multimap`。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/multimap::allocator_type.md)|一种类型，此类型表示 `allocator` 对象的 `multimap` 类。|  
|[const\_iterator](../Topic/multimap::const_iterator.md)|一种类型，此类型提供可读取 `const` 中的 `multimap` 元素的双向迭代器。|  
|[const\_pointer](../Topic/multimap::const_pointer.md)|一种类型，此类型提供指向 `const` 中的 `multimap` 元素的指针。|  
|[const\_reference](../Topic/multimap::const_reference.md)|一种类型，此类型提供对存储在 `const` 中的 `multimap` 元素的引用（用于读取和执行 `const` 操作）。|  
|[const\_reverse\_iterator](../Topic/multimap::const_reverse_iterator.md)|一种类型，此类型提供可读取 `const` 中的任何 `multimap` 元素的双向迭代器。|  
|[difference\_type](../Topic/multimap::difference_type.md)|一种有符号整数类型，此类型可用于表示 `multimap` 中迭代器指向的元素间范围内的元素数量。|  
|[iterator](../Topic/multimap::iterator.md)|一种类型，此类型提供引用同一 `multimap` 中的元素的两个迭代器之间的差异。|  
|[key\_compare](../Topic/multimap::key_compare.md)|一种提供函数对象的类型，该函数对象可比较两个排序键以确定 `multimap` 中两个元素的相对顺序。|  
|[key\_type](../Topic/multimap::key_type.md)|一种类型，此类型描述组成 `multimap` 中每个元素的排序键对象。|  
|[mapped\_type](../Topic/multimap::mapped_type.md)|一种类型，此类型表示存储在 `multimap` 中的数据类型。|  
|[指针](../Topic/multimap::pointer.md)|一种类型，此类型提供指向 `const` 中的 `multimap` 元素的指针。|  
|[引用](../Topic/multimap::reference.md)|一种类型，此类型提供对存储在 `multimap` 中的元素的引用。|  
|[reverse\_iterator](../Topic/multimap::reverse_iterator.md)|一种类型，此类型提供可读取或修改反向 `multimap` 中的元素的双向迭代器。|  
|[size\_type](../Topic/multimap::size_type.md)|一种无符号整数类型，此类型提供指向 `const` 中`multimap` 元素的指针。|  
|[value\_type](../Topic/multimap::value_type.md)|一种提供函数对象的类型，该函数对象可将两个元素作为排序键比较以确定它们在 `multimap` 中的相对顺序。|  
  
### 成员函数  
  
|||  
|-|-|  
|[begin](../Topic/multimap::begin.md)|返回一个迭代器，此迭代器用于发现 `multimap` 中的第一个元素。|  
|[cbegin](../Topic/multimap::cbegin.md)|返回一个常量迭代器，此迭代器用于发现 `multimap` 中的第一个元素。|  
|[cend](../Topic/multimap::cend.md)|返回一个常量迭代器，此迭代器用于发现 `multimap` 中最后一个元素之后的位置。|  
|[清除](../Topic/multimap::clear.md)|清除 `multimap` 的所有元素。|  
|[count](../Topic/multimap::count.md)|返回 `multimap` 中其键与指定为参数的键匹配的元素数量。|  
|[crbegin](../Topic/multimap::crbegin.md)|返回一个常量迭代器，此迭代器用于发现反向 `multimap` 中的第一个元素。|  
|[crend](../Topic/multimap::crend.md)|返回一个常量迭代器，此迭代器用于发现反向 `multimap` 中最后一个元素之后的位置。|  
|[emplace](../Topic/multimap::emplace.md)|将就地构造的元素插入到 `multimap`。|  
|[emplace\_hint](../Topic/multimap::emplace_hint.md)|将就地构造的元素插入到 `multimap`，附带位置提示|  
|[空](../Topic/multimap::empty.md)|测试 `multimap` 是否为空。|  
|[end](../Topic/multimap::end.md)|返回一个迭代器，此迭代器用于发现 `multimap` 中最后一个元素之后的位置。|  
|[equal\_range](../Topic/multimap::equal_range.md)|查找其中元素的键与指定值匹配的元素范围。|  
|[erase](../Topic/multimap::erase.md)|从 `multimap` 中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。|  
|[find](../Topic/multimap::find.md)|返回一个迭代器，此迭代器用于发现 `multimap` 中其键与指定键等效的元素的第一个位置。|  
|[get\_allocator](../Topic/multimap::get_allocator.md)|返回用于构造 `allocator` 的 `multimap` 对象的副本。|  
|[插入](../Topic/multimap::insert.md)|将一个元素或元素范围插入到 `multimap`。|  
|[key\_comp](../Topic/multimap::key_comp.md)|检索用于对 `multimap` 中的键进行排序的比较对象副本。|  
|[lower\_bound](../Topic/multimap::lower_bound.md)|返回一个迭代器，此迭代器指向 `multimap` 中其键等于或大于指定键的第一个元素。|  
|[max\_size](../Topic/multimap::max_size.md)|返回 `multimap` 的最大长度。|  
|[rbegin](../Topic/multimap::rbegin.md)|返回一个迭代器，此迭代器用于发现反向 `multimap` 中的第一个元素。|  
|[rend](../Topic/multimap::rend.md)|返回一个迭代器，此迭代器用于发现反向 `multimap` 中最后一个元素之后的位置。|  
|[size](../Topic/multimap::size.md)|返回 `multimap` 中的元素数量。|  
|[swap](../Topic/multimap::swap.md)|交换两个 `multimap` 的元素。|  
|[upper\_bound](../Topic/multimap::upper_bound.md)|返回一个迭代器，此迭代器指向 `multimap` 中其键大于指定键的第一个元素。|  
|[value\_comp](../Topic/multimap::value_comp.md)|此成员函数返回一个函数对象，该函数对象可通过比较 `multimap` 中元素的键值来确定元素顺序。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../Topic/multimap::operator=.md)|将一个 `multimap` 中的元素替换为另一 `multimap` 副本。|  
  
## 要求  
 **标头：**\<map\>  
  
 **命名空间:** std  
  
 \(**key**, **value**\) 对作为 `pair` 类型的对象存储在多重映射中。  此对类需要标头 \<utility\>，\<map\> 自动包括此标头。  
  
## 请参阅  
 [\<map\> Members](http://msdn.microsoft.com/zh-cn/7e8f0bc2-6034-40f6-9d14-76d4cef86308)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)