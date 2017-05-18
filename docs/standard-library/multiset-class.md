---
title: "multiset 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- set/std::multiset
- multiset
- set/std::multiset::allocator_type
- set/std::multiset::const_iterator
- set/std::multiset::const_pointer
- set/std::multiset::const_reference
- set/std::multiset::const_reverse_iterator
- set/std::multiset::difference_type
- set/std::multiset::iterator
- set/std::multiset::key_compare
- set/std::multiset::key_type
- set/std::multiset::pointer
- set/std::multiset::reference
- set/std::multiset::reverse_iterator
- set/std::multiset::size_type
- set/std::multiset::value_compare
- set/std::multiset::value_type
- set/std::multiset::begin
- set/std::multiset::cbegin
- set/std::multiset::cend
- set/std::multiset::clear
- set/std::multiset::count
- set/std::multiset::crbegin
- set/std::multiset::crend
- set/std::multiset::emplace
- set/std::multiset::emplace_hint
- set/std::multiset::empty
- set/std::multiset::end
- set/std::multiset::equal_range
- set/std::multiset::erase
- set/std::multiset::find
- set/std::multiset::get_allocator
- set/std::multiset::insert
- set/std::multiset::key_comp
- set/std::multiset::lower_bound
- set/std::multiset::max_size
- set/std::multiset::rbegin
- set/std::multiset::rend
- set/std::multiset::size
- set/std::multiset::swap
- set/std::multiset::upper_bound
- set/std::multiset::value_comp
dev_langs:
- C++
helpviewer_keywords:
- multiset class
ms.assetid: 630e8c10-0ce9-4ad9-8d79-9e91a600713f
caps.latest.revision: 21
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
ms.openlocfilehash: ff713a2813798c82b42ecc814d433e64ba2a51a6
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="multiset-class"></a>multiset 类
C++ 标准库多重集合类用于存储和检索集合中的数据，此集合中包含的元素值无需唯一，并且用作数据自动排序所依据的键值。 不能直接更改多重集合中元素的键值。 必须先删除旧值，才能插入具有新值的元素。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Key, class Compare =less <Key>, class Allocator =allocator <Key>>  
class multiset  
```  
  
#### <a name="parameters"></a>参数  
 *Key*  
 要存储在多重集合中的元素数据类型。  
  
 *Compare*  
 一种提供函数对象的类型，该函数对象可将两个元素值作为排序键进行比较，以确定其在多重集合中的相对顺序。 默认值是二元谓词 **less**\<Key>。  
  
 在 C++ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。 有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 一种表示存储的分配器对象的类型，该分配器对象封装有关多重集合的内存分配和解除分配的详细信息。 默认值为 **allocator***\<Key>。*  
  
## <a name="remarks"></a>备注  
 C++ 标准库多重集合类为：  
  
-   大小可变的关联容器，支持基于关联键值高效检索元素值。  
  
-   可逆，因为它提供双向迭代器来访问其元素。  
  
-   有序，因为它的元素在容器中根据指定的比较函数按键值排序。  
  
-   多个，它的元素不需要具有唯一键，因此一个键值可具有多个相关联的元素值。  
  
-   简单的关联容器，因为它的元素值即为它的键值。  
  
-   模板类，因为它提供的功能是一般性的功能，因此与作为元素包含的特定数据类型无关。 可使用的数据类型作为类模板以及比较函数和分配器中的参数指定。  
  
 多重集合类提供的迭代器是双向迭代器，但类成员函数 [insert](#insert) 和 [multiset](#multiset) 具有将较弱输入迭代器作为模板参数的版本，较弱输入迭代器的功能需求比双向迭代器类保证的功能需求更少。 不同的迭代器概念形成一个系列，通过它们的功能优化相关联。 每个迭代器概念有它自己的一套要求，使用这些概念的算法必须根据迭代器类型提供的要求限制它们的假设。 可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。 这是最小的功能集，但足以按有意义的方式提供类成员函数的上下文中的迭代器范围 [`First`, `Last`)。  
  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。 关联容器针对查找、插入和移除操作进行了优化。 显式支持这些操作的成员函数较为高效，执行这些操作的时间与容器中元素数量的对数平均成比例。 插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。  
  
 当应用程序满足将值与其键关联的条件时，应选择多重集合作为关联容器。 多重集合的元素可以为多个，并用作其自己的排序键，因此键不是唯一的。 此类结构的模型是排序列表，如关键字排序列表，其中关键字可以出现多次。 如果不允许关键字多次出现，则应使用集作为适当的容器结构。 如果将唯一定义作为值附加到唯一关键字的列表，则映射应为包含此数据的适当结构。 如果定义不唯一，则应选择多重映射作为容器。  
  
 多重集合通过调用存储的 `Compare` 类型的函数对象，对它控制的序列进行排序。 此存储对象是比较函数，可通过调用成员函数 [key_comp](#key_comp) 进行访问。 通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。 二元谓词 *f*( *x*, *y*) 是包含两个参数对象（*x* 和 *y*）以及一个返回值（**true** 或 **false**）的函数对象。 如果二元谓词具有自反性、反对称性和传递性且等效可传递，对集进行的排序将为严格弱排序，其中两个对象 x 和 y 定义为在 *f*( *x,y*) 和 *f*( *y,x*) 均为 false 时等效。 如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。  
  
 在 C++ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。 有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[multiset](#multiset)|构造一个空的或者是指定 `multiset` 的全部或部分副本的 `multiset`。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|`allocator` 对象的 `multiset` 类的 typedef。|  
|[const_iterator](#const_iterator)|可读取 `const` 中 `multiset` 元素的双向迭代器的 typedef。|  
|[const_pointer](#const_pointer)|指向 `const` 中的 `multiset` 元素的指针的 typedef。|  
|[const_reference](#const_reference)|对存储在 `const` 中的 `multiset` 元素的引用（用于读取和执行 `const` 操作）的 typedef。|  
|[const_reverse_iterator](#const_reverse_iterator)|可读取 `const` 中任何 `multiset` 元素的双向迭代器的 typedef。|  
|[difference_type](#difference_type)|`multiset` 中迭代器指向的元素间范围内元素数量的有符号整数 typedef。|  
|[iterator](#iterator)|可读取或修改 `multiset` 中任何元素的双向迭代器的 typedef。|  
|[key_compare](#key_compare)|可比较两个键以确定 `multiset` 中两个元素的相对顺序的函数对象的 typedef。|  
|[key_type](#key_type)|可比较两个排序键以确定 `multiset` 中两个元素的相对顺序的函数对象的 typedef。|  
|[pointer](#pointer)|指向 `multiset` 中的元素的指针的 typedef。|  
|[reference](#reference)|对 `multiset` 中存储的元素的引用的 typedef。|  
|[reverse_iterator](#reverse_iterator)|可读取或修改反向 `multiset` 中的元素的双向迭代器的 typedef。|  
|[size_type](#size_type)|可表示 `multiset` 中元素数量的无符号整数类型。|  
|[value_compare](#value_compare)|可将两个元素作为排序键比较以确定它们在 `multiset` 中的相对顺序的函数对象的 typedef。|  
|[value_type](#value_type)|一个 typedef，描述当 `multiset` 作为值时存储为元素的对象。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[begin](#begin)|返回一个迭代器，此迭代器指向 `multiset` 中的第一个元素。|  
|[cbegin](#cbegin)|返回一个常量迭代器，此迭代器用于发现 `multiset` 中的第一个元素。|  
|[cend](#cend)|返回一个常量迭代器，此迭代器用于发现 `multiset` 中最后一个元素之后的位置。|  
|[clear](#clear)|清除 `multiset` 的所有元素。|  
|[count](#count)|返回 `multiset` 中其键与指定为参数的键匹配的元素数量。|  
|[crbegin](#crbegin)|返回一个常量迭代器，此迭代器用于发现反向集中的第一个元素。|  
|[crend](#crend)|返回一个常量迭代器，此迭代器用于发现反向集中最后一个元素之后的位置。|  
|[emplace](#emplace)|将就地构造的元素插入到 `multiset`。|  
|[emplace_hint](#emplace_hint)|将就地构造的元素插入到 `multiset`，附带位置提示。|  
|[empty](#empty)|测试 `multiset` 是否为空。|  
|[end](#end)|返回一个迭代器，此迭代器指向 `multiset` 中最后一个元素之后的位置。|  
|[equal_range](#equal_range)|返回一对迭代器。 此迭代器对中的第一个迭代器指向 `multiset` 中其键大于指定键的第一个元素。 此迭代器对中的第二个迭代器指向 `multiset` 中其键等于或大于指定键的第一个元素。|  
|[erase](#erase)|从 `multiset` 中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。|  
|[find](#find)|返回一个迭代器，此迭代器指向 `multiset` 中其键与指定键相等的元素的第一个位置。|  
|[get_allocator](#get_allocator)|返回用于构造 `allocator` 的 `multiset` 对象的副本。|  
|[insert](#insert)|将一个元素或元素范围插入到 `multiset`。|  
|[key_comp](#key_comp)|提供一个函数对象，此函数对象可比较两个排序键以确定 `multiset` 中两个元素的相对顺序。|  
|[lower_bound](#lower_bound)|返回一个迭代器，此迭代器指向 `multiset` 中其键等于或大于指定键的第一个元素。|  
|[max_size](#max_size)|返回 `multiset` 的最大长度。|  
|[rbegin](#rbegin)|返回一个迭代器，此迭代器指向反向 `multiset` 中的第一个元素。|  
|[rend](#rend)|返回一个迭代器，此迭代器指向反向 `multiset` 中最后一个元素之后的位置。|  
|[size](#size)|返回 `multiset` 中的元素数量。|  
|[swap](#swap)|交换两个 `multiset` 的元素。|  
|[upper_bound](#upper_bound)|返回一个迭代器，此迭代器指向 `multiset` 中其键大于指定键的第一个元素。|  
|[value_comp](#value_comp)|检索用于对 `multiset` 中的元素值进行排序的比较对象副本。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator=](#op_eq)|将一个 `multiset` 中的元素替换为另一 `multiset` 副本。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<set>  
  
 **命名空间：** std  
  
##  <a name="allocator_type"></a>  multiset::allocator_type  
 一种类型，它代表多重集对象的分配器类  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>备注  
 `allocator_type` 是模板参数 `Allocator` 的同义词。  
  
 有关 `Allocator` 的详细信息，请参阅 [multiset 类](../standard-library/multiset-class.md)主题的备注部分。  
  
### <a name="example"></a>示例  
  有关使用 `allocator_type` 的示例，请参阅 [get_allocator](#get_allocator) 的示例  
  
##  <a name="begin"></a>  multiset::begin  
 返回发现多重集中第一个元素的位置的迭代器。  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>返回值  
 发现多重集中第一个元素或空多重集之后的位置的双向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_begin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter;  
   multiset <int>::const_iterator ms1_cIter;  
  
   ms1.insert( 1 );  
   ms1.insert( 2 );  
   ms1.insert( 3 );  
  
   ms1_Iter = ms1.begin( );  
   cout << "The first element of ms1 is " << *ms1_Iter << endl;  
  
   ms1_Iter = ms1.begin( );  
   ms1.erase( ms1_Iter );  
  
   // The following 2 lines would err as the iterator is const  
   // ms1_cIter = ms1.begin( );  
   // ms1.erase( ms1_cIter );  
  
   ms1_cIter = ms1.begin( );  
   cout << "The first element of ms1 is now " << *ms1_cIter << endl;  
}  
```  
  
```Output  
The first element of ms1 is 1  
The first element of ms1 is now 2  
```  
  
##  <a name="cbegin"></a>  multiset::cbegin  
 返回确定范围中第一个元素地址的 `const` 迭代器。  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 `const` 双向访问迭代器，指向范围的第一个元素，或刚超出空范围末尾的位置（对于空范围，`cbegin() == cend()`）。  
  
### <a name="remarks"></a>备注  
 由于使用 `cbegin` 的返回值，因此不能修改范围中的元素。  
  
 可以使用此成员函数替代 `begin()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在该示例中，将 `Container` 视为支持 `begin()` 和 `cbegin()` 的任何类型的可修改（非 `const`）的容器。  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>  multiset::cend  
 返回一个 `const` 迭代器，此迭代器用于发现刚超出范围中最后一个元素的位置。  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>返回值  
 指向刚超出范围末尾的位置的 `const` 双向访问迭代器。  
  
### <a name="remarks"></a>备注  
 `cend` 用于测试迭代器是否超过了其范围的末尾。  
  
 可以使用此成员函数替代 `end()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在此示例中，将 `Container` 视为支持 `end()` 和 `cend()` 的可修改的任何类型的（非- `const`）容器。  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 不应对 `cend` 返回的值取消引用。  
  
##  <a name="clear"></a>  multiset::clear  
 清除多重集的所有元素。  
  
```  
void clear();
```  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_clear.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
  
   ms1.insert( 1 );  
   ms1.insert( 2 );  
  
   cout << "The size of the multiset is initially "  
        << ms1.size( ) << "." << endl;  
  
   ms1.clear( );  
   cout << "The size of the multiset after clearing is "   
        << ms1.size( ) << "." << endl;  
}  
```  
  
```Output  
The size of the multiset is initially 2.  
The size of the multiset after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>  multiset::const_iterator  
 一种类型，提供可读取多重集中 **const** 元素的双向迭代器。  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `const_iterator` 类型不能用于修改元素的值。  
  
### <a name="example"></a>示例  
  有关使用 `const_iterator` 的示例，请参阅 [begin](#begin) 的示例。  
  
##  <a name="const_pointer"></a>  multiset::const_pointer  
 一种类型，它提供指向多重集中 **const** 元素的指针。  
  
```  
typedef typename allocator_type::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>备注  
 `const_pointer` 类型不能用于修改元素的值。  
  
 在大多数情况下，应使用 [iterator](#iterator) 访问多重集对象中的元素。  
  
##  <a name="const_reference"></a>  multiset::const_reference  
 一种类型，此类型提供对用于读取和执行 **const** 操作的多重集中存储的 **const** 元素的引用。  
  
```  
typedef typename allocator_type::const_reference const_reference;  
```  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_const_ref.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> ms1;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the 1st element  
   const int &Ref1 = *ms1.begin( );  
  
   cout << "The first element in the multiset is "  
        << Ref1 << "." << endl;  
  
   // The following line would cause an error because the   
   // const_reference cannot be used to modify the multiset  
   // Ref1 = Ref1 + 5;  
}  
```  
  
```Output  
The first element in the multiset is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>  multiset::const_reverse_iterator  
 一种类型，提供可读取多重集中任何 **const** 元素的双向迭代器。  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `const_reverse_iterator` 类型无法修改元素的值，它用于反向循环访问多重集。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `const_reverse_iterator` 的示例，请参阅 [rend](#rend) 的示例。  
  
##  <a name="count"></a>  multiset::count  
 返回 multiset 中其键与指定了参数的键匹配的元素数量。  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要从 multiset 中进行匹配的元素的键。  
  
### <a name="return-value"></a>返回值  
 multiset 中其排序键与参数键匹配的元素数量。  
  
### <a name="remarks"></a>备注  
 成员函数返回以下范围内的元素 *x* 的数量  
  
 [ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) )。  
  
### <a name="example"></a>示例  
  下面的示例演示 multiset::count 成员函数的用法。  
  
```  
// multiset_count.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    multiset<int> ms1;  
    multiset<int>::size_type i;  
  
    ms1.insert(1);  
    ms1.insert(1);  
    ms1.insert(2);  
  
    // Elements do not need to be unique in multiset,  
    // so duplicates are allowed and counted.  
    i = ms1.count(1);  
    cout << "The number of elements in ms1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = ms1.count(2);  
    cout << "The number of elements in ms1 with a sort key of 2 is: "  
         << i << "." << endl;  
  
    i = ms1.count(3);  
    cout << "The number of elements in ms1 with a sort key of 3 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in ms1 with a sort key of 1 is: 2.  
The number of elements in ms1 with a sort key of 2 is: 1.  
The number of elements in ms1 with a sort key of 3 is: 0.  
```  
  
##  <a name="crbegin"></a>  multiset::crbegin  
 返回一个常量迭代器，此迭代器用于发现反向多重集中的第一个元素。  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 一个发现反向多重集中的第一个元素或发现非反向多重集中的最后一个元素的的常量反向双向迭代器。  
  
### <a name="remarks"></a>备注  
 `crbegin` 用于反向多重集，正如 begin 用于多重集一样。  
  
 返回值为 `crbegin`时，无法修改多重集对象。  
  
 `crbegin` 可用于向后循环访问多重集。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_crbegin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::const_reverse_iterator ms1_crIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_crIter = ms1.crbegin( );  
   cout << "The first element in the reversed multiset is "  
        << *ms1_crIter << "." << endl;  
}  
```  
  
```Output  
The first element in the reversed multiset is 30.  
```  
  
##  <a name="crend"></a>  multiset::crend  
 返回一个常量迭代器，此迭代器用于发现反向多重集中最后一个元素之后的位置。  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>返回值  
 用于发现反向多重集中最后一个元素之后的位置（非反向多重集中第一个元素之前的位置）的常量反向双向迭代器。  
  
### <a name="remarks"></a>备注  
 `crend` 用于反向多重集，正如 [end](#end) 用于多重集一样。  
  
 返回值为 `crend` 时，无法修改多重集对象。  
  
 `crend` 可用于测试反向迭代器是否已到达其多重集末尾。  
  
 不应对 `crend` 返回的值取消引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_crend.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::const_reverse_iterator ms1_crIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_crIter = ms1.crend( ) ;  
   ms1_crIter--;  
   cout << "The last element in the reversed multiset is "  
        << *ms1_crIter << "." << endl;  
}  
```  
  
##  <a name="difference_type"></a>  multiset::difference_type  
 一种带符号整数类型，此类型可用于表示多重集中迭代器指向的元素间范围内的元素数量。  
  
```  
typedef typename allocator_type::difference_type difference_type;  
```  
  
### <a name="remarks"></a>备注  
 `difference_type` 是通过容器迭代器减少或递增时返回的类型。 `difference_type` 通常用于表示迭代器 `first` 和 `last` 之间的范围 [ `first`, `last`) 内元素的数目，包括 `first` 指向的元素以及那一系列元素，但不包括 `last` 指向的元素。  
  
 注意，尽管 `difference_type` 适用于满足输入迭代器（包括可逆容器支持的双向迭代器的类，如集）需求的所有迭代器，迭代器之间的减法仅受随机访问容器（如 vector）提供的随机访问迭代器支持。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <set>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
  
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter, ms1_bIter, ms1_eIter;  
  
   ms1.insert( 20 );  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
  
   ms1_bIter = ms1.begin( );  
   ms1_eIter = ms1.end( );  
  
   multiset <int>::difference_type   df_typ5, df_typ10, df_typ20;  
  
   df_typ5 = count( ms1_bIter, ms1_eIter, 5 );  
   df_typ10 = count( ms1_bIter, ms1_eIter, 10 );  
   df_typ20 = count( ms1_bIter, ms1_eIter, 20 );  
  
   // The keys, and hence the elements, of a multiset are not unique  
   cout << "The number '5' occurs " << df_typ5  
        << " times in multiset ms1.\n";  
   cout << "The number '10' occurs " << df_typ10  
        << " times in multiset ms1.\n";  
   cout << "The number '20' occurs " << df_typ20  
        << " times in multiset ms1.\n";  
  
   // Count the number of elements in a multiset   
   multiset <int>::difference_type  df_count = 0;  
   ms1_Iter = ms1.begin( );  
   while ( ms1_Iter != ms1_eIter)  
   {  
      df_count++;  
      ms1_Iter++;  
   }  
  
   cout << "The number of elements in the multiset ms1 is: "   
        << df_count << "." << endl;  
}  
```  
  
```Output  
The number '5' occurs 0 times in multiset ms1.  
The number '10' occurs 1 times in multiset ms1.  
The number '20' occurs 2 times in multiset ms1.  
The number of elements in the multiset ms1 is: 3.  
```  
  
##  <a name="emplace"></a>  multiset::emplace  
 使用位置提示就地插入构造的元素（不执行复制或移动操作）。  
  
```  
template <class... Args>  
iterator emplace(Args&&... args);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|`args`|用于构造要插入到多重集中的元素的转发参数。|  
  
### <a name="return-value"></a>返回值  
 指向新插入的元素的迭代器。  
  
### <a name="remarks"></a>备注  
 对容器元素的引用不会因为此函数而失效，但是它可能会使所有指向容器的迭代器都失效。  
  
 在定位过程中，如果引发异常，则不会修改该容器的状态。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_emplace.cpp  
// compile with: /EHsc  
#include <set>  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
template <typename S> void print(const S& s) {  
    cout << s.size() << " elements: ";  
  
    for (const auto& p : s) {  
        cout << "(" << p << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    multiset<string> s1;  
  
    s1.emplace("Anna");  
    s1.emplace("Bob");  
    s1.emplace("Carmine");  
  
    cout << "multiset modified, now contains ";  
    print(s1);  
    cout << endl;  
  
    s1.emplace("Bob");  
  
    cout << "multiset modified, now contains ";  
    print(s1);  
    cout << endl;  
}  
  
```  
  
##  <a name="emplace_hint"></a>  multiset::emplace_hint  
 使用位置提示就地插入构造的元素（不执行复制或移动操作）。  
  
```  
template <class... Args>  
iterator emplace_hint(
    const_iterator where,  
    Args&&... args);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|`args`|用于构造要插入到多重集中的元素的转发参数。|  
|`where`|开始搜索正确插入点的位置。 （如果该点紧贴在 `where` 之前，则插入可能发生在分期常量时间内而非对数时间内。)|  
  
### <a name="return-value"></a>返回值  
 指向新插入的元素的迭代器。  
  
### <a name="remarks"></a>备注  
 对容器元素的引用不会因为此函数而失效，但是它可能会使所有指向容器的迭代器都失效。  
  
 在定位过程中，如果引发异常，则不会修改该容器的状态。  
  
 有关代码示例，请参阅 [set::emplace_hint](../standard-library/set-class.md#emplace_hint)。  
  
##  <a name="empty"></a>  multiset::empty  
 测试多重集是否为空。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 如果多重集为空，则为 **true**；如果多重集不为空，则为 **false**。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_empty.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> ms1, ms2;  
   ms1.insert ( 1 );  
  
   if ( ms1.empty( ) )  
      cout << "The multiset ms1 is empty." << endl;  
   else  
      cout << "The multiset ms1 is not empty." << endl;  
  
   if ( ms2.empty( ) )  
      cout << "The multiset ms2 is empty." << endl;  
   else  
      cout << "The multiset ms2 is not empty." << endl;  
}  
```  
  
```Output  
The multiset ms1 is not empty.  
The multiset ms2 is empty.  
```  
  
##  <a name="end"></a>  multiset::end  
 返回超过末尾迭代器。  
  
```  
const_iterator end() const;

 
 
iterator end();
```  
  
### <a name="return-value"></a>返回值  
 超过末尾迭代器。 如果多重集为空，则 `multiset::end() == multiset::begin()`。  
  
### <a name="remarks"></a>备注  
 **end** 用于测试迭代器是否超过多重集的末尾。  
  
 不应对 **end** 返回的值取消引用。  
  
 有关代码示例，请参阅 [multiset::find](#find)。  
  
##  <a name="equal_range"></a>  multiset::equal_range  
 返回一对迭代器，这两个迭代器分别用于发现多重集中其键大于指定键的第一个元素，以及多重集中其键等于或大于指定键的第一个元素。  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的多重集中元素的排序键进行比较的参数键。  
  
### <a name="return-value"></a>返回值  
 一对迭代器，其中第一个是键的 [lower_bound](#lower_bound)，第二个是键的 [upper_bound](#upper_bound)。  
  
 若要访问成员函数返回的 `pr` 对的第一个迭代器，请使用 `pr`. **first**；若要取消引用下界迭代器，请使用 \*( `pr`. **first**)。 若要访问成员函数返回的 `pr` 对的第二个迭代器，请使用 `pr`. **second**；若要取消引用上界迭代器，请使用 \*( `pr`. **second**)。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_equal_range.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;      
   typedef multiset<int, less<int> > IntSet;  
   IntSet ms1;  
   multiset <int> :: const_iterator ms1_RcIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;  
   p1 = ms1.equal_range( 20 );  
  
   cout << "The upper bound of the element with "  
        << "a key of 20 in the multiset ms1 is: "  
        << *( p1.second ) << "." << endl;  
  
   cout << "The lower bound of the element with "  
        << "a key of 20 in the multiset ms1 is: "  
        << *( p1.first ) << "." << endl;  
  
   // Compare the upper_bound called directly   
   ms1_RcIter = ms1.upper_bound( 20 );  
   cout << "A direct call of upper_bound( 20 ) gives "  
        << *ms1_RcIter << "," << endl  
        << "matching the 2nd element of the pair"  
        << " returned by equal_range( 20 )." << endl;  
  
   p2 = ms1.equal_range( 40 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == ms1.end( ) ) && ( p2.second == ms1.end( ) ) )  
      cout << "The multiset ms1 doesn't have an element "  
              << "with a key less than 40." << endl;  
   else  
      cout << "The element of multiset ms1 with a key >= 40 is: "  
                << *( p1.first ) << "." << endl;  
}  
```  
  
```Output  
The upper bound of the element with a key of 20 in the multiset ms1 is: 30.  
The lower bound of the element with a key of 20 in the multiset ms1 is: 20.  
A direct call of upper_bound( 20 ) gives 30,  
matching the 2nd element of the pair returned by equal_range( 20 ).  
The multiset ms1 doesn't have an element with a key less than 40.  
```  
  
##  <a name="erase"></a>  multiset::erase  
 从多重集中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。  
  
```  
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,  
    const_iterator Last);

size_type erase(
    const key_type& Key);
```  
  
### <a name="parameters"></a>参数  
 `Where`  
 要移除的元素的位置。  
  
 `First`  
 要移除的第一个元素的位置。  
  
 `Last`  
 要移除的刚超出最后一个元素的位置。  
  
 `Key`  
 要移除的元素的关键值。  
  
### <a name="return-value"></a>返回值  
 对于前两个成员函数，则为双向迭代器，它指定已删除的任何元素之外留存的第一个元素，如果此类元素不存在，则为多重集末尾的元素。  
  
 对于第三个成员函数，则返回已从多重集中移除的元素的数目。  
  
### <a name="remarks"></a>备注  
 有关代码示例，请参阅 [set::erase](../standard-library/set-class.md#erase)。  
  
##  <a name="find"></a>  multiset::find  
 返回引用多重集当中具有与指定键等效的键的元素的位置的迭代器。  
  
```  
iterator find(const Key& key);

 
const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 与所搜索多重集中元素的排序键匹配的键值。  
  
### <a name="return-value"></a>返回值  
 引用具有指定键的元素的位置的迭代器，如果找不到该键的匹配项，则引用这个多重集中 (`multiset::end()`) 最后一个元素后面的位置。  
  
### <a name="remarks"></a>备注  
 成员函数返回引用多重集中其键与二元谓词下的参数 `key` 等效的元素的迭代器，该谓词基于小于比较关系进行顺序。  
  
 如果 **find** 的返回值赋予了 **const_iterator**，则无法修改多重集对象。 如果 **find** 的返回值赋予了 **iterator**，则可以修改多重集对象  
  
### <a name="example"></a>示例  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
#include <set>  
#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
template <typename T> void print_elem(const T& t) {  
    cout << "(" << t << ") ";  
}  
  
template <typename T> void print_collection(const T& t) {  
    cout << t.size() << " elements: ";  
  
    for (const auto& p : t) {  
        print_elem(p);  
    }  
    cout << endl;  
}  
  
template <typename C, class T> void findit(const C& c, T val) {  
    cout << "Trying find() on value " << val << endl;  
    auto result = c.find(val);  
    if (result != c.end()) {  
        cout << "Element found: "; print_elem(*result); cout << endl;  
    } else {  
        cout << "Element not found." << endl;  
    }  
}  
  
int main()  
{  
    multiset<int> s1({ 40, 45 });  
    cout << "The starting multiset s1 is: " << endl;  
    print_collection(s1);  
  
    vector<int> v;  
    v.push_back(43);  
    v.push_back(41);  
    v.push_back(46);  
    v.push_back(42);  
    v.push_back(44);  
    v.push_back(44); // attempt a duplicate  
  
    cout << "Inserting the following vector data into s1: " << endl;  
    print_collection(v);  
  
    s1.insert(v.begin(), v.end());  
  
    cout << "The modified multiset s1 is: " << endl;  
    print_collection(s1);  
    cout << endl;  
    findit(s1, 45);  
    findit(s1, 6);  
}  
```  
  
##  <a name="get_allocator"></a>  multiset::get_allocator  
 返回用于构造多重集的分配器对象的一个副本。  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>返回值  
 多重集使用的分配器。  
  
### <a name="remarks"></a>备注  
 多重集类的分配器指定类管理存储的方式。 C++ 标准库容器类提供的默认分配器足以满足大多编程需求。 编写和使用你自己的分配器类是高级 C++ 主题。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_get_allocator.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int>::allocator_type ms1_Alloc;  
   multiset <int>::allocator_type ms2_Alloc;  
   multiset <double>::allocator_type ms3_Alloc;  
   multiset <int>::allocator_type ms4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   multiset <int> ms1;  
   multiset <int, allocator<int> > ms2;  
   multiset <double, allocator<double> > ms3;  
  
   cout << "The number of integers that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << ms2.max_size( ) << "." << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << ms3.max_size( ) <<  "." << endl;  
  
   // The following lines create a multiset ms4  
   // with the allocator of multiset ms1  
   ms1_Alloc = ms1.get_allocator( );  
   multiset <int> ms4( less<int>( ), ms1_Alloc );  
   ms4_Alloc = ms4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated with the other  
   if( ms1_Alloc == ms4_Alloc )     
   {  
      cout << "Allocators are interchangeable."  
           << endl;     
   }  
   else     
   {  
      cout << "Allocators are not interchangeable."  
           << endl;     
   }  
}  
```  
  
##  <a name="insert"></a>  multiset::insert  
 将一个元素或元素范围插入到多重集合中。  
  
```  
// (1) single element  
pair<iterator, bool> insert(
    const value_type& Val);

 
// (2) single element, perfect forwarded  
template <class ValTy>  
pair<iterator, bool>  
insert(
    ValTy&& Val);

 
// (3) single element with hint  
iterator insert(
    const_iterator Where,  
    const value_type& Val);

 
// (4) single element, perfect forwarded, with hint  
template <class ValTy>  
iterator insert(
    const_iterator Where,  
    ValTy&& Val);

 
// (5) range   
template <class InputIterator>   
void insert(
    InputIterator First,  
    InputIterator Last);

 
// (6) initializer list  
void insert(
    initializer_list<value_type>  
IList);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`Val`|要插入到多重集合中的元素的值。|  
|`Where`|开始搜索正确插入点的位置。 （如果该点紧贴在 `Where` 之前，则插入可能发生在分期常量时间内而非对数时间内。)|  
|`ValTy`|指定多重集合可用于构造 [value_type](../standard-library/map-class.md#value_type) 元素的自变量类型并将 `Val` 作为自变量完美转发的模板参数。|  
|`First`|要复制的第一个元素的位置。|  
|`Last`|要复制的最后一个元素以外的位置。|  
|`InputIterator`|满足[输入迭代器](../standard-library/input-iterator-tag-struct.md)需求的模板函数自变量，该输入迭代器指向可用于构造 [value_type](../standard-library/map-class.md#value_type) 对象的类型的元素。|  
|`IList`|从中复制元素的 [initializer_list](../standard-library/initializer-list.md)。|  
  
### <a name="return-value"></a>返回值  
 单个元素插入的成员函数 (1) 和 (2) 返回迭代器，该迭代器指向将新元素插入到多重集合中的位置。  
  
 附带提示的单个元素的成员函数 (3) 和 (4) 返回迭代器，该迭代器指向将新元素插入到多重集合中的位置。  
  
### <a name="remarks"></a>备注  
 指针或引用不会因为此函数而失效，但是它可能会使所有指向容器的迭代器都失效。  
  
 在插入单个元素的过程中，如果引发异常，则不会修改该容器的状态。 在插入多个元素的过程中，如果引发异常，则会使容器处于未指定但有效的状态。  
  
 容器的 [value_type](../standard-library/map-class.md#value_type) 是属于该容器的 typedef；对于集，`multiset<V>::value_type` 是 `const V` 类型。  
  
 范围成员函数 (5) 将元素值序列插入到多重集合中，它对应于迭代器在范围 `[First, Last)` 中所处理的每一个元素；因此，不会插入 `Last`。 容器成员函数 `end()` 是指容器中最后一个元素之后的位置，例如，`s.insert(v.begin(), v.end());` 语句会将 `v` 的所有元素插入到 `s` 中。  
  
 初始值设定项列表成员函数 (6) 使用 [initializer_list](../standard-library/initializer-list.md) 将元素复制到多重集合中。  
  
 有关就地构造的元素的插入（即不会执行复制或移动操作），请参阅 [multiset::emplace](#emplace) 和 [multiset::emplace_hint](#emplace_hint)。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_insert.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
#include <string>  
#include <vector>  
  
using namespace std;  
  
template <typename S> void print(const S& s) {  
    cout << s.size() << " elements: ";  
  
    for (const auto& p : s) {  
        cout << "(" << p << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
  
    // insert single values   
    multiset<int> s1;  
    // call insert(const value_type&) version  
    s1.insert({ 1, 10 });  
    // call insert(ValTy&&) version   
    s1.insert(20);  
  
    cout << "The original multiset values of s1 are:" << endl;  
    print(s1);  
  
    // intentionally attempt a duplicate, single element  
    s1.insert(1);  
    cout << "The modified multiset values of s1 are:" << endl;  
    print(s1);  
    cout << endl;  
  
    // single element, with hint  
    s1.insert(s1.end(), 30);  
    cout << "The modified multiset values of s1 are:" << endl;  
    print(s1);  
    cout << endl;  
  
    // The templatized version inserting a jumbled range  
    multiset<int> s2;  
    vector<int> v;  
    v.push_back(43);  
    v.push_back(294);  
    v.push_back(41);  
    v.push_back(330);  
    v.push_back(42);  
    v.push_back(45);  
  
    cout << "Inserting the following vector data into s2:" << endl;  
    print(v);  
  
    s2.insert(v.begin(), v.end());  
  
    cout << "The modified multiset values of s2 are:" << endl;  
    print(s2);  
    cout << endl;  
  
    // The templatized versions move-constructing elements  
    multiset<string>  s3;  
    string str1("blue"), str2("green");  
  
    // single element  
    s3.insert(move(str1));  
    cout << "After the first move insertion, s3 contains:" << endl;  
    print(s3);  
  
    // single element with hint  
    s3.insert(s3.end(), move(str2));  
    cout << "After the second move insertion, s3 contains:" << endl;  
    print(s3);  
    cout << endl;  
  
    multiset<int> s4;  
    // Insert the elements from an initializer_list  
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });  
    cout << "After initializer_list insertion, s4 contains:" << endl;  
    print(s4);  
    cout << endl;  
}  
  
```  
  
##  <a name="iterator"></a>  multiset::iterator  
 提供可读取多组中的任何元素的常量[双向迭代器](../standard-library/bidirectional-iterator-tag-struct.md)的类型。  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="example"></a>示例  
  有关如何声明和使用 **iterator** 的示例，请参阅 [begin](#begin) 的示例。  
  
##  <a name="key_comp"></a>  multiset::key_comp  
 检索用于对多重集中的键进行排序的比较对象副本。  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>返回值  
 返回多重集用来对其元素进行排序的函数对象，即模板参数 `Compare`。  
  
 有关 `Compare` 的详细信息，请参阅 [multiset 类](../standard-library/multiset-class.md)主题的备注部分。  
  
### <a name="remarks"></a>备注  
 存储对象用于定义以下成员函数：  
  
 **bool operator**( **const Key&** *x*, **const Key&** *y*);  
  
 如果在排序顺序中 *x* 严格位于 *y* 之前，则返回 true。  
  
 请注意，[key_compare](#key_compare) 和 [value_compare](#value_compare) 皆是模板参数 `Compare` 的同义词。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_key_comp.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   multiset <int, less<int> > ms1;  
   multiset <int, less<int> >::key_compare kc1 = ms1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )     
   {  
      cout << "kc1( 2,3 ) returns value of true, "  
           << "where kc1 is the function object of s1."  
           << endl;  
   }  
   else     
   {  
      cout << "kc1( 2,3 ) returns value of false "  
           << "where kc1 is the function object of ms1."  
           << endl;  
   }  
  
   multiset <int, greater<int> > ms2;  
   multiset <int, greater<int> >::key_compare kc2 = ms2.key_comp( ) ;  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )     
   {  
      cout << "kc2( 2,3 ) returns value of true, "  
           << "where kc2 is the function object of ms2."  
           << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false, "  
           << "where kc2 is the function object of ms2."  
           << endl;  
   }  
}  
```  
  
```Output  
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.  
kc2( 2,3 ) returns value of false, where kc2 is the function object of ms2.  
```  
  
##  <a name="key_compare"></a>  multiset::key_compare  
 一种提供函数对象的类型，该函数对象可比较两个排序键以确定多重集中两个元素的相对顺序。  
  
```  
typedef Compare key_compare;  
```  
  
### <a name="remarks"></a>备注  
 **key_compare** 是模板参数 `Compare` 的同义词。  
  
 有关 `Compare` 的详细信息，请参阅 [multiset 类](../standard-library/multiset-class.md)主题的备注部分。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `key_compare` 的示例，请参阅 [key_comp](#key_comp) 的示例。  
  
##  <a name="key_type"></a>  multiset::key_type  
 一种提供函数对象的类型，该函数对象可比较排序键以确定多重集中两个元素的相对顺序。  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>备注  
 `key_type` 是模板参数 `Key` 的同义词。  
  
 有关 `Key` 的详细信息，请参阅 [multiset 类](../standard-library/multiset-class.md)主题的备注部分。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `key_type` 的示例，请参阅 [value_type](#value_type) 的示例。  
  
##  <a name="lower_bound"></a>  multiset::lower_bound  
 返回一个迭代器，此迭代器指向多重集中其键等于或大于指定键的第一个元素。  
  
```  
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的多重集中元素的排序键进行比较的参数键。  
  
### <a name="return-value"></a>返回值  
 一个**迭代器**或 `const_iterator`，它会发现多重集中其键等于或大于参数键的元素的位置，或如果未找到键的匹配项，则发现多重集中最后一个元素之后的位置。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_lower_bound.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_RcIter = ms1.lower_bound( 20 );  
   cout << "The element of multiset ms1 with a key of 20 is: "  
        << *ms1_RcIter << "." << endl;  
  
   ms1_RcIter = ms1.lower_bound( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( ms1_RcIter == ms1.end( ) )  
      cout << "The multiset ms1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of multiset ms1 with a key of 40 is: "  
           << *ms1_RcIter << "." << endl;  
  
   // The element at a specific location in the multiset can be   
   // found using a derefenced iterator addressing the location  
   ms1_AcIter = ms1.end( );  
   ms1_AcIter--;  
   ms1_RcIter = ms1.lower_bound( *ms1_AcIter );  
   cout << "The element of ms1 with a key matching "  
        << "that of the last element is: "  
        << *ms1_RcIter << "." << endl;  
}  
```  
  
```Output  
The element of multiset ms1 with a key of 20 is: 20.  
The multiset ms1 doesn't have an element with a key of 40.  
The element of ms1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="max_size"></a>  multiset::max_size  
 返回多重集的最大长度。  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>返回值  
 多重集的最大可取长度。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_max_size.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::size_type i;  
  
   i = ms1.max_size( );     
   cout << "The maximum possible length "  
        << "of the multiset is " << i << "." << endl;  
}  
```  
  
##  <a name="multiset"></a>  multiset::multiset  
 构造一个空的或者是其他某个多重集的全部或部分副本的多重集。  
  
```  
multiset();

explicit multiset (
    const Compare& Comp);

multiset (
    const Compare& Comp,  
    const Allocator& Al);

multiset(
    const multiset& Right);

multiset(
    multiset&& Right);

multiset(
    initializer_list<Type> IList);

multiset(
    initializer_list<Type> IList,   
    const Compare& Comp);

multiset(
    initializer_list<Type> IList,   
    const Compare& Comp,   
    const Allocator& Al);

 
template <class InputIterator>  
multiset (
    InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
multiset (
    InputIterator First,  
    InputIterator Last,  
    const Compare& Comp);

template <class InputIterator>  
multiset (
    InputIterator First,  
    InputIterator Last,  
    const Compare& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|`Al`|要用于此多重集对象的存储分配器类，默认为 `Allocator`。|  
|`Comp`|用于对多重集中元素排序的 `const Compare` 类型比较函数，默认为 `Compare`。|  
|`Right`|所构造多重集要作为副本的多重集。|  
|`First`|要复制的范围元素中的第一个元素的位置。|  
|`Last`|要复制的元素范围以外的第一个元素的位置。|  
|`IList`|从中复制元素的 initializer_list。|  
  
### <a name="remarks"></a>备注  
 所有构造函数存储一种类型的分配器对象，此类对象管理多重集的内存存储，且事后可通过调用 [get_allocator](#get_allocator) 返回。 此分配器参数在类声明中常省略，并预处理用于代替备用分配器的宏。  
  
 所有构造函数对它们的多重集进行初始化。  
  
 所有构造函数会存储类型为 Compare 的函数对象，此对象用于在多重集的键之间建立顺序，且事后可通过调用 [key_comp](#key_comp) 返回。  
  
 前三个构造函数均指定空的起始多重集，此外，第二个函数还指定用于建立元素顺序的比较函数 (`Comp`) 的类型，第三个函数还显式指定了要使用的分配器类型 (`Al`)。 关键字 `explicit` 取消了某些种类的自动类型转换。  
  
 第四个构造函数指定多重集 `Right` 的副本。  
  
 第五个构造函数通过移动 `Right` 指定多重集的副本。  
  
 第六个、第七个和第八个构造函数指定要从中复制元素的 initializer_list。  
  
 接下来的三个构造函数复制多重集的范围 `[First, Last)`，在指定比较函数类型和分配器时更加明确。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_ctor.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    //multiset <int>::iterator ms1_Iter, ms2_Iter, ms3_Iter;  
    multiset <int>::iterator ms4_Iter, ms5_Iter, ms6_Iter, ms7_Iter;  
  
    // Create an empty multiset ms0 of key type integer  
    multiset <int> ms0;  
  
    // Create an empty multiset ms1 with the key comparison  
    // function of less than, then insert 4 elements  
    multiset <int, less<int> > ms1;  
    ms1.insert(10);  
    ms1.insert(20);  
    ms1.insert(20);  
    ms1.insert(40);  
  
    // Create an empty multiset ms2 with the key comparison  
    // function of geater than, then insert 2 elements  
    multiset <int, less<int> > ms2;  
    ms2.insert(10);  
    ms2.insert(20);  
  
    // Create a multiset ms3 with the   
    // allocator of multiset ms1  
    multiset <int>::allocator_type ms1_Alloc;  
    ms1_Alloc = ms1.get_allocator();  
    multiset <int> ms3(less<int>(), ms1_Alloc);  
    ms3.insert(30);  
  
    // Create a copy, multiset ms4, of multiset ms1  
    multiset <int> ms4(ms1);  
  
    // Create a multiset ms5 by copying the range ms1[ first,  last)  
    multiset <int>::const_iterator ms1_bcIter, ms1_ecIter;  
    ms1_bcIter = ms1.begin();  
    ms1_ecIter = ms1.begin();  
    ms1_ecIter++;  
    ms1_ecIter++;  
    multiset <int> ms5(ms1_bcIter, ms1_ecIter);  
  
    // Create a multiset ms6 by copying the range ms4[ first,  last)  
    // and with the allocator of multiset ms2  
    multiset <int>::allocator_type ms2_Alloc;  
    ms2_Alloc = ms2.get_allocator();  
    multiset <int> ms6(ms4.begin(), ++ms4.begin(), less<int>(), ms2_Alloc);  
  
    cout << "ms1 =";  
    for (auto i : ms1)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "ms2 =";  
    for (auto i : ms2)  
        cout << " " << i;  
   cout << endl;  
  
   cout << "ms3 =";  
   for (auto i : ms3)  
       cout << " " << i;  
    cout << endl;  
  
    cout << "ms4 =";  
    for (auto i : ms4)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "ms5 =";  
    for (auto i : ms5)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "ms6 =";  
    for (auto i : ms6)  
        cout << " " << i;  
    cout << endl;  
  
    // Create a multiset by moving ms5  
    multiset<int> ms7(move(ms5));  
    cout << "ms7 =";  
    for (auto i : ms7)  
        cout << " " << i;  
    cout << endl;  
  
    // Create a multiset with an initializer_list  
    multiset<int> ms8({1, 2, 3, 4});  
    cout << "ms8=";  
    for (auto i : ms8)  
        cout << " " << i;  
    cout << endl;  
}  
```  
  
##  <a name="op_eq"></a>  multiset::operator=  
 使用另一个 `multiset` 的元素替换该 `multiset` 的元素。  
  
```  
multiset& operator=(const multiset& right);

multiset& operator=(multiset&& right);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`right`|从中复制或移动元素的 `multiset`。|  
  
### <a name="remarks"></a>备注  
 `operator=` 会将 `right` 中的元素复制或移动到此 `multiset`，具体取决于使用的引用类型（左值或右值）。 放弃 `operator=` executes 之前此 `multiset` 中的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_operator_as.cpp  
// compile with: /EHsc  
#include <multiset>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   multiset<int> v1, v2, v3;  
   multiset<int>::iterator iter;  
  
   v1.insert(10);  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
   }  
```  
  
##  <a name="pointer"></a>  multiset::pointer  
 一种类型，此类型提供指向多重集中元素的指针。  
  
```  
typedef typename allocator_type::pointer pointer;  
```  
  
### <a name="remarks"></a>备注  
 **pointer** 类型可用于修改元素的值。  
  
 在大多数情况下，应使用 [iterator](#iterator) 访问多重集对象中的元素。  
  
##  <a name="rbegin"></a>  multiset::rbegin  
 返回一个迭代器，此迭代器用于发现反向多重集中的第一个元素。  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>返回值  
 一个发现反向多重集中的第一个元素或发现非反向多重集中的最后一个元素的的反向双向迭代器。  
  
### <a name="remarks"></a>备注  
 `rbegin` 用于反向多重集，正如 rbegin 用于多重集。  
  
 如果将 `rbegin` 的返回值分配给 `const_reverse_iterator`，则无法修改多重集对象。 如果将 `rbegin` 的返回值分配给 `reverse_iterator`，则可修改多重集对象。  
  
 `rbegin` 可用于向后循环访问多重集。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_rbegin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter;  
   multiset <int>::reverse_iterator ms1_rIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_rIter = ms1.rbegin( );  
   cout << "The first element in the reversed multiset is "  
        << *ms1_rIter << "." << endl;  
  
   // begin can be used to start an interation   
   // throught a multiset in a forward order  
   cout << "The multiset is:";  
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout << endl;  
  
   // rbegin can be used to start an interation   
   // throught a multiset in a reverse order  
   cout << "The reversed multiset is:";  
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )  
      cout << " " << *ms1_rIter;  
   cout << endl;  
  
   // A multiset element can be erased by dereferencing to its key   
   ms1_rIter = ms1.rbegin( );  
   ms1.erase ( *ms1_rIter );  
  
   ms1_rIter = ms1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed multiset is "<< *ms1_rIter << "."   
        << endl;  
}  
```  
  
```Output  
The first element in the reversed multiset is 30.  
The multiset is: 10 20 30  
The reversed multiset is: 30 20 10  
After the erasure, the first element in the reversed multiset is 20.  
```  
  
##  <a name="reference"></a>  multiset::reference  
 一种类型，此类型提供对存储在多重集中的元素的引用。  
  
```  
typedef typename allocator_type::reference reference;  
```  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_ref.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
  
   // Declare and initialize a reference &Ref1 to the 1st element  
   const int &Ref1 = *ms1.begin( );  
  
   cout << "The first element in the multiset is "  
        << Ref1 << "." << endl;  
}  
```  
  
```Output  
The first element in the multiset is 10.  
```  
  
##  <a name="rend"></a>  multiset::rend  
 返回一个迭代器，此迭代器用于发现反向多重集中最后一个元素之后的位置。  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>返回值  
 用于发现反向多重集中最后一个元素之后的位置（非反向多重集中第一个元素之前的位置）的反向双向迭代器。  
  
### <a name="remarks"></a>备注  
 `rend` 用于反向多重集，正如 [end](#end) 用于多重集一样。  
  
 如果将 `rend` 的返回值赋予 `const_reverse_iterator`，则无法修改多重集对象。 如果将 `rend` 的返回值赋予 `reverse_iterator`，则可修改多重集对象。  
  
 `rend` 可用于测试反向迭代器是否已到达其多重集末尾。  
  
 不应对 `rend` 返回的值取消引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_rend.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter;  
   multiset <int>::reverse_iterator ms1_rIter;  
   multiset <int>::const_reverse_iterator ms1_crIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_rIter = ms1.rend( ) ;  
   ms1_rIter--;  
   cout << "The last element in the reversed multiset is "  
        << *ms1_rIter << "." << endl;  
  
   // end can be used to terminate an interation   
   // throught a multiset in a forward order  
   cout << "The multiset is: ";  
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << *ms1_Iter << " ";  
   cout << "." << endl;  
  
   // rend can be used to terminate an interation   
   // throught a multiset in a reverse order  
   cout << "The reversed multiset is: ";  
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )  
      cout << *ms1_rIter << " ";  
   cout << "." << endl;  
  
   ms1_rIter = ms1.rend( );  
   ms1_rIter--;  
   ms1.erase ( *ms1_rIter );  
  
   ms1_rIter = ms1.rend( );  
   --ms1_rIter;  
   cout << "After the erasure, the last element in the "  
        << "reversed multiset is " << *ms1_rIter << "." << endl;  
}  
```  
  
##  <a name="reverse_iterator"></a>  multiset::reverse_iterator  
 一种类型，此类型提供可读取或修改反向多重集中的元素的双向迭代器。  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `reverse_iterator` 类型用于反向循环访问多重集。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `reverse_iterator` 的示例，请参阅 [rbegin](#rbegin) 的示例。  
  
##  <a name="size"></a>  multiset::size  
 返回多重集中的元素数量。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 多重集的当前长度。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_size.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int> :: size_type i;  
  
   ms1.insert( 1 );  
   i = ms1.size( );  
   cout << "The multiset length is " << i << "." << endl;  
  
   ms1.insert( 2 );  
   i = ms1.size( );  
   cout << "The multiset length is now " << i << "." << endl;  
}  
```  
  
```Output  
The multiset length is 1.  
The multiset length is now 2.  
```  
  
##  <a name="size_type"></a>  multiset::size_type  
 一种无符号整数类型，此类型可表示多重集中的元素数量。  
  
```  
typedef typename allocator_type::size_type size_type;  
```  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `size_type` 的示例，请参阅 [size](#size) 的示例  
  
##  <a name="swap"></a>  multiset::swap  
 交换两个多重集的元素。  
  
```  
void swap(
    multiset<Key, Compare, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 参数多重集提供与目标多重集进行交换的元素。  
  
### <a name="remarks"></a>备注  
 成员函数不会使在彼此交换元素的两个多重集中指定元素的任何引用、指针或迭代器无效。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_swap.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> ms1, ms2, ms3;  
   multiset <int>::iterator ms1_Iter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
   ms2.insert( 100 );  
   ms2.insert( 200 );  
   ms3.insert( 300 );  
  
   cout << "The original multiset ms1 is:";  
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout << "." << endl;  
  
   // This is the member function version of swap  
   ms1.swap( ms2 );  
  
   cout << "After swapping with ms2, list ms1 is:";  
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( ms1, ms3 );  
  
   cout << "After swapping with ms3, list ms1 is:";  
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original multiset ms1 is: 10 20 30.  
After swapping with ms2, list ms1 is: 100 200.  
After swapping with ms3, list ms1 is: 300.  
```  
  
##  <a name="upper_bound"></a>  multiset::upper_bound  
 返回一个迭代器，此迭代器指向多重集中其键大于指定键的第一个元素。  
  
```  
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的多重集中元素的排序键进行比较的参数键。  
  
### <a name="return-value"></a>返回值  
 一个**迭代器**或 `const_iterator`，它会发现多重集中其键大于参数键的元素的位置，或如果未找到键的匹配项，则发现多重集中最后一个元素之后的位置。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_upper_bound.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_RcIter = ms1.upper_bound( 20 );  
   cout << "The first element of multiset ms1 with a key greater "  
           << "than 20 is: " << *ms1_RcIter << "." << endl;  
  
   ms1_RcIter = ms1.upper_bound( 30 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( ms1_RcIter == ms1.end( ) )  
      cout << "The multiset ms1 doesn't have an element "  
              << "with a key greater than 30." << endl;  
   else  
      cout << "The element of multiset ms1 with a key > 40 is: "  
           << *ms1_RcIter << "." << endl;  
  
   // The element at a specific location in the multiset can be   
   // found using a dereferenced iterator addressing the location  
   ms1_AcIter = ms1.begin( );  
   ms1_RcIter = ms1.upper_bound( *ms1_AcIter );  
   cout << "The first element of ms1 with a key greater than"  
        << endl << "that of the initial element of ms1 is: "  
        << *ms1_RcIter << "." << endl;  
}  
```  
  
```Output  
The first element of multiset ms1 with a key greater than 20 is: 30.  
The multiset ms1 doesn't have an element with a key greater than 30.  
The first element of ms1 with a key greater than  
that of the initial element of ms1 is: 20.  
```  
  
##  <a name="value_comp"></a>  multiset::value_comp  
 检索用于对多重集中的元素值进行排序的比较对象副本。  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>返回值  
 返回多重集用来对其元素进行排序的函数对象，即模板参数 `Compare`。  
  
 有关 `Compare` 的详细信息，请参阅 [multiset 类](../standard-library/multiset-class.md)主题的备注部分。  
  
### <a name="remarks"></a>备注  
 存储对象用于定义以下成员函数：  
  
 **bool operator**( **const Key&**`_xVal`, **const Key&**`_yVal`);  
  
 如果 `_xVal` 在排序顺序中先于且不等于 `_yVal`，则该函数会返回 true。  
  
 请注意，[key_compare](#key_compare) 和 [value_compare](#value_compare) 皆是模板参数 `Compare` 的同义词。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_value_comp.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   multiset <int, less<int> > ms1;  
   multiset <int, less<int> >::value_compare vc1 = ms1.value_comp( );  
   bool result1 = vc1( 2, 3 );  
   if( result1 == true )     
   {  
      cout << "vc1( 2,3 ) returns value of true, "  
           << "where vc1 is the function object of ms1."  
           << endl;  
   }  
   else     
   {  
      cout << "vc1( 2,3 ) returns value of false, "  
           << "where vc1 is the function object of ms1."  
           << endl;  
   }  
  
   set <int, greater<int> > ms2;  
   set<int, greater<int> >::value_compare vc2 = ms2.value_comp( );  
   bool result2 = vc2( 2, 3 );  
   if( result2 == true )     
   {  
      cout << "vc2( 2,3 ) returns value of true, "  
           << "where vc2 is the function object of ms2."  
           << endl;  
   }  
   else     
   {  
      cout << "vc2( 2,3 ) returns value of false, "  
           << "where vc2 is the function object of ms2."  
           << endl;  
   }  
}  
```  
  
```Output  
vc1( 2,3 ) returns value of true, where vc1 is the function object of ms1.  
vc2( 2,3 ) returns value of false, where vc2 is the function object of ms2.  
```  
  
##  <a name="value_compare"></a>  multiset::value_compare  
 一种提供函数对象的类型，该函数对象可比较两个排序键以确定它们在多重集中的相对顺序。  
  
```  
typedef key_compare value_compare;  
```  
  
### <a name="remarks"></a>备注  
 `value_compare` 是模板参数 `Compare` 的同义词。  
  
 请注意，[key_compare](#key_compare) 和 **value_compare** 皆是模板参数 `Compare` 的同义词。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。  
  
 有关 `Compare` 的详细信息，请参阅 [multiset 类](../standard-library/multiset-class.md)主题的备注部分。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `value_compare` 的示例，请参阅 [value_comp](#value_comp) 的示例。  
  
##  <a name="value_type"></a>  multiset::value_type  
 一种类型，此类型将在其容量中存储为多重集元素的对象描述为值。  
  
```  
typedef Key value_type;  
```  
  
### <a name="remarks"></a>备注  
 `value_type` 是模板参数 `Key` 的同义词。  
  
 请注意，[key_type](#key_type) 和 `value_type` 皆是模板参数 **Key** 的同义词。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。  
  
 有关 `Key` 的详细信息，请参阅该主题的备注部分。  
  
### <a name="example"></a>示例  
  
```cpp  
// multiset_value_type.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter;  
  
   multiset <int> :: value_type svt_Int;   // Declare value_type  
   svt_Int = 10;             // Initialize value_type  
  
   multiset <int> :: key_type skt_Int;   // Declare key_type  
   skt_Int = 20;             // Initialize key_type  
  
   ms1.insert( svt_Int );         // Insert value into s1  
   ms1.insert( skt_Int );         // Insert key into s1  
  
   // A multiset accepts key_types or value_types as elements  
   cout << "The multiset has elements:";  
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout << "." << endl;  
}  
```  
  
```Output  
The multiset has elements: 10 20.  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<set> 成员](http://msdn.microsoft.com/en-us/0c2d57c0-173f-4204-b579-c5f06aad8b95)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)


