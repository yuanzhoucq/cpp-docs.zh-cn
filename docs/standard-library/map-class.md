---
title: "map 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::map"
  - "map/std::map"
  - "map"
  - "std.map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "map 类"
ms.assetid: 7876f4c9-ebb4-4878-af1e-09364c43af0a
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# map 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于存储和检索集合中的数据，此集合中的每个元素均为包含数据值和排序键的元素对。  键的值是唯一的，用于自动排序数据。  
  
 可以直接更改映射中的元素值。  键值是常量，不能更改。  必须先删除与旧元素关联的键值，才能为新元素插入新键值。  
  
## 语法  
  
```  
template <  
   class Key,   
   class Type,   
   class Traits = less<Key>,   
   class Allocator=allocator<pair <const Key, Type> >   
> class map;  
```  
  
#### 参数  
 `Key`  
 要存储在映射中的键数据类型。  
  
 `Type`  
 要存储在映射中的元素数据类型。  
  
 `Traits`  
 一种提供函数对象的类型，该函数对象可将两个元素值作为排序键进行比较，以确定其在映射中的相对顺序。  此参数为可选参数，默认值是二元谓词 `less<``Key``>`。  
  
 在 C\+\+ 14 中可以通过指定没有类型参数的 std:: less \<\> 谓词来启用异类查找。  有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 一种表示存储的分配器对象的类型，该分配器对象封装有关映射的内存分配和解除分配的详细信息。  此参数为可选参数，默认值为 `allocator<pair` `<const``Key`*,* `Type``> >`。  
  
## 备注  
 标准模板库 \(STL\) 映射类是：  
  
-   大小可变的关联容器，基于关联键值高效检索元素值。  
  
-   可逆，因为它提供双向迭代器来访问其元素。  
  
-   有序，因为它的元素根据指定的比较函数按键值排序。  
  
-   唯一。  因为它的每个元素必须具有唯一键。  
  
-   关联容器对，因为它的元素数据值与其键值不同。  
  
-   模板类，因为它提供的功能是一般性的功能，与元素或键类型无关。  用于元素和键的数据类型作为类模板以及比较函数和分配器中的参数指定。  
  
 映射类提供的迭代器是双向迭代器，但类成员函数 [insert](../Topic/map::insert.md) 和 [map](../Topic/map::map.md) 具有将较弱输入迭代器作为模板参数的版本，较弱输入迭代器的功能要求少于双向迭代器类保证的功能要求。  不同的迭代器概念通过它们的功能优化相关联。  每个迭代器概念有它自己的一套要求，使用这些概念的算法必须受这些要求的限制。  输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。  
  
 建议你根据应用程序需要的搜索和插入类型选择容器类型。  关联容器针对查找、插入和移除操作进行了优化。  显式支持这些操作的成员函数执行这些操作的最坏情况时间与容器中元素数量的对数成比例。  插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。  
  
 建议你在应用程序满足将值与键关联的条件时，选择映射作为关联容器。  此类结构的模型是关键字排序列表，这些关键字只出现一次，并具有提供定义的关联字符串值。  如果关键字有多个正确定义，则此关键字不唯一，应选择多重映射作为容器。  如果仅存储关键字列表，则应使用集作为适当容器。  如果允许关键字多次出现，则多重集合为适当容器。  
  
 映射通过调用存储的 [key\_compare](../Topic/map::key_compare.md) 类型的函数对象，对它控制的元素进行排序。  此存储的对象是比较函数，可通过调用 [key\_comp](../Topic/map::key_comp.md) 方法访问。  通常，将比较任意两个给当元素，以确定其中一个是否小于另一个或两者是否等效。  比较所有元素后，将创建非等效元素的排序序列。  
  
> [!NOTE]
>  比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。  二元谓词 f\(x,y\) 是包含两个参数对象（x 和 y）以及一个返回值（`true` 或 `false`）的函数对象。  如果二元谓词具有自反性、反对称性和传递性且等效可传递，对集进行的排序将为严格弱排序，当 f\(x,y\) ``  和 f\(y,x\) 为 `false` 时，其中两个对象 x 和 y 定义为等效。  如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。  
>   
>  在 C\+\+ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。  有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)  
  
## 成员  
  
### 构造函数  
  
|||  
|-|-|  
|[map](../Topic/map::map.md)|构造特定大小的列表、包含具有特定值的元素的列表、包含特定 `allocator` 的列表或作为其他某个映射的副本的列表。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/map::allocator_type.md)|映射对象的 `allocator` 类的 typedef。|  
|[const\_iterator](../Topic/map::const_iterator.md)|可读取映射中 `const` 元素的双向迭代器的 typedef。|  
|[const\_pointer](../Topic/map::const_pointer.md)|指向映射中的 `const` 元素的指针的 typedef。|  
|[const\_reference](../Topic/map::const_reference.md)|对存储在映射中的 `const` 元素的引用（用于读取和执行 `const` 操作）的 typedef。|  
|[const\_reverse\_iterator](../Topic/map::const_reverse_iterator.md)|一种类型，此类型提供可读取映射中的任何 `const` 元素的双向迭代器。|  
|[difference\_type](../Topic/map::difference_type.md)|映射中迭代器指向的元素间范围内元素数量的有符号整数 typedef。|  
|[iterator](../Topic/map::iterator.md)|可读取或修改映射中任何元素的双向迭代器的 typedef。|  
|[key\_compare](../Topic/map::key_compare.md)|可比较两个排序键以确定映射中两个元素的相对顺序的函数对象的 typedef。|  
|[key\_type](../Topic/map::key_type.md)|存储在映射内每个元素中的排序键的 typedef。|  
|[mapped\_type](../Topic/map::mapped_type.md)|存储在映射内每个元素中的数据的 typedef。|  
|[指针](../Topic/map::pointer.md)|指向映射中的 `const` 元素的指针的 typedef。|  
|[引用](../Topic/map::reference.md)|对映射中存储的元素的引用的 typedef。|  
|[reverse\_iterator](../Topic/map::reverse_iterator.md)|可读取或修改反向映射中的元素的双向迭代器的 typedef。|  
|[size\_type](../Topic/map::size_type.md)|映射中元素数量的无符号整数 typedef。|  
|[value\_type](../Topic/map::value_type.md)|作为元素存储在映射中的对象类型的 typedef。|  
  
### 成员函数  
  
|||  
|-|-|  
|[在](../Topic/map::at.md)|查找具有指定键值的元素。|  
|[begin](../Topic/map::begin.md)|返回一个迭代器，此迭代器指向映射中的第一个元素。|  
|[cbegin](../Topic/map::cbegin.md)|返回一个常量迭代器，此迭代器指向映射中的第一个元素。|  
|[cend](../Topic/map::cend.md)|返回一个超过末尾常量迭代器。|  
|[清除](../Topic/map::clear.md)|清除映射的所有元素。|  
|[count](../Topic/map::count.md)|返回映射中其键与参数中指定的键匹配的元素数量。|  
|[crbegin](../Topic/map::crbegin.md)|返回一个常量迭代器，此迭代器指向反向映射中的第一个元素。|  
|[crend](../Topic/map::crend.md)|返回一个常量迭代器，此迭代器指向反向映射中最后一个元素之后的位置。|  
|[emplace](../Topic/map::emplace.md)|将就地构造的元素插入到映射。|  
|[emplace\_hint](../Topic/map::emplace_hint.md)|将就地构造的元素插入到映射，附带位置提示。|  
|[空](../Topic/map::empty.md)|如果映射为空，则返回 `true`。|  
|[end](../Topic/map::end.md)|返回超过末尾迭代器。|  
|[equal\_range](../Topic/map::equal_range.md)|返回一对迭代器。  此迭代器对中的第一个迭代器指向 `map` 中其键大于指定键的第一个元素。  此迭代器对中的第二个迭代器指向 `map` 中其键等于或大于指定键的第一个元素。|  
|[erase](../Topic/map::erase.md)|从指定位置移除映射中的元素或元素范围。|  
|[find](../Topic/map::find.md)|返回一个迭代器，此迭代器指向映射中其键与指定键相等的元素的位置。|  
|[get\_allocator](../Topic/map::get_allocator.md)|返回用于构造映射的 `allocator` 对象的副本。|  
|[插入](../Topic/map::insert.md)|将元素或元素范围插入到映射中的指定位置。|  
|[key\_comp](../Topic/map::key_comp.md)|返回用于对映射中的键进行排序的比较对象副本。|  
|[lower\_bound](../Topic/map::lower_bound.md)|返回一个迭代器，此迭代器指向映射中其键值等于或大于指定键的键值的第一个元素。|  
|[max\_size](../Topic/map::max_size.md)|返回映射的最大长度。|  
|[rbegin](../Topic/map::rbegin.md)|返回一个迭代器，此迭代器指向反向映射中的第一个元素。|  
|[rend](../Topic/map::rend.md)|返回一个迭代器，此迭代器指向反向映射中最后一个元素之后的位置。|  
|[size](../Topic/map::size.md)|返回映射中的元素数量。|  
|[swap](../Topic/map::swap.md)|交换两个映射的元素。|  
|[upper\_bound](../Topic/map::upper_bound.md)|返回一个迭代器，此迭代器指向映射中其键值大于指定键的键值的第一个元素。|  
|[value\_comp](../Topic/map::value_comp.md)|检索用于对映射中的元素值进行排序的比较对象副本。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator&#91;&#93;](../Topic/map::operator[].md)|将元素插入到具有指定键值的映射。|  
|[operator \=](../Topic/map::operator=.md)|将一个映射中的元素替换为另一映射副本。|  
  
## 要求  
 **标头：**\<map\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<map\>](http://msdn.microsoft.com/zh-cn/7e8f0bc2-6034-40f6-9d14-76d4cef86308)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)