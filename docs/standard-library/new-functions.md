---
title: '&lt;new&gt; 函数 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: f930fb43ea554e1dd445dabb382adecc6f67e35f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964952"
---
# <a name="ltnewgt-functions"></a>&lt;new&gt; 函数

|||
|-|-|
|[nothrow](#nothrow)|[set_new_handler](#set_new_handler)|

## <a name="nothrow"></a>  nothrow

提供一个对象，用作自变量**nothrow**新版**新**并**删除**。

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>备注

该对象用作与参数类型 [std::nothrow_t](../standard-library/nothrow-t-structure.md) 匹配的函数自变量。

### <a name="example"></a>示例

有关如何将 `std::nothrow_t` 用作函数参数的示例，请参阅[运算符 new](../standard-library/new-operators.md#op_new) 和[运算符 new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)。

## <a name="set_new_handler"></a>  set_new_handler

安装时要调用的用户函数**运算符 new**中尝试分配内存失败。

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>参数

*Pnew*  
`new_handler`安装。

### <a name="return-value"></a>返回值

第一次调用时为 0，后续调用时为上一个 `new_handler`。

### <a name="remarks"></a>备注

函数存储*Pnew*在静态[新的处理程序](../standard-library/new-typedefs.md#new_handler)指针维护，然后返回以前存储在指针中的值。 新的处理程序可供[运算符 new](../standard-library/new-operators.md#op_new)(**size_t**)。

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

## <a name="see-also"></a>请参阅

[\<new>](../standard-library/new.md)<br/>
