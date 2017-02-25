---
title: "hash_set 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hash_set/stdext::hash_set"
  - "std::hash_set"
  - "std.hash_set"
  - "stdext::hash_set"
  - "hash_set"
  - "stdext.hash_set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_set 类"
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# hash_set 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  此 API 已废弃不用。  替代项为 [unordered\_set 类](../standard-library/unordered-set-class.md)。  
  
 容器类 hash\_set 是标准模板库 \(STL\) 的扩展，用于存储和快速检索集合中的数据，集合中内含元素的值是唯一的且用作键值。  
  
## 语法  
  
```  
template <  
   class Key,   
   class Traits=hash_compare<Key, less<Key> >,   
   class Allocator=allocator<Key>   
>  
class hash_set  
```  
  
#### 参数  
 `Key`  
 要存储在 hash\_set 中的元素数据类型。  
  
 `Traits`  
 该类型包括两个函数对象，其中一个是类比较函数，这是一个二元谓词，能够比较作为排序键的两个元素值以确定其相对顺序；另一个是哈希函数，这是一个一元谓词，用于将元素的键值映射到 **size\_t** 类型的无符号整数。  此参数是可选参数，并且默认值为 `hash_compare`*\<Key,* **less***\<Key\> \>*。  
  
 `Allocator`  
 一种表示存储的分配器对象的类型，该分配器对象封装有关 hash\_set 的内存分配和解除分配的详细信息。  此参数是可选参数，默认值为 **allocator***\<Key\>*。  
  
## 备注  
 Hash\_set 是：  
  
-   大小可变的关联容器，支持基于关联键值高效检索元素值。  此外，它是简单的关联容器，因为它的元素值即为它的键值。  
  
-   可逆，因为它提供双向迭代器来访问其元素。  
  
-   经过哈希处理，因为其元素分组到了哈希桶中，哈希桶基于应用于元素键值的哈希函数的值。  
  
-   唯一，每个元素必须具有唯一键。  由于 hash\_set 也是简单的关联容器，因此其元素也都是唯一的。  
  
-   一个模板类，由于其提供的功能是一般功能，因此与作为元素或键包含的特定数据类型无关。  用于元素和键的数据类型作为类模板以及比较函数和分配器中的参数指定。  
  
 哈希算法相比于排序的主要优点是效率更高；在排序技术中，时间与容器中元素数的对数成正比，而成功的哈希算法可在恒定的平均时间内执行插入、删除和查找操作。  不能直接更改集中元素的值。  必须先删除旧值，才能插入具有新值的元素。  
  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。  经过哈希处理的关联容器针对查找、插入和删除操作进行了优化。  与设计良好的哈希函数一起使用时，显式支持这些操作的成员函数较为高效，执行这些操作的时间为平均恒定值，而不取决于容器中元素的数目。  精心设计的哈希函数将生成统一分布的哈希值，并将最大限度地减少冲突数量，据说当非重复键值映射到相同的哈希值时会发生冲突。  在最坏情况下，使用可能是最差的哈希运算，操作数量与序列中的元素数量成比例（线性时间）。  
  
 当应用程序满足将值与其键关联的条件时，应选择 hash\_set 作为关联容器。  Hash\_set 的元素是唯一的，并用作其自己的排序键。  此类结构的模型是排序列表，如关键字排序列表，其中关键字只能出现一次。  如果允许关键字多次出现，那么相应的容器结构应该是 hash\_multiset。  如果需要将值附加到唯一关键字的列表，则包含此数据的适当结构应为 hash\_map。  如果键不唯一，则应选择 hash\_multimap 作为容器。  
  
 hash\_set 通过调用类型 [value\_compare](../Topic/hash_set::value_compare.md) 存储的哈希**特征**对象，对其控制的序列进行排序。  此存储对象可通过调用成员函数 [key\_comp](../Topic/hash_set::key_comp.md) 进行访问。  此类函数对象的行为必须与类 *hash\_compare\<Key, less\<Key\>\> 的对象的相同。*具体而言，对于类型 Key 的所有值 `_Key`，调用 Trait\(`_Key` \) 都会对类型 size\_t 的值进行分配。  
  
 通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。  这会导致在非等效元素之间进行排序。  在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。  二元谓词 *f*\(*x*,*y*\) 是具有两个参数对象（x 和 y）和一个返回值（true 或 false）的函数对象。  如果二元谓词具有非自反性、反对称性和传递性且等效可传递，对 hash\_set 进行的排序将为严格弱排序，其中两个对象 *x* 和 *y* 定义为在 *f*\(*x*,*y*\) 和 *f*\(*y*,*x*\) 均为 false 时等效。  如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。  
  
 受控序列中元素的实际顺序取决于哈希函数、排序函数和存储在容器对象中的哈希表的当前大小。  无法确定哈希表的当前大小，因此通常无法预测受控序列中元素的顺序。  插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。  
  
 hash\_set 类提供的迭代器是双向迭代器，但类成员函数[insert](../Topic/hash_set::insert.md) 和[hash\_set](../Topic/hash_set::hash_set.md) 具有将较弱输入迭代器作为模板参数的版本，较弱输入迭代器的功能要求比双向迭代器类保证的功能要求更少。  不同的迭代器概念形成一个系列，通过它们的功能优化相关联。  每个迭代器概念有它自己的一套要求，使用这些概念的算法必须根据迭代器类型提供的要求限制它们的假设。  可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。  这是最小的功能集，但足以按有意义的方式提供类成员函数的上下文中的迭代器范围 \[`_First`, `_Last`\)。  
  
 在 Visual C\+\+ .NET 2003 中，[\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。  有关更多信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### 构造函数  
  
|||  
|-|-|  
|[hash\_set](../Topic/hash_set::hash_set.md)|构造一个空的或者是其他某个 `hash_set` 的全部或部分副本的 `hash_set`。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/hash_set::allocator_type.md)|一种类型，此类型表示 `allocator` 对象的 `hash_set` 类。|  
|[const\_iterator](../Topic/hash_set::const_iterator.md)|一种类型，此类型提供可读取 `const` 中的 `hash_set` 元素的双向迭代器。|  
|[const\_pointer](../Topic/hash_set::const_pointer.md)|一种类型，此类型提供指向 `const` 中的 `hash_set` 元素的指针。|  
|[const\_reference](../Topic/hash_set::const_reference.md)|一种类型，此类型提供对存储在 `const` 中的 `hash_set` 元素的引用（用于读取和执行 `const` 操作）。|  
|[const\_reverse\_iterator](../Topic/hash_set::const_reverse_iterator.md)|一种类型，此类型提供可读取 `const` 中的任何 `hash_set` 元素的双向迭代器。|  
|[difference\_type](../Topic/hash_set::difference_type.md)|一种有符号整数类型，此类型可用于表示 `hash_set` 中迭代器指向的元素间范围内的元素数量。|  
|[iterator](../Topic/hash_set::iterator.md)|一种类型，它提供可读取或修改 `hash_set` 中任何元素的双向迭代器。|  
|[key\_compare](../Topic/hash_set::key_compare.md)|一种提供函数对象的类型，该函数对象可比较两个排序键以确定 `hash_set` 中两个元素的相对顺序。|  
|[key\_type](../Topic/hash_set::key_type.md)|一种类型，它描述当作为排序键存储为其容量中 `hash_set` 的元素的对象。|  
|[指针](../Topic/hash_set::pointer.md)|一种类型，它提供指向 `hash_set` 中的某个元素的指针。|  
|[引用](../Topic/hash_set::reference.md)|一种类型，此类型提供对存储在 `hash_set` 中的元素的引用。|  
|[reverse\_iterator](../Topic/hash_set::reverse_iterator.md)|一种类型，此类型提供可读取或修改反向 `hash_set` 中的元素的双向迭代器。|  
|[size\_type](../Topic/hash_set::size_type.md)|可表示 `hash_set` 中元素数量的无符号整数类型。|  
|[value\_compare](../Topic/hash_set::value_compare.md)|一种类型，它提供两个函数对象：一个是类比较二元谓词，可以比较 `hash_set` 的两个元素值以确定其相对顺序，另一个是一元谓词，可对元素进行哈希处理。|  
|[value\_type](../Topic/hash_set::value_type.md)|一种类型，它描述当作为值存储为其容量中 `hash_set` 的元素的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[begin](../Topic/hash_set::begin.md)|返回一个迭代器，此迭代器用于发现 `hash_set` 中的第一个元素。|  
|[hash\_set::cbegin](../Topic/hash_set::cbegin.md)|返回一个常量迭代器，此迭代器用于发现 `hash_set` 中的第一个元素。|  
|[hash\_set::cend](../Topic/hash_set::cend.md)|返回一个常量迭代器，此迭代器用于发现 `hash_set` 中最后一个元素之后的位置。|  
|[清除](../Topic/hash_set::clear.md)|清除 `hash_set` 的所有元素。|  
|[count](../Topic/hash_set::count.md)|返回 `hash_set` 中其键与指定为参数的键匹配的元素数量。|  
|[hash\_set::crbegin](../Topic/hash_set::crbegin.md)|返回一个常量迭代器，此迭代器用于发现反向 `hash_set` 中的第一个元素。|  
|[hash\_set::crend](../Topic/hash_set::crend.md)|返回一个常量迭代器，此迭代器用于发现反向 `hash_set` 中最后一个元素之后的位置。|  
|[hash\_set::emplace](../Topic/hash_set::emplace.md)|将就地构造的元素插入到 `hash_set`。|  
|[hash\_set::emplace\_hint](../Topic/hash_set::emplace_hint.md)|将就地构造的元素插入到 `hash_set`，附带位置提示。|  
|[空](../Topic/hash_set::empty.md)|测试 `hash_set` 是否为空。|  
|[end](../Topic/hash_set::end.md)|返回一个迭代器，此迭代器用于发现 `hash_set` 中最后一个元素之后的位置。|  
|[equal\_range](../Topic/hash_set::equal_range.md)|返回一对迭代器，这两个迭代器分别用于发现 `hash_set` 中其键大于指定键的第一个元素，以及 `hash_set` 中其键等于或大于指定键的第一个元素。|  
|[erase](../Topic/hash_set::erase.md)|从 `hash_set` 中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。|  
|[find](../Topic/hash_set::find.md)|返回一个迭代器，此迭代器用于发现 `hash_set` 中其键与指定键等效的元素的位置。|  
|[get\_allocator](../Topic/hash_set::get_allocator.md)|返回用于构造 `allocator` 的 `hash_set` 对象的副本。|  
|[插入](../Topic/hash_set::insert.md)|将一个元素或元素范围插入到 `hash_set`。|  
|[key\_comp](../Topic/hash_set::key_comp.md)|检索用于对 `hash_set` 中的键进行排序的比较对象副本。|  
|[lower\_bound](../Topic/hash_set::lower_bound.md)|返回一个迭代器，此迭代器指向 `hash_set` 中其键等于或大于指定键的第一个元素。|  
|[max\_size](../Topic/hash_set::max_size.md)|返回 `hash_set` 的最大长度。|  
|[rbegin](../Topic/hash_set::rbegin.md)|返回一个迭代器，此迭代器用于发现反向 `hash_set` 中的第一个元素。|  
|[rend](../Topic/hash_set::rend.md)|返回一个迭代器，此迭代器用于发现反向 `hash_set` 中最后一个元素之后的位置。|  
|[size](../Topic/hash_set::size.md)|返回 `hash_set` 中的元素数量。|  
|[swap](../Topic/hash_set::swap.md)|交换两个 `hash_set` 的元素。|  
|[upper\_bound](../Topic/hash_set::upper_bound.md)|返回一个迭代器，此迭代器指向 `hash_set` 中其键等于或大于指定键的第一个元素。|  
|[value\_comp](../Topic/hash_set::value_comp.md)|检索哈希特征对象的副本，该哈希特征对象用于对 `hash_set` 中的元素键值进行哈希处理和排序。|  
  
### 运算符  
  
|||  
|-|-|  
|[hash\_set::operator\=](../Topic/hash_set::operator=.md)|将一个 `hash_set` 中的元素替换为另一 `hash_set` 副本。|  
  
## 要求  
 **标头：**\<hash\_set\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)