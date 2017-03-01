---
title: "allocator 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::allocator
- allocator
- memory/std::allocator
- std.allocator
dev_langs:
- C++
helpviewer_keywords:
- allocator class
ms.assetid: 3fd58076-56cc-43bb-ad58-b4b7c9c6b410
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 4c9e2c1acffd7286644ca61a4ef782e7b3a11eef
ms.lasthandoff: 02/24/2017

---
# <a name="allocator-class"></a>allocator 类
模板类描述一个对象，用于管理对象类型 **Type** 数组的存储分配和释放。 类 **allocator** 的对象是 C++ 标准库中的多个容器模板类的构造函数中所指定的默认分配器对象。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Type>  
class allocator  
```  
  
#### <a name="parameters"></a>参数  
 *类型*  
 为其分配或释放存储的对象的类型。  
  
## <a name="remarks"></a>备注  
 所有 C++ 标准库容器均有默认为 **allocator** 的模板参数。 通过使用自定义分配器构造容器可控制该容器的元素的分配和释放。  
  
 例如，分配器对象可能会在私有堆上或共享内存中分配存储，或者可能针对小型或大型对象大小进行优化。 它可能还会通过它提供的类型定义靠指定通过管理共享内存或执行自动垃圾回收的特殊访问器对象访问元素。 因此，使用分配器对象分配存储的类应使用这些类型来声明指针和引用对象，这与 C++ 标准库中的容器所执行的操作一样。  
  
 **（仅适用于 C_++98/03）** 从allocator 类提取时，必须提供一个 [rebind](#allocator__rebind) 构造函数（你新提取类的 `_Other` typedef 引用）。  
  
 因此，分配器定义以下类型：  
  
- [pointer](#allocator__pointer) 的行为方式与 **Type** 的指针相同。  
  
- [const_pointer](#allocator__const_pointer) 的行为方式与 **Type** 的常量指针相同。  
  
- [reference](#allocator__reference) 的行为方式与 **Type** 的引用相同。  
  
- [const_reference](#allocator__const_reference) 的行为方式与 **Type** 的常量引用相同。  
  
 这些 **Type** 指定了指针和引用必须为分配的元素所采用的形式。 （对于所有的分配器对象，[allocator::pointer](#allocator__pointer) 不必与 **Type**\* 相同，尽管它对类 **allocator** 具有此明显定义。）  
  
 **C++11 和更高版本：** 若要在你的分配器中启动移动操作，请使用最小的分配器界面并执行复制构造函数、 == and != operators、分配和释放。 有关详细信息和示例，请参阅 [Allocators](../standard-library/allocators.md)  
  
## <a name="members"></a>成员  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[allocator](#allocator__allocator)|用于创建 `allocator` 对象的构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[const_pointer](#allocator__const_pointer)|提供指向由分配器管理的对象类型的常量指针的类型。|  
|[const_reference](#allocator__const_reference)|提供对由分配器管理的对象类型的常量引用的类型。|  
|[difference_type](#allocator__difference_type)|有符号的整型，可以表示指向由分配器管理的对象类型的指针值之间的差异。|  
|[pointer](#allocator__pointer)|提供指向由分配器管理的对象类型的指针的类型。|  
|[reference](#allocator__reference)|提供指向对分配器管理的对象类型的引用的类型。|  
|[size_type](#allocator__size_type)|无符号整型，可以表示模板类 `allocator` 的对象可以分配的任何序列的长度。|  
|[value_type](#allocator__value_type)|由分配器管理的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[address](#allocator__address)|查找指定了其值的对象的地址。|  
|[allocate](#allocator__allocate)|分配大小足以存储至少某个指定数量的元素的内存块。|  
|[construct](#allocator__construct)|在使用指定值初始化的指定地址处构造特定类型的对象。|  
|[deallocate](#allocator__deallocate)|从指定位置开始从存储中释放指定数量的的对象。|  
|[destroy](#allocator__destroy)|调用对象析构函数而不释放存储对象的内存。|  
|[max_size](#allocator__max_size)|返回在可用内存用完之前，可以由类 `allocator` 的对象分配的类型 `Type` 的元素数。|  
|[rebind](#allocator__rebind)|使得一种类型的对象分配器可以为另一种类型的对象分配存储的结构。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator=](#allocator__operator_eq)|将一个 `allocator` 对象分配给另一个 `allocator` 对象。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<memory>  
  
 **命名空间：** std  
  
##  <a name="a-nameallocatoraddressa--allocatoraddress"></a><a name="allocator__address"></a>  allocator::address  
 查找指定了其值的对象的地址。  
  
```  
pointer address(reference val) const;
const_pointer address(const_reference val) const;
```  
  
### <a name="parameters"></a>参数  
 ` val`  
 要搜索其地址的对象的常量或非常量值。  
  
### <a name="return-value"></a>返回值  
 指向所找到的各自常量或非常量值的对象的常量或非常量指针。  
  
### <a name="remarks"></a>备注  
 成员函数返回 ` val` 的地址（以指针为分配的元素必须采用的形式）。  
  
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
  
##  <a name="a-nameallocatorallocatea--allocatorallocate"></a><a name="allocator__allocate"></a>  allocator::allocate  
 分配大小足以存储至少某个指定数量的元素的内存块。  
  
```  
pointer allocate(size_type count, const void* _Hint);
```  
  
### <a name="parameters"></a>参数  
 ` count`  
 要分配足够的存储空间的元素数量。  
  
 *_Hint*  
 通过定位在请求之前分配的对象的地址，常量指针可能帮助分配器对象满足存储请求。  
  
### <a name="return-value"></a>返回值  
 如果未分配内存，则指向分配的对象的指针或为 null。  
  
### <a name="remarks"></a>备注  
 成员函数通过调用运算符 new( ` count`) 来为计算元素的类型 **Type** 的数组分配存储。 它返回指向已分配对象的指针。 提示参数帮助某些分配器改进引用区域；有效的选择是由同一分配器对象较早分配且尚未被释放的对象的地址。 若不提供提示，请改用 null 指针参数。  
  
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
  
##  <a name="a-nameallocatorallocatora--allocatorallocator"></a><a name="allocator__allocator"></a>  allocator::allocator  
 用于创建分配器对象的构造函数。  
  
```  
allocator();
allocator(const allocator<Type>& right);
template <class Other>  
allocator(const allocator<Other>& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
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
  
##  <a name="a-nameallocatorconstpointera--allocatorconstpointer"></a><a name="allocator__const_pointer"></a>  allocator::const_pointer  
 提供指向由分配器管理的对象类型的常量指针的类型。  
  
```  
typedef const value_type *const_pointer;  
```  
  
### <a name="remarks"></a>备注  
 指针类型描述一个对象 **ptr**，能够通过表达式 **\*ptr** 指定模板类分配器对象可以分配的任何常量对象。  
  
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
  
##  <a name="a-nameallocatorconstreferencea--allocatorconstreference"></a><a name="allocator__const_reference"></a>  allocator::const_reference  
 提供对由分配器管理的对象类型的常量引用的类型。  
  
```  
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
  
##  <a name="a-nameallocatorconstructa--allocatorconstruct"></a><a name="allocator__construct"></a>  allocator::construct  
 在使用指定值初始化的指定地址处构造特定类型的对象。  
  
```  
void construct(pointer ptr, const Type& val);
void construct(pointer ptr, Type&& val);
template <class _Other>  
void construct(pointer ptr, _Other&&...   val);
```  
  
### <a name="parameters"></a>参数  
 ` ptr`  
 指向要构造对象的位置的指针。  
  
 ` val`  
 要进行初始化的要构造的对象的值。  
  
### <a name="remarks"></a>备注  
 第一个成员函数等于 **new** ( ( `void` \*) ` ptr` ) **Type** ( ` val` )。  
  
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
  
##  <a name="a-nameallocatordeallocatea--allocatordeallocate"></a><a name="allocator__deallocate"></a>  allocator::deallocate  
 从指定位置开始从存储中释放指定数量的的对象。  
  
```  
void deallocate(pointer ptr, size_type count);
```  
  
### <a name="parameters"></a>参数  
 ` ptr`  
 指向从存储释放的第一个对象的指针。  
  
 ` count`  
 要从存储中释放的对象数量。  
  
### <a name="remarks"></a>备注  
 成员函数通过调用 `operator delete`( ` ptr`) 来为 ` ptr` 中开始的计数对象类型 **Type** 的数组释放存储。 通过为与 **\*this** 相等的分配器对象调用 [allocate](#allocator__allocate)（分配具有同一大小和类型的数组对象），指针 ` ptr` 必须较早返回。 `deallocate` 绝不会引发异常。  
  
### <a name="example"></a>示例  
  有关使用 member 函数的示例，请参阅 [allocator::allocate](#allocator__allocate)  
  
##  <a name="a-nameallocatordestroya--allocatordestroy"></a><a name="allocator__destroy"></a>  allocator::destroy  
 调用对象析构函数而不释放存储对象的内存。  
  
```  
void destroy(pointer ptr);
```  
  
### <a name="parameters"></a>参数  
 ` ptr`  
 指定要销毁的对象的地址的指针。  
  
### <a name="remarks"></a>备注  
 member 函数通过调用析构函数 ` ptr` -> **Type**:: **~Type** 来销毁由 ` ptr` 指定的对象。  
  
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
  
##  <a name="a-nameallocatordifferencetypea--allocatordifferencetype"></a><a name="allocator__difference_type"></a>  allocator::difference_type  
 有符号的整型，可以表示指向由分配器管理的对象类型的指针值之间的差异。  
  
```  
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
  
##  <a name="a-nameallocatormaxsizea--allocatormaxsize"></a><a name="allocator__max_size"></a>  allocator::max_size  
 在可用内存用完之前，返回可以由类分配器的对象分配的类型 **Type** 的元素数。  
  
```  
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
  
##  <a name="a-nameallocatoroperatoreqa--allocatoroperator"></a><a name="allocator__operator_eq"></a>  allocator::operator=  
 将一个分配器对象分配到另一个分配器对象。  
  
```  
template <class Other>  
allocator<Type>& operator=(const allocator<Other>& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
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
  
##  <a name="a-nameallocatorpointera--allocatorpointer"></a><a name="allocator__pointer"></a>  allocator::pointer  
 提供指向由分配器管理的对象类型的指针的类型。  
  
```  
typedef value_type *pointer;  
```  
  
### <a name="remarks"></a>备注  
 指针类型描述一个对象 **ptr**，可以通过表达式 **\*ptr** 指定模板类分配器对象可以分配的任何对象。  
  
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
  
   cout << "The original vector v1 is:\n ( " ;  
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
  
##  <a name="a-nameallocatorrebinda--allocatorrebind"></a><a name="allocator__rebind"></a>  allocator::rebind  
 使得一种类型的对象分配器可以为另一种类型的对象分配存储的结构。  
```  
struct rebind {    typedef allocator<_Other> other ;    };  
```  
### <a name="parameters"></a>参数  
 *other*  
 所分配内存的元素的类型。  
  
### <a name="remarks"></a>备注  
 此结构可用于为与所实现的容器的元素类型不同的类型分配内存。  
  
 成员模板类定义其他类型。 其唯一目的是在给出类型名称 **allocator**\< **Type**> 时提供类型名称 **allocator**\<_ **Other**>  
  
 例如，给出分配器对象 **al** of type **A** 时，可以使用以下表达式分配对象类型 **_Other**：  
  
```  
A::rebind<Other>::other(al).allocate(1, (Other *)0)  
```  
  
 或者，可以通过编写类型来命名其指针类型：  
  
```  
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
  
##  <a name="a-nameallocatorreferencea--allocatorreference"></a><a name="allocator__reference"></a>  allocator::reference  
 提供指向对分配器管理的对象类型的引用的类型。  
  
```  
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
  
##  <a name="a-nameallocatorsizetypea--allocatorsizetype"></a><a name="allocator__size_type"></a>  allocator::size_type  
 无符号整型，可以表示模板类分配器的对象可以分配的任何序列的长度。  
  
```  
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
  
##  <a name="a-nameallocatorvaluetypea--allocatorvaluetype"></a><a name="allocator__value_type"></a>  allocator::value_type  
 由分配器管理的类型。  
  
```  
typedef Type value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **Type** 的同义词。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


