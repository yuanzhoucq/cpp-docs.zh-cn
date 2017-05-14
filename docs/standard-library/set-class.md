---
title: "set 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- set
- set/std::set
- set/std::set::allocator_type
- set/std::set::const_iterator
- set/std::set::const_pointer
- set/std::set::const_reference
- set/std::set::const_reverse_iterator
- set/std::set::difference_type
- set/std::set::iterator
- set/std::set::key_compare
- set/std::set::key_type
- set/std::set::pointer
- set/std::set::reference
- set/std::set::reverse_iterator
- set/std::set::size_type
- set/std::set::value_compare
- set/std::set::value_type
- set/std::set::begin
- set/std::set::cbegin
- set/std::set::cend
- set/std::set::clear
- set/std::set::count
- set/std::set::crbegin
- set/std::set::crend
- set/std::set::emplace
- set/std::set::emplace_hint
- set/std::set::empty
- set/std::set::end
- set/std::set::equal_range
- set/std::set::erase
- set/std::set::find
- set/std::set::get_allocator
- set/std::set::insert
- set/std::set::key_comp
- set/std::set::lower_bound
- set/std::set::max_size
- set/std::set::rbegin
- set/std::set::rend
- set/std::set::size
- set/std::set::swap
- set/std::set::upper_bound
- set/std::set::value_comp
dev_langs:
- C++
helpviewer_keywords:
- set class
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
caps.latest.revision: 22
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
ms.openlocfilehash: 43eeea7d80f332e180342bd18460f1750c1b4b44
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="set-class"></a>set 类
C++ 标准库容器类集用于存储和检索集合中的数据，此集合中包含的元素值是唯一的，并且用作数据自动排序所依据的键值。 不能直接更改集中元素的值。 必须先删除旧值，才能插入具有新值的元素。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Key,   
    class Traits=less<Key>,   
    class Allocator=allocator<Key>>  
class set  
```  
  
#### <a name="parameters"></a>参数  
 `Key`  
 要存储在集中的元素数据类型。  
  
 `Traits`  
 一种提供函数对象的类型，该函数对象将两个元素值作为排序键进行比较，以确定其在集中的相对顺序。 此参数是可选自变量，默认值为二元谓词 **less***\<Key>*。  
  
 在 C++ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。 有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 一种表示存储的分配器对象的类型，该分配器对象封装有关集的内存分配和解除分配的详细信息。 此自变量是可选自变量，且默认值为 **allocator***\<Key>。*  
  
## <a name="remarks"></a>备注  
 C++ 标准库集是：  
  
-   大小可变的关联容器，支持基于关联键值高效检索元素值。 此外，它是简单的关联容器，因为它的元素值即为它的键值。  
  
-   可逆，因为它提供双向迭代器来访问其元素。  
  
-   有序，因为它的元素在容器中根据指定的比较函数按键值排序。  
  
-   唯一，每个元素必须具有唯一键。 集还是简单关联容器，因此它的元素也是唯一的。  
  
 集还被描述为模板类，因为它提供的功能是一般性的功能，因此与作为元素包含的特定数据类型无关。 可使用的数据类型作为类模板以及比较函数和分配器中的参数指定。  
  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。 关联容器针对查找、插入和移除操作进行了优化。 显式支持这些操作的成员函数较为高效，执行这些操作的时间与容器中元素数量的对数平均成比例。 插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。  
  
 当应用程序满足将值与其键关联的条件时，应选择集作为关联容器。 集的元素是唯一的，并用作其自己的排序键。 此类结构的模型是排序列表，如关键字排序列表，其中关键字只能出现一次。 如果允许关键字多次出现，则应使用多重集合作为适当的容器结构。 如果需要将值附加到唯一关键字的列表，则映射应为包含此数据的适当结构。 如果键不唯一，则应选择多重映射作为容器。  
  
 集通过调用存储的 [key_compare](#key_compare) 类型的函数对象，对它控制的序列进行排序。 此存储对象是比较函数，可通过调用成员函数 [key_comp](#key_comp) 进行访问。 通常，元素仅需小于比较元素即可建立此顺序，因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。 二元谓词 *f*( *x,y*) 是包含两个参数对象（*x* 和 *y*）以及一个返回值（**true** 或 **false**）的函数对象。 如果二元谓词具有自反性、反对称性和传递性且等效可传递，对集进行的排序将为严格弱排序，其中两个对象 *x* 和 *y* 定义为在 *f*(*x,y*) 和 *f*(*y,x*) 均为 false 时等效。 如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。  
  
 在 C++ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。 有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)  
  
 集类提供的迭代器是双向迭代器，但类成员函数 [insert](#insert) 和 [set](#set) 具有将较弱输入迭代器作为模板参数的版本，较弱输入迭代器的功能需求比双向迭代器类保证的功能需求更少。 不同的迭代器概念形成一个系列，通过它们的功能优化相关联。 每个迭代器概念有它自己的一套要求，使用这些概念的算法必须根据迭代器类型提供的要求限制它们的假设。 可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。 这是最小的功能集，但足以按有意义的方式提供类成员函数的上下文中的迭代器范围 [`First`, `Last`)。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[set](#set)|构造一个空的或者是其他某个集的全部或部分副本的集。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|一种类型，此类型表示集对象的 `allocator` 类。|  
|[const_iterator](#const_iterator)|一种类型，此类型提供可读取集中的 `const` 元素的双向迭代器。|  
|[const_pointer](#const_pointer)|一种类型，此类型提供指向集中的 `const` 元素的指针。|  
|[const_reference](#const_reference)|一种类型，此类型提供对存储在集中的 `const` 元素的引用（用于读取和执行 `const` 操作）。|  
|[const_reverse_iterator](#const_reverse_iterator)|一种类型，此类型提供可读取集中的任何 `const` 元素的双向迭代器。|  
|[difference_type](#difference_type)|一种有符号整数类型，此类型可用于表示集中迭代器指向的元素间范围内的元素数量。|  
|[iterator](#iterator)|一种类型，此类型提供可读取或修改集中的任何元素的双向迭代器。|  
|[key_compare](#key_compare)|一种提供函数对象的类型，该函数对象可比较两个排序键以确定集中两个元素的相对顺序。|  
|[key_type](#key_type)|此类型描述当作为排序键时存储为集中元素的对象。|  
|[pointer](#pointer)|一种类型，此类型提供指向集中元素的指针。|  
|[reference](#reference)|一种类型，此类型提供对存储在集中的元素的引用。|  
|[reverse_iterator](#reverse_iterator)|一种类型，此类型提供可读取或修改反向集中的元素的双向迭代器。|  
|[size_type](#size_type)|一种无符号整数类型，此类型可表示集中的元素数量。|  
|[value_compare](#value_compare)|一种提供函数对象的类型，该函数对象可比较两个元素以确定其在集中的相对顺序。|  
|[value_type](#value_type)|此类型描述当作为值时存储为集中元素的对象。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[begin](#begin)|返回一个迭代器，此迭代器用于发现集中的第一个元素。|  
|[cbegin](#cbegin)|返回一个常量迭代器，此迭代器用于发现集中的第一个元素。|  
|[cend](#cend)|返回一个常量迭代器，此迭代器用于发现集中最后一个元素之后的位置。|  
|[clear](#clear)|清除集的所有元素。|  
|[count](#count)|返回集中其键与指定为参数的键匹配的元素数量。|  
|[crbegin](#rbegin)|返回一个常量迭代器，此迭代器用于发现反向集中的第一个元素。|  
|[crend](#rend)|返回一个常量迭代器，此迭代器用于发现反向集中最后一个元素之后的位置。|  
|[emplace](#emplace)|将就地构造的元素插入到集中。|  
|[emplace_hint](#emplace_hint)|将就地构造的元素插入到集中，附带位置提示。|  
|[empty](#empty)|测试集是否为空。|  
|[end](#end)|返回一个迭代器，此迭代器用于发现集中最后一个元素之后的位置。|  
|[equal_range](#equal_range)|返回一对迭代器，这两个迭代器分别用于发现集中其键大于指定键的第一个元素，以及集中其键等于或大于指定键的第一个元素。|  
|[erase](#erase)|从集中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。|  
|[find](#find)|返回一个迭代器，此迭代器用于发现集中其键与指定键等效的元素的位置。|  
|[get_allocator](#get_allocator)|返回用于构造集的 `allocator` 对象的副本。|  
|[insert](#insert)|将一个元素或元素范围插入到集。|  
|[key_comp](#key_comp)|检索用于对集中的键进行排序的比较对象副本。|  
|[lower_bound](#lower_bound)|返回一个迭代器，此迭代器指向集中其键等于或大于指定键的第一个元素。|  
|[max_size](#max_size)|返回集的最大长度。|  
|[rbegin](#rbegin)|返回一个迭代器，此迭代器用于发现反向集中的第一个元素。|  
|[rend](#rend)|返回一个迭代器，此迭代器用于发现反向集中最后一个元素之后的位置。|  
|[size](#size)|返回集合中元素的数目。|  
|[swap](#swap)|交换两个集的元素。|  
|[upper_bound](#upper_bound)|返回一个迭代器，此迭代器指向集中其键大于指定键的第一个元素。|  
|[value_comp](#value_comp)|检索用于对集中的元素值进行排序的比较对象副本。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator=](#op_eq)|将一个集中的元素替换为另一个集的副本。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<set>  
  
 **命名空间：** std  
  
##  <a name="allocator_type"></a>  set::allocator_type  
 一个类型，代表集对象的分配器类。  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>备注  
 **allocator_type** 是模板参数 [Allocator](../standard-library/set-class.md) 的同义词。  
  
 返回多重集用来对其元素进行排序的函数对象，即模板参数 `Allocator`。  
  
 有关 `Allocator` 的详细信息，请参阅 [set 类](../standard-library/set-class.md)主题的“备注”部分。  
  
### <a name="example"></a>示例  
  有关使用 `allocator_type` 的示例，请参阅 [get_allocator](#get_allocator) 的示例。  
  
##  <a name="begin"></a>  set::begin  
 返回一个迭代器，此迭代器用于发现集中的第一个元素。  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>返回值  
 一个双向迭代器，发现集中第一个元素的位置或空集之后的位置。  
  
### <a name="remarks"></a>备注  
 如果 **begin`const_iterator` 的返回值赋给了** ，则无法修改集对象中的元素。 如果 **begin** 的返回值赋给了 **iterator**，则可以修改集对象中的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_begin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1;  
   set <int>::iterator s1_Iter;  
   set <int>::const_iterator s1_cIter;  
  
   s1.insert( 1 );  
   s1.insert( 2 );  
   s1.insert( 3 );  
  
   s1_Iter = s1.begin( );  
   cout << "The first element of s1 is " << *s1_Iter << endl;  
  
   s1_Iter = s1.begin( );  
   s1.erase( s1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // s1_cIter = s1.begin( );  
   // s1.erase( s1_cIter );  
  
   s1_cIter = s1.begin( );  
   cout << "The first element of s1 is now " << *s1_cIter << endl;  
}  
```  
  
```Output  
The first element of s1 is 1  
The first element of s1 is now 2  
```  
  
##  <a name="cbegin"></a>  set::cbegin  
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
  
##  <a name="cend"></a>  set::cend  
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
  
##  <a name="clear"></a>  set::clear  
 清除集的所有元素。  
  
```  
void clear();
```  
  
### <a name="example"></a>示例  
  
```cpp  
// set_clear.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   set <int> s1;  
  
   s1.insert( 1 );  
   s1.insert( 2 );  
  
   cout << "The size of the set is initially " << s1.size( )  
        << "." << endl;  
  
   s1.clear( );  
   cout << "The size of the set after clearing is "   
        << s1.size( ) << "." << endl;  
}  
```  
  
```Output  
The size of the set is initially 2.  
The size of the set after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>  set::const_iterator  
 一个提供双向迭代器的类型，双向迭代器可读取集中的 **const** 元素。  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `const_iterator` 类型不能用于修改元素的值。  
  
### <a name="example"></a>示例  
  有关 `const_iterator` 的示例，请参阅 [begin](#begin) 的示例。  
  
##  <a name="const_pointer"></a>  set::const_pointer  
 一种类型，此类型提供指向集中的 **const** 元素的指针。  
  
```  
typedef typename allocator_type::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>备注  
 `const_pointer` 类型不能用于修改元素的值。  
  
 在大多数情况下，应使用 [const_iterator](#const_iterator) 访问 const 集对象中的元素。  
  
##  <a name="const_reference"></a>  set::const_reference  
 一种类型，此类型提供对用于读取和执行 **const** 操作的集中存储的 **const** 元素的引用。  
  
```  
typedef typename allocator_type::const_reference const_reference;  
```  
  
### <a name="example"></a>示例  
  
```cpp  
// set_const_ref.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the 1st element  
   const int &Ref1 = *s1.begin( );  
  
   cout << "The first element in the set is "  
        << Ref1 << "." << endl;  
  
   // The following line would cause an error because the   
   // const_reference cannot be used to modify the set  
   // Ref1 = Ref1 + 5;  
}  
```  
  
```Output  
The first element in the set is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>  set::const_reverse_iterator  
 一个提供双向迭代器的类型，双向迭代器可读取集中的任何 **const** 元素。  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `const_reverse_iterator` 类型无法修改元素的值，它用于反向循环访问集。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `const_reverse_iterator` 的示例，请参阅 [rend](#rend) 的示例。  
  
##  <a name="count"></a>  set::count  
 返回集中其键与指定为参数的键匹配的元素数量。  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要从集中进行匹配的元素的键。  
  
### <a name="return-value"></a>返回值  
 如果该集包含其排序关键字匹配参数键的元素，则为 1。 如果该集不包含具有匹配键的元素，则为 0。  
  
### <a name="remarks"></a>备注  
 成员函数返回在以下范围内的元素数目：  
  
 [ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) )。  
  
### <a name="example"></a>示例  
  以下示例演示 set:: count 成员函数的使用。  
  
```  
// set_count.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    set<int> s1;  
    set<int>::size_type i;  
  
    s1.insert(1);  
    s1.insert(1);  
  
    // Keys must be unique in set, so duplicates are ignored  
    i = s1.count(1);  
    cout << "The number of elements in s1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = s1.count(2);  
    cout << "The number of elements in s1 with a sort key of 2 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in s1 with a sort key of 1 is: 1.  
The number of elements in s1 with a sort key of 2 is: 0.  
```  
  
##  <a name="crbegin"></a>  set::crbegin  
 返回一个常量迭代器，此迭代器用于发现反向集中的第一个元素。  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 一个常量反向双向迭代器，发现反向集中的第一个元素或发现曾是非反向集中的最后一个元素的元素。  
  
### <a name="remarks"></a>备注  
 `crbegin` 用于反向集，正如 [begin](#begin) 用于集一样。  
  
 返回值为 `crbegin` 时，无法修改集对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_crbegin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   set <int> s1;  
   set <int>::const_reverse_iterator s1_crIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   s1_crIter = s1.crbegin( );  
   cout << "The first element in the reversed set is "  
        << *s1_crIter << "." << endl;  
}  
```  
  
```Output  
The first element in the reversed set is 30.  
```  
  
##  <a name="crend"></a>  set::crend  
 返回一个常量迭代器，此迭代器用于发现反向集中最后一个元素之后的位置。  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>返回值  
 一个常量反向双向迭代器，用于发现反向集中最后一个元素之后的位置（非反向集中第一个元素之前的位置）。  
  
### <a name="remarks"></a>备注  
 `crend` 用于反向集，正如 [end](#end) 用于集一样。  
  
 返回值为 `crend` 时，无法修改集对象。 不应对 `crend` 返回的值取消引用。  
  
 `crend` 可用于测试反向迭代器是否已到达其集的末尾。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_crend.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   set <int> s1;  
   set <int>::const_reverse_iterator s1_crIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   s1_crIter = s1.crend( );  
   s1_crIter--;  
   cout << "The last element in the reversed set is "  
        << *s1_crIter << "." << endl;  
}  
```  
  
##  <a name="difference_type"></a>  set::difference_type  
 一种有符号整数类型，此类型可用于表示集中迭代器指向的元素间范围内的元素数量。  
  
```  
typedef typename allocator_type::difference_type difference_type;  
```  
  
### <a name="remarks"></a>备注  
 `difference_type` 是通过容器迭代器减少或递增时返回的类型。 `difference_type` 通常用于表示迭代器 `first` 和 `last` 之间的范围 *[ first,  last)* 内元素的数目，包括 `first` 指向的元素以及那一系列元素，但不包括 `last` 指向的元素。  
  
 注意，尽管 `difference_type` 适用于满足输入迭代器（包括可逆容器支持的双向迭代器的类，如集）需求的所有迭代器，迭代器之间的减法仅受随机访问容器（如 vector）提供的随机访问迭代器支持。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <set>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
  
   set <int> s1;  
   set <int>::iterator s1_Iter, s1_bIter, s1_eIter;  
  
   s1.insert( 20 );  
   s1.insert( 10 );  
   s1.insert( 20 );   // won't insert as set elements are unique  
  
   s1_bIter = s1.begin( );  
   s1_eIter = s1.end( );  
  
   set <int>::difference_type   df_typ5, df_typ10, df_typ20;  
  
   df_typ5 = count( s1_bIter, s1_eIter, 5 );  
   df_typ10 = count( s1_bIter, s1_eIter, 10 );  
   df_typ20 = count( s1_bIter, s1_eIter, 20 );  
  
   // the keys, and hence the elements of a set are unique,  
   // so there is at most one of a given value  
   cout << "The number '5' occurs " << df_typ5  
        << " times in set s1.\n";  
   cout << "The number '10' occurs " << df_typ10  
        << " times in set s1.\n";  
   cout << "The number '20' occurs " << df_typ20  
        << " times in set s1.\n";  
  
   // count the number of elements in a set  
   set <int>::difference_type  df_count = 0;  
   s1_Iter = s1.begin( );  
   while ( s1_Iter != s1_eIter)     
   {  
      df_count++;  
      s1_Iter++;  
   }  
  
   cout << "The number of elements in the set s1 is: "   
        << df_count << "." << endl;  
}  
```  
  
```Output  
The number '5' occurs 0 times in set s1.  
The number '10' occurs 1 times in set s1.  
The number '20' occurs 1 times in set s1.  
The number of elements in the set s1 is: 2.  
```  
  
##  <a name="emplace"></a>  set::emplace  
 就地插入构造的元素（不执行复制或移动操作）。  
  
```  
template <class... Args>  
pair<iterator, bool>  
emplace(
    Args&&... args);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`args`|用于构造要插入到集中的元素的转发参数（除非它已包含一个具有相对有序的值的元素）。|  
  
### <a name="return-value"></a>返回值  
 如果完成插入，则 [pair](../standard-library/pair-structure.md) 的组件返回 true；如果映射已经包含一个其值在排序中具有等效值的元素，则为 false。 返回值 pair 的迭代器组件将返回地址。如果 bool 组件为 true，则返回在其中插入新元素的地址；如果 bool 组件为 false，则返回在其中找到元素的地址。  
  
### <a name="remarks"></a>备注  
 此函数不会使迭代器或引用无效。  
  
 在定位过程中，如果引发异常，则不会修改该容器的状态。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_emplace.cpp  
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
    set<string> s1;  
  
    auto ret = s1.emplace("ten");  
  
    if (!ret.second){  
        cout << "Emplace failed, element with value \"ten\" already exists."  
            << endl << "  The existing element is (" << *ret.first << ")"  
            << endl;  
        cout << "set not modified" << endl;  
    }  
    else{  
        cout << "set modified, now contains ";  
        print(s1);  
    }  
    cout << endl;  
  
    ret = s1.emplace("ten");  
  
    if (!ret.second){  
        cout << "Emplace failed, element with value \"ten\" already exists."  
            << endl << "  The existing element is (" << *ret.first << ")"  
            << endl;  
    }  
    else{  
        cout << "set modified, now contains ";  
        print(s1);  
    }  
    cout << endl;  
}  
  
```  
  
##  <a name="emplace_hint"></a>  set::emplace_hint  
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
|参数|描述|  
|`args`|用于构造要插入集中的元素的转发自变量，除非集已包含该元素，或更普遍的情况是除非它已包含其值已经过相同排序的元素。|  
|`where`|开始搜索正确插入点的位置。 （如果该点紧贴在 `where` 之前，则插入可能发生在分期常量时间内而非对数时间内。)|  
  
### <a name="return-value"></a>返回值  
 指向新插入的元素的迭代器。  
  
 如果因元素已存在导致插入失败，则将迭代器返回现有元素。  
  
### <a name="remarks"></a>备注  
 此函数不会使迭代器或引用无效。  
  
 在定位过程中，如果引发异常，则不会修改该容器的状态。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_emplace.cpp  
// compile with: /EHsc  
#include <set>  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
template <typename S> void print(const S& s) {  
    cout << s.size() << " elements: " << endl;  
  
    for (const auto& p : s) {  
        cout << "(" << p <<  ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    set<string> s1;  
  
    // Emplace some test data  
    s1.emplace("Anna");  
    s1.emplace("Bob");  
    s1.emplace("Carmine");  
  
    cout << "set starting data: ";  
    print(s1);  
    cout << endl;  
  
    // Emplace with hint  
    // s1.end() should be the "next" element after this emplacement  
    s1.emplace_hint(s1.end(), "Doug");  
  
    cout << "set modified, now contains ";  
    print(s1);  
    cout << endl;  
}  
  
```  
  
##  <a name="empty"></a>  set::empty  
 测试集是否为空。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 如果集为空，则为 **true**；如果集不为空，则为 **false**。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_empty.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2;  
   s1.insert ( 1 );  
  
   if ( s1.empty( ) )  
      cout << "The set s1 is empty." << endl;  
   else  
      cout << "The set s1 is not empty." << endl;  
  
   if ( s2.empty( ) )  
      cout << "The set s2 is empty." << endl;  
   else  
      cout << "The set s2 is not empty." << endl;  
}  
```  
  
```Output  
The set s1 is not empty.  
The set s2 is empty.  
```  
  
##  <a name="end"></a>  set::end  
 返回超过末尾迭代器。  
  
```  
const_iterator end() const;

 
 
iterator end();
```  
  
### <a name="return-value"></a>返回值  
 超过末尾迭代器。 如果该集为空，则 `set::end() == set::begin()`。  
  
### <a name="remarks"></a>备注  
 **end** 用于测试迭代器是否超过集的末尾。  
  
 不应对 **end** 返回的值取消引用。  
  
 有关代码示例，请参阅 [set::find](#find)。  
  
##  <a name="equal_range"></a>  set::equal_range  
 返回一对迭代器，这两个迭代器分别用于发现集中其键大于或等于指定键的第一个元素，以及集中其键大于指定键的第一个元素。  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的集中元素的排序键进行比较的参数键。  
  
### <a name="return-value"></a>返回值  
 一对迭代器，其中第一个是键的 [lower_bound](#lower_bound)，第二个是键的 [upper_bound](#upper_bound)。  
  
 若要访问成员函数返回的 `pr` 对的第一个迭代器，请使用 `pr`. **first**；若要取消引用下界迭代器，请使用 \*( `pr`. **first**)。 若要访问成员函数返回的 `pr` 对的第二个迭代器，请使用 `pr`. **second**；若要取消引用上界迭代器，请使用 \*( `pr`. **second**)。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_equal_range.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   typedef set<int, less< int > > IntSet;  
   IntSet s1;  
   set <int, less< int > > :: const_iterator s1_RcIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;  
   p1 = s1.equal_range( 20 );  
  
   cout << "The upper bound of the element with "  
        << "a key of 20 in the set s1 is: "  
        << *(p1.second) << "." << endl;  
  
   cout << "The lower bound of the element with "  
        << "a key of 20 in the set s1 is: "  
        << *(p1.first) << "." << endl;  
  
   // Compare the upper_bound called directly   
   s1_RcIter = s1.upper_bound( 20 );  
   cout << "A direct call of upper_bound( 20 ) gives "  
        << *s1_RcIter << "," << endl  
        << "matching the 2nd element of the pair"  
        << " returned by equal_range( 20 )." << endl;  
  
   p2 = s1.equal_range( 40 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == s1.end( ) ) && ( p2.second == s1.end( ) ) )  
      cout << "The set s1 doesn't have an element "  
           << "with a key less than 40." << endl;  
   else  
      cout << "The element of set s1 with a key >= 40 is: "  
           << *(p1.first) << "." << endl;  
}  
```  
  
```Output  
The upper bound of the element with a key of 20 in the set s1 is: 30.  
The lower bound of the element with a key of 20 in the set s1 is: 20.  
A direct call of upper_bound( 20 ) gives 30,  
matching the 2nd element of the pair returned by equal_range( 20 ).  
The set s1 doesn't have an element with a key less than 40.  
```  
  
##  <a name="erase"></a>  set::erase  
 从集中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。  
  
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
 对于前两个成员函数，则为双向迭代器，它指定已删除的任何元素之外留存的第一个元素，如果此类元素不存在，则为集末尾的元素。  
  
 对于第三个成员函数，则返回已从集中删除的元素数目。  
  
### <a name="remarks"></a>备注  
  
### <a name="example"></a>示例  
  
```cpp  
// set_erase.cpp  
// compile with: /EHsc  
#include <set>  
#include <string>  
#include <iostream>  
#include <iterator> // next() and prev() helper functions  
  
using namespace std;  
  
using myset = set<string>;  
  
void printset(const myset& s) {  
    for (const auto& iter : s) {  
        cout << " [" << iter << "]";  
    }  
    cout << endl << "size() == " << s.size() << endl << endl;  
}  
  
int main()  
{  
    myset s1;  
  
    // Fill in some data to test with, one at a time  
    s1.insert("Bob");  
    s1.insert("Robert");  
    s1.insert("Bert");  
    s1.insert("Rob");  
    s1.insert("Bobby");  
  
    cout << "Starting data of set s1 is:" << endl;  
    printset(s1);  
    // The 1st member function removes an element at a given position  
    s1.erase(next(s1.begin()));  
    cout << "After the 2nd element is deleted, the set s1 is:" << endl;  
    printset(s1);  
  
    // Fill in some data to test with, one at a time, using an intializer list  
    myset s2{ "meow", "hiss", "purr", "growl", "yowl" };  
  
    cout << "Starting data of set s2 is:" << endl;  
    printset(s2);  
    // The 2nd member function removes elements  
    // in the range [First, Last)  
    s2.erase(next(s2.begin()), prev(s2.end()));  
    cout << "After the middle elements are deleted, the set s2 is:" << endl;  
    printset(s2);  
  
    myset s3;  
  
    // Fill in some data to test with, one at a time, using emplace  
    s3.emplace("C");  
    s3.emplace("C#");  
    s3.emplace("D");  
    s3.emplace("D#");  
    s3.emplace("E");  
    s3.emplace("E#");  
    s3.emplace("F");  
    s3.emplace("F#");  
    s3.emplace("G");  
    s3.emplace("G#");  
    s3.emplace("A");  
    s3.emplace("A#");  
    s3.emplace("B");  
  
    cout << "Starting data of set s3 is:" << endl;  
    printset(s3);  
    // The 3rd member function removes elements with a given Key  
    myset::size_type count = s3.erase("E#");  
    // The 3rd member function also returns the number of elements removed  
    cout << "The number of elements removed from s3 is: " << count << "." << endl;  
    cout << "After the element with a key of \"E#\" is deleted, the set s3 is:" << endl;  
    printset(s3);  
}  
  
```  
  
##  <a name="find"></a>  set::find  
 返回引用集中具有与指定键等效的键的元素的位置的迭代器。  
  
```  
iterator find(const Key& key);

 
const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要从集中搜索的元素的排序键与键值匹配。  
  
### <a name="return-value"></a>返回值  
 引用具有指定键的元素的位置，或引用集 (`set::end()`) 中最后一个元素后面的位置（如果找不到键匹配）的迭代器。  
  
### <a name="remarks"></a>备注  
 成员函数返回引用集中其键与二元谓词下的参数 `key` 等效的元素的迭代器，该谓词基于小于比较关系生成排序。  
  
 如果 **find** 的返回值赋给 **const_iterator**，则无法修改集对象。 如果 **find** 的返回值赋给 **iterator**，则可以修改集对象  
  
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
    set<int> s1({ 40, 45 });  
    cout << "The starting set s1 is: " << endl;  
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
  
    cout << "The modified set s1 is: " << endl;  
    print_collection(s1);  
    cout << endl;  
    findit(s1, 45);  
    findit(s1, 6);  
}  
  
```  
  
##  <a name="get_allocator"></a>  set::get_allocator  
 返回用于构造集的分配器对象的一个副本。  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>返回值  
 由集用来管理内存的分配器，即模板参数 `Allocator`。  
  
 有关 `Allocator` 的详细信息，请参阅 [set 类](../standard-library/set-class.md)主题的“备注”部分。  
  
### <a name="remarks"></a>备注  
 set 类的分配器指定类管理存储的方式。 C++ 标准库容器类提供的默认分配器足以满足大多编程需求。 编写和使用你自己的分配器类是高级 C++ 主题。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_get_allocator.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int>::allocator_type s1_Alloc;  
   set <int>::allocator_type s2_Alloc;  
   set <double>::allocator_type s3_Alloc;  
   set <int>::allocator_type s4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   set <int> s1;  
   set <int, allocator<int> > s2;  
   set <double, allocator<double> > s3;  
  
   s1_Alloc = s1.get_allocator( );  
   s2_Alloc = s2.get_allocator( );  
   s3_Alloc = s3.get_allocator( );  
  
   cout << "The number of integers that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << s2.max_size( ) << "." << endl;  
  
   cout << "\nThe number of doubles that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << s3.max_size( ) <<  "." << endl;  
  
   // The following line creates a set s4  
   // with the allocator of multiset s1.  
   set <int> s4( less<int>( ), s1_Alloc );  
  
   s4_Alloc = s4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated by the other  
   if( s1_Alloc == s4_Alloc )  
   {  
      cout << "\nThe allocators are interchangeable."  
           << endl;  
   }  
   else  
   {  
      cout << "\nThe allocators are not interchangeable."  
           << endl;  
   }  
}  
```  
  
##  <a name="insert"></a>  set::insert  
 将一个元素或元素范围插入到集。  
  
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
|`Val`|要插入到集中的元素的值（除非它已经包含一个具有相对有序的值的元素）。|  
|`Where`|开始搜索正确插入点的位置。 （如果该点紧贴在 `Where` 之前，则插入可能发生在分期常量时间内而非对数时间内。)|  
|`ValTy`|指定集可用于构造 [value_type`Val` 元素的自变量类型并将 ](../standard-library/map-class.md#value_type) 作为自变量完美转发的模板参数。|  
|`First`|要复制的第一个元素的位置。|  
|`Last`|要复制的最后一个元素以外的位置。|  
|`InputIterator`|满足[输入迭代器](../standard-library/input-iterator-tag-struct.md)需求的模板函数自变量，该输入迭代器指向可用于构造 [value_type](../standard-library/map-class.md#value_type) 对象的类型的元素。|  
|`IList`|从中复制元素的 [initializer_list](../standard-library/initializer-list.md)。|  
  
### <a name="return-value"></a>返回值  
 单个元素成员函数 (1) 和 (2) 将返回 [pair](../standard-library/pair-structure.md)，如果完成插入，则其 `bool` 组件为 true；如果该集已经包含一个在排序中具有等效值的元素，则为 false。 返回值对的迭代器组件将指向新插入的元素（如果 `bool` 组件为 true）或现有元素（如果 `bool` 组件为 false）。  
  
 附带提示的单个元素成员函数 (3) 和 (4) 将返回迭代器，该迭代器指向将新元素插入到该集中的位置，如果具有等效键的元素已经存在，则指向现有元素。  
  
### <a name="remarks"></a>备注  
 任何迭代器、指针或引用都不会因为此函数而失效。  
  
 在插入单个元素的过程中，如果引发异常，则不会修改该容器的状态。 在插入多个元素的过程中，如果引发异常，则会使容器处于未指定但有效的状态。  
  
 若要访问单个元素成员函数返回的 `pair``pr` 的迭代器组件，请使用 `pr.first`；若要在返回的对中取消引用迭代器，请使用 `*pr.first`，这将向你提供一个元素。 要访问 `bool` 组件，请使用 `pr.second`。 有关示例，请参阅本文后面的示例代码。  
  
 容器的 [value_type](../standard-library/map-class.md#value_type) 是属于该容器的 typedef；对于集，`set<V>::value_type` 是 `const V` 类型。  
  
 范围成员函数 (5) 将元素值序列插入到集中，它对应于迭代器在范围 `[First, Last)` 中所处理的每一个元素；因此，不会插入 `Last`。 容器成员函数 `end()` 是指容器中最后一个元素之后的位置，例如，`s.insert(v.begin(), v.end());` 语句尝试将 `v` 的所有元素插入到 `s` 中。 只插入在该范围中具有唯一值的元素；忽略副本。 若要观察拒绝了哪些元素，请使用单个元素版本的 `insert`。  
  
 初始值设定项列表成员函数 (6) 使用 [initializer_list](../standard-library/initializer-list.md) 将元素复制到该集中。  
  
 有关就地构造的元素的插入（即不会执行复制或移动操作），请参阅 [set::emplace](#emplace) 和 [set::emplace_hint](#emplace_hint)。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_insert.cpp  
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
    set<int> s1;  
    // call insert(const value_type&) version  
    s1.insert({ 1, 10 });  
    // call insert(ValTy&&) version   
    s1.insert(20);  
  
    cout << "The original set values of s1 are:" << endl;  
    print(s1);  
  
    // intentionally attempt a duplicate, single element  
    auto ret = s1.insert(1);  
    if (!ret.second){  
        auto elem = *ret.first;  
        cout << "Insert failed, element with value 1 already exists."  
            << endl << "  The existing element is (" << elem << ")"  
            << endl;  
    }  
    else{  
        cout << "The modified set values of s1 are:" << endl;  
        print(s1);  
    }  
    cout << endl;  
  
    // single element, with hint  
    s1.insert(s1.end(), 30);  
    cout << "The modified set values of s1 are:" << endl;  
    print(s1);  
    cout << endl;  
  
    // The templatized version inserting a jumbled range  
    set<int> s2;  
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
  
    cout << "The modified set values of s2 are:" << endl;  
    print(s2);  
    cout << endl;  
  
    // The templatized versions move-constructing elements  
    set<string>  s3;  
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
  
    set<int> s4;  
    // Insert the elements from an initializer_list  
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });  
    cout << "After initializer_list insertion, s4 contains:" << endl;  
    print(s4);  
    cout << endl;  
}  
  
```  
  
##  <a name="iterator"></a>  set::iterator  
 一种提供常量[双向迭代器](../standard-library/bidirectional-iterator-tag-struct.md)的类型，双向迭代器可读取集中的任何元素。  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="example"></a>示例  
  有关如何声明和使用 **iterator** 的示例，请参阅 [begin](#begin) 的示例。  
  
##  <a name="key_comp"></a>  set::key_comp  
 检索用于对集中的键进行排序的比较对象副本。  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>返回值  
 返回集使用对其元素进行排序的函数对象，即模板参数 `Traits`。  
  
 有关 `Traits` 的详细信息，请参阅 [set 类](../standard-library/set-class.md)主题。  
  
### <a name="remarks"></a>备注  
 存储对象用于定义以下成员函数：  
  
 **bool operator()**( **const Key&**`_xVal`, **const Key&**`_yVal`);  
  
 如果 `_xVal` 在排序顺序中先于且不等于 `_yVal`，则该函数会返回 **true**。  
  
 请注意，[key_compare](#key_compare) 和 [value_compare](#value_compare) 皆是模板参数 **Traits** 的同义词。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_key_comp.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   set <int, less<int> > s1;  
   set<int, less<int> >::key_compare kc1 = s1.key_comp( ) ;  
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
           << "where kc1 is the function object of s1."  
           << endl;  
   }  
  
   set <int, greater<int> > s2;  
   set<int, greater<int> >::key_compare kc2 = s2.key_comp( ) ;  
   bool result2 = kc2( 2, 3 ) ;  
   if(result2 == true)     
   {  
      cout << "kc2( 2,3 ) returns value of true, "  
           << "where kc2 is the function object of s2."  
           << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false, "  
           << "where kc2 is the function object of s2."  
           << endl;  
   }  
}  
```  
  
```Output  
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.  
kc2( 2,3 ) returns value of false, where kc2 is the function object of s2.  
```  
  
##  <a name="key_compare"></a>  set::key_compare  
 一种提供函数对象的类型，该函数对象可比较两个排序键以确定集中两个元素的相对顺序。  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>备注  
 `key_compare` 是模板参数 `Traits` 的同义词。  
  
 有关 `Traits` 的详细信息，请参阅 [set 类](../standard-library/set-class.md)主题。  
  
 请注意，`key_compare` 和 [value_compare](#value_compare) 皆是模板参数 **Traits** 的同义词。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `key_compare` 的示例，请参阅 [key_comp](#key_comp) 的示例。  
  
##  <a name="key_type"></a>  set::key_type  
 一种类型，此类型将在其容量中存储为 set 元素的对象描述为排序键。  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>备注  
 `key_type` 是模板参数 `Key` 的同义词。  
  
 有关 `Key` 的详细信息，请参阅 [set 类](../standard-library/set-class.md)主题的“备注”部分。  
  
 请注意，`key_type` 和 [value_type](#value_type) 皆是模板参数 **Key** 的同义词。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `key_type` 的示例，请参阅 [value_type](#value_type) 的示例。  
  
##  <a name="lower_bound"></a>  set::lower_bound  
 返回一个迭代器，此迭代器指向集中其键等于或大于指定键的第一个元素。  
  
```  
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的集中元素的排序键进行比较的参数键。  
  
### <a name="return-value"></a>返回值  
 一个迭代器或 `const_iterator`，其会发现集中其键等于或大于参数键的元素的位置，或如果未找到键的匹配项，则发现集中最后一个元素之后的位置。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_lower_bound.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1;  
   set <int> :: const_iterator s1_AcIter, s1_RcIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   s1_RcIter = s1.lower_bound( 20 );  
   cout << "The element of set s1 with a key of 20 is: "  
        << *s1_RcIter << "." << endl;  
  
   s1_RcIter = s1.lower_bound( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( s1_RcIter == s1.end( ) )  
      cout << "The set s1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of set s1 with a key of 40 is: "  
           << *s1_RcIter << "." << endl;  
  
   // The element at a specific location in the set can be found   
   // by using a dereferenced iterator that addresses the location  
   s1_AcIter = s1.end( );  
   s1_AcIter--;  
   s1_RcIter = s1.lower_bound( *s1_AcIter );  
   cout << "The element of s1 with a key matching "  
        << "that of the last element is: "  
        << *s1_RcIter << "." << endl;  
}  
```  
  
```Output  
The element of set s1 with a key of 20 is: 20.  
The set s1 doesn't have an element with a key of 40.  
The element of s1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="max_size"></a>  set::max_size  
 返回集的最大长度。  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>返回值  
 集的最大可取长度。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_max_size.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   set <int> s1;  
   set <int>::size_type i;  
  
   i = s1.max_size( );     
   cout << "The maximum possible length "  
        << "of the set is " << i << "." << endl;  
}  
```  
  
##  <a name="op_eq"></a>set::operator=  
 使用另一个 `set` 的元素替换该 `set` 的元素。  
  
```  
set& operator=(const set& right);

set& operator=(set&& right);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`right`|`set` 提供用于分配给此 `set` 的新元素。|  
  
### <a name="remarks"></a>备注  
 `operator=` 的第一个版本使用 `right` 的 [左值引用](../cpp/lvalue-reference-declarator-amp.md)，将元素从 `right` 复制到此 `set`。  
  
 第二个版本使用 right 的[右值引用](../cpp/rvalue-reference-declarator-amp-amp.md)。 将元素从 `right` 移动到此 `set`。  
  
 执行运算符函数之前，丢弃此 `set` 中的任何元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_operator_as.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   set<int> v1, v2, v3;  
   set<int>::iterator iter;  
  
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
  
##  <a name="pointer"></a>  set::pointer  
 一种类型，此类型提供指向集中元素的指针。  
  
```  
typedef typename allocator_type::pointer pointer;  
```  
  
### <a name="remarks"></a>备注  
 **pointer** 类型可用于修改元素的值。  
  
 在大多数情况下，应使用 [iterator](#iterator) 访问集对象中的元素。  
  
##  <a name="rbegin"></a>  set::rbegin  
 返回一个迭代器，此迭代器用于发现反向集中的第一个元素。  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>返回值  
 一个反向双向迭代器，发现反向集中的第一个元素或发现曾是非反向集中的最后一个元素的元素。  
  
### <a name="remarks"></a>备注  
 `rbegin` 用于反向集，正如 [begin](#begin) 用于集一样。  
  
 如果将 `rbegin` 的返回值分配给 `const_reverse_iterator`，则无法修改集对象。 如果将 `rbegin` 的返回值分配给 `reverse_iterator`，则可修改集对象。  
  
 `rbegin` 可用于向后循环访问集。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_rbegin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   set <int> s1;  
   set <int>::iterator s1_Iter;  
   set <int>::reverse_iterator s1_rIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   s1_rIter = s1.rbegin( );  
   cout << "The first element in the reversed set is "  
        << *s1_rIter << "." << endl;  
  
   // begin can be used to start an iteration   
   // throught a set in a forward order  
   cout << "The set is:";  
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter;  
   cout << endl;  
  
   // rbegin can be used to start an iteration   
   // throught a set in a reverse order  
   cout << "The reversed set is:";  
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )  
      cout << " " << *s1_rIter;  
   cout << endl;  
  
   // A set element can be erased by dereferencing to its key   
   s1_rIter = s1.rbegin( );  
   s1.erase ( *s1_rIter );  
  
   s1_rIter = s1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed set is "<< *s1_rIter << "." << endl;  
}  
```  
  
```Output  
The first element in the reversed set is 30.  
The set is: 10 20 30  
The reversed set is: 30 20 10  
After the erasure, the first element in the reversed set is 20.  
```  
  
##  <a name="reference"></a>  set::reference  
 一种类型，此类型提供对存储在集中的元素的引用。  
  
```  
typedef typename allocator_type::reference reference;  
```  
  
### <a name="example"></a>示例  
  
```cpp  
// set_reference.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
  
   // Declare and initialize a reference &Ref1 to the 1st element  
   const int &Ref1 = *s1.begin( );  
  
   cout << "The first element in the set is "  
        << Ref1 << "." << endl;  
}  
```  
  
```Output  
The first element in the set is 10.  
```  
  
##  <a name="rend"></a>  set::rend  
 返回一个迭代器，此迭代器用于发现反向集中最后一个元素之后的位置。  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>返回值  
 一个反向双向迭代器，用于发现反向集中最后一个元素之后的位置（非反向集中第一个元素之前的位置）。  
  
### <a name="remarks"></a>备注  
 `rend` 用于反向集，正如 [end](#end) 用于集一样。  
  
 如果将 `rend` 的返回值分配给 `const_reverse_iterator`，则无法修改集对象。 如果将 `rend` 的返回值分配给 `reverse_iterator`，则可修改集对象。 不应对 `rend` 返回的值取消引用。  
  
 `rend` 可用于测试反向迭代器是否已到达其集的末尾。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_rend.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   set <int> s1;  
   set <int>::iterator s1_Iter;  
   set <int>::reverse_iterator s1_rIter;  
   set <int>::const_reverse_iterator s1_crIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   s1_rIter = s1.rend( );  
   s1_rIter--;  
   cout << "The last element in the reversed set is "  
        << *s1_rIter << "." << endl;  
  
   // end can be used to terminate an iteration   
   // throught a set in a forward order  
   cout << "The set is: ";  
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )  
      cout << *s1_Iter << " ";  
   cout << "." << endl;  
  
   // rend can be used to terminate an iteration   
   // throught a set in a reverse order  
   cout << "The reversed set is: ";  
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )  
      cout << *s1_rIter << " ";  
   cout << "." << endl;  
  
   s1_rIter = s1.rend( );  
   s1_rIter--;  
   s1.erase ( *s1_rIter );  
  
   s1_rIter = s1.rend( );  
   --s1_rIter;  
   cout << "After the erasure, the last element in the "  
        << "reversed set is " << *s1_rIter << "." << endl;  
}  
```  
  
##  <a name="reverse_iterator"></a>  set::reverse_iterator  
 一种类型，此类型提供可读取或修改反向集中的元素的双向迭代器。  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `reverse_iterator` 类型用于反向循环访问集。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `reverse_iterator` 的示例，请参阅 [rbegin](#rbegin) 的示例。  
  
##  <a name="set"></a>  set::set  
 构造一个空的或者是其他某个集的全部或部分副本的集。  
  
```  
set();

explicit set(
    const Traits& Comp);

set(
    const Traits& Comp,  
    const Allocator& Al);

set(
    const set& Right);

set(
    set&& Right);

set(
    initializer_list<Type> IList);

set(
    initializer_list<Type> IList,  
    const Compare& Comp);

set(
    initializer_list<Type> IList,  
    const Compare& Comp,   
    const Allocator& Al);

 
template <class InputIterator>  
set(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
set(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp);

template <class InputIterator>  
set(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`Al`|要用于此集对象的存储分配器类，默认为 **Allocator**。|  
|`Comp`|用于对集中元素排序的 `const Traits` 类型比较函数，默认为 `Compare`。|  
|`Rght`|要以构造的集为副本的集。|  
|`First`|要复制的范围元素中的第一个元素的位置。|  
|`Last`|要复制的元素范围以外的第一个元素的位置。|  
|`IList`|从中复制元素的 initializer_list。|  
  
### <a name="remarks"></a>备注  
 所有构造函数存储一种类型的分配器对象，此类对象管理集的内存存储，且事后可通过调用 [get_allocator](#get_allocator) 返回。 此分配器参数在类声明中常省略，并预处理用于代替备用分配器的宏。  
  
 所有构造函数对其集进行初始化。  
  
 所有构造函数会存储 **Traits** 类型的函数对象，此对象用于在集的键之间建立排序，且稍后可通过调用 [key_comp](#key_comp) 返回。  
  
 前三个构造函数均指定空的初始集，此外，第二个函数还指定用于建立元素顺序的比较函数 ( `comp`) 的类型，第三个函数显式指定了要使用的分配器类型 ( `al`)。 关键字 **explicit** 取消某些种类的自动类型转换。  
  
 第四个构造函数指定集 `right` 的副本。  
  
 接下来的三个构造函数使用 initializer_list 指定元素。  
  
 接下来的三个构造函数复制集的范围 [ `first`, `last`)，且对类 **Traits** 和 **Allocator** 的比较函数类型的指定更明确。  
  
 第八个构造函数通过移动 `right` 指定集副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_set.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    // Create an empty set s0 of key type integer  
    set <int> s0;  
  
    // Create an empty set s1 with the key comparison  
    // function of less than, then insert 4 elements  
    set <int, less<int> > s1;  
    s1.insert(10);  
    s1.insert(20);  
    s1.insert(30);  
    s1.insert(40);  
  
    // Create an empty set s2 with the key comparison  
    // function of less than, then insert 2 elements  
    set <int, less<int> > s2;  
    s2.insert(10);  
    s2.insert(20);  
  
    // Create a set s3 with the   
    // allocator of set s1  
    set <int>::allocator_type s1_Alloc;  
    s1_Alloc = s1.get_allocator();  
    set <int> s3(less<int>(), s1_Alloc);  
    s3.insert(30);  
  
    // Create a copy, set s4, of set s1  
    set <int> s4(s1);  
  
    // Create a set s5 by copying the range s1[ first,  last)  
    set <int>::const_iterator s1_bcIter, s1_ecIter;  
    s1_bcIter = s1.begin();  
    s1_ecIter = s1.begin();  
    s1_ecIter++;  
    s1_ecIter++;  
    set <int> s5(s1_bcIter, s1_ecIter);  
  
    // Create a set s6 by copying the range s4[ first,  last)  
    // and with the allocator of set s2  
    set <int>::allocator_type s2_Alloc;  
    s2_Alloc = s2.get_allocator();  
    set <int> s6(s4.begin(), ++s4.begin(), less<int>(), s2_Alloc);  
  
    cout << "s1 =";  
    for (auto i : s1)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "s2 = " << *s2.begin() << " " << *++s2.begin() << endl;  
  
    cout << "s3 =";  
    for (auto i : s3)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "s4 =";  
    for (auto i : s4)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "s5 =";  
    for (auto i : s5)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "s6 =";  
    for (auto i : s6)  
        cout << " " << i;  
    cout << endl;  
  
    // Create a set by moving s5  
    set<int> s7(move(s5));  
    cout << "s7 =";  
    for (auto i : s7)  
        cout << " " << i;  
    cout << endl;  
  
    // Create a set with an initializer_list  
    cout << "s8 =";  
    set<int> s8{ { 1, 2, 3, 4 } };  
    for (auto i : s8)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "s9 =";  
    set<int> s9{ { 5, 6, 7, 8 }, less<int>() };  
    for (auto i : s9)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "s10 =";  
    set<int> s10{ { 10, 20, 30, 40 }, less<int>(), s9.get_allocator() };  
    for (auto i : s10)  
        cout << " " << i;  
    cout << endl;  
}  
  
```  
  
```Output  
s1 = 10 20 30 40s2 = 10 20s3 = 30s4 = 10 20 30 40s5 = 10 20s6 = 10s7 = 10 20s8 = 1 2 3 4s9 = 5 6 7 8s10 = 10 20 30 40  
```  
  
##  <a name="size"></a>  set::size  
 返回集合中元素的数目。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 集的当前长度。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_size.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1;  
   set <int> :: size_type i;  
  
   s1.insert( 1 );  
   i = s1.size( );  
   cout << "The set length is " << i << "." << endl;  
  
   s1.insert( 2 );  
   i = s1.size( );  
   cout << "The set length is now " << i << "." << endl;  
}  
```  
  
```Output  
The set length is 1.  
The set length is now 2.  
```  
  
##  <a name="size_type"></a>  set::size_type  
 一种无符号整数类型，此类型可表示集中的元素数量。  
  
```  
typedef typename allocator_type::size_type size_type;  
```  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `size_type` 的示例，请参阅 [size](#size) 的示例  
  
##  <a name="swap"></a>  set::swap  
 交换两个集的元素。  
  
```  
void swap(
    set<Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 参数集，提供与目标集进行交换的元素。  
  
### <a name="remarks"></a>备注  
 此成员函数不会使后列项失效：用于在正在交换元素的两个集中指定元素的任何引用、指针或迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_swap.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3;  
   set <int>::iterator s1_Iter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
   s2.insert( 100 );  
   s2.insert( 200 );  
   s3.insert( 300 );  
  
   cout << "The original set s1 is:";  
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   s1.swap( s2 );  
  
   cout << "After swapping with s2, list s1 is:";  
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( s1, s3 );  
  
   cout << "After swapping with s3, list s1 is:";  
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original set s1 is: 10 20 30.  
After swapping with s2, list s1 is: 100 200.  
After swapping with s3, list s1 is: 300.  
```  
  
##  <a name="upper_bound"></a>  set::upper_bound  
 返回一个迭代器，此迭代器指向集中其键大于指定键的第一个元素。  
  
```  
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要与当前搜索的集中元素的排序键进行比较的参数键。  
  
### <a name="return-value"></a>返回值  
 一个 **iterator** 或 `const_iterator`，其会发现集中其键大于参数键的元素位置，或如果未找到键的匹配项，则发现集中最后一个元素之后的位置。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_upper_bound.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   set <int> s1;  
   set <int> :: const_iterator s1_AcIter, s1_RcIter;  
  
   s1.insert( 10 );  
   s1.insert( 20 );  
   s1.insert( 30 );  
  
   s1_RcIter = s1.upper_bound( 20 );  
   cout << "The first element of set s1 with a key greater "  
        << "than 20 is: " << *s1_RcIter << "." << endl;  
  
   s1_RcIter = s1.upper_bound( 30 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( s1_RcIter == s1.end( ) )  
      cout << "The set s1 doesn't have an element "  
           << "with a key greater than 30." << endl;  
   else  
      cout << "The element of set s1 with a key > 40 is: "  
           << *s1_RcIter << "." << endl;  
  
   // The element at a specific location in the set can be found   
   // by using a dereferenced iterator addressing the location  
   s1_AcIter = s1.begin( );  
   s1_RcIter = s1.upper_bound( *s1_AcIter );  
   cout << "The first element of s1 with a key greater than"  
        << endl << "that of the initial element of s1 is: "  
        << *s1_RcIter << "." << endl;  
}  
```  
  
```Output  
The first element of set s1 with a key greater than 20 is: 30.  
The set s1 doesn't have an element with a key greater than 30.  
The first element of s1 with a key greater than  
that of the initial element of s1 is: 20.  
```  
  
##  <a name="value_comp"></a>  set::value_comp  
 检索用于对集中的元素值进行排序的比较对象副本。  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>返回值  
 返回集使用对其元素进行排序的函数对象，即模板参数 `Traits`。  
  
 有关 `Traits` 的详细信息，请参阅 [set 类](../standard-library/set-class.md)主题。  
  
### <a name="remarks"></a>备注  
 存储对象用于定义以下成员函数：  
  
 **bool operator**( **const Key&**`_xVal`, **const Key&**`_yVal`);  
  
 如果 `_xVal` 在排序顺序中先于且不等于 `_yVal`，则该函数会返回 **true**。  
  
 请注意，[value_compare](#value_compare) 和 [key_compare](#key_compare) 皆是模板参数 **Traits** 的同义词。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_value_comp.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   set <int, less<int> > s1;  
   set <int, less<int> >::value_compare vc1 = s1.value_comp( );  
   bool result1 = vc1( 2, 3 );  
   if( result1 == true )     
   {  
      cout << "vc1( 2,3 ) returns value of true, "  
           << "where vc1 is the function object of s1."  
           << endl;  
   }  
   else     
   {  
      cout << "vc1( 2,3 ) returns value of false, "  
           << "where vc1 is the function object of s1."  
           << endl;  
   }  
  
   set <int, greater<int> > s2;  
   set<int, greater<int> >::value_compare vc2 = s2.value_comp( );  
   bool result2 = vc2( 2, 3 );  
   if( result2 == true )     
   {  
      cout << "vc2( 2,3 ) returns value of true, "  
           << "where vc2 is the function object of s2."  
           << endl;  
   }  
   else     
   {  
      cout << "vc2( 2,3 ) returns value of false, "  
           << "where vc2 is the function object of s2."  
           << endl;  
   }  
}  
```  
  
```Output  
vc1( 2,3 ) returns value of true, where vc1 is the function object of s1.  
vc2( 2,3 ) returns value of false, where vc2 is the function object of s2.  
```  
  
##  <a name="value_compare"></a>  set::value_compare  
 一种提供函数对象的类型，该函数对象可比较两个元素值以确定其在集中的相对顺序。  
  
```  
typedef key_compare value_compare;  
```  
  
### <a name="remarks"></a>备注  
 `value_compare` 是模板参数 `Traits` 的同义词。  
  
 有关 `Traits` 的详细信息，请参阅 [set 类](../standard-library/set-class.md)主题。  
  
 请注意，[key_compare](#key_compare) 和 **value_compare** 皆是模板参数 **Traits** 的同义词。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `value_compare` 的示例，请参阅 [value_comp](#value_comp) 的示例。  
  
##  <a name="value_type"></a>  set::value_type  
 一种类型，此类型将在其容量中存储为 set 元素的对象描述为值。  
  
```  
typedef Key value_type;  
```  
  
### <a name="remarks"></a>备注  
 `value_type` 是模板参数 `Key` 的同义词。  
  
 有关 `Key` 的详细信息，请参阅 [set 类](../standard-library/set-class.md)主题的“备注”部分。  
  
 请注意，[key_type](#key_type) 和 `value_type` 皆是模板参数 **Key** 的同义词。 对于 set 和 multiset 类，会同时提供这两种类型，且二者相同，但为实现与 map 和 multimap 类的兼容性时，二者则不同。  
  
### <a name="example"></a>示例  
  
```cpp  
// set_value_type.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1;  
   set <int>::iterator s1_Iter;  
  
   set <int>::value_type svt_Int;   // Declare value_type  
   svt_Int = 10;            // Initialize value_type  
  
   set <int> :: key_type skt_Int;   // Declare key_type  
   skt_Int = 20;             // Initialize key_type  
  
   s1.insert( svt_Int );         // Insert value into s1  
   s1.insert( skt_Int );         // Insert key into s1  
  
   // A set accepts key_types or value_types as elements  
   cout << "The set has elements:";  
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++)  
      cout << " " << *s1_Iter;  
   cout << "." << endl;  
}  
```  
  
```Output  
The set has elements: 10 20.  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<set>](../standard-library/set.md)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)


