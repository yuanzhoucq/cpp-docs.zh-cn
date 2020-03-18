---
title: '&lt;new&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: c912e5be07ea0ebdd3148d30c80c39a5f8cfa1a5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425411"
---
# <a name="ltnewgt-functions"></a>&lt;new&gt; 函数

## <a name="get_new_handler"></a>get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>备注

返回当前 `new_handler`。

## <a name="launder"></a>launder

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>parameters

*ptr*\
内存中的字节地址，其中包含类型类似于*T*的对象。

### <a name="return-value"></a>返回值

指向 X\*类型*T*的值。

### <a name="remarks"></a>备注

也称为指针优化障碍。

在常量表达式中使用的参数值时用作常量表达式。 如果存储在另一个对象占用的存储中，则可通过指向该对象的指针值访问该字节的存储，该指针指向一个具有类似指针的对象。

### <a name="example"></a>示例

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a>nothrow

提供一个对象，该对象用作**new**和**delete**的**nothrow**版本的参数。

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>备注

该对象用作与参数类型 [std::nothrow_t](../standard-library/nothrow-t-structure.md) 匹配的函数自变量。

### <a name="example"></a>示例

有关如何将 [ 用作函数参数的示例，请参阅](../standard-library/new-operators.md#op_new)运算符 new[ 和](../standard-library/new-operators.md#op_new_arr)运算符 new&#91;&#93;`std::nothrow_t`。

## <a name="set_new_handler"></a>set_new_handler

安装一个用户函数，当**运算符 new**尝试分配内存失败时将调用该函数。

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>parameters

*Pnew*\
要安装的 `new_handler`。

### <a name="return-value"></a>返回值

第一次调用时为 0，后续调用时为上一个 `new_handler`。

### <a name="remarks"></a>备注

函数将*Pnew*存储在它所维护的静态[新处理程序](../standard-library/new-typedefs.md#new_handler)指针中，然后返回以前存储在指针中的值。 New 处理程序由[运算符 new](../standard-library/new-operators.md#op_new)（**size_t**）使用。

### <a name="example"></a>示例

```cpp
// new_set_new_handler.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;
void __cdecl newhandler( )
{
   cout << "The new_handler is called:" << endl;
   throw bad_alloc( );
   return;
}

int main( )
{
   set_new_handler (newhandler);
   try
   {
      while ( 1 )
      {
         new int[5000000];
         cout << "Allocating 5000000 ints." << endl;
      }
   }
   catch ( exception e )
   {
      cout << e.what( ) << endl;
   }
}
```

```Output
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
The new_handler is called:
bad allocation
```
