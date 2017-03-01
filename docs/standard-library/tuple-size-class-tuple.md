---
title: "tuple_size 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tuple_size
- std::tuple_size
- utility/std::tuple_size
dev_langs:
- C++
helpviewer_keywords:
- tuple_size Class
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
caps.latest.revision: 23
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
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: f0ae102852f1db46b68d86438e20ce9645535d19
ms.lasthandoff: 02/24/2017

---
# <a name="tuplesize-class"></a>tuple_size 类
包含 `tuple` 包含的元素数目。  
  
## <a name="syntax"></a>语法  
  
```  
// TEMPLATE STRUCT tuple_size  
template <class Tuple>  
   struct tuple_size;  
  
// number of elements in array  
template <class Elem, size_t Size>  
   struct tuple_size<array<Elem, Size>>  
      : integral_constant<size_t, Size>; 
  
// size of pair
template <class T1, class T2>
   struct tuple_size<pair<T1, T2>> 
      : integral_constant<size_t, 2>

// size of tuple  
template <class... Types>  
   struct tuple_size<tuple<Types...>>  
      : integral_constant<size_t, sizeof...(Types)>;  
  
// size of const tuple  
template <class Tuple>  
   struct tuple_size<const Tuple>;  
  
// size of volatile tuple  
template <class Tuple>  
   struct tuple_size<volatile Tuple>;  
  
// size of const volatile tuple  
template <class Tuple>  
   struct tuple_size<const volatile Tuple>;   
```  
  
#### <a name="parameters"></a>参数  
*Tuple*  
元组的类型。 
  
*Elem*  
数组元素的类型。 
  
*Size*  
数组大小。 
  
T1  
对的第一个成员的类型。 
  
T2  
对的第二个成员的类型。 
  
*类型*  
元组元素的类型。 
  
  
## <a name="remarks"></a>备注  
模板类拥有成员 `value` ，此成员是一个整型常数表达式，值为元祖类型 `Tuple`的范围。  
  
数组的模板专用化拥有成员 `value`，它是整型常数表达式，值为 `Size`，即数组的大小。  
  
对的模板专用化拥有成员 `value`，它是整型常数表达式，值为 2。  
  
## <a name="example"></a>示例  
  
```cpp  
#include <tuple>   
#include <iostream>  
  
using namespace std;  
  
typedef tuple<int, double, int, double> MyTuple;  
int main()  
{  
    MyTuple c0(0, 1.5, 2, 3.7);  
  
    // display contents " 0 1 2 3"   
    cout << " " << get<0>(c0);  
    cout << " " << get<1>(c0);  
    cout << " " << get<2>(c0);  
    cout << " " << get<3>(c0) << endl;  
  
    // display size " 4"   
    cout << " " << tuple_size<MyTuple>::value << endl;  
}  
```  
  
```Output  
 0 1.5 2 3.7  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<tuple>  
 **标头：**\<array>（适用于数组专用化）  
 **标头：**\<utility>（适用于对专用化）  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [\<tuple>](../standard-library/tuple.md)   
 [tuple](../standard-library/tuple-class.md)  
 [tuple_element 类](../standard-library/tuple-element-class-tuple.md)

