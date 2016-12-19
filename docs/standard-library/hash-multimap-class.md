---
title: "hash_multimap 类 | Microsoft Docs"
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
  - "stdext::hash_multimap"
  - "stdext.hash_multimap"
  - "hash_map/stdext::hash_multimap"
  - "hash_multimap"
  - "std::hash_multimap"
  - "std.hash_multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_multimap 类"
ms.assetid: f41a6db9-67aa-43a3-a3c5-dbfe9ec3ae7d
caps.latest.revision: 24
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hash_multimap 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  此 API 已废弃不用。  替代项为 [unordered\_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 容器类 hash\_multimap 是标准模板库的扩展，用于存储和快速检索集合中的数据，集合中的每个元素都是具有排序键的元素对，而排序键的值不需要具有唯一性或是相关数据值。  
  
## 语法  
  
```  
template <  
   class Key,   
   class Type,   
   class Traits=hash_compare<Key, less<Key> >,   
   class Allocator=allocator<pair <const Key, Type> >   
>  
class hash_multimap  
```  
  
#### 参数  
 `Key`  
 要存储在 hash\_multimap 中的键数据类型。  
  
 `Type`  
 要存储在 hash\_multimap 中的元素数据类型。  
  
 `Traits`  
 此类型包括两个函数对象，其中一个是类 `Traits`，能够作为排序键对两个元素值进行比较，以确定其相对顺序；另一个是哈希函数，这是一个一元谓词，用于将元素的键值映射到 **size\_t** 类型的无符号整数。  此参数是可选参数，默认值为 `hash_compare``<Key, less<Key> >`。  
  
 `Allocator`  
 该类型表示的是已存储的分配器对象，该对象中封装了有关 hash\_multimap 的内存分配和内存释放的详细信息。  此参数是可选参数，默认值为 `allocator<pair <const Key, Type> >`。  
  
## 备注  
 hash\_multimap 为：  
  
-   大小可变的关联容器，支持基于关联键值高效检索元素值。  
  
-   可逆，因为它提供双向迭代器来访问其元素。  
  
-   经过哈希处理，因为其元素分组到了哈希桶中，哈希桶基于应用于元素键值的哈希函数的值。  
  
-   多个，它的元素不需要具有唯一键，因此一个键值可具有多个相关联的元素数据值。  
  
-   关联容器对，因为它的元素值与其键值不同。  
  
-   模板类，因为它提供的功能是一般性的功能，因此与作为元素或键包含的特定数据类型无关。  用于元素和键的数据类型作为类模板以及比较函数和分配器中的参数指定。  
  
 哈希算法相比于排序的主要优点是效率更高；在排序技术中，时间与容器中元素数的对数成正比，而成功的哈希算法可在恒定的平均时间内执行插入、删除和查找操作。  hash\_multimap 中某个元素的值，但不是其关联键值，可直接更改。  必须先删除与旧元素关联的键值，才能插入与新元素关联的新键值。  
  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。  经过哈希处理的关联容器针对查找、插入和删除操作进行了优化。  与设计良好的哈希函数一起使用时，显式支持这些操作的成员函数较为高效，执行这些操作的时间为平均恒定值，而不取决于容器中元素的数目。  精心设计的哈希函数将生成统一分布的哈希值，并将最大限度地减少冲突数量，据说当非重复键值映射到相同的哈希值时会发生冲突。  在最坏情况下，使用可能是最差的哈希运算，操作数量与序列中的元素数量成比例（线性时间）。  
  
 将应用程序满足将值与其键关联的条件时，应选择 hash\_multimap 作为关联容器。  此类结构的模型是关键字排序列表，这些关键字具有提供定义等的关联字符串值，并且并非始终唯一定义。  相反，如果对关键字进行唯一定义，以使键具有唯一性，那么应选择 hash\_map 作为容器。  另一方面，如果仅存储关键字列表，则应使用 hash\_set 作为正确容器。  如果允许关键字多次出现，那么相应的容器结构应该是 hash\_multiset。  
  
 hash\_multimap 通过调用类型 [value\_compare](../standard-library/value-compare-class.md) 的已存储哈希 `Traits` 对象对其控制的序列进行排序。  此存储对象可通过调用成员函数 [key\_comp](../Topic/hash_map::key_comp.md) 进行访问。  此类函数对象的行为必须与类 [hash\_compare](../standard-library/hash-compare-class.md)`<Key,  less<Key> >` 的对象行为相同。  具体而言，针对类型为 `Key` 的所有值 `Key`，调用 `Traits (Key)` 将对类型为 `size_t` 的值进行分布。  
  
 通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。  这会导致在非等效元素之间进行排序。  在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。  二元谓词 f\(x, y\) 是包含两个自变量对象（`x` 和 `y`）以及一个返回值（`true` 或 `false`）的函数对象。  如果二元谓词具有非自反性、反对称性和传递性且等效可传递，则对 hash\_multimap 进行的排序将为严格弱排序，其中 `x` 和 `y` 两个对象定义为在 f\(x, y\) 和 f\(y, x\) 均为 `false` 时等效。  如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。  
  
 受控序列中元素的实际顺序取决于哈希函数、排序函数和存储在容器对象中的哈希表的当前大小。  无法确定哈希表的当前大小，因此通常无法预测受控序列中元素的顺序。  插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。  
  
 hash\_multimap 类所提供的迭代器是双向迭代器，但类成员函数 [insert](../Topic/hash_multimap::insert.md) 和 [hash\_multimap](../Topic/hash_multimap::hash_multimap.md) 的版本是将较弱输入迭代器作为模板参数，该迭代器的功能要求比双向迭代器类所保证的功能要求更少。  不同的迭代器概念形成一个系列，通过它们的功能优化相关联。  每个迭代器概念有自己的 hash\_multimap 要求，使用这些要求的算法必须根据该类型的迭代器所提供的要求来限制它们的假设。  可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。  这是最小的 hash\_multimap 功能，但足以按有意义的方式说明成员函数上下文中的 `[First, Last)` 迭代器范围。  
  
 在 Visual C\+\+ .NET 2003 中，[\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。  有关更多信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### 构造函数  
  
|||  
|-|-|  
|[hash\_multimap](../Topic/hash_multimap::hash_multimap.md)|构造一个列表，它具有特定大小、具有特定值的元素、包含特定 `allocator` 或作为其他一些 `hash_multimap` 的副本。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/hash_multimap::allocator_type.md)|一种类型，此类型表示 `allocator` 对象的 `hash_multimap` 类。|  
|[const\_iterator](../Topic/hash_multimap::const_iterator.md)|一种类型，此类型提供可读取 `const` 中的 `hash_multimap` 元素的双向迭代器。|  
|[const\_pointer](../Topic/hash_multimap::const_pointer.md)|一种类型，此类型提供指向 `const` 中的 `hash_multimap` 元素的指针。|  
|[const\_reference](../Topic/hash_multimap::const_reference.md)|一种类型，此类型提供对存储在 `const` 中的 `hash_multimap` 元素的引用（用于读取和执行 `const` 操作）。|  
|[const\_reverse\_iterator](../Topic/hash_multimap::const_reverse_iterator.md)|一种类型，此类型提供可读取 `const` 中的任何 `hash_multimap` 元素的双向迭代器。|  
|[difference\_type](../Topic/hash_multimap::difference_type.md)|一种有符号整数类型，此类型可用于表示 `hash_multimap` 中迭代器指向的元素间范围内的元素数量。|  
|[iterator](../Topic/hash_multimap::iterator.md)|一种类型，它提供可读取或修改 `hash_multimap` 中任何元素的双向迭代器。|  
|[key\_compare](../Topic/hash_multimap::key_compare.md)|一种提供函数对象的类型，该函数对象可比较两个排序键以确定 `hash_multimap` 中两个元素的相对顺序。|  
|[key\_type](../Topic/hash_multimap::key_type.md)|一种类型，此类型描述组成 `hash_multimap` 中每个元素的排序键对象。|  
|[mapped\_type](../Topic/hash_multimap::mapped_type.md)|一种类型，此类型表示存储在 `hash_multimap` 中的数据类型。|  
|[指针](../Topic/hash_multimap::pointer.md)|一种类型，它提供指向 `hash_multimap` 中的某个元素的指针。|  
|[引用](../Topic/hash_multimap::reference.md)|一种类型，此类型提供对存储在 `hash_multimap` 中的元素的引用。|  
|[reverse\_iterator](../Topic/hash_multimap::reverse_iterator.md)|一种类型，此类型提供可读取或修改反向 `hash_multimap` 中的元素的双向迭代器。|  
|[size\_type](../Topic/hash_multimap::size_type.md)|可表示 `hash_multimap` 中元素数量的无符号整数类型。|  
|[value\_type](../Topic/hash_multimap::value_type.md)|一种提供函数对象的类型，该函数对象可将两个元素作为排序键比较以确定它们在 `hash_multimap` 中的相对顺序。|  
  
### 成员函数  
  
|||  
|-|-|  
|[begin](../Topic/hash_multimap::begin.md)|返回一个迭代器，此迭代器用于发现 `hash_multimap` 中的第一个元素。|  
|[hash\_multimap::cbegin](../Topic/hash_multimap::cbegin.md)|返回一个常量迭代器，此迭代器用于发现 `hash_multimap` 中的第一个元素。|  
|[hash\_multimap::cend](../Topic/hash_multimap::cend.md)|返回一个常量迭代器，此迭代器用于发现 `hash_multimap` 中最后一个元素之后的位置。|  
|[清除](../Topic/hash_multimap::clear.md)|清除 `hash_multimap` 的所有元素。|  
|[count](../Topic/hash_multimap::count.md)|返回 `hash_multimap` 中其键与指定为参数的键匹配的元素数量。|  
|[hash\_multimap::crbegin](../Topic/hash_multimap::crbegin.md)|返回一个常量迭代器，此迭代器用于发现反向 `hash_multimap` 中的第一个元素。|  
|[hash\_multimap::crend](../Topic/hash_multimap::crend.md)|返回一个常量迭代器，此迭代器用于发现反向 `hash_multimap` 中最后一个元素之后的位置。|  
|[hash\_multimap::emplace](../Topic/hash_multimap::emplace.md)|将就地构造的元素插入到 `hash_multimap`。|  
|[hash\_multimap::emplace\_hint](../Topic/hash_multimap::emplace_hint.md)|将就地构造的元素插入到 `hash_multimap`，附带位置提示。|  
|[空](../Topic/hash_multimap::empty.md)|测试 `hash_multimap` 是否为空。|  
|[end](../Topic/hash_multimap::end.md)|返回一个迭代器，此迭代器用于发现 `hash_multimap` 中最后一个元素之后的位置。|  
|[equal\_range](../Topic/hash_multimap::equal_range.md)|返回一个迭代器，此迭代器用于发现 `hash_multimap` 中最后一个元素之后的位置。|  
|[erase](../Topic/hash_multimap::erase.md)|从指定位置删除 `hash_multimap` 中的一个元素或一系列元素|  
|[find](../Topic/hash_multimap::find.md)|返回一个迭代器，此迭代器用于发现 `hash_multimap` 中其键与指定键等效的元素的位置。|  
|[get\_allocator](../Topic/hash_multimap::get_allocator.md)|返回用于构造 `allocator` 的 `hash_multimap` 对象的副本。|  
|[插入](../Topic/hash_multimap::insert.md)|将一个或一系列元素插入到 `hash_multimap` 中的指定位置。|  
|[key\_comp](../Topic/hash_multimap::key_comp.md)|检索用于对 `hash_multimap` 中的键进行排序的比较对象副本。|  
|[lower\_bound](../Topic/hash_multimap::lower_bound.md)|返回一个迭代器，此迭代器指向 `hash_multimap` 中其键值等于或大于指定键的键值的第一个元素。|  
|[max\_size](../Topic/hash_multimap::max_size.md)|返回 `hash_multimap` 的最大长度。|  
|[rbegin](../Topic/hash_multimap::rbegin.md)|返回一个迭代器，此迭代器用于发现反向 `hash_multimap` 中的第一个元素。|  
|[rend](../Topic/hash_multimap::rend.md)|返回一个迭代器，此迭代器用于发现反向 `hash_multimap` 中最后一个元素之后的位置。|  
|[size](../Topic/hash_multimap::size.md)|为 `hash_multimap` 指定新的大小。|  
|[swap](../Topic/hash_multimap::swap.md)|交换两个 `hash_multimap` 的元素。|  
|[upper\_bound](../Topic/hash_multimap::upper_bound.md)|返回一个迭代器，此迭代器指向 `hash_multimap` 中其键值大于指定键的键值的第一个元素。|  
|[value\_comp](../Topic/hash_multimap::value_comp.md)|检索用于对 `hash_multimap` 中的元素值进行排序的比较对象副本。|  
  
### 运算符  
  
|||  
|-|-|  
|[hash\_multimap::operator\=](../Topic/hash_multimap::operator=.md)|将一个 `hash_multimap` 中的元素替换为另一 `hash_multimap` 副本。|  
  
## 要求  
 **标头：**\<hash\_map\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)