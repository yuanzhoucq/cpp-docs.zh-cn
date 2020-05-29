---
title: reverse_iterator 类
ms.date: 03/27/2019
f1_keywords:
- xutility/std::reverse_iterator
- iterator/std::reverse_iterator::difference_type
- iterator/std::reverse_iterator::iterator_type
- iterator/std::reverse_iterator::pointer
- iterator/std::reverse_iterator::reference
- iterator/std::reverse_iterator::base
- iterator/std::reverse_iterator::operator_star
helpviewer_keywords:
- std::reverse_iterator [C++]
- std::reverse_iterator [C++], difference_type
- std::reverse_iterator [C++], iterator_type
- std::reverse_iterator [C++], pointer
- std::reverse_iterator [C++], reference
- std::reverse_iterator [C++], base
- std::reverse_iterator [C++], operator_star
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
ms.openlocfilehash: 882d0f7f4930e9d809098a29384a962d0aa8f4ea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373434"
---
# <a name="reverse_iterator-class"></a>reverse_iterator 类

类模板是一个迭代器适配器，用于描述反向迭代器对象，该对象类似于随机访问或双向迭代器，仅相反。 它允许向后遍历范围。

## <a name="syntax"></a>语法

```cpp
template <class RandomIterator>
class reverse_iterator
```

### <a name="parameters"></a>参数

随机迭代器 表示要适应的迭代器的类型，可反向操作。

## <a name="remarks"></a>备注

现有 C++ 标准库容器还定义 `reverse_iterator` 和 `const_reverse_iterator` 类型，并拥有返回反向迭代器的成员函数 `rbegin` 和 `rend`。 这些迭代器具有覆盖语义。 适配器`reverse_iterator`补充此功能，因为它提供插入语义，也可以与流一起使用。

`reverse_iterator`需要`operator+=`双向迭代器的不能调用任何成员函数`operator+`、、`operator-=``operator-`或`operator[]`，这些函数只能与随机访问迭代器一起使用。

迭代器的范围是 [*第一*个，*最后*]，左侧的方括号表示包含*第一*个，右侧的括号表示包含的元素最多，但不包括*最后一个*本身。 相同的元素包含在反向序列中 =**首先转稿** - *first*，**最后修订** - *），因此*，如果*最后*一个元素是序列中的一个结束元素，则第一个元素在反向序列中**首先转稿** - *first*指向\*（*最后*- 1）。 将所有反向迭代器与其基础迭代器关联的标识是：

&\*（ **reverse_iterator** （ *i* ） \*= &（ *i* - 1 ）.

在实际操作中，这意味着在反向序列中，reverse_iterator 将引用迭代器在原有序列中引用的元素之外（右侧）一个位置的元素。 因此，如果迭代器在序列 (2, 4, 6, 8) 中发现元素 6，则 `reverse_iterator` 将在反向序列 (8, 6, 4, 2) 中发现元素 4。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[reverse_iterator](#reverse_iterator)|构造默认 `reverse_iterator` 或从基础迭代器构造 `reverse_iterator`。|

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|[difference_type](#difference_type)|一种类型，此类型提供引用同一容器中的元素的两个 `reverse_iterator` 之间的差异。|
|[iterator_type](#iterator_type)|一种类型，此类型为 `reverse_iterator` 提供基础迭代器。|
|[指针 (pointer)](#pointer)|一种类型，此类型提供指向 `reverse_iterator` 所发现元素的指针。|
|[参考](#reference)|一种类型，此类型提供对 `reverse_iterator` 所发现元素的引用。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[base](#base)|将基础迭代器从其 `reverse_iterator` 恢复。|

### <a name="operators"></a>运算符

|操作员|说明|
|-|-|
|[operator_star](#op_star)|返回 `reverse_iterator` 发现的元素。|
|[运算符*](#op_add)|将偏移量添加到迭代器，并返回在新偏移位置处发现插入元素的新 `reverse_iterator`。|
|[运算符*](#op_add_add)|将 `reverse_iterator` 递增到下一元素。|
|[运算符*](#op_add_eq)|从 `reverse_iterator` 添加指定偏移量。|
|[操作员-](#operator-)|从 `reverse_iterator` 减去偏移量，并返回在偏移位置处发现元素的 `reverse_iterator`。|
|[运算符--](#operator--)|将 `reverse_iterator` 递减到前一元素。|
|[运算符-*](#operator-_eq)|从 `reverse_iterator` 减去指定偏移量。|
|[运算符>](#op-arrow)|返回指向 `reverse_iterator` 发现的元素的指针。|
|[operator&#91;&#93;](#op_at)|返回对于从 `reverse_iterator` 发现的元素偏移指定个位置的元素的引用。|

## <a name="requirements"></a>要求

**标头：** \<iterator>

**命名空间:** std

## <a name="reverse_iteratorbase"></a><a name="base"></a>reverse_iterator：基数

将基础迭代器从其 `reverse_iterator` 恢复。

```cpp
RandomIterator base() const;
```

### <a name="return-value"></a>返回值

构成 `reverse_iterator` 的基础的迭代器。

### <a name="remarks"></a>备注

将所有反向迭代器与其基础迭代器关联的标识是：

&\*（ `reverse_iterator` *i* ） = \*&（ *i* - 1 ）.

在实际操作中，这意味着在反向序列中，`reverse_iterator` 将引用迭代器在原有序列中引用的元素之外（右侧）一个位置的元素。 因此，如果迭代器在序列 (2, 4, 6, 8) 中发现元素 6，则 `reverse_iterator` 将在反向序列 (8, 6, 4, 2) 中发现元素 4。

### <a name="example"></a>示例

```cpp
// reverse_iterator_base.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );
   cout << "The iterator pos points to: " << *pos << "." << endl;

   typedef reverse_iterator<vector<int>::iterator>::iterator_type it_vec_int_type;

   reverse_iterator<it_vec_int_type> rpos ( pos );
   cout << "The reverse_iterator rpos points to: " << *rpos
        << "." << endl;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
```

## <a name="reverse_iteratordifference_type"></a><a name="difference_type"></a>reverse_iterator：:d）类型

一种类型，此类型提供引用同一容器中的元素的两个 `reverse_iterator` 之间的差异。

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type  difference_type;
```

### <a name="remarks"></a>备注

`reverse_iterator` 差异类型与迭代器差异类型相同。

该类型是迭代器特征`iterator_traits`\<类型名称**RandomIter：:pointer**> **的同**义词。

### <a name="example"></a>示例

请参阅 [reverse_iterator::operator&#91;&#93;](#op_at)，获取关于如何声明和使用 `difference_type` 的示例。

## <a name="reverse_iteratoriterator_type"></a><a name="iterator_type"></a>reverse_iterator：iterator_type

一种类型，此类型为 `reverse_iterator` 提供基础迭代器。

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>备注

类型是模板参数 `Iterator` 的同义词。

### <a name="example"></a>示例

请参阅 [reverse_iterator::base](#base)，获取关于如何声明和使用 `iterator_type` 的示例。

## <a name="reverse_iteratoroperator"></a><a name="op_star"></a>reverse_iterator：：操作员\*

返回由 reverse_iterator 寻址的元素。

```cpp
reference operator*() const;
```

### <a name="return-value"></a>返回值

由 reverse_iterator 寻址的元素的值。

### <a name="remarks"></a>备注

运算符返回\*（**当前**- 1）。

### <a name="example"></a>示例

```cpp
// reverse_iterator_op_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );

   // Declare a difference type for a parameter
   // declare a reference return type
   reverse_iterator<vector<int>::iterator>::reference refpos = *pos;
   cout << "The iterator pos points to: " << refpos << "." << endl;
}
```

## <a name="reverse_iteratoroperator"></a><a name="op_add"></a>reverse_iterator：：操作员*

将偏移量添加到迭代器，并返回在新偏移位置处发现插入元素的新 `reverse_iterator`。

```cpp
reverse_iterator<RandomIterator> operator+(difference_type Off) const;
```

### <a name="parameters"></a>参数

*关闭*\
要添加到反向迭代器的偏移量。

### <a name="return-value"></a>返回值

寻址偏移元素的 `reverse_iterator`。

### <a name="remarks"></a>备注

仅当 `reverse_iterator` 满足随机访问迭代器的要求时才能使用此成员函数。

### <a name="example"></a>示例

```cpp
// reverse_iterator_op_add.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 + 2; // offset added
   cout << "After the +2 offset, the iterator rVPOS2 points\n"
        << " to the 3rd element in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS2 points
to the 3rd element in the reversed sequence: 6.
```

## <a name="reverse_iteratoroperator"></a><a name="op_add_add"></a>reverse_iterator：：操作员*

向上一个元素逐量添加 reverse_iterato。

```cpp
reverse_iterator<RandomIterator>& operator++();
reverse_iterator<RandomIterator> operator++(int);
```

### <a name="return-value"></a>返回值

第一个运算符返回前置递增的 `reverse_iterator`，而第二个运算符为后置递增运算符，返回递增的 `reverse_iterator` 的副本。

### <a name="remarks"></a>备注

仅当 `reverse_iterator` 满足双向迭代器的要求时才能使用此成员函数。

### <a name="example"></a>示例

```cpp
// reverse_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1++;  // postincrement, preincrement: ++rVPSO1

   cout << "After incrementing, the iterator rVPOS1 points\n"
        << " to the second element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 9.
After incrementing, the iterator rVPOS1 points
to the second element in the reversed sequence: 7.
```

## <a name="reverse_iteratoroperator"></a><a name="op_add_eq"></a>reverse_iterator：：操作员*

从 reverse_iterator 添加指定偏移量。

```cpp
reverse_iterator<RandomIterator>& operator+=(difference_type Off);
```

### <a name="parameters"></a>参数

*关闭*\
迭代器要递增的偏移量。

### <a name="return-value"></a>返回值

由 `reverse_iterator` 寻址的元素的引用。

### <a name="example"></a>示例

```cpp
// reverse_iterator_op_addoff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1+=2;   // addition of an offset
   cout << "After the +2 offset, the iterator rVPOS1 now points\n"
        << " to the third element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS1 now points
to the third element in the reversed sequence: 6.
```

## <a name="reverse_iteratoroperator-"></a><a name="operator-"></a>reverse_iterator：操作员-

从 `reverse_iterator` 减去偏移量，并返回在偏移位置处发现元素的 `reverse_iterator`。

```cpp
reverse_iterator<RandomIterator> operator-(difference_type Off) const;
```

### <a name="parameters"></a>参数

*关闭*\
要从 everse_iterator 中减去的偏移量。

### <a name="return-value"></a>返回值

寻址偏移元素的 `reverse_iterator`。

### <a name="remarks"></a>备注

仅当 `reverse_iterator` 满足随机访问迭代器的要求时才能使用此成员函数。

### <a name="example"></a>示例

```cpp
// reverse_iterator_op_sub.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 - 2; // offset subtracted
   cout << "After the -2 offset, the iterator rVPOS2 points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS2 points
to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="reverse_iteratoroperator--"></a><a name="operator--"></a>reverse_iterator：运算符 --

向上一个元素逐量递减 reverse_iterato。

```cpp
reverse_iterator<RandomIterator>& operator--();
reverse_iterator<RandomIterator> operator--(int);
```

### <a name="return-value"></a>返回值

第一个运算符返回前置递减的 `reverse_iterator`，而第二个运算符为后置递减运算符，返回递减的 `reverse_iterator` 的副本。

### <a name="remarks"></a>备注

仅当 `reverse_iterator` 满足双向迭代器的要求时才能使用此成员函数。

### <a name="example"></a>示例

```cpp
// reverse_iterator_op_decr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;
   rVPOS1--;  // postdecrement, predecrement: --rVPSO1

   cout << "After the decrement, the iterator rVPOS1 points\n"
        << " to the next-to-last element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 1.
After the decrement, the iterator rVPOS1 points
to the next-to-last element in the reversed sequence: 3.
```

## <a name="reverse_iteratoroperator-"></a><a name="operator-_eq"></a>reverse_iterator：：操作员*

从 `reverse_iterator` 减去指定偏移量。

```cpp
reverse_iterator<RandomIterator>& operator-=(difference_type Off);
```

### <a name="parameters"></a>参数

*关闭*\
要从 `reverse_iterator` 中减去的偏移量。

### <a name="remarks"></a>备注

仅当 `reverse_iterator` 满足随机访问迭代器的要求时才能使用此成员函数。

运算符计算**当前** + *Off，* 然后返回**\*此**。

### <a name="example"></a>示例

```cpp
// reverse_iterator_op_suboff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1-=2;      // Subtraction of an offset
   cout << "After the -2 offset, the iterator rVPOS1 now points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS1 now points
to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="reverse_iteratoroperator-gt"></a><a name="op-arrow"></a>reverse_iterator：操作员-&gt;

返回指向 `reverse_iterator` 发现的元素的指针。

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>返回值

指向由 `reverse_iterator` 寻址的元素的指针。

### <a name="remarks"></a>备注

运算符**&\*返回\*此**。

### <a name="example"></a>示例

```cpp
// reverse_iterator_ptrto.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back(pVector::value_type(1,2));
   vec.push_back(pVector::value_type(3,4));
   vec.push_back(pVector::value_type(5,6));

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::reverse_iterator rpvIter;
   cout << "The vector vec reversed is:\n( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++ )
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "The iterator pos points to:\n( " << pos -> first << ", "
   << pos -> second << " )" << endl << endl;

   pVector::reverse_iterator rpos (pos);

   // Use operator -> with return type: why type int and not int*
   int fint = rpos -> first;
   int sint = rpos -> second;

   cout << "The reverse_iterator rpos points to:\n( " << fint << ", "
   << sint << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The reverse_iterator rpos points to:
( 1, 2 )
```

## <a name="reverse_iteratoroperator"></a><a name="op_at"></a>reverse_iterator：：操作员*

返回对于从 `reverse_iterator` 发现的元素偏移指定个位置的元素的引用。

```cpp
reference operator[](difference_type Off) const;
```

### <a name="parameters"></a>参数

*关闭*\
`reverse_iterator` 地址的偏移量。

### <a name="return-value"></a>返回值

对元素偏移量的引用。

### <a name="remarks"></a>备注

运算符返回<strong>\*</strong>（**\*这** + `Off`）。

### <a name="example"></a>示例

```cpp
// reverse_iterator_ret_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 8 );
   reverse_iterator<vector<int>::iterator> rpos ( pos );

   // Declare a difference type for a parameter
   reverse_iterator<vector<int>::iterator>::difference_type diff = 2;

   cout << "The iterator pos points to: " << *pos << "." << endl;
   cout << "The iterator rpos points to: " << *rpos << "." << endl;

   // Declare a reference return type & use operator[]
   reverse_iterator<vector<int>::iterator>::reference refrpos = rpos [diff];
   cout << "The iterator rpos now points to: " << refrpos << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator pos points to: 8.
The iterator rpos points to: 6.
The iterator rpos now points to: 2.
```

## <a name="reverse_iteratorpointer"></a><a name="pointer"></a>reverse_iterator：:p奥米特

一种类型，此类型提供指向 `reverse_iterator` 所发现元素的指针。

```cpp
typedef typename iterator_traits<RandomIterator>::pointer pointer;
```

### <a name="remarks"></a>备注

该类型是迭代器特征`iterator_traits`\<类型名称*RandomIter：:pointer*> **的同**义词。

### <a name="example"></a>示例

```cpp
// reverse_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back( pVector::value_type( 1,2 ) );
   vec.push_back( pVector::value_type( 3,4 ) );
   vec.push_back( pVector::value_type( 5,6 ) );

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n" << "( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl;

   pVector::reverse_iterator rpvIter;
   cout << "\nThe vector vec reversed is:\n" << "( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++)
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "\nThe iterator pos points to:\n"
        << "( " << pos -> first << ", "
        << pos -> second << " )" << endl;

   pVector::reverse_iterator rpos (pos);
   cout << "\nThe iterator rpos points to:\n"
        << "( " << rpos -> first << ", "
        << rpos -> second << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The iterator rpos points to:
( 1, 2 )
```

## <a name="reverse_iteratorreference"></a><a name="reference"></a>reverse_iterator：参考

一种类型，此类型提供对 reverse_iterator 所发现元素的引用。

```cpp
typedef typename iterator_traits<RandomIterator>::reference reference;
```

### <a name="remarks"></a>备注

该类型是迭代器特征类型`iterator_traits`\<名称*RandomIterer：：：*> **引用**的同义词。

### <a name="example"></a>示例

有关如何声明和使用 的示例，请参阅[reverse_iterator：：运算符&#91;&#93;](#op_at)或`reference`[reverse_iterator：：运算符*。](#op_star)

## <a name="reverse_iteratorreverse_iterator"></a><a name="reverse_iterator"></a>reverse_iterator：：reverse_iterator

构造默认 `reverse_iterator` 或从基础迭代器构造 `reverse_iterator`。

```cpp
reverse_iterator();
explicit reverse_iterator(RandomIterator right);

template <class Type>
reverse_iterator(const reverse_iterator<Type>& right);
```

### <a name="parameters"></a>参数

*对*\
适用于 `reverse_iterator` 的迭代器。

### <a name="return-value"></a>返回值

默认的 `reverse_iterator` 或用于调整基础迭代器的 `reverse_iterator`。

### <a name="remarks"></a>备注

将所有反向迭代器与其基础迭代器关联的标识是：

&\*（ `reverse_iterator` *i* ） = \*&（ *i* - 1 ）.

在实际操作中，这意味着在反向序列中，reverse_iterator 将引用迭代器在原有序列中引用的元素之外（右侧）一个位置的元素。 因此，如果迭代器在序列 (2, 4, 6, 8) 中发现元素 6，则 `reverse_iterator` 将在反向序列 (8, 6, 4, 2) 中发现元素 4。

### <a name="example"></a>示例

```cpp
// reverse_iterator_reverse_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 4 );
   cout << "The iterator pos = " << *pos << "." << endl;

   vector <int>::reverse_iterator rpos ( pos );
   cout << "The reverse_iterator rpos = " << *rpos
        << "." << endl;
}
```

## <a name="see-also"></a>另请参阅

[\<迭代器>](../standard-library/iterator.md)\
[C++标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
