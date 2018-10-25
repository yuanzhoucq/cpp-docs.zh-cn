---
title: allocator 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::allocator
- memory/std::allocator::const_pointer
- memory/std::allocator::const_reference
- memory/std::allocator::difference_type
- memory/std::allocator::pointer
- memory/std::allocator::reference
- memory/std::allocator::size_type
- memory/std::allocator::value_type
- memory/std::allocator::address
- memory/std::allocator::allocate
- memory/std::allocator::construct
- memory/std::allocator::deallocate
- memory/std::allocator::destroy
- memory/std::allocator::max_size
- memory/std::allocator::rebind
dev_langs:
- C++
helpviewer_keywords:
- std::allocator [C++]
- std::allocator [C++], const_pointer
- std::allocator [C++], const_reference
- std::allocator [C++], difference_type
- std::allocator [C++], pointer
- std::allocator [C++], reference
- std::allocator [C++], size_type
- std::allocator [C++], value_type
- std::allocator [C++], address
- std::allocator [C++], allocate
- std::allocator [C++], construct
- std::allocator [C++], deallocate
- std::allocator [C++], destroy
- std::allocator [C++], max_size
- std::allocator [C++], rebind
ms.assetid: 3fd58076-56cc-43bb-ad58-b4b7c9c6b410
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6bd8c230f17e3b62d02d724cfd0744c0d335eac
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060541"
---
# <a name="allocator-class"></a>allocator 类

此模板类描述一个对象，用于管理存储分配和释放对象的类型数组的`Type`。 类的对象`allocator`是 c + + 标准库中的多个容器模板类的构造函数中指定的默认分配器对象。

## <a name="syntax"></a>语法

```cpp
template <class Type>
class allocator
```

### <a name="parameters"></a>参数

*Type*<br/>
为其分配或释放存储的对象的类型。

## <a name="remarks"></a>备注

所有 c + + 标准库容器都具有一个模板参数，默认为`allocator`。 通过使用自定义分配器构造容器可控制该容器的元素的分配和释放。

例如，分配器对象可能会在私有堆上或共享内存中分配存储，或者可能针对小型或大型对象大小进行优化。 它可能还会通过它提供的类型定义靠指定通过管理共享内存或执行自动垃圾回收的特殊访问器对象访问元素。 因此，使用分配器对象分配存储的类应使用这些类型来声明指针和引用对象，这与 C++ 标准库中的容器所执行的操作一样。

**（仅适用于 C_++98/03）** 从allocator 类提取时，必须提供一个 [rebind](#rebind) 构造函数（你新提取类的 `_Other` typedef 引用）。

因此，分配器定义以下类型：

- [指针](#pointer)的行为类似于一个指向`Type`。

- [const_pointer](#const_pointer)的行为类似于指向 const 指针`Type`。

- [引用](#reference)的行为类似于对引用`Type`。

- [const_reference](#const_reference)的行为方式类似的常量引用`Type`。

这些`Type`s 指定的窗体的指针和引用必须采取的分配的元素。 ( [allocator:: pointer](#pointer)不一定是相同`Type*`的所有分配器对象，即使它具有此明显定义为类`allocator`。)

**C++11 和更高版本：** 若要在你的分配器中启动移动操作，请使用最小的分配器界面并执行复制构造函数、 == and != operators、分配和释放。 有关详细信息和示例，请参阅 [Allocators](../standard-library/allocators.md)

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[allocator](#allocator)|用于创建 `allocator` 对象的构造函数。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[const_pointer](#const_pointer)|提供指向由分配器管理的对象类型的常量指针的类型。|
|[const_reference](#const_reference)|提供对由分配器管理的对象类型的常量引用的类型。|
|[difference_type](#difference_type)|有符号的整型，可以表示指向由分配器管理的对象类型的指针值之间的差异。|
|[pointer](#pointer)|提供指向由分配器管理的对象类型的指针的类型。|
|[reference](#reference)|提供指向对分配器管理的对象类型的引用的类型。|
|[size_type](#size_type)|无符号整型，可以表示模板类 `allocator` 的对象可以分配的任何序列的长度。|
|[value_type](#value_type)|由分配器管理的类型。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[address](#address)|查找指定了其值的对象的地址。|
|[allocate](#allocate)|分配大小足以存储至少某个指定数量的元素的内存块。|
|[construct](#construct)|在使用指定值初始化的指定地址处构造特定类型的对象。|
|[deallocate](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|
|[destroy](#destroy)|调用对象析构函数而不释放存储对象的内存。|
|[max_size](#max_size)|返回在可用内存用完之前，可以由类 `allocator` 的对象分配的类型 `Type` 的元素数。|
|[rebind](#rebind)|使得一种类型的对象分配器可以为另一种类型的对象分配存储的结构。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator=](#op_eq)|将一个 `allocator` 对象分配给另一个 `allocator` 对象。|

## <a name="requirements"></a>要求

**标头：**\<memory>

**命名空间：** std

## <a name="address"></a>  allocator::address

查找指定了其值的对象的地址。

```cpp
pointer address(reference val) const;
const_pointer address(const_reference val) const;
```

### <a name="parameters"></a>参数

*val*<br/>
要搜索其地址的对象的常量或非常量值。

### <a name="return-value"></a>返回值

指向所找到的各自常量或非常量值的对象的常量或非常量指针。

### <a name="remarks"></a>备注

成员函数返回的地址*val*中的窗体的指针必须采取的分配的元素。

### <a name="example"></a>示例

```cpp
// allocator_address.cpp
// compile with: /EHsc
#include <memory>
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 8;
   v1Ptr = v1Alloc.address( *find(v1.begin( ), v1.end( ), k) );
   // v1Ptr = v1Alloc.address( k );
   cout << "The integer addressed by v1Ptr has a value of: "
        << "*v1Ptr = " << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The integer addressed by v1Ptr has a value of: *v1Ptr = 8.
```

## <a name="allocate"></a>  allocator::allocate

分配大小足以存储至少某个指定数量的元素的内存块。

```cpp
pointer allocate(size_type count, const void* _Hint);
```

### <a name="parameters"></a>参数

*count*<br/>
要分配足够大的存储空间的元素数。

*_Hint*<br/>
通过定位在请求之前分配的对象的地址，常量指针可能帮助分配器对象满足存储请求。

### <a name="return-value"></a>返回值

如果未分配内存，则指向分配的对象的指针或为 null。

### <a name="remarks"></a>备注

成员函数的类型的计数元素数组分配存储`Type`，通过调用运算符 new (*计数*)。 它返回指向已分配对象的指针。 提示参数帮助某些分配器改进引用区域；有效的选择是由同一分配器对象较早分配且尚未被释放的对象的地址。 若不提供提示，请改用 null 指针参数。

### <a name="example"></a>示例

```cpp
// allocator_allocate.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<int> v1Alloc;
   allocator<int>::pointer v1aPtr;
   v1aPtr = v1Alloc.allocate ( 10 );

   int i;
   for ( i = 0 ; i < 10 ; i++ )
   {
      v1aPtr[ i ] = i;
   }

   for ( i = 0 ; i < 10 ; i++ )
   {
      cout << v1aPtr[ i ] << " ";
   }
   cout << endl;
   v1Alloc.deallocate( v1aPtr, 10 );
}
```

```Output
0 1 2 3 4 5 6 7 8 9
```

## <a name="allocator"></a>  allocator::allocator

用于创建分配器对象的构造函数。

```cpp
allocator();
allocator(const allocator<Type>& right);
template <class Other>
allocator(const allocator<Other>& right);
```

### <a name="parameters"></a>参数

*right*<br/>
要复制的分配器对象。

### <a name="remarks"></a>备注

构造函数不执行任何操作。 但是，一般情况下，从另一个分配器对象构造的分配器对象与之比较应相等，并允许在两个分配器对象间混合对象分配和释放。

### <a name="example"></a>示例

```cpp
// allocator_allocator.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int {
public:
   Int( int i )
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( )
{
   allocator<double> Alloc;
   vector <Int>:: allocator_type v1Alloc;

   allocator<double> cAlloc(Alloc);
   allocator<Int> cv1Alloc(v1Alloc);

   if ( cv1Alloc == v1Alloc )
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."
           << endl;

   if ( cAlloc == Alloc )
      cout << "The allocator objects cAlloc & Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cAlloc & Alloc are not equal."
           << endl;
}
```

```Output
The allocator objects cv1Alloc & v1Alloc are equal.
The allocator objects cAlloc & Alloc are equal.
```

## <a name="const_pointer"></a>  allocator::const_pointer

提供指向由分配器管理的对象类型的常量指针的类型。

```cpp
typedef const value_type *const_pointer;
```

### <a name="remarks"></a>备注

指针类型描述一个对象`ptr`，可以指定，通过表达式`*ptr`，模板类分配器对象可以分配的任何常量对象。

### <a name="example"></a>示例

```cpp
// allocator_const_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( i * 2 );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 10;
   v1Ptr = v1Alloc.address( k );

   cout << "The integer's address found has a value of: "
        << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The integer's address found has a value of: 10.
```

## <a name="const_reference"></a>  allocator::const_reference

提供对由分配器管理的对象类型的常量引用的类型。

```cpp
typedef const value_type& const_reference;
```

### <a name="remarks"></a>备注

引用类型描述一个对象，可以指定模板类分配器对象可以分配的任何常量对象。

### <a name="example"></a>示例

```cpp
// allocator_const_ref.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::const_reference vcref =*vfIter;
   cout << "The value of the element referred to by vref is: "
        << vcref << ",\n the first element in the vector." << endl;

   // const references can have their elements modified,
   // so the following would generate an error:
   // vcref = 150;
   // but the value of the first element could be modified through
   // its nonconst iterator and the const reference would remain valid
*vfIter = 175;
   cout << "The value of the element referred to by vcref,"
        <<"\n after nofication through its nonconst iterator, is: "
        << vcref << "." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element referred to by vref is: 100,
the first element in the vector.
The value of the element referred to by vcref,
after nofication through its nonconst iterator, is: 175.
```

## <a name="construct"></a>  allocator::construct

在使用指定值初始化的指定地址处构造特定类型的对象。

```cpp
void construct(pointer ptr, const Type& val);
void construct(pointer ptr, Type&& val);
template <class _Other>
void construct(pointer ptr, _Other&&...   val);
```

### <a name="parameters"></a>参数

*ptr*<br/>
指向要构造对象的位置的指针。

*val*<br/>
要进行初始化的要构造的对象的值。

### <a name="remarks"></a>备注

第一个成员函数等于 **new** ( ( `void` \*) `ptr` ) **Type** ( `val` )。

### <a name="example"></a>示例

```cpp
// allocator_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 3 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::pointer v1PtrA;
   int kA = 6, kB = 7;
   v1PtrA = v1Alloc.address( *find( v1.begin( ), v1.end( ), kA ) );
   v1Alloc.destroy ( v1PtrA );
   v1Alloc.construct ( v1PtrA , kB );

   cout << "The modified vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 3 6 9 12 15 18 21 ).
The modified vector v1 is:
( 3 7 9 12 15 18 21 ).
```

## <a name="deallocate"></a>  allocator::deallocate

从指定位置开始从存储中释放指定数量的的对象。

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>参数

*ptr*<br/>
指向要从存储中释放的第一个对象的指针。

*count*<br/>
要从存储中释放的对象数量。

### <a name="remarks"></a>备注

成员函数释放存储类型的计数对象的数组`Type`开始*ptr*，通过调用`operator delete(ptr)`。 指针*ptr*必须较早返回通过调用[分配](#allocate)相等的分配器对象**\*这**，分配一个数组相同的大小和类型的对象。 `deallocate` 绝不会引发异常。

### <a name="example"></a>示例

有关使用 member 函数的示例，请参阅 [allocator::allocate](#allocate)

## <a name="destroy"></a>  allocator::destroy

调用对象析构函数而不释放存储对象的内存。

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>参数

*ptr*<br/>
指定要销毁的对象的地址的指针。

### <a name="remarks"></a>备注

成员函数会销毁指定的对象*ptr*，通过调用析构函数`ptr->`**类型**::**~ 类型**。

### <a name="example"></a>示例

```cpp
// allocator_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::pointer v1PtrA;
   int kA = 12, kB = -99;
   v1PtrA = v1Alloc.address( *find(v1.begin( ), v1.end( ), kA) );
   v1Alloc.destroy ( v1PtrA );
   v1Alloc.construct ( v1PtrA , kB );

   cout << "The modified vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The modified vector v1 is:
( 2 4 6 8 10 -99 14 ).
```

## <a name="difference_type"></a>  allocator::difference_type

有符号的整型，可以表示指向由分配器管理的对象类型的指针值之间的差异。

```cpp
typedef ptrdiff_t difference_type;
```

### <a name="remarks"></a>备注

带符号的整数类型描述一个可表示模板类分配器对象可以分配的序列中任意两个元素的地址之间的差异的对象。

### <a name="example"></a>示例

```cpp
// allocator_diff_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 0 ; i <= 7 ; i++ )
   {
      v1.push_back( i * 2 );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1PtrA, v1PtrB;
   const int kA = 4, kB =12;
   v1PtrA = v1Alloc.address( kA );
   v1PtrB = v1Alloc.address( kB );
   allocator<int>::difference_type v1diff = *v1PtrB - *v1PtrA;

   cout << "Pointer v1PtrA addresses " << *v1PtrA << "." << endl;
   cout << "Pointer v1PtrB addresses " << *v1PtrB <<  "." << endl;
   cout << "The difference between the integer's addresses is: "
        << v1diff << "." << endl;
}
```

```Output
The original vector v1 is:
( 0 2 4 6 8 10 12 14 ).
Pointer v1PtrA addresses 4.
Pointer v1PtrB addresses 12.
The difference between the integer's addresses is: 8.
```

## <a name="max_size"></a>  allocator::max_size

在可用内存用完之前，返回可以由类分配器的对象分配的类型 `Type` 的元素数。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>返回值

可分配的元素数量。

### <a name="example"></a>示例

```cpp
// allocator_max_size.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   vector <double> v2;
   vector <double> ::iterator v2Iter;
   vector <double> :: allocator_type v2Alloc;
   allocator<int>::size_type v1size;
   v1size = v1Alloc.max_size( );

   cout << "The number of integers that can be allocated before\n"
        << " the free memory in the vector v1 is used up is: "
        << v1size << "." << endl;

   int ii;
   for ( ii = 1 ; ii <= 7 ; ii++ )
   {
      v2.push_back( ii * 10.0 );
   }

   cout << "The original vector v2 is:\n ( " ;
   for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ; v2Iter++ )
      cout << *v2Iter << " ";
   cout << ")." << endl;
   allocator<double>::size_type v2size;
   v2size = v2Alloc.max_size( );

   cout << "The number of doubles that can be allocated before\n"
        << " the free memory in the vector v2 is used up is: "
        << v2size << "." << endl;
}
```

## <a name="op_eq"></a>  allocator::operator=

将一个分配器对象分配到另一个分配器对象。

```cpp
template <class Other>
allocator<Type>& operator=(const allocator<Other>& right);
```

### <a name="parameters"></a>参数

*right*<br/>
要分配到另一个对象的分配器对象。

### <a name="return-value"></a>返回值

分配器对象的引用

### <a name="remarks"></a>备注

模板赋值运算符没有任何影响。 但是，一般情况下，分配到另一个分配器对象的分配器对象与之比较应相等，并允许在两个分配器对象间混合对象分配和释放。

### <a name="example"></a>示例

```cpp
// allocator_op_assign.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int {
public:
   Int(int i)
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( ) {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( )
{
   allocator<Int> Alloc;
   allocator<Int> cAlloc ;
   cAlloc = Alloc;
}
```

## <a name="pointer"></a>  allocator::pointer

提供指向由分配器管理的对象类型的指针的类型。

```cpp
typedef value_type *pointer;
```

### <a name="remarks"></a>备注

指针类型描述一个对象`ptr`，可以指定，通过表达式 **\*ptr**，模板类分配器对象可以分配任何对象。

### <a name="example"></a>示例

```cpp
// allocator_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 3 * i );
   }

   cout << "The original vector v1 is:\n( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 12;
   v1Ptr = v1Alloc.address( k );

   cout << "The integer addressed by v1Ptr has a value of: "
        << "*v1Ptr = " << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 3 6 9 12 15 18 21 ).
The integer addressed by v1Ptr has a value of: *v1Ptr = 12.
```

## <a name="rebind"></a>  allocator::rebind

使得一种类型的对象分配器可以为另一种类型的对象分配存储的结构。
```cpp
struct rebind {    typedef allocator<_Other> other ;    };
```

### <a name="parameters"></a>参数

*other*<br/>
所分配内存的元素的类型。

### <a name="remarks"></a>备注

此结构可用于为与所实现的容器的元素类型不同的类型分配内存。

成员模板类定义其他类型。 其唯一目的是在给出类型名称 **allocator**\< **Type**> 时提供类型名称 **allocator**\<_ **Other**>

例如，给定一个分配器对象`al`类型的`A`，你可以分配类型的对象`_Other`使用表达式：

```cpp
A::rebind<Other>::other(al).allocate(1, (Other *)0)
```

或者，可以通过编写类型来命名其指针类型：

```cpp
A::rebind<Other>::other::pointer
```

### <a name="example"></a>示例

```cpp
// allocator_rebind.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

typedef vector<int>::allocator_type IntAlloc;
int main( )
{
   IntAlloc v1Iter;
   vector<int> v1;

   IntAlloc::rebind<char>::other::pointer pszC =
      IntAlloc::rebind<char>::other(v1.get_allocator()).allocate(1, (void *)0);

   int * pInt = v1Iter.allocate(10);
}
```

## <a name="reference"></a>  allocator::reference

提供指向对分配器管理的对象类型的引用的类型。

```cpp
typedef value_type& reference;
```

### <a name="remarks"></a>备注

引用类型描述一个对象，可以指定模板类分配器的对象可以分配的任何对象。

### <a name="example"></a>示例

```cpp
// allocator_reference.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::reference vref =*vfIter;
   cout << "The value of the element referred to by vref is: "
        << vref << ",\n the first element in the vector." << endl;

   // nonconst references can have their elements modified
   vref = 150;
   cout << "The element referred to by vref after being modified is: "
        << vref << "." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element referred to by vref is: 100,
the first element in the vector.
The element referred to by vref after being modified is: 150.
```

## <a name="size_type"></a>  allocator::size_type

无符号整型，可以表示模板类分配器的对象可以分配的任何序列的长度。

```cpp
typedef size_t size_type;
```

### <a name="example"></a>示例

```cpp
// allocator_size_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   allocator<double>::size_type vsize;
   vsize = vAlloc.max_size( );

   cout << "The number of doubles that can be allocated before\n"
        << " the free memory in the vector v is used up is: "
        << vsize << "." << endl;
}
```

## <a name="value_type"></a>  allocator::value_type

由分配器管理的类型。

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 `Type` 的同义词。

### <a name="example"></a>示例

```cpp
// allocator_value_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::value_type vecVal = 150.0;
*vfIter = vecVal;
   cout << "The value of the element addressed by vfIter is: "
        << *vfIter << ",\n the first element in the vector." << endl;

   cout << "The modified vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element addressed by vfIter is: 150,
the first element in the vector.
The modified vector v is:
( 150 200 300 400 500 600 700 ).
```

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
