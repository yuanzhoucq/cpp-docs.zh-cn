---
title: vector 类
ms.date: 11/04/2016
f1_keywords:
- vector/std::vector::allocator_type
- vector/std::vector::const_iterator
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::const_reverse_iterator
- vector/std::vector::difference_type
- vector/std::vector::iterator
- vector/std::vector::pointer
- vector/std::vector::reference
- vector/std::vector::reverse_iterator
- vector/std::vector::size_type
- vector/std::vector::value_type
- vector/std::vector::assign
- vector/std::vector::at
- vector/std::vector::back
- vector/std::vector::begin
- vector/std::vector::capacity
- vector/std::vector::cbegin
- vector/std::vector::cend
- vector/std::vector::crbegin
- vector/std::vector::crend
- vector/std::vector::clear
- vector/std::vector::data
- vector/std::vector::emplace
- vector/std::vector::emplace_back
- vector/std::vector::empty
- vector/std::vector::end
- vector/std::vector::erase
- vector/std::vector::front
- vector/std::vector::get_allocator
- vector/std::vector::insert
- vector/std::vector::max_size
- vector/std::vector::pop_back
- vector/std::vector::push_back
- vector/std::vector::rbegin
- vector/std::vector::rend
- vector/std::vector::reserve
- vector/std::vector::resize
- vector/std::vector::shrink_to_fit
- vector/std::vector::size
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], allocator_type
- std::vector [C++], const_iterator
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], const_reverse_iterator
- std::vector [C++], difference_type
- std::vector [C++], iterator
- std::vector [C++], pointer
- std::vector [C++], reference
- std::vector [C++], reverse_iterator
- std::vector [C++], size_type
- std::vector [C++], value_type
- std::vector [C++], assign
- std::vector [C++], at
- std::vector [C++], back
- std::vector [C++], begin
- std::vector [C++], capacity
- std::vector [C++], cbegin
- std::vector [C++], cend
- std::vector [C++], crbegin
- std::vector [C++], crend
- std::vector [C++], clear
- std::vector [C++], data
- std::vector [C++], emplace
- std::vector [C++], emplace_back
- std::vector [C++], empty
- std::vector [C++], end
- std::vector [C++], erase
- std::vector [C++], front
- std::vector [C++], get_allocator
- std::vector [C++], insert
- std::vector [C++], max_size
- std::vector [C++], pop_back
- std::vector [C++], push_back
- std::vector [C++], rbegin
- std::vector [C++], rend
- std::vector [C++], reserve
- std::vector [C++], resize
- std::vector [C++], shrink_to_fit
- std::vector [C++], size
- std::vector [C++], swap
ms.assetid: a3e0a8f8-7565-4fe0-93e4-e4d74ae1b70d
ms.openlocfilehash: 501f6547378b5461fe314410f54a6cc7d64c1221
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583356"
---
# <a name="vector-class"></a>vector 类

C++ 标准库 vector 类是序列容器的一个模板类，这些容器将给定类型的元素以线性排列方式进行排列，并且允许快速随机访问任何元素。 它们应是随机访问性能最佳时的首选序列容器。

## <a name="syntax"></a>语法

```cpp
template <class Type, class Allocator = allocator<Type>>
class vector
```

### <a name="parameters"></a>参数

*Type*<br/>
要存储在矢量中的元素数据类型

*分配器*<br/>
表示所存储分配器对象的类型，该分配器对象封装有关矢量的内存分配和解除分配的详细信息。 此参数为可选参数，默认值为 `allocator<Type>`。

## <a name="remarks"></a>备注

向量允许在序列末尾插入和删除常量事件。 若要在矢量中间插入或删除元素，则需要线性时间。 就在序列开头和末尾进行插入和删除而言，[deque 类](../standard-library/deque-class.md)容器的性能更胜一筹。 就在序列任何位置进行插入和删除而言，[list 类](../standard-library/list-class.md)容器更胜一筹。

当成员函数必须将矢量对象中所含序列增加到超过其当前存储容量时，将进行矢量重新分配。 其他的插入和删除均可能改变序列中的各个存储地址。 在所有此类情况下，指向序列更改部分的迭代器或引用将变为无效。 如果未进行重新分配，则只有插入/删除点前的迭代器和引用保持有效。

[vector\<bool> 类](../standard-library/vector-bool-class.md)是一种模板类矢量的完全专用化，针对类型 bool 的元素，且带有专用化所使用的基础类型的分配器。

[vector\<bool> reference 类](../standard-library/vector-bool-class.md#reference_class)是一个嵌套类，其对象能够提供对 vector\<bool> 对象内的元素（单个位）的引用。

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[vector](#vector)|构造一个向量，它具有特定大小、具有特定值的元素、具有特定 `allocator`，或将其构造成某个其它向量的副本。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[allocator_type](#allocator_type)|一个类型，它表示矢量对象的 `allocator` 类。|
|[const_iterator](#const_iterator)|一个类型，它提供可读取矢量中 **const** 元素的随机访问迭代器。|
|[const_pointer](#const_pointer)|一个类型，它提供指向矢量中 **const** 元素的指针。|
|[const_reference](#const_reference)|一种类型，此类型提供对用于读取和执行 **const** 操作的矢量中存储的 **const** 元素的引用。|
|[const_reverse_iterator](#const_reverse_iterator)|一个类型，它提供可读取矢量中任何 **const** 元素的随机访问迭代器。|
|[difference_type](#difference_type)|一个类型，它提供矢量中两个元素的址间的差异。|
|[Iterator](#iterator)|一个类型，它提供可读取或修改向量中任何元素的随机访问迭代器。|
|[pointer](#pointer)|一个类型，提供指向向量中元素的指针。|
|[reference](#reference)|一个类型，它提供对向量中存储的元素的引用。|
|[reverse_iterator](#reverse_iterator)|一个类型，它提供可读取或修改反向矢量中的任意元素的随机访问迭代器。|
|[size_type](#size_type)|一个类型，它计算矢量中的元素数目。|
|[value_type](#value_type)|一个类型，它代表向量中存储的数据类型。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[assign](#assign)|清除矢量并将指定的元素复制到该空矢量。|
|[at](#at)|返回对矢量中指定位置的元素的引用。|
|[back](#back)|返回对向量中最后一个元素的引用。|
|[begin](#begin)|对该向量中第一个元素返回随机访问迭代器。|
|[capacity](#capacity)|返回在不分配更多的存储的情况下向量可以包含的元素数。|
|[cbegin](#cbegin)|返回指向向量中第一个元素的随机访问常量迭代器。|
|[cend](#cend)|返回一个随机访问常量迭代器，它指向刚超过矢量末尾的位置。|
|[crbegin](#crbegin)|返回一个指向反向矢量中第一个元素的常量迭代器。|
|[crend](#crend)|返回一个指向反向矢量末尾的常量迭代器。|
|[clear](#clear)|清除向量的元素。|
|[data](#data)|返回指向向量中第一个元素的指针。|
|[emplace](#emplace)|将就地构造的元素插入到指定位置的向量中。|
|[emplace_back](#emplace_back)|将一个就地构造的元素添加到向量末尾。|
|[empty](#empty)|测试矢量容器是否为空。|
|[end](#end)|返回指向矢量末尾的随机访问迭代器。|
|[erase](#erase)|从指定位置删除向量中的一个元素或一系列元素。|
|[front](#front)|返回对向量中第一个元素的引用。|
|[get_allocator](#get_allocator)|将对象返回到矢量使用的 `allocator` 类。|
|[insert](#insert)|将一个元素或多个元素插入到指定位置的向量中。|
|[max_size](#max_size)|返回向量的最大长度。|
|[pop_back](#pop_back)|删除矢量末尾处的元素。|
|[push_back](#push_back)|在矢量末尾处添加一个元素。|
|[rbegin](#rbegin)|返回指向反向向量中第一个元素的迭代器。|
|[rend](#rend)|返回一个指向反向矢量末尾的迭代器。|
|[reserve](#reserve)|保留向量对象的最小存储长度。|
|[resize](#resize)|为矢量指定新的大小。|
|[shrink_to_fit](#shrink_to_fit)|放弃额外容量。|
|[size](#size)|返回向量中的元素数量。|
|[swap](#swap)|交换两个向量的元素。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator[]](#op_at)|返回对指定位置的矢量元素的引用。|
|[operator=](#op_eq)|用另一个向量的副本替换该向量中的元素。|

## <a name="requirements"></a>要求

**标头：**\<vector>

**命名空间：** std

## <a name="allocator_type"></a>vector::allocator_type

一个类型，它代表向量对象的分配器类。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>备注

`allocator_type` 是模板参数 `Allocator` 的同义词。

### <a name="example"></a>示例

有关使用 `allocator_type` 的示例，请参阅 [get_allocator](#get_allocator) 的示例。

## <a name="assign"></a>vector::assign

清除矢量并将指定的元素复制到该空矢量。

```cpp
void assign(size_type Count, const Type& Val);
void assign(initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>参数

*第一个*<br/>
要复制的元素范围内的第一个元素的位置。

*最后一个*<br/>
要复制的元素范围外的第一个元素的位置。

“计数”<br/>
要插入到矢量的元素的副本数。

*val*<br/>
插入到向量中的元素的值。

*IList*<br/>
包含要插入的元素的 initializer_list。

### <a name="remarks"></a>备注

清除向量中的任何现有元素后，将原始向量中指定范围的值插入向量或将新元素或指定值的副本插入向量。

### <a name="example"></a>示例

```cpp
/ vector_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2, v3;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(30);
    v1.push_back(40);
    v1.push_back(50);

    cout << "v1 = ";
    for (auto& v : v1){
        cout << v << " ";
    }
    cout << endl;

    v2.assign(v1.begin(), v1.end());
    cout << "v2 = ";
    for (auto& v : v2){
        cout << v << " ";
    }
    cout << endl;

    v3.assign(7, 4);
    cout << "v3 = ";
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;

    v3.assign({ 5, 6, 7 });
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;
}

```

## <a name="at"></a>vector::at

返回对矢量中指定位置的元素的引用。

```cpp
reference at(size_type _Pos);

const_reference at(size_type _Pos) const;
```

### <a name="parameters"></a>参数

*_Pos*<br/>
要在矢量中引用的元素的下标或位置编号。

### <a name="return-value"></a>返回值

对自变量中的下标元素的引用。 如果`_Off`向量的大小大于`at`将引发异常。

### <a name="remarks"></a>备注

如果将 `at` 的返回值分配给 `const_reference`，则无法修改矢量对象。 如果将 `at` 的返回值分配给 `reference`，则可以修改矢量对象。

### <a name="example"></a>示例

```cpp
// vector_at.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const int &i = v1.at( 0 );
   int &j = v1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a>vector::back

返回对向量中最后一个元素的引用。

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>返回值

向量的最后一个元素。 如果向量为空，则返回值不确定。

### <a name="remarks"></a>备注

如果将 `back` 的返回值分配给 `const_reference`，则无法修改矢量对象。 如果将 `back` 的返回值分配给 `reference`，则可以修改矢量对象。

当使用定义为 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 进行编译时，如果试图访问空矢量中的元素，将发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md) 。

### <a name="example"></a>示例

```cpp
// vector_back.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.back( );
   const int& ii = v1.front( );

   cout << "The last integer of v1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of v1 is "<< ii << endl;
}
```

## <a name="begin"></a>vector::begin

对该向量中第一个元素返回随机访问迭代器。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>返回值

发现 `vector` 中第一个元素或空 `vector` 之后的位置的随机访问迭代器。 应始终将返回的值与 [vector::end](#end) 进行比较以确保其有效。

### <a name="remarks"></a>备注

如果将 `begin` 的返回值分配给 [vector::const_iterator](#const_iterator)，则无法修改 `vector` 对象。 如果将 `begin` 的返回值分配给 [vector::iterator](#iterator)，则无法修改 `vector` 对象。

### <a name="example"></a>示例

```cpp
// vector_begin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::iterator c1_Iter;
    vector<int>::const_iterator c1_cIter;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_Iter = c1.begin();
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_Iter = c1.begin();
    *c1_Iter = 20;
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    // The following line would be an error because iterator is const
    // *c1_cIter = 200;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="capacity"></a>vector::capacity

返回在不分配更多的存储的情况下向量可以包含的元素数。

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>返回值

分配给该向量的当前存储长度。

### <a name="remarks"></a>备注

如果为成员函数 [resize](#resize) 分配了足够的内存，它将更高效。 使用成员函数 [reserve](#reserve) 指定分配的内存量。

### <a name="example"></a>示例

```cpp
// vector_capacity.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 1 );
   cout << "The length of storage allocated is "
        << v1.capacity( ) << "." << endl;

   v1.push_back( 2 );
   cout << "The length of storage allocated is now "
        << v1.capacity( ) << "." << endl;
}
```

```Output
The length of storage allocated is 1.
The length of storage allocated is now 2.
```

## <a name="cbegin"></a>vector::cbegin

返回**const**的范围中的第一个元素的迭代器。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>返回值

一个**const**指向的范围或刚超出空范围末尾的位置的第一个元素的随机访问迭代器 (对于空范围， `cbegin() == cend()`)。

### <a name="remarks"></a>备注

由于使用 `cbegin` 的返回值，因此不能修改范围中的元素。

可以使用此成员函数替代 `begin()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在示例中，请考虑`Container`的可修改 (非**const**) 的任何类型的支持的容器`begin()`和`cbegin()`。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>vector::cend

返回**const**刚超出范围中的最后一个元素的位置的迭代器。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>返回值

一个**const**指向刚超出范围末尾的随机访问迭代器。

### <a name="remarks"></a>备注

`cend` 用于测试迭代器是否超过了其范围的末尾。

可以使用此成员函数替代 `end()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在示例中，请考虑`Container`的可修改 (非**const**) 的任何类型的支持的容器`end()`和`cend()`。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

不应对 `cend` 返回的值取消引用。

## <a name="clear"></a>vector::clear

清除向量的元素。

```cpp
void clear();
```

### <a name="example"></a>示例

```cpp
// vector_clear.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "The size of v1 is " << v1.size( ) << endl;
   v1.clear( );
   cout << "The size of v1 after clearing is " << v1.size( ) << endl;
}
```

```Output
The size of v1 is 3
The size of v1 after clearing is 0
```

## <a name="const_iterator"></a>vector::const_iterator

一个类型，它提供可读取矢量中 **const** 元素的随机访问迭代器。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>备注

`const_iterator` 类型不能用于修改元素的值。

### <a name="example"></a>示例

有关使用 `const_iterator` 的示例，请参阅 [back](#back) 的示例。

## <a name="const_pointer"></a>vector::const_pointer

一个类型，它提供指向矢量中 **const** 元素的指针。

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>备注

`const_pointer` 类型不能用于修改元素的值。

[iterator](#iterator) 更常用于访问矢量元素。

## <a name="const_reference"></a>vector::const_reference

一种类型，此类型提供对用于读取和执行 **const** 操作的矢量中存储的 **const** 元素的引用。

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>备注

`const_reference` 类型不能用于修改元素的值。

### <a name="example"></a>示例

```cpp
// vector_const_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const vector <int> v2 = v1;
   const int &i = v2.front( );
   const int &j = v2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as v2 is const
   // v2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a>vector::const_reverse_iterator

一个类型，它提供可读取矢量中任何 **const** 元素的随机访问迭代器。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>备注

`const_reverse_iterator` 类型无法修改元素的值，它用于反向循环访问矢量。

### <a name="example"></a>示例

有关如何声明和使用迭代器的示例，请参阅 [rbegin](#rbegin)。

## <a name="crbegin"></a>vector::crbegin

返回一个指向反向矢量中第一个元素的常量迭代器。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>返回值

发现反向[矢量](../standard-library/vector-class.md)中的第一个元素或发现曾是非反向 `vector` 中的最后一个元素的常量反向双向迭代器。

### <a name="remarks"></a>备注

返回值为 `crbegin` 时，无法修改 `vector` 对象。

### <a name="example"></a>示例

```cpp
// vector_crbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="crend"></a>vector::crend

返回一个常量迭代器，此迭代器用于发现反向矢量中最后一个元素之后的位置。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>返回值

用于寻址反向[矢量](../standard-library/vector-class.md)中最后一个元素之后的位置（非反向 `vector` 中第一个元素之前的位置）的常量反向随机存取迭代器。

### <a name="remarks"></a>备注

`crend` 用于反向 `vector`，正如 [vector::cend](#cend) 用于 `vector` 一样。

由于使用 `crend` 的返回值（适当递减），因此不能修改 `vector` 对象。

`crend` 可用于测试反向迭代器是否已到达其 `vector` 的末尾。

不应对 `crend` 返回的值取消引用。

### <a name="example"></a>示例

```cpp
// vector_crend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="data"></a>vector::data

返回指向向量中第一个元素的指针。

```cpp
const_pointer data() const;

pointer data();
```

### <a name="return-value"></a>返回值

一个指针，它指向[矢量](../standard-library/vector-class.md)中第一个元素或紧随空 `vector` 后的位置。

### <a name="example"></a>示例

```cpp
// vector_data.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::pointer c1 ptr;
    vector<int>::const_pointer c1_cPtr;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_cPtr = c1.data();
    for (size_t n = c1.size(); 0 < n; --n, c1_cPtr++)
    {
        cout << " " << *c1_cPtr;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1 ptr = c1.data();
    *c1 ptr = 20;
    for (size_t n = c1.size(); 0 < n; --n, c1 ptr++)
    {
        cout << " " << *c1 ptr;
    }
    cout << endl;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="difference_type"></a>vector::difference_type

一个类型，它提供引用同一向量中元素的两个迭代器之间的差异。

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>备注

`difference_type` 也可以被描述为两个指针之间的元素数，因为指向一个元素的指针包含其地址。

[iterator](#iterator) 更常用于访问矢量元素。

### <a name="example"></a>示例

```cpp
// vector_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <vector>
#include <algorithm>

int main( )
{
   using namespace std;

   vector <int> c1;
   vector <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   vector <int>::difference_type   df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a>vector::emplace

将就地构造的元素插入到指定位置的向量中。

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|*_Where*|[矢量](../standard-library/vector-class.md)中插入第一个元素的位置。|
|*val*|插入到 `vector` 中的元素的值。|

### <a name="return-value"></a>返回值

该函数将返回一个指向 `vector` 中新元素的插入位置的迭代器。

### <a name="remarks"></a>备注

任何插入操作都可能产生巨额费用，请参阅 [vector 类](../standard-library/vector-class.md)，了解有关 `vector` 性能的讨论。

### <a name="example"></a>示例

```cpp
// vector_emplace.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.emplace( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
vv1[0] = 10 20 30
```

## <a name="emplace_back"></a>vector::emplace_back

将一个就地构造的元素添加到向量末尾。

```cpp
template <class... Types>
void emplace_back(Types&&... _Args);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*_Args*|构造函数参数。 函数根据所提供的自变量来推断要调用的构造函数重载。|

### <a name="example"></a>示例

```cpp
#include <vector>
struct obj
{
   obj(int, double) {}
};

int main()
{
   std::vector<obj> v;
   v.emplace_back(1, 3.14); // obj in created in place in the vector
}

```

## <a name="empty"></a>vector::empty

测试矢量是否为空。

```cpp
bool empty() const;
```

### <a name="return-value"></a>返回值

如果矢量为空，则为 **true**；如果矢量不为空，则为 **false**。

### <a name="example"></a>示例

```cpp
// vector_empty.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );

   if ( v1.empty( ) )
      cout << "The vector is empty." << endl;
   else
      cout << "The vector is not empty." << endl;
}
```

```Output
The vector is not empty.
```

## <a name="end"></a>vector::end

返回超过末尾迭代器。

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>返回值

向量的超过末尾迭代器。 如果该向量为空，则 `vector::end() == vector::begin()`。

### <a name="remarks"></a>备注

如果返回值`end`分配给类型的变量的`const_iterator`，无法修改矢量对象。 如果返回值`end`分配给类型的变量的`iterator`，可以修改矢量对象。

### <a name="example"></a>示例

```cpp
// vector_end.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << endl;
}
```

```Output
1
2
```

## <a name="erase"></a>vector::erase

从指定位置删除向量中的一个元素或一系列元素。

```cpp
iterator erase(
    const_iterator _Where);

iterator erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|*_Where*|要从向量中移除的元素的位置。|
|*first*|要从向量中移除的第一个元素的位置。|
|*最后一个*|紧接要从向量中移除的最后一个元素的位置。|

### <a name="return-value"></a>返回值

一个迭代器，它指定已移除的任何元素之外保留的第一个元素或指向向量末尾的指针（若此类元素不存在）。

### <a name="example"></a>示例

```cpp
// vector_erase.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );
   v1.push_back( 40 );
   v1.push_back( 50 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) + 1, v1.begin( ) + 3 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
v1 = 10 20 30 40 50
v1 = 20 30 40 50
v1 = 20 50
```

## <a name="front"></a>vector::front

返回对向量中第一个元素的引用。

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>返回值

对向量对象中第一个元素的引用。 如果向量为空，则返回值不确定。

### <a name="remarks"></a>备注

如果将 `front` 的返回值分配给 `const_reference`，则无法修改矢量对象。 如果将 `front` 的返回值分配给 **reference**，则可以修改矢量对象。

当使用定义为 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 进行编译时，如果试图访问空矢量中的元素，将发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md) 。

### <a name="example"></a>示例

```cpp
// vector_front.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.front( );
   const int& ii = v1.front( );

   cout << "The first integer of v1 is "<< i << endl;
   // by incrementing i, we move the front reference to the second element
   i++;
   cout << "Now, the first integer of v1 is "<< i << endl;
}
```

## <a name="get_allocator"></a>vector::get_allocator

返回用于构造矢量的分配器对象的一个副本。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>返回值

向量所使用的分配器。

### <a name="remarks"></a>备注

矢量类的分配器指定类管理存储的方式。 C++ 标准库容器类提供的默认分配器足以满足大多编程需求。 编写和使用你自己的分配器类是高级 C++ 主题。

### <a name="example"></a>示例

```cpp
// vector_get_allocator.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   vector<int> v1;
   vector<int, allocator<int> > v2 = vector<int, allocator<int> >(allocator<int>( )) ;

   // v3 will use the same allocator class as v1
   vector <int> v3( v1.get_allocator( ) );

   vector<int>::allocator_type xvec = v3.get_allocator( );
   // You can now call functions on the allocator class used by vec
}
```

## <a name="insert"></a>vector::insert

将一个、多个或一系列元素插入到指定位置的向量中。

```cpp
iterator insert(
    const_iterator _Where,
    const Type& val);

iterator insert(
    const_iterator _Where,
    Type&& val);

void insert(
    const_iterator _Where,
    size_type count,
    const Type& val);

template <class InputIterator>
void insert(
    const_iterator _Where,
    InputIterator first,
    InputIterator last);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|*_Where*|向量中插入第一个元素的位置。|
|*val*|插入到向量中的元素的值。|
|*count*|插入向量中的元素数目。|
|*first*|要复制的范围元素中的第一个元素的位置。|
|*最后一个*|要复制的元素范围以外的第一个元素的位置。|

### <a name="return-value"></a>返回值

前两个 `insert` 函数返回一个指定新元素插入到向量的位置的迭代器。

### <a name="remarks"></a>备注

前提是，*第一个*并*最后一个*不能向量中的迭代器或该行为不确定。 任何插入操作都可能产生巨额费用，请参阅 [vector 类](../standard-library/vector-class.md)，了解有关 `vector` 性能的讨论。

### <a name="example"></a>示例

```cpp
// vector_insert.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.insert( v1.begin( ) + 1, 40 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
   v1.insert( v1.begin( ) + 2, 4, 50 );

   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.insert( v1.begin( )+1, v1.begin( )+2, v1.begin( )+4 );
   cout << "v1 =";
   for (Iter = v1.begin( ); Iter != v1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.insert( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      vector < vector <int> >::iterator Iter;
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
v1 = 10 40 20 30
v1 = 10 40 50 50 50 50 20 30
v1 = 10 50 50 40 50 50 50 50 20 30
vv1[0] = 10 50 50 40 50 50 50 50 20 30
```

## <a name="iterator"></a>vector::iterator

一个类型，它提供可读取或修改向量中任何元素的随机访问迭代器。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>备注

**iterator** 类型可用于修改元素的值。

### <a name="example"></a>示例

请参阅 [begin](#begin) 的示例。

## <a name="max_size"></a>vector::max_size

返回向量的最大长度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>返回值

向量的最大可取长度。

### <a name="example"></a>示例

```cpp
// vector_max_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   i = v1.max_size( );
   cout << "The maximum possible length of the vector is " << i << "." << endl;
}
```

## <a name="op_at"></a>vector::operator[]

返回对指定位置的矢量元素的引用。

```cpp
reference operator[](size_type Pos);

const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|*pos*|矢量元素的位置。|

### <a name="return-value"></a>返回值

如果指定的位置大于或等于容器大小，则结果为 undefined。

### <a name="remarks"></a>备注

如果将 `operator[]` 的返回值分配给 `const_reference`，则无法修改矢量对象。 如果将 `operator[]` 的返回值分配给引用，则可以修改矢量对象。

当使用定义为 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 进行编译时，如果试图访问矢量边界之外的元素，将发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md) 。

### <a name="example"></a>示例

```cpp
// vector_op_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   int& i = v1[1];
   cout << "The second integer of v1 is " << i << endl;
}
```

## <a name="op_eq"></a>vector::operator=

用另一个向量的副本替换该向量中的元素。

```cpp
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|*right*|要复制到 `vector` 中的[矢量](../standard-library/vector-class.md)。|

### <a name="remarks"></a>备注

在清除中的任何现有元素后`vector`，`operator=`复制或移动的内容*右*到`vector`。

### <a name="example"></a>示例

```cpp
// vector_operator_as.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> v1, v2, v3;
   vector<int>::iterator iter;

   v1.push_back(10);
   v1.push_back(20);
   v1.push_back(30);
   v1.push_back(40);
   v1.push_back(50);

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

## <a name="pointer"></a>vector::pointer

一个类型，提供指向向量中元素的指针。

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>备注

**pointer** 类型可用于修改元素的值。

### <a name="example"></a>示例

```cpp
// vector_pointer.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
    using namespace std;
    vector<int> v;
    v.push_back( 11 );
    v.push_back( 22 );

    vector<int>::pointer ptr = &v[0];
    cout << *ptr << endl;
    ptr++;
    cout << *ptr << endl;
    *ptr = 44;
    cout << *ptr << endl;
}
```

```Output
11
22
44
```

## <a name="pop_back"></a>vector::pop_back

删除矢量末尾处的元素。

```cpp
void pop_back();
```

### <a name="remarks"></a>备注

有关代码示例，请参阅 [vector::push_back()](#push_back)。

## <a name="push_back"></a>vector::push_back

在矢量末尾处添加一个元素。

```cpp
void push_back(const T& Val);

void push_back(T&& Val);
```

### <a name="parameters"></a>参数

*val*<br/>
要赋给添加到矢量末尾处的元素的值。

### <a name="example"></a>示例

```cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << "  " << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

int main()
{
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(10 + i);
    }

    cout << "vector data: " << endl;
    print_collection(v);

    // pop_back() until it's empty, printing the last element as we go
    while (v.begin() != v.end()) {
        cout << "v.back(): "; print_elem(v.back()); cout << endl;
        v.pop_back();
    }
}
```

## <a name="rbegin"></a>vector::rbegin

返回指向反向向量中第一个元素的迭代器。

```cpp
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>返回值

发现反向矢量中的第一个元素或发现曾是非反向矢量中的最后一个元素的反向双向迭代器。

### <a name="remarks"></a>备注

如果将 `rbegin` 的返回值分配给 `const_reverse_iterator`，则无法修改矢量对象。 如果将 `rbegin` 的返回值分配给 `reverse_iterator`，则可以修改矢量对象。

### <a name="example"></a>示例

```cpp
// vector_rbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.rbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="reference"></a>vector::reference

一个类型，它提供对向量中存储的元素的引用。

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>示例

有关如何使用矢量类中的 **reference** 的示例，请参阅 [at](#at)。

## <a name="rend"></a>vector::rend

返回一个迭代器，此迭代器用于发现反向矢量中最后一个元素之后的位置。

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>返回值

用于发现反向矢量中最后一个元素之后的位置（非反向矢量中第一个元素之前的位置）的反向随机访问迭代器。

### <a name="remarks"></a>备注

`rend` 用于反向矢量，正如 [end](#end) 用于矢量一样。

如果将 `rend` 的返回值分配给 `const_reverse_iterator`，则无法修改矢量对象。 如果将 `rend` 的返回值分配给 `reverse_iterator`，则可以修改矢量对象。

`rend` 可用于测试反向迭代器是否已到达其矢量末尾。

不应对 `rend` 返回的值取消引用。

### <a name="example"></a>示例

```cpp
// vector_rend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="reserve"></a>vector::reserve

为向量对象保留最小的存储长度，必要时为其分配空间。

```cpp
void reserve(size_type count);
```

### <a name="parameters"></a>参数

*count*<br/>
要分配给向量的最小存储长度。

### <a name="example"></a>示例

```cpp
// vector_reserve.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
```

## <a name="resize"></a>vector::resize

为矢量指定新的大小。

```cpp
void resize(size_type Newsize);
void resize(size_type Newsize, Type Val);
```

### <a name="parameters"></a>参数

*Newsize*<br/>
矢量的新大小。

*val*<br/>
新大小大于旧大小时添加至矢量的新元素的初始化值。 如果省略该值，则新对象将使用其默认构造函数。

### <a name="remarks"></a>备注

如果容器的大小小于请求的大小*Newsize*，元素添加到矢量，直到它达到请求的大小。 如果容器的大小大于请求的大小，最接近容器末尾的元素将被删除之前该容器达到大小*Newsize*。 如果容器的当前大小与请求的大小相同，则不采取任何操作。

[size](#size) 表示矢量的当前大小。

### <a name="example"></a>示例

```cpp
// vectorsizing.cpp
// compile with: /EHsc /W4
// Illustrates vector::reserve, vector::max_size,
// vector::resize, vector::resize, and vector::capacity.
//
// Functions:
//
//    vector::max_size - Returns maximum number of elements vector could
//                       hold.
//
//    vector::capacity - Returns number of elements for which memory has
//                       been allocated.
//
//    vector::size - Returns number of elements in the vector.
//
//    vector::resize - Reallocates memory for vector, preserves its
//                     contents if new size is larger than existing size.
//
//    vector::reserve - Allocates elements for vector to ensure a minimum
//                      size, preserving its contents if the new size is
//                      larger than existing size.
//
//    vector::push_back - Appends (inserts) an element to the end of a
//                        vector, allocating memory for it if necessary.
//
//////////////////////////////////////////////////////////////////////

// The debugger cannot handle symbols more than 255 characters long.
// The C++ Standard Library often creates symbols longer than that.
// The warning can be disabled:
//#pragma warning(disable:4786)

#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }
    cout << endl;
}

void printvstats(const vector<int>& v) {
    cout << "   the vector's size is: " << v.size() << endl;
    cout << "   the vector's capacity is: " << v.capacity() << endl;
    cout << "   the vector's maximum size is: " << v.max_size() << endl;
}

int main()
{
    // declare a vector that begins with 0 elements.
    vector<int> v;

    // Show statistics about vector.
    cout << endl << "After declaring an empty vector:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Add one element to the end of the vector.
    v.push_back(-1);
    cout << endl << "After adding an element:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }
    cout << endl << "After adding 10 elements:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(6);
    cout << endl << "After resizing to 6 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(9, 999);
    cout << endl << "After resizing to 9 elements with an initialization value of 999:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(12);
    cout << endl << "After resizing to 12 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Ensure there's room for at least 1000 elements.
    v.reserve(1000);
    cout << endl << "After vector::reserve(1000):" << endl;
    printvstats(v);

    // Ensure there's room for at least 2000 elements.
    v.resize(2000);
    cout << endl << "After vector::resize(2000):" << endl;
    printvstats(v);
}
```

## <a name="reverse_iterator"></a>vector::reverse_iterator

一个类型，它提供可读取或修改反向矢量中的任意元素的随机访问迭代器。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>备注

`reverse_iterator` 类型用于反向循环访问向量。

### <a name="example"></a>示例

请参阅 [rbegin](#rbegin) 的示例。

## <a name="shrink_to_fit"></a>vector::shrink_to_fit

放弃额外容量。

```cpp
void shrink_to_fit();
```

### <a name="example"></a>示例

```cpp
// vector_shrink_to_fit.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.shrink_to_fit();
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
Current capacity of v1 = 1
```

## <a name="size"></a>vector::size

返回向量中的元素数量。

```cpp
size_type size() const;
```

### <a name="return-value"></a>返回值

向量的当前长度。

### <a name="example"></a>示例

```cpp
// vector_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   v1.push_back( 1 );
   i = v1.size( );
   cout << "Vector length is " << i << "." << endl;

   v1.push_back( 2 );
   i = v1.size( );
   cout << "Vector length is now " << i << "." << endl;
}
```

```Output
Vector length is 1.
Vector length is now 2.
```

## <a name="size_type"></a>vector::size_type

一个类型，它计算矢量中的元素数目。

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>示例

请参阅 [capacity](#capacity) 的示例。

## <a name="swap"></a>vector::swap

交换两个向量的元素。

```cpp
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*right*<br/>
一个向量，提供要交换的元素或其元素将要与向量的交换的向量*左*。

*left*<br/>
其元素将要与向量的交换的向量*右*。

### <a name="example"></a>示例

```cpp
// vector_swap.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1, v2;

   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 3 );

   v2.push_back( 10 );
   v2.push_back( 20 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
   cout << endl;

   v1.swap( v2 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
}
```

```Output
The number of elements in v1 = 3
The number of elements in v2 = 2

The number of elements in v1 = 2
The number of elements in v2 = 3
```

## <a name="value_type"></a>vector::value_type

一个类型，它代表向量中存储的数据类型。

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>备注

`value_type` 是模板参数 `Type` 的同义词。

### <a name="example"></a>示例

```cpp
// vector_value_type.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="vector"></a>vector::vector

构造一个具有以下特性的矢量：特定大小、特定值的元素、特定分配器或作为其他矢量的全部或部分副本。

```cpp
vector();
explicit vector(const Allocator& Al);
explicit vector(size_type Count);
vector(size_type Count, const Type& Val);
vector(size_type Count, const Type& Val, const Allocator& Al);

vector(const vector& Right);
vector(vector&& Right);
vector(initializer_list<Type> IList, const _Allocator& Al);

template <class InputIterator>
vector(InputIterator First, InputIterator Last);
template <class InputIterator>
vector(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|*Al*|要用于此对象的分配器类。 [get_allocator](#get_allocator) 返回对象的分配器类。|
|“计数”|构造的矢量中的元素数。|
|*val*|构造的矢量中的元素值。|
|右侧|要成为副本的构造的矢量中的矢量。|
|*第一个*|要复制的元素范围内的第一个元素的位置。|
|*最后一个*|要复制的元素范围外的第一个元素的位置。|
|*IList*|包含要复制的元素的 initializer_list。|

### <a name="remarks"></a>备注

所有构造函数存储一个分配器对象 (*Al*) 并初始化此矢量。

前两个构造函数指定一个空初始矢量。 第二个显式指定的分配器类型 (*Al*) 使用。

第三个构造函数指定指定数目的重复项 (*计数*) 的类的默认值的元素`Type`。

第四个和第五个构造函数指定的重复项 (*计数*) 值的元素*Val*。

第六个构造函数指定向量的副本*右*。

第七个构造函数移动矢量*右*。

第八个构造函数使用 initializer_list 指定元素。

第九个和第十个构造函数复制矢量的范围（`First`、`Last`）。

### <a name="example"></a>示例

```cpp
// vector_ctor.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector <int>::iterator v1_Iter, v2_Iter, v3_Iter, v4_Iter, v5_Iter, v6_Iter;

    // Create an empty vector v0
    vector <int> v0;

    // Create a vector v1 with 3 elements of default value 0
    vector <int> v1(3);

    // Create a vector v2 with 5 elements of value 2
    vector <int> v2(5, 2);

    // Create a vector v3 with 3 elements of value 1 and with the allocator
    // of vector v2
    vector <int> v3(3, 1, v2.get_allocator());

    // Create a copy, vector v4, of vector v2
    vector <int> v4(v2);

    // Create a new temporary vector for demonstrating copying ranges
    vector <int> v5(5);
    for (auto i : v5) {
        v5[i] = i;
    }

    // Create a vector v6 by copying the range v5[ first,  last)
    vector <int> v6(v5.begin() + 1, v5.begin() + 3);

    cout << "v1 =";
    for (auto& v : v1){
        cout << " " << v;
    }
    cout << endl;

    cout << "v2 =";
    for (auto& v : v2){
        cout << " " << v;
    }
    cout << endl;

    cout << "v3 =";
    for (auto& v : v3){
        cout << " " << v;
    }
    cout << endl;
    cout << "v4 =";
    for (auto& v : v4){
        cout << " " << v;
    }
    cout << endl;

    cout << "v5 =";
    for (auto& v : v5){
        cout << " " << v;
    }
    cout << endl;

    cout << "v6 =";
    for (auto& v : v6){
        cout << " " << v;
    }
    cout << endl;

    // Move vector v2 to vector v7
    vector <int> v7(move(v2));
    vector <int>::iterator v7_Iter;

    cout << "v7 =";
    for (auto& v : v7){
        cout << " " << v;
    }
    cout << endl;

    vector<int> v8{ { 1, 2, 3, 4 } };
    for (auto& v : v8){
        cout << " " << v ;
    }
    cout << endl;
}

```

```Output
v1 = 0 0 0v2 = 2 2 2 2 2v3 = 1 1 1v4 = 2 2 2 2 2v5 = 0 1 2 3 4v6 = 1 2v7 = 2 2 2 2 21 2 3 4
```

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
