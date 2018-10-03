---
title: hash_multiset 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- hash_set/stdext::hash_multiset
- hash_set/stdext::hash_multiset::allocator_type
- hash_set/stdext::hash_multiset::const_iterator
- hash_set/stdext::hash_multiset::const_pointer
- hash_set/stdext::hash_multiset::const_reference
- hash_set/stdext::hash_multiset::const_reverse_iterator
- hash_set/stdext::hash_multiset::difference_type
- hash_set/stdext::hash_multiset::iterator
- hash_set/stdext::hash_multiset::key_compare
- hash_set/stdext::hash_multiset::key_type
- hash_set/stdext::hash_multiset::pointer
- hash_set/stdext::hash_multiset::reference
- hash_set/stdext::hash_multiset::reverse_iterator
- hash_set/stdext::hash_multiset::size_type
- hash_set/stdext::hash_multiset::value_compare
- hash_set/stdext::hash_multiset::value_type
- hash_set/stdext::hash_multiset::begin
- hash_set/stdext::hash_multiset::cbegin
- hash_set/stdext::hash_multiset::cend
- hash_set/stdext::hash_multiset::clear
- hash_set/stdext::hash_multiset::count
- hash_set/stdext::hash_multiset::crbegin
- hash_set/stdext::hash_multiset::crend
- hash_set/stdext::hash_multiset::emplace
- hash_set/stdext::hash_multiset::emplace_hint
- hash_set/stdext::hash_multiset::empty
- hash_set/stdext::hash_multiset::end
- hash_set/stdext::hash_multiset::equal_range
- hash_set/stdext::hash_multiset::erase
- hash_set/stdext::hash_multiset::find
- hash_set/stdext::hash_multiset::get_allocator
- hash_set/stdext::hash_multiset::insert
- hash_set/stdext::hash_multiset::key_comp
- hash_set/stdext::hash_multiset::lower_bound
- hash_set/stdext::hash_multiset::max_size
- hash_set/stdext::hash_multiset::rbegin
- hash_set/stdext::hash_multiset::rend
- hash_set/stdext::hash_multiset::size
- hash_set/stdext::hash_multiset::swap
- hash_set/stdext::hash_multiset::upper_bound
- hash_set/stdext::hash_multiset::value_comp
dev_langs:
- C++
helpviewer_keywords:
- stdext::hash_multiset
- stdext::hash_multiset::allocator_type
- stdext::hash_multiset::const_iterator
- stdext::hash_multiset::const_pointer
- stdext::hash_multiset::const_reference
- stdext::hash_multiset::const_reverse_iterator
- stdext::hash_multiset::difference_type
- stdext::hash_multiset::iterator
- stdext::hash_multiset::key_compare
- stdext::hash_multiset::key_type
- stdext::hash_multiset::pointer
- stdext::hash_multiset::reference
- stdext::hash_multiset::reverse_iterator
- stdext::hash_multiset::size_type
- stdext::hash_multiset::value_compare
- stdext::hash_multiset::value_type
- stdext::hash_multiset::begin
- stdext::hash_multiset::cbegin
- stdext::hash_multiset::cend
- stdext::hash_multiset::clear
- stdext::hash_multiset::count
- stdext::hash_multiset::crbegin
- stdext::hash_multiset::crend
- stdext::hash_multiset::emplace
- stdext::hash_multiset::emplace_hint
- stdext::hash_multiset::empty
- stdext::hash_multiset::end
- stdext::hash_multiset::equal_range
- stdext::hash_multiset::erase
- stdext::hash_multiset::find
- stdext::hash_multiset::get_allocator
- stdext::hash_multiset::insert
- stdext::hash_multiset::key_comp
- stdext::hash_multiset::lower_bound
- stdext::hash_multiset::max_size
- stdext::hash_multiset::rbegin
- stdext::hash_multiset::rend
- stdext::hash_multiset::size
- stdext::hash_multiset::swap
- stdext::hash_multiset::upper_bound
- stdext::hash_multiset::value_comp
ms.assetid: 0580397a-a76e-40ad-aea2-5c6f3a9d0a21
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce9e442ce9a53c44fd4fe37b6991952b76f13cec
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235966"
---
# <a name="hashmultiset-class"></a>hash_multiset 类

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

容器类 hash_multiset 是 C++ 标准库的扩展，用于存储和快速检索集合中的数据，此集合中包含的元素值用作键值并且不要求具有唯一性。

## <a name="syntax"></a>语法

```cpp
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>
class hash_multiset
```

### <a name="parameters"></a>参数

*Key*<br/>
要存储在 hash_multiset 中的元素数据类型。

*特征*<br/>
该类型包括两个函数对象，其中一个类，它是比较二元谓词，能够将两个元素值作为排序键以确定其相对顺序是为无符号的元素的一元谓词映射键值的哈希函数进行比较类型的整数`size_t`。 此自变量是可选自变量，默认值为 `hash_compare<Key, less<Key> >`。

*分配器*<br/>
一种类型，它表示存储的分配器对象，该分配器对象封装有关 hash_multiset 的内存分配和解除分配的详细信息。 此参数是可选参数，默认值为 `allocator<Key>`。

## <a name="remarks"></a>备注

hash_multiset 是：

- 大小可变的关联容器，支持基于关联键值高效检索元素值。 此外，它是简单的关联容器，因为它的元素值即为它的键值。

- 可逆，因为它提供双向迭代器来访问其元素。

- 经过哈希处理，因为其元素分组到了哈希桶中，哈希桶基于应用于元素键值的哈希函数的值。

- 唯一，每个元素必须具有唯一键。 由于 hash_multiset 还是简单的关联容器，因此其元素也是唯一的。

- 一个模板类，由于其提供的功能是一般功能，因此与作为元素或键包含的特定数据类型无关。 用于元素和键的数据类型作为类模板以及比较函数和分配器中的参数指定。

哈希算法相比于排序比较的主要优点是效率更高；在排序技术中，时间与容器中元素数的对数成正比，而成功的哈希算法可在恒定的平均时间内执行插入、删除和查找操作。 不能直接更改集中元素的值。 必须先删除旧值，才能插入具有新值的元素。

容器类型选择通常应根据应用程序所需的搜索和插入的类型。 经过哈希处理的关联容器针对查找、插入和删除操作进行了优化。 与设计良好的哈希函数一起使用时，显式支持这些操作的成员函数较为高效，执行这些操作的时间为平均恒定值，而不取决于容器中元素的数目。 精心设计的哈希函数将生成统一分布的哈希值，并将最大限度地减少冲突数量，据说当非重复键值映射到相同的哈希值时会发生冲突。 在最坏情况下，使用可能是最差的哈希运算，操作数量与序列中的元素数量成比例（线性时间）。

当应用程序满足将值与其键关联的条件时，应选择 hash_multiset 作为关联容器。 hash_multiset 的元素可以是多个，并用作其自己的排序键，因此键不是唯一的。 此类结构的模型是排序列表，如关键字排序列表，其中关键字可以出现多次。 如果不允许关键字多次出现，则应使用 hash_set 作为适当的容器结构。 如果将唯一定义作为值附加到唯一关键字的列表，则 hash_map 应为包含此数据的适当结构。 如果定义不唯一，则应选择 hash_multimap 作为容器。

hash_multiset 通过调用所存储的 [value_compare](#value_compare) 类型的哈希特征对象，对其控制的序列进行排序。 此存储对象可通过调用成员函数 [key_comp](#key_comp) 进行访问。 此类函数对象的行为必须与类的对象相同`hash_compare<Key, less<Key> >`。 具体而言，对于所有值*键*类型的`Key`，在调用`Trait(Key)`生成的类型的值的分布`size_t`。

通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。 二元谓词 *f*( *x*, *y*) 是包含两个参数对象（x 和 y）以及一个返回值（true 或 false）的函数对象。 如果二元谓词具有自反性、反对称性和传递性且等效可传递，对 hash_multiset 进行的排序将为严格弱排序，其中在 *f*( *x*, *y*) 和 *f*( *y*, *x*) 均为 false 时两个对象 x 和 y 定义为等效。 如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。

受控序列中元素的实际顺序取决于哈希函数、排序函数和存储在容器对象中的哈希表的当前大小。 无法确定哈希表的当前大小，因此通常无法预测受控序列中元素的顺序。 插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。

hash_multiset 类提供的迭代器是双向迭代器，但类成员函数 insert 和 hash_multiset 具有较弱输入迭代器将用作模板参数的版本，较弱输入迭代器的功能需求比双向迭代器类保证的功能需求更少。 不同的迭代器概念形成一个系列，通过它们的功能优化相关联。 每个迭代器概念有它自己的 hash_multiset 要求，使用这些概念的算法必须根据迭代器类型提供的要求限制它们的假设。 可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。 这是最小的功能 hash_multiset，但足以按有意义的方式提供类成员函数上下文中的迭代器范围 [ `first`, `last`)。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[hash_multiset](#hash_multiset)|构造一个空的或者是其他某个 `hash_multiset` 的全部或部分副本的 `hash_multiset`。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[allocator_type](#allocator_type)|一种类型，此类型表示 `allocator` 对象的 `hash_multiset` 类。|
|[const_iterator](#const_iterator)|一个类型，提供双向迭代器可读取**const**中的元素`hash_multiset`。|
|[const_pointer](#const_pointer)|提供一个指针指向的类型**const**中的元素`hash_multiset`。|
|[const_reference](#const_reference)|提供对引用的类型**const**元素存储在`hash_multiset`用于读取和执行**const**操作。|
|[const_reverse_iterator](#const_reverse_iterator)|一个类型，提供双向迭代器可读取任何**const**中的元素`hash_multiset`。|
|[difference_type](#difference_type)|一种带符号的整数类型，它提供发现同一 `hash_multiset` 中的元素的两个迭代器之间的差异。|
|[Iterator](#iterator)|一种类型，它提供可读取或修改 `hash_multiset` 中任何元素的双向迭代器。|
|[key_compare](#key_compare)|一种提供函数对象的类型，该函数对象可比较两个排序键以确定 `hash_multiset` 中两个元素的相对顺序。|
|[key_type](#key_type)|一种类型，它描述当作为排序键存储为其容量中 `hash_set` 的元素的对象。|
|[pointer](#pointer)|一种类型，它提供指向 `hash_multiset` 中的某个元素的指针。|
|[reference](#reference)|一种类型，此类型提供对存储在 `hash_multiset` 中的元素的引用。|
|[reverse_iterator](#reverse_iterator)|一种类型，此类型提供可读取或修改反向 `hash_multiset` 中的元素的双向迭代器。|
|[size_type](#size_type)|可表示 `hash_multiset` 中元素数量的无符号整数类型。|
|[value_compare](#value_compare)|一种类型，它提供两个函数对象：一个是类比较二元谓词，可以比较 `hash_multiset` 的两个元素值以确定其相对顺序，另一个是一元谓词，可对元素进行哈希处理。|
|[value_type](#value_type)|一种类型，它描述当作为值存储为其容量中 `hash_multiset` 的元素的对象。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[begin](#begin)|返回一个迭代器，此迭代器用于发现 `hash_multiset` 中的第一个元素。|
|[cbegin](#cbegin)|返回一个常量迭代器，此迭代器用于发现 `hash_multiset` 中的第一个元素。|
|[cend](#cend)|返回一个常量迭代器，此迭代器用于发现 `hash_multiset` 中最后一个元素之后的位置。|
|[clear](#clear)|清除 `hash_multiset` 的所有元素。|
|[count](#count)|返回 `hash_multiset` 中其键与参数指定键匹配的元素数量|
|[crbegin](#crbegin)|返回一个常量迭代器，此迭代器用于发现反向 `hash_multiset` 中的第一个元素。|
|[crend](#crend)|返回一个常量迭代器，此迭代器用于发现反向 `hash_multiset` 中最后一个元素之后的位置。|
|[emplace](#emplace)|将就地构造的元素插入到 `hash_multiset`。|
|[emplace_hint](#emplace_hint)|将就地构造的元素插入到 `hash_multiset`，附带位置提示。|
|[empty](#empty)|测试 `hash_multiset` 是否为空。|
|[end](#end)|返回一个迭代器，此迭代器用于发现 `hash_multiset` 中最后一个元素之后的位置。|
|[equal_range](#equal_range)|返回一对迭代器，这两个迭代器分别用于发现 `hash_multiset` 中其键大于指定键的第一个元素，以及 `hash_multiset` 中其键等于或大于指定键的第一个元素。|
|[erase](#erase)|从 `hash_multiset` 中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。|
|[find](#find)|返回一个迭代器，此迭代器用于发现 `hash_multiset` 中其键与指定键等效的元素的位置。|
|[get_allocator](#get_allocator)|返回用于构造 `allocator` 的 `hash_multiset` 对象的副本。|
|[insert](#insert)|将一个元素或元素范围插入到 `hash_multiset`。|
|[key_comp](#key_compare)|检索用于对 `hash_multiset` 中的键进行排序的比较对象副本。|
|[lower_bound](#lower_bound)|返回一个迭代器，此迭代器指向 `hash_multiset` 中其键等于或大于指定键的第一个元素。|
|[max_size](#max_size)|返回 `hash_multiset` 的最大长度。|
|[rbegin](#rbegin)|返回一个迭代器，此迭代器用于发现反向 `hash_multiset` 中的第一个元素。|
|[rend](#rend)|返回一个迭代器，此迭代器用于发现反向 `hash_multiset` 中最后一个元素之后的位置。|
|[size](#size)|返回 `hash_multiset` 中的元素数量。|
|[swap](#swap)|交换两个 `hash_multiset` 的元素。|
|[upper_bound](#upper_bound)|返回一个迭代器，此迭代器指向 `hash_multiset` 中其键等于或大于指定键的第一个元素。|
|[value_comp](#value_comp)|检索哈希特征对象的副本，该哈希特征对象用于对 `hash_multiset` 中的元素键值进行哈希处理和排序。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[hash_multiset::operator=](#op_eq)|将 hash_multiset 的元素替换为另一个 hash_multiset 的副本。|

## <a name="requirements"></a>要求

**标头：**\<hash_set>

**命名空间：** stdext

## <a name="allocator_type"></a>hash_multiset::allocator_type

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一个类型，它代表 hash_multiset 对象的分配器类。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>示例

有关使用 `allocator_type` 的示例，请参阅 [get_allocator](#get_allocator) 的示例

## <a name="begin"></a>hash_multiset::begin

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回一个迭代器，此迭代器用于发现 hash_multiset 中的第一个元素。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>返回值

一个双向迭代器，发现 hash_multiset 中的第一个元素或空 hash_multiset 后的位置。

### <a name="remarks"></a>备注

如果返回值`begin`分配给`const_iterator`，无法修改 hash_multiset 对象中的元素。 如果返回值`begin`分配给`iterator`，可以修改 hash_multiset 对象中的元素。

### <a name="example"></a>示例

```cpp
// hash_multiset_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.begin( );
   cout << "The first element of hms1 is " << *hms1_Iter << endl;

   hms1_Iter = hms1.begin( );
   hms1.erase( hms1_Iter );

   // The following 2 lines would err because the iterator is const
   // hms1_cIter = hms1.begin( );
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.begin( );
   cout << "The first element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The first element of hms1 is 1
The first element of hms1 is now 2
```

## <a name="cbegin"></a>hash_multiset::cbegin

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回一个常量迭代器，此迭代器用于发现 hash_multiset 中的第一个元素。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>返回值

一个常量双向迭代器，用于发现 [hash_multiset](../standard-library/hash-multiset-class.md) 中的第一个元素或空 `hash_multiset` 后的位置。

### <a name="remarks"></a>备注

由于使用 `cbegin` 的返回值，因此不能修改 `hash_multiset` 对象中的元素。

### <a name="example"></a>示例

```cpp
// hash_multiset_cbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cbegin( );
   cout << "The first element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
```

## <a name="cend"></a>hash_multiset::cend

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回一个常量迭代器，此迭代器用于 hash_multiset 中最后一个元素之后的位置。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>返回值

用于发现 [hash_multiset](../standard-library/hash-multiset-class.md) 中最后一个元素之后的位置的常量双向迭代器。 如果 `hash_multiset` 为空，则 `hash_multiset::cend == hash_multiset::begin`。

### <a name="remarks"></a>备注

`cend` 用于测试迭代器是否已到达其 `hash_multiset` 的末尾。 不应对 `cend` 返回的值取消引用。

### <a name="example"></a>示例

```cpp
// hash_multiset_cend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cend( );
   hs1_cIter--;
   cout << "The last element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
```

## <a name="clear"></a>hash_multiset::clear

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

清除 hash_multiset 的所有元素。

```cpp
void clear();
```

### <a name="remarks"></a>备注

### <a name="example"></a>示例

```cpp
// hash_multiset_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 1 );
   hms1.insert( 2 );

   cout << "The size of the hash_multiset is initially " << hms1.size( )
        << "." << endl;

   hms1.clear( );
   cout << "The size of the hash_multiset after clearing is "
        << hms1.size( ) << "." << endl;
}
```

```Output
The size of the hash_multiset is initially 2.
The size of the hash_multiset after clearing is 0.
```

## <a name="const_iterator"></a>hash_multiset::const_iterator

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一个类型，用于提供可读取 hash_multiset 中 **const** 元素的双向迭代器。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>备注

`const_iterator` 类型不能用于修改元素的值。

### <a name="example"></a>示例

有关使用 `const_iterator` 的示例，请参阅 [begin](#begin) 的示例。

## <a name="const_pointer"></a>hash_multiset::const_pointer

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一种类型，此类型提供指向 hash_multiset 中的 **const** 元素的指针。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>备注

`const_pointer` 类型不能用于修改元素的值。

在大多数情况下，应使用 [const_iterator](#const_iterator) 访问 **const** hash_multiset 对象中的元素。

## <a name="const_reference"></a>hash_multiset::const_reference

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一种类型，此类型提供对用于读取和执行 **const** 操作的 hash_multiset 中存储的 **const** 元素的引用。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>备注

### <a name="example"></a>示例

```cpp
// hash_multiset_const_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_multiset is 10.
```

## <a name="const_reverse_iterator"></a>hash_multiset::const_reverse_iterator

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一个类型，用于提供可读取 hash_multiset 中任何 **const** 元素的双向迭代器。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>备注

`const_reverse_iterator` 类型无法修改元素的值，它用于反向循环访问 hash_multiset。

### <a name="example"></a>示例

有关如何声明和使用 `const_reverse_iterator` 的示例，请参阅 [rend](#rend) 的示例。

## <a name="count"></a>hash_multiset::count

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回 hash_multiset 中其键与指定了参数的键匹配的元素数量。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>参数

*key*<br/>
要从 hash_multiset 中进行匹配的元素的键。

### <a name="return-value"></a>返回值

带有指定了参数的键的 hash_multiset 中的元素数量。

### <a name="remarks"></a>备注

成员函数返回在以下范围内的元素数目：

[ `lower_bound` (_ `Key` ), `upper_bound` (\_ `Key` ) ).

### <a name="example"></a>示例

下面的示例演示 hash_multiset::count 成员函数的用法。

```cpp
// hash_multiset_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1;
    hash_multiset<int>::size_type i;

    hms1.insert(1);
    hms1.insert(1);

    // Keys do not need to be unique in hash_multiset,
    // so duplicates may exist.
    i = hms1.count(1);
    cout << "The number of elements in hms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hms1.count(2);
    cout << "The number of elements in hms1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hms1 with a sort key of 1 is: 2.
The number of elements in hms1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>hash_multiset::crbegin

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回一个常量迭代器，此迭代器用于发现反向 hash_multiset 中的第一个元素的位置。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>返回值

发现反向 [hash_multiset](../standard-library/hash-multiset-class.md) 中的第一个元素或发现曾是非反向 `hash_multiset` 中的最后一个元素的常量反向双向迭代器。

### <a name="remarks"></a>备注

`crbegin` 用于反向 `hash_multiset`，正如 [hash_multiset::begin](#begin) 用于 `hash_multiset` 一样。

返回值为 `crbegin` 时，无法修改 `hash_multiset` 对象。

`crbegin` 可用于向后循环访问 `hash_multiset`。

### <a name="example"></a>示例

```cpp
// hash_multiset_crbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
```

## <a name="crend"></a>hash_multiset::crend

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回一个常量迭代器，此迭代器用于发现反向 hash_multiset 中最后一个元素之后的位置。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>返回值

一个常量反向双向迭代器，用于发现反向 [hash_multiset](../standard-library/hash-multiset-class.md) 中最后一个元素之后的位置（非反向 `hash_multiset` 中第一个元素之前的位置）。

### <a name="remarks"></a>备注

`crend` 用于反向 `hash_multiset`，正如 [hash_multiset::end](#end) 用于 `hash_multiset` 一样。

返回值为 `crend` 时，无法修改 `hash_multiset` 对象。

`crend` 可用于测试反向迭代器是否已到达其 hash_multiset 的末尾。

### <a name="example"></a>示例

```cpp
// hash_multiset_crend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
```

## <a name="difference_type"></a>hash_multiset::difference_type

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一种带符号的整数类型，它提供发现同一 hash_multiset 中的元素的两个迭代器之间的差异。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>备注

`difference_type` 是通过容器迭代器减少或递增时返回的类型。 `difference_type` 通常用于表示迭代器 `first` 和 `last` 之间的范围 [ `first`, `last`) 内元素的数目，包括 `first` 指向的元素以及那一系列元素，但不包括 `last` 指向的元素。

请注意，尽管 `difference_type` 可用于满足输入迭代器（包括 set 等可逆容器支持的双向迭代器类）要求的所有迭代器， 但仅 vector 或 deque 等随机访问容器提供的随机访问迭代器支持迭代器间的减法操作。

### <a name="example"></a>示例

```cpp
// hash_multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter, hms1_bIter, hms1_eIter;

   hms1.insert( 20 );
   hms1.insert( 10 );

   // hash_multiset elements need not be unique
   hms1.insert( 20 );

   hms1_bIter = hms1.begin( );
   hms1_eIter = hms1.end( );

   hash_multiset <int>::difference_type   df_typ5, df_typ10,
        df_typ20;

   df_typ5 = count( hms1_bIter, hms1_eIter, 5 );
   df_typ10 = count( hms1_bIter, hms1_eIter, 10 );
   df_typ20 = count( hms1_bIter, hms1_eIter, 20 );

   // The keys & hence the elements of a hash_multiset
   // need not be unique and may occur multiple times
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_multiset hms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_multiset hms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_multiset hms1.\n";

   // Count the number of elements in a hash_multiset
   hash_multiset <int>::difference_type  df_count = 0;
   hms1_Iter = hms1.begin( );
   while ( hms1_Iter != hms1_eIter)
   {
      df_count++;
      hms1_Iter++;
   }

   cout << "The number of elements in the hash_multiset hms1 is "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_multiset hms1.
The number '10' occurs 1 times in hash_multiset hms1.
The number '20' occurs 2 times in hash_multiset hms1.
The number of elements in the hash_multiset hms1 is 3.
```

## <a name="emplace"></a>hash_multiset::emplace

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

将就地构造的元素插入到 hash_multiset 中。

```cpp
template <class ValTy>
iterator insert(ValTy&& val);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|*val*|要插入 [hash_multiset](../standard-library/hash-multiset-class.md) 的元素的值，除非 `hash_multiset` 已包含该元素，或更宽泛地说，包含其键经过等效排序的元素。|

### <a name="return-value"></a>返回值

`emplace` 成员函数将返回一个指向新元素插入位置的迭代器。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

```cpp
// hash_multiset_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms3;
   string str1("a");

   hms3.emplace(move(str1));
   cout << "After the emplace insertion, hms3 contains "
      << *hms3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms3 contains a.
```

## <a name="emplace_hint"></a>hash_multiset::emplace_hint

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

将就地构造的元素插入到 hash_multiset，并附带位置提示。

```cpp
template <class ValTy>
iterator insert(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|*val*|要插入 [hash_multiset](../standard-library/hash-multiset-class.md) 的元素的值，除非 `hash_multiset` 已包含该元素，或更宽泛地说，包含其键经过等效排序的元素。|
|*_Where*|开始搜索正确插入点的位置。 (插入可发生在分期常量时间内，而非对数时间，如果插入点紧随 *_Where*。)|

### <a name="return-value"></a>返回值

[hash_multiset::emplace](#emplace) 成员函数将返回一个指向 `hash_multiset` 中新元素插入位置的迭代器。

### <a name="remarks"></a>备注

插入可发生在分期常量时间内，而非对数时间，如果插入点紧随 *_Where*。

### <a name="example"></a>示例

```cpp
// hash_multiset_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms1;
   string str1("a");

   hms1.insert(hms1.begin(), move(str1));
   cout << "After the emplace insertion, hms1 contains "
      << *hms1.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms1 contains a.
```

## <a name="empty"></a>hash_multiset::empty

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

测试 hash_multiset 是否为空。

```cpp
bool empty() const;
```

### <a name="return-value"></a>返回值

如果 hash_multiset 为空，则为 **true**；如果 hash_multiset 不为空，则为 **false**。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

```cpp
// hash_multiset_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2;
   hms1.insert ( 1 );

   if ( hms1.empty( ) )
      cout << "The hash_multiset hms1 is empty." << endl;
   else
      cout << "The hash_multiset hms1 is not empty." << endl;

   if ( hms2.empty( ) )
      cout << "The hash_multiset hms2 is empty." << endl;
   else
      cout << "The hash_multiset hms2 is not empty." << endl;
}
```

```Output
The hash_multiset hms1 is not empty.
The hash_multiset hms2 is empty.
```

## <a name="end"></a>hash_multiset::end

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回一个迭代器，此迭代器用于发现 hash_multiset 中最后一个元素之后的位置。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>返回值

用于发现 hash_multiset 中最后一个元素之后的位置的双向迭代器。 如果 hash_multiset 为空，则 hash_multiset::end == hash_multiset::begin。

### <a name="remarks"></a>备注

`end` 用于测试迭代器是否已到达其 hash_multiset 的末尾。 不应对 `end` 返回的值取消引用。

### <a name="example"></a>示例

```cpp
// hash_multiset_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: iterator hms1_Iter;
   hash_multiset <int> :: const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.end( );
   hms1_Iter--;
   cout << "The last element of hms1 is " << *hms1_Iter << endl;

   hms1.erase( hms1_Iter );

   // The following 3 lines would err because the iterator is const
   // hms1_cIter = hms1.end( );
   // hms1_cIter--;
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.end( );
   hms1_cIter--;
   cout << "The last element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The last element of hms1 is 3
The last element of hms1 is now 2
```

## <a name="equal_range"></a>hash_multiset::equal_range

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回一对迭代器，这两个迭代器分别用于发现 hash_multiset 中其键大于指定键的第一个元素，以及 hash_multiset 中其键等于或大于指定键的第一个元素。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>参数

*key*<br/>
要与当前搜索的 hash_multiset 中元素的排序键进行比较的参数键。

### <a name="return-value"></a>返回值

一对迭代器，其中第一个是键的 [lower_bound](#lower_bound)，第二个是键的 [upper_bound](#upper_bound)。

若要访问成员函数返回的 `pr` 对的第一个迭代器，请使用 `pr`. **first**；若要取消引用下界迭代器，请使用 \*( `pr`. **first**)。 若要访问成员函数返回的 `pr` 对的第二个迭代器，请使用 `pr`. **second**；若要取消引用上界迭代器，请使用 \*( `pr`. **second**)。

### <a name="example"></a>示例

```cpp
// hash_multiset_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multiset<int> IntHSet;
   IntHSet hms1;
   hash_multiset <int> :: const_iterator hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hms1.end( ) )
      && ( p2.second == hms1.end( ) ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20
in the hash_multiset hms1 is: 30.
The lower bound of the element with a key of 20
in the hash_multiset hms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_multiset hms1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>hash_multiset::erase

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

从 hash_multiset 中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>参数

*_Where*<br/>
要从 hash_multiset 移除的元素的位置。

*first*<br/>
要从 hash_multiset 中移除的第一个元素的位置。

*最后一个*<br/>
紧接要从 hash_multiset 中移除的最后一个元素的位置。

*key*<br/>
要从 hash_multiset 中移除的元素的键。

### <a name="return-value"></a>返回值

对于前两个成员函数，可为指定已移除的任何元素之外保留的第一个元素；如果此类元素不存在，则为指向 hash_multiset 末尾的指针。 对于第三个成员函数，是已从 hash_multiset 中移除的元素的数目。

### <a name="remarks"></a>备注

成员函数从不引发异常。

### <a name="example"></a>示例

下面的示例演示 hash_multiset::erase 成员函数的用法。

```cpp
// hash_multiset_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1, hms2, hms3;
    hash_multiset<int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multiset<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hms1.insert(i);
        hms2.insert(i * i);
        hms3.insert(i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hms1.begin();
    hms1.erase(Iter1);

    cout << "After the 2nd element is deleted,\n"
         << "the hash_multiset hms1 is:" ;
    for (pIter = hms1.begin(); pIter != hms1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hms2.begin();
    Iter2 = --hms2.end();
    hms2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted,\n"
         << "the hash_multiset hms2 is:" ;
    for (pIter = hms2.begin(); pIter != hms2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hms3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hms3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hms3.begin();
    hms3.erase(Iter1);

    cout << "After another element with a key "
         << "equal to that of the 2nd element\n"
         << "is deleted, the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted,
the hash_multiset hms1 is: 1 3 4.
After the middle two elements are deleted,
the hash_multiset hms2 is: 16 4.
After the element with a key of 2 is deleted,
the hash_multiset hms3 is: 0 1 3.
The number of elements removed from hms3 is: 1.
After another element with a key equal to that of the 2nd element
is deleted, the hash_multiset hms3 is: 0 3.
```

## <a name="find"></a>hash_multiset::find

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回一个迭代器，此迭代器用于发现 hash_multiset 中其键与指定键等效的元素的位置。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>参数

*key*<br/>
要与当前搜索的 hash_multiset 中元素的排序键匹配的参数键。

### <a name="return-value"></a>返回值

一个 [迭代器](#iterator) 或 [const_iterator](#const_iterator)，此迭代器发现等效于指定键的元素的位置，或者如果找不到此键的匹配项，则发现 hash_multiset 中最后一个元素后面的位置。

### <a name="remarks"></a>备注

此成员函数返回其排序键与的 hash_multiset 中元素的迭代器`equivalent`的参数键在排序的二元谓词基于小于-比较关系。

如果返回值`find`分配给`const_iterator`，无法修改 hash_multiset 对象。 如果返回值`find`分配给`iterator`，可以修改 hash_multiset 对象。

### <a name="example"></a>示例

```cpp
// hash_multiset_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.find( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // The element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.find( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The element of hash_multiset hms1 with a key of 20 is: 20.
The hash_multiset hms1 doesn't have an element with a key of 40.
The element of hms1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>hash_multiset::get_allocator

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回用于构造 hash_multiset 的分配器对象的一个副本。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>返回值

由 hash_multiset 用来管理内存的分配器，即类的模板参数 `Allocator`。

有关 `Allocator` 的详细信息，请参阅 [hash_multiset 类](../standard-library/hash-multiset-class.md)主题的备注部分。

### <a name="remarks"></a>备注

hash_multiset 类的分配器指定类管理存储的方式。 C++ 标准库容器类提供的默认分配器足以满足大多编程需求。 编写和使用你自己的分配器类是高级 C++ 主题。

### <a name="example"></a>示例

```cpp
// hash_multiset_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_multiset <int, hash_compare <int, less<int> > > hms1;
   hash_multiset <int, hash_compare <int, greater<int> > > hms2;
   hash_multiset <double, hash_compare <double,
      less<double> >, allocator<double> > hms3;

   hash_multiset <int, hash_compare <int,
      greater<int> > >::allocator_type hms2_Alloc;
   hash_multiset <double>::allocator_type hms3_Alloc;
   hms2_Alloc = hms2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms3.max_size( ) <<  "." << endl;

   // The following lines create a hash_multiset hms4
   // with the allocator of hash_multiset hms1.
   hash_multiset <int>::allocator_type hms4_Alloc;
   hash_multiset <int> hms4;
   hms4_Alloc = hms2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hms2_Alloc == hms4_Alloc )
   {
      cout << "The allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="hash_multiset"></a>hash_multiset::hash_multiset

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

构造一个空的或者是其他某个 `hash_multiset` 的全部或部分副本的 `hash_multiset`。

```cpp
hash_multiset();

explicit hash_multiset(
    const Traits& Comp);

hash_multiset(
    const Traits& Comp,
    const Allocator& Al);

hash_multiset(
    const hash_multiset<Key, Traits, Allocator>& Right);

hash_multiset(
    hash_multiset&& Right
};
hash_multiset (initializer_list<Type> IList);

hash_multiset(
    initializer_list<Tu[e> IList, const Compare& Comp):
hash_multiset(
    initializer_list<Type> IList, const Compare& Comp, const Allocator& Al);

template <class InputIterator>
hash_multiset(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_multiset(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_multiset(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|*Al*|要用于此 `hash_multiset` 对象的存储分配器类，默认为 `Allocator`。|
|*Comp*|用于对 `hash_multiset` 中元素排序的类型 `const Traits` 的比较函数，默认为 `hash_compare`。|
|右侧|所构造的 `hash_multiset` 要作为其副本的 `hash_multiset`。|
|*第一个*|要复制的范围元素中的第一个元素的位置。|
|*最后一个*|要复制的元素范围以外的第一个元素的位置。|
|*IList*|包含要复制的元素的 initializer_list。|

### <a name="remarks"></a>备注

所有构造函数存储一类分配器对象，此对象管理 `hash_multiset` 的内存存储，且稍后可通过调用 [hash_multiset::get_allocator](#get_allocator) 返回此对象。 此分配器参数在类声明中常省略，并预处理用于代替备用分配器的宏。

所有构造函数对其 hash_multiset 进行初始化。

所有构造函数会存储类型 `Traits` 的函数对象，此对象用于在 `hash_multiset` 的键之间建立顺序，且稍后可通过调用 [hash_multiset::key_comp](#key_comp) 进行返回。 有关 `Traits` 的详细信息，请参阅 [hash_multiset 类](../standard-library/hash-multiset-class.md)主题。

前三个构造函数指定空的初始`hash_multiset`，则第二个指定的比较函数类型 (*Comp*) 用于建立元素和第三个显式指定的顺序分配器类型 (*Al*) 使用。 关键字 **explicit** 取消某些种类的自动类型转换。

第四个构造函数移动`hash_multiset` `Right`。

第五个、第六个和第七个构造函数使用 initializer_list。

最后三个构造函数复制 `hash_multiset` 的范围 [ `First`, `Last`)，其指定类 Compare 的比较函数类型和分配器的明确性更高。

哈希集容器中元素的实际位置取决于哈希函数、ordering 函数和哈希表的当前大小，且通常无法像在 set 容器中那样可进行预测，因为在 set 容器中该位置仅由 ordering 函数决定。

## <a name="insert"></a>hash_multiset::insert

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

将一个元素或元素范围插入到 hash_multiset 中。

```cpp
iterator insert(
    const Type& Val);

iterator insert(
    iterator Where,
    const Type& Al);

void insert(
    initializer_list<Type> IList);

iterator insert(
    const Type& Val);

iterator insert(
    Iterator Where,
    const Type& Val);

template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

template <class ValTy>
iterator insert(
    ValTy&& Val);

template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|*val*|要插入 hash_multiset 的元素的值，除非 hash_multiset 已包含该元素，或更宽泛地说，包含其键经过等效排序的元素。|
|*Where*|开始搜索正确插入点的位置。 （如果插入点紧随 `_Where`，则插入可发生在分期常量时间内，而非对数时间内。）|
|*第一个*|要从 hash_multiset 复制的第一个元素的位置。|
|*最后一个*|刚超出要从 hash_multiset 复制的最后一个元素的位置。|
|*IList*|包含要复制的元素的 initializer_list。|

### <a name="return-value"></a>返回值

前两个 insert 成员函数返回一个指向新元素插入位置的迭代器。

接下来的三个成员函数使用 initializer_list。

第三个个成员函数将元素值序列插入到 hash_multiset，它对应于迭代器在指定的 hash_multiset 的范围 [ `First`, `Last`) 中所处理的每一个元素。

### <a name="remarks"></a>备注

插入可发生在分期常量时间内插入，而非对数时间的提示版本，如果插入点紧随*其中*。

## <a name="iterator"></a>hash_multiset::iterator

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一种提供双向迭代器的类型，所提供的迭代器可读取或修改 hash_multiset 中的任何元素。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>备注

一种类型`iterator`可用于修改元素的值。

### <a name="example"></a>示例

示例，请参阅[开始](#begin)有关如何声明和使用的示例`iterator`。

## <a name="key_comp"></a>hash_multiset::key_comp

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

检索用于对 hash_multiset 中的键进行排序的比较对象的副本。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>返回值

返回 hash_multiset 模板参数*特征*，其中包含用于哈希和容器的元素进行排序的函数对象。

有关详细信息*特征*请参阅[hash_multiset 类](../standard-library/hash-multiset-class.md)主题。

### <a name="remarks"></a>备注

存储对象用于定义成员函数：

**bool operator**( **const Key&** *_xVal,* **const Key&** _ `yVal`);

如果 `_xVal` 在排序顺序中先于且不等于 `_yVal`，则该函数会返回 **true**。

请注意，[key_compare](#key_compare) 和 [value_compare](#value_compare) 皆是模板参数 *Traits* 的同义词。 对于 hash_set 和 hash_multiset 类，会同时提供这两种类型，且二者相同，但为实现与 hash_map 和 hash_multimap 类的兼容性时，二者则不同。

### <a name="example"></a>示例

```cpp
// hash_multiset_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > >hms1;
   hash_multiset<int, hash_compare < int, less<int> > >::key_compare kc1
          = hms1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hms1."
        << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
}
```

## <a name="key_compare"></a>hash_multiset::key_compare

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一种类型，它提供两个函数对象：一个是类比较二元谓词，可以比较 hash_multiset 的两个元素值以确定其相对顺序，另一个是一元谓词，可对元素进行哈希处理。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>备注

`key_compare` 是模板参数的同义词*特征*。

有关详细信息*特征*请参阅[hash_multiset 类](../standard-library/hash-multiset-class.md)主题。

请注意，`key_compare` 和 value_compare 皆是模板参数 *Traits* 的同义词。 对于 hash_set 和 hash_multiset 类，会同时提供这两种类型，且二者相同，但为实现与 hash_map 和 hash_multimap 类的兼容性时，二者则不同。

### <a name="example"></a>示例

有关如何声明和使用 `key_compare` 的示例，请参阅 [key_comp](#key_comp) 的示例。

## <a name="key_type"></a>hash_multiset::key_type

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一种提供函数对象的类型，该函数对象可比较排序键以确定 hash_multiset 中两个元素的相对顺序。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>备注

`key_type` 是模板参数的同义词*密钥*。

请注意，`key_type` 和 [value_type](../standard-library/hash-set-class.md#value_type) 皆是模板参数 *Key* 的同义词。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。

有关详细信息*键*，请参阅备注部分[hash_multiset 类](../standard-library/hash-multiset-class.md)主题。

### <a name="example"></a>示例

有关如何声明和使用 `key_type` 的示例，请参阅 [value_type](#value_type) 的示例。

## <a name="lower_bound"></a>hash_multiset::lower_bound

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回一个迭代器，此迭代器指向 hash_multiset 中其键等于或大于指定键的第一个元素。

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>参数

*key*<br/>
要与当前搜索的 hash_multiset 中元素的排序键进行比较的参数键。

### <a name="return-value"></a>返回值

一个 [iterator](#iterator) 或 [const_iterator](#const_iterator)，其会发现 hash_multiset 中其键等于或大于参数键的第一个元素的位置，或如果未找到键的匹配项，则发现 hash_multiset 中最后一个元素之后的位置。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

```cpp
// hash_multiset_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main() {
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.lower_bound( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator that addresses the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.lower_bound( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

## <a name="max_size"></a>hash_multiset::max_size

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回 hash_multiset 的最大长度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>返回值

hash_multiset 的最大可取长度。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

```cpp
// hash_multiset_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::size_type i;

   i = hms1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multiset is " << i << "." << endl;
}
```

## <a name="op_eq"></a>hash_multiset::operator=

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

将 hash_multiset 的元素替换为另一个 hash_multiset 的副本。

```cpp
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|*right*|[hash_multiset](../standard-library/hash-multiset-class.md)，正在复制到 `hash_multiset`。|

### <a name="remarks"></a>备注

在清除中的任何现有元素后`hash_multiset`，`operator=`复制或移动的内容*右*到`hash_multiset`。

### <a name="example"></a>示例

```cpp
// hash_multiset_operator_as.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<int> v1, v2, v3;
   hash_multiset<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>hash_multiset::pointer

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一种类型，此类型提供指向 hash_multiset 中元素的指针。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>备注

一种类型`pointer`可用于修改元素的值。

在大多数情况下，应使用 [iterator](#iterator) 访问多重集对象中的元素。

## <a name="rbegin"></a>hash_multiset::rbegin

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回一个迭代器，此迭代器用于发现反向 hash_multiset 中的第一个元素。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>返回值

发现反向 hash_multiset 中的第一个元素或发现曾是非反向 hash_multiset 中的最后一个元素的反向双向迭代器。

### <a name="remarks"></a>备注

`rbegin` 用于反向 hash_multiset，正如 [begin](#begin) 用于 hash_multiset 一样。

如果将 `rbegin` 的返回值赋给 `const_reverse_iterator`，则无法修改 hash_multiset 对象。 如果将 `rbegin` 的返回值赋给 `reverse_iterator`，则可修改 hash_multiset 对象。

`rbegin` 可用于向后循环访问 hash_multiset。

### <a name="example"></a>示例

```cpp
// hash_multiset_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // throught a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // throught a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << endl;

   // A hash_multiset element can be erased by dereferencing to its key
   hms1_rIter = hms1.rbegin( );
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_multiset is "<< *hms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
The hash_multiset is: 10 20 30
The reversed hash_multiset is: 30 20 10
After the erasure, the first element in the reversed hash_multiset is 20.
```

## <a name="reference"></a>hash_multiset::reference

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一种类型，此类型提供对存储在 hash_multiset 中的元素的引用。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>备注

### <a name="example"></a>示例

```cpp
// hash_multiset_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_multiset can be
   // changed by operating on its (non const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_multiset is now "
        << *hms1.begin() << "." << endl;
}
```

```Output
The first element in the hash_multiset is 10.
The first element in the hash_multiset is now 15.
```

## <a name="rend"></a>hash_multiset::rend

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回一个迭代器，此迭代器用于发现反向 hash_multiset 中最后一个元素之后的位置。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>返回值

用于发现反向 hash_multiset 中最后一个元素之后的位置（非反向 hash_multiset 中第一个元素之前的位置）的反向双向迭代器。

### <a name="remarks"></a>备注

`rend` 用于反向 hash_multiset，正如 [end](#end) 用于 hash_multiset 一样。

如果将 `rend` 的返回值赋给 `const_reverse_iterator`，则无法修改 hash_multiset 对象。 如果将 `rend` 的返回值赋给 `reverse_iterator`，则可修改 hash_multiset 对象。 不应对 `rend` 返回的值取消引用。

`rend` 可用于测试反向迭代器是否已到达其 hash_multiset 的末尾。

### <a name="example"></a>示例

```cpp
// hash_multiset_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;
   hash_multiset <int>::const_reverse_iterator hms1_crIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // throught a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << "." << endl;

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_multiset is " << *hms1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
The hash_multiset is: 10 20 30 .
The reversed hash_multiset is: 30 20 10 .
After the erasure, the last element in the reversed hash_multiset is 20.
```

## <a name="reverse_iterator"></a>hash_multiset::reverse_iterator

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一种类型，此类型提供可读取或修改反向 hash_multiset 中的元素的双向迭代器。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>备注

`reverse_iterator` 类型用于反向循环访问 hash_multiset。

### <a name="example"></a>示例

有关如何声明和使用 `reverse_iterator` 的示例，请参阅 [rbegin](#rbegin) 的示例。

## <a name="size"></a>hash_multiset::size

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回 hash_multiset 中的元素数量。

```cpp
size_type size() const;
```

### <a name="return-value"></a>返回值

hash_multiset 的当前长度。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

```cpp
// hash_multiset_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: size_type i;

   hms1.insert( 1 );
   i = hms1.size( );
   cout << "The hash_multiset length is " << i << "." << endl;

   hms1.insert( 2 );
   i = hms1.size( );
   cout << "The hash_multiset length is now " << i << "." << endl;
}
```

```Output
The hash_multiset length is 1.
The hash_multiset length is now 2.
```

## <a name="size_type"></a>hash_multiset::size_type

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一种无符号整数类型，此类型可表示 hash_multiset 中的元素数量。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>备注

### <a name="example"></a>示例

有关如何声明和使用 `size_type` 的示例，请参阅 [size](#size) 的示例

## <a name="swap"></a>hash_multiset::swap

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

交换两个 hash_multiset 的元素。

```cpp
void swap(hash_multiset& right);
```

### <a name="parameters"></a>参数

*right*<br/>
参数 hash_multiset，提供要与目标 hash_multiset 进行交换的元素。

### <a name="remarks"></a>备注

此成员函数不会使后列项无效：用于在正在交换元素的两个 hash_multiset 中指定元素的任何引用、指针或迭代器。

### <a name="example"></a>示例

```cpp
// hash_multiset_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2, hms3;
   hash_multiset <int>::iterator hms1_Iter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );
   hms2.insert( 100 );
   hms2.insert( 200 );
   hms3.insert( 300 );

   cout << "The original hash_multiset hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hms1.swap( hms2 );

   cout << "After swapping with hms2, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hms1, hms3 );

   cout << "After swapping with hms3, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_multiset hms1 is: 10 20 30.
After swapping with hms2, list hms1 is: 200 100.
After swapping with hms3, list hms1 is: 300.
```

## <a name="upper_bound"></a>hash_multiset::upper_bound

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

返回一个迭代器，此迭代器指向 hash_multiset 中其键大于指定键的第一个元素。

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>参数

*key*<br/>
要与当前搜索的 hash_multiset 中元素的排序键进行比较的参数键。

### <a name="return-value"></a>返回值

一个 [iterator](#iterator) 或 [const_iterator](#const_iterator)，其会发现 hash_multiset 中其键大于参数键的第一个元素的位置，或如果未找到键的匹配项，则发现 hash_multiset 中最后一个元素之后的位置。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

```cpp
// hash_multiset_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "The first element of hash_multiset hms1" << endl
        << "with a key greater than 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element\n"
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key > 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be
   // found by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.begin( );
   hms1_RcIter = hms1.upper_bound( *hms1_AcIter );
   cout << "The first element of hms1 with a key greater than "
        << endl << "that of the initial element of hms1 is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The first element of hash_multiset hms1
with a key greater than 20 is: 30.
The hash_multiset hms1 doesn't have an element
with a key greater than 30.
The first element of hms1 with a key greater than
that of the initial element of hms1 is: 20.
```

## <a name="value_comp"></a>hash_multiset::value_comp

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

检索用于对 hash_multiset 中的元素值进行排序的比较对象副本。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>返回值

返回 hash_multiset 模板参数*特征*，其中包含使用哈希处理和顺序容器中的元素的函数对象。

有关详细信息*特征*请参阅[hash_multiset 类](../standard-library/hash-multiset-class.md)主题。

### <a name="remarks"></a>备注

存储对象用于定义成员函数：

**bool operator**( **constKey&**`_xVal`, **const Key&** *_yVal*);

如果 `_xVal` 在排序顺序中先于且不等于 `_yVal`，则该函数会返回 **true**。

请注意，[key_compare](#key_compare) 和 [value_compare](#value_compare) 皆是模板参数 *Traits* 的同义词。 对于 hash_set 和 hash_multiset 类，会同时提供这两种类型，且二者相同，但为实现与 hash_map 和 hash_multimap 类的兼容性时，二者则不同。

### <a name="example"></a>示例

```cpp
// hash_multiset_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > > hms1;
   hash_multiset <int, hash_compare < int, less<int> > >::value_compare
      vc1 = hms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hms1."
           << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::
           value_compare vc2 = hms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of hms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of hms2.
```

## <a name="value_compare"></a>hash_multiset::value_compare

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一种类型，它提供两个函数对象：一个是类比较二元谓词，可以比较 hash_multiset 的两个元素值以确定其相对顺序，另一个是一元谓词，可对元素进行哈希处理。

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>备注

`value_compare` 是模板参数的同义词*特征*。

有关详细信息*特征*请参阅[hash_multiset 类](../standard-library/hash-multiset-class.md)主题。

请注意，这两[key_compare](#key_compare)并`value_compare`是模板参数的同义词*Traits*。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。

### <a name="example"></a>示例

有关如何声明和使用 `value_compare` 的示例，请参阅 [value_comp](#value_comp) 的示例。

## <a name="value_type"></a>hash_multiset::value_type

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

一种类型，此类型将在其容量中存储为 hash_multiset 元素的对象描述为值。

```cpp
typedef Key value_type;
```

### <a name="example"></a>示例

```cpp
// hash_multiset_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;

   // Declare value_type
   hash_multiset <int> :: value_type hmsvt_Int;

   hmsvt_Int = 10;   // Initialize value_type

   // Declare key_type
   hash_multiset <int> :: key_type hmskt_Int;
   hmskt_Int = 20;             // Initialize key_type

   hms1.insert( hmsvt_Int );         // Insert value into s1
   hms1.insert( hmskt_Int );         // Insert key into s1

   // A hash_multiset accepts key_types or value_types as elements
   cout << "The hash_multiset has elements:";
   for ( hms1_Iter = hms1.begin() ; hms1_Iter != hms1.end( );
         hms1_Iter++)
      cout << " " << *hms1_Iter;
      cout << "." << endl;
}
```

```Output
The hash_multiset has elements: 10 20.
```

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
