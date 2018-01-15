---
title: "hash_set 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hash_set/stdext::hash_set
- hash_set/stdext::hash_set::allocator_type
- hash_set/stdext::hash_set::const_iterator
- hash_set/stdext::hash_set::const_pointer
- hash_set/stdext::hash_set::const_reference
- hash_set/stdext::hash_set::const_reverse_iterator
- hash_set/stdext::hash_set::difference_type
- hash_set/stdext::hash_set::iterator
- hash_set/stdext::hash_set::key_compare
- hash_set/stdext::hash_set::key_type
- hash_set/stdext::hash_set::pointer
- hash_set/stdext::hash_set::reference
- hash_set/stdext::hash_set::reverse_iterator
- hash_set/stdext::hash_set::size_type
- hash_set/stdext::hash_set::value_compare
- hash_set/stdext::hash_set::value_type
- hash_set/stdext::hash_set::begin
- hash_set/stdext::hash_set::cbegin
- hash_set/stdext::hash_set::cend
- hash_set/stdext::hash_set::clear
- hash_set/stdext::hash_set::count
- hash_set/stdext::hash_set::crbegin
- hash_set/stdext::hash_set::crend
- hash_set/stdext::hash_set::emplace
- hash_set/stdext::hash_set::emplace_hint
- hash_set/stdext::hash_set::empty
- hash_set/stdext::hash_set::end
- hash_set/stdext::hash_set::equal_range
- hash_set/stdext::hash_set::erase
- hash_set/stdext::hash_set::find
- hash_set/stdext::hash_set::get_allocator
- hash_set/stdext::hash_set::insert
- hash_set/stdext::hash_set::key_comp
- hash_set/stdext::hash_set::lower_bound
- hash_set/stdext::hash_set::max_size
- hash_set/stdext::hash_set::rbegin
- hash_set/stdext::hash_set::rend
- hash_set/stdext::hash_set::size
- hash_set/stdext::hash_set::swap
- hash_set/stdext::hash_set::upper_bound
- hash_set/stdext::hash_set::value_comp
dev_langs: C++
helpviewer_keywords:
- stdext::hash_set
- stdext::hash_set::allocator_type
- stdext::hash_set::const_iterator
- stdext::hash_set::const_pointer
- stdext::hash_set::const_reference
- stdext::hash_set::const_reverse_iterator
- stdext::hash_set::difference_type
- stdext::hash_set::iterator
- stdext::hash_set::key_compare
- stdext::hash_set::key_type
- stdext::hash_set::pointer
- stdext::hash_set::reference
- stdext::hash_set::reverse_iterator
- stdext::hash_set::size_type
- stdext::hash_set::value_compare
- stdext::hash_set::value_type
- stdext::hash_set::begin
- stdext::hash_set::cbegin
- stdext::hash_set::cend
- stdext::hash_set::clear
- stdext::hash_set::count
- stdext::hash_set::crbegin
- stdext::hash_set::crend
- stdext::hash_set::emplace
- stdext::hash_set::emplace_hint
- stdext::hash_set::empty
- stdext::hash_set::end
- stdext::hash_set::equal_range
- stdext::hash_set::erase
- stdext::hash_set::find
- stdext::hash_set::get_allocator
- stdext::hash_set::insert
- stdext::hash_set::key_comp
- stdext::hash_set::lower_bound
- stdext::hash_set::max_size
- stdext::hash_set::rbegin
- stdext::hash_set::rend
- stdext::hash_set::size
- stdext::hash_set::swap
- stdext::hash_set::upper_bound
- stdext::hash_set::value_comp
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3dd9f781b39db5e8c9df5e70a4a291db44e61cbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hashset-class"></a>hash_set 类
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 容器类 hash_set 是 C++ 标准库的扩展，用于存储和快速检索集合中的数据，集合中内含元素的值是唯一的且用作键值。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Key,   
    class Traits=hash_compare<Key, less<Key>>,   
    class Allocator=allocator<Key>>  
class hash_set  
```  
  
#### <a name="parameters"></a>参数  
 `Key`  
 要存储在 hash_set 中的元素数据类型。  
  
 `Traits`  
 该类型包括两个函数对象，其中一个是类比较函数，这是一个二元谓词，能够比较作为排序键的两个元素值以确定其相对顺序；另一个是哈希函数，这是一个一元谓词，用于将元素的键值映射到 **size_t** 类型的无符号整数。 此自变量是可选自变量，且默认值为 `hash_compare`*<Key,* **less***\<Key> >*。  
  
 `Allocator`  
 一种表示存储的分配器对象的类型，该分配器对象封装有关 hash_set 的内存分配和解除分配的详细信息。 此自变量是可选自变量，且默认值为 **allocator***\<Key>。*  
  
## <a name="remarks"></a>备注  
 Hash_set 是：  
  
-   大小可变的关联容器，支持基于关联键值高效检索元素值。 此外，它是简单的关联容器，因为它的元素值即为它的键值。  
  
-   可逆，因为它提供双向迭代器来访问其元素。  
  
-   经过哈希处理，因为其元素分组到了哈希桶中，哈希桶基于应用于元素键值的哈希函数的值。  
  
-   唯一，每个元素必须具有唯一键。 由于 hash_set 也是简单的关联容器，因此其元素也都是唯一的。  
  
-   一个模板类，由于其提供的功能是一般功能，因此与作为元素或键包含的特定数据类型无关。 用于元素和键的数据类型作为类模板以及比较函数和分配器中的参数指定。  
  
 哈希算法相比于排序的主要优点是效率更高；在排序技术中，时间与容器中元素数的对数成正比，而成功的哈希算法可在恒定的平均时间内执行插入、删除和查找操作。 不能直接更改集中元素的值。 必须先删除旧值，才能插入具有新值的元素。  
  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。 经过哈希处理的关联容器针对查找、插入和删除操作进行了优化。 与设计良好的哈希函数一起使用时，显式支持这些操作的成员函数较为高效，执行这些操作的时间为平均恒定值，而不取决于容器中元素的数目。 精心设计的哈希函数将生成统一分布的哈希值，并将最大限度地减少冲突数量，据说当非重复键值映射到相同的哈希值时会发生冲突。 在最坏情况下，使用可能是最差的哈希运算，操作数量与序列中的元素数量成比例（线性时间）。  
  
 当应用程序满足将值与其键关联的条件时，应选择 hash_set 作为关联容器。 Hash_set 的元素是唯一的，并用作其自己的排序键。 此类结构的模型是排序列表，如关键字排序列表，其中关键字只能出现一次。 如果允许关键字多次出现，那么相应的容器结构应该是 hash_multiset。 如果需要将值附加到唯一关键字的列表，则包含此数据的适当结构应为 hash_map。 如果键不唯一，则应选择 hash_multimap 作为容器。  
  
 hash_set 通过调用类型 [value_compare](#value_compare) 存储的哈希 **Traits** 对象，对其控制的序列进行排序。 此存储对象可通过调用成员函数 [key_comp](#key_comp) 进行访问。 此类函数对象的行为必须与类 *hash_compare\<<Key, less*Key>> 的对象的行为相同。 具体而言，对于类型 Key 的所有值 `key`，调用 Trait( `key` ) 都会对类型 size_t 的值进行分配。  
  
 通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。 这会导致在非等效元素之间进行排序。 在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。 二元谓词 *f*( *x*, *y*) 是包含两个参数对象（x 和 y）以及一个返回值（true 或 false）的函数对象。 如果二元谓词具有非自反性、反对称性和传递性且等效可传递，对 hash_set 进行的排序将为严格弱排序，其中两个对象 *x* 和 *y* 定义为在 *f*( *x*, *y*) 和 *f*( *y*, *x*) 均为 false 时等效。 如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。  
  
 受控序列中元素的实际顺序取决于哈希函数、排序函数和存储在容器对象中的哈希表的当前大小。 无法确定哈希表的当前大小，因此通常无法预测受控序列中元素的顺序。 插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。  
  
 hash_set 类提供的迭代器是双向迭代器，但类成员函数[insert](#insert) 和[hash_set](#hash_set) 具有将较弱输入迭代器作为模板参数的版本，较弱输入迭代器的功能需求比双向迭代器类保证的功能需求更少。 不同的迭代器概念形成一个系列，通过它们的功能优化相关联。 每个迭代器概念有它自己的一套要求，使用这些概念的算法必须根据迭代器类型提供的要求限制它们的假设。 可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。 这是最小的功能集，但足以按有意义的方式提供类成员函数的上下文中的迭代器范围 [ `first`, `last`)。  
  
   
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[hash_set](#hash_set)|构造一个空的或者是其他某个 `hash_set` 的全部或部分副本的 `hash_set`。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|一种类型，此类型表示 `allocator` 对象的 `hash_set` 类。|  
|[const_iterator](#const_iterator)|一种类型，此类型提供可读取 `const` 中的 `hash_set` 元素的双向迭代器。|  
|[const_pointer](#const_pointer)|一种类型，此类型提供指向 `const` 中的 `hash_set` 元素的指针。|  
|[const_reference](#const_reference)|一种类型，此类型提供对存储在 `const` 中的 `hash_set` 元素的引用（用于读取和执行 `const` 操作）。|  
|[const_reverse_iterator](#const_reverse_iterator)|一种类型，此类型提供可读取 `const` 中的任何 `hash_set` 元素的双向迭代器。|  
|[difference_type](#difference_type)|一种有符号整数类型，此类型可用于表示 `hash_set` 中迭代器指向的元素间范围内的元素数量。|  
|[Iterator](#iterator)|一种类型，它提供可读取或修改 `hash_set` 中任何元素的双向迭代器。|  
|[key_compare](#key_compare)|一种提供函数对象的类型，该函数对象可比较两个排序键以确定 `hash_set` 中两个元素的相对顺序。|  
|[key_type](#key_type)|一种类型，它描述当作为排序键存储为其容量中 `hash_set` 的元素的对象。|  
|[pointer](#pointer)|一种类型，它提供指向 `hash_set` 中的某个元素的指针。|  
|[reference](#reference)|一种类型，此类型提供对存储在 `hash_set` 中的元素的引用。|  
|[reverse_iterator](#reverse_iterator)|一种类型，此类型提供可读取或修改反向 `hash_set` 中的元素的双向迭代器。|  
|[size_type](#size_type)|可表示 `hash_set` 中元素数量的无符号整数类型。|  
|[value_compare](#value_compare)|一种类型，它提供两个函数对象：一个是类比较二元谓词，可以比较 `hash_set` 的两个元素值以确定其相对顺序，另一个是一元谓词，可对元素进行哈希处理。|  
|[value_type](#value_type)|一种类型，它描述当作为值存储为其容量中 `hash_set` 的元素的对象。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[begin](#begin)|返回一个迭代器，此迭代器用于发现 `hash_set` 中的第一个元素。|  
|[cbegin](#cbegin)|返回一个常量迭代器，此迭代器用于发现 `hash_set` 中的第一个元素。|  
|[cend](#cend)|返回一个常量迭代器，此迭代器用于发现 `hash_set` 中最后一个元素之后的位置。|  
|[clear](#clear)|清除 `hash_set` 的所有元素。|  
|[count](#count)|返回 `hash_set` 中其键与指定为参数的键匹配的元素数量。|  
|[crbegin](#crbegin)|返回一个常量迭代器，此迭代器用于发现反向 `hash_set` 中的第一个元素。|  
|[crend](#crend)|返回一个常量迭代器，此迭代器用于发现反向 `hash_set` 中最后一个元素之后的位置。|  
|[emplace](#emplace)|将就地构造的元素插入到 `hash_set`。|  
|[emplace_hint](#emplace_hint)|将就地构造的元素插入到 `hash_set`，附带位置提示。|  
|[empty](#empty)|测试 `hash_set` 是否为空。|  
|[end](#end)|返回一个迭代器，此迭代器用于发现 `hash_set` 中最后一个元素之后的位置。|  
|[equal_range](#equal_range)|返回一对迭代器，这两个迭代器分别用于发现 `hash_set` 中其键大于指定键的第一个元素，以及 `hash_set` 中其键等于或大于指定键的第一个元素。|  
|[erase](#erase)|从 `hash_set` 中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。|  
|[find](#find)|返回一个迭代器，此迭代器用于发现 `hash_set` 中其键与指定键等效的元素的位置。|  
|[get_allocator](#get_allocator)|返回用于构造 `allocator` 的 `hash_set` 对象的副本。|  
|[insert](#insert)|将一个元素或元素范围插入到 `hash_set`。|  
|[key_comp](#key_comp)|检索用于对 `hash_set` 中的键进行排序的比较对象副本。|  
|[lower_bound](#lower_bound)|返回一个迭代器，此迭代器指向 `hash_set` 中其键等于或大于指定键的第一个元素。|  
|[max_size](#max_size)|返回 `hash_set` 的最大长度。|  
|[rbegin](#rbegin)|返回一个迭代器，此迭代器用于发现反向 `hash_set` 中的第一个元素。|  
|[rend](#rend)|返回一个迭代器，此迭代器用于发现反向 `hash_set` 中最后一个元素之后的位置。|  
|[size](#size)|返回 `hash_set` 中的元素数量。|  
|[swap](#swap)|交换两个 `hash_set` 的元素。|  
|[upper_bound](#upper_bound)|返回一个迭代器，此迭代器指向 `hash_set` 中其键等于或大于指定键的第一个元素。|  
|[value_comp](#value_comp)|检索哈希特征对象的副本，该哈希特征对象用于对 `hash_set` 中的元素键值进行哈希处理和排序。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[hash_set::operator=](#op_eq)|将一个 `hash_set` 中的元素替换为另一 `hash_set` 副本。|  
  
## <a name="requirements"></a>惠?  
 **标头：**\<hash_set>  
  
 **命名空间：** stdext  
  
##  <a name="allocator_type"></a>hash_set::allocator_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一个类型，它代表 hash_set 对象的分配器类。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;  
```  
  
### <a name="remarks"></a>备注  
 **allocator_type** 是模板参数 `Allocator` 的同义词。  
  
 有关 `Allocator` 的详细信息，请参阅 [hash_set 类](../standard-library/hash-set-class.md)主题的备注部分。  
  
   
  
### <a name="example"></a>示例  
  有关使用 `allocator_type` 的示例，请参阅 [get_allocator](#get_allocator) 的示例。  
  
##  <a name="begin"></a>hash_set::begin  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回一个迭代器，此迭代器用于发现 hash_set 中的第一个元素。  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>返回值  
 一个双向迭代器，发现 hash_set 中第一个元素的位置或空 hash_set 之后的位置。  
  
### <a name="remarks"></a>备注  
 如果 **begin** 的返回值赋给了 `const_iterator`，则无法修改 hash_set 对象中的元素。 如果 **begin** 的返回值赋给了 **iterator**，则可以修改 hash_set 对象中的元素。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_begin.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::iterator hs1_Iter;  
   hash_set <int>::const_iterator hs1_cIter;  
  
   hs1.insert( 1 );  
   hs1.insert( 2 );  
   hs1.insert( 3 );  
  
   hs1_Iter = hs1.begin( );  
   cout << "The first element of hs1 is " << *hs1_Iter << endl;  
  
   hs1_Iter = hs1.begin( );  
   hs1.erase( hs1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // hs1_cIter = hs1.begin( );  
   // hs1.erase( hs1_cIter );  
  
   hs1_cIter = hs1.begin( );  
   cout << "The first element of hs1 is now " << *hs1_cIter << endl;  
}  
```  
  
```Output  
The first element of hs1 is 1  
The first element of hs1 is now 2  
```  
  
##  <a name="cbegin"></a>hash_set::cbegin  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回一个常量迭代器，此迭代器用于发现 hash_set 中第一个元素的位置。  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 一个常量双向迭代器，发现 [hash_set](../standard-library/hash-set-class.md) 中第一个元素的位置或空 `hash_set` 之后的位置。  
  
### <a name="remarks"></a>备注  
 由于使用 `cbegin` 的返回值，因此不能修改 `hash_set` 对象中的元素。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_cbegin.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::const_iterator hs1_cIter;  
  
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
  
##  <a name="cend"></a>hash_set::cend  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回一个常量迭代器，此迭代器用于发现 hash_set 中最后一个元素之后的位置。  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>返回值  
 用于发现 [hash_set](../standard-library/hash-set-class.md) 中最后一个元素之后的位置的常量双向迭代器。 如果 `hash_set` 为空，则 `hash_set::cend == hash_set::begin`。  
  
### <a name="remarks"></a>备注  
 `cend` 用于测试迭代器是否已到达其 `hash_set` 的末尾。 不应对 `cend` 返回的值取消引用。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_cend.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int> :: const_iterator hs1_cIter;  
  
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
  
##  <a name="clear"></a>hash_set::clear  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 清除 hash_set 的所有元素。  
  
```  
void clear();
```  
  
### <a name="remarks"></a>备注  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_clear.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
  
   hs1.insert( 1 );  
   hs1.insert( 2 );  
  
   cout << "The size of the hash_set is initially " << hs1.size( )  
        << "." << endl;  
  
   hs1.clear( );  
   cout << "The size of the hash_set after clearing is "   
        << hs1.size( ) << "." << endl;  
}  
```  
  
```Output  
The size of the hash_set is initially 2.  
The size of the hash_set after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>hash_set::const_iterator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 提供可读取 hash_set 中 **const** 元素的双向迭代器的类型。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `const_iterator` 类型不能用于修改元素的值。  
  
   
  
### <a name="example"></a>示例  
  有关使用 `const_iterator` 的示例，请参阅 [begin](#begin) 的示例。  
  
##  <a name="const_pointer"></a>hash_set::const_pointer  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一种类型，此类型提供指向 hash_set 中的 **const** 元素的指针。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>备注  
 `const_pointer` 类型不能用于修改元素的值。  
  
 在大多数情况下，应使用 [const_iterator](#const_iterator) 访问 **const** hash_set 对象中的元素。  
  
   
  
##  <a name="const_reference"></a>hash_set::const_reference  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一种类型，此类型提供对用于读取和执行 **const** 操作的 hash_set 中存储的 **const** 元素的引用。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reference const_reference;  
```  
  
### <a name="remarks"></a>备注  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_const_ref.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the 1st element  
   const int &Ref1 = *hs1.begin( );  
  
   cout << "The first element in the hash_set is "  
        << Ref1 << "." << endl;  
  
   // The following line would cause an error because the   
   // const_reference cannot be used to modify the hash_set  
   // Ref1 = Ref1 + 5;  
}  
```  
  
```Output  
The first element in the hash_set is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>hash_set::const_reverse_iterator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 提供可读取 hash_set 中任何 **const** 元素的双向迭代器的类型。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `const_reverse_iterator` 类型无法修改元素的值，它用于反向循环访问 hash_set。  
  
   
  
### <a name="example"></a>示例  
  有关如何声明和使用 `const_reverse_iterator` 的示例，请参阅 [rend](#rend) 的示例  
  
##  <a name="count"></a>hash_set::count  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回 hash_set 中其键与参数指定的键匹配的元素数量。  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要从 hash_set 中进行匹配的元素的键。  
  
### <a name="return-value"></a>返回值  
 如果该 hash_set 包含其排序键匹配参数键的元素，则为 1。  
  
 如果该 hash_set 不包含具有匹配键的元素，则为 0。  
  
### <a name="remarks"></a>备注  
 成员函数返回在以下范围内的元素数目：  
  
 [ **lower_bound** (_ *Key* ), **upper_bound** (\_ *Key* ) )。  
  
   
  
### <a name="example"></a>示例  
  下面的示例演示如何使用 hash_set::count 成员函数。  
  
```  
// hash_set_count.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_set<int> hs1;  
    hash_set<int>::size_type i;  
  
    hs1.insert(1);  
    hs1.insert(1);  
  
    // Keys must be unique in hash_set, so duplicates are ignored.  
    i = hs1.count(1);  
    cout << "The number of elements in hs1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = hs1.count(2);  
    cout << "The number of elements in hs1 with a sort key of 2 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in hs1 with a sort key of 1 is: 1.  
The number of elements in hs1 with a sort key of 2 is: 0.  
```  
  
##  <a name="crbegin"></a>hash_set::crbegin  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回一个常量迭代器，此迭代器用于发现反向 hash_set 中的第一个元素的位置。  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 一个常量反向双向迭代器，发现反向 [hash_set](../standard-library/hash-set-class.md) 中的第一个元素位置或发现曾是非反向 `hash_set` 中的最后一个元素位置。  
  
### <a name="remarks"></a>备注  
 `crbegin` 用于反向 hash_set，正如 [hash_set::begin](#begin) 用于 hash_set 一样。  
  
 返回值为 `crbegin` 时，无法修改 `hash_set` 对象。  
  
 `crbegin` 可用于向后循环访问 `hash_set`。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_crbegin.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::const_reverse_iterator hs1_crIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_crIter = hs1.crbegin( );  
   cout << "The first element in the reversed hash_set is "  
        << *hs1_crIter << "." << endl;  
}  
```  
  
```Output  
The first element in the reversed hash_set is 30.  
```  
  
##  <a name="crend"></a>hash_set::crend  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回一个常量迭代器，此迭代器用于发现反向 hash_set 中最后一个元素之后的位置。  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>返回值  
 一个常量反向双向迭代器，用于发现反向 [hash_set](../standard-library/hash-set-class.md) 中最后一个元素之后的位置（非反向 `hash_set` 中第一个元素之前的位置）。  
  
### <a name="remarks"></a>备注  
 `crend` 用于反向 `hash_set`，正如 [hash_set::end](#end) 用于 `hash_set` 一样。  
  
 返回值为 `crend` 时，无法修改 `hash_set` 对象。  
  
 `crend` 可用于测试反向迭代器是否已到达其 `hash_set` 的末尾。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_crend.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::const_reverse_iterator hs1_crIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_crIter = hs1.crend( );  
   hs1_crIter--;  
   cout << "The last element in the reversed hash_set is "  
        << *hs1_crIter << "." << endl;  
}  
```  
  
```Output  
The last element in the reversed hash_set is 10.  
```  
  
##  <a name="difference_type"></a>hash_set::difference_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一种有符号整数类型，此类型可用于表示 hash_set 中迭代器指向的元素间范围内的元素数量。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;  
```  
  
### <a name="remarks"></a>备注  
 `difference_type` 是通过容器迭代器减少或递增时返回的类型。 `difference_type` 通常用于表示迭代器 `first` 和 `last` 之间的范围 [ `first`, `last`) 内元素的数目，包括 `first` 指向的元素以及那一系列元素，但不包括 `last` 指向的元素。  
  
 请注意，尽管 `difference_type` 适用于满足输入迭代器（包括可逆容器支持的双向迭代器的类，如 set）要求的所有迭代器，迭代器之间的减法仅受随机访问容器（如 vector 或 deque）提供的随机访问迭代器支持。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <hash_set>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_set <int> hs1;  
   hash_set <int>::iterator hs1_Iter, hs1_bIter, hs1_eIter;  
  
   hs1.insert( 20 );  
   hs1.insert( 10 );  
   hs1.insert( 20 );   // Won't insert as hash_set elements are unique  
  
   hs1_bIter = hs1.begin( );  
   hs1_eIter = hs1.end( );  
  
   hash_set <int>::difference_type   df_typ5, df_typ10, df_typ20;  
  
   df_typ5 = count( hs1_bIter, hs1_eIter, 5 );  
   df_typ10 = count( hs1_bIter, hs1_eIter, 10 );  
   df_typ20 = count( hs1_bIter, hs1_eIter, 20 );  
  
   // The keys, and hence the elements, of a hash_set are unique,  
   // so there is at most one of a given value  
   cout << "The number '5' occurs " << df_typ5  
        << " times in hash_set hs1.\n";  
   cout << "The number '10' occurs " << df_typ10  
        << " times in hash_set hs1.\n";  
   cout << "The number '20' occurs " << df_typ20  
        << " times in hash_set hs1.\n";  
  
   // Count the number of elements in a hash_set  
   hash_set <int>::difference_type  df_count = 0;  
   hs1_Iter = hs1.begin( );  
   while ( hs1_Iter != hs1_eIter)  
   {  
      df_count++;  
      hs1_Iter++;  
   }  
  
   cout << "The number of elements in the hash_set hs1 is: "   
        << df_count << "." << endl;  
}  
```  
  
```Output  
The number '5' occurs 0 times in hash_set hs1.  
The number '10' occurs 1 times in hash_set hs1.  
The number '20' occurs 1 times in hash_set hs1.  
The number of elements in the hash_set hs1 is: 2.  
```  
  
##  <a name="emplace"></a>hash_set::emplace  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 将就地构造的元素插入到 hash_set 中。  
  
```  
template <class ValTy>  
pair <iterator, bool>  
emplace(
    ValTy&& val);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`val`|要插入 [hash_set](../standard-library/hash-set-class.md) 的元素的值，除非 `hash_set` 已包含该元素（更宽泛地说，是其键经等效排序的元素）。|  
  
### <a name="return-value"></a>返回值  
 `emplace` 成员函数返回一个对，其中，如果完成插入操作，则此对的 `bool` 组件返回 `true`，如果 `hash_set` 已包含一个其值在排序中具有等效值的元素，则返回 `false`；此对的迭代器组件返回新元素的插入位置或已包含的元素的位置。  
  
### <a name="remarks"></a>备注  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_emplace.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set<string> hs3;  
   string str1("a");  
  
   hs3.emplace(move(str1));  
   cout << "After the emplace insertion, hs3 contains "  
      << *hs3.begin() << "." << endl;  
}  
```  
  
```Output  
After the emplace insertion, hs3 contains a.  
```  
  
##  <a name="emplace_hint"></a>hash_set::emplace_hint  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 将就地构造的元素插入到 hash_set 中。  
  
```  
template <class ValTy>  
iterator emplace(
    const_iterator _Where,  
    ValTy&& val);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`val`|要插入 [hash_set](../standard-library/hash-set-class.md) 的元素的值，除非 `hash_set` 已包含该元素（更宽泛地说，是其键经等效排序的元素）。|  
|`_Where`|开始搜索正确插入点的位置。 （如果插入点紧随 `_Where`，则插入可发生在分期常量时间内，而非对数时间内。）|  
  
### <a name="return-value"></a>返回值  
 [hash_set::emplace](#emplace) 成员函数返回一个迭代器，此迭代器指向 `hash_set` 中插入的新元素的位置或具有等效顺序的现有元素的所在位置。  
  
### <a name="remarks"></a>备注  
 如果插入点紧随 `_Where`，则插入可发生在分期常量时间内，而非对数时间内。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_emplace_hint.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set<string> hs3;  
   string str1("a");  
  
   hs3.insert(hs3.begin(), move(str1));  
   cout << "After the emplace insertion, hs3 contains "  
      << *hs3.begin() << "." << endl;  
}  
```  
  
```Output  
After the emplace insertion, hs3 contains a.  
```  
  
##  <a name="empty"></a>hash_set::empty  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 测试 hash_set 是否为空。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 如果 hash_set 为空，则为 **true**；如果 hash_set 不为空，则为 **false**。  
  
### <a name="remarks"></a>备注  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_empty.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1, hs2;  
   hs1.insert ( 1 );  
  
   if ( hs1.empty( ) )  
      cout << "The hash_set hs1 is empty." << endl;  
   else  
      cout << "The hash_set hs1 is not empty." << endl;  
  
   if ( hs2.empty( ) )  
      cout << "The hash_set hs2 is empty." << endl;  
   else  
      cout << "The hash_set hs2 is not empty." << endl;  
}  
```  
  
```Output  
The hash_set hs1 is not empty.  
The hash_set hs2 is empty.  
```  
  
##  <a name="end"></a>hash_set::end  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回一个迭代器，此迭代器用于发现 hash_set 中最后一个元素之后的位置。  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>返回值  
 用于发现 hash_set 中最后一个元素之后的位置的双向迭代器。 如果 hash_set 为空，则 hash_set::end == hash_set::begin。  
  
### <a name="remarks"></a>备注  
 **end** 用于测试迭代器是否已到达 hash_set 的末尾。 不应对 **end** 返回的值取消引用。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_end.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int> :: iterator hs1_Iter;  
   hash_set <int> :: const_iterator hs1_cIter;  
  
   hs1.insert( 1 );  
   hs1.insert( 2 );  
   hs1.insert( 3 );  
  
   hs1_Iter = hs1.end( );  
   hs1_Iter--;  
   cout << "The last element of hs1 is " << *hs1_Iter << endl;  
  
   hs1.erase( hs1_Iter );  
  
   // The following 3 lines would err because the iterator is const:  
   // hs1_cIter = hs1.end( );  
   // hs1_cIter--;  
   // hs1.erase( hs1_cIter );  
  
   hs1_cIter = hs1.end( );  
   hs1_cIter--;  
   cout << "The last element of hs1 is now " << *hs1_cIter << endl;  
}  
```  
  
```Output  
The last element of hs1 is 3  
The last element of hs1 is now 2  
```  
  
##  <a name="equal_range"></a>hash_set::equal_range  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回一对迭代器，这两个迭代器分别用于发现哈希集中其键等于指定键的第一个元素，以及哈希集中其键大于指定键的第一个元素。  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的 hash_set 中元素的排序键进行比较的参数键。  
  
### <a name="return-value"></a>返回值  
 一对迭代器，其中第一个是键的 [lower_bound](../standard-library/set-class.md#lower_bound)，第二个是键的 [upper_bound](../standard-library/set-class.md#upper_bound)。  
  
 若要访问成员函数返回的 pr 对的第一个迭代器，请使用 `pr`. **first**；若要取消引用下界迭代器，请使用 \*( `pr`. **first**)。 若要访问成员函数返回的 `pr` 对的第二个迭代器，请使用 `pr`. **second**；若要取消引用上界迭代器，请使用 \*( `pr`. **second**)。  
  
### <a name="remarks"></a>备注  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_equal_range.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
   using namespace stdext;  
   typedef hash_set<int> IntHSet;  
   IntHSet hs1;  
   hash_set <int> :: const_iterator hs1_RcIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;  
   p1 = hs1.equal_range( 20 );  
  
   cout << "The upper bound of the element with "  
        << "a key of 20 in the hash_set hs1 is: "  
        << *(p1.second) << "." << endl;  
  
   cout << "The lower bound of the element with "  
        << "a key of 20 in the hash_set hs1 is: "  
        << *(p1.first) << "." << endl;  
  
   // Compare the upper_bound called directly   
   hs1_RcIter = hs1.upper_bound( 20 );  
   cout << "A direct call of upper_bound( 20 ) gives "  
        << *hs1_RcIter << "," << endl  
        << "matching the 2nd element of the pair"  
        << " returned by equal_range( 20 )." << endl;  
  
   p2 = hs1.equal_range( 40 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == hs1.end( ) ) && ( p2.second == hs1.end( ) ) )  
      cout << "The hash_set hs1 doesn't have an element "  
           << "with a key greater than or equal to 40." << endl;  
   else  
      cout << "The element of hash_set hs1 with a key >= 40 is: "  
           << *(p1.first) << "." << endl;  
}  
```  
  
```Output  
The upper bound of the element with a key of 20 in the hash_set hs1 is: 30.  
The lower bound of the element with a key of 20 in the hash_set hs1 is: 20.  
A direct call of upper_bound( 20 ) gives 30,  
matching the 2nd element of the pair returned by equal_range( 20 ).  
The hash_set hs1 doesn't have an element with a key greater than or equal to 40.  
```  
  
##  <a name="erase"></a>hash_set::erase  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 在 hash_set 中从指定位置删除一个元素或一定范围的元素或删除与指定键匹配的元素。  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```  
  
### <a name="parameters"></a>参数  
 `_Where`  
 要从 hash_set 中删除的元素的位置。  
  
 `first`  
 要从 hash_set 中删除的第一个元素的位置。  
  
 `last`  
 紧接要从 hash_set 中删除的最后一个元素的位置。  
  
 `key`  
 要从 hash_set 中删除的元素的键。  
  
### <a name="return-value"></a>返回值  
 对于前两个成员函数，则为双向迭代器，它指定已删除的任何元素之外留存的第一个元素，如果此类元素不存在，则为指向 hash_set 末尾的指针。 对于第三个成员函数，则为已从 hash_set 中删除的元素的数目。  
  
### <a name="remarks"></a>备注  
 成员函数从不引发异常。  
  
   
  
### <a name="example"></a>示例  
  下面的示例演示 hash_set::erase 成员函数的用法。  
  
```  
// hash_set_erase.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_set<int> hs1, hs2, hs3;  
    hash_set<int>::iterator pIter, Iter1, Iter2;  
    int i;  
    hash_set<int>::size_type n;  
  
    for (i = 1; i < 5; i++)  
    {  
        hs1.insert (i);  
        hs2.insert (i * i);  
        hs3.insert (i - 1);  
    }  
  
    // The 1st member function removes an element at a given position  
    Iter1 = ++hs1.begin();  
    hs1.erase(Iter1);  
  
    cout << "After the 2nd element is deleted, the hash_set hs1 is:";  
    for (pIter = hs1.begin(); pIter != hs1.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
  
    // The 2nd member function removes elements  
    // in the range [ first,  last)  
    Iter1 = ++hs2.begin();  
    Iter2 = --hs2.end();  
    hs2.erase(Iter1, Iter2);  
  
    cout << "After the middle two elements are deleted, "  
         << "the hash_set hs2 is:";  
    for (pIter = hs2.begin(); pIter != hs2.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
  
    // The 3rd member function removes elements with a given  key  
    n = hs3.erase(2);  
  
    cout << "After the element with a key of 2 is deleted, "  
         << "the hash_set hs3 is:";  
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
  
    // The 3rd member function returns the number of elements removed  
    cout << "The number of elements removed from hs3 is: "  
         << n << "." << endl;  
  
    // The dereferenced iterator can also be used to specify a key  
    Iter1 = ++hs3.begin();  
    hs3.erase(Iter1);  
  
    cout << "After another element (unique for hash_set) with a key "  
         << endl;  
    cout  << "equal to that of the 2nd element is deleted, "  
          << "the hash_set hs3 is:";  
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)  
        cout << " " << *pIter;  
    cout << "." << endl;  
}  
```  
  
```Output  
After the 2nd element is deleted, the hash_set hs1 is: 1 3 4.  
After the middle two elements are deleted, the hash_set hs2 is: 16 4.  
After the element with a key of 2 is deleted, the hash_set hs3 is: 0 1 3.  
The number of elements removed from hs3 is: 1.  
After another element (unique for hash_set) with a key   
equal to that of the 2nd element is deleted, the hash_set hs3 is: 0 3.  
```  
  
##  <a name="find"></a>hash_set::find  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回一个迭代器，此迭代器用于发现 hash_set 中其键与指定键等效的元素的位置。  
  
```  
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的 hash_set 中元素的排序键匹配的参数键。  
  
### <a name="return-value"></a>返回值  
 一个**迭代器**或 `const_iterator`，此迭代器发现等效于指定键的元素的位置，或者如果找不到此键的匹配项，则发现 hash_set 中最后一个元素后面的位置。  
  
### <a name="remarks"></a>备注  
 此成员函数返回一个迭代器，此迭代器发现 hash_set 中其排序键与二元谓词下的参数键**等效**的元素的位置，该谓词基于小于比较关系进行顺序。  
  
 如果将 **find** 的返回值赋给 `const_iterator`，则无法修改 hash_set 对象。 如果 **find** 的返回值赋给 **iterator**，则可以修改 hash_set 对象。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_find.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_RcIter = hs1.find( 20 );  
   cout << "The element of hash_set hs1 with a key of 20 is: "  
        << *hs1_RcIter << "." << endl;  
  
   hs1_RcIter = hs1.find( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( hs1_RcIter == hs1.end( ) )  
      cout << "The hash_set hs1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of hash_set hs1 with a key of 40 is: "  
           << *hs1_RcIter << "." << endl;  
  
   // The element at a specific location in the hash_set can be found   
   // by using a dereferenced iterator addressing the location  
   hs1_AcIter = hs1.end( );  
   hs1_AcIter--;  
   hs1_RcIter = hs1.find( *hs1_AcIter );  
   cout << "The element of hs1 with a key matching "  
        << "that of the last element is: "  
        << *hs1_RcIter << "." << endl;  
}  
```  
  
```Output  
The element of hash_set hs1 with a key of 20 is: 20.  
The hash_set hs1 doesn't have an element with a key of 40.  
The element of hs1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="get_allocator"></a>hash_set::get_allocator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回用于构造 hash_set 的分配器对象的一个副本。  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>返回值  
 hash_set 用于管理内存的分配器，即模板参数 `Allocator`。  
  
 有关 `Allocator` 的详细信息，请参阅 [hash_set 类](../standard-library/hash-set-class.md)主题的备注部分。  
  
### <a name="remarks"></a>备注  
 hash_set 类的分配器指定类管理存储的方式。 C++ 标准库容器类提供的默认分配器足以满足大多编程需求。 编写和使用你自己的分配器类是高级 C++ 主题。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_get_allocator.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   hash_set <int, hash_compare <int, less<int> > > hs1;  
   hash_set <int,  hash_compare <int, greater<int> > > hs2;  
   hash_set <double, hash_compare <double,  
      less<double> >, allocator<double> > hs3;  
  
   hash_set <int, hash_compare <int,  
      greater<int> > >::allocator_type hs2_Alloc;  
   hash_set <double>::allocator_type hs3_Alloc;  
   hs2_Alloc = hs2.get_allocator( );  
  
   cout << "The number of integers that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << hs1.max_size( ) << "." << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << hs3.max_size( ) <<  "." << endl;  
  
   // The following lines create a hash_set hs4  
   // with the allocator of hash_set hs1.  
   hash_set <int>::allocator_type hs4_Alloc;  
   hash_set <int> hs4;  
   hs4_Alloc = hs2.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated by the other  
   if( hs2_Alloc == hs4_Alloc )  
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
  
##  <a name="hash_set"></a>hash_set::hash_set  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 构造一个空的或者是其他某个 `hash_set` 的全部或部分副本的 `hash_set`。  
  
```  
hash_set();

explicit hash_set(
    const Traits& Comp);

hash_set(
    const Traits& Comp,  
    const Allocator& Al);

hash_set(
    const hash_set<Key, Traits, Allocator>& Right);

hash_set(
    hash_set&& Right);

hash_set(
    initializer_list<Type> IList);

hash_set(
    initializer_list<Type> IList,   
    const Compare& Comp);

hash_set(
    initializer_list<value_type> IList,   
    const Compare& Comp,   
    const Allocator& Al);

template <class InputIterator>  
hash_set(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
hash_set(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp);

template <class InputIterator>  
hash_set(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`Al`|要用于此 `hash_set` 对象的存储分配器类，默认为 `Allocator`。|  
|`Comp`|用于对 `hash_set` 中元素排序的类型 `const Traits` 的比较函数，默认为 `hash_compare`。|  
|`Right`|所构造的 `hash_set` 要作为其副本的 `hash_set`。|  
|`First`|要复制的范围元素中的第一个元素的位置。|  
|`Last`|要复制的元素范围以外的第一个元素的位置。|  
  
### <a name="remarks"></a>备注  
 所有构造函数存储一类分配器对象，此对象管理 `hash_set` 的内存存储，且稍后可通过调用 [hash_set::get_allocator](#get_allocator) 进行返回。 此分配器参数在类声明中常省略，并预处理用于代替备用分配器的宏。  
  
 所有构造函数对其 hash_set 进行初始化。  
  
 所有构造函数会存储 `Traits` 类型的函数对象，此对象用于在 `hash_set` 的键之间建立排序，且稍后通过调用 [hash_set::key_comp](#key_comp) 可进行返回。 有关 `Traits` 的详细信息，请参阅 [hash_set 类](../standard-library/hash-set-class.md)主题。  
  
 第一个构造函数创建一个空的起始 `hash_set`，第二个构造函数指定用于建立元素顺序的比较函数 ( `Comp`) 的类型，第三个构造函数显式指定要使用的分配器类型 ( `Al`)。 关键字 `explicit` 取消了某些种类的自动类型转换。  
  
 第四个和第五个构造函数指定一份`hash_set` `Right`。  
  
 最后，第六个、第七个和第八个构造函数对元素使用 initializer_list。  
  
 最后的这些构造函数复制 `hash_set` 的范围 [ `First`, `Last`)，其指定类 Traits 的比较函数类型和分配器的明确性更高。  
  
 第八个构造函数移动`hash_set` `Right`。  
  
 `hash_set` 容器中元素的实际顺序取决于哈希函数、排序函数和哈希表的当前大小，且通常无法进行预测，而在设置容器中则可对其进行预测，因为在设置容器中其仅由排序函数决定。  
  
##  <a name="insert"></a>hash_set::insert  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 将一个元素或元素范围插入到 `hash_set`。  
  
```  
pair<iterator, bool> insert(
    const value_type& Val);

iterator insert(
    iterator Where,  
    const value_type& Val);

void insert(
    initializer_list<value_type> IList)  
template <class InputIterator>  
void insert(
    InputIterator First,  
    InputIterator Last);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`Val`|要插入 `hash_set` 的元素的值，除非 `hash_set` 已包含该元素（更宽泛地说，是其键经等效排序的元素）。|  
|`Where`|开始搜索正确插入点的位置。 （如果插入点紧随 `_Where`，则插入可发生在分期常量时间内，而非对数时间内。）|  
|`First`|要从 `hash_set` 中复制的第一个元素的位置。|  
|`Last`|要从 `hash_set` 中复制的最后一个元素以外的位置。|  
|`IList`|从中复制元素的 initializer_list。|  
  
### <a name="return-value"></a>返回值  
 第一个 `insert` 成员函数会返回一个对，其中，如果完成插入操作，则此对的 `bool` 组件返回 `true`，如果 `hash_set` 已包含一个其值在排序中具有等效值的元素，则返回 `false`；此对的迭代器组件返回新元素的插入位置或已包含的元素的位置。  
  
 若要访问此成员函数返回的 `pr` 对的迭代器组件，请使用 `pr.first`；若要对其取消引用，请使用 `*(pr.first)`。 若要访问此成员函数返回的 `pr` 对的 `bool` 组件，请使用 `pr.second`；若要对其取消引用，请使用 `*(pr.second)`。  
  
 第二个 `insert` 成员函数将返回一个指向 `hash_set` 中新元素的插入位置的迭代器。  
  
### <a name="remarks"></a>备注  
 第三个成员函数在 initializer_list 中插入元素。  
  
 第三个成员函数将元素值序列插入到 `hash_set`，它对应于迭代器在指定 `hash_set` 的范围 [ `First`, `Last`) 中所处理的每一个元素。  
  
##  <a name="iterator"></a>hash_set::iterator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一种类型，此类型提供可读取或修改 hash_set 中的任何元素的双向迭代器。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;  
```  
  
### <a name="remarks"></a>备注  
 **iterator** 类型可用于修改元素的值。  
  
   
  
### <a name="example"></a>示例  
  有关如何声明和使用 **iterator** 的示例，请参阅 [begin](#begin) 的示例。  
  
##  <a name="key_comp"></a>hash_set::key_comp  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 检索哈希特征对象的副本，该哈希特征对象用于对 hash_set 中的元素键值进行哈希处理和排序。  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>返回值  
 返回 hash_set 用来对其元素进行排序的函数对象，即模板参数 `Traits`。  
  
 有关 `Traits` 的详细信息，请参阅 [hash_set 类](../standard-library/hash-set-class.md)主题。  
  
### <a name="remarks"></a>备注  
 存储对象用于定义以下成员函数：  
  
 **bool operator**( **const Key&** _ *xVal*, **const Key&** \_ `yVal`);  
  
 如果 `_xVal` 在排序顺序中先于且不等于 `_yVal`，则该函数会返回 **true**。  
  
 请注意，[key_compare](#key_compare) 和 [value_compare](#value_compare) 皆是模板参数 **Traits** 的同义词。 对于 hash_set 和 hash_multiset 类，会同时提供这两种类型，且二者相同，但为实现与 hash_map 和 hash_multimap 类的兼容性时，二者则不同。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_key_comp.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_set <int, hash_compare < int, less<int> > >hs1;  
   hash_set<int, hash_compare < int, less<int> > >::key_compare kc1  
          = hs1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )  
   {  
      cout << "kc1( 2,3 ) returns value of true, "  
           << "where kc1 is the function object of hs1."  
           << endl;  
   }  
   else  
   {  
      cout << "kc1( 2,3 ) returns value of false "  
           << "where kc1 is the function object of hs1."  
        << endl;  
   }  
  
   hash_set <int, hash_compare < int, greater<int> > > hs2;  
   hash_set<int, hash_compare < int, greater<int> > >::key_compare  
         kc2 = hs2.key_comp( ) ;  
   bool result2 = kc2( 2, 3 ) ;  
   if(result2 == true)  
   {  
      cout << "kc2( 2,3 ) returns value of true, "  
           << "where kc2 is the function object of hs2."  
           << endl;  
   }  
   else  
   {  
      cout << "kc2( 2,3 ) returns value of false, "  
           << "where kc2 is the function object of hs2."  
           << endl;  
   }  
}  
```  
  
##  <a name="key_compare"></a>hash_set::key_compare  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一种提供函数对象的类型，该函数对象可比较两个排序键以确定 hash_set 中两个元素的相对顺序。  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>备注  
 `key_compare` 是模板参数 `Traits` 的同义词。  
  
 有关 `Traits` 的详细信息，请参阅 [hash_set 类](../standard-library/hash-set-class.md)主题。  
  
 请注意，`key_compare` 和 [value_compare](#value_compare) 皆是模板参数 **Traits** 的同义词。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。  
  
   
  
### <a name="example"></a>示例  
  有关如何声明和使用 `key_compare` 的示例，请参阅 [key_comp](#key_comp) 的示例。  
  
##  <a name="key_type"></a>hash_set::key_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一种类型，此类型将在其容量中存储为 hash_set 元素的对象描述为排序键。  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>备注  
 **key_type** 类型是模板参数 `Key` 的同义词。  
  
 有关 `Key` 的详细信息，请参阅 [hash_set 类](../standard-library/hash-set-class.md)主题的备注部分。  
  
 请注意，`key_type` 和 [value_type](#value_type) 皆是模板参数 **Key** 的同义词。 对于 hash_set 和 hash_multiset 类，会同时提供这两种类型，且二者相同，但为实现与 hash_map 和 hash_multimap 类的兼容性时，二者则不同。  
  
   
  
### <a name="example"></a>示例  
  有关如何声明和使用 `key_type` 的示例，请参阅 [value_type](#value_type) 的示例。  
  
##  <a name="lower_bound"></a>hash_set::lower_bound  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回一个迭代器，此迭代器指向 hash_set 中其键等于或大于指定键的第一个元素。  
  
```  
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的 hash_set 中元素的排序键进行比较的参数键。  
  
### <a name="return-value"></a>返回值  
 一个 **iterator** 或 `const_iterator`，其会发现 hash_set 中其键等于或大于参数键的元素的位置，或如果未找到键的匹配项，则发现 hash_set 中最后一个元素之后的位置。  
  
### <a name="remarks"></a>备注  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_lower_bound.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_RcIter = hs1.lower_bound( 20 );  
   cout << "The element of hash_set hs1 with a key of 20 is: "  
        << *hs1_RcIter << "." << endl;  
  
   hs1_RcIter = hs1.lower_bound( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( hs1_RcIter == hs1.end( ) )  
      cout << "The hash_set hs1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of hash_set hs1 with a key of 40 is: "  
           << *hs1_RcIter << "." << endl;  
  
   // An element at a specific location in the hash_set can be found   
   // by using a dereferenced iterator that addresses the location  
   hs1_AcIter = hs1.end( );  
   hs1_AcIter--;  
   hs1_RcIter = hs1.lower_bound( *hs1_AcIter );  
   cout << "The element of hs1 with a key matching "  
        << "that of the last element is: "  
        << *hs1_RcIter << "." << endl;  
}  
```  
  
```Output  
The element of hash_set hs1 with a key of 20 is: 20.  
The hash_set hs1 doesn't have an element with a key of 40.  
The element of hs1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="max_size"></a>hash_set::max_size  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回 hash_set 的最大长度。  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>返回值  
 hash_set 的最大可取长度。  
  
### <a name="remarks"></a>备注  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_max_size.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::size_type i;  
  
   i = hs1.max_size( );  
   cout << "The maximum possible length "  
        << "of the hash_set is " << i << "." << endl;  
}  
```  
  
##  <a name="op_eq"></a>hash_set::operator=  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 将 hash_set 的元素替换为另一个 hash_set 的副本。  
  
```  
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`right`|要复制到 `hash_set` 中的 [hash_set](../standard-library/hash-set-class.md)。|  
  
### <a name="remarks"></a>备注  
 清除 `hash_set` 中的任何现有元素后，`operator=` 会将 `right` 的内容复制或移动到 `hash_set`。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_operator_as.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set<int> v1, v2, v3;  
   hash_set<int>::iterator iter;  
  
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
  
##  <a name="pointer"></a>hash_set::pointer  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一种类型，此类型提供指向 hash_set 中元素的指针。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;  
```  
  
### <a name="remarks"></a>备注  
 **pointer** 类型可用于修改元素的值。  
  
 在大多数情况下，应使用 [iterator](#iterator) 访问 hash_set 对象中的元素。  
  
   
  
##  <a name="rbegin"></a>hash_set::rbegin  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回一个迭代器，此迭代器用于发现反向 hash_set 中的第一个元素位置。  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>返回值  
 一个反向双向迭代器，用于发现反向 hash_set 中的第一个元素或发现曾是非反向 hash_set 中的最后一个元素位置。  
  
### <a name="remarks"></a>备注  
 `rbegin` 用于反向 hash_set，正如 [begin](#begin) 用于 hash_set 一样。  
  
 如果将 `rbegin` 的返回值赋给 `const_reverse_iterator`，则无法修改 hash_set 对象。 如果将 `rbegin` 的返回值赋给 `reverse_iterator`，则可修改 hash_set 对象。  
  
 `rbegin` 可用于向后循环访问 hash_set。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_rbegin.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::iterator hs1_Iter;  
   hash_set <int>::reverse_iterator hs1_rIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_rIter = hs1.rbegin( );  
   cout << "The first element in the reversed hash_set is "  
        << *hs1_rIter << "." << endl;  
  
   // begin can be used to start an iteration   
   // throught a hash_set in a forward order  
   cout << "The hash_set is: ";  
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );  
         hs1_Iter++ )  
      cout << *hs1_Iter << " ";  
   cout << endl;  
  
   // rbegin can be used to start an iteration   
   // throught a hash_set in a reverse order  
   cout << "The reversed hash_set is: ";  
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );  
         hs1_rIter++ )  
      cout << *hs1_rIter << " ";  
   cout << endl;  
  
   // A hash_set element can be erased by dereferencing to its key   
   hs1_rIter = hs1.rbegin( );  
   hs1.erase ( *hs1_rIter );  
  
   hs1_rIter = hs1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed hash_set is "<< *hs1_rIter << "."  
        << endl;  
}  
```  
  
```Output  
The first element in the reversed hash_set is 30.  
The hash_set is: 10 20 30   
The reversed hash_set is: 30 20 10   
After the erasure, the first element in the reversed hash_set is 20.  
```  
  
##  <a name="reference"></a>hash_set::reference  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一种类型，此类型提供对存储在 hash_set 中的元素的引用。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reference reference;  
```  
  
### <a name="remarks"></a>备注  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_reference.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
  
   // Declare and initialize a reference &Ref1 to the 1st element  
   int &Ref1 = *hs1.begin( );  
  
   cout << "The first element in the hash_set is "  
        << Ref1 << "." << endl;  
  
   // The value of the 1st element of the hash_set can be changed  
   // by operating on its (non-const) reference  
   Ref1 = Ref1 + 5;  
  
   cout << "The first element in the hash_set is now "  
        << *hs1.begin() << "." << endl;  
}  
```  
  
```Output  
The first element in the hash_set is 10.  
The first element in the hash_set is now 15.  
```  
  
##  <a name="rend"></a>hash_set::rend  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回一个迭代器，此迭代器用于发现反向 hash_set 中最后一个元素之后的位置。  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>返回值  
 一个反向双向迭代器，用于发现反向 hash_set 中最后一个元素之后的位置（非反向 hash_set 中第一个元素之前的位置）。  
  
### <a name="remarks"></a>备注  
 `rend` 用于反向 hash_set，正如 [end](#end) 用于 hash_set 一样。  
  
 如果将 `rend` 的返回值赋给 `const_reverse_iterator`，则无法修改 hash_set 对象。 如果将 `rend` 的返回值赋给 `reverse_iterator`，则可修改 hash_set 对象。 不应对 `rend` 返回的值取消引用。  
  
 `rend` 可用于测试反向迭代器是否已到达其 hash_set 的末尾。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_rend.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::iterator hs1_Iter;  
   hash_set <int>::reverse_iterator hs1_rIter;  
   hash_set <int>::const_reverse_iterator hs1_crIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_rIter = hs1.rend( );  
   hs1_rIter--;  
   cout << "The last element in the reversed hash_set is "  
        << *hs1_rIter << "." << endl;  
  
   // end can be used to terminate an iteration   
   // throught a hash_set in a forward order  
   cout << "The hash_set is: ";  
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );  
         hs1_Iter++ )  
      cout << *hs1_Iter << " ";  
   cout << "." << endl;  
  
   // rend can be used to terminate an iteration   
   // through a hash_set in a reverse order  
   cout << "The reversed hash_set is: ";  
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );  
         hs1_rIter++ )  
      cout << *hs1_rIter << " ";  
   cout << "." << endl;  
  
   hs1_rIter = hs1.rend( );  
   hs1_rIter--;  
   hs1.erase ( *hs1_rIter );  
  
   hs1_rIter = hs1.rend( );  
   hs1_rIter--;  
   cout << "After the erasure, the last element in the "  
        << "reversed hash_set is " << *hs1_rIter << "."  
        << endl;  
}  
```  
  
```Output  
The last element in the reversed hash_set is 10.  
The hash_set is: 10 20 30 .  
The reversed hash_set is: 30 20 10 .  
After the erasure, the last element in the reversed hash_set is 20.  
```  
  
##  <a name="reverse_iterator"></a>hash_set::reverse_iterator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一种类型，此类型提供可读取或修改反向 hash_set 中的元素的双向迭代器。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `reverse_iterator` 类型用于反向循环访问 hash_set。  
  
   
  
### <a name="example"></a>示例  
  有关如何声明和使用 `reverse_iterator` 的示例，请参阅 [rbegin](#rbegin) 的示例。  
  
##  <a name="size"></a>hash_set::size  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回 hash_set 中元素的数目。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 hash_set 的当前长度。  
  
### <a name="remarks"></a>备注  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_size.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int> :: size_type i;  
  
   hs1.insert( 1 );  
   i = hs1.size( );  
   cout << "The hash_set length is " << i << "." << endl;  
  
   hs1.insert( 2 );  
   i = hs1.size( );  
   cout << "The hash_set length is now " << i << "." << endl;  
}  
```  
  
```Output  
The hash_set length is 1.  
The hash_set length is now 2.  
```  
  
##  <a name="size_type"></a>hash_set::size_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一种无符号整数类型，此类型可表示 hash_set 中的元素数量。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;  
```  
  
### <a name="remarks"></a>备注  
   
  
### <a name="example"></a>示例  
  有关如何声明和使用 `size_type` 的示例，请参阅 [size](#size) 的示例  
  
##  <a name="swap"></a>hash_set::swap  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 交换两个 hash_set 的元素。  
  
```  
void swap(hash_set& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 参数 hash_set 提供与目标 hash_set 进行交换的元素。  
  
### <a name="remarks"></a>备注  
 此成员函数不会使得用以在所含元素正进行交换的两个 hash_set 中指定元素的任何引用、指针或迭代器无效。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_swap.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1, hs2, hs3;  
   hash_set <int>::iterator hs1_Iter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
   hs2.insert( 100 );  
   hs2.insert( 200 );  
   hs3.insert( 300 );  
  
   cout << "The original hash_set hs1 is:";  
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );  
         hs1_Iter++ )  
         cout << " " << *hs1_Iter;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   hs1.swap( hs2 );  
  
   cout << "After swapping with hs2, list hs1 is:";  
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );  
         hs1_Iter++ )  
         cout << " " << *hs1_Iter;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( hs1, hs3 );  
  
   cout << "After swapping with hs3, list hs1 is:";  
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );  
         hs1_Iter++ )  
         cout << " " << *hs1_Iter;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original hash_set hs1 is: 10 20 30.  
After swapping with hs2, list hs1 is: 200 100.  
After swapping with hs3, list hs1 is: 300.  
```  
  
##  <a name="upper_bound"></a>hash_set::upper_bound  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 返回一个迭代器，此迭代器指向 hash_set 中其键大于指定键的第一个元素。  
  
```  
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的 hash_set 中元素的排序键进行比较的参数键。  
  
### <a name="return-value"></a>返回值  
 一个 **iterator** 或 `const_iterator`，其会发现 hash_set 中其键等于或大于参数键的元素的位置，或如果未找到键的匹配项，则发现 hash_set 中最后一个元素之后的位置。  
  
### <a name="remarks"></a>备注  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_upper_bound.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;  
  
   hs1.insert( 10 );  
   hs1.insert( 20 );  
   hs1.insert( 30 );  
  
   hs1_RcIter = hs1.upper_bound( 20 );  
   cout << "The first element of hash_set hs1 with a key greater "  
        << "than 20 is: " << *hs1_RcIter << "." << endl;  
  
   hs1_RcIter = hs1.upper_bound( 30 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( hs1_RcIter == hs1.end( ) )  
      cout << "The hash_set hs1 doesn't have an element "  
           << "with a key greater than 30." << endl;  
   else  
      cout << "The element of hash_set hs1 with a key > 40 is: "  
           << *hs1_RcIter << "." << endl;  
  
   // An element at a specific location in the hash_set can be found  
   // by using a dereferenced iterator addressing the location  
   hs1_AcIter = hs1.begin( );  
   hs1_RcIter = hs1.upper_bound( *hs1_AcIter );  
   cout << "The first element of hs1 with a key greater than "  
        << endl << "that of the initial element of hs1 is: "  
        << *hs1_RcIter << "." << endl;  
}  
```  
  
```Output  
The first element of hash_set hs1 with a key greater than 20 is: 30.  
The hash_set hs1 doesn't have an element with a key greater than 30.  
The first element of hs1 with a key greater than   
that of the initial element of hs1 is: 20.  
```  
  
##  <a name="value_comp"></a>hash_set::value_comp  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 检索用于对 hash_set 中的元素值进行排序的比较对象副本。  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>返回值  
 返回 hash_set 用来对其元素进行排序的函数对象，即模板参数 `Compare`。  
  
 有关 `Compare` 的详细信息，请参阅 [hash_set 类](../standard-library/hash-set-class.md)主题的备注部分。  
  
### <a name="remarks"></a>备注  
 存储对象用于定义以下成员函数：  
  
 **bool operator**( **const Key&** _ *xVal*, **const Key&** \_ `yVal`);  
  
 如果 `_xVal` 在排序顺序中先于且不等于 `_yVal`，则该函数会返回 **true**。  
  
 请注意，[value_compare](../standard-library/set-class.md#value_compare) 和 [key_compare](../standard-library/set-class.md#key_compare) 皆是模板参数 `Compare` 的同义词。 对于 hash_set 和 hash_multiset 类，会同时提供这两种类型，且二者相同，但为实现与 hash_map 和 hash_multimap 类的兼容性时，二者则不同。  
  
   
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_value_comp.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_set <int, hash_compare < int, less<int> > > hs1;  
   hash_set <int, hash_compare < int, less<int> >  >::value_compare  
      vc1 = hs1.value_comp( );  
   bool result1 = vc1( 2, 3 );  
   if( result1 == true )  
   {  
      cout << "vc1( 2,3 ) returns value of true, "  
           << "where vc1 is the function object of hs1."  
           << endl;  
   }  
   else  
   {  
      cout << "vc1( 2,3 ) returns value of false, "  
           << "where vc1 is the function object of hs1."  
           << endl;  
   }  
  
   hash_set <int, hash_compare < int, greater<int> > > hs2;  
   hash_set<int, hash_compare < int, greater<int> > >::value_compare  
      vc2 = hs2.value_comp( );  
   bool result2 = vc2( 2, 3 );  
   if( result2 == true )  
   {  
      cout << "vc2( 2,3 ) returns value of true, "  
           << "where vc2 is the function object of hs2."  
           << endl;  
   }  
   else  
   {  
      cout << "vc2( 2,3 ) returns value of false, "  
           << "where vc2 is the function object of hs2."  
           << endl;  
   }  
}  
```  
  
##  <a name="value_compare"></a>hash_set::value_compare  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一种类型，它提供两个函数对象：一个是类比较二元谓词（用于比较 hash_set 的两个元素值以确定其相对顺序），另一个是一元谓词（用于对元素进行哈希处理）。  
  
```  
typedef key_compare value_compare;  
```  
  
### <a name="remarks"></a>备注  
 **value_compare** 是模板参数 `Traits` 的同义词。  
  
 有关 `Traits` 的详细信息，请参阅 [hash_set 类](../standard-library/hash-set-class.md)主题。  
  
 请注意，[key_compare](#key_compare) 和 **value_compare** 皆是模板参数 **Traits** 的同义词。 对于 hash_set 和 hash_multiset 类，会同时提供这两种类型，且二者相同，但为实现与 hash_map 和 hash_multimap 类的兼容性时，二者则不同。  
  
   
  
### <a name="example"></a>示例  
  有关如何声明和使用 `value_compare` 的示例，请参阅 [value_comp](#value_comp) 的示例。  
  
##  <a name="value_type"></a>hash_set::value_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 一种类型，此类型将在其容量中存储为 hash_set 元素的对象描述为值。  
  
```  
typedef Key value_type;  
```  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_value_type.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1;  
   hash_set <int>::iterator hs1_Iter;  
  
   hash_set <int> :: value_type hsvt_Int;   // Declare value_type  
   hsvt_Int = 10;             // Initialize value_type  
  
   hash_set <int> :: key_type hskt_Int;   // Declare key_type  
   hskt_Int = 20;             // Initialize key_type  
  
   hs1.insert( hsvt_Int );         // Insert value into hs1  
   hs1.insert( hskt_Int );         // Insert key into hs1  
  
   // A hash_set accepts key_types or value_types as elements  
   cout << "The hash_set has elements:";  
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( ); hs1_Iter++)  
      cout << " " << *hs1_Iter;  
   cout << "." << endl;  
}  
```  
  
```Output  
The hash_set has elements: 10 20.  
```  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)

