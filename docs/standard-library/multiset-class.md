---
title: "multiset 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::multiset"
  - "set/std::multiset"
  - "std.multiset"
  - "multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multiset 类"
ms.assetid: 630e8c10-0ce9-4ad9-8d79-9e91a600713f
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# multiset 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

标准模板库多重集合类用于存储和检索集合中的数据，此集合中包含的元素值无需唯一，并且用作数据自动排序所依据的键值。  不能直接更改多重集合中元素的键值。  必须先删除旧值，才能插入具有新值的元素。  
  
## 语法  
  
```  
  
        template <  
   class Key,   
   class Compare=less<Key>,   
   class Allocator=allocator<Key>   
>  
class multiset  
```  
  
#### 参数  
 *键*  
 要存储在多重集合中的元素数据类型。  
  
 *比较*  
 一种提供函数对象的类型，该函数对象可将两个元素值作为排序键进行比较，以确定其在多重集合中的相对顺序。  默认值是二元谓词 **less**\<Key\>。  
  
 在 C\+\+ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。  有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 一种表示存储的分配器对象的类型，该分配器对象封装有关多重集合的内存分配和解除分配的详细信息。  默认值是 **allocator***\<Key\>*。  
  
## 备注  
 STL 多重集合类是：  
  
-   大小可变的关联容器，支持基于关联键值高效检索元素值。  
  
-   可逆，因为它提供双向迭代器来访问其元素。  
  
-   有序，因为它的元素在容器中根据指定的比较函数按键值排序。  
  
-   多个，它的元素不需要具有唯一键，因此一个键值可具有多个相关联的元素值。  
  
-   简单的关联容器，因为它的元素值即为它的键值。  
  
-   模板类，因为它提供的功能是一般性的功能，因此与作为元素包含的特定数据类型无关。  可使用的数据类型作为类模板以及比较函数和分配器中的参数指定。  
  
 多重集合类提供的迭代器是双向迭代器，但类成员函数 [insert](../Topic/multiset::insert.md) 和 [multiset](../Topic/multiset::multiset.md) 具有将较弱输入迭代器作为模板参数的版本，较弱输入迭代器的功能要求比双向迭代器类保证的功能要求更少。  不同的迭代器概念形成一个系列，通过它们的功能优化相关联。  每个迭代器概念有它自己的一套要求，使用这些概念的算法必须根据迭代器类型提供的要求限制它们的假设。  可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。  这是最小的功能集，但足以按有意义的方式提供类成员函数的上下文中的迭代器范围 \[`First`, `Last`\)。  
  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。  关联容器针对查找、插入和移除操作进行了优化。  显式支持这些操作的成员函数较为高效，执行这些操作的时间与容器中元素数量的对数平均成比例。  插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。  
  
 当应用程序满足将值与其键关联的条件时，应选择多重集合作为关联容器。  多重集合的元素可以为多个，并用作其自己的排序键，因此键不是唯一的。  此类结构的模型是排序列表，如关键字排序列表，其中关键字可以出现多次。  如果不允许关键字多次出现，则应使用集作为适当的容器结构。  如果将唯一定义作为值附加到唯一关键字的列表，则映射应为包含此数据的适当结构。  如果定义不唯一，则应选择多重映射作为容器。  
  
 多重集合通过调用存储的 `Compare` 类型的函数对象，对它控制的序列进行排序。  此存储的对象是比较函数，可通过调用成员函数 [key\_comp](../Topic/multiset::key_comp.md) 访问。  通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。  这将导致在非等效元素之间进行排序。  在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。  二元谓词 *f*\(*x*,*y*\) 是包含两个参数对象（*x* 和 *y*）以及一个返回值（**true** 或 **false**）的函数对象。  如果二元谓词具有自反性、反对称性和传递性且等效可传递，对集进行的排序将为严格弱排序，其中两个对象 x 和 y 定义为在 *f*\(*x,y*\) 和 *f*\(*y,x*\) 均为 false 时等效。  如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。  
  
 在 C\+\+ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。  有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)  
  
### 构造函数  
  
|||  
|-|-|  
|[multiset](../Topic/multiset::multiset.md)|构造一个空的或者是指定 `multiset` 的全部或部分副本的 `multiset`。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/multiset::allocator_type.md)|`allocator` 对象的 `multiset` 类的 typedef。|  
|[const\_iterator](../Topic/multiset::const_iterator.md)|可读取 `const` 中 `multiset` 元素的双向迭代器的 typedef。|  
|[const\_pointer](../Topic/multiset::const_pointer.md)|指向 `const` 中的 `multiset` 元素的指针的 typedef。|  
|[const\_reference](../Topic/multiset::const_reference.md)|对存储在 `const` 中的 `multiset` 元素的引用（用于读取和执行 `const` 操作）的 typedef。|  
|[const\_reverse\_iterator](../Topic/multiset::const_reverse_iterator.md)|可读取 `const` 中任何 `multiset` 元素的双向迭代器的 typedef。|  
|[difference\_type](../Topic/multiset::difference_type.md)|`multiset` 中迭代器指向的元素间范围内元素数量的有符号整数 typedef。|  
|[iterator](../Topic/multiset::iterator.md)|可读取或修改 `multiset` 中任何元素的双向迭代器的 typedef。|  
|[key\_compare](../Topic/multiset::key_compare.md)|可比较两个键以确定 `multiset` 中两个元素的相对顺序的函数对象的 typedef。|  
|[key\_type](../Topic/multiset::key_type.md)|可比较两个排序键以确定 `multiset` 中两个元素的相对顺序的函数对象的 typedef。|  
|[指针](../Topic/multiset::pointer.md)|指向 `multiset` 中的元素的指针的 typedef。|  
|[引用](../Topic/multiset::reference.md)|对 `multiset` 中存储的元素的引用的 typedef。|  
|[reverse\_iterator](../Topic/multiset::reverse_iterator.md)|可读取或修改反向 `multiset` 中的元素的双向迭代器的 typedef。|  
|[size\_type](../Topic/multiset::size_type.md)|可表示 `multiset` 中元素数量的无符号整数类型。|  
|[value\_compare](../Topic/multiset::value_compare.md)|可将两个元素作为排序键比较以确定它们在 `multiset` 中的相对顺序的函数对象的 typedef。|  
|[value\_type](../Topic/multiset::value_type.md)|一个 typedef，描述当 `multiset` 作为值时存储为元素的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[begin](../Topic/multiset::begin.md)|返回一个迭代器，此迭代器指向 `multiset` 中的第一个元素。|  
|[cbegin](../Topic/multiset::cbegin.md)|返回一个常量迭代器，此迭代器用于发现 `multiset` 中的第一个元素。|  
|[cend](../Topic/multiset::cend.md)|返回一个常量迭代器，此迭代器用于发现 `multiset` 中最后一个元素之后的位置。|  
|[清除](../Topic/multiset::clear.md)|清除 `multiset` 的所有元素。|  
|[count](../Topic/multiset::count.md)|返回 `multiset` 中其键与指定为参数的键匹配的元素数量。|  
|[crbegin](../Topic/multiset::crbegin.md)|返回一个常量迭代器，此迭代器用于发现反向集中的第一个元素。|  
|[crend](../Topic/multiset::crend.md)|返回一个常量迭代器，此迭代器用于发现反向集中最后一个元素之后的位置。|  
|[emplace](../Topic/multiset::emplace.md)|将就地构造的元素插入到 `multiset`。|  
|[emplace\_hint](../Topic/multiset::emplace_hint.md)|将就地构造的元素插入到 `multiset`，附带位置提示。|  
|[空](../Topic/multiset::empty.md)|测试 `multiset` 是否为空。|  
|[end](../Topic/multiset::end.md)|返回一个迭代器，此迭代器指向 `multiset` 中最后一个元素之后的位置。|  
|[equal\_range](../Topic/multiset::equal_range.md)|返回一对迭代器。  此迭代器对中的第一个迭代器指向 `multiset` 中其键大于指定键的第一个元素。  此迭代器对中的第二个迭代器指向 `multiset` 中其键等于或大于指定键的第一个元素。|  
|[erase](../Topic/multiset::erase.md)|从 `multiset` 中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。|  
|[find](../Topic/multiset::find.md)|返回一个迭代器，此迭代器指向 `multiset` 中其键与指定键相等的元素的第一个位置。|  
|[get\_allocator](../Topic/multiset::get_allocator.md)|返回用于构造 `allocator` 的 `multiset` 对象的副本。|  
|[插入](../Topic/multiset::insert.md)|将一个元素或元素范围插入到 `multiset`。|  
|[key\_comp](../Topic/multiset::key_comp.md)|提供一个函数对象，此函数对象可比较两个排序键以确定 `multiset` 中两个元素的相对顺序。|  
|[lower\_bound](../Topic/multiset::lower_bound.md)|返回一个迭代器，此迭代器指向 `multiset` 中其键等于或大于指定键的第一个元素。|  
|[max\_size](../Topic/multiset::max_size.md)|返回 `multiset` 的最大长度。|  
|[rbegin](../Topic/multiset::rbegin.md)|返回一个迭代器，此迭代器指向反向 `multiset` 中的第一个元素。|  
|[rend](../Topic/multiset::rend.md)|返回一个迭代器，此迭代器指向反向 `multiset` 中最后一个元素之后的位置。|  
|[size](../Topic/multiset::size.md)|返回 `multiset` 中的元素数量。|  
|[swap](../Topic/multiset::swap.md)|交换两个 `multiset` 的元素。|  
|[upper\_bound](../Topic/multiset::upper_bound.md)|返回一个迭代器，此迭代器指向 `multiset` 中其键大于指定键的第一个元素。|  
|[value\_comp](../Topic/multiset::value_comp.md)|检索用于对 `multiset` 中的元素值进行排序的比较对象副本。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../Topic/multiset::operator=.md)|将一个 `multiset` 中的元素替换为另一 `multiset` 副本。|  
  
## 要求  
 **标头：**\<set\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<set\> Members](http://msdn.microsoft.com/zh-cn/0c2d57c0-173f-4204-b579-c5f06aad8b95)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)