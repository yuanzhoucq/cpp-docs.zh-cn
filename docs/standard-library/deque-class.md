---
title: deque 类
ms.date: 11/04/2016
f1_keywords:
- deque/std::deque
- deque/std::deque::allocator_type
- deque/std::deque::const_iterator
- deque/std::deque::const_pointer
- deque/std::deque::const_reference
- deque/std::deque::const_reverse_iterator
- deque/std::deque::difference_type
- deque/std::deque::iterator
- deque/std::deque::pointer
- deque/std::deque::reference
- deque/std::deque::reverse_iterator
- deque/std::deque::size_type
- deque/std::deque::value_type
- deque/std::deque::assign
- deque/std::deque::at
- deque/std::deque::back
- deque/std::deque::begin
- deque/std::deque::cbegin
- deque/std::deque::cend
- deque/std::deque::clear
- deque/std::deque::crbegin
- deque/std::deque::crend
- deque/std::deque::emplace
- deque/std::deque::emplace_back
- deque/std::deque::emplace_front
- deque/std::deque::empty
- deque/std::deque::end
- deque/std::deque::erase
- deque/std::deque::front
- deque/std::deque::get_allocator
- deque/std::deque::insert
- deque/std::deque::max_size
- deque/std::deque::pop_back
- deque/std::deque::pop_front
- deque/std::deque::push_back
- deque/std::deque::push_front
- deque/std::deque::rbegin
- deque/std::deque::rend
- deque/std::deque::resize
- deque/std::deque::shrink_to_fit
- deque/std::deque::size
- deque/std::deque::swap
helpviewer_keywords:
- std::deque [C++]
- std::deque [C++], allocator_type
- std::deque [C++], const_iterator
- std::deque [C++], const_pointer
- std::deque [C++], const_reference
- std::deque [C++], const_reverse_iterator
- std::deque [C++], difference_type
- std::deque [C++], iterator
- std::deque [C++], pointer
- std::deque [C++], reference
- std::deque [C++], reverse_iterator
- std::deque [C++], size_type
- std::deque [C++], value_type
- std::deque [C++], assign
- std::deque [C++], at
- std::deque [C++], back
- std::deque [C++], begin
- std::deque [C++], cbegin
- std::deque [C++], cend
- std::deque [C++], clear
- std::deque [C++], crbegin
- std::deque [C++], crend
- std::deque [C++], emplace
- std::deque [C++], emplace_back
- std::deque [C++], emplace_front
- std::deque [C++], empty
- std::deque [C++], end
- std::deque [C++], erase
- std::deque [C++], front
- std::deque [C++], get_allocator
- std::deque [C++], insert
- std::deque [C++], max_size
- std::deque [C++], pop_back
- std::deque [C++], pop_front
- std::deque [C++], push_back
- std::deque [C++], push_front
- std::deque [C++], rbegin
- std::deque [C++], rend
- std::deque [C++], resize
- std::deque [C++], shrink_to_fit
- std::deque [C++], size
- std::deque [C++], swap
ms.assetid: 64842ee5-057a-4063-8c16-4267a0332584
ms.openlocfilehash: d78bbc6e66fe97af1049fa6976ac8c5fa806ef43
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424865"
---
# <a name="deque-class"></a>deque 类

对线性排列中给定类型的元素进行排序，并且类似于矢量，允许快速随机访问任何元素并在容器后面高效插入和删除。 但是，和矢量不同的是，`deque` 类还支持在容器前面高效插入和删除。

## <a name="syntax"></a>语法

```unstlib
template <class Type, class Allocator =allocator<Type>>
class deque
```

### <a name="parameters"></a>参数

*类型*\
要存储在 deque 中的元素数据类型。

*分配*器\
表示所存储分配器对象的类型，该分配器对象封装有关 deque 的内存分配和解除分配的详细信息。 此参数是可选的，默认值为**分配器\<类型 >** 。

## <a name="remarks"></a>备注

容器类型选择通常应根据应用程序所需的搜索和插入的类型。 当对任何元素的随机访问超出限制并且仅要求在序列的末尾插入或删除元素时，[矢量](../standard-library/vector-class.md)应作为用于管理序列的首选容器。 当在序列内任何位置的高效插入和删除（采用常量时间）超出限制时，list 容器的性能会很优异。 序列中间的此类操作需要元素副本和与序列中的元素数量成正比的分配（线性时间）。

当成员函数必须插入或清除序列中的元素时，将发生 deque 的重新分配：

- 如果元素插入到一个空序列中，或如果清除元素留下一个空序列，则之前由 [begin](#begin) 和 [end](#end) 返回的迭代器变为无效。

- 如果在 deque 的第一个位置插入一个元素，则所有指定现有元素的迭代器（但没有引用）将变为无效。

- 如果在 deque 的末尾插入一个元素，则 [end](#end) 和所有指定了现有元素的迭代器（但没有引用）将变为无效。

- 如果在 deque 的前面清除元素，只有该迭代器和对已清除元素的引用变得无效。

- 如果从 deque 的末尾清除最后一个元素，则仅指向最后一个元素的迭代器和对清除元素的引用将变为无效。

否则，插入或清除元素将使所有迭代器和引用失效。

## <a name="members"></a>Members

### <a name="constructors"></a>构造函数

|||
|-|-|
|[deque](#deque)|构造一个 `deque`。 提供了多个构造函数来以不同的方式设置新 `deque` 的内容：空;使用指定数量的空元素加载;从另一个 `deque`移动或复制的内容;使用迭代器复制或移动内容;和一个元素复制到 `deque` `count` 次。 一些构造函数可实现使用自定义 `allocator` 创建元素。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[allocator_type](#allocator_type)|一种类型，此类型表示 `allocator` 对象的 `deque` 类。|
|[const_iterator](#const_iterator)|一种类型，此类型提供可访问和读取 `deque` 中作为 `const` 的元素的随机访问迭代器|
|[const_pointer](#const_pointer)|一种类型，用于提供指向 `deque` 中作为 `const.` 的元素的指针|
|[const_reference](#const_reference)|一种类型，此类型提供对 `deque` 中作为 `const.` 用于读取和其他操作的元素的引用|
|[const_reverse_iterator](#const_reverse_iterator)|一种类型，它提供可访问和读取 `deque`**中的元素**的随机访问迭代器。 以相反顺序查看 deque。 有关详细信息，请参阅 [reverse_iterator 类](../standard-library/reverse-iterator-class.md)|
|[difference_type](#difference_type)|一种类型，该类型提供引用同一 `deque` 中的元素的两个随机访问迭代器之间的差异。|
|[迭代器](#iterator)|一种类型，此类型提供可读取或修改 `deque` 中的任何元素的随机访问迭代器。|
|[指针](#pointer)|一种类型，它提供指向 `deque` 中的某个元素的指针。|
|[reference](#reference)|一种类型，此类型提供对存储在 `deque` 中的元素的引用。|
|[reverse_iterator](#reverse_iterator)|一种类型，此类型提供可读取或修改 `deque` 中的某个元素的随机访问迭代器。 以相反顺序查看 deque。|
|[size_type](#size_type)|一种类型，此类型计算 `deque` 中的元素数目。|
|[value_type](#value_type)|一种类型，此类型表示存储在 `deque` 中的数据类型。|

### <a name="functions"></a>函数

|||
|-|-|
|[assign](#assign)|将元素从 `deque` 中清除并将新的元素序列复制到目标 `deque`。|
|[at](#at)|返回对 `deque` 中指定位置的元素的引用。|
|[back](#back)|返回对 `deque` 中最后一个元素的引用。|
|[begin](#begin)|返回发现 `deque` 中第一个元素的随机访问迭代器。|
|[cbegin](#cbegin)|返回一个指向 `deque` 中第一个元素的常量迭代器。|
|[cend](#cend)|返回一个随机访问**常量**迭代器，它指向刚超出 `deque`末尾的位置。|
|[clear](#clear)|清除 `deque` 的所有元素。|
|[crbegin](#crbegin)|返回一个指向以相反顺序查看的 `deque` 中的第一个元素的随机访问常量迭代器。|
|[crend](#crend)|返回一个指向以相反顺序查看的 `deque` 中的第一个元素的随机访问常量迭代器。|
|[emplace](#emplace)|将就地构造的元素插入到指定位置的 `deque` 中。|
|[emplace_back](#emplace_back)|将就地构造的元素添加到 `deque` 的末尾。|
|[emplace_front](#emplace_front)|将就地构造的元素添加到 `deque` 的开头。|
|[empty](#empty)|如果 `deque` 包含零个元素，则返回**true** ; 如果包含一个或多个元素，则返回**false** 。|
|[end](#end)|返回指向刚超出 `deque` 末尾位置的随机访问迭代器。|
|[erase](#erase)|从指定位置删除 `deque` 中一个或一系列元素。|
|[front](#front)|返回对 `deque` 中第一个元素的引用。|
|[get_allocator](#get_allocator)|返回用于构造 `allocator` 的 `deque` 对象的副本。|
|[insert](#insert)|将一个、多个或一系列元素插入到指定位置的 `deque` 中。|
|[max_size](#max_size)|返回 `deque` 的最大可取长度。|
|[pop_back](#pop_back)|清除 `deque` 末尾处的元素。|
|[pop_front](#pop_front)|清除 `deque` 开头处的元素。|
|[push_back](#push_back)|将元素添加到 `deque` 的末尾。|
|[push_front](#push_front)|将元素添加到 `deque` 的开头。|
|[rbegin](#rbegin)|返回指向反向 `deque` 中的第一个元素的随机访问迭代器。|
|[rend](#rend)|返回指向刚超出反向 `deque` 中的最后一个元素位置的随机访问迭代器。|
|[resize](#resize)|为 `deque` 指定新的大小。|
|[shrink_to_fit](#shrink_to_fit)|放弃额外容量。|
|[size](#size)|返回 `deque` 中的元素数量。|
|[swap](#swap)|交换两个 `deque` 的元素。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator[]](#op_at)|返回对指定位置的 `deque` 元素的引用。|
|[operator=](#op_eq)|将 `deque` 的元素替换为另一个 `deque` 的副本。|

## <a name="allocator_type"></a>allocator_type

一个类型，它代表 deque 对象的分配器类。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>备注

`allocator_type` 是模板参数 `Allocator` 的同义词。

### <a name="example"></a>示例

请参阅 [get_allocator](#get_allocator) 的示例。

## <a name="assign"></a>将

将元素从 deque 中擦除并将一组新的元素复制到目标 deque。

```cpp
template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);

void assign(
    size_type Count,
    const Type& Val);

void assign(initializer_list<Type> IList);
```

### <a name="parameters"></a>参数

*第一个*\
要从参数 deque 中复制的一系列元素中的第一个元素的位置。

*最后*\
超出要从自变量 deque 中复制的一系列元素范围的第一个元素的位置。

*计数*\
要插入 deque 中的元素副本数。

*Val*\
要插入 deque 中的元素的值。

*IList*\
要插入 deque 中的 initializer_list。

### <a name="remarks"></a>备注

清除 deque 中的任何现有元素后，`assign` 将原始列表或其他 deque 中的一系列指定的元素插入目标 deque 中，或将指定值的新元素副本插入目标 deque 中。

### <a name="example"></a>示例

```cpp
// deque_assign.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <initializer_list>

int main()
{
    using namespace std;
    deque <int> c1, c2;
    deque <int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    deque<int> d1{ 1, 2, 3, 4 };
    initializer_list<int> iList{ 5, 6, 7, 8 };
    d1.assign(iList);

    cout << "d1 = ";
    for (int i : d1)
        cout << i;
    cout << endl;

    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;
}
```

```Output
d1 = 5678c1 =102030c1 =5060c1 =4444444
```

## <a name="at"></a>最

返回对 deque 中指定位置的元素的引用。

```cpp
reference at(size_type pos);

const_reference at(size_type pos) const;
```

### <a name="parameters"></a>参数

*pos*\
要在 deque 中引用的元素的下标（或位置编号）。

### <a name="return-value"></a>返回值

如果*pos*大于 deque 的大小，`at` 会引发异常。

### <a name="return-value"></a>返回值

如果 `at` 的返回值赋给了 `const_reference`，则无法修改 deque 对象。 如果 `at` 的返回值赋给了 `reference`，则可以修改 deque 对象。

### <a name="example"></a>示例

```cpp
// deque_at.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int& i = c1.at( 0 );
   int& j = c1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a>返回

返回对 deque 中最后一个元素的引用。

```cpp
reference back();
const_reference back() const;
```

### <a name="return-value"></a>返回值

deque 的最后一个元素。 如果 deque 为空，则返回值不确定。

### <a name="remarks"></a>备注

如果 `back` 的返回值赋给了 `const_reference`，则无法修改 deque 对象。 如果 `back` 的返回值赋给了 `reference`，则可以修改 deque 对象。

当使用定义为 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 进行编译时，如果试图访问空 deque 中的元素，则将发生运行时错误。  有关更多信息，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>示例

```cpp
// deque_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a>准备

返回一个迭代器，此迭代器用于发现 deque 中第一个元素的位置。

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>返回值

一个随机访问迭代器，此迭代器用于发现 deque 中第一个元素的位置或空 deque 之后的位置。

### <a name="remarks"></a>备注

如果 `begin` 的返回值赋给了 `const_iterator`，则无法修改 deque 对象。 如果 `begin` 的返回值分配给某个 `iterator`，则可以修改 deque 对象。

### <a name="example"></a>示例

```cpp
// deque_begin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a> cbegin

返回一个**常量**迭代器，该迭代器用于寻址范围内的第一个元素。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>返回值

**常量**随机访问迭代器，指向范围的第一个元素，或刚超出空范围末尾的位置（对于空范围，则为 `cbegin() == cend()`）。

### <a name="remarks"></a>备注

由于使用 `cbegin` 的返回值，因此不能修改范围中的元素。

可以使用此成员函数替代 `begin()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在此示例中，将 `Container` 视为支持 `begin()` 和 `cbegin()` 的可修改的任何类型的（非- `const`）容器。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

返回一个**常量**迭代器，该迭代器用于寻址范围内最后一个元素之外的位置。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>返回值

指向刚超出范围末尾的位置的随机访问迭代器。

### <a name="remarks"></a>备注

`cend` 用于测试迭代器是否超过了其范围的末尾。

可以使用此成员函数替代 `end()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在此示例中，请考虑 `Container` 为支持 `end()` 和 `cend()`的任何类型的可修改（非常**量**）容器。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

不应对 `cend` 返回的值取消引用。

## <a name="clear"></a>清除

清除 deque 的所有元素。

```cpp
void clear();
```

### <a name="example"></a>示例

```cpp
// deque_clear.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the deque is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of the deque after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the deque is initially 3
The size of the deque after clearing is 0
```

## <a name="const_iterator"></a>const_iterator

提供可访问和读取 deque 中 **const** 元素的随机访问迭代器的类型。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>备注

`const_iterator` 类型不能用于修改元素的值。

### <a name="example"></a>示例

请参阅 [back](#back) 的示例。

## <a name="const_pointer"></a>const_pointer

提供指向 deque 中的**const**元素的指针。

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>备注

`const_pointer` 类型不能用于修改元素的值。 [iterator](#iterator) 更常用于访问 deque 元素。

## <a name="const_reference"></a>const_reference

一个类型，提供对存储于 deque 中供读取和执行 **const** 操作的 **const** 元素的引用。

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>备注

`const_reference` 类型不能用于修改元素的值。

### <a name="example"></a>示例

```cpp
// deque_const_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const deque <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a>const_reverse_iterator

一个类型，提供可读取 deque 中任何 **const** 元素的随机访问迭代器。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>备注

`const_reverse_iterator` 类型无法修改元素的值，它用于反向循环访问 deque。

### <a name="example"></a>示例

有关如何声明和使用迭代器的示例，请参阅 [rbegin](#rbegin) 的示例。

## <a name="crbegin"></a>crbegin

返回一个指向反向 deque 中第一个元素的常量迭代器。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>返回值

发现反向 [deque](../standard-library/deque-class.md) 中的第一个元素或发现曾是非反向 `deque` 中的最后一个元素的常量反向随机访问迭代器。

### <a name="remarks"></a>备注

返回值为 `crbegin` 时，无法修改 `deque` 对象。

### <a name="example"></a>示例

```cpp
// deque_crbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator v1_Iter;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of deque is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed deque is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of deque is 1.
The first element of the reversed deque is 2.
```

## <a name="crend"></a>crend

返回一个常量迭代器，此迭代器用于发现反向 deque 中最后一个元素之后的位置。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>返回值

用于寻址反向 [deque](../standard-library/deque-class.md) 中最后一个元素之后的位置（非反向 deque 中第一个元素之前的位置）的常量反向随机存取迭代器。

### <a name="remarks"></a>备注

`crend` 用于反向 `deque`，正如 [array::cend](../standard-library/array-class-stl.md#cend) 用于 `deque` 一样。

由于使用 `crend` 的返回值（适当递减），因此不能修改 `deque` 对象。

`crend` 可用于测试反向迭代器是否已到达其 deque 末尾。

不应对 `crend` 返回的值取消引用。

### <a name="example"></a>示例

```cpp
// deque_crend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::const_reverse_iterator v1_rIter;

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

## <a name="deque"></a>deque

构造一个 deque，它具有特定大小或它的元素具有特定值，或具有特定分配器或作为其他 deque 的全部或部分副本。

```cpp
deque();

explicit deque(const Allocator& Al);
explicit deque(size_type Count);
deque(size_type Count, const Type& Val);

deque(
    size_type Count,
    const Type& Val,
    const Allocator& Al);

deque(const deque& Right);

template <class InputIterator>
deque(InputIterator First,  InputIterator Last);

template <class InputIterator>
deque(
   InputIterator First,
   InputIterator Last,
   const Allocator& Al);

deque(initializer_list<value_type> IList, const Allocator& Al);
```

### <a name="parameters"></a>参数

*Al*\
要用于此对象的分配器类。

*计数*\
构造的 deque 中的元素数。

*Val*\
构造的 deque 中的元素值。

*Right*\
构造的 deque 要作为其副本的 deque。

*第一个*\
要复制的元素范围内的第一个元素的位置。

*最后*\
要复制的元素范围外的第一个元素的位置。

*IList*\
要复制的 initializer_list。

### <a name="remarks"></a>备注

所有构造函数都存储一个分配器对象（*Al*）并初始化 deque。

前两个构造函数指定一个空的初始 deque;第二个还指定要使用的分配器类型（`_Al`）。

第三个构造函数指定类 `count` 的默认值的指定数量 (`Type`) 的元素的重复。

第四个和第五个构造函数指定 `val`的值的（*计数*）元素的重复。

第六个构造函数指定 deque*权限*的副本。

第七个和第八个构造函数复制 deque 的范围 `[First, Last)`。

第七个构造函数移动 deque*权限*。

第八个构造函数复制 initializer_list 的内容。

所有构造函数均不执行任何临时重新分配。

### <a name="example"></a>示例

```cpp
/ compile with: /EHsc
#include <deque>
#include <iostream>
#include <forward_list>

int main()
{
    using namespace std;

    forward_list<int> f1{ 1, 2, 3, 4 };

    f1.insert_after(f1.begin(), { 5, 6, 7, 8 });

    deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1(3);

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2(5, 2);

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3(3, 1, c2.get_allocator());

    // Create a copy, deque c4, of deque c2
    deque <int> c4(c2);

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    deque <int> c5(c4.begin(), c4_Iter);

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    deque <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

    initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for (int i : c1)
        cout << i << " ";
    cout << endl;

    cout << "c2 = ";
    for (int i : c2)
        cout << i << " ";
    cout << endl;

    cout << "c3 = ";
    for (int i : c3)
        cout << i << " ";
    cout << endl;

    cout << "c4 = ";
    for (int i : c4)
        cout << i << " ";
    cout << endl;

    cout << "c5 = ";
    for (int i : c5)
        cout << i << " ";
    cout << endl;

    cout << "c6 = ";
    for (int i : c6)
        cout << i << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7(move(c6));
    deque <int>::iterator c7_Iter;

    cout << "c7 =";
    for (int i : c7)
        cout << i << " ";
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    for (int i : c9)
        cout << i << " ";
    cout << endl;

    int x = 3;
}
// deque_deque.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
    using namespace std;
   deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1( 3 );

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2( 5, 2 );

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3( 3, 1, c2.get_allocator( ) );

    // Create a copy, deque c4, of deque c2
    deque <int> c4( c2 );

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin( );
    c4_Iter++;
    c4_Iter++;
    deque <int> c5( c4.begin( ), c4_Iter );

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin( );
   c4_Iter++;
   c4_Iter++;
   c4_Iter++;
   deque <int> c6( c4.begin( ), c4_Iter, c2.get_allocator( ) );

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

        initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
        cout << *c1_Iter << " ";
    cout << endl;

    cout << "c2 = ";
    for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
        cout << *c2_Iter << " ";
    cout << endl;

    cout << "c3 = ";
    for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
        cout << *c3_Iter << " ";
    cout << endl;

    cout << "c4 = ";
    for ( c4_Iter = c4.begin( ); c4_Iter != c4.end( ); c4_Iter++ )
        cout << *c4_Iter << " ";
    cout << endl;

    cout << "c5 = ";
    for ( c5_Iter = c5.begin( ); c5_Iter != c5.end( ); c5_Iter++ )
        cout << *c5_Iter << " ";
    cout << endl;

    cout << "c6 = ";
    for ( c6_Iter = c6.begin( ); c6_Iter != c6.end( ); c6_Iter++ )
        cout << *c6_Iter << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7( move(c6) );
    deque <int>::iterator c7_Iter;

    cout << "c7 =" ;
    for ( c7_Iter = c7.begin( ) ; c7_Iter != c7.end( ) ; c7_Iter++ )
        cout << " " << *c7_Iter;
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    or (int i : c9)
        cout << i << " ";
    cout << endl;
}
```

## <a name="difference_type"></a>difference_type

一个类型，此类型提供引用同一 deque 中的元素的两个迭代器之间的差异。

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>备注

`difference_type` 也可以被描述为两个指针之间的元素数目。

### <a name="example"></a>示例

```cpp
// deque_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <deque>
#include <algorithm>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   deque <int>::difference_type df_typ1, df_typ2, df_typ3;

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

## <a name="emplace"></a>emplace

将适当构造的元素插入到指定位置的 deque 中。

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>参数

*_Where*\
[deque](../standard-library/deque-class.md) 中插入第一个元素的位置。

*val*\
插入到 `deque` 中的元素的值。

### <a name="return-value"></a>返回值

该函数将返回一个迭代器，指向 deque 中新元素的插入位置。

### <a name="remarks"></a>备注

任何插入操作都可能产生巨额开销，请参阅 `deque`，了解有关 `deque` 性能的讨论。

### <a name="example"></a>示例

```cpp
// deque_emplace.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

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

## <a name="emplace_back"></a>emplace_back

将一个适当构造的元素添加到 deque 末尾。

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>参数

*val*\
添加到 [deque](../standard-library/deque-class.md) 末尾的元素。

### <a name="example"></a>示例

```cpp
// deque_emplace_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_back( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="emplace_front"></a>emplace_front

将一个适当构造的元素添加到 deque 末尾。

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>参数

*val*\
要添加到 [deque](../standard-library/deque-class.md) 开头的元素。

### <a name="example"></a>示例

```cpp
// deque_emplace_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_front( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="empty"></a>空白处

测试 deque 是否为空。

```cpp
bool empty() const;
```

### <a name="return-value"></a>返回值

如果 deque 为空，则为 **true**；如果 deque 不为空，则为 **false**。

### <a name="example"></a>示例

```cpp
// deque_empty.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The deque is empty." << endl;
   else
      cout << "The deque is not empty." << endl;
}
```

```Output
The deque is not empty.
```

## <a name="end"></a>端面

返回一个迭代器，此迭代器用于发现 deque 中最后一个元素之后的位置。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>返回值

用于发现 deque 中最后一个元素之后的位置的随机访问迭代器。 如果 deque 为空，则 deque:: end = = deque:: begin。

### <a name="remarks"></a>备注

`end` 用于测试迭代器是否已到达其 deque 的末尾。

### <a name="example"></a>示例

```cpp
// deque_end.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
   *c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is " << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // deque <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The deque is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The deque is now: 10 400 30
```

## <a name="erase"></a>擦除

在 deque 的指定位置移除一个元素或一系列元素。

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>参数

*_Where*\
要从 deque 中移除的元素的位置。

*第一个*\
要从 deque 中移除的第一个元素的位置。

*最后*\
要从 deque 中移除的刚超出最后一个元素的位置。

### <a name="return-value"></a>返回值

指定已移除的任何元素之外保留的第一个元素的随机访问迭代器；如果不存在此类元素，则为指向 deque 末尾的指针。

### <a name="remarks"></a>备注

`erase` 绝不会引发异常。

### <a name="example"></a>示例

```cpp
// deque_erase.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial deque is: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the deque becomes:  ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, deque becomes: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
}
```

```Output
The initial deque is: 10 20 30 40 50
After erasing the first element, the deque becomes:  20 30 40 50
After erasing all elements but the first, deque becomes: 20
```

## <a name="front"></a>主

返回对 deque 中第一个元素的引用。

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>返回值

如果 deque 为空，则返回的结果不确定。

### <a name="remarks"></a>备注

如果 `front` 的返回值赋给了 `const_reference`，则无法修改 deque 对象。 如果 `front` 的返回值赋给了 `reference`，则可以修改 deque 对象。

当使用定义为 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 进行编译时，如果试图访问空 deque 中的元素，则将发生运行时错误。  有关更多信息，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>示例

```cpp
// deque_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.front( );
   const int& ii = c1.front( );

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The second integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 11
```

## <a name="get_allocator"></a> get_allocator

返回用于构造 deque 的分配器对象的一个副本。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>返回值

deque 使用的分配器。

### <a name="remarks"></a>备注

deque 类的分配器指定类管理存储的方式。 C++ 标准库容器类提供的默认分配器足以满足大多编程需求。 编写和使用你自己的分配器类是高级 C++ 主题。

### <a name="example"></a>示例

```cpp
// deque_get_allocator.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   deque <int> c1;
   deque <int, allocator<int> > c2 = deque <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   deque <int> c3( c1.get_allocator( ) );

   deque <int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a>&

将一个、多个或一系列元素插入 deque 中的指定位置。

```cpp
iterator insert(
    const_iterator Where,
    const Type& Val);

iterator insert(
    const_iterator Where,
    Type&& Val);

void insert(
    iterator Where,
    size_type Count,
    const Type& Val);

template <class InputIterator>
void insert(
    iterator Where,
    InputIterator First,
    InputIterator Last);

iterator insert(
    iterator Where,initializer_list<Type>
IList);
```

### <a name="parameters"></a>参数

*Where*\
目标 deque 中插入第一个元素的位置。

*Val*\
要插入 deque 中的元素的值。

*计数*\
要插入 deque 中的元素数。

*第一个*\
要从自变量 deque 中复制的一系列元素中第一个元素的位置。

*最后*\
要从自变量 deque 中复制的一系列元素以外的第一个元素的位置。

*IList*\
要插入的元素的 initializer_list。

### <a name="return-value"></a>返回值

前两个插入函数返回一个迭代器，该迭代器指向新元素插入到 deque 中的位置。

### <a name="remarks"></a>备注

任何插入操作都可能产生巨额开销。

## <a name="iterator"></a>器

一个类型，它提供可读取或修改 deque 中任何元素的随机访问迭代器。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>备注

类型 `iterator` 可用于修改元素的值。

### <a name="example"></a>示例

请参阅 [begin](#begin) 的示例。

## <a name="max_size"></a>max_size

返回 deque 的最大长度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>返回值

deque 的最大可能长度。

### <a name="example"></a>示例

```cpp
// deque_max_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   i = c1.max_size( );
   cout << "The maximum possible length of the deque is " << i << "." << endl;
}
```

## <a name="op_at"></a>运算符 []

返回对指定位置的 deque 元素的引用。

```cpp
reference operator[](size_type pos);

const_reference operator[](size_type pos) const;
```

### <a name="parameters"></a>参数

*pos*\
要引用的 deque 元素的位置。

### <a name="return-value"></a>返回值

对参数中指定其位置的元素的引用。 如果指定的位置大于 deque 的大小，则结果为不确定。

### <a name="remarks"></a>备注

如果 `operator[]` 的返回值赋给了 `const_reference`，则无法修改 deque 对象。 如果 `operator[]` 的返回值赋给了 `reference`，则可以修改 deque 对象。

通过使用定义为 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 进行编译时，如果你尝试访问 deque 边界以外的元素，将发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md) 。

### <a name="example"></a>示例

```cpp
// deque_op_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   cout << "The first integer of c1 is " << c1[0] << endl;
   int& i = c1[1];
   cout << "The second integer of c1 is " << i << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 20
```

## <a name="op_eq"></a>operator =

使用另一个 deque 中的元素替换此 deque 的元素。

```cpp
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```

### <a name="parameters"></a>参数

*right*\
提供新内容的 deque。

### <a name="remarks"></a>备注

第一次重写将元素复制到*right*此 deque。 第二次重写将元素移动到此*deque。*

执行该运算符之前移除此 deque 中包含的元素。

### <a name="example"></a>示例

```cpp
// deque_operator_as.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
using namespace std;

typedef deque<int> MyDeque;

template<typename MyDeque> struct S;

template<typename MyDeque> struct S<MyDeque&> {
  static void show( MyDeque& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
    cout << endl;
  }
};

template<typename MyDeque> struct S<MyDeque&&> {
  static void show( MyDeque&& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
cout << " via unnamed rvalue reference " << endl;
  }
};

int main( )
{
   MyDeque d1, d2;

   d1.push_back(10);
   d1.push_back(20);
   d1.push_back(30);
   d1.push_back(40);
   d1.push_back(50);

   cout << "d1 = " ;
   S<MyDeque&>::show( d1 );

   d2 = d1;
   cout << "d2 = ";
   S<MyDeque&>::show( d2 );

   cout << "     ";
   S<MyDeque&&>::show ( move< MyDeque& > (d1) );
}
```

## <a name="pointer"></a>变为

提供指向 [deque](../standard-library/deque-class.md) 中的元素的指针。

```unstlib
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>备注

类型 `pointer` 可用于修改元素的值。 [iterator](#iterator) 更常用于访问 deque 元素。

## <a name="pop_back"></a>pop_back

删除 deque 末尾处的元素。

```cpp
void pop_back();
```

### <a name="remarks"></a>备注

最后一个元素不得为空。 `pop_back` 绝不会引发异常。

### <a name="example"></a>示例

```cpp
// deque_pop_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the deque, the "
      "last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the deque, the last element is: 1
```

## <a name="pop_front"></a>pop_front

删除 deque 开头的元素。

```cpp
void pop_front();
```

### <a name="remarks"></a>备注

第一个元素不得为空。 `pop_front` 绝不会引发异常。

### <a name="example"></a>示例

```cpp
// deque_pop_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the "
      "deque, the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the deque, the first element is: 2
```

## <a name="push_back"></a>push_back

在 deuqe 末尾处添加一个元素。

```cpp
void push_back(const Type& val);

void push_back(Type&& val);
```

### <a name="parameters"></a>参数

*val*\
添加到 deque 末尾的元素。

### <a name="remarks"></a>备注

如果引发了异常，deque 保持不变，该异常将被重新引发。

## <a name="push_front"></a>push_front

在 deque 的开头添加元素。

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>参数

*val*\
要添加到 deque 开头的元素。

### <a name="remarks"></a>备注

如果引发了异常，deque 保持不变，该异常将被重新引发。

### <a name="example"></a>示例

```cpp
// deque_push_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a deque of strings
   deque <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a>rbegin

返回指向反向 deque 中第一个元素的迭代器。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>返回值

发现反向 deque 中的第一个元素或发现曾是非反向 deque 中的最后一个元素的反向随机访问迭代器。

### <a name="remarks"></a>备注

`rbegin` 用于反向 deque，正如将 [begin](#begin) 用于 deque 一样。

如果 `rbegin` 的返回值赋给了 `const_reverse_iterator`，则无法修改 deque 对象。 如果 `rbegin` 的返回值赋给了 `reverse_iterator`，则可以修改 deque 对象。

`rbegin` 可用于向后循环访问 deque。

### <a name="example"></a>示例

```cpp
// deque_rbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rbegin( );
   cout << "Last element in the deque is " << *c1_rIter << "." << endl;

   cout << "The deque contains the elements: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << "in that order.";
   cout << endl;

   // rbegin can be used to iterate through a deque in reverse order
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rbegin( );
   *c1_rIter = 40;  // This would have caused an error if a
                    // const_reverse iterator had been declared as
                    // noted above
   cout << "Last element in deque is now " << *c1_rIter << "." << endl;
}
```

```Output
Last element in the deque is 30.
The deque contains the elements: 10 20 30 in that order.
The reversed deque is: 30 20 10
Last element in deque is now 40.
```

## <a name="reference"></a>对

一种类型，此类型提供对存储在 deque 中的元素的引用。

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>示例

```cpp
// deque_reference.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="rend"></a>rend

返回一个迭代器，此迭代器用于发现反向 deque 中最后一个元素之后的位置。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>返回值

用于寻址反向 deque 中最后一个元素之后的位置（非反向 deque 中第一个元素之前的位置）的反向随机访问迭代器。

### <a name="remarks"></a>备注

`rend` 与反向 deque 配合使用，正如 [end](#end) 与 deque 配合使用一样。

如果 `rend` 的返回值赋给了 `const_reverse_iterator`，则无法修改 deque 对象。 如果 `rend` 的返回值赋给了 `reverse_iterator`，则可以修改 deque 对象。

`rend` 可用于测试反向迭代器是否已到达其 deque 末尾。

不应对 `rend` 返回的值取消引用。

### <a name="example"></a>示例

```cpp
// deque_rend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;
   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --; // Decrementing a reverse iterator moves it forward
                // in the deque (to point to the first element here)
   cout << "The first element in the deque is: " << *c1_rIter << endl;

   cout << "The deque is: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << endl;

   // rend can be used to test if an iteration is through all of
   // the elements of a reversed deque
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--; // Decrementing the reverse iterator moves it backward
               // in the reversed deque (to the last element here)
   *c1_rIter = 40; // This modification of the last element would
                   // have caused an error if a const_reverse
                   // iterator had been declared (as noted above)
   cout << "The modified reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;
}
```

```Output
The first element in the deque is: 10
The deque is: 10 20 30
The reversed deque is: 30 20 10
The modified reversed deque is: 30 20 40
```

## <a name="resize"></a>调节

为 deque 指定新的大小。

```cpp
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>参数

*_Newsize*\
列表的新大小。

*val*\
新的大小大于原始大小时要添加至 deque 的新元素的值。 如果省略此值，则会赋给新元素该类的默认值。

### <a name="remarks"></a>备注

如果 deque 的大小小于请求的大小， *_Newsize*会将元素添加到 deque 中，直到它达到请求的大小。

如果 deque 的大小大于请求的大小，则将删除离 deque 末尾最近的元素，直到 deque 达到 *_Newsize*大小。

如果 deque 的当前大小与请求的大小相同，则不采取任何操作。

[size](#size) 表示 deque 的当前大小。

### <a name="example"></a>示例

```cpp
// deque_resize.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is: 4
The value of the last element is 40
The size of c1 is now: 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse_iterator"></a>reverse_iterator

提供可读取或修改反向 deque 中元素的随机访问迭代器的类型。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>备注

`reverse_iterator` 类型用于循环访问 deque。

### <a name="example"></a>示例

请参阅 rbegin 的示例。

## <a name="shrink_to_fit"></a> shrink_to_fit

放弃额外容量。

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>备注

没有可移植方法来确定 `shrink_to_fit` 是否可以减少 [deque](../standard-library/deque-class.md) 使用的存储。

### <a name="example"></a>示例

```cpp
// deque_shrink_to_fit.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   //deque <int>::iterator Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
   v1.shrink_to_fit();
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
}
```

```Output
Current size of v1 = 1
Current size of v1 = 1
```

## <a name="size"></a>规格

返回 deque 中的元素数。

```cpp
size_type size() const;
```

### <a name="return-value"></a>返回值

deque 的当前长度。

### <a name="example"></a>示例

```cpp
// deque_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   c1.push_back( 1 );
   i = c1.size( );
   cout << "The deque length is " << i << "." << endl;

   c1.push_back( 2 );
   i = c1.size( );
   cout << "The deque length is now " << i << "." << endl;
}
```

```Output
The deque length is 1.
The deque length is now 2.
```

## <a name="size_type"></a>size_type

计算 deque 中元素数量的类型。

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>示例

请参阅 [size](#size) 的示例。

## <a name="swap"></a>购

交换两个 deque 的元素。

```cpp
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*right*\
提供要交换的元素的 deque，或其元素将要与deque `left` 的元素交换的 deque。

*左*\
其元素要与 deque*权限*的元素进行交换的 deque。

### <a name="example"></a>示例

```cpp
// deque_swap.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2, c3;
   deque <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap<>(c1, c2);
   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original deque c1 is: 1 2 3
After swapping with c2, deque c1 is: 10 20
After swapping with c3, deque c1 is: 100
After swapping with c2, deque c1 is: 1 2 3
```

## <a name="value_type"></a> value_type

表示 deque 中存储的数据类型的类型。

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>备注

`value_type` 是模板参数 `Type` 的同义词。

### <a name="example"></a>示例

```cpp
// deque_value_type.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
int main( )
{
   using namespace std;
   deque<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
