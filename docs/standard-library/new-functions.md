---
title: "&lt;new&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
caps.latest.revision: 10
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 6ce4e11a41f199d4ec82a593b53c2f0b7f1c47e4
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="ltnewgt-functions"></a>&lt;new&gt; 函数
|||  
|-|-|  
|[nothrow](#nothrow)|[set_new_handler](#set_new_handler)|  
  
##  <a name="nothrow"></a>  nothrow  
 提供一个对象，用作 **new** 和 **delete** 的 `nothrow` 版本的自变量。  
  
```  
extern const std::nothrow_t nothrow;  
```  
  
### <a name="remarks"></a>备注  
 该对象用作与参数类型 [std::nothrow_t](../standard-library/nothrow-t-structure.md) 匹配的函数自变量。  
  
### <a name="example"></a>示例  
  有关如何将 `std::nothrow_t` 用作函数参数的示例，请参阅[运算符 new](../standard-library/new-operators.md#op_new) 和[运算符 new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)。  
  
##  <a name="set_new_handler"></a>  set_new_handler  
 安装一个用户函数，当 `operator new` 尝试分配内存失败时会调用该函数。  
  
```  
new_handler set_new_handler(new_handler Pnew) throw();
```  
  
### <a name="parameters"></a>参数  
 `Pnew`  
 要安装的 new_handler。  
  
### <a name="return-value"></a>返回值  
 第一次调用时为 0，后续调用时为上一个 `new_handler`。  
  
### <a name="remarks"></a>备注  
 该函数将 `Pnew` 存储于其维护的静态[新处理程序](../standard-library/new-typedefs.md#new_handler)指针中，然后返回以前存储在指针中的值。 此新处理程序由[运算符 new](../standard-library/new-operators.md#op_new)( **size_t**) 使用。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [\<new>](../standard-library/new.md)


