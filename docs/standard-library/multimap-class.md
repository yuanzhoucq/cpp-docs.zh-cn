---
title: multimap 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- map/std::multimap
- map/std::multimap::allocator_type
- map/std::multimap::const_iterator
- map/std::multimap::const_pointer
- map/std::multimap::const_reference
- map/std::multimap::const_reverse_iterator
- map/std::multimap::difference_type
- map/std::multimap::iterator
- map/std::multimap::key_compare
- map/std::multimap::key_type
- map/std::multimap::mapped_type
- map/std::multimap::pointer
- map/std::multimap::reference
- map/std::multimap::reverse_iterator
- map/std::multimap::size_type
- map/std::multimap::value_type
- map/std::multimap::begin
- map/std::multimap::cbegin
- map/std::multimap::cend
- map/std::multimap::clear
- map/std::multimap::count
- map/std::multimap::crbegin
- map/std::multimap::crend
- map/std::multimap::emplace
- map/std::multimap::emplace_hint
- map/std::multimap::empty
- map/std::multimap::end
- map/std::multimap::equal_range
- map/std::multimap::erase
- map/std::multimap::find
- map/std::multimap::get_allocator
- map/std::multimap::insert
- map/std::multimap::key_comp
- map/std::multimap::lower_bound
- map/std::multimap::max_size
- map/std::multimap::rbegin
- map/std::multimap::rend
- map/std::multimap::size
- map/std::multimap::swap
- map/std::multimap::upper_bound
- map/std::multimap::value_comp
dev_langs:
- C++
helpviewer_keywords:
- std::multimap [C++]
- std::multimap [C++], allocator_type
- std::multimap [C++], const_iterator
- std::multimap [C++], const_pointer
- std::multimap [C++], const_reference
- std::multimap [C++], const_reverse_iterator
- std::multimap [C++], difference_type
- std::multimap [C++], iterator
- std::multimap [C++], key_compare
- std::multimap [C++], key_type
- std::multimap [C++], mapped_type
- std::multimap [C++], pointer
- std::multimap [C++], reference
- std::multimap [C++], reverse_iterator
- std::multimap [C++], size_type
- std::multimap [C++], value_type
- std::multimap [C++], begin
- std::multimap [C++], cbegin
- std::multimap [C++], cend
- std::multimap [C++], clear
- std::multimap [C++], count
- std::multimap [C++], crbegin
- std::multimap [C++], crend
- std::multimap [C++], emplace
- std::multimap [C++], emplace_hint
- std::multimap [C++], empty
- std::multimap [C++], end
- std::multimap [C++], equal_range
- std::multimap [C++], erase
- std::multimap [C++], find
- std::multimap [C++], get_allocator
- std::multimap [C++], insert
- std::multimap [C++], key_comp
- std::multimap [C++], lower_bound
- std::multimap [C++], max_size
- std::multimap [C++], rbegin
- std::multimap [C++], rend
- std::multimap [C++], size
- std::multimap [C++], swap
- std::multimap [C++], upper_bound
- std::multimap [C++], value_comp
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25dffabfe01bb68af180d67b5b47dfee44ce30ff
ms.sourcegitcommit: 39585672df8874fb5df4e70de97cd7f328fe9880
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2018
ms.locfileid: "34153140"
---
# <a name="multimap-class"></a>multimap 类

C++ 标准库多重映射类用于存储和检索集合中的数据，此集合中的每个元素均为包含数据值和排序键的元素对。 键值不需要唯一，用于自动排序数据。 可以直接更改多重映射中的元素值，但不能直接更改其关联键值。 必须先删除与旧元素关联的键值，才能插入与新元素关联的新键值。

## <a name="syntax"></a>语法

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>参数

`Key` 要存储在多重映射中的键数据类型。

`Type` 要存储在多重映射中的元素数据类型。

`Traits` 提供可比较两个元素值作为排序键以确定在多重映射中其相对顺序的函数对象的类型。 默认值是二元谓词 `less<Key>`。

在 C++ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。 有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#heterogeneous-lookup-in-associative-containers-c14)

`Allocator` 表示存储的分配器对象封装有关映射的分配和解除分配内存的详细信息的类型。 此参数为可选参数，默认值为 `allocator<pair <const Key, Type> >`。

## <a name="remarks"></a>备注

C++ 标准库多重映射类为

- 大小可变的关联容器，支持基于关联键值高效检索元素值。

- 可逆，因为它提供双向迭代器来访问其元素。

- 有序，因为它的元素在容器中根据指定的比较函数按键值排序。

- 多个，它的元素不需要具有唯一键，因此一个键值可具有多个相关联的元素数据值。

- 关联容器对，因为它的元素数据值与其键值不同。

- 模板类，因为它提供的功能是一般性的功能，因此与作为元素或键包含的特定数据类型无关。 用于元素和键的数据类型作为类模板以及比较函数和分配器中的参数指定。

映射类提供的迭代器是双向迭代器，但类成员函数 [insert](#insert) 和 [multimap](#multimap) 具有将较弱输入迭代器作为模板参数的版本，较弱输入迭代器的功能需求比双向迭代器类保证的功能需求更少。 不同的迭代器概念形成一个系列，通过它们的功能优化相关联。 每个迭代器概念有它自己的一套要求，使用这些概念的算法必须根据迭代器类型提供的要求限制它们的假设。 可以假定输入迭代器可取消引用以引用某个对象，并可递增到序列中的下一迭代器。 这是最小的功能集，但足以按有意义的方式提供类成员函数的上下文中的迭代器范围 `[First, Last)`。

容器类型选择通常应根据应用程序所需的搜索和插入的类型。 关联容器针对查找、插入和移除操作进行了优化。 显式支持这些操作的成员函数较为高效，执行这些操作的时间与容器中元素数量的对数平均成比例。 插入元素不会使迭代器失效，移除元素仅会使专门指向已移除元素的迭代器失效。

当应用程序满足将值与其键关联的条件时，应选择多重映射作为关联容器。 此类结构的模型是关键字排序列表，这些关键字具有提供定义等的关联字符串值，并且并非始终唯一定义。 如果关键字经过唯一定义以使键唯一，则应选择映射作为容器。 另一方面，如果仅存储关键字列表，则应使用集作为正确容器。 如果允许关键字多次出现，则应使用多重集合作为适当的容器结构。

多重映射通过调用存储的 [key_compare](#key_compare) 类型的函数对象，对它控制的序列进行排序。 此存储对象是比较函数，可通过调用成员函数 [key_comp](#key_comp) 进行访问。 通常，元素仅需小于比较元素即可建立此顺序；因此，给定任意两个元素，可以确定这两个元素等效（即两者均不小于对方）或其中一个小于另一个。 这将导致在非等效元素之间进行排序。 在技术性更强的说明中，比较函数是一个二元谓词，在标准数学的意义上引发严格弱排序。 二元谓词 `f(x,y)` 是包含两个参数对象（`x` 和 `y`）以及一个返回值（true 或 false）的函数对象。 如果二元谓词具有自反性、反对称性和传递性且等效可传递，对集进行的排序将为严格弱排序，其中两个对象 `x` 和 `y` 定义为在 `f(x,y)` 和 `f(y,x)` 均为 false 时等效。 如果键之间的更强相等条件取代了等效性，则排序将为总排序（即所有元素彼此排序），并且匹配的键将难以彼此辨别。

在 C++ 14 中可以通过指定没有类型参数的 `std::less<>` 或 `std::greater<>` 谓词来启用异类查找。 有关详细信息，请参阅[关联容器中的异类查找](../standard-library/stl-containers.md#sequence_containers)

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[multimap](#multimap)|构造一个空的或者是其他某个 `multimap` 的全部或部分副本的 `multimap`。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[allocator_type](#allocator_type)|一种类型，此类型表示 `allocator` 对象的 `multimap` 类。|
|[const_iterator](#const_iterator)|一种类型，此类型提供可读取 `const` 中的 `multimap` 元素的双向迭代器。|
|[const_pointer](#const_pointer)|一种类型，此类型提供指向 `const` 中的 `multimap` 元素的指针。|
|[const_reference](#const_reference)|一种类型，此类型提供对存储在 `const` 中的 `multimap` 元素的引用（用于读取和执行 `const` 操作）。|
|[const_reverse_iterator](#const_reverse_iterator)|一种类型，此类型提供可读取 `const` 中的任何 `multimap` 元素的双向迭代器。|
|[difference_type](#difference_type)|一种有符号整数类型，此类型可用于表示 `multimap` 中迭代器指向的元素间范围内的元素数量。|
|[Iterator](#iterator)|一种类型，此类型提供引用同一 `multimap` 中的元素的两个迭代器之间的差异。|
|[key_compare](#key_compare)|一种提供函数对象的类型，该函数对象可比较两个排序键以确定 `multimap` 中两个元素的相对顺序。|
|[key_type](#key_type)|一种类型，此类型描述组成 `multimap` 中每个元素的排序键对象。|
|[mapped_type](#mapped_type)|一种类型，此类型表示存储在 `multimap` 中的数据类型。|
|[pointer](#pointer)|一种类型，此类型提供指向 `const` 中的 `multimap` 元素的指针。|
|[reference](#reference)|一种类型，此类型提供对存储在 `multimap` 中的元素的引用。|
|[reverse_iterator](#reverse_iterator)|一种类型，此类型提供可读取或修改反向 `multimap` 中的元素的双向迭代器。|
|[size_type](#size_type)|一种无符号整数类型，此类型提供指向 `const` 中`multimap` 元素的指针。|
|[value_type](#value_type)|一种提供函数对象的类型，该函数对象可将两个元素作为排序键比较以确定它们在 `multimap` 中的相对顺序。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[begin](#begin)|返回一个迭代器，此迭代器用于发现 `multimap` 中的第一个元素。|
|[cbegin](#cbegin)|返回一个常量迭代器，此迭代器用于发现 `multimap` 中的第一个元素。|
|[cend](#cend)|返回一个常量迭代器，此迭代器用于发现 `multimap` 中最后一个元素之后的位置。|
|[clear](#clear)|清除 `multimap` 的所有元素。|
|[count](#count)|返回 `multimap` 中其键与指定为参数的键匹配的元素数量。|
|[crbegin](#crbegin)|返回一个常量迭代器，此迭代器用于发现反向 `multimap` 中的第一个元素。|
|[crend](#crend)|返回一个常量迭代器，此迭代器用于发现反向 `multimap` 中最后一个元素之后的位置。|
|[emplace](#emplace)|将就地构造的元素插入到 `multimap`。|
|[emplace_hint](#emplace_hint)|将就地构造的元素插入到 `multimap`，附带位置提示|
|[empty](#empty)|测试 `multimap` 是否为空。|
|[end](#end)|返回一个迭代器，此迭代器用于发现 `multimap` 中最后一个元素之后的位置。|
|[equal_range](#equal_range)|查找其中元素的键与指定值匹配的元素范围。|
|[erase](#erase)|从 `multimap` 中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。|
|[find](#find)|返回一个迭代器，此迭代器用于发现 `multimap` 中其键与指定键等效的元素的第一个位置。|
|[get_allocator](#get_allocator)|返回用于构造 `allocator` 的 `multimap` 对象的副本。|
|[insert](#insert)|将一个元素或元素范围插入到 `multimap`。|
|[key_comp](#key_comp)|检索用于对 `multimap` 中的键进行排序的比较对象副本。|
|[lower_bound](#lower_bound)|返回一个迭代器，此迭代器指向 `multimap` 中其键等于或大于指定键的第一个元素。|
|[max_size](#max_size)|返回 `multimap` 的最大长度。|
|[rbegin](#rbegin)|返回一个迭代器，此迭代器用于发现反向 `multimap` 中的第一个元素。|
|[rend](#rend)|返回一个迭代器，此迭代器用于发现反向 `multimap` 中最后一个元素之后的位置。|
|[size](#size)|返回 `multimap` 中的元素数量。|
|[swap](#swap)|交换两个 `multimap` 的元素。|
|[upper_bound](#upper_bound)|返回一个迭代器，此迭代器指向 `multimap` 中其键大于指定键的第一个元素。|
|[value_comp](#value_comp)|此成员函数返回一个函数对象，该函数对象可通过比较 `multimap` 中元素的键值来确定元素顺序。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator=](#op_eq)|将一个 `multimap` 中的元素替换为另一 `multimap` 副本。|

## <a name="requirements"></a>要求

**Header:** \<map>

**命名空间：** std

(**key**, **value**) 对作为 `pair` 类型的对象存储在多重映射中。 此对类需要标头 \<utility>，\<map> 自动包括此标头。

## <a name="allocator_type"></a>  multimap::allocator_type

一种类型，它代表多重映射对象的分配器类。

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>示例

有关使用 `allocator_type` 的示例，请参阅 [get_allocator](#get_allocator) 的示例。

## <a name="begin"></a>  multimap::begin

返回发现多重映射中第一个元素的迭代器。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>返回值

发现多重映射中第一个元素或空多重映射之后的位置的双向迭代器。

### <a name="example"></a>示例

```cpp
// multimap_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err as the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "First element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
First element of m1 is now 1
```

## <a name="cbegin"></a>  multimap::cbegin

返回确定范围中第一个元素地址的 `const` 迭代器。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>返回值

`const` 双向访问迭代器，指向范围的第一个元素，或刚超出空范围末尾的位置（对于空范围，`cbegin() == cend()`）。

### <a name="remarks"></a>备注

由于使用 `cbegin` 的返回值，因此不能修改范围中的元素。

可以使用此成员函数替代 `begin()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在此示例中，将 `Container` 视为支持 `begin()` 和 `cbegin()` 的可修改的任何类型的（非- `const`）容器。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  multimap::cend

返回一个 `const` 迭代器，此迭代器用于发现刚超出范围中最后一个元素的位置。

```cpp
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

## <a name="clear"></a>  multimap::clear

清除多重映射的所有元素。

```cpp
void clear();
```

### <a name="example"></a>示例

下列示例演示了 multimap::clear 成员函数的用法。

```cpp
// multimap_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1;
   multimap<int, int>::size_type i;
   typedef pair<int, int> Int_Pair;

   m1.insert(Int_Pair(1, 1));
   m1.insert(Int_Pair(2, 4));

   i = m1.size();
   cout << "The size of the multimap is initially "
        << i << "." << endl;

   m1.clear();
   i = m1.size();
   cout << "The size of the multimap after clearing is "
        << i << "." << endl;
}
```

```Output
The size of the multimap is initially 2.
The size of the multimap after clearing is 0.
```

## <a name="const_iterator"></a>  multimap::const_iterator

一种类型，提供可读取多重映射中 **const** 元素的双向迭代器。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>备注

`const_iterator` 类型不能用于修改元素的值。

`const_iterator`由多重映射指向的对象定义[value_type](#value_type)，类型`pair` * \< * **const 密钥**，**类型 * * * >*。 键值通过第一个成员对可用，已映射元素的值通过对的第二个成员可用。

若要取消引用`const_iterator``cIter`多重映射中指向的元素，使用**->** 运算符。

若要访问元素的键值，请使用 `cIter` -> **first**，其作用与 (\* `cIter`). **first** 相同。 若要访问元素的映射值，请使用 `cIter` -> **second**，其作用与 (\* `cIter`). **second** 相同。

### <a name="example"></a>示例

有关使用 `const_iterator` 的示例，请参阅 [begin](#begin) 的示例。

## <a name="const_pointer"></a>  multimap::const_pointer

一种类型，它提供指向多重映射中 **const** 元素的指针。

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>备注

`const_pointer` 类型不能用于修改元素的值。

在大多数情况下，应使用 [iterator](#iterator) 访问多重映射对象中的元素。

## <a name="const_reference"></a>  multimap::const_reference

一种类型，此类型提供对用于读取和执行 **const** 操作的多重映射中存储的 **const** 元素的引用。

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>示例

```cpp
// multimap_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of the first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of the first element in the multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the multimap is 1.
The data value of the first element in the multimap is 10.
```

## <a name="const_reverse_iterator"></a>  multimap::const_reverse_iterator

一种类型，提供可读取多重映射中任何 **const** 元素的双向迭代器。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>备注

`const_reverse_iterator` 类型无法修改元素的值，它用于反向循环访问多重映射。

`const_reverse_iterator`由多重映射指向的对象定义[value_type](#value_type)，类型`pair` * \< * **const 密钥**，**类型 * * * >*。 键值通过第一个成员对可用，已映射元素的值通过对的第二个成员可用。

若要取消引用`const_reverse_iterator``crIter`多重映射中指向的元素，使用**->** 运算符。

若要访问元素的键值，请使用 `crIter` -> **first**，其作用与 (\* `crIter`). **first** 相同。 若要访问元素的映射值，请使用 `crIter` -> **second**，其作用与 (\* `crIter`). **first** 相同。

### <a name="example"></a>示例

有关如何声明和使用 `const_reverse_iterator` 的示例，请参阅 [rend](#rend) 的示例。

## <a name="count"></a>  multimap::count

返回 multimap 中其键与指定了参数的键匹配的元素数量。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>参数

`key` 要匹配的多重映射中的元素的键。

### <a name="return-value"></a>返回值

其排序键与参数键匹配的元素数量；如果 multimap 不包含具有匹配键的元素，则为 0。

### <a name="remarks"></a>备注

成员函数返回在以下范围内的元素数量：

[ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) )

这些元素具有键值 `key`。

### <a name="example"></a>示例

下面的示例演示 multimap::count 成员函数的用法。

```cpp
// multimap_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
    using namespace std;
    multimap<int, int> m1;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in multimap,
    // so duplicates are allowed and counted
    i = m1.count(1);
    cout << "The number of elements in m1 with a sort key of 1 is: "
         << i << "." << endl;

    i = m1.count(2);
    cout << "The number of elements in m1 with a sort key of 2 is: "
         << i << "." << endl;

    i = m1.count(3);
    cout << "The number of elements in m1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in m1 with a sort key of 1 is: 2.
The number of elements in m1 with a sort key of 2 is: 2.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  multimap::crbegin

返回一个常量迭代器，此迭代器用于发现反向多重映射中的第一个元素。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>返回值

发现反向 [multimap](../standard-library/multimap-class.md) 中的第一个元素或发现曾是非反向 `multimap` 中的最后一个元素的常量反向双向迭代器。

### <a name="remarks"></a>备注

`crbegin` 用于反向 `multimap`，正如 [begin](#begin) 用于 `multimap` 一样。

返回值为 `crbegin` 时，无法修改 `multimap` 对象。

`crbegin` 可用于向后循环访问 `multimap`。

### <a name="example"></a>示例

```cpp
// multimap_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
```

## <a name="crend"></a>  multimap::crend

返回一个常量迭代器，此迭代器用于发现反向多重映射中最后一个元素之后的位置。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>返回值

用于发现反向 [multimap](../standard-library/multimap-class.md)中最后一个元素之后的位置（非反向 `multimap` 中第一个元素之前的位置）的常量反向双向迭代器。

### <a name="remarks"></a>备注

`crend` 用于反向 `multimap`，正如 [multimap::end](#end) 用于 `multimap` 一样。

返回值为 `crend` 时，无法修改 `multimap` 对象。

`crend` 可用于测试反向迭代器是否已到达其 `multimap` 的末尾。

不应对 `crend` 返回的值取消引用。

### <a name="example"></a>示例

```cpp
// multimap_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
```

## <a name="difference_type"></a>  multimap::difference_type

一种带符号整数类型，此类型可用于表示多重映射中迭代器指向的元素间范围内的元素数量。

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>备注

`difference_type` 是通过容器迭代器减少或递增时返回的类型。 `difference_type`通常用于表示的范围中元素数 [*第一个*，*最后一个*) 迭代器之间`first`和`last`，包括指向的元素通过`first`和元素，但不是包括的范围，该元素指向`last`。

注意，尽管 `difference_type` 适用于满足输入迭代器（包括可逆容器支持的双向迭代器的类，如集）需求的所有迭代器，迭代器之间的减法仅受随机访问容器（如 vector）提供的随机访问迭代器支持。

### <a name="example"></a>示例

```cpp
// multimap_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );

   // The following will insert as multimap keys are not unique
   m1.insert ( Int_Pair ( 2, 30 ) );

   multimap <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a multimap
   multimap <int, int>::difference_type  df_count = 0;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter )
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the multimap m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the multimap m1 is: 4.
```

## <a name="emplace"></a>  multimap::emplace

就地插入构造的元素（不执行复制或移动操作）。

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|`args`|用于构造要插入到多重映射中的元素的转发参数。|

### <a name="return-value"></a>返回值

指向新插入的元素的迭代器。

### <a name="remarks"></a>备注

对容器元素的引用不会因为此函数而失效，但是它可能会使所有指向容器的迭代器都失效。

如果在插入过程中引发异常，该容器将保持不变并重新引发异常。

元素的 [value_type](../standard-library/map-class.md#value_type) 是一个对，因此元素的值为一个有序对，其中第一个组件相当于键值，第二个组件相当于该元素的数据值。

### <a name="example"></a>示例

```cpp
// multimap_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: " << endl;

    for (const auto& p : m) {
        cout << "(" << p.first <<  "," << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    multimap<string, string> m1;

    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;

    m1.emplace("Bob", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;
}

```

## <a name="emplace_hint"></a>  multimap::emplace_hint

使用位置提示就地插入构造的元素（不执行复制或移动操作）。

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|`args`|用于构造要插入到多重映射中的元素的转发参数。|
|`where`|开始搜索正确插入点的位置。 （如果该点紧贴在 `where` 之前，则插入可能发生在分期常量时间内而非对数时间内。)|

### <a name="return-value"></a>返回值

指向新插入的元素的迭代器。

### <a name="remarks"></a>备注

对容器元素的引用不会因为此函数而失效，但是它可能会使所有指向容器的迭代器都失效。

在定位过程中，如果引发异常，则不会修改该容器的状态。

元素的 [value_type](../standard-library/map-class.md#value_type) 是一个对，因此元素的值为一个有序对，其中第一个组件相当于键值，第二个组件相当于该元素的数据值。

有关代码示例，请参阅 [map::emplace_hint](../standard-library/map-class.md#emplace_hint)。

## <a name="empty"></a>  multimap::empty

测试多重映射是否为空。

```cpp
bool empty() const;
```

### <a name="return-value"></a>返回值

如果多重映射为空，则为 **true**；如果多重映射不为空，则为 **false**。

### <a name="example"></a>示例

```cpp
// multimap_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The multimap m1 is empty." << endl;
   else
      cout << "The multimap m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The multimap m2 is empty." << endl;
   else
      cout << "The multimap m2 is not empty." << endl;
}
```

```Output
The multimap m1 is not empty.
The multimap m2 is empty.
```

## <a name="end"></a>  multimap::end

返回超过末尾迭代器。

```cpp
const_iterator end() const;


iterator end();
```

### <a name="return-value"></a>返回值

超过末尾迭代器。 如果多重映射为空，则 `multimap::end() == multimap::begin()`。

### <a name="remarks"></a>备注

**end** 用于测试迭代器是否超过其多重映射的末尾。

不应对 **end** 返回的值取消引用。

有关代码示例，请参阅 [multimap::find](#find)。

## <a name="equal_range"></a>  multimap::equal_range

查找其中元素的键与指定值匹配的元素范围。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>参数

`key` 要与所搜索多重映射中的元素的排序键进行比较的自变量键。

### <a name="return-value"></a>返回值

一对迭代器，其中第一个是键的 [lower_bound](#lower_bound)，第二个是键的 [upper_bound](#upper_bound)。

若要访问成员函数返回的 `pr` 对的第一个迭代器，请使用 `pr`. **first**；若要取消引用下界迭代器，请使用 \*( `pr`. **first**)。 若要访问成员函数返回的 `pr` 对的第二个迭代器，请使用 `pr`. **second**；若要取消引用上界迭代器，请使用 \*( `pr`. **second**)。

### <a name="example"></a>示例

```cpp
// multimap_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multimap <int, int, less<int> > IntMMap;
   IntMMap m1;
   multimap <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << " matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of multimap m1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the multimap m1 is: 20.
The upper bound of the element with a key of 2 in the multimap m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
 matching the 2nd element of the pair returned by equal_range( 2 ).
The multimap m1 doesn't have an element with a key less than 4.
```

## <a name="erase"></a>  multimap::erase

从多重映射中的指定位置移除一个元素或元素范围，或者移除与指定键匹配的元素。

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>参数

`Where` 要删除的元素的位置。

`First` 要移除的第一个元素的位置。

`Last` 要移除的最后一个元素以外的位置。

`Key` 要移除的元素的键。

### <a name="return-value"></a>返回值

对于前两个成员函数，则为双向迭代器，它指定已删除的任何元素之外留存的第一个元素，如果此类元素不存在，则为 map 末尾的元素。

对于第三个成员函数，则返回已从多重映射中移除的元素的数目。

### <a name="remarks"></a>备注

有关代码示例，请参阅 [map::erase](../standard-library/map-class.md#erase)。

## <a name="find"></a>  multimap::find

返回一个迭代器，此迭代器引用多重映射当中具有与指定键等效的键的元素的第一个位置。

```cpp
iterator find(const Key& key);


const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>参数

`key` 要从所搜索多重映射的元素的排序键匹配的键值。

### <a name="return-value"></a>返回值

引用具有指定键的元素的位置的迭代器，如果找不到具有这个键的元素，则引用这个多重映射中 (`multimap::end()`) 最后一个元素后面的位置。

### <a name="remarks"></a>备注

成员函数返回一个迭代器，它引用多重映射中其排序键与二元谓词下的参数键等效的元素，该谓词基于小于比较关系进行排序。

如果 **find** 的返回值赋予 **const_iterator**，则无法修改多重映射对象。 如果 **find** 的返回值赋予 **iterator**，则可以修改多重映射对象。

### <a name="example"></a>示例

```cpp
// compile with: /EHsc /W4 /MTd
#include <map>
#include <iostream>
#include <vector>
#include <string>
#include <utility>  // make_pair()

using namespace std;

template <typename A, typename B> void print_elem(const pair<A, B>& p) {
    cout << "(" << p.first << ", " << p.second << ") ";
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
    multimap<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting multimap m1 is (key, value):" << endl;
    print_collection(m1);

    vector<pair<int, string>> v;
    v.push_back(make_pair(43, "Tc"));
    v.push_back(make_pair(41, "Nb"));
    v.push_back(make_pair(46, "Pd"));
    v.push_back(make_pair(42, "Mo"));
    v.push_back(make_pair(44, "Ru"));
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate

    cout << "Inserting the following vector data into m1:" << endl;
    print_collection(v);

    m1.insert(v.begin(), v.end());

    cout << "The modified multimap m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}

```

## <a name="get_allocator"></a>  multimap::get_allocator

返回用于构造多重映射的分配器对象的一个副本。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>返回值

多重映射使用的分配器。

### <a name="remarks"></a>备注

多重映射类的分配器指定类管理存储的方式。 C++ 标准库容器类提供的默认分配器足以满足大多编程需求。 编写和使用你自己的分配器类是高级 C++ 主题。

### <a name="example"></a>示例

```cpp
// multimap_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int>::allocator_type m1_Alloc;
   multimap <int, int>::allocator_type m2_Alloc;
   multimap <int, double>::allocator_type m3_Alloc;
   multimap <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multimap <int, int> m1;
   multimap <int, int, allocator<int> > m2;
   multimap <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a multimap m4
   // with the allocator of multimap m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated via the other
   if( m1_Alloc == m4_Alloc )
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

## <a name="insert"></a>  multimap::insert

将一个元素或元素范围插入到多重映射中。

```cpp
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

|参数|描述|
|-|-|
|`Val`|要插入到多重映射中的元素的值。|
|`Where`|开始搜索正确插入点的位置。 （如果该点紧贴在 `Where` 之前，则插入可能发生在分期常量时间内而非对数时间内。)|
|`ValTy`|指定 map 可用于构造 [value_type](../standard-library/map-class.md#value_type) 元素的自变量类型并将 `Val` 作为自变量完美转发的模板参数。|
|`First`|要复制的第一个元素的位置。|
|`Last`|要复制的最后一个元素以外的位置。|
|`InputIterator`|满足[输入迭代器](../standard-library/input-iterator-tag-struct.md)需求的模板函数自变量，该输入迭代器指向可用于构造 [value_type](../standard-library/map-class.md#value_type) 对象的类型的元素。|
|`IList`|从中复制元素的 [initializer_list](../standard-library/initializer-list.md)。|

### <a name="return-value"></a>返回值

单个元素插入的成员函数 (1) 和 (2) 返回迭代器，该迭代器指向将新元素插入到多重映射中的位置。

附带提示的单个元素的成员函数 (3) 和 (4) 返回迭代器，该迭代器指向将新元素插入到多重映射中的位置。

### <a name="remarks"></a>备注

指针或引用不会因为此函数而失效，但是它可能会使所有指向容器的迭代器都失效。

在插入单个元素的过程中，如果引发异常，则不会修改该容器的状态。 在插入多个元素的过程中，如果引发异常，则会使容器处于未指定但有效的状态。

容器的 [value_type](../standard-library/map-class.md#value_type) 是属于该容器的 typedef；对于映射，`multimap<K, V>::value_type` 是 `pair<const K, V>`。 元素的值是一个有序对，其中第一个组件相当于键值，第二个组件相当于该元素的数据值。

范围成员函数 (5) 将元素值序列插入到多重映射中，它对应于迭代器在范围 `[First, Last)` 中所处理的每一个元素；因此，不会插入 `Last`。 容器成员函数 `end()` 是指容器中最后一个元素之后的位置，例如，`m.insert(v.begin(), v.end());` 语句会将 `v` 的所有元素插入到 `m` 中。

初始值设定项列表成员函数 (6) 使用 [initializer_list](../standard-library/initializer-list.md) 将元素复制到映射中。

有关就地构造的元素的插入（即不会执行复制或移动操作），请参阅 [multimap::emplace](#emplace) 和 [multimap::emplace_hint](#emplace_hint)。

### <a name="example"></a>示例

```cpp
// multimap_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
#include <vector>
#include <utility>  // make_pair()

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    multimap<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    m1.insert(make_pair(1, 111));

    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multimap<int, int> m2;
    vector<pair<int, int>> v;
    v.push_back(make_pair(43, 294));
    v.push_back(make_pair(41, 262));
    v.push_back(make_pair(45, 330));
    v.push_back(make_pair(42, 277));
    v.push_back(make_pair(44, 311));

    cout << "Inserting the following vector data into m2:" << endl;
    print(v);

    m2.insert(v.begin(), v.end());

    cout << "The modified key and mapped values of m2 are:" << endl;
    print(m2);
    cout << endl;

    // The templatized versions move-constructing elements
    multimap<int, string>  m3;
    pair<int, string> ip1(475, "blue"), ip2(510, "green");

    // single element
    m3.insert(move(ip1));
    cout << "After the first move insertion, m3 contains:" << endl;
    print(m3);

    // single element with hint
    m3.insert(m3.end(), move(ip2));
    cout << "After the second move insertion, m3 contains:" << endl;
    print(m3);
    cout << endl;

    multimap<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}

```

## <a name="iterator"></a>  multimap::iterator

一种类型，此类型提供可读取或修改多重映射中的任何元素的双向迭代器。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>备注

**迭代器**由多重映射指向的对象定义[value_type](#value_type)，类型`pair` * \< * **const 密钥**，**类型 * * * >*。 键值通过第一个成员对可用，已映射元素的值通过对的第二个成员可用。

若要取消引用指向 multimap 中元素的 **iterator**`Iter`，请使用 **->** 运算符。

若要访问元素的键值，请使用 `Iter` -> **first**，其作用与 (\* `Iter`). **first** 相同。 若要访问元素的映射值，请使用 `Iter` -> **second**，其作用与 (\* `Iter`). **second** 相同。

**iterator** 类型可用于修改元素的值。

### <a name="example"></a>示例

有关如何声明和使用 **iterator** 的示例，请参阅 [begin](#begin) 的示例。

## <a name="key_comp"></a>  multimap::key_comp

检索用于对多重映射中的键进行排序的比较对象副本。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>返回值

返回多重映射用来对其元素进行排序的函数对象。

### <a name="remarks"></a>备注

存储对象会定义成员函数

**bool operator**( **const Key&** *x*, **const Key&** *y*);

如果在排序顺序中 *x* 严格位于 *y* 之前，则返回 true。

### <a name="example"></a>示例

```cpp
// multimap_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of m1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of m1."
           << endl;
   }

   multimap <int, int, greater<int> > m2;
   multimap <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of m2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of m2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.
```

## <a name="key_compare"></a>  multimap::key_compare

一种提供函数对象的类型，该函数对象可比较两个排序键以确定多重映射中两个元素的相对顺序。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>备注

**key_compare** 是模板参数 `Traits` 的同义词。

有关 `Traits` 的详细信息，请参阅 [multimap 类](../standard-library/multimap-class.md)主题。

### <a name="example"></a>示例

有关如何声明和使用 `key_compare` 的示例，请参阅 [key_comp](#key_comp) 的示例。

## <a name="key_type"></a>  multimap::key_type

一种类型，此类型描述组成多重映射中每个元素的排序键对象。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>备注

**key_type** 类型是模板参数 `Key` 的同义词。

有关 `Key` 的详细信息，请参阅 [multimap 类](../standard-library/multimap-class.md)主题的备注部分。

### <a name="example"></a>示例

有关如何声明和使用 `key_type` 的示例，请参阅 [value_type](#value_type) 的示例。

## <a name="lower_bound"></a>  multimap::lower_bound

返回一个迭代器，此迭代器指向多重映射中其键等于或大于指定键的第一个元素。

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>参数

`key` 要与所搜索多重映射中的元素的排序键进行比较的自变量键。

### <a name="return-value"></a>返回值

一个迭代器或 `const_iterator`，它会发现多重映射中其键等于或大于参数键的元素的位置，或如果未找到键的匹配项，则发现多重映射中最后一个元素之后的位置。

如果将 `lower_bound` 的返回值赋予 `const_iterator`，则无法修改多重映射对象。 如果 `lower_bound` 的返回值赋予 **iterator**，则可以修改多重映射对象。

### <a name="example"></a>示例

```cpp
// multimap_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The element of multimap m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.lower_bound( 3 );
   cout << "The first element of multimap m1 with a key of 3 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
              << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
                << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1.lower_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key matching\n"
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( m1_RcIter == --m1.end( ) )
      cout << "This is the last element of multimap m1."
           << endl;
   else
      cout << "This is not the last element of multimap m1."
           << endl;
}
```

```Output
The element of multimap m1 with a key of 2 is: 20.
The first element of multimap m1 with a key of 3 is: 20.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key matching
that of the last element is: 20.
This is not the last element of multimap m1.
```

## <a name="mapped_type"></a>  multimap::mapped_type

一种类型，它代表多重映射中存储的数据类型。

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>备注

`mapped_type` 是模板参数 `Type` 的同义词。

有关 `Type` 的详细信息，请参阅 [multimap 类](../standard-library/multimap-class.md)主题。

### <a name="example"></a>示例

有关如何声明和使用 `key_type` 的示例，请参阅 [value_type](#value_type) 的示例。

## <a name="max_size"></a>  multimap::max_size

返回多重映射的最大长度。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>返回值

多重映射的最大可取长度。

### <a name="example"></a>示例

```cpp
// multimap_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the multimap is " << i << "." << endl;
}
```

## <a name="multimap"></a>  multimap::multimap

构造一个空的或者是其他某个多重映射的全部或部分副本的多重映射。

```cpp
multimap();

explicit multimap(
    const Traits& Comp);

multimap(
    const Traits& Comp,
    const Allocator& Al);

map(
    const multimap& Right);

multimap(
    multimap&& Right);

multimap(
    initializer_list<value_type> IList);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multimap(
 InputIterator First,
    InputIterator Last);

template <class InputIterator>
multimap(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
multimap(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|`Al`|要用于此多重映射对象的存储分配器类，默认为分配器。|
|`Comp`|用于对映射中的元素排序的类型 **constTraits** 的比较函数，默认为 **Traits**。|
|`Right`|所构造集要作为其副本的映射。|
|`First`|要复制的范围元素中的第一个元素的位置。|
|`Last`|要复制的元素范围以外的第一个元素的位置。|
|`IList`|从中复制元素的 initializer_list。|

### <a name="remarks"></a>备注

所有构造函数存储一种类型的分配器对象，此类对象管理多重映射的内存存储，且事后可通过调用 [get_allocator](#get_allocator) 返回。 此分配器参数在类声明中常省略，并预处理用于代替备用分配器的宏。

所有构造函数初始化其多重映射。

所有构造函数会存储类型为 `Traits` 的函数对象，此对象用于在多重映射的键之间建立顺序，且事后可通过调用 [key_comp](#key_comp) 返回。

前三个构造函数均指定空的起始多重映射，此外，第二个函数还指定用于建立元素顺序的比较函数 (`Comp`) 的类型，第三个函数还显式指定了要使用的分配器类型 (`Al`)。 关键字 `explicit` 取消了某些种类的自动类型转换。

第四个构造函数指定多重映射 `Right` 的副本。

第五个构造函数通过移动 `Right` 指定多重映射的副本。

第六、第七和第八个构造函数复制 initializer_list 的成员。

接下来的三个构造函数复制映射的范围 `[First, Last)`，其指定类 **Traits** 和 Allocator 的比较函数类型和分配器时更加明确。

### <a name="example"></a>示例

```cpp
// multimap_ctor.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;

    // Create an empty multimap m0 of key type integer
    multimap <int, int> m0;

    // Create an empty multimap m1 with the key comparison
    // function of less than, then insert 4 elements
    multimap <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty multimap m2 with the key comparison
    // function of geater than, then insert 2 elements
    multimap <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a multimap m3 with the
    // allocator of multimap m1
    multimap <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    multimap <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, multimap m4, of multimap m1
    multimap <int, int> m4(m1);

    // Create a multimap m5 by copying the range m1[ first,  last)
    multimap <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    multimap <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a multimap m6 by copying the range m4[ first,  last)
    // and with the allocator of multimap m2
    multimap <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    multimap <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for (auto i : m2)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m3 =";
    for (auto i : m3)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m4 =";
    for (auto i : m4)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m5 =";
    for (auto i : m5)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m6 =";
    for (auto i : m6)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m8 by copying in an initializer_list
    multimap<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m9 with an initializer_list and a comparator
    multimap<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m10 with an initializer_list, a comparator, and an allocator
    multimap<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

}

```

## <a name="op_eq"></a>multimap::operator=

将一个多重映射中的元素替换为另一多重映射副本。

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>参数

|参数|描述|
|-|-|
|`right`|正在复制到 `multimap` 的 [multimap](../standard-library/multimap-class.md)。|

### <a name="remarks"></a>备注

清除 `multimap` 中的任何现有元素后，`operator=` 会将 `right` 的内容复制或移动到 `multimap`。

### <a name="example"></a>示例

```cpp
// multimap_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   multimap<int, int> v1, v2, v3;
   multimap<int, int>::iterator iter;

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

## <a name="pointer"></a>  multimap::pointer

一种类型，此类型提供指向多重映射中元素的指针。

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>备注

**pointer** 类型可用于修改元素的值。

在大多数情况下，应使用 [iterator](#iterator) 访问多重映射对象中的元素。

## <a name="rbegin"></a>  multimap::rbegin

返回一个迭代器，此迭代器用于发现反向多重映射中的第一个元素。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>返回值

一个发现反向多重映射中的第一个元素或发现非反向多重映射中的最后一个元素的的反向双向迭代器。

### <a name="remarks"></a>备注

`rbegin` 用于反向多重映射，正如 [begin](#begin) 用于多重映射一样。

如果将 `rbegin` 的返回值赋予 `const_reverse_iterator`，则无法修改多重映射对象。 如果将 `rbegin` 的返回值赋予 `reverse_iterator`，则可以修改多重映射对象。

`rbegin` 可用于向后循环访问多重映射。

### <a name="example"></a>示例

```cpp
// multimap_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // throught a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // throught a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the first element in the reversed multimap is 2.
```

## <a name="reference"></a>  multimap::reference

一种类型，此类型提供对存储在多重映射中的元素的引用。

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>示例

```cpp
// multimap_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the multimap is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  multimap::rend

返回一个迭代器，此迭代器用于发现反向多重映射中最后一个元素之后的位置。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>返回值

用于发现反向多重映射中最后一个元素之后的位置（非反向多重映射中第一个元素之前的位置）的反向双向迭代器。

### <a name="remarks"></a>备注

`rend` 用于反向多重映射，正如 [end](../standard-library/map-class.md#end) 用于多重映射一样。

如果将 `rend` 的返回值赋予 `const_reverse_iterator`，则无法修改多重映射对象。 如果将 `rend` 的返回值赋予 `reverse_iterator`，则可以修改多重映射对象。

`rend` 可用于测试反向迭代器是否已到达其多重映射末尾。

不应对 `rend` 返回的值取消引用。

### <a name="example"></a>示例

```cpp
// multimap_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // throught a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // throught a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the last element in the reversed multimap is 2.
```

## <a name="reverse_iterator"></a>  multimap::reverse_iterator

一种类型，此类型提供可读取或修改反向多重映射中的元素的双向迭代器。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>备注

`reverse_iterator` 类型用于反向循环访问多重映射。

`reverse_iterator`由多重映射指向的对象定义[value_type](#value_type)，类型`pair` * \< * **const 密钥**，**类型 * * * >*。 键值通过第一个成员对可用，已映射元素的值通过对的第二个成员可用。

若要取消引用`reverse_iterator``rIter`多重映射中指向的元素，使用-> 运算符。

若要访问元素的键值，请使用 `rIter` -> **first**，其作用与 (\* `rIter`). **first** 相同。 若要访问元素的映射值，请使用 `rIter` -> **second**，其作用与 (\* `rIter`). **first** 相同。

### <a name="example"></a>示例

有关如何声明和使用 `reverse_iterator` 的示例，请参阅 [rbegin](#rbegin) 的示例。

## <a name="size"></a>  multimap::size

返回 multimap 中的元素数量。

```cpp
size_type size() const;
```

### <a name="return-value"></a>返回值

multimap 的当前长度。

### <a name="example"></a>示例

下面的示例演示如何使用 multimap::size 成员函数。

```cpp
// multimap_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    multimap<int, int> m1, m2;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The multimap length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The multimap length is now " << i << "." << endl;
}
```

```Output
The multimap length is 1.
The multimap length is now 2.
```

## <a name="size_type"></a>  multimap::size_type

一种无符号整数类型，此类型会对多重映射中元素的数量计数。

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>示例

有关如何声明和使用 `size_type` 的示例，请参阅 [size](#size) 的示例

## <a name="swap"></a>  multimap::swap

交换两个多重映射的元素。

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`right` 多重映射提供要交换的元素或其元素将要与那些多重映射交换 multimap `left`。

### <a name="remarks"></a>备注

成员函数不会使在彼此交换元素的两个多重映射中指定元素的任何引用、指针或迭代器无效。

### <a name="example"></a>示例

```cpp
// multimap_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   multimap <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   m1.swap( m2 );

   cout << "After swapping with m2, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original multimap m1 is: 10 20 30.
After swapping with m2, multimap m1 is: 100 200.
After swapping with m3, multimap m1 is: 300.
```

## <a name="upper_bound"></a>  multimap::upper_bound

返回一个迭代器，此迭代器指向多重映射中其键大于指定键的第一个元素。

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>参数

`key` 要与所搜索多重映射中的元素的排序键进行比较的自变量键。

### <a name="return-value"></a>返回值

一个迭代器或 `const_iterator`，它会发现多重映射中其键大于参数键的元素的位置，或如果未找到键的匹配项，则发现多重映射中最后一个元素之后的位置。

如果将返回值赋予 `const_iterator`，则无法修改多重映射对象。 如果将返回值赋予 **iterator**，则可以修改多重映射对象。

### <a name="example"></a>示例

```cpp
// multimap_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m1.insert ( Int_Pair ( 3, 40 ) );

   m1_RcIter = m1.upper_bound( 1 );
   cout << "The 1st element of multimap m1 with "
        << "a key greater than 1 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of multimap m1 with a key "
        << " greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a derefenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1.upper_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of multimap m1 with a key greater than 1 is: 20.
The first element of multimap m1 with a key  greater than 2 is: 30.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a>  multimap::value_comp

此成员函数返回一个函数对象，该函数对象可通过比较多重映射中元素的键值来确定元素顺序。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>返回值

返回多重映射用来对其元素进行排序的比较函数对象。

### <a name="remarks"></a>备注

对于多重映射 *m*，如果 *e*1( *k*1, *d*1) 和 *e*2( *k*2, `d`2) 两个元素为类型 `value_type` 的对象，其中 *k*1 和 *k*2 为 `key_type` 类型的键，`d`1 和 `d`2 为 `mapped_type` 类型的数据，则 *m.*`value_comp`( *e*1, *e*2) 等同于 *m.*`key_comp`( *k*1, *k*2)。

### <a name="example"></a>示例

```cpp
// multimap_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   multimap<int,int>::iterator Iter1, Iter2;

   Iter1= m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= m1.insert ( multimap <int, int> :: value_type ( 2, 5 ) );

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

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a>  multimap::value_type

一种类型，它表示存储为映射中元素的对象的类型。

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>示例

```cpp
// multimap_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   multimap <int, int> m1;
   multimap <int, int> :: key_type key1;
   multimap <int, int> :: mapped_type mapped1;
   multimap <int, int> :: value_type value1;
   multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitely to avoid implicit type conversion
   m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   m1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>请参阅

[\<映射 > 成员](http://msdn.microsoft.com/en-us/7e8f0bc2-6034-40f6-9d14-76d4cef86308)<br/>
[容器](../cpp/containers-modern-cpp.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
