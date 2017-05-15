---
title: "hash_multimap 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdext::hash_multimap
- hash_map/stdext::hash_multimap
- hash_multimap
- hash_map/stdext::hash_multimap::allocator_type
- hash_map/stdext::hash_multimap::const_iterator
- hash_map/stdext::hash_multimap::const_pointer
- hash_map/stdext::hash_multimap::const_reference
- hash_map/stdext::hash_multimap::const_reverse_iterator
- hash_map/stdext::hash_multimap::difference_type
- hash_map/stdext::hash_multimap::iterator
- hash_map/stdext::hash_multimap::key_compare
- hash_map/stdext::hash_multimap::key_type
- hash_map/stdext::hash_multimap::mapped_type
- hash_map/stdext::hash_multimap::pointer
- hash_map/stdext::hash_multimap::reference
- hash_map/stdext::hash_multimap::reverse_iterator
- hash_map/stdext::hash_multimap::size_type
- hash_map/stdext::hash_multimap::value_type
- hash_map/stdext::hash_multimap::begin
- hash_map/stdext::hash_multimap::cbegin
- hash_map/stdext::hash_multimap::cend
- hash_map/stdext::hash_multimap::clear
- hash_map/stdext::hash_multimap::count
- hash_map/stdext::hash_multimap::crbegin
- hash_map/stdext::hash_multimap::crend
- hash_map/stdext::hash_multimap::emplace
- hash_map/stdext::hash_multimap::emplace_hint
- hash_map/stdext::hash_multimap::empty
- hash_map/stdext::hash_multimap::end
- hash_map/stdext::hash_multimap::equal_range
- hash_map/stdext::hash_multimap::erase
- hash_map/stdext::hash_multimap::find
- hash_map/stdext::hash_multimap::get_allocator
- hash_map/stdext::hash_multimap::insert
- hash_map/stdext::hash_multimap::key_comp
- hash_map/stdext::hash_multimap::lower_bound
- hash_map/stdext::hash_multimap::max_size
- hash_map/stdext::hash_multimap::rbegin
- hash_map/stdext::hash_multimap::rend
- hash_map/stdext::hash_multimap::size
- hash_map/stdext::hash_multimap::swap
- hash_map/stdext::hash_multimap::upper_bound
- hash_map/stdext::hash_multimap::value_comp
dev_langs:
- C++
helpviewer_keywords:
- hash_multimap class
ms.assetid: f41a6db9-67aa-43a3-a3c5-dbfe9ec3ae7d
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 50239067b11ef3fc8ac5c7d3c4d155dab0dc3822
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="hashmultimap-class"></a>hash_multimap 类
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 容器类 hash_multimap 是 C++ 标准库的扩展，用于存储和快速检索集合中的数据，集合中的每个元素都是具有排序键的元素对，而排序键的值不需要具有唯一性或是相关数据值。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Key,   
    class Type,   
    class Traits=hash_compare <Key, less <Key>>,   
    class Allocator=allocator <pair  <const Key, Type>>>  
class hash_multimap  
```  
  
#### <a name="parameters"></a>参数  
 `Key`  
 要存储在 hash_multimap 中的键数据类型。  
  
 `Type`  
 要存储在 hash_multimap 中的元素数据类型。  
  
 `Traits`  
 此类型包括两个函数对象，其中一个是类 `Traits`，能够作为排序键对两个元素值进行比较，以确定其相对顺序；另一个是哈希函数，这是一个一元谓词，用于将元素的键值映射到 **size_t** 类型的无符号整数。 此自变量是可选自变量，默认值为 `hash_compare``<Key, less<Key> >`。  
  
 `Allocator`  
 该类型表示的是已存储的分配器对象，该对象中封装了有关 hash_multimap 的内存分配和内存释放的详细信息。 此参数是可选参数，默认值为 `allocator<pair <const Key, Type> >`。  
  
## <a name="remarks"></a>备注  
 hash_multimap 为：  
  
-   大小可变的关联容器，支持基于关联键值高效检索元素值。  
  
-   可逆，因为它提供双向迭代器来访问其元素。  
  
-   经过哈希处理，因为其元素分组到了哈希桶中，哈希桶基于应用于元素键值的哈希函数的值。  
  
-   多个，它的元素不需要具有唯一键，因此一个键值可具有多个相关联的元素数据值。  
  
-   关联容器对，因为它的元素值与其键值不同。  
  
-   模板类，因为它提供的功能是一般性的功能，因此与作为元素或键包含的特定数据类型无关。 用于元素和键的数据类型作为类模板以及比较函数和分配器中的参数指定。  
  
 哈希算法相比于排序的主要优点是效率更高；在排序技术中，时间与容器中元素数的对数成正比，而成功的哈希算法可在恒定的平均时间内执行插入、删除和查找操作。 hash_multimap 中某个元素的值，但不是其关联键值，可直接更改。 必须先删除与旧元素关联的键值，才能插入与新元素关联的新键值。  
  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。 经过哈希处理的关联容器针对查找、插入和删除操作进行了优化。 与设计良好的哈希函数一起使用时，显式支持这些操作的成员函数较为高效，执行这些操作的时间为平均恒定值，而不取决于容器中元素的数目。 精心设计的哈希函数将生成统一分布的哈希值，并将最大限度地减少冲突数量，据说当非重复键值映射到相同的哈希值时会发生冲突。 在最坏情况下，使用可能是最差的哈希运算，操作数量与序列中的元素数量成比例（线性时间）。  
  
 将应用程序满足将值与其键关联的条件时，应选择 hash_multimap 作为关联容器。 此类结构的模型是关键字排序列表，这些关键字具有提供定义等的关联字符串值，并且并非始终唯一定义。 相反，如果对关键字进行唯一定义，以使键具有唯一性，那么应选择 hash_map 作为容器。 另一方面，如果仅存储关键字列表，则应使用 hash_set 作为正确容器。 如果允许关键字多次出现，那么相应的容器结构应该是 hash_multiset。  
  
 hash_multimap 通过调用类型 [value_compare](../standard-library/value-compare-class.md) 的已存储哈希 `Traits` 对象，对其控制的序列进行排序。 此存储对象可通过调用成员函数 [key_comp](../standard-library/hash-map-class.md#key_comp) 进行访问。 此类函数对象的行为必须与类 [hash_compare](../standard-library/hash-compare-class.md)`<Key,  less<Key> >` 的对象行为相同。 具体而言，针对类型为 `Key` 的所有值 `Key`，调用 `Traits (Key)` 将对类型为 `size_t` 的值进行分布。  
  
 通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。 这会导致在非等效元素之间进行排序。 在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。 二元谓词 f(x, y) 是包含两个自变量对象（`x` 和 `y`）以及一个返回值（`true` 或 `false`）的函数对象。 如果二元谓词具有非自反性、反对称性和传递性且等效可传递，则对 hash_multimap 进行的排序将为严格弱排序，其中 `x` 和 `y` 两个对象定义为在 f(x, y) 和 f(y, x) 均为 `false` 时等效。 如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。  
  
 受控序列中元素的实际顺序取决于哈希函数、排序函数和存储在容器对象中的哈希表的当前大小。 无法确定哈希表的当前大小，因此通常无法预测受控序列中元素的顺序。 插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。  
  
 hash_multimap 类所提供的迭代器是双向迭代器，但类成员函数 [insert](#insert) 和 [hash_multimap](#hash_multimap) 的版本是将较弱输入迭代器作为模板参数，该迭代器的功能需求比双向迭代器类所保证的功能需求更少。 不同的迭代器概念形成一个系列，通过它们的功能优化相关联。 每个迭代器概念有自己的 hash_multimap 要求，使用这些要求的算法必须根据该类型的迭代器所提供的要求来限制它们的假设。 可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。 这是最小的 hash_multimap 功能，但足以按有意义的方式说明成员函数上下文中的 `[First, Last)` 迭代器范围。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[hash_multimap](#hash_multimap)|构造一个列表，它具有特定大小、具有特定值的元素、包含特定 `allocator` 或作为其他一些 `hash_multimap` 的副本。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|一种类型，此类型表示 `allocator` 对象的 `hash_multimap` 类。|  
|[const_iterator](#const_iterator)|一种类型，此类型提供可读取 `const` 中的 `hash_multimap` 元素的双向迭代器。|  
|[const_pointer](#const_pointer)|一种类型，此类型提供指向 `const` 中的 `hash_multimap` 元素的指针。|  
|[const_reference](#const_reference)|一种类型，此类型提供对存储在 `const` 中的 `hash_multimap` 元素的引用（用于读取和执行 `const` 操作）。|  
|[const_reverse_iterator](#const_reverse_iterator)|一种类型，此类型提供可读取 `const` 中的任何 `hash_multimap` 元素的双向迭代器。|  
|[difference_type](#difference_type)|一种有符号整数类型，此类型可用于表示 `hash_multimap` 中迭代器指向的元素间范围内的元素数量。|  
|[iterator](#iterator)|一种类型，它提供可读取或修改 `hash_multimap` 中任何元素的双向迭代器。|  
|[key_compare](#key_compare)|一种提供函数对象的类型，该函数对象可比较两个排序键以确定 `hash_multimap` 中两个元素的相对顺序。|  
|[key_type](#key_type)|一种类型，此类型描述组成 `hash_multimap` 中每个元素的排序键对象。|  
|[mapped_type](#mapped_type)|一种类型，此类型表示存储在 `hash_multimap` 中的数据类型。|  
|[pointer](#pointer)|一种类型，它提供指向 `hash_multimap` 中的某个元素的指针。|  
|[reference](#reference)|一种类型，此类型提供对存储在 `hash_multimap` 中的元素的引用。|  
|[reverse_iterator](#reverse_iterator)|一种类型，此类型提供可读取或修改反向 `hash_multimap` 中的元素的双向迭代器。|  
|[size_type](#size_type)|可表示 `hash_multimap` 中元素数量的无符号整数类型。|  
|[value_type](#value_type)|一种提供函数对象的类型，该函数对象可将两个元素作为排序键比较以确定它们在 `hash_multimap` 中的相对顺序。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[begin](#begin)|返回一个迭代器，此迭代器用于发现 `hash_multimap` 中的第一个元素。|  
|[cbegin](#cbegin)|返回一个常量迭代器，此迭代器用于发现 `hash_multimap` 中的第一个元素。|  
|[cend](#cend)|返回一个常量迭代器，此迭代器用于发现 `hash_multimap` 中最后一个元素之后的位置。|  
|[clear](#clear)|清除 `hash_multimap` 的所有元素。|  
|[count](#count)|返回 `hash_multimap` 中其键与指定为参数的键匹配的元素数量。|  
|[crbegin](#crbegin)|返回一个常量迭代器，此迭代器用于发现反向 `hash_multimap` 中的第一个元素。|  
|[crend](#crend)|返回一个常量迭代器，此迭代器用于发现反向 `hash_multimap` 中最后一个元素之后的位置。|  
|[emplace](#emplace)|将就地构造的元素插入到 `hash_multimap`。|  
|[emplace_hint](#emplace_hint)|将就地构造的元素插入到 `hash_multimap`，附带位置提示。|  
|[empty](#empty)|测试 `hash_multimap` 是否为空。|  
|[end](#end)|返回一个迭代器，此迭代器用于发现 `hash_multimap` 中最后一个元素之后的位置。|  
|[equal_range](#equal_range)|返回一个迭代器，此迭代器用于发现 `hash_multimap` 中最后一个元素之后的位置。|  
|[erase](#erase)|从指定位置删除 `hash_multimap` 中的一个元素或一系列元素|  
|[find](#find)|返回一个迭代器，此迭代器用于发现 `hash_multimap` 中其键与指定键等效的元素的位置。|  
|[get_allocator](#get_allocator)|返回用于构造 `allocator` 的 `hash_multimap` 对象的副本。|  
|[insert](#insert)|将一个或一系列元素插入到 `hash_multimap` 中的指定位置。|  
|[key_comp](#key_comp)|检索用于对 `hash_multimap` 中的键进行排序的比较对象副本。|  
|[lower_bound](#lower_bound)|返回一个迭代器，此迭代器指向 `hash_multimap` 中其键值等于或大于指定键的键值的第一个元素。|  
|[max_size](#max_size)|返回 `hash_multimap` 的最大长度。|  
|[rbegin](#rbegin)|返回一个迭代器，此迭代器用于发现反向 `hash_multimap` 中的第一个元素。|  
|[rend](#rend)|返回一个迭代器，此迭代器用于发现反向 `hash_multimap` 中最后一个元素之后的位置。|  
|[size](#size)|为 `hash_multimap` 指定新的大小。|  
|[swap](#swap)|交换两个 `hash_multimap` 的元素。|  
|[upper_bound](#upper_bound)|返回一个迭代器，此迭代器指向 `hash_multimap` 中其键值大于指定键的键值的第一个元素。|  
|[value_comp](#value_comp)|检索用于对 `hash_multimap` 中的元素值进行排序的比较对象副本。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[hash_multimap::operator=](#op_eq)|将一个 `hash_multimap` 中的元素替换为另一 `hash_multimap` 副本。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<hash_map>  
  
 **命名空间：** stdext  
  
##  <a name="allocator_type"></a>hash_multimap::allocator_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一个类型，它代表 hash_multimap 对象的分配器类。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;  
```  
  
### <a name="remarks"></a>备注  
 `allocator_type` 是模板参数 `Allocator` 的同义词。  
  
 有关 `Allocator` 的详细信息，请参阅 [hash_multimap 类](../standard-library/hash-multimap-class.md)主题的备注部分。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关使用 `allocator_type` 的示例，请参阅 [get_allocator](#get_allocator) 的示例。  
  
##  <a name="begin"></a>hash_multimap::begin  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回发现 hash_multimap 中第一个元素的位置的迭代器。  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>返回值  
 发现 hash_multimap 中第一个元素的位置或空 hash_multimap 后的位置的双向迭代器。  
  
### <a name="remarks"></a>备注  
 如果 **begin** 的返回值赋给了 `const_iterator`，则无法修改 hash_multimap 对象中的元素。 如果 **begin** 的返回值赋给了 **iterator**，则可修改 hash_multimap 对象中的元素。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_begin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: iterator hm1_Iter;  
   hash_multimap <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 0, 0 ) );  
   hm1.insert ( Int_Pair ( 1, 1 ) );  
   hm1.insert ( Int_Pair ( 2, 4 ) );  
  
   hm1_cIter = hm1.begin ( );  
   cout << "The first element of hm1 is " << hm1_cIter -> first   
        << "." << endl;  
  
   hm1_Iter = hm1.begin ( );  
   hm1.erase ( hm1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // hm1_cIter = hm1.begin ( );  
   // hm1.erase ( hm1_cIter );  
  
   hm1_cIter = hm1.begin( );  
   cout << "The first element of hm1 is now " << hm1_cIter -> first   
        << "." << endl;  
}  
```  
  
```Output  
The first element of hm1 is 0.  
The first element of hm1 is now 1.  
```  
  
##  <a name="cbegin"></a>hash_multimap::cbegin  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回发现 hash_multimap 中第一个元素的位置的常量迭代器。  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 发现 [hash_multimap](../standard-library/hash-multimap-class.md) 中第一个元素的位置或空 `hash_multimap` 之后的位置的常量双向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_cbegin.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 2, 4 ) );  
  
   hm1_cIter = hm1.cbegin ( );  
   cout << "The first element of hm1 is "   
        << hm1_cIter -> first << "." << endl;  
   }  
```  
  
```Output  
The first element of hm1 is 2.  
```  
  
##  <a name="cend"></a>hash_multimap::cend  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回一个常量迭代器，此迭代器用于 hash_multimap 中最后一个元素之后的位置。  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>返回值  
 用于发现 [hash_multimap](../standard-library/hash-multimap-class.md) 中最后一个元素之后的位置的常量双向迭代器。 如果 `hash_multimap` 为空，则 `hash_multimap::cend == hash_multimap::begin`。  
  
### <a name="remarks"></a>备注  
 `cend` 用于测试迭代器是否已到达 hash_multimap 的末尾。  
  
 不应对 `cend` 返回的值取消引用。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_cend.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_cIter = hm1.cend( );  
   hm1_cIter--;  
   cout << "The value of last element of hm1 is "   
        << hm1_cIter -> second << "." << endl;  
   }  
```  
  
```Output  
The value of last element of hm1 is 30.  
```  
  
##  <a name="clear"></a>hash_multimap::clear  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 清除 hash_multimap 的所有元素。  
  
```  
void clear();
```  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  下列示例演示了 hash_multimap::clear 成员函数的用法。  
  
```  
// hash_multimap_clear.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1;  
    hash_multimap<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    hm1.insert(Int_Pair(2, 4));  
  
    i = hm1.size();  
    cout << "The size of the hash_multimap is initially "  
         << i  << "." << endl;  
  
    hm1.clear();  
    i = hm1.size();  
    cout << "The size of the hash_multimap after clearing is "  
         << i << "." << endl;  
}  
```  
  
```Output  
The size of the hash_multimap is initially 2.  
The size of the hash_multimap after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>hash_multimap::const_iterator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 提供可读取 hash_multimap 中 **const** 元素的双向迭代器的类型。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `const_iterator` 类型不能用于修改元素的值。  
  
 hash_multimap 定义的 `const_iterator` 会指向 [value_type](#value_type) 对象，其为 `pair`*\<***constKey, Type***>* 类型。 键值通过第一个成员对可用，已映射元素的值通过第二个成员对可用。  
  
 若要取消引用指向 hash_multimap 中元素的 `const_iterator``cIter`，请使用 **->** 运算符。  
  
 若要访问元素的键值，请使用 `cIter` -> **first**，其等同于 (\* `cIter`)。 **first** 相同。 若要访问元素的映射值，请使用 `cIter` -> **second**，其作用与 (\* `cIter`). **first**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关使用 `const_iterator` 的示例，请参阅 [begin](#begin) 的示例。  
  
##  <a name="const_pointer"></a>hash_multimap::const_pointer  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一种类型，此类型提供指向 hash_multimap 中的 **const** 元素的指针。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>备注  
 `const_pointer` 类型不能用于修改元素的值。  
  
 在大多数情况下，应使用 [iterator](#iterator) 访问 hash_multimap 对象中的元素。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
##  <a name="const_reference"></a>hash_multimap::const_reference  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一种类型，此类型提供对用于读取和执行 **const** 操作的 hash_multimap 中存储的 **const** 元素的引用。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;  
```  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_const_ref.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap<int, int> hm1;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( hm1.begin( ) -> first );  
  
   // The following line would cause an error because the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( hm1.begin( ) -> first );  
  
   cout << "The key of first element in the hash_multimap is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( hm1.begin() -> second );  
  
   cout << "The data value of 1st element in the hash_multimap is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the hash_multimap is 1.  
The data value of 1st element in the hash_multimap is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>hash_multimap::const_reverse_iterator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 提供可读取 hash_multimap 中任何 **const** 元素的双向迭代器的类型。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `const_reverse_iterator` 类型无法修改元素的值，它用于反向循环访问 hash_multimap。  
  
 由 hash_multimap 定义的 `const_reverse_iterator` 会指向 [value_type](#value_type) 的对象（即 `pair`*\<***const Key, Type>** 类型），其第一个成员是元素的键，第二个成员是此元素保留的映射基准。  
  
 若要取消引用指向 hash_multimap 中元素的 `const_reverse_iterator``crIter`，请使用 **->** 运算符。  
  
 若要访问元素的键值，请使用 `crIter` -> **first**，其等同于 (\* `crIter`)。 **first** 相同。 若要访问元素的映射值，请使用 `crIter` -> **second**，其作用与 (\* `crIter`). **first**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `const_reverse_iterator` 的示例，请参阅 [rend](#rend) 的示例。  
  
##  <a name="count"></a>hash_multimap::count  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回 hash_multimap 中其键与指定了参数的键匹配的元素数量。  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要从 hash_multimap 中进行匹配的元素的键。  
  
### <a name="return-value"></a>返回值  
 如果 hash_multimap 包含其排序键与参数键匹配的元素，则返回 1；如果 hash_multimap 不包含带有匹配键的元素，则返回 0。  
  
### <a name="remarks"></a>备注  
 成员函数返回在以下范围内的元素数量：  
  
 **[lower_bound (** `key` **), upper_bound (** `key` **) )**  
  
 这些元素具有键值 `key`。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  下面的示例演示 hash_multimap::count 成员函数的用法。  
  
```  
// hash_multimap_count.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1;  
    hash_multimap<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    hm1.insert(Int_Pair(2, 1));  
    hm1.insert(Int_Pair(1, 4));  
    hm1.insert(Int_Pair(2, 1));  
  
    // Elements do not need to have unique keys in hash_multimap,  
    // so duplicates are allowed and counted  
    i = hm1.count(1);  
    cout << "The number of elements in hm1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = hm1.count(2);  
    cout << "The number of elements in hm1 with a sort key of 2 is: "  
         << i << "." << endl;  
  
    i = hm1.count(3);  
    cout << "The number of elements in hm1 with a sort key of 3 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in hm1 with a sort key of 1 is: 2.  
The number of elements in hm1 with a sort key of 2 is: 2.  
The number of elements in hm1 with a sort key of 3 is: 0.  
```  
  
##  <a name="crbegin"></a>hash_multimap::crbegin  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回一个常量迭代器，此迭代器用于发现反向 hash_multimap 中的第一个元素的位置。  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 一个常量反向双向迭代器，发现反向 [hash_multimap](../standard-library/hash-multimap-class.md) 中的第一个元素位置或发现曾是非反向 `hash_multimap` 中的最后一个元素位置。  
  
### <a name="remarks"></a>备注  
 `crbegin` 用于反向 hash_multimap，正如 [hash_multimap::begin](#begin) 用于 `hash_multimap` 一样。  
  
 返回值为 `crbegin` 时，无法修改 `hash_multimap` 对象。  
  
 `crbegin` 可用于向后循环访问 `hash_multimap`。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_crbegin.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_crIter = hm1.crbegin( );  
   cout << "The first element of the reversed hash_multimap hm1 is "  
        << hm1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed hash_multimap hm1 is 3.  
```  
  
##  <a name="crend"></a>hash_multimap::crend  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回一个常量迭代器，此迭代器用于发现反向 hash_multimap 中最后一个元素之后的位置。  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>返回值  
 用于发现反向 [hash_multimap](../standard-library/hash-multimap-class.md) 中最后一个元素之后的位置（非反向 `hash_multimap` 中第一个元素之前的位置）的常量反向双向迭代器。  
  
### <a name="remarks"></a>备注  
 `crend` 用于反向 hash_multimap，正如 [hash_multimap::end](#end) 用于 hash_multimap 一样。  
  
 返回值为 `crend` 时，无法修改 `hash_multimap` 对象。  
  
 `crend` 可用于测试反向迭代器是否已到达其 hash_multimap 的末尾。  
  
 不应对 `crend` 返回的值取消引用。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_crend.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_crIter = hm1.crend( );  
   hm1_crIter--;  
   cout << "The last element of the reversed hash_multimap hm1 is "  
        << hm1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed hash_multimap hm1 is 3.  
```  
  
##  <a name="difference_type"></a>hash_multimap::difference_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一种带符号整数类型，此类型可用于表示中迭代器指向的元素间范围内 hash_multimap 的元素数量。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;  
```  
  
### <a name="remarks"></a>备注  
 `difference_type` 是通过容器迭代器减少或递增时返回的类型。 `difference_type` 通常用于表示迭代器 `first` 和 `last` 之间的范围 *[ first,  last)* 内元素的数目，包括 `first` 指向的元素以及那一系列元素，但不包括 `last` 指向的元素。  
  
 注意，尽管 `difference_type` 适用于满足输入迭代器（包括可逆容器支持的双向迭代器的类，如集）需求的所有迭代器，迭代器之间的减法仅受随机访问容器（如 vector）提供的随机访问迭代器支持。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_difference_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <hash_map>  
#include <algorithm>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(2, 20));  
    hm1.insert(Int_Pair(1, 10));  
    hm1.insert(Int_Pair(3, 20));  
  
    // The following will insert, because map keys  
    // do not need to be unique  
    hm1.insert(Int_Pair(2, 30));  
  
    hash_multimap<int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;  
    hm1_bIter = hm1.begin();  
    hm1_eIter = hm1.end();  
  
    // Count the number of elements in a hash_multimap  
    hash_multimap<int, int>::difference_type df_count = 0;  
    hm1_Iter = hm1.begin();  
    while (hm1_Iter != hm1_eIter)  
    {  
        df_count++;  
        hm1_Iter++;  
    }  
  
    cout << "The number of elements in the hash_multimap hm1 is: "  
         << df_count << "." << endl;  
  
    cout << "The keys of the mapped elements are:";  
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();  
        hm1_Iter++)  
        cout << " " << hm1_Iter-> first;  
    cout << "." << endl;  
  
    cout << "The values of the mapped elements are:";  
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();  
        hm1_Iter++)  
        cout << " " << hm1_Iter-> second;  
    cout << "." << endl;  
}  
```  
  
```Output  
The number of elements in the hash_multimap hm1 is: 4.  
The keys of the mapped elements are: 1 2 2 3.  
The values of the mapped elements are: 10 20 30 20.  
```  
  
##  <a name="emplace"></a>hash_multimap::emplace  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 将就地构造的元素插入到 hash_multimap 中。  
  
```  
template <class ValTy>  
iterator emplace(ValTy&& val);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`val`|此值用于移动构造要插入到 [hash_multimap](../standard-library/hash-multimap-class.md) 的元素。|  
  
### <a name="return-value"></a>返回值  
 `emplace` 成员函数将返回一个指向新元素插入位置的迭代器。  
  
### <a name="remarks"></a>备注  
 元素的 [hash_multimap::value_type](#value_type) 是一个对，因此元素的值为一个有序对，其中第一个组件相当于键值，第二个组件相当于该元素的数据值。  
  
 从 Visual C++ .NET 2003 开始，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_emplace.cpp  
// compile with: /EHsc  
#include<hash_multimap>  
#include<iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, string> hm1;  
    typedef pair<int, string> is1(1, "a");  
  
    hm1.emplace(move(is1));  
    cout << "After the emplace, hm1 contains:" << endl  
      << " " << hm1.begin()->first  
      << " => " << hm1.begin()->second  
      << endl;  
}  
```  
  
```Output  
After the emplace insertion, hm1 contains:  
 1 => a  
```  
  
##  <a name="emplace_hint"></a>hash_multimap::emplace_hint  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 将就地构造的元素插入到 hash_multimap，并附带位置提示。  
  
```  
template <class ValTy>  
iterator emplace_hint(
    const_iterator _Where,  
    ValTy&& val);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`val`|要插入 [hash_multimap](../standard-library/hash-multimap-class.md) 的用于移动构造元素的值，除非此 `hash_multimap` 已包含该元素（更宽泛地说，是其键经等效排序的元素）。|  
|`_Where`|有关开始搜索正确插入点的位置的提示。|  
  
### <a name="return-value"></a>返回值  
 [hash_multimap::emplace](#emplace) 成员函数将返回一个指向 `hash_multimap` 中新元素插入位置的迭代器。  
  
### <a name="remarks"></a>备注  
 元素的 [hash_multimap::value_type](#value_type) 是一个对，因此元素的值为一个有序对，其中第一个组件相当于键值，第二个组件相当于该元素的数据值。  
  
 如果插入点紧随 `_Where`，则插入可发生在分期常量时间内，而非对数时间内。  
  
 从 Visual C++ .NET 2003 开始，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_emplace_hint.cpp  
// compile with: /EHsc  
#include<hash_multimap>  
#include<iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, string> hm1;  
    typedef pair<int, string> is1(1, "a");  
  
    hm1.emplace(hm1.begin(), move(is1));  
    cout << "After the emplace insertion, hm1 contains:" << endl  
      << " " << hm1.begin()->first  
      << " => " << hm1.begin()->second  
      << endl;  
}  
```  
  
```Output  
After the emplace insertion, hm1 contains:  
 1 => a  
```  
  
##  <a name="empty"></a>hash_multimap::empty  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 测试 hash_multimap 是否为空。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 如果 hash_multimap 为空，则为 **true**；如果 hash_multimap 不为空，则为 **false**。  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_empty.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1, hm2;  
  
   typedef pair <int, int> Int_Pair;  
   hm1.insert ( Int_Pair ( 1, 1 ) );  
  
   if ( hm1.empty( ) )  
      cout << "The hash_multimap hm1 is empty." << endl;  
   else  
      cout << "The hash_multimap hm1 is not empty." << endl;  
  
   if ( hm2.empty( ) )  
      cout << "The hash_multimap hm2 is empty." << endl;  
   else  
      cout << "The hash_multimap hm2 is not empty." << endl;  
}  
```  
  
```Output  
The hash_multimap hm1 is not empty.  
The hash_multimap hm2 is empty.  
```  
  
##  <a name="end"></a>hash_multimap::end  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回一个迭代器，此迭代器用于发现 hash_multimap 中最后一个元素之后的位置。  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>返回值  
 用于发现 hash_multimap 中最后一个元素之后的位置的双向迭代器。 如果 hash_multimap 为空，则 hash_multimap::end == hash_multimap::begin。  
  
### <a name="remarks"></a>备注  
 **end** 用于测试迭代器是否已到达 hash_multimap 的末尾。  
  
 不应对 **end** 返回的值取消引用。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_end.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: iterator hm1_Iter;  
   hash_multimap <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_cIter = hm1.end( );  
   hm1_cIter--;  
   cout << "The value of last element of hm1 is "   
        << hm1_cIter -> second << "." << endl;  
  
   hm1_Iter = hm1.end( );  
   hm1_Iter--;  
   hm1.erase ( hm1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // hm1_cIter = hm1.end ( );  
   // hm1_cIter--;  
   // hm1.erase ( hm1_cIter );  
  
   hm1_cIter = hm1.end( );  
   hm1_cIter--;  
   cout << "The value of last element of hm1 is now "  
        << hm1_cIter -> second << "." << endl;  
}  
```  
  
```Output  
The value of last element of hm1 is 30.  
The value of last element of hm1 is now 20.  
```  
  
##  <a name="equal_range"></a>hash_multimap::equal_range  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回一对迭代器，这两个迭代器分别用于发现 hash_multimap 中其键大于指定键的第一个元素，以及 hash_multimap 中其键等于或大于指定键的第一个元素。  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的 hash_multimap 中元素的排序键进行比较的参数键。  
  
### <a name="return-value"></a>返回值  
 一对迭代器，其中第一个是键的 [lower_bound](#lower_bound)，第二个是键的 [upper_bound](#upper_bound)。  
  
 若要访问成员函数返回的 `pr` 对的第一个迭代器，请使用 `pr`. **first**；若要取消引用下界迭代器，请使用 \*( `pr`. **first**)。 若要访问成员函数返回的 `pr` 对的第二个迭代器，请使用 `pr`. **second**；若要取消引用上界迭代器，请使用 \*( `pr`. **second**)。  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_equal_range.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef hash_multimap <int, int> IntMMap;  
   IntMMap hm1;  
   hash_multimap <int, int> :: const_iterator hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;  
   p1 = hm1.equal_range( 2 );  
  
   cout << "The lower bound of the element with "  
        << "a key of 2\n in the hash_multimap hm1 is: "  
        << p1.first -> second << "." << endl;  
  
   cout << "The upper bound of the element with "  
        << "a key of 2\n in the hash_multimap hm1 is: "  
        << p1.second -> second << "." << endl;  
  
   // Compare the upper_bound called directly   
   hm1_RcIter = hm1.upper_bound( 2 );  
  
   cout << "A direct call of upper_bound( 2 ) gives "  
        << hm1_RcIter -> second << "," << endl  
        << " matching the 2nd element of the pair"  
        << " returned by equal_range( 2 )." << endl;  
  
   p2 = hm1.equal_range( 4 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )  
      cout << "The hash_multimap hm1 doesn't have an element "  
           << "with a key less than 4." << endl;  
   else  
      cout << "The element of hash_multimap hm1 with a key >= 40 is: "  
           << p1.first -> first << "." << endl;  
}  
```  
  
```Output  
The lower bound of the element with a key of 2  
 in the hash_multimap hm1 is: 20.  
The upper bound of the element with a key of 2  
 in the hash_multimap hm1 is: 30.  
A direct call of upper_bound( 2 ) gives 30,  
 matching the 2nd element of the pair returned by equal_range( 2 ).  
The hash_multimap hm1 doesn't have an element with a key less than 4.  
```  
  
##  <a name="erase"></a>hash_multimap::erase  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 从 hash_multimap 中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```  
  
### <a name="parameters"></a>参数  
 `_Where`  
 要从 hash_multimap 移除的元素的位置。  
  
 `first`  
 要从 hash_multimap 中移除的第一个元素的位置。  
  
 `last`  
 紧接要从 hash_multimap 中移除的最后一个元素的位置。  
  
 `key`  
 要从 hash_multimap 中移除的元素的键。  
  
### <a name="return-value"></a>返回值  
 对于前两个成员函数，可为指定已移除的任何元素之外保留的第一个元素；如果此类元素不存在，则为指向 hash_multimap 末尾的指针。  
  
 对于第三个成员函数，则返回已从 hash_multimap 中移除的元素的数目。  
  
### <a name="remarks"></a>备注  
 成员函数从不引发异常。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  下面的示例演示 hash_multimap::erase 成员函数的用法。  
  
```  
// hash_multimap_erase.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1, hm2, hm3;  
    hash_multimap<int, int> :: iterator pIter, Iter1, Iter2;  
    int i;  
    hash_multimap<int, int>::size_type n;  
    typedef pair<int, int> Int_Pair;  
  
    for (i = 1; i < 5; i++)  
    {  
        hm1.insert(Int_Pair (i, i) );  
        hm2.insert(Int_Pair (i, i*i) );  
        hm3.insert(Int_Pair (i, i-1) );  
    }  
  
    // The 1st member function removes an element at a given position  
    Iter1 = ++hm1.begin();  
    hm1.erase(Iter1);  
  
    cout << "After the 2nd element is deleted, "  
         << "the hash_multimap hm1 is:";  
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 2nd member function removes elements  
    // in the range [ first,  last)  
    Iter1 = ++hm2.begin();  
    Iter2 = --hm2.end();  
    hm2.erase(Iter1, Iter2);  
  
    cout << "After the middle two elements are deleted, "  
         << "the hash_multimap hm2 is:";  
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 3rd member function removes elements with a given  key  
    hm3.insert(Int_Pair (2, 5));  
    n = hm3.erase(2);  
  
    cout << "After the element with a key of 2 is deleted,\n"  
         << " the hash_multimap hm3 is:";  
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 3rd member function returns the number of elements removed  
    cout << "The number of elements removed from hm3 is: "  
         << n << "." << endl;  
  
    // The dereferenced iterator can also be used to specify a key  
    Iter1 = ++hm3.begin();  
    hm3.erase(Iter1);  
  
    cout << "After another element with a key equal to that of the"  
         << endl;  
    cout  << " 2nd element is deleted, "  
          << "the hash_multimap hm3 is:";  
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
}  
```  
  
```Output  
After the 2nd element is deleted, the hash_multimap hm1 is: 1 3 4.  
After the middle two elements are deleted, the hash_multimap hm2 is: 1 16.  
After the element with a key of 2 is deleted,  
 the hash_multimap hm3 is: 0 2 3.  
The number of elements removed from hm3 is: 2.  
After another element with a key equal to that of the  
 2nd element is deleted, the hash_multimap hm3 is: 0 3.  
```  
  
##  <a name="find"></a>hash_multimap::find  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回一个迭代器，此迭代器用于发现 hash_multimap 中其键与指定键等效的元素的第一个位置。  
  
```  
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与搜索的 hash_multimap 中元素的排序键匹配的键。  
  
### <a name="return-value"></a>返回值  
 一个迭代器，此迭代器发现具有指定键的元素的第一个位置，或者如果找不到此键的匹配项，则发现 hash_multimap 中最后一个元素后面的位置。  
  
### <a name="remarks"></a>备注  
 此成员函数返回一个迭代器，此迭代器发现 hash_multimap 中其排序键与二元谓词下的参数键**等效**的元素的位置，该谓词基于小于比较关系进行顺序。  
  
 如果将 **find** 的返回值赋给 `const_iterator`，则无法修改 hash_multimap 对象。 如果 **find** 的返回值赋给 **iterator**，则可修改 hash_multimap 对象。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_find.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <hash_map>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1;  
    hash_multimap<int, int> :: const_iterator hm1_AcIter, hm1_RcIter;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 10));  
    hm1.insert(Int_Pair(2, 20));  
    hm1.insert(Int_Pair(3, 20));  
    hm1.insert(Int_Pair(3, 30));  
  
    hm1_RcIter = hm1.find(2);  
    cout << "The element of hash_multimap hm1 with a key of 2 is: "  
          << hm1_RcIter -> second << "." << endl;  
  
    hm1_RcIter = hm1.find(3);  
    cout << "The first element of hash_multimap hm1 with a key of 3 is: "  
          << hm1_RcIter -> second << "." << endl;  
  
    // If no match is found for the key, end() is returned  
    hm1_RcIter = hm1.find(4);  
  
    if (hm1_RcIter == hm1.end())  
        cout << "The hash_multimap hm1 doesn't have an element "  
             << "with a key of 4." << endl;  
    else  
        cout << "The element of hash_multimap hm1 with a key of 4 is: "  
             << hm1_RcIter -> second << "." << endl;  
  
    // The element at a specific location in the hash_multimap can be  
    // found using a dereferenced iterator addressing the location  
    hm1_AcIter = hm1.end();  
    hm1_AcIter--;  
    hm1_RcIter = hm1.find(hm1_AcIter -> first);  
    cout << "The first element of hm1 with a key matching"  
         << endl << "that of the last element is: "  
         << hm1_RcIter -> second << "." << endl;  
  
    // Note that the first element with a key equal to  
    // the key of the last element is not the last element  
    if (hm1_RcIter == --hm1.end())  
        cout << "This is the last element of hash_multimap hm1."  
             << endl;  
    else  
        cout << "This is not the last element of hash_multimap hm1."  
             << endl;  
}  
```  
  
```Output  
The element of hash_multimap hm1 with a key of 2 is: 20.  
The first element of hash_multimap hm1 with a key of 3 is: 20.  
The hash_multimap hm1 doesn't have an element with a key of 4.  
The first element of hm1 with a key matching  
that of the last element is: 20.  
This is not the last element of hash_multimap hm1.  
```  
  
##  <a name="get_allocator"></a>hash_multimap::get_allocator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回用于构造 hash_multimap 的分配器对象的一个副本。  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>返回值  
 hash_multimap 使用的分配器。  
  
### <a name="remarks"></a>备注  
 hash_multimap 类的分配器指定类管理存储的方式。 C++ 标准库容器类提供的默认分配器足以满足大多编程需求。 编写和使用你自己的分配器类是高级 C++ 主题。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_get_allocator.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int>::allocator_type hm1_Alloc;  
   hash_multimap <int, int>::allocator_type hm2_Alloc;  
   hash_multimap <int, double>::allocator_type hm3_Alloc;  
   hash_multimap <int, int>::allocator_type hm4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> hm2;  
   hash_multimap <int, double> hm3;  
  
   hm1_Alloc = hm1.get_allocator( );  
   hm2_Alloc = hm2.get_allocator( );  
   hm3_Alloc = hm3.get_allocator( );  
  
   cout << "The number of integers that can be allocated"  
        << endl << " before free memory is exhausted: "  
        << hm2.max_size( ) << "." << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << " before free memory is exhausted: "  
        << hm3.max_size( ) <<  "." << endl;  
  
   // The following line creates a hash_multimap hm4  
   // with the allocator of hash_multimap hm1.  
   hash_multimap <int, int> hm4( less<int>( ), hm1_Alloc );  
  
   hm4_Alloc = hm4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated by the other  
   if( hm1_Alloc == hm4_Alloc )     
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
  
##  <a name="hash_multimap"></a>hash_multimap::hash_multimap  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 构造一个空的或者是其他某个 hash_multimap 的全部或部分副本的 hash_multimap。  
  
```  
hash_multimap();

explicit hash_multimap(
    const Compare& Comp);

hash_multimap(
    const Compare& Comp,  
    const Allocator& Al);

hash_multimap(
    const hash_multimap& Right);

hash_multimap(
    hash_multimap&& Right);

hash_multimap(
    initializer_list<Type> IList);

hash_multimap(
    initializer_list<Type> IList,  
    const Compare& Comp);

 
hash_multimap(
    initializer_list<Type> IList,  
    const Compare& Comp,  
    const Allocator& Al);

template <class InputIterator>  
hash_multimap(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
hash_multimap(
 InputIterator First,  
    InputIterator Last,  
    const Compare& Comp);

template <class InputIterator>  
hash_multimap(
 InputIterator First,  
    InputIterator Last,  
    const Compare& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`Al`|要用于此 hash_multimap 对象的存储分配器类，默认为 `Allocator`。|  
|`Comp`|用于对映射中元素排序的类型 `const``Traits` 的比较函数，默认为 `Traits`。|  
|`Right`|所构造集要作为其副本的 map 。|  
|`First`|要复制的范围元素中的第一个元素的位置。|  
|`Last`|要复制的元素范围以外的第一个元素的位置。|  
|`IList`|要从中进行复制的 initializer_list。|  
  
### <a name="remarks"></a>备注  
 所有构造函数存储一类分配器对象，此对象管理 hash_multimap 的内存存储，且稍后可通过调用 [get_allocator](#get_allocator) 进行返回。 此分配器参数在类声明中常省略，并使用预处理宏来代替备用分配器。  
  
 所有构造函数对其 hash_multimap 进行初始化。  
  
 所有构造函数会存储 `Traits` 类的函数对象，此对象用于在 hash_multimap 的键之间建立排序，且稍后通过调用 [key_comp](#key_comp) 可进行返回。  
  
 前三个构造函数均指定空的起始 hash_multimap；第二个函数还指定用于建立元素顺序的比较函数 ( `Comp`) 的类型，第三个函数还显式指定了要使用的分配器类型 ( `_Al`)。 关键字 `explicit` 取消了某些种类的自动类型转换。  
  
 第四个构造函数指定 hash_multimap `Right` 的副本。  
  
 接下来的三个构造函数复制映射的范围 `First, Last)`，其指定类 **Traits** 和 Allocator 的比较函数类型和分配器时更加明确。  
  
 第八个构造函数移动 hash_multimap `Right`。  
  
 最后三个构造函数使用 initializer_list。  
  
##  <a name="insert"></a>hash_multimap::insert  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 将一个元素或元素范围插入到 hash_multimap 中。  
  
```  
iterator insert(
    const value_type& Val);

iterator insert(
    const_iterator Where,  
    const value_type& Val);void insert(
    initializer_list<value_type> IList);

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
  
|||  
|-|-|  
|参数|描述|  
|`Val`|将插入 hash_multimap 的元素的值，除非已包含该元素，或更普遍的情况是除非它已包含其键已经过相同排序的元素。|  
|`Where`|有关从哪里开始搜索正确插入点的位置的提示。|  
|`First`|要从映射中复制的第一个元素的位置。|  
|`Last`|要从映射中复制的最后一个元素以外的位置。|  
  
### <a name="return-value"></a>返回值  
 前两个 `insert` 成员函数返回一个指向新元素插入位置的迭代器。  
  
 第三个成员函数针对要插入的元素使用 initializer_list。  
  
 第四个成员函数将元素值序列插入到映射中，它对应于迭代器在指定集内的范围 `[First, Last)` 中所处理的每一个元素。  
  
 最后两个 `insert` 成员函数与前两个成员函数的行为相同，除了它们用于移动构造插入的值。  
  
### <a name="remarks"></a>备注  
 元素的 [value_type](#value_type) 是一个对，从而元素的值为一个有序对，其中第一个组件相当于键值，第二个组件相当于该元素的数据值。  
  
 对于 `insert`的提示版本，如果插入点紧随 `Where`，插入可能发生在分期常量时间内，而非对数时间内。  
  
##  <a name="iterator"></a>hash_multimap::iterator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一种提供双向迭代器的类型，所提供的迭代器可读取或修改 hash_multimap 中的元素。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;  
```  
  
### <a name="remarks"></a>备注  
 由 hash_multimap 定义的 **iterator** 会指向 [value_type](#value_type) 的对象（即 `pair`\< **const Key, Type**> 类型），其第一个成员是元素的键，第二个成员是此元素保留的映射基准。  
  
 若要取消引用指向 hash_multimap 中元素的 **iterator**`Iter`，请使用 **->** 运算符。  
  
 若要访问元素的键值，请使用 `Iter` -> **first**，其等同于 (\* `Iter`)。 **first** 相同。 若要访问元素的映射值，请使用 `Iter` -> **second**，其作用与 (\* `Iter`). **first**。  
  
 **iterator** 类型可用于修改元素的值。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 **iterator** 的示例，请参阅 [begin](#begin) 的示例。  
  
##  <a name="key_comp"></a>hash_multimap::key_comp  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 检索用于对 hash_multimap 中的键进行排序的比较对象的副本。  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>返回值  
 返回 hash_multimap 用来对其元素进行排序的函数对象。  
  
### <a name="remarks"></a>备注  
 存储对象会定义成员函数  
  
 **bool operator(const Key&** `left` **, const Key&** `right` **);**  
  
 如果 `left` 在排序顺序中先于且不等于 `right`，则该函数会返回 **true**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_key_comp.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_multimap <int, int, hash_compare<int, less<int> > > hm1;  
   hash_multimap <int, int, hash_compare<int, less<int> >   
      >::key_compare kc1 = hm1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )  
   {  
      cout << "kc1( 2,3 ) returns value of true,\n"  
           << "where kc1 is the function object of hm1.\n"  
           << endl;  
   }  
   else     
   {  
      cout << "kc1( 2,3 ) returns value of false,\n"  
           << "where kc1 is the function object of hm1.\n"  
           << endl;  
   }  
  
   hash_multimap <int, int, hash_compare<int, greater<int> > > hm2;  
   hash_multimap <int, int, hash_compare<int, greater<int> >   
      >::key_compare kc2 = hm2.key_comp( );  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )  
   {  
      cout << "kc2( 2,3 ) returns value of true,\n"  
           << "where kc2 is the function object of hm2."  
           << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false,\n"  
           << "where kc2 is the function object of hm2."  
           << endl;  
   }  
}  
```  
  
##  <a name="key_compare"></a>hash_multimap::key_compare  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一种提供函数对象的类型，该函数对象可比较两个排序键以确定 hash_multimap 中两个元素的相对顺序。  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>备注  
 **key_compare** 是模板参数 `Traits` 的同义词。  
  
 有关 `Traits` 的详细信息，请参阅 [hash_multimap 类](../standard-library/hash-multimap-class.md)主题。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `key_compare` 的示例，请参阅 [key_comp](#key_comp) 的示例。  
  
##  <a name="key_type"></a>hash_multimap::key_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一种类型，此类型描述组成 hash_multimap 每个元素的排序键对象。  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>备注  
 `key_type` 是模板参数 `Key` 的同义词。  
  
 有关 `Key` 的详细信息，请参阅 [hash_multimap 类](../standard-library/hash-multimap-class.md)主题的备注部分。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `key_compare` 的示例，请参阅 [value_type](#value_type) 的示例。  
  
##  <a name="lower_bound"></a>hash_multimap::lower_bound  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回一个迭代器，此迭代器指向 hash_multimap 中其键等于或大于指定键的第一个元素。  
  
```  
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的 hash_multimap 中元素的排序键进行比较的参数键。  
  
### <a name="return-value"></a>返回值  
 一个 [iterator](#iterator) 或 [const_iterator](#const_iterator)，其会发现 hash_multimap 中其键等于或大于参数键的元素的位置，或如果未找到键的匹配项，则发现 hash_multimap 中最后一个元素之后的位置。  
  
 如果将 `lower_bound` 的返回值赋给 `const_iterator`，则无法修改 hash_multimap 对象。 如果 `lower_bound` 的返回值赋给 **iterator**，则可修改 hash_multimap 对象。  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_lower_bound.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> :: const_iterator hm1_AcIter,   
      hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_RcIter = hm1.lower_bound( 2 );  
   cout << "The element of hash_multimap hm1 with a key of 2 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   hm1_RcIter = hm1.lower_bound( 3 );  
   cout << "The first element of hash_multimap hm1 with a key of 3 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end( ) is returned  
   hm1_RcIter = hm1.lower_bound( 4 );  
  
   if ( hm1_RcIter == hm1.end( ) )  
      cout << "The hash_multimap hm1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of hash_multimap hm1 with a key of 4 is: "  
           << hm1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the hash_multimap can be  
   // found using a dereferenced iterator addressing the location  
   hm1_AcIter = hm1.end( );  
   hm1_AcIter--;  
   hm1_RcIter = hm1.lower_bound( hm1_AcIter -> first );  
   cout << "The first element of hm1 with a key matching"  
        << endl << " that of the last element is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // Note that the first element with a key equal to  
   // the key of the last element is not the last element  
   if ( hm1_RcIter == --hm1.end( ) )  
      cout << "This is the last element of hash_multimap hm1."  
           << endl;  
   else  
      cout << "This is not the last element of hash_multimap hm1."  
           << endl;  
}  
```  
  
```Output  
The element of hash_multimap hm1 with a key of 2 is: 20.  
The first element of hash_multimap hm1 with a key of 3 is: 20.  
The hash_multimap hm1 doesn't have an element with a key of 4.  
The first element of hm1 with a key matching  
 that of the last element is: 20.  
This is not the last element of hash_multimap hm1.  
```  
  
##  <a name="mapped_type"></a>hash_multimap::mapped_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一个类型，它代表 hash_multimap 中存储的数据类型。  
  
```  
typedef Type mapped_type;  
```  
  
### <a name="remarks"></a>备注  
 `mapped_type` 是模板参数 `Type` 的同义词。  
  
 有关 `Type` 的详细信息，请参阅 [hash_multimap 类](../standard-library/hash-multimap-class.md)主题。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `key_type` 的示例，请参阅 [value_type](#value_type) 的示例。  
  
##  <a name="max_size"></a>hash_multimap::max_size  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回 hash_multimap 的最大长度。  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>返回值  
 hash_multimap 的最大可取长度。  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_max_size.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> :: size_type i;  
  
   i = hm1.max_size( );  
   cout << "The maximum possible length "  
        << "of the hash_multimap is " << i << "." << endl;  
}  
```  
  
##  <a name="op_eq"></a>hash_multimap::operator=  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 将 hash_multimap 的元素替换为另一个 hash_multimap 的副本。  
  
```  
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`right`|正在复制到 `hash_multimap` 的 [hash_multimap](../standard-library/hash-multimap-class.md)。|  
  
### <a name="remarks"></a>备注  
 清除 `hash_multimap` 中的任何现有元素后，`operator=` 会将 `right` 的内容复制或移动到 `hash_multimap`。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_operator_as.cpp  
// compile with: /EHsc  
#include <hash_multimap>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap<int, int> v1, v2, v3;  
   hash_multimap<int, int>::iterator iter;  
  
   v1.insert(pair<int, int>(1, 10));  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
}  
```  
  
##  <a name="pointer"></a>hash_multimap::pointer  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一种类型，此类型提供指向 hash_multimap 中元素的指针。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;  
```  
  
### <a name="remarks"></a>备注  
 **pointer** 类型可用于修改元素的值。  
  
 在大多数情况下，应使用 [iterator](#iterator) 访问 hash_multimap 对象中的元素。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
##  <a name="rbegin"></a>hash_multimap::rbegin  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回一个迭代器，此迭代器用于发现反向 hash_multimap 中的第一个元素。  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>返回值  
 一个反向双向迭代器，发现反向 hash_multimap 中的第一个元素位置或发现曾是非反向 hash_multimap 中的最后一个元素位置。  
  
### <a name="remarks"></a>备注  
 `rbegin` 用于反向 hash_multimap，正如 [begin](#begin) 用于 hash_multimap 一样。  
  
 如果将 `rbegin` 的返回值赋给 `const_reverse_iterator`，则无法修改 hash_multimap 对象。 如果将 `rbegin` 的返回值赋给 `reverse_iterator`，则可修改 hash_multimap 对象。  
  
 `rbegin` 可用于向后循环访问 hash_multimap。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_rbegin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: iterator hm1_Iter;  
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;  
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_rIter = hm1.rbegin( );  
   cout << "The first element of the reversed hash_multimap hm1 is "  
        << hm1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a hash_multimap in a forward order  
   cout << "The hash_multimap is: ";  
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)  
      cout << hm1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a hash_multimap in a reverse order  
   cout << "The reversed hash_multimap is: ";  
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)  
      cout << hm1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A hash_multimap element can be erased by dereferencing its key   
   hm1_rIter = hm1.rbegin( );  
   hm1.erase ( hm1_rIter -> first );  
  
   hm1_rIter = hm1.rbegin( );  
   cout << "After the erasure, the first element"  
        << "\n in the reversed hash_multimap is "  
        << hm1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed hash_multimap hm1 is 3.  
The hash_multimap is: 1 2 3 .  
The reversed hash_multimap is: 3 2 1 .  
After the erasure, the first element  
 in the reversed hash_multimap is 2.  
```  
  
##  <a name="reference"></a>hash_multimap::reference  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一种类型，此类型提供对存储在 hash_multimap 中的元素的引用。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;  
```  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_reference.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( hm1.begin( ) -> first );  
  
   // The following line would cause an error as the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( hm1.begin( ) -> first );  
  
   cout << "The key of first element in the hash_multimap is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( hm1.begin( ) -> second );  
  
   cout << "The data value of first element in the hash_multimap is "  
        << Ref2 << "." << endl;  
  
   //The non-const_reference can be used to modify the   
   //data value of the first element  
   Ref2 = Ref2 + 5;  
   cout << "The modified data value of first element is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the hash_multimap is 1.  
The data value of first element in the hash_multimap is 10.  
The modified data value of first element is 15.  
```  
  
##  <a name="rend"></a>hash_multimap::rend  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回一个迭代器，此迭代器用于发现反向 hash_multimap 中最后一个元素之后的位置。  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>返回值  
 一个反向双向迭代器，用于发现反向 hash_multimap 中最后一个元素之后的位置（非反向 hash_multimap 中第一个元素之前的位置）。  
  
### <a name="remarks"></a>备注  
 `rend` 用于反向 hash_multimap，正如 [end](#end) 用于 hash_multimap 一样。  
  
 如果 `rend` 的返回值赋给了 [const_reverse_iterator](#const_reverse_iterator)，则无法修改 hash_multimap 对象。 如果 `rend` 的返回值赋给了 [const_reverse_iterator](#reverse_iterator)，则可修改 hash_multimap 对象。  
  
 `rend` 可用于测试反向迭代器是否已到达其 hash_multimap 的末尾。  
  
 不应对 `rend` 返回的值取消引用。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_rend.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
  
   hash_multimap <int, int> :: iterator hm1_Iter;  
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;  
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_rIter = hm1.rend( );  
   hm1_rIter--;  
   cout << "The last element of the reversed hash_multimap hm1 is "  
        << hm1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a hash_multimap in a forward order  
   cout << "The hash_multimap is: ";  
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)  
      cout << hm1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a hash_multimap in a reverse order  
   cout << "The reversed hash_multimap is: ";  
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)  
      cout << hm1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A hash_multimap element can be erased by dereferencing its key   
   hm1_rIter = --hm1.rend( );  
   hm1.erase ( hm1_rIter -> first );  
  
   hm1_rIter = hm1.rend( );  
   hm1_rIter--;  
   cout << "After the erasure, the last element "  
        << "in the reversed hash_multimap is "  
        << hm1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed hash_multimap hm1 is 1.  
The hash_multimap is: 1 2 3 .  
The reversed hash_multimap is: 3 2 1 .  
After the erasure, the last element in the reversed hash_multimap is 2.  
```  
  
##  <a name="reverse_iterator"></a>hash_multimap::reverse_iterator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一种类型，此类型提供可读取或修改反向 hash_multimap 中的元素的双向迭代器。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `reverse_iterator` 类型用于反向循环访问 hash_multimap。  
  
 hash_multimap 定义的 `reverse_iterator` 会指向 [value_type](#value_type) 对象，其为 `pair`\< **const Key, Type**> 类型。 键值通过第一个成员对可用，已映射元素的值通过对的第二个成员可用。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `reverse_iterator` 的示例，请参阅 [rbegin](#rbegin) 的示例。  
  
##  <a name="size"></a>hash_multimap::size  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回 hash_multimap 中的元素数量。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 hash_multimap 的当前长度。  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  下列示例演示了 hash_multimap::size 成员函数的用法。  
  
```  
// hash_multimap_size.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_multimap<int, int> hm1, hm2;  
    hash_multimap<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    i = hm1.size();  
    cout << "The hash_multimap length is " << i << "." << endl;  
  
    hm1.insert(Int_Pair(2, 4));  
    i = hm1.size();  
    cout << "The hash_multimap length is now " << i << "." << endl;  
}  
```  
  
```Output  
The hash_multimap length is 1.  
The hash_multimap length is now 2.  
```  
  
##  <a name="size_type"></a>hash_multimap::size_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一种无符号整数类型，此类型会对 hash_multimap 中元素的数量计数。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;  
```  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `size_type` 的示例，请参阅 [size](#size) 的示例  
  
##  <a name="swap"></a>hash_multimap::swap  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 交换两个 hash_multimap 的元素。  
  
```  
void swap(hash_multimap& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 hash_multimap 提供要交换的元素或其元素要与 hash_multimap 的元素进行交换的 hash_multimap。  
  
### <a name="remarks"></a>备注  
 此成员函数不会使得用以在所含元素正进行交换的两个 hash_multimap 中指定元素的任何引用、指针或迭代器无效。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_swap.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1, hm2, hm3;  
   hash_multimap <int, int>::iterator hm1_Iter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
   hm2.insert ( Int_Pair ( 10, 100 ) );  
   hm2.insert ( Int_Pair ( 20, 200 ) );  
   hm3.insert ( Int_Pair ( 30, 300 ) );  
  
   cout << "The original hash_multimap hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   hm1.swap( hm2 );  
  
   cout << "After swapping with hm2, hash_multimap hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( hm1, hm3 );  
  
   cout << "After swapping with hm3, hash_multimap hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original hash_multimap hm1 is: 10 20 30.  
After swapping with hm2, hash_multimap hm1 is: 100 200.  
After swapping with hm3, hash_multimap hm1 is: 300.  
```  
  
##  <a name="upper_bound"></a>hash_multimap::upper_bound  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 返回一个迭代器，此迭代器指向 hash_multimap 中其键大于指定键的第一个元素。  
  
```  
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的 hash_multimap 中元素的排序键进行比较的参数键。  
  
### <a name="return-value"></a>返回值  
 一个 [iterator](#iterator) 或 [const_iterator](#const_iterator)，其会发现 hash_multimap 中其键大于参数键的元素的位置，或如果未找到键的匹配项，则发现 hash_multimap 中最后一个元素之后的位置。  
  
 如果将 `upper_bound` 的返回值赋给 `const_iterator`，则无法修改 hash_multimap 对象。 如果 `upper_bound` 的返回值赋给 **iterator**，则可修改 hash_multimap 对象。  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_upper_bound.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
   hm1.insert ( Int_Pair ( 3, 40 ) );  
  
   hm1_RcIter = hm1.upper_bound( 1 );  
   cout << "The 1st element of hash_multimap hm1 with "  
        << "a key greater than 1 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   hm1_RcIter = hm1.upper_bound( 2 );  
   cout << "The first element of hash_multimap hm1\n with a key "  
        << " greater than 2 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end( ) is returned  
   hm1_RcIter = hm1.lower_bound( 4 );  
  
   if ( hm1_RcIter == hm1.end( ) )  
      cout << "The hash_multimap hm1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of hash_multimap hm1 with a key of 4 is: "  
           << hm1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the hash_multimap can be  
   // found using a dereferenced iterator addressing the location  
   hm1_AcIter = hm1.begin( );  
   hm1_RcIter = hm1.upper_bound( hm1_AcIter -> first );  
   cout << "The first element of hm1 with a key greater than"  
        << endl << " that of the initial element of hm1 is: "  
        << hm1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The 1st element of hash_multimap hm1 with a key greater than 1 is: 20.  
The first element of hash_multimap hm1  
 with a key  greater than 2 is: 30.  
The hash_multimap hm1 doesn't have an element with a key of 4.  
The first element of hm1 with a key greater than  
 that of the initial element of hm1 is: 20.  
```  
  
##  <a name="value_comp"></a>hash_multimap::value_comp  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 此成员函数返回一个函数对象，该函数对象可通过比较 hash_multimap 中元素的键值来确定元素顺序。  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>返回值  
 返回 hash_multimap 用来对其元素进行排序的比较函数对象。  
  
### <a name="remarks"></a>备注  
 对于 hash_multimap *m*，如果 *e*1( *k*1 *, d*1) 和 *e*2( *k*2 *, d*2) 两个元素为 [value_type](#value_type) 类型的对象，其中 *k*1 和 *k*2 为 [key_type](#key_type) 类型的键，`d`1 和 `d`2 为 [mapped_type](#mapped_type) 类型的数据，则 *m.*`value_comp`( )( *e*1 *, e*2) 等同于 *m.*`key_comp`( ) ( *k*1 *, k*2)。 存储对象会定义成员函数  
  
 **bool operator**( **value_type&**`left`, **value_type&** `right`);  
  
 如果 `left` 的键值在排序顺序中先于且不等于 `right` 的键值，则该函数会返回 **true**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_value_comp.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_multimap <int, int, hash_compare<int, less<int> > > hm1;  
   hash_multimap <int, int, hash_compare<int, less<int> >   
      >::value_compare vc1 = hm1.value_comp( );  
   hash_multimap <int,int>::iterator Iter1, Iter2;  
  
   Iter1= hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );  
   Iter2= hm1.insert ( hash_multimap <int, int> :: value_type ( 2, 5 ) );  
  
   if( vc1( *Iter1, *Iter2 ) == true )  
   {  
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 1,10 ) does "  
           << "not precede the element ( 2,5 )."  
           << endl;  
   }  
  
   if( vc1( *Iter2, *Iter1 ) == true )     
   {  
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 2,5 ) does "  
           << "not precede the element ( 1,10 )."  
           << endl;  
   }  
}  
```  
  
##  <a name="value_type"></a>hash_multimap::value_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 一种类型，它表示 hash_multimap 中存储的对象类型。  
  
```  
typedef pair<const Key, Type> value_type;  
```  
  
### <a name="remarks"></a>备注  
 `value_type`被声明为对\<const [key_type](#key_type)， [mapped_type](#mapped_type)> 然后不配对\<key_type，mapped_type > 因为不能更改的关联容器的密钥使用非常量的迭代器或引用。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multimap_value_type.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef pair <const int, int> cInt2Int;  
   hash_multimap <int, int> hm1;  
   hash_multimap <int, int> :: key_type key1;  
   hash_multimap <int, int> :: mapped_type mapped1;  
   hash_multimap <int, int> :: value_type value1;  
   hash_multimap <int, int> :: iterator pIter;  
  
   // value_type can be used to pass the correct type  
   // explicitely to avoid implicit type conversion  
   hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );  
  
   // Compare another way to insert objects into a hash_multimap  
   hm1.insert ( cInt2Int ( 2, 20 ) );  
  
   // Initializing key1 and mapped1  
   key1 = ( hm1.begin( ) -> first );  
   mapped1 = ( hm1.begin( ) -> second );  
  
   cout << "The key of first element in the hash_multimap is "  
        << key1 << "." << endl;  
  
   cout << "The data value of first element in the hash_multimap is "  
        << mapped1 << "." << endl;  
  
   // The following line would cause an error because  
   // the value_type is not assignable  
   // value1 = cInt2Int ( 4, 40 );  
  
   cout  << "The keys of the mapped elements are:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
}  
```  
  
```Output  
The key of first element in the hash_multimap is 1.  
The data value of first element in the hash_multimap is 10.  
The keys of the mapped elements are: 1 2.  
The values of the mapped elements are: 10 20.  
```  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)


