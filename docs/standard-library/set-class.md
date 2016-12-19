---
title: "set 类 | Microsoft Docs"
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
  - "std::set"
  - "set"
  - "set/std::set"
  - "std.set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "set 类"
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
caps.latest.revision: 22
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# set 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL 容器类集用于存储和检索集合中的数据，此集合中包含的元素值是唯一的，并且用作数据自动排序所依据的键值。  不能直接更改集中元素的值。  必须先删除旧值，才能插入具有新值的元素。  
  
## 语法  
  
```  
template <  
    class Key,   
    class Traits=less<Key>,   
    class Allocator=allocator<Key>   
>  
class set  
```  
  
#### 参数  
 `Key`  
 要存储在集中的元素数据类型。  
  
 `Traits`  
 一种提供函数对象的类型，该函数对象将两个元素值作为排序键进行比较，以确定其在集中的相对顺序。  此参数是可选参数，默认值为二元谓词 **less***\<Key\>*。  
  
 在 C\+\+ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。  有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 一种表示存储的分配器对象的类型，该分配器对象封装有关集的内存分配和解除分配的详细信息。  此参数是可选参数，默认值为 **allocator***\<Key\>*。  
  
## 备注  
 STL 集是：  
  
-   大小可变的关联容器，支持基于关联键值高效检索元素值。  此外，它是简单的关联容器，因为它的元素值即为它的键值。  
  
-   可逆，因为它提供双向迭代器来访问其元素。  
  
-   有序，因为它的元素在容器中根据指定的比较函数按键值排序。  
  
-   唯一，每个元素必须具有唯一键。  集还是简单关联容器，因此它的元素也是唯一的。  
  
 集还被描述为模板类，因为它提供的功能是一般性的功能，因此与作为元素包含的特定数据类型无关。  可使用的数据类型作为类模板以及比较函数和分配器中的参数指定。  
  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。  关联容器针对查找、插入和移除操作进行了优化。  显式支持这些操作的成员函数较为高效，执行这些操作的时间与容器中元素数量的对数平均成比例。  插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。  
  
 当应用程序满足将值与其键关联的条件时，应选择集作为关联容器。  集的元素是唯一的，并用作其自己的排序键。  此类结构的模型是排序列表，如关键字排序列表，其中关键字只能出现一次。  如果允许关键字多次出现，则应使用多重集合作为适当的容器结构。  如果需要将值附加到唯一关键字的列表，则映射应为包含此数据的适当结构。  如果键不唯一，则应选择多重映射作为容器。  
  
 集通过调用存储的 [key\_compare](../Topic/set::key_compare.md) 类型的函数对象，对它控制的序列进行排序。  此存储的对象是比较函数，可通过调用成员函数 [key\_comp](../Topic/set::key_comp.md) 访问。  通常，元素仅需小于比较元素即可建立此顺序，因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。  这将导致在非等效元素之间进行排序。  在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。  二元谓词 *f*\(*x,y*\) 是包含两个参数对象（*x* 和 *y*）以及一个返回值（**true** 或 **false**）的函数对象。  如果二元谓词具有自反性、反对称性和传递性且等效可传递，对集进行的排序将为严格弱排序，其中两个对象 *x* 和 *y* 定义为在 *f*\(*x,y*\) 和 *f*\(*y,x*\) 均为 false 时等效。  如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。  
  
 在 C\+\+ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。  有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)  
  
 集类提供的迭代器是双向迭代器，但类成员函数 [insert](../Topic/set::insert.md) 和 [set](../Topic/set::set.md) 具有将较弱输入迭代器作为模板参数的版本，较弱输入迭代器的功能要求比双向迭代器类保证的功能要求更少。  不同的迭代器概念形成一个系列，通过它们的功能优化相关联。  每个迭代器概念有它自己的一套要求，使用这些概念的算法必须根据迭代器类型提供的要求限制它们的假设。  可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。  这是最小的功能集，但足以按有意义的方式提供类成员函数的上下文中的迭代器范围 \[`First`, `Last`\)。  
  
### 构造函数  
  
|||  
|-|-|  
|[set](../Topic/set::set.md)|构造一个空的或者是其他某个集的全部或部分副本的集。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/set::allocator_type.md)|一种类型，此类型表示集对象的 `allocator` 类。|  
|[const\_iterator](../Topic/set::const_iterator.md)|一种类型，此类型提供可读取集中的 `const` 元素的双向迭代器。|  
|[const\_pointer](../Topic/set::const_pointer.md)|一种类型，此类型提供指向集中的 `const` 元素的指针。|  
|[const\_reference](../Topic/set::const_reference.md)|一种类型，此类型提供对存储在集中的 `const` 元素的引用（用于读取和执行 `const` 操作）。|  
|[const\_reverse\_iterator](../Topic/set::const_reverse_iterator.md)|一种类型，此类型提供可读取集中的任何 `const` 元素的双向迭代器。|  
|[difference\_type](../Topic/set::difference_type.md)|一种有符号整数类型，此类型可用于表示集中迭代器指向的元素间范围内的元素数量。|  
|[iterator](../Topic/set::iterator.md)|一种类型，此类型提供可读取或修改集中的任何元素的双向迭代器。|  
|[key\_compare](../Topic/set::key_compare.md)|一种提供函数对象的类型，该函数对象可比较两个排序键以确定集中两个元素的相对顺序。|  
|[key\_type](../Topic/set::key_type.md)|此类型描述当作为排序键时存储为集中元素的对象。|  
|[指针](../Topic/set::pointer.md)|一种类型，此类型提供指向集中元素的指针。|  
|[引用](../Topic/set::reference.md)|一种类型，此类型提供对存储在集中的元素的引用。|  
|[reverse\_iterator](../Topic/set::reverse_iterator.md)|一种类型，此类型提供可读取或修改反向集中的元素的双向迭代器。|  
|[size\_type](../Topic/set::size_type.md)|一种无符号整数类型，此类型可表示集中的元素数量。|  
|[value\_compare](../Topic/set::value_compare.md)|一种提供函数对象的类型，该函数对象可比较两个元素以确定其在集中的相对顺序。|  
|[value\_type](../Topic/set::value_type.md)|此类型描述当作为值时存储为集中元素的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[begin](../Topic/set::begin.md)|返回一个迭代器，此迭代器用于发现集中的第一个元素。|  
|[cbegin](../Topic/set::cbegin.md)|返回一个常量迭代器，此迭代器用于发现集中的第一个元素。|  
|[cend](../Topic/set::cend.md)|返回一个常量迭代器，此迭代器用于发现集中最后一个元素之后的位置。|  
|[清除](../Topic/set::clear.md)|清除集的所有元素。|  
|[count](../Topic/set::count.md)|返回集中其键与指定为参数的键匹配的元素数量。|  
|[crbegin](../Topic/set::rbegin.md)|返回一个常量迭代器，此迭代器用于发现反向集中的第一个元素。|  
|[crend](../Topic/set::rend.md)|返回一个常量迭代器，此迭代器用于发现反向集中最后一个元素之后的位置。|  
|[emplace](../Topic/set::emplace.md)|将就地构造的元素插入到集中。|  
|[emplace\_hint](../Topic/set::emplace_hint.md)|将就地构造的元素插入到集中，附带位置提示。|  
|[空](../Topic/set::empty.md)|测试集是否为空。|  
|[end](../Topic/set::end.md)|返回一个迭代器，此迭代器用于发现集中最后一个元素之后的位置。|  
|[equal\_range](../Topic/set::equal_range.md)|返回一对迭代器，这两个迭代器分别用于发现集中其键大于指定键的第一个元素，以及集中其键等于或大于指定键的第一个元素。|  
|[erase](../Topic/set::erase.md)|从集中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。|  
|[find](../Topic/set::find.md)|返回一个迭代器，此迭代器用于发现集中其键与指定键等效的元素的位置。|  
|[get\_allocator](../Topic/set::get_allocator.md)|返回用于构造集的 `allocator` 对象的副本。|  
|[插入](../Topic/set::insert.md)|将一个元素或元素范围插入到集。|  
|[key\_comp](../Topic/set::key_comp.md)|检索用于对集中的键进行排序的比较对象副本。|  
|[lower\_bound](../Topic/set::lower_bound.md)|返回一个迭代器，此迭代器指向集中其键等于或大于指定键的第一个元素。|  
|[max\_size](../Topic/set::max_size.md)|返回集的最大长度。|  
|[rbegin](../Topic/set::rbegin.md)|返回一个迭代器，此迭代器用于发现反向集中的第一个元素。|  
|[rend](../Topic/set::rend.md)|返回一个迭代器，此迭代器用于发现反向集中最后一个元素之后的位置。|  
|[size](../Topic/set::size.md)|返回集合中元素的数目。|  
|[swap](../Topic/set::swap.md)|交换两个集的元素。|  
|[upper\_bound](../Topic/set::upper_bound.md)|返回一个迭代器，此迭代器指向集中其键大于指定键的第一个元素。|  
|[value\_comp](../Topic/set::value_comp.md)|检索用于对集中的元素值进行排序的比较对象副本。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../Topic/set::operator=.md)|将一个集中的元素替换为另一个集的副本。|  
  
## 要求  
 **标头：**\<set\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<set\>](../standard-library/set.md)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)