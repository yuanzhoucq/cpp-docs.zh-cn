---
title: reverse_iterator 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- xutility/std::reverse_iterator
- iterator/std::reverse_iterator::difference_type
- iterator/std::reverse_iterator::iterator_type
- iterator/std::reverse_iterator::pointer
- iterator/std::reverse_iterator::reference
- iterator/std::reverse_iterator::base
- iterator/std::reverse_iterator::operator_star
dev_langs:
- C++
helpviewer_keywords:
- std::reverse_iterator [C++]
- std::reverse_iterator [C++], difference_type
- std::reverse_iterator [C++], iterator_type
- std::reverse_iterator [C++], pointer
- std::reverse_iterator [C++], reference
- std::reverse_iterator [C++], base
- std::reverse_iterator [C++], operator_star
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6bd2f74919ba757f7154d534e8dbca91510cdeb
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="reverseiterator-class"></a>reverse_iterator 类

此模板类是迭代器适配器，描述在行为上与随机访问迭代器或双向迭代器类似（只不过方向相反）的反向迭代器对象。 它允许向后遍历范围。

## <a name="syntax"></a>语法

```cpp
template <class RandomIterator>
class reverse_iterator
```

### <a name="parameters"></a>参数

RandomIterator 表示要进行适配化以反向操作的迭代器的类型。

## <a name="remarks"></a>备注

现有 C++ 标准库容器还定义 `reverse_iterator` 和 `const_reverse_iterator` 类型，并拥有返回反向迭代器的成员函数 `rbegin` 和 `rend`。 这些迭代器具有覆盖语义。 `reverse_iterator`适配器补充此功能，因为它提供插入语义，并且还与流一起使用。

`reverse_iterator`需要双向迭代器不能调用任何成员函数`operator+=`， `operator+`， `operator-=`， `operator-`，或`operator[]`，这可能仅能与使用随机访问迭代器。

迭代器的范围是 [*第一个*，*最后一个*)，其中左侧方括号指示包含*第一个*和右侧的括号指示包含的元素但不包括*最后一个*本身。 相同的元素包含在反向序列 [**修订** - *第一个*，**修订** - *最后一个*) 以便如果*最后一个*为一个过去的结束元素在序列中，则第一个元素**修订** - *第一个*中的反向的序列点\*(*最后一个*-1)。 将所有反向迭代器与其基础迭代器关联的标识是：

&\*( **reverse_iterator** (*我*)) = = （& a)\*(*我*-1)。

在实际操作中，这意味着在反向序列中，reverse_iterator 将引用迭代器在原有序列中引用的元素之外（右侧）一个位置的元素。 因此，如果迭代器在序列 (2, 4, 6, 8) 中发现元素 6，则 `reverse_iterator` 将在反向序列 (8, 6, 4, 2) 中发现元素 4。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[reverse_iterator](#reverse_iterator)|构造默认 `reverse_iterator` 或从基础迭代器构造 `reverse_iterator`。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[difference_type](#difference_type)|一种类型，此类型提供引用同一容器中的元素的两个 `reverse_iterator` 之间的差异。|
|[iterator_type](#iterator_type)|一种类型，此类型为 `reverse_iterator` 提供基础迭代器。|
|[pointer](#pointer)|一种类型，此类型提供指向 `reverse_iterator` 所发现元素的指针。|
|[reference](#reference)|一种类型，此类型提供对 `reverse_iterator` 所发现元素的引用。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[base](#base)|将基础迭代器从其 `reverse_iterator` 恢复。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator_star](#op_star)|返回 `reverse_iterator` 发现的元素。|
|[operator+](#op_add)|将偏移量添加到迭代器，并返回在新偏移位置处发现插入元素的新 `reverse_iterator`。|
|[operator++](#op_add_add)|将 `reverse_iterator` 递增到下一元素。|
|[operator+=](#op_add_eq)|从 `reverse_iterator` 添加指定偏移量。|
|[operator-](#operator-)|从 `reverse_iterator` 减去偏移量，并返回在偏移位置处发现元素的 `reverse_iterator`。|
|[operator--](#operator--)|将 `reverse_iterator` 递减到前一元素。|
|[operator-=](#operator-_eq)|从 `reverse_iterator` 减去指定偏移量。|
|[operator->](#operator-_gt)|返回指向 `reverse_iterator` 发现的元素的指针。|
|[operator[]](#op_at)|返回对于从 `reverse_iterator` 发现的元素偏移指定个位置的元素的引用。|

## <a name="requirements"></a>要求

**标头：** \<iterator>

**命名空间：** std

## <a name="base"></a>reverse_iterator::base

将基础迭代器从其 `reverse_iterator` 恢复。

```cpp
RandomIterator base() const;
```

### <a name="return-value"></a>返回值

构成 `reverse_iterator` 的基础的迭代器。

### <a name="remarks"></a>备注

将所有反向迭代器与其基础迭代器关联的标识是：

&\*( `reverse_iterator` ( *i* ) ) == &\*( *i* - 1 ).

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

## <a name="difference_type"></a>reverse_iterator::difference_type

一种类型，此类型提供引用同一容器中的元素的两个 `reverse_iterator` 之间的差异。

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type  difference_type;
```

### <a name="remarks"></a>备注

`reverse_iterator` 差异类型与迭代器差异类型相同。

该类型为迭代器特征类型名 `iterator_traits`\< **RandomIterator**> **::pointer** 的同义词。

### <a name="example"></a>示例

请参阅 [reverse_iterator::operator&#91;&#93;](#op_at)，获取关于如何声明和使用 `difference_type` 的示例。

## <a name="iterator_type"></a>  reverse_iterator::iterator_type

一种类型，此类型为 `reverse_iterator` 提供基础迭代器。

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 `Iterator` 的同义词。

### <a name="example"></a>示例

请参阅 [reverse_iterator::base](#base)，获取关于如何声明和使用 `iterator_type` 的示例。

## <a name="op_star"></a>  reverse_iterator::operator*

返回由 reverse_iterator 寻址的元素。

```cpp
reference operator*() const;
```

### <a name="return-value"></a>返回值

由 reverse_iterator 寻址的元素的值。

### <a name="remarks"></a>备注

该运算符将返回\*(**当前**-1)。

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

## <a name="op_add"></a>reverse_iterator::operator+

将偏移量添加到迭代器，并返回在新偏移位置处发现插入元素的新 `reverse_iterator`。

```cpp
reverse_iterator<RandomIterator> operator+(difference_type Off) const;
```

### <a name="parameters"></a>参数

`Off` 要添加到反向迭代器的偏移量。

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

## <a name="op_add_add"></a>reverse_iterator::operator++

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

## <a name="op_add_eq"></a>reverse_iterator::operator+=

从 reverse_iterator 添加指定偏移量。

```cpp
reverse_iterator<RandomIterator>& operator+=(difference_type Off);
```

### <a name="parameters"></a>参数

`Off` 若要将迭代器递增依据偏移量。

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

## <a name="reverse_iterator__operator-"></a>reverse_iterator::operator-

从 `reverse_iterator` 减去偏移量，并返回在偏移位置处发现元素的 `reverse_iterator`。

```cpp
reverse_iterator<RandomIterator> operator-(difference_type Off) const;
```

### <a name="parameters"></a>参数

`Off` 要从 reverse_iterator 减去的偏移量。

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

## <a name="reverse_iterator__operator--"></a>reverse_iterator::operator--

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

## <a name="reverse_iterator__operator-_eq"></a>  reverse_iterator::operator-=

从 `reverse_iterator` 减去指定偏移量。

```cpp
reverse_iterator<RandomIterator>& operator-=(difference_type Off);
```

### <a name="parameters"></a>参数

`Off` 要从减去的偏移量`reverse_iterator`。

### <a name="remarks"></a>备注

仅当 `reverse_iterator` 满足随机访问迭代器的要求时才能使用此成员函数。

运算符计算 **current** + _ *Off*。 然后返回 **\*this**。

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

## <a name="op_arrow"></a>reverse_iterator::operator&gt;

返回指向 `reverse_iterator` 发现的元素的指针。

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>返回值

指向由 `reverse_iterator` 寻址的元素的指针。

### <a name="remarks"></a>备注

运算符返回 **&\*\*this**。

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

## <a name="op_at"></a>  reverse_iterator::operator[]

返回对于从 `reverse_iterator` 发现的元素偏移指定个位置的元素的引用。

```cpp
reference operator[](difference_type Off) const;
```

### <a name="parameters"></a>参数

`Off` 从的偏移量`reverse_iterator`地址。

### <a name="return-value"></a>返回值

对元素偏移量的引用。

### <a name="remarks"></a>备注

运算符返回 **\***( **\*this** + `Off`)。

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

## <a name="pointer"></a>  reverse_iterator::pointer

一种类型，此类型提供指向 `reverse_iterator` 所发现元素的指针。

```cpp
typedef typename iterator_traits<RandomIterator>::pointer pointer;
```

### <a name="remarks"></a>备注

该类型为迭代器特征类型名 `iterator_traits`\< *RandomIterator*> **::pointer** 的同义词。

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

## <a name="reference"></a>  reverse_iterator::reference

一种类型，此类型提供对 reverse_iterator 所发现元素的引用。

```cpp
typedef typename iterator_traits<RandomIterator>::reference reference;
```

### <a name="remarks"></a>备注

该类型为迭代器特征类型名 `iterator_traits`\< *RandomIterator*> **::reference**.的同义词。

### <a name="example"></a>示例

请参阅 [reverse_iterator:: operator&#91;&#93;](#op_at) 或 [reverse_iterator:: operator *](#op_star)，获取有关如何声明和使用**引用**的示例。

## <a name="reverse_iterator"></a>  reverse_iterator::reverse_iterator

构造默认 `reverse_iterator` 或从基础迭代器构造 `reverse_iterator`。

```cpp
reverse_iterator();
explicit reverse_iterator(RandomIterator right);

template <class Type>
reverse_iterator(const reverse_iterator<Type>& right);
```

### <a name="parameters"></a>参数

`right` 是要进行适配化到的迭代器`reverse_iterator`。

### <a name="return-value"></a>返回值

默认的 `reverse_iterator` 或用于调整基础迭代器的 `reverse_iterator`。

### <a name="remarks"></a>备注

将所有反向迭代器与其基础迭代器关联的标识是：

&\*( `reverse_iterator` ( *i* ) ) == &\*( *i* - 1 ).

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

## <a name="see-also"></a>请参阅

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
