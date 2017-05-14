---
title: "hash_map 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdext::hash_map
- hash_map/stdext::hash_map
- hash_map
- hash_map/stdext::hash_map::allocator_type
- hash_map/stdext::hash_map::const_iterator
- hash_map/stdext::hash_map::const_pointer
- hash_map/stdext::hash_map::const_reference
- hash_map/stdext::hash_map::const_reverse_iterator
- hash_map/stdext::hash_map::difference_type
- hash_map/stdext::hash_map::iterator
- hash_map/stdext::hash_map::key_compare
- hash_map/stdext::hash_map::key_type
- hash_map/stdext::hash_map::mapped_type
- hash_map/stdext::hash_map::pointer
- hash_map/stdext::hash_map::reference
- hash_map/stdext::hash_map::reverse_iterator
- hash_map/stdext::hash_map::size_type
- hash_map/stdext::hash_map::value_type
- hash_map/stdext::hash_map::at
- hash_map/stdext::hash_map::begin
- hash_map/stdext::hash_map::cbegin
- hash_map/stdext::hash_map::cend
- hash_map/stdext::hash_map::clear
- hash_map/stdext::hash_map::count
- hash_map/stdext::hash_map::crbegin
- hash_map/stdext::hash_map::crend
- hash_map/stdext::hash_map::emplace
- hash_map/stdext::hash_map::emplace_hint
- hash_map/stdext::hash_map::empty
- hash_map/stdext::hash_map::end
- hash_map/stdext::hash_map::equal_range
- hash_map/stdext::hash_map::erase
- hash_map/stdext::hash_map::find
- hash_map/stdext::hash_map::get_allocator
- hash_map/stdext::hash_map::insert
- hash_map/stdext::hash_map::key_comp
- hash_map/stdext::hash_map::lower_bound
- hash_map/stdext::hash_map::max_size
- hash_map/stdext::hash_map::rbegin
- hash_map/stdext::hash_map::rend
- hash_map/stdext::hash_map::size
- hash_map/stdext::hash_map::swap
- hash_map/stdext::hash_map::upper_bound
- hash_map/stdext::hash_map::value_comp
dev_langs:
- C++
helpviewer_keywords:
- hash_map class
ms.assetid: 40879dfc-51ba-4a59-9f9e-26208de568a8
caps.latest.revision: 25
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
ms.openlocfilehash: e16f164014497c2065c0632534d914067b88bb36
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="hashmap-class"></a>hash_map 类
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 从集合快速存储和检索数据，集合中的每个元素都是一个具有排序关键字和关联数据值的一对值，排序关键字的值是唯一的。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Key,   
    class Type,   
    class Traits=hash_compare<Key, less<Key>>,   
    class Allocator=allocator<pair <const Key, Type>>>  
class hash_map  
```  
  
#### <a name="parameters"></a>参数  
 `Key`  
 要存储在 hash_map 中的键数据类型。  
  
 `Type`  
 要存储在 hash_map 中的元素数据类型。  
  
 `Traits`  
 此类型包括两个函数对象，其中一个是类 compare，可与作为排序关键字的两个元素值进行比较以确定其相对顺序；另一个是哈希函数，这是一个一元谓词，用于将元素的关键字值映射到 `size_t` 类型的无符号整数。 此自变量为可选自变量，默认值为 hash_compare< `Key`, less< `Key`> >。  
  
 `Allocator`  
 一种表示存储的分配器对象的类型，该分配器对象封装有关 hash_map 的内存分配和解除分配的详细信息。 此参数为可选参数，其默认值为 allocator<pair <const `Key`, `Type`>>。  
  
## <a name="remarks"></a>备注  
 hash_map 是：  
  
-   大小可变的关联容器，支持基于关联键值高效检索元素值。  
  
-   可逆，因为它提供双向迭代器来访问其元素。  
  
-   经过哈希处理，因为其元素分组到了哈希桶中，哈希桶基于应用于元素键值的哈希函数的值。  
  
-   唯一，每个元素必须具有唯一键。  
  
-   关联容器对，因为它的元素数据值与其键值不同。  
  
-   模板类，因为它提供的功能是一般性的功能，因此与作为元素或键包含的特定数据类型无关。 用于元素和键的数据类型作为类模板以及比较函数和分配器中的参数指定。  
  
 哈希算法相比于排序的主要优点是效率更高；在排序技术中，时间与容器中元素数的对数成正比，而成功的哈希算法可在恒定的平均时间内执行插入、删除和查找操作。 可以直接更改 hash_map 中的元素值，但不能直接更改其关联的键值。 必须先删除与旧元素关联的键值，才能插入与新元素关联的新键值。  
  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。 经过哈希处理的关联容器针对查找、插入和删除操作进行了优化。 与设计良好的哈希函数一起使用时，显式支持这些操作的成员函数较为高效，执行这些操作的时间为平均恒定值，而不取决于容器中元素的数目。 精心设计的哈希函数将生成统一分布的哈希值，并将最大限度地减少冲突数量，据说当非重复键值映射到相同的哈希值时会发生冲突。 在最坏情况下，使用可能是最差的哈希运算，操作数量与序列中的元素数量成比例（线性时间）。  
  
 当应用程序满足将值与其键关联的条件时，应选择 hash_map 作为关联容器。 此类结构的模型是关键字排序列表，这些关键字只出现一次，并具有提供定义的关联字符串值。 相反，如果关键字有多个正确定义，则此关键字不唯一，应选择 hash_multimap 作为容器。 另一方面，如果仅存储关键字列表，则应使用 hash_set 作为正确容器。 如果允许关键字多次出现，那么相应的容器结构应该是 hash_multiset。  
  
 hash_map 通过调用存储的 [value_compare](../standard-library/value-compare-class.md) 类的哈希 `Traits` 对象，对其控制的序列进行排序。 此存储对象可通过调用成员函数 [key_comp](#key_comp) 进行访问。 此类函数对象的行为必须与类 [hash_compare](../standard-library/hash-compare-class.md)<Key, less\<Key>> 的对象的行为相同。 具体而言，针对类型为 `Key` 的所有值 `Key`，调用 `Traits`( `Key` ) 会提供 `size_t` 类型的值的分布。  
  
 通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。 二元谓词 f(x y) 是包含两个自变量对象（`x` 和 `y`）以及一个返回值（`true` 或 `false`）的函数对象。 如果二元谓词具有自反性、反对称性和传递性且等效可传递，对 hash_map 进行的排序将为严格弱排序，其中两个对象 x 和 y 定义为在 f(x, y) 和 f(y, x) 均为 false 时等效。 如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。  
  
 受控序列中元素的实际顺序取决于哈希函数、排序函数和存储在容器对象中的哈希表的当前大小。 无法确定哈希表的当前大小，因此通常无法预测受控序列中元素的顺序。 插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。  
  
 hash_map 类提供的迭代器是双向迭代器，但类成员函数 [insert](#insert) 和 [hash_map](#hash_map) 的版本是将较弱输入迭代器作为模板参数，该迭代器的功能需求比双向迭代器类保证的功能需求更少。 不同的迭代器概念形成一个系列，通过它们的功能优化相关联。 每个迭代器概念有它自己的一套要求，使用这些概念的算法必须根据迭代器类型提供的要求限制它们的假设。 可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。 这是最小的功能集，但足以按有意义的方式提供类成员函数的上下文中的迭代器范围 `[First, Last)`。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[hash_map](#hash_map)|构造一个空的或者是其他某个 `hash_map` 的全部或部分副本的 `hash_map`。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|一种类型，此类型表示 `allocator` 对象的 `hash_map` 类。|  
|[const_iterator](#const_iterator)|一种类型，此类型提供可读取 `const` 中的 `hash_map` 元素的双向迭代器。|  
|[const_pointer](#const_pointer)|一种类型，此类型提供指向 `const` 中的 `hash_map` 元素的指针。|  
|[const_reference](#const_reference)|一种类型，此类型提供对存储在 `const` 中的 `hash_map` 元素的引用（用于读取和执行 `const` 操作）。|  
|[const_reverse_iterator](#const_reverse_iterator)|一种类型，此类型提供可读取 `const` 中的任何 `hash_map` 元素的双向迭代器。|  
|[difference_type](#difference_type)|一种有符号整数类型，此类型可用于表示 `hash_map` 中迭代器指向的元素间范围内的元素数量。|  
|[iterator](#iterator)|一种类型，它提供可读取或修改 `hash_map` 中任何元素的双向迭代器。|  
|[key_compare](#key_compare)|一种提供函数对象的类型，该函数对象可比较两个排序键以确定 `hash_map` 中两个元素的相对顺序。|  
|[key_type](#key_type)|一种类型，用于描述组成 `hash_map` 中每个元素的排序关键字对象。|  
|[mapped_type](#mapped_type)|一种类型，此类型表示存储在 `hash_map` 中的数据类型。|  
|[pointer](#pointer)|一种类型，它提供指向 `hash_map` 中的某个元素的指针。|  
|[reference](#reference)|一种类型，此类型提供对存储在 `hash_map` 中的元素的引用。|  
|[reverse_iterator](#reverse_iterator)|一种类型，此类型提供可读取或修改反向 `hash_map` 中的元素的双向迭代器。|  
|[size_type](#size_type)|可表示 `hash_map` 中元素数量的无符号整数类型。|  
|[value_type](#value_type)|一种提供函数对象的类型，该函数对象可将两个元素作为排序键比较以确定它们在 `hash_map` 中的相对顺序。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[at](#at)|在 `hash_map` 中查找具有指定关键字值的元素。|  
|[begin](#begin)|返回一个迭代器，此迭代器用于发现 `hash_map` 中的第一个元素。|  
|[cbegin](#cbegin)|返回一个常量迭代器，此迭代器用于发现 `hash_map` 中的第一个元素。|  
|[cend](#cend)|返回一个常量迭代器，此迭代器用于发现 `hash_map` 中最后一个元素之后的位置。|  
|[clear](#clear)|清除 `hash_map` 的所有元素。|  
|[count](#count)|返回 `hash_map` 中其键与指定为参数的键匹配的元素数量。|  
|[crbegin](#crbegin)|返回一个常量迭代器，此迭代器用于发现反向 `hash_map` 中的第一个元素。|  
|[crend](#crend)|返回一个常量迭代器，此迭代器用于发现反向 `hash_map` 中最后一个元素之后的位置。|  
|[emplace](#emplace)|将就地构造的元素插入到 `hash_map`。|  
|[emplace_hint](#emplace_hint)|将就地构造的元素插入到 `hash_map`，附带位置提示。|  
|[empty](#empty)|测试 `hash_map` 是否为空。|  
|[end](#end)|返回一个迭代器，此迭代器用于发现 `hash_map` 中最后一个元素之后的位置。|  
|[equal_range](#equal_range)|返回一对迭代器，这两个迭代器分别用于发现 `hash_map` 中其键大于指定键的第一个元素，以及 `hash_map` 中其键等于或大于指定键的第一个元素。|  
|[erase](#erase)|从指定位置删除 `hash_map` 中的一个元素或一系列元素|  
|[find](#find)|返回一个迭代器，此迭代器用于发现 `hash_map` 中其键与指定键等效的元素的位置。|  
|[get_allocator](#get_allocator)|返回用于构造 `allocator` 的 `hash_map` 对象的副本。|  
|[insert](#insert)|将一个元素或元素范围插入到 `hash_map`。|  
|[key_comp](#key_comp)|返回一个迭代器，此迭代器指向 `hash_map` 中其键值等于或大于指定键的键值的第一个元素。|  
|[lower_bound](#lower_bound)|返回一个迭代器，此迭代器指向 `hash_map` 中其键值等于或大于指定键的键值的第一个元素。|  
|[max_size](#max_size)|返回 `hash_map` 的最大长度。|  
|[rbegin](#rbegin)|返回一个迭代器，此迭代器用于发现反向 `hash_map` 中的第一个元素。|  
|[rend](#rend)|返回一个迭代器，此迭代器用于发现反向 `hash_map` 中最后一个元素之后的位置。|  
|[size](#size)|返回 `hash_map` 中的元素数量。|  
|[swap](#swap)|交换两个 `hash_map` 的元素。|  
|[upper_bound](#upper_bound)|返回一个迭代器，此迭代器指向 `hash_map` 中其键值大于指定键的键值的第一个元素。|  
|[value_comp](#value_comp)|检索用于对 `hash_map` 中的元素值进行排序的比较对象副本。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator[]](#op_at)|将元素插入到具有指定键值的 `hash_map`。|  
|[hash_map::operator=](#op_eq)|将一个 `hash_map` 中的元素替换为另一 `hash_map` 副本。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<hash_map>  
  
 **命名空间：** stdext  
  
##  <a name="allocator_type"></a>hash_map::allocator_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一个类型，它代表 hash_map 对象的分配器类。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;  
```  
  
### <a name="example"></a>示例  
  有关使用 `allocator_type` 的示例，请参阅 [get_allocator](#get_allocator) 的示例。  
  
##  <a name="at"></a>hash_map::at  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 在 hash_map 中查找具有指定键值的元素。  
  
```  
Type& at(const Key& key);

const Type& at(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`key`|要查找的元素的键值。|  
  
### <a name="return-value"></a>返回值  
 对找到的元素数据值的引用。  
  
### <a name="remarks"></a>备注  
 如果未找到参数键值，函数将引发类 [out_of_range 类](../standard-library/out-of-range-class.md)的对象。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_at.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef pair <const int, int> cInt2Int;  
   hash_map <int, int> hm1;  
  
   // Insert data values  
   hm1.insert ( cInt2Int ( 1, 10 ) );  
   hm1.insert ( cInt2Int ( 2, 20 ) );  
   hm1.insert ( cInt2Int ( 3, 30 ) );  
  
   cout  << "The values of the mapped elements are:";  
   for ( int i = 1 ; i <= hm1.size() ; i++ )  
      cout << " " << hm1.at(i);  
   cout << "." << endl;  
}  
```  
  
##  <a name="begin"></a>hash_map::begin  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回发现 hash_map 中第一个元素的位置的迭代器。  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>返回值  
 发现 hash_map 中第一个元素的位置或空 hash_map 后的位置的双向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_begin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: iterator hm1_Iter;  
   hash_map <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 0, 0 ) );  
   hm1.insert ( Int_Pair ( 1, 1 ) );  
   hm1.insert ( Int_Pair ( 2, 4 ) );  
  
   hm1_cIter = hm1.begin ( );  
   cout << "The first element of hm1 is "   
        << hm1_cIter -> first << "." << endl;  
  
   hm1_Iter = hm1.begin ( );  
   hm1.erase ( hm1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // hm1_cIter = hm1.begin ( );  
   // hm1.erase ( hm1_cIter );  
  
   hm1_cIter = hm1.begin( );  
   cout << "The first element of hm1 is now "   
        << hm1_cIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of hm1 is 0.  
The first element of hm1 is now 1.  
```  
  
##  <a name="cbegin"></a>hash_map::cbegin  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回发现 hash_map 中第一个元素的位置的常量迭代器。  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 发现 [hash_map](../standard-library/hash-map-class.md) 中第一个元素的位置或空 `hash_map` 后位置的常量双向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_cbegin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: const_iterator hm1_cIter;  
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
  
##  <a name="cend"></a>hash_map::cend  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回一个常量迭代器，此迭代器用于发现 hash_map 中最后一个元素之后的位置。  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>返回值  
 用于发现 [hash_map](../standard-library/hash-map-class.md) 中最后一个元素之后的位置的常量双向迭代器。 如果 `hash_map` 为空，则 `hash_map::cend == hash_map::begin`。  
  
### <a name="remarks"></a>备注  
 `cend` 用于测试迭代器是否已到达其 `hash_map` 的末尾。  
  
 不应对 `cend` 返回的值取消引用。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_cend.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: const_iterator hm1_cIter;  
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
  
##  <a name="clear"></a>hash_map::clear  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 清除 hash_map 的所有元素。  
  
```  
void clear();
```  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  下列示例演示了 hash_map::clear 成员函数的用法。  
  
```  
// hash_map_clear.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, int> hm1;  
    hash_map<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    hm1.insert(Int_Pair(2, 4));  
  
    i = hm1.size();  
    cout << "The size of the hash_map is initially "  
         << i << "." << endl;  
  
    hm1.clear();  
    i = hm1.size();  
    cout << "The size of the hash_map after clearing is "  
         << i << "." << endl;  
}  
```  
  
```Output  
The size of the hash_map is initially 2.  
The size of the hash_map after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>hash_map::const_iterator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 提供可读取 hash_map 中 **const** 元素的双向迭代器的类型。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `const_iterator` 类型不能用于修改元素的值。  
  
 由 hash_map 定义的 `const_iterator` 会指向作为 [value_type](#value_type) 的对象的元素（即 `pair`*\<***const Key, Type***>* 类型），其第一个成员是元素的键，第二个成员是此元素保留的映射基准。  
  
 若要取消引用指向 hash_map 中元素的 `const_iterator``cIter`，请使用 **->** 运算符。  
  
 若要访问元素的键值，请使用 `cIter` **-> first**，其等同于 (\* `cIter`) **.first**。 若要访问元素的映射基准值，请使用 `cIter` **-> second**，其等同于 (\* `cIter`) **.second**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关使用 `const_iterator` 的示例，请参阅 [begin](#begin) 的示例。  
  
##  <a name="const_pointer"></a>hash_map::const_pointer  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一种类型，此类型提供指向 hash_map 中的 **const** 元素的指针。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>备注  
 `const_pointer` 类型不能用于修改元素的值。  
  
 在大多数情况下，应使用 [iterator](#iterator) 访问 hash_map 对象中的元素。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
##  <a name="const_reference"></a>hash_map::const_reference  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一种类型，此类型提供对用于读取和执行 **const** 操作的 hash_map 中存储的 **const** 元素的引用。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;  
```  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_const_ref.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map<int, int> hm1;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( hm1.begin( ) -> first );  
  
   // The following line would cause an error because the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( hm1.begin( ) -> first );  
  
   cout << "The key of the first element in the hash_map is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( hm1.begin( ) -> second );  
  
   cout << "The data value of the first element in the hash_map is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of the first element in the hash_map is 1.  
The data value of the first element in the hash_map is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>hash_map::const_reverse_iterator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 提供可读取 hash_map 中任何 **const** 元素的双向迭代器的类型。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse)iterator const_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `const_reverse_iterator` 类型无法修改元素的值，它用于反向循环访问 hash_map。  
  
 由 hash_map 定义的 `const_reverse_iterator` 会指向作为 [value_type](#value_type) 的对象的元素（即 `pair`\<**const Key, Type** 类型），其第一个成员是元素的键，第二个成员是此元素保留的映射基准。  
  
 若要取消引用指向 hash_map 中元素的 `const_reverse_iterator``crIter`，请使用 **->** 运算符。  
  
 若要访问元素的键值，请使用 `crIter` -> **first**，其等同于 (\* `crIter`) **.first**。 若要访问元素的映射基准值，请使用 `crIter` -> **second**，其等同于 (\* `crIter`)。 **first**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `const_reverse_iterator` 的示例，请参阅 [rend](#rend) 的示例。  
  
##  <a name="count"></a>hash_map::count  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回 hash_map 中其键与参数指定的键匹配的元素的数量。  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要从 hash_map 中进行匹配的元素的键值。  
  
### <a name="return-value"></a>返回值  
 如果 hash_map 包含其排序键与参数键匹配的元素，则返回 1；如果 hash_map 不包含具有匹配键的元素，则返回 0。  
  
### <a name="remarks"></a>备注  
 成员函数返回以下范围内的元素 *x* 的数量  
  
 [ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) )  
  
 对于唯一的关联容器 hash_map，数量为 0 或 1。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  下面的示例演示如何使用 hash_map::count 成员函数。  
  
```  
// hash_map_count.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, int> hm1;  
    hash_map<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair (1, 1));  
    hm1.insert(Int_Pair (2, 1));  
    hm1.insert(Int_Pair (1, 4));  
    hm1.insert(Int_Pair (2, 1));  
  
    // Keys must be unique in hash_map, so duplicates are ignored  
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
The number of elements in hm1 with a sort key of 1 is: 1.  
The number of elements in hm1 with a sort key of 2 is: 1.  
The number of elements in hm1 with a sort key of 3 is: 0.  
```  
  
##  <a name="crbegin"></a>hash_map::crbegin  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回一个常量迭代器，此迭代器用于发现反向 hash_map 中的第一个元素的位置。  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 发现反向 [hash_map](../standard-library/hash-map-class.md) 中的第一个元素或发现曾是非反向 `hash_map` 中的最后一个元素的常量反向双向迭代器。  
  
### <a name="remarks"></a>备注  
 `crbegin` 用于反向 hash_map，正如 [begin](#begin) 用于 `hash_map` 一样。  
  
 返回值为 `crbegin` 时，无法修改 `hash_map` 对象。  
  
 `crbegin` 可用于向后循环访问 `hash_map`。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_crbegin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_crIter = hm1.crbegin( );  
   cout << "The first element of the reversed hash_map hm1 is "  
        << hm1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed hash_map hm1 is 3.  
```  
  
##  <a name="crend"></a>hash_map::crend  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回一个常量迭代器，此迭代器用于发现反向 hash_map 中最后一个元素之后的位置。  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>返回值  
 用于发现反向 [hash_map](../standard-library/hash-map-class.md) 中最后一个元素之后的位置（非反向 `hash_map` 中第一个元素之前的位置）的常量反向双向迭代器。  
  
### <a name="remarks"></a>备注  
 `crend` 用于反向 `hash_map`，正如 [hash_map::end](#end) 用于 `hash_map` 一样。  
  
 返回值为 `crend` 时，无法修改 `hash_map` 对象。  
  
 `crend` 可用于测试反向迭代器是否已到达其 `hash_map` 的末尾。  
  
 不应对 `crend` 返回的值取消引用。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_crend.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_crIter = hm1.crend( );  
   hm1_crIter--;  
   cout << "The last element of the reversed hash_map hm1 is "  
        << hm1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed hash_map hm1 is 3.  
```  
  
##  <a name="difference_type"></a>hash_map::difference_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一种带符号整数类型，此类型可用于表示中迭代器指向的元素间范围内 hash_map 的元素数量。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;  
```  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <hash_map>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 3, 20 ) );  
  
   // The following won't insert, because map keys are unique  
   hm1.insert ( Int_Pair ( 2, 30 ) );     
  
   hash_map <int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;     
   hm1_bIter = hm1.begin( );  
   hm1_eIter = hm1.end( );  
  
   // Count the number of elements in a hash_map   
   hash_map <int, int>::difference_type  df_count = 0;  
   hm1_Iter = hm1.begin( );  
   while ( hm1_Iter != hm1_eIter)     
   {  
      df_count++;  
      hm1_Iter++;  
   }  
  
   cout << "The number of elements in the hash_map hm1 is: "   
        << df_count << "." << endl;  
  
   cout  << "The keys of the mapped elements are:";  
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;  
         hm1_Iter++)  
      cout << " " << hm1_Iter-> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are:";  
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;  
         hm1_Iter++)  
      cout << " " << hm1_Iter-> second;  
   cout << "." << endl;  
}  
```  
  
```Output  
The number of elements in the hash_map hm1 is: 3.  
The keys of the mapped elements are: 1 2 3.  
The values of the mapped elements are: 10 20 20.  
```  
  
##  <a name="emplace"></a>hash_map::emplace  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 将就地构造的元素插入到 hash_map 中。  
  
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
|`val`|要插入 [hash_map](../standard-library/hash-map-class.md) 的用于移动构造元素的值，除非此 `hash_map` 已包含该元素（更宽泛地说，是其键经等效排序的元素）。|  
  
### <a name="return-value"></a>返回值  
 `hash_map` 成员函数返回一个对，其中，如果完成插入操作，则此对的 bool 组件返回 true，如果 `emplace` 已包含一个其值在排序中具有等效值的元素，则返回 false；此对的迭代器组件返回新元素的插入位置或已包含的元素的位置。  
  
 若要访问此成员函数返回的 `pr` 对的迭代器组件，请使用 `pr.first`；若要对其取消引用，请使用 `*(pr.first)`。 若要访问此成员函数返回的 `pr` 对的 `bool` 组件，请使用 `pr.second`；若要对其取消引用，请使用 `*(pr.second)`。  
  
### <a name="remarks"></a>备注  
 元素的 [hash_map::value_type](#value_type) 是一个对，因此元素的值为一个有序对，其中第一个组件相当于键值，第二个组件相当于该元素的数据值。  
  
 从 Visual C++ .NET 2003 开始，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_emplace.cpp  
// compile with: /EHsc  
#include<hash_map>  
#include<iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, string> hm1;  
    typedef pair<int, string> is1(1, "a");  
  
    hm1.emplace(move(is1));  
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
  
##  <a name="emplace_hint"></a>hash_map::emplace_hint  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 将就地构造的元素插入到 hash_map，并附带位置提示。  
  
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
|`val`|要插入 [hash_map](../standard-library/hash-map-class.md) 的用于移动构造元素的值，除非此 `hash_map` 已包含该元素（更宽泛地说，是其键经等效排序的元素）。|  
|`_Where`|有关开始搜索正确插入点的位置的提示。|  
  
### <a name="return-value"></a>返回值  
 [hash_multimap::emplace](../standard-library/hash-multimap-class.md#emplace) 成员函数返回一个迭代器，此迭代器指向 `hash_map` 中插入的新元素的位置或具有等效顺序的现有元素的所在位置。  
  
### <a name="remarks"></a>备注  
 元素的 [hash_map::value_type](#value_type) 是一个对，因此元素的值为一个有序对，其中第一个组件相当于键值，第二个组件相当于该元素的数据值。  
  
 如果插入点紧随 `_Where`，则插入可发生在分期常量时间内，而非对数时间内。  
  
 从 Visual C++ .NET 2003 开始，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_emplace_hint.cpp  
// compile with: /EHsc  
#include<hash_map>  
#include<iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, string> hm1;  
    typedef pair<int, string> is1(1, "a");  
  
    hm1.emplace(hm1.begin(), move(is1));  
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
  
##  <a name="empty"></a>hash_map::empty  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 测试 hash_map 是否为空。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 如果 hash_map 为空，则为 **true**；如果 hash_map 不为空，则为 **false**。  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_empty.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1, hm2;  
  
   typedef pair <int, int> Int_Pair;  
   hm1.insert ( Int_Pair ( 1, 1 ) );  
  
   if ( hm1.empty( ) )  
      cout << "The hash_map hm1 is empty." << endl;  
   else  
      cout << "The hash_map hm1 is not empty." << endl;  
  
   if ( hm2.empty( ) )  
      cout << "The hash_map hm2 is empty." << endl;  
   else  
      cout << "The hash_map hm2 is not empty." << endl;  
}  
```  
  
```Output  
The hash_map hm1 is not empty.  
The hash_map hm2 is empty.  
```  
  
##  <a name="end"></a>hash_map::end  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回一个迭代器，此迭代器用于发现 hash_map 中最后一个元素之后的位置。  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>返回值  
 用于发现 hash_map 中最后一个元素之后的位置的双向迭代器。 如果 hash_map 为空，则 hash_map::end == hash_map::begin。  
  
### <a name="remarks"></a>备注  
 **end** 用于测试迭代器是否已到达 hash_map 的末尾。  
  
 不应对 **end** 返回的值取消引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_end.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: iterator hm1_Iter;  
   hash_map <int, int> :: const_iterator hm1_cIter;  
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
  
##  <a name="equal_range"></a>hash_map::equal_range  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回一对迭代器，这两个迭代器分别用于发现 hash_map 中其键大于指定键的第一个元素，以及 hash_map 中其键等于或大于指定键的第一个元素。  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的 hash_map 中元素的排序键进行比较的参数键值。  
  
### <a name="return-value"></a>返回值  
 一对迭代器，其中第一个是键的 [lower_bound](#lower_bound)，第二个是键的 [upper_bound](#upper_bound)。  
  
 若要访问成员函数返回的 `pr` 对的第一个迭代器，请使用 `pr`. **first**；若要取消引用下界迭代器，请使用 \*( `pr`. **first**)。 若要访问成员函数返回的 `pr` 对的第二个迭代器，请使用 `pr`. **second**；若要取消引用上界迭代器，请使用 \*( `pr`. **second**)。  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_equal_range.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef hash_map <int, int> IntMap;  
   IntMap hm1;  
   hash_map <int, int> :: const_iterator hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;  
   p1 = hm1.equal_range( 2 );  
  
   cout << "The lower bound of the element with "  
        << "a key of 2 in the hash_map hm1 is: "  
        << p1.first -> second << "." << endl;  
  
   cout << "The upper bound of the element with "  
        << "a key of 2 in the hash_map hm1 is: "  
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
      cout << "The hash_map hm1 doesn't have an element "  
             << "with a key less than 40." << endl;  
   else  
      cout << "The element of hash_map hm1 with a key >= 40 is: "  
           << p1.first -> first << "." << endl;  
}  
```  
  
```Output  
The lower bound of the element with a key of 2 in the hash_map hm1 is: 20.  
The upper bound of the element with a key of 2 in the hash_map hm1 is: 30.  
A direct call of upper_bound( 2 ) gives 30,  
 matching the 2nd element of the pair returned by equal_range( 2 ).  
The hash_map hm1 doesn't have an element with a key less than 40.  
```  
  
##  <a name="erase"></a>hash_map::erase  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 从 hash_map 中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```  
  
### <a name="parameters"></a>参数  
 `_Where`  
 要从 hash_map 移除的元素的位置。  
  
 `first`  
 要从 hash_map 中移除的第一个元素的位置。  
  
 `last`  
 紧接要从 hash_map 中移除的最后一个元素的位置。  
  
 `key`  
 要从 hash_map 中移除的元素的键值。  
  
### <a name="return-value"></a>返回值  
 对于前两个成员函数，可为指定已移除的任何元素之外保留的第一个元素；如果此类元素不存在，则为指向 hash_map 末尾的指针。  
  
 对于第三个成员函数，则返回已从 hash_map 中移除的元素的数目。  
  
### <a name="remarks"></a>备注  
 成员函数从不引发异常。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  下面的示例演示 hash_map::erase 成员函数的用法。  
  
```  
// hash_map_erase.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, int> hm1, hm2, hm3;  
    hash_map<int, int> :: iterator pIter, Iter1, Iter2;  
    int i;  
    hash_map<int, int>::size_type n;  
    typedef pair<int, int> Int_Pair;  
  
    for (i = 1; i < 5; i++)  
    {  
        hm1.insert(Int_Pair (i, i));  
        hm2.insert(Int_Pair (i, i*i));  
        hm3.insert(Int_Pair (i, i-1));  
    }  
  
    // The 1st member function removes an element at a given position  
    Iter1 = ++hm1.begin();  
    hm1.erase(Iter1);  
  
    cout << "After the 2nd element is deleted, the hash_map hm1 is:";  
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 2nd member function removes elements  
    // in the range [ first,  last)  
    Iter1 = ++hm2.begin();  
    Iter2 = --hm2.end();  
    hm2.erase(Iter1, Iter2);  
  
    cout << "After the middle two elements are deleted, "  
         << "the hash_map hm2 is:";  
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 3rd member function removes elements with a given  key  
    n = hm3.erase(2);  
  
    cout << "After the element with a key of 2 is deleted,\n"  
         << "the hash_map hm3 is:";  
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 3rd member function returns the number of elements removed  
    cout << "The number of elements removed from hm3 is: "  
         << n << "." << endl;  
  
    // The dereferenced iterator can also be used to specify a key  
    Iter1 = ++hm3.begin();  
    hm3.erase(Iter1);  
  
    cout << "After another element with a key equal to that"  
         << endl;  
    cout  << "of the 2nd element is deleted, "  
          << "the hash_map hm3 is:";  
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
}  
```  
  
```Output  
After the 2nd element is deleted, the hash_map hm1 is: 1 3 4.  
After the middle two elements are deleted, the hash_map hm2 is: 1 16.  
After the element with a key of 2 is deleted,  
the hash_map hm3 is: 0 2 3.  
The number of elements removed from hm3 is: 1.  
After another element with a key equal to that  
of the 2nd element is deleted, the hash_map hm3 is: 0 3.  
```  
  
##  <a name="find"></a>hash_map::find  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回一个迭代器，此迭代器用于发现 hash_map 中其键与指定键等效的元素的位置。  
  
```  
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的 hash_map 中元素的排序键匹配的键值。  
  
### <a name="return-value"></a>返回值  
 一个迭代器，此迭代器发现具有指定键的元素的位置，或者如果找不到此键的匹配项，则发现 hash_map 中最后一个元素后面的位置。  
  
### <a name="remarks"></a>备注  
 **find** 返回一个发现 hash_map 中其排序键与二元谓词下的参数键等效的元素位置的迭代器，该谓词基于小于比较关系引起排序。  
  
 如果 **find** 的返回值赋给了 [const_iterator](#const_iterator)，则无法修改 hash_map 对象。 如果 **find** 的返回值赋给了 [iterator](#iterator)，则可以修改 hash_map 对象  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_find.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_RcIter = hm1.find( 2 );  
   cout << "The element of hash_map hm1 with a key of 2 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end( ) is returned  
   hm1_RcIter = hm1.find( 4 );  
  
   if ( hm1_RcIter == hm1.end( ) )  
      cout << "The hash_map hm1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of hash_map hm1 with a key of 4 is: "  
           << hm1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the hash_map can be found   
   // using a dereferenced iterator addressing the location  
   hm1_AcIter = hm1.end( );  
   hm1_AcIter--;  
   hm1_RcIter = hm1.find( hm1_AcIter -> first );  
   cout << "The element of hm1 with a key matching "  
        << "that of the last element is: "  
        << hm1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The element of hash_map hm1 with a key of 2 is: 20.  
The hash_map hm1 doesn't have an element with a key of 4.  
The element of hm1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="get_allocator"></a>hash_map::get_allocator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回用于构造 hash_map 的分配器对象的一个副本。  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>返回值  
 hash_map 使用的分配器。  
  
### <a name="remarks"></a>备注  
 hash_map 类的分配器指定类管理存储的方式。 C++ 标准库容器类提供的默认分配器足以满足大多编程需求。 编写和使用你自己的分配器类是高级 C++ 主题。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_get_allocator.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int>::allocator_type hm1_Alloc;  
   hash_map <int, int>::allocator_type hm2_Alloc;  
   hash_map <int, double>::allocator_type hm3_Alloc;  
   hash_map <int, int>::allocator_type hm4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   hash_map <int, int> hm1;  
   hash_map <int, int> hm2;  
   hash_map <int, double> hm3;  
  
   hm1_Alloc = hm1.get_allocator( );  
   hm2_Alloc = hm2.get_allocator( );  
   hm3_Alloc = hm3.get_allocator( );  
  
   cout << "The number of integers that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << hm2.max_size( ) << "." << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << hm3.max_size( ) <<  "." << endl;  
  
   // The following line creates a hash_map hm4  
   // with the allocator of hash_map hm1.  
   hash_map <int, int> hm4( less<int>( ), hm1_Alloc );  
  
   hm4_Alloc = hm4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated with the other  
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
  
##  <a name="hash_map"></a>hash_map::hash_map  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 构造一个空的或者是其他某个 hash_map 的全部或部分副本的 hash_map。  
  
```  
hash_map();

explicit hash_map(
    const Traits& Comp);

hash_map(
    const Traits& Comp,  
    const Allocator& Al);

hash_map(
    const hash_map& Right);

hash_map(
    hash_map&& Right);

hash_map(
    initializer_list<Type> IList);hash_map(initializer_list<Type> IList,  
    const key_compare& Comp);

hash_map(
    initializer_list<Type> IList,  
    const key_compare& Comp,   
    const allocator_type& Al);

template <class InputIterator>  
hash_map(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
hash_map(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp);

template <class InputIterator>  
hash_map(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp,  
    const Allocator& Al  
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`Al`|要用于此 hash_map 对象的存储分配器类，默认为**分配器**。|  
|`Comp`|用于对 hash_map 中元素排序的类常量 `Traits` 的比较函数，默认为 `hash_compare`。|  
|`Right`|所构造映射要作为其副本的 hash_map。|  
|`First`|要复制的范围元素中的第一个元素的位置。|  
|`Last`|要复制的元素范围以外的第一个元素的位置。|  
|`IList`|initializer_list|  
  
### <a name="remarks"></a>备注  
 所有构造函数存储一类分配器对象，此对象管理 hash_map 的内存存储，且稍后可通过调用 [get_allocator](#get_allocator) 进行返回。 此分配器参数在类声明中常省略，并预处理用于代替备用分配器的宏。  
  
 所有构造函数会初始化其 hash_map。  
  
 所有构造函数会存储 `Traits` 类的函数对象，此对象用于在 hash_map 的键之间建立顺序，且稍后通过调用 [key_comp](#key_comp) 可进行返回。  
  
 前三个构造函数均指定空的起始 hash_map，此外，第二个函数还指定用于建立元素顺序的比较函数 ( `Comp`) 的类型，第三个函数还显式指定了要使用的分配器类型 ( `Al`)。 关键字 `explicit` 取消了某些种类的自动类型转换。  
  
 第四个构造函数指定 hash_map `Right` 的副本。  
  
 接下来的三个构造函数复制 hash_map 的范围 `[First, Last)`，其指定类 `Traits` 和 Allocator 的比较函数类型和分配器时更加明确。  
  
 最后一个构造函数会移动 hash_map `Right`。  
  
##  <a name="insert"></a>hash_map::insert  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 将一个元素或元素范围插入到 hash_map。  
  
```  
pair <iterator, bool> insert(
    const value_type& val);

iterator insert(
    const_iterator _Where,  
    const value_type& val);

template <class InputIterator>  
void insert(
    InputIterator first,  
    InputIterator last);

template <class ValTy>  
pair <iterator, bool>  
insert(
    ValTy&& val);

template <class ValTy>  
iterator insert(
    const_iterator _Where,  
    ValTy&& val);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`val`|要插入 hash_map 的元素的值，除非 hash_map 已包含该元素（更宽泛地说，是其键经等效排序的元素）。|  
|`_Where`|有关开始搜索正确插入点的位置的提示。|  
|`first`|要从 hash_map 复制的第一个元素的位置。|  
|`last`|刚超出要从 hash_map 复制的最后一个元素的位置。|  
  
### <a name="return-value"></a>返回值  
 第一个 **insert** 成员函数返回一个对，其中，如果完成插入操作，则此对的 bool 组件返回 true，如果 hash_map 已包含一个其值在排序中具有等效值的元素，则返回 false；此对的迭代器组件返回新元素的插入位置或已包含的元素的位置。  
  
 若要访问此成员函数返回的 `pr` 对的迭代器组件，请使用 `pr`. **first**；若要对其取消引用，请使用 \*( `pr`. **first**)。 若要访问此成员函数返回的 `pr` 对的 `bool` 组件，请使用 `pr`。 **second**；若要对其取消引用，请使用 \*( `pr`. **second**)。  
  
 第二个 **insert** 成员函数（提示版本）返回一个迭代器，此迭代器指向插入到 hash_map 中的新元素的位置。  
  
 除移动构造插入值外，最后两个 **insert** 成员函数与最初两个函数行为相同。  
  
### <a name="remarks"></a>备注  
 元素的 [value_type](../standard-library/map-class.md#value_type) 是一个对，因此元素的值为一个有序对，其中第一个组件相当于键值，第二个组件相当于该元素的数据值。  
  
 对于 insert 的提示版本，如果插入点紧随 `_Where`，则插入可发生在分期常量时间内，而非对数时间内。  
  
 第三个成员函数将元素值序列插入到 hash_map 中，该 hash_map 对应于迭代器在指定集范围 [First, Last) 中所处理的每一个元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_insert.cpp  
// compile with: /EHsc  
#include<hash_map>  
#include<iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, int>::iterator hm1_pIter, hm2_pIter;  
  
    hash_map<int, int> hm1, hm2;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 10));  
    hm1.insert(Int_Pair(2, 20));  
    hm1.insert(Int_Pair(3, 30));  
    hm1.insert(Int_Pair(4, 40));  
  
    cout<< "The original elements (Key => Value) of hm1 are:";  
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)  
        cout << endl << " " << hm1_pIter -> first << " => "  
             << hm1_pIter->second;  
    cout << endl;  
  
    pair< hash_map<int,int>::iterator, bool > pr;  
    pr = hm1.insert(Int_Pair(1, 10));  
  
    if (pr.second == true)  
    {  
        cout<< "The element 10 was inserted in hm1 successfully."  
            << endl;  
    }  
    else  
    {  
        cout<< "The element 10 already exists in hm1\n with a key value of"  
            << "((pr.first) -> first)= "<<(pr.first)-> first  
            << "."<< endl;  
    }  
  
    // The hint version of insert  
    hm1.insert(--hm1.end(), Int_Pair(5, 50));  
  
    cout<< "After the insertions, the elements of hm1 are:";  
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)  
        cout << endl << " " << hm1_pIter -> first << " => "  
             << hm1_pIter->second;  
    cout << endl;  
  
    hm2.insert(Int_Pair(10, 100));  
  
    // The templatized version inserting a range  
    hm2.insert( ++hm1.begin(), --hm1.end() );  
  
    cout<< "After the insertions, the elements of hm2 are:";  
    for (hm2_pIter = hm2.begin(); hm2_pIter != hm2.end(); hm2_pIter++)  
        cout << endl << " " << hm2_pIter -> first << " => "  
             << hm2_pIter->second;  
    cout << endl;  
  
    // The templatized versions move constructing elements  
    hash_map<int, string> hm3, hm4;  
    pair<int, string> is1(1, "a"), is2(2, "b");  
  
    hm3.insert(move(is1));  
    cout << "After the move insertion, hm3 contains:" << endl  
      << " " << hm3.begin()->first  
      << " => " << hm3.begin()->second  
      << endl;  
  
    hm4.insert(hm4.begin(), move(is2));  
    cout << "After the move insertion, hm4 contains:" << endl  
      << " " << hm4.begin()->first  
      << " => " << hm4.begin()->second  
      << endl;  
}  
```  
  
```Output  
The original elements (Key => Value) of hm1 are:  
 1 => 10  
 2 => 20  
 3 => 30  
 4 => 40  
The element 10 already exists in hm1  
 with a key value of((pr.first) -> first)= 1.  
After the insertions, the elements of hm1 are:  
 1 => 10  
 2 => 20  
 3 => 30  
 4 => 40  
 5 => 50  
After the insertions, the elements of hm2 are:  
 2 => 20  
 10 => 100  
 3 => 30  
 4 => 40  
After the move insertion, hm3 contains:  
 1 => a  
After the move insertion, hm4 contains:  
 2 => b  
```  
  
##  <a name="iterator"></a>hash_map::iterator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一种类型，此类型提供可读取或修改 hash_map 中的任何元素的双向迭代器。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;  
```  
  
### <a name="remarks"></a>备注  
 由 hash_map 定义的 **iterator** 会指向作为 [value_type](#value_type) 的对象的元素（即 **pair\<const Key, Type>,** 类型），其第一个成员是元素的键，第二个成员是此元素保留的映射基准。  
  
 若要取消引用指向 multimap 中元素的 **iterator**`Iter`，请使用 **->** 运算符。  
  
 若要访问元素的键值，请使用 `Iter` -> **first**，其等同于 (\* `Iter`)。 **first** 相同。 若要访问元素的映射值，请使用 `Iter` -> **second**，其作用与 (\* `Iter`). **second**。  
  
 **iterator** 类型可用于修改元素的值。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 **iterator** 的示例，请参阅 [begin](#begin) 的示例。  
  
##  <a name="key_comp"></a>hash_map::key_comp  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 检索用于对 hash_map 中的键进行排序的比较对象的副本。  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>返回值  
 返回 hash_map 用来对其元素进行排序的函数对象。  
  
### <a name="remarks"></a>备注  
 存储对象会定义成员函数  
  
 **bool operator**( **const Key&** `left`**, const Key&** `right`);  
  
 如果 `left` 在前且不等于排序顺序中的 `right`，则该函数会返回 **true**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_key_comp.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_map <int, int, hash_compare<int, less<int> > > hm1;  
   hash_map <int, int, hash_compare<int, less<int> > >::key_compare   
      kc1 = hm1.key_comp( ) ;  
  
   // Operator stored in kc1 tests order & returns bool value  
   bool result1 = kc1( 2, 3 ) ;     
   if( result1 == true )     
   {  
      cout << "kc1( 2,3 ) returns value of true,"  
           << "\n where kc1 is the function object of hm1"  
           << " of type key_compare." << endl;  
   }  
   else     
   {  
      cout << "kc1( 2,3 ) returns value of false"  
           << "\n where kc1 is the function object of hm1"  
           << " of type key_compare." << endl;  
   }  
  
   hash_map <int, int, hash_compare<int, greater<int> > > hm2;  
   hash_map <int, int, hash_compare<int, greater<int> > >  
      ::key_compare kc2 = hm2.key_comp( );  
  
   // Operator stored in kc2 tests order & returns bool value  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )  
   {  
      cout << "kc2( 2,3 ) returns value of true,"  
           << "\n where kc2 is the function object of hm2"  
           << " of type key_compare." << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false,"  
           << "\n where kc2 is the function object of hm2"  
           << " of type key_compare." << endl;  
   }  
}  
```  
  
##  <a name="key_compare"></a>hash_map::key_compare  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一种提供函数对象的类型，该函数对象可比较两个排序键以确定映射中两个元素的相对顺序。  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>备注  
 `key_compare` 是模板参数 `Traits` 的同义词。  
  
 有关 `Traits` 的详细信息，请参阅 [hash_map 类](../standard-library/hash-map-class.md)主题。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `key_compare` 的示例，请参阅 [key_comp](#key_comp) 的示例。  
  
##  <a name="key_type"></a>hash_map::key_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一种类型，用于描述组成 hash_map 的每个元素的排序关键字对象。  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>备注  
 `key_type` 是模板参数 `Key` 的同义词。  
  
 有关 `Key` 的详细信息，请参阅 [hash_map 类](../standard-library/hash-map-class.md)主题的备注部分。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `key_type` 的示例，请参阅 [value_type](#value_type) 的示例。  
  
##  <a name="lower_bound"></a>hash_map::lower_bound  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回一个迭代器，此迭代器指向 hash_map 中其键值等于或大于指定键的键值的第一个元素。  
  
```  
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的 hash_map 中元素的排序键进行比较的参数键值。  
  
### <a name="return-value"></a>返回值  
 一个 [iterator](#iterator) 或 [const_iterator](#const_iterator)，其会发现 hash_map 中其键等于或大于参数键的元素的位置，或如果未找到键的匹配项，则发现 hash_map 中最后一个元素之后的位置。  
  
 如果将 `lower_bound` 的返回值赋给 `const_iterator`，则无法修改 hash_map 对象。 如果将 `lower_bound` 的返回值赋给 **iterator**，则无法修改 hash_map 对象。  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_lower_bound.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_RcIter = hm1.lower_bound( 2 );  
   cout << "The first element of hash_map hm1 with a key of 2 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end( ) is returned  
   hm1_RcIter = hm1. lower_bound ( 4 );  
  
   if ( hm1_RcIter == hm1.end( ) )  
      cout << "The hash_map hm1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of hash_map hm1 with a key of 4 is: "  
           << hm1_RcIter -> second << "." << endl;  
  
   // An element at a specific location in the hash_map can be   
   // found using a dereferenced iterator addressing the location  
   hm1_AcIter = hm1.end( );  
   hm1_AcIter--;  
   hm1_RcIter = hm1. lower_bound ( hm1_AcIter -> first );  
   cout << "The element of hm1 with a key matching "  
        << "that of the last element is: "  
        << hm1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The first element of hash_map hm1 with a key of 2 is: 20.  
The hash_map hm1 doesn't have an element with a key of 4.  
The element of hm1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="mapped_type"></a>hash_map::mapped_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一个类型，它代表 hash_map 中存储的数据类型。  
  
```  
typedef Type mapped_type;  
```  
  
### <a name="remarks"></a>备注  
 类型 `mapped_type` 是模板参数 `Type` 的同义词。  
  
 有关 `Type` 的详细信息，请参阅 [hash_map 类](../standard-library/hash-map-class.md)主题。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `key_type` 的示例，请参阅 [value_type](#value_type) 的示例。  
  
##  <a name="max_size"></a>hash_map::max_size  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回 hash_map 的最大长度。  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>返回值  
 hash_map 的最大可取长度。  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_max_size.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
   hash_map <int, int> :: size_type i;  
  
   i = hm1.max_size( );     
   cout << "The maximum possible length "  
        << "of the hash_map is " << i << "."  
        << endl << "(Magnitude is machine specific.)";  
}  
```  
  
##  <a name="op_at"></a>hash_map::operator[]  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 将元素插入到具有指定键值的 `hash_map`。  
  
```  
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`key`|要插入的元素的键值。|  
  
### <a name="return-value"></a>返回值  
 对插入元素的数据值的引用。  
  
### <a name="remarks"></a>备注  
 如果未找到自变量键值，则它将与数据类型的默认值一起插入。  
  
 `operator[]` 可用于将元素插入 `hash_map m`，通过   
  
 `m[ key] = DataValue`;  
  
 在 DataValue 值是具有 `key` 键值的元素的 `mapped_type` 的值处进行插入。  
  
 使用 `operator[]` 插入元素时，返回的引用不会指示插入是更改预先存在的元素还是创建一个新元素。 成员函数 [find](../standard-library/map-class.md#find) 和 [insert](../standard-library/map-class.md#insert) 可用于确定具有指定键的元素在插入前是否已存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_op_ref.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef pair <const int, int> cInt2Int;  
   hash_map <int, int> hm1;  
   hash_map <int, int> :: iterator pIter;  
  
   // Insert a data value of 10 with a key of 1  
   // into a hash_map using the operator[] member function  
   hm1[ 1 ] = 10;  
  
   // Compare other ways to insert objects into a hash_map  
   hm1.insert ( hash_map <int, int> :: value_type ( 2, 20 ) );  
   hm1.insert ( cInt2Int ( 3, 30 ) );  
  
   cout  << "The keys of the mapped elements are:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
  
   // If the key already exists, operator[]  
   // changes the value of the datum in the element  
   hm1[ 2 ] = 40;  
  
   // operator[] will also insert the value of the data  
   // type's default constructor if the value is unspecified  
   hm1[5];  
  
   cout  << "The keys of the mapped elements are now:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are now:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
  
   // opperator[] will also insert by moving a key  
   hash_map <string, int> hm2;  
   string str("a");  
   hm2[move(str)] = 1;  
   cout << "The moved key is " << hm2.begin()->first  
      << ", with value " << hm2.begin()->second << endl;  
}  
```  
  
##  <a name="op_eq"></a>hash_map::operator=  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 将 hash_map 的元素替换为另一个 hash_map 的副本。  
  
```  
hash_map& operator=(const hash_map& right);

hash_map& operator=(hash_map&& right);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`right`|正在复制到 `hash_map` 的 [hash_map 类](../standard-library/hash-map-class.md)。|  
  
### <a name="remarks"></a>备注  
 清除 `hash_map` 中的任何现有元素后，`operator=` 会将 `right` 的内容复制或移动到 `hash_map`。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_operator_as.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map<int, int> v1, v2, v3;  
   hash_map<int, int>::iterator iter;  
  
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
  
##  <a name="pointer"></a>hash_map::pointer  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一种类型，此类型提供指向 hash_map 中元素的指针。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;  
```  
  
### <a name="remarks"></a>备注  
 **pointer** 类型可用于修改元素的值。  
  
 在大多数情况下，应使用 [iterator](#iterator) 访问 hash_map 对象中的元素。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
##  <a name="rbegin"></a>hash_map::rbegin  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回一个迭代器，此迭代器用于发现反向 hash_map 中的第一个元素。  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>返回值  
 发现反向 hash_map 中的第一个元素或发现曾是非反向 hash_map 中的最后一个元素的反向双向迭代器。  
  
### <a name="remarks"></a>备注  
 `rbegin` 用于反向 hash_map，正如 [begin](#begin) 用于 hash_map 一样。  
  
 如果 `rbegin` 的返回值赋给了 [const_reverse_iterator](#const_reverse_iterator)，则无法修改 hash_map 对象。 如果 `rbegin` 的返回值赋给了 [reverse_iterator](#reverse_iterator)，则可修改 hash_map 对象。  
  
 `rbegin` 可用于向后循环访问 hash_map。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_rbegin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: iterator hm1_Iter;  
   hash_map <int, int> :: reverse_iterator hm1_rIter;  
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_rIter = hm1.rbegin( );  
   cout << "The first element of the reversed hash_map hm1 is "  
        << hm1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a hash_map in a forward order  
   cout << "The hash_map is: ";  
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)  
      cout << hm1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a hash_map in a reverse order  
   cout << "The reversed hash_map is: ";  
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)  
      cout << hm1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A hash_map element can be erased by dereferencing to its key   
   hm1_rIter = hm1.rbegin( );  
   hm1.erase ( hm1_rIter -> first );  
  
   hm1_rIter = hm1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed hash_map is "  
        << hm1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed hash_map hm1 is 3.  
The hash_map is: 1 2 3 .  
The reversed hash_map is: 3 2 1 .  
After the erasure, the first element in the reversed hash_map is 2.  
```  
  
##  <a name="reference"></a>hash_map::reference  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一种类型，此类型提供对存储在 hash_map 中的元素的引用。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;  
```  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_reference.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( hm1.begin( ) -> first );  
  
   // The following line would cause an error as the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( hm1.begin( ) -> first );  
  
   cout << "The key of first element in the hash_map is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( hm1.begin( ) -> second );  
  
   cout << "The data value of first element in the hash_map is "  
        << Ref2 << "." << endl;  
  
   // The non-const_reference can be used to modify the   
   // data value of the first element  
   Ref2 = Ref2 + 5;  
   cout << "The modified data value of first element is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the hash_map is 1.  
The data value of first element in the hash_map is 10.  
The modified data value of first element is 15.  
```  
  
##  <a name="rend"></a>hash_map::rend  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回一个迭代器，此迭代器用于发现反向 hash_map 中最后一个元素之后的位置。  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>返回值  
 用于发现反向 hash_map 中最后一个元素之后的位置（非反向 hash_map 中第一个元素之前的位置）的反向双向迭代器。  
  
### <a name="remarks"></a>备注  
 `rend` 用于反向 hash_map，正如 [end](#end) 用于 hash_map 一样。  
  
 如果 `rend` 的返回值赋给了 [const_reverse_iterator](#const_reverse_iterator)，则无法修改 hash_map 对象。 如果 `rend` 的返回值赋给了 [reverse_iterator](#reverse_iterator)，则可修改 hash_map 对象。  
  
 `rend` 可用于测试反向迭代器是否已到达其 hash_map 的末尾。  
  
 不应对 `rend` 返回的值取消引用。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_rend.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: iterator hm1_Iter;  
   hash_map <int, int> :: reverse_iterator hm1_rIter;  
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_rIter = hm1.rend( );  
   hm1_rIter--;  
   cout << "The last element of the reversed hash_map hm1 is "  
        << hm1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a hash_map in a forward order  
   cout << "The hash_map is: ";  
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( );  
   hm1_Iter++)  
      cout << hm1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a hash_map in a reverse order  
   cout << "The reversed hash_map is: ";  
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( );  
      hm1_rIter++)  
      cout << hm1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A hash_map element can be erased by dereferencing to its key   
   hm1_rIter = --hm1.rend( );  
   hm1.erase ( hm1_rIter -> first );  
  
   hm1_rIter = hm1.rend( );  
   hm1_rIter--;  
   cout << "After the erasure, the last element "  
        << "in the reversed hash_map is "  
        << hm1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed hash_map hm1 is 1.  
The hash_map is: 1 2 3 .  
The reversed hash_map is: 3 2 1 .  
After the erasure, the last element in the reversed hash_map is 2.  
```  
  
##  <a name="reverse_iterator"></a>hash_map::reverse_iterator  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一种类型，此类型提供可读取或修改反向 hash_map 中的元素的双向迭代器。  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `reverse_iterator` 类型无法修改元素的值，它用于反向循环访问 hash_map。  
  
 由 hash_map 定义的 `reverse_iterator` 会指向作为 [value_type](#value_type) 的对象的元素（即 **pair\<const Key, Type>** 类型），其第一个成员是元素的键，第二个成员是此元素保留的映射基准。  
  
 若要取消引用指向 hash_map 中元素的 `reverse_iterator``rIter`，请使用 -> 运算符。  
  
 若要访问元素的键值，请使用 `rIter` -> **first**，其等同于 (\* `rIter`)。 **first** 相同。 若要访问元素的映射值，请使用 `rIter` -> **second**，其作用与 (\* `rIter`). **first**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `reverse_iterator` 的示例，请参阅 [rbegin](#rbegin) 的示例。  
  
##  <a name="size"></a>hash_map::size  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回 hash_map 中的元素数量。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 hash_map 的当前长度。  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  下面的示例演示 hash_map::size 成员函数的用法。  
  
```  
// hash_map_size.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, int> hm1, hm2;  
    hash_map<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    i = hm1.size();  
    cout << "The hash_map length is " << i << "." << endl;  
  
    hm1.insert(Int_Pair(2, 4));  
    i = hm1.size();  
    cout << "The hash_map length is now " << i << "." << endl;  
}  
```  
  
```Output  
The hash_map length is 1.  
The hash_map length is now 2.  
```  
  
##  <a name="size_type"></a>hash_map::size_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一种无符号整数类型，此类型可表示 hash_map 中的元素数量。  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;  
```  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `size_type` 的示例，请参阅 [size](#size) 的示例  
  
##  <a name="swap"></a>hash_map::swap  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 交换两个 hash_map 的元素。  
  
```  
void swap(hash_map& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 参数 hash_map 提供与目标 hash_map 进行交换的元素。  
  
### <a name="remarks"></a>备注  
 此成员函数不会使得用以在所含元素正进行交换的两个 hash_map 中指定元素的任何引用、指针或迭代器无效。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_swap.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1, hm2, hm3;  
   hash_map <int, int>::iterator hm1_Iter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
   hm2.insert ( Int_Pair ( 10, 100 ) );  
   hm2.insert ( Int_Pair ( 20, 200 ) );  
   hm3.insert ( Int_Pair ( 30, 300 ) );  
  
   cout << "The original hash_map hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   // hm2 is said to be the argument hash_map;   
   // hm1 is said to be the target hash_map  
   hm1.swap( hm2 );  
  
   cout << "After swapping with hm2, hash_map hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( hm1, hm3 );  
  
   cout << "After swapping with hm3, hash_map hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original hash_map hm1 is: 10 20 30.  
After swapping with hm2, hash_map hm1 is: 100 200.  
After swapping with hm3, hash_map hm1 is: 300.  
```  
  
##  <a name="upper_bound"></a>hash_map::upper_bound  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回一个迭代器，此迭代器指向 hash_map 中其键值大于指定键的键值的第一个元素。  
  
```  
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的 hash_map 中元素的排序键值进行比较的参数键值。  
  
### <a name="return-value"></a>返回值  
 一个 [iterator](#iterator) 或 [const_iterator](#const_iterator)，其会发现 hash_map 中其键大于参数键的元素的位置，或如果未找到键的匹配项，则发现 hash_map 中最后一个元素之后的位置。  
  
 如果将返回值赋给 `const_iterator`，则无法修改 hash_map 对象。 如果将返回值赋给 **iterator**，则无法修改 hash_map 对象。  
  
### <a name="remarks"></a>备注  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_upper_bound.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_RcIter = hm1.upper_bound( 2 );  
   cout << "The first element of hash_map hm1 with a key "  
        << "greater than 2 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end is returned  
   hm1_RcIter = hm1. upper_bound ( 4 );  
  
   if ( hm1_RcIter == hm1.end( ) )  
      cout << "The hash_map hm1 doesn't have an element "  
           << "with a key greater than 4." << endl;  
   else  
      cout << "The element of hash_map hm1 with a key > 4 is: "  
           << hm1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the hash_map can be found   
   // using a dereferenced iterator addressing the location  
   hm1_AcIter = hm1.begin( );  
   hm1_RcIter = hm1. upper_bound ( hm1_AcIter -> first );  
   cout << "The 1st element of hm1 with a key greater than "  
        << "that\n of the initial element of hm1 is: "  
        << hm1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The first element of hash_map hm1 with a key greater than 2 is: 30.  
The hash_map hm1 doesn't have an element with a key greater than 4.  
The 1st element of hm1 with a key greater than that  
 of the initial element of hm1 is: 20.  
```  
  
##  <a name="value_comp"></a>hash_map::value_comp  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 返回一个函数对象，该函数对象可通过比较 hash_map 中元素的键值来确定元素顺序。  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>返回值  
 返回 hash_map 用来对其元素进行排序的比较函数对象。  
  
### <a name="remarks"></a>备注  
 对于 hash_map *m*，如果 *e*1 *(k*1 *, d*1 *)* 和 *e*2 *(k*2 *, d*2 *)* 两个元素为 [value_type](#value_type) 类型的对象，其中 *k*1 和 *k*2 为 [key_type](#key_type) 类型的键，`d`1 和 `d`2 为 [mapped_type](#mapped_type) 类型的数据，则 *m.*`value_comp`*( )(e*1 *, e*2 *)* 等同于 *m.*`key_comp`*( ) (k*1 *, k*2 *)*。 存储对象会定义成员函数  
  
 **bool operator**( **value_type&** `left`, **value_type&** `right`) **;**。  
  
 如果 `left` 的键值在排序顺序中先于且不等于 `right` 的键值，则该函数会返回 **true**。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_value_comp.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_map <int, int, hash_compare<int, less<int> > > hm1;  
   hash_map <int, int, hash_compare<int, less<int> > >  
   ::value_compare vc1 = hm1.value_comp( );  
   pair< hash_map<int,int>::iterator, bool > pr1, pr2;  
  
   pr1= hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );  
   pr2= hm1.insert ( hash_map <int, int> :: value_type ( 2, 5 ) );  
  
   if( vc1( *pr1.first, *pr2.first ) == true )     
   {  
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."  
           << endl;  
   }  
  
   if( vc1 ( *pr2.first, *pr1.first ) == true )  
   {  
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."  
           << endl;  
   }  
}  
```  
  
##  <a name="value_type"></a>hash_map::value_type  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 一种类型，它表示 hash_map 中存储的对象类型。  
  
```  
typedef pair<const Key, Type> value_type;  
```  
  
### <a name="remarks"></a>备注  
 `value_type` 被声明为 `pair` *\<***const**[key_type](#key_type), [mapped_type](#mapped_type)*>* 而不是 `pair`**\<key_type, mapped_type>**，因为使用非常量迭代器或引用可能不会更改关联容器的键。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_map_value_type.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   typedef pair <const int, int> cInt2Int;  
   hash_map <int, int> hm1;  
   hash_map <int, int> :: key_type key1;  
   hash_map <int, int> :: mapped_type mapped1;  
   hash_map <int, int> :: value_type value1;  
   hash_map <int, int> :: iterator pIter;  
  
   // value_type can be used to pass the correct type  
   // explicitely to avoid implicit type conversion  
   hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );  
  
   // Compare other ways to insert objects into a hash_map  
   hm1.insert ( cInt2Int ( 2, 20 ) );  
   hm1[ 3 ] = 30;  
  
   // Initializing key1 and mapped1  
   key1 = ( hm1.begin( ) -> first );  
   mapped1 = ( hm1.begin( ) -> second );  
  
   cout << "The key of first element in the hash_map is "  
        << key1 << "." << endl;  
  
   cout << "The data value of first element in the hash_map is "  
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
The key of first element in the hash_map is 1.  
The data value of first element in the hash_map is 10.  
The keys of the mapped elements are: 1 2 3.  
The values of the mapped elements are: 10 20 30.  
```  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)


