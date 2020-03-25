---
title: raw_storage_iterator 类
ms.date: 11/04/2016
f1_keywords:
- memory/std::raw_storage_iterator
- memory/std::raw_storage_iterator::element_type
- memory/std::raw_storage_iterator::iter_type
helpviewer_keywords:
- std::raw_storage_iterator [C++]
- std::raw_storage_iterator [C++], element_type
- std::raw_storage_iterator [C++], iter_type
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
ms.openlocfilehash: 9372fa884d75e10c1a0f2ec92d6cca9caa65808e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167610"
---
# <a name="raw_storage_iterator-class"></a>raw_storage_iterator 类

一种所提供的适配器类，使算法能够将它们的结果存储到未初始化的内存中。

## <a name="syntax"></a>语法

```cpp
template <class OutputIterator, class Type>
    class raw_storage_iterator
```

### <a name="parameters"></a>parameters

*OutputIterator*\
为正被存储的对象指定输出迭代器。

*类型*\
正为其分配存储的对象的类型。

## <a name="remarks"></a>备注

此类描述一个输出迭代器，该迭代器按其生成的序列构造 `Type` 类型的对象。 类 `raw_storage_iterator`类的对象 \< **ForwardIterator**，**类型**> 通过在构造对象时指定的 `ForwardIterator`类的向前迭代器对象来访问存储。 对于类 `ForwardIterator`的第一个对象， **&\*** 的表达式首先必须为生成的序列中的下一个对象（类型 `Type`）指定未构造存储。

在需要分隔内存分配和对象构造时使用此适配器类。 `raw_storage_iterator` 可用于将对象复制到未初始化的存储中，如使用 `malloc` 函数分配的内存。

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|使用指定的基础输出迭代器构造原始存储迭代器。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[element_type](#element_type)|提供一种类型，该类型描述要存储在原始存储迭代器中的元素。|
|[iter_type](#iter_type)|提供了一种类型，该类型描述原始存储迭代器所基于的迭代器。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator*](#op_star)|用于实现输出迭代器表达式的取消引用运算符，\* `ii` = `x`。|
|[operator=](#op_eq)|用于实现原始存储迭代器表达式的赋值运算符，\* `i` = `x` 存储在内存中。|
|[operator++](#op_add_add)|原始存储迭代器的前置递增和后置递增运算符。|

### <a name="element_type"></a><a name="element_type"></a>element_type

提供一种类型，该类型描述要存储在原始存储迭代器中的元素。

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>备注

类型是 raw_storage_iterator 类模板参数 `Type`的同义词。

### <a name="iter_type"></a><a name="iter_type"></a>iter_type

提供了一种类型，该类型描述原始存储迭代器所基于的迭代器。

```cpp
typedef ForwardIterator iter_type;
```

#### <a name="remarks"></a>备注

该类型是模板参数 `ForwardIterator`的同义词。

### <a name="operator"></a><a name="op_star"></a> 运算符\*

用于实现原始存储迭代器表达式的取消引用*运算符 = * *x*\*。

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

#### <a name="return-value"></a>返回值

对原始存储迭代器的引用

#### <a name="remarks"></a>备注

`ForwardIterator` 的要求是原始存储迭代器必须满足仅要求表达式 \* *ii* = *t*有效，并且它不会对**运算符**或 `operator=` 显示任何内容。 此实现中的成员运算符将返回 **\*this**，使[operator =](#op_eq)（**constType**&）可以在表达式中执行实际存储，如 \* *ptr* = `val`。

#### <a name="example"></a>示例

```cpp
// raw_storage_iterator_op_deref.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };

   Int &operator=(int i)
   {
      if (!bIsConstructed)
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl;
      x = i;
      return *this;
   };

   int x;

private:
   bool bIsConstructed;
};

int main( void)
{
   Int *pInt = ( Int* ) malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;
*pInt = 5;
   raw_storage_iterator< Int*, Int > it( pInt );
*it = 5;
}
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="operator"></a><a name="op_eq"></a>operator =

用于实现原始存储迭代器表达式的赋值运算符，\**我* = *x*存储在内存中。

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

#### <a name="parameters"></a>parameters

*val*\
要插入到内存中 `Type` 类型的对象的值。

#### <a name="return-value"></a>返回值

运算符会将 `val` 插入到内存，然后向原始存储迭代器返回引用。

#### <a name="remarks"></a>备注

原始存储迭代器必须满足 `ForwardIterator` 状态要求仅要求表达式 \* *ii* = *t*有效，并且它不会对**运算符**或 `operator=` 显示任何内容。 这些成员运算符返回 **\*this**。

赋值运算符首先使用存储的迭代器值来构造输出序列中的下一个对象，方法是计算 new 表达式**new** （（`void` \*） &\***第一个**）**类型**（`val`）。

#### <a name="example"></a>示例

```cpp
// raw_storage_iterator_op_assign.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int( int i )
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if ( !bIsConstructed )
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl; x = i;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( void )
{
   Int *pInt = ( Int* )malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;

*pInt = 5;

   raw_storage_iterator<Int*, Int> it( pInt );
*it = 5;
}
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="operator"></a><a name="op_add_add"></a>operator + +

原始存储迭代器的前置递增和后置递增运算符。

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

#### <a name="return-value"></a>返回值

原始存储迭代器或对原始存储迭代器的引用。

#### <a name="remarks"></a>备注

第一个运算符最终尝试从关联的输入流提取和存储类型 `CharType` 的对象。 第二个运算符生成对象的副本，递增对象，然后返回副本。

第一个前置递增运算符递增存储的输出迭代器对象，然后返回 **\*this**。

第二个后置递增运算符生成 **\*this** 的副本，递增存储的输出迭代器对象，然后返回副本。

构造函数将 `first` 存储为输出迭代器对象。

#### <a name="example"></a>示例

```cpp
// raw_storage_iterator_op_incr.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

int main( void )
{
   int *pInt = new int[5];
   std::raw_storage_iterator<int*,int> it( pInt );
   for ( int i = 0; i < 5; i++, it++ ) {
      *it = 2 * i;
   };

   for ( int i = 0; i < 5; i++ ) cout << "array " << i << " = " << pInt[i] << endl;;

   delete[] pInt;
}
```

```Output
array 0 = 0
array 1 = 2
array 2 = 4
array 3 = 6
array 4 = 8
```

### <a name="raw_storage_iterator"></a><a name="raw_storage_iterator"></a>raw_storage_iterator

使用指定的基础输出迭代器构造原始存储迭代器。

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

#### <a name="parameters"></a>parameters

*第一个*\
前向迭代器，是正在构造的 `raw_storage_iterator` 对象的基础。

#### <a name="example"></a>示例

```cpp
// raw_storage_iterator_ctor.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if (!bIsConstructed)
         cout << "Error! I'm not constructed!\n";
      cout << "Copying " << i << endl;  x = i; return *this;
   };
   int x;
   bool bIsConstructed;
};

int main( void )
{
   std::list<int> l;
   l.push_back( 1 );
   l.push_back( 2 );
   l.push_back( 3 );
   l.push_back( 4 );

   Int *pInt = (Int*)malloc(sizeof(Int)*l.size( ));
   memset (pInt, 0, sizeof(Int)*l.size( ));
   // Hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ), pInt );  // C4996
   for (unsigned int i = 0; i < l.size( ); i++)
      cout << "array " << i << " = " << pInt[i].x << endl;;

   memset (pInt, 0, sizeof(Int)*l.size( ));
   // hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ),
      std::raw_storage_iterator<Int*,Int>(pInt));  // C4996
   for (unsigned int i = 0; i < l.size( ); i++ )
      cout << "array " << i << " = " << pInt[i].x << endl;

   free(pInt);
}
```

```Output
Error! I'm not constructed!
Copying 1
Error! I'm not constructed!
Copying 2
Error! I'm not constructed!
Copying 3
Error! I'm not constructed!
Copying 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
Constructing 1
Constructing 2
Constructing 3
Constructing 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
```
