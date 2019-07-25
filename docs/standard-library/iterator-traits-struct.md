---
title: iterator_traits 结构
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator_traits
helpviewer_keywords:
- iterator_traits struct
- iterator_traits class
ms.assetid: 8b92c2c5-f658-402f-8ca1-e7ae301b8514
ms.openlocfilehash: 9d2f9d79d200579f539f7d9edc49d4a907e6cdb2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455581"
---
# <a name="iteratortraits-struct"></a>iterator_traits 结构

用于指定迭代器应具有的所有关键类型定义的模板帮助器结构。

## <a name="syntax"></a>语法

```cpp
struct iterator_traits {
   typedef typename Iterator::iterator_category iterator_category;
   typedef typename Iterator::value_type value_type;
   typedef typename Iterator::difference_type difference_type;
   typedef difference_type distance_type;
   typedef typename Iterator::pointer pointer;
   typedef typename Iterator::reference reference;
   };
```

## <a name="remarks"></a>备注

此模板结构定义成员类型

- `iterator_category`: 的同义词`Iterator::iterator_category`。

- `value_type`: 的同义词`Iterator::value_type`。

- `difference_type`: 的同义词`Iterator::difference_type`。

- `distance_type`: 一个同义词, 用于`Iterator::difference_type.`

- `pointer`: 的同义词`Iterator::pointer`。

- `reference`: 的同义词`Iterator::reference`。

部分专用化确定与类型为**类型** <strong>\*</strong>或**const 类型** <strong>\*</strong>的对象指针关联的关键类型。

在此实现中，还可使用几个不会使用部分专用化的模板函数：

```cpp
template <class Category, class Type, class Diff>
C _Iter_cat(const iterator<Category, Ty, Diff>&);

template <class Ty>
random_access_iterator_tag _Iter_cat(const Ty *);

template <class Category, class Ty, class Diff>
Ty *val_type(const iterator<Category, Ty, Diff>&);

template <class Ty>
Ty *val_type(const Ty *);

template <class Category, class Ty, class Diff>
Diff *_Dist_type(const iterator<Category, Ty, Diff>&);

template <class Ty>
ptrdiff_t *_Dist_type(const Ty *);
```

它更加间接地决定其中几个相同类型。 函数调用时将这些函数用作参数。 其唯一目的是向被调用函数提供有用的模板类参数。

## <a name="example"></a>示例

```cpp
// iterator_traits.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <vector>
#include <list>

using namespace std;

template< class it >
void
function( it i1, it i2 )
{
   iterator_traits<it>::iterator_category cat;
   cout << typeid( cat ).name( ) << endl;
   while ( i1 != i2 )
   {
      iterator_traits<it>::value_type x;
      x = *i1;
      cout << x << " ";
      i1++;
   };
   cout << endl;
};

int main( )
{
   vector<char> vc( 10,'a' );
   list<int> li( 10 );
   function( vc.begin( ), vc.end( ) );
   function( li.begin( ), li.end( ) );
}
/* Output:
struct std::random_access_iterator_tag
a a a a a a a a a a
struct std::bidirectional_iterator_tag
0 0 0 0 0 0 0 0 0 0
*/
```

## <a name="requirements"></a>要求

**标头：** \<iterator>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<iterator>](../standard-library/iterator.md)\
[C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
