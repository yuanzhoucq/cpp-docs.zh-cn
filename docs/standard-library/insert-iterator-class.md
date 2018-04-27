---
title: insert_iterator 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iterator/std::insert_iterator
- iterator/std::insert_iterator::container_type
- iterator/std::insert_iterator::reference
dev_langs:
- C++
helpviewer_keywords:
- std::insert_iterator [C++]
- std::insert_iterator [C++], container_type
- std::insert_iterator [C++], reference
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ddd843b281cc9c4bd1259669d3f6e300058a1a87
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="insertiterator-class"></a>insert_iterator 类

描述满足输出迭代器需求的迭代器适配器。 它是将元素插入到序列而不是覆盖，因此不同于 C++ 序列和关联容器的迭代器所提供的覆盖语义，它可以提供不同的语义。 `insert_iterator` 类会针对要适配的容器类型进行模板化。

## <a name="syntax"></a>语法

```cpp
template <class Container>
class insert_iterator;
```

### <a name="parameters"></a>参数

`Container` 元素是由插入到其中的容器的类型`insert_iterator`。

## <a name="remarks"></a>备注

**Container** 类型的容器必须满足可变大小容器的需求，并具有一个两个自变量插入成员函数，其中，形式参数分别为 **Container::iterator** 类型和 **Container::value_type** 类型，将返回 **Container::iterator** 类型。 C++ 标准库序列和排序关联容器符合这些需求，可以进行适配以便用于 `insert_iterator`。 对于关联容器，位置自变量将被当做提示来处理，有可能会提高或降低性能，具体取决于该提示的好坏。 `insert_iterator` 必须使用其容器进行初始化。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[insert_iterator](#insert_iterator)|构造一个 `insert_iterator`，以便将元素插入到容器中的指定位置。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[container_type](#container_type)|一种类型，代表要对其执行泛型插入的容器。|
|[reference](#reference)|一种类型，此类型提供对关联容器所控制序列中的元素的引用。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator*](#op_star)|取消引用运算符，用于实现泛型插入的输出迭代器表达式 * `i` = `x`。|
|[operator++](#op_add_add)|将 `insert_iterator` 递增到下一个可用来存储值的位置。|
|[operator=](#op_eq)|赋值运算符，用于实现泛型插入的输出迭代器表达式 * `i` = `x`。|

## <a name="requirements"></a>要求

**标头**：\<iterator>

**命名空间：** std

## <a name="container_type"></a>insert_iterator::container_type

一种类型，代表要对其执行泛型插入的容器。

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **Container** 的同义词。

### <a name="example"></a>示例

```cpp
// insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   insert_iterator<list<int> >::container_type L2 = L1;
   inserter ( L2, L2.end ( ) ) = 20;
   inserter ( L2, L2.end ( ) ) = 10;
   inserter ( L2, L2.begin ( ) ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
\* Output:
The list L2 is: ( 40 20 10 ).
*\
```

## <a name="insert_iterator"></a>insert_iterator::insert_iterator

构造一个 `insert_iterator`，以便将元素插入到容器中的指定位置。

```cpp
insert_iterator(Container& _Cont, typename Container::iterator _It);
```

### <a name="parameters"></a>参数

`_Cont` 在其中容器`insert_iterator`是插入元素。

`_It` 插入位置。

### <a name="remarks"></a>备注

所有容器都具有由 `insert_iterator` 调用 insert 成员函数。 对于关联容器，位置参数仅是一项建议。 inserter 函数提供了方便插入值的方式。

### <a name="example"></a>示例

```cpp
// insert_iterator_insert_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = 1 ; i < 4 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   inserter ( L, L.begin ( ) ) = 2;

   // Alternatively, you may use the template version
   insert_iterator< list < int> > Iter(L, L.end ( ) );
 *Iter = 300;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
\* Output:
The list L is:
 ( 10 20 30 ).
After the insertions, the list L is:
 ( 2 10 20 30 300 ).
*\
```

## <a name="op_star"></a>insert_iterator::operator*

取消引用插入迭代器，其返回元素为地址。

```cpp
insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>返回值

此成员函数返回已寻址元素的值。

### <a name="remarks"></a>备注

用于实现输出迭代器表达式 **\*Iter** = **value**。 如果 **Iter** 是对序列中元素进行寻址的迭代器，则 **\*Iter** = **value** 会替换该元素的值，且不会改变此序列中元素的总数。

### <a name="example"></a>示例

```cpp
// insert_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
 *Iter = 10;
 *Iter = 20;
 *Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
\* Output:
The original list L is:
 ( 0 2 4 6 ).
After the insertions, the list L is:
 ( 10 20 30 0 2 4 6 ).
*\
```

## <a name="op_add_add"></a>insert_iterator::operator++

将 **insert_iterator** 递增到下一个可用来存储值的位置。

```cpp
insert_iterator<Container>& operator++();

insert_iterator<Container> operator++(int);
```

### <a name="parameters"></a>参数

`insert_iterator`，它寻找下一个可用来存储值的位置。

### <a name="remarks"></a>备注

前递增和后递增运算符将返回相同的结果。

### <a name="example"></a>示例

```cpp
// insert_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 5 ; ++i )
   {
      vec.push_back (  i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   insert_iterator<vector<int> > ii ( vec, vec.begin ( ) );
 *ii = 30;
   ii++;
 *ii = 40;
   ii++;
 *ii = 50;

   cout << "After the insertions, the vector vec becomes:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
\* Output:
The vector vec is:
 ( 1 2 3 4 ).
After the insertions, the vector vec becomes:
 ( 30 40 50 1 2 3 4 ).
*\
```

## <a name="op_eq"></a>insert_iterator::operator=

将值插入容器并返回更新的迭代器，以指向新元素。

```cpp
insert_iterator<Container>& operator=(
    typename Container::const_reference val,);

insert_iterator<Container>& operator=(
    typename Container::value_type&& val);
```

### <a name="parameters"></a>参数

`val` 要分配给容器的值。

### <a name="return-value"></a>返回值

对插入到容器中的元素的引用。

### <a name="remarks"></a>备注

第一个成员运算符会求值

`Iter = container->insert(Iter, val)`;

`++Iter;`

然后返回 `*this`。

第二个成员运算符会求值

`Iter = container->insert(Iter, std::move(val));`

`++Iter;`

然后返回 `*this`。

### <a name="example"></a>示例

```cpp
// insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
 *Iter = 10;
 *Iter = 20;
 *Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
\* Output:
The original list L is:
 ( 0 2 4 6 ).
After the insertions, the list L is:
 ( 10 20 30 0 2 4 6 ).
*\
```

## <a name="reference"></a>insert_iterator::reference

一种类型，此类型提供对关联容器所控制序列中的元素的引用。

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>备注

此类型描述对关联容器控制的序列元素的引用。

### <a name="example"></a>示例

```cpp
// insert_iterator_container_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   insert_iterator<list<int> > iivIter( L , L.begin ( ) );
 *iivIter = 10;
 *iivIter = 20;
 *iivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++ )
      cout << *LIter << " ";
   cout << ")." << endl;

   insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
\* Output:
The list L is: ( 10 20 30 ).
The first element in the list L is: 10.
*\
```

## <a name="see-also"></a>请参阅

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
