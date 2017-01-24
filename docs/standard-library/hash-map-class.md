---
title: "hash_map 类 | Microsoft Docs"
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
  - "stdext::hash_map"
  - "hash_map/stdext::hash_map"
  - "std.hash_map"
  - "stdext.hash_map"
  - "std::hash_map"
  - "hash_map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_map 类"
ms.assetid: 40879dfc-51ba-4a59-9f9e-26208de568a8
caps.latest.revision: 25
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hash_map 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  此 API 已废弃不用。  替代项为 [unordered\_map 类](../standard-library/unordered-map-class.md)。  
  
 从集合快速存储和检索数据，集合中的每个元素都是一个具有排序关键字和关联数据值的一对值，排序关键字的值是唯一的。  
  
## 语法  
  
```  
template <  
   class Key,   
   class Type,   
   class Traits=hash_compare<Key, less<Key> >,   
   class Allocator=allocator<pair <const Key, Type> >   
>  
class hash_map  
```  
  
#### 参数  
 `Key`  
 要存储在 hash\_map 中的键数据类型。  
  
 `Type`  
 要存储在 hash\_map 中的元素数据类型。  
  
 `Traits`  
 此类型包括两个函数对象，其中一个是类 compare，可与作为排序关键字的两个元素值进行比较以确定其相对顺序；另一个是哈希函数，这是一个一元谓词，用于将元素的关键字值映射到 `size_t` 类型的无符号整数。  此参数为可选参数，其默认值为 hash\_compare\<`Key`, less\<`Key`\> \>。  
  
 `Allocator`  
 一种表示存储的分配器对象的类型，该分配器对象封装有关 hash\_map 的内存分配和解除分配的详细信息。  此参数为可选参数，其默认值为 allocator\<pair \<const `Key`, `Type`\>\>。  
  
## 备注  
 hash\_map 是：  
  
-   大小可变的关联容器，支持基于关联键值高效检索元素值。  
  
-   可逆，因为它提供双向迭代器来访问其元素。  
  
-   经过哈希处理，因为其元素分组到了哈希桶中，哈希桶基于应用于元素键值的哈希函数的值。  
  
-   唯一，每个元素必须具有唯一键。  
  
-   关联容器对，因为它的元素数据值与其键值不同。  
  
-   模板类，因为它提供的功能是一般性的功能，因此与作为元素或键包含的特定数据类型无关。  用于元素和键的数据类型作为类模板以及比较函数和分配器中的参数指定。  
  
 哈希算法相比于排序的主要优点是效率更高；在排序技术中，时间与容器中元素数的对数成正比，而成功的哈希算法可在恒定的平均时间内执行插入、删除和查找操作。  可以直接更改 hash\_map 中的元素值，但不能直接更改其关联的键值。  必须先删除与旧元素关联的键值，才能插入与新元素关联的新键值。  
  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。  经过哈希处理的关联容器针对查找、插入和删除操作进行了优化。  与设计良好的哈希函数一起使用时，显式支持这些操作的成员函数较为高效，执行这些操作的时间为平均恒定值，而不取决于容器中元素的数目。  精心设计的哈希函数将生成统一分布的哈希值，并将最大限度地减少冲突数量，据说当非重复键值映射到相同的哈希值时会发生冲突。  在最坏情况下，使用可能是最差的哈希运算，操作数量与序列中的元素数量成比例（线性时间）。  
  
 当应用程序满足将值与其键关联的条件时，应选择 hash\_map 作为关联容器。  此类结构的模型是关键字排序列表，这些关键字只出现一次，并具有提供定义的关联字符串值。  相反，如果关键字有多个正确定义，则此关键字不唯一，应选择 hash\_multimap 作为容器。  另一方面，如果仅存储关键字列表，则应使用 hash\_set 作为正确容器。  如果允许关键字多次出现，那么相应的容器结构应该是 hash\_multiset。  
  
 hash\_map 通过调用存储的 [value\_compare](../standard-library/value-compare-class.md) 类的哈希 `Traits` 对象，对其控制的序列进行排序。  此存储对象可通过调用成员函数 [key\_comp](../Topic/hash_map::key_comp.md) 进行访问。  此类函数对象必须与 [hash\_compare](../standard-library/hash-compare-class.md)\<Key, less\<Key\>\> 类的对象具有相同的行为。  具体而言，对于类型 `Key` 的所有值 `Key`，调用 `Traits`\(`Key`\) 会提供 `size_t` 类型的值的分布。  
  
 通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。  这将导致在非等效元素之间进行排序。  在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。  二元谓词 f\(x y\) 是包含两个自变量对象（`x` 和 `y`）以及一个返回值（`true` 或 `false`）的函数对象。  如果二元谓词具有自反性、反对称性和传递性且等效可传递，对 hash\_map 进行的排序将为严格弱排序，其中两个对象 x 和 y 定义为在 f\(x, y\) 和 f\(y, x\) 均为 false 时等效。  如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。  
  
 受控序列中元素的实际顺序取决于哈希函数、排序函数和存储在容器对象中的哈希表的当前大小。  无法确定哈希表的当前大小，因此通常无法预测受控序列中元素的顺序。  插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。  
  
 hash\_map 类提供的迭代器是双向迭代器，但类成员函数 [insert](../Topic/hash_map::insert.md) 和 [hash\_map](../Topic/hash_map::hash_map.md) 的版本是将较弱输入迭代器作为模板参数，该迭代器的功能要求比双向迭代器类保证的功能要求更少。  不同的迭代器概念形成一个系列，通过它们的功能优化相关联。  每个迭代器概念有它自己的一套要求，使用这些概念的算法必须根据迭代器类型提供的要求限制它们的假设。  可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。  这是最小的功能集，但足以按有意义的方式提供类成员函数的上下文中的迭代器范围 `[First, Last)`。  
  
 在 Visual C\+\+ .NET 2003 中，[\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。  有关更多信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### 构造函数  
  
|||  
|-|-|  
|[hash\_map](../Topic/hash_map::hash_map.md)|构造一个空的或者是其他某个 `hash_map` 的全部或部分副本的 `hash_map`。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/hash_map::allocator_type.md)|一种类型，此类型表示 `allocator` 对象的 `hash_map` 类。|  
|[const\_iterator](../Topic/hash_map::const_iterator.md)|一种类型，此类型提供可读取 `const` 中的 `hash_map` 元素的双向迭代器。|  
|[const\_pointer](../Topic/hash_map::const_pointer.md)|一种类型，此类型提供指向 `const` 中的 `hash_map` 元素的指针。|  
|[const\_reference](../Topic/hash_map::const_reference.md)|一种类型，此类型提供对存储在 `const` 中的 `hash_map` 元素的引用（用于读取和执行 `const` 操作）。|  
|[const\_reverse\_iterator](../Topic/hash_map::const_reverse_iterator.md)|一种类型，此类型提供可读取 `const` 中的任何 `hash_map` 元素的双向迭代器。|  
|[difference\_type](../Topic/hash_map::difference_type.md)|一种有符号整数类型，此类型可用于表示 `hash_map` 中迭代器指向的元素间范围内的元素数量。|  
|[iterator](../Topic/hash_map::iterator.md)|一种类型，它提供可读取或修改 `hash_map` 中任何元素的双向迭代器。|  
|[key\_compare](../Topic/hash_map::key_compare.md)|一种提供函数对象的类型，该函数对象可比较两个排序键以确定 `hash_map` 中两个元素的相对顺序。|  
|[key\_type](../Topic/hash_map::key_type.md)|一种类型，用于描述组成 `hash_map` 中每个元素的排序关键字对象。|  
|[mapped\_type](../Topic/hash_map::mapped_type.md)|一种类型，此类型表示存储在 `hash_map` 中的数据类型。|  
|[指针](../Topic/hash_map::pointer.md)|一种类型，它提供指向 `hash_map` 中的某个元素的指针。|  
|[引用](../Topic/hash_map::reference.md)|一种类型，此类型提供对存储在 `hash_map` 中的元素的引用。|  
|[reverse\_iterator](../Topic/hash_map::reverse_iterator.md)|一种类型，此类型提供可读取或修改反向 `hash_map` 中的元素的双向迭代器。|  
|[size\_type](../Topic/hash_map::size_type.md)|可表示 `hash_map` 中元素数量的无符号整数类型。|  
|[value\_type](../Topic/hash_map::value_type.md)|一种提供函数对象的类型，该函数对象可将两个元素作为排序键比较以确定它们在 `hash_map` 中的相对顺序。|  
  
### 成员函数  
  
|||  
|-|-|  
|[hash\_map::at](../Topic/hash_map::at.md)|在 `hash_map` 中查找具有指定关键字值的元素。|  
|[begin](../Topic/hash_map::begin.md)|返回一个迭代器，此迭代器用于发现 `hash_map` 中的第一个元素。|  
|[hash\_map::cbegin](../Topic/hash_map::cbegin.md)|返回一个常量迭代器，此迭代器用于发现 `hash_map` 中的第一个元素。|  
|[hash\_map::cend](../Topic/hash_map::cend.md)|返回一个常量迭代器，此迭代器用于发现 `hash_map` 中最后一个元素之后的位置。|  
|[清除](../Topic/hash_map::clear.md)|清除 `hash_map` 的所有元素。|  
|[count](../Topic/hash_map::count.md)|返回 `hash_map` 中其键与指定为参数的键匹配的元素数量。|  
|[hash\_map::crbegin](../Topic/hash_map::crbegin.md)|返回一个常量迭代器，此迭代器用于发现反向 `hash_map` 中的第一个元素。|  
|[hash\_map::crend](../Topic/hash_map::crend.md)|返回一个常量迭代器，此迭代器用于发现反向 `hash_map` 中最后一个元素之后的位置。|  
|[hash\_map::emplace](../Topic/hash_map::emplace.md)|将就地构造的元素插入到 `hash_map`。|  
|[hash\_map::emplace\_hint](../Topic/hash_map::emplace_hint.md)|将就地构造的元素插入到 `hash_map`，附带位置提示。|  
|[空](../Topic/hash_map::empty.md)|测试 `hash_map` 是否为空。|  
|[end](../Topic/hash_map::end.md)|返回一个迭代器，此迭代器用于发现 `hash_map` 中最后一个元素之后的位置。|  
|[equal\_range](../Topic/hash_map::equal_range.md)|返回一对迭代器，这两个迭代器分别用于发现 `hash_map` 中其键大于指定键的第一个元素，以及 `hash_map` 中其键等于或大于指定键的第一个元素。|  
|[erase](../Topic/hash_map::erase.md)|从指定位置删除 `hash_map` 中的一个元素或一系列元素|  
|[find](../Topic/hash_map::find.md)|返回一个迭代器，此迭代器用于发现 `hash_map` 中其键与指定键等效的元素的位置。|  
|[get\_allocator](../Topic/hash_map::get_allocator.md)|返回用于构造 `allocator` 的 `hash_map` 对象的副本。|  
|[插入](../Topic/hash_map::insert.md)|将一个元素或元素范围插入到 `hash_map`。|  
|[key\_comp](../Topic/hash_map::key_comp.md)|返回一个迭代器，此迭代器指向 `hash_map` 中其键值等于或大于指定键的键值的第一个元素。|  
|[lower\_bound](../Topic/hash_map::lower_bound.md)|返回一个迭代器，此迭代器指向 `hash_map` 中其键值等于或大于指定键的键值的第一个元素。|  
|[max\_size](../Topic/hash_map::max_size.md)|返回 `hash_map` 的最大长度。|  
|[rbegin](../Topic/hash_map::rbegin.md)|返回一个迭代器，此迭代器用于发现反向 `hash_map` 中的第一个元素。|  
|[rend](../Topic/hash_map::rend.md)|返回一个迭代器，此迭代器用于发现反向 `hash_map` 中最后一个元素之后的位置。|  
|[size](../Topic/hash_map::size.md)|返回 `hash_map` 中的元素数量。|  
|[swap](../Topic/hash_map::swap.md)|交换两个 `hash_map` 的元素。|  
|[upper\_bound](../Topic/hash_map::upper_bound.md)|返回一个迭代器，此迭代器指向 `hash_map` 中其键值大于指定键的键值的第一个元素。|  
|[value\_comp](../Topic/hash_map::value_comp.md)|检索用于对 `hash_map` 中的元素值进行排序的比较对象副本。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator&#91;&#93;](../Topic/hash_map::operator.md)|将元素插入到具有指定键值的 `hash_map`。|  
|[hash\_map::operator\=](../Topic/hash_map::operator=.md)|将一个 `hash_map` 中的元素替换为另一 `hash_map` 副本。|  
  
## 要求  
 **标头：**\<hash\_map\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)