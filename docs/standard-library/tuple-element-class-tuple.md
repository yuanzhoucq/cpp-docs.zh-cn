---
title: "tuple_element 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tuple_element
- std::tuple_element
- utility/std::tuple_element
dev_langs:
- C++
helpviewer_keywords:
- tuple_element Class
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: aadbf7d2c6fece48ab29c1b818995464a790c38b
ms.openlocfilehash: b5568eb951738b1c0c53321d7430c84db6bac9ec
ms.contentlocale: zh-cn
ms.lasthandoff: 03/07/2017

---
# <a name="tupleelement-class"></a>tuple_element 类
包装 `tuple` 元素。 专用化包装 `array` 元素和 `pair` 元素。  
  
## <a name="syntax"></a>语法  
  
```  
// CLASS tuple_element (find element by index)  
template <size_t Index, class Tuple>  
   struct tuple_element;  
 
// tuple_element for const 
template <size_t Index, class Tuple>  
   struct tuple_element<Index, const Tuple>;  
 
// tuple_element for volatile  
template <size_t Index, class Tuple>  
   struct tuple_element<Index, volatile Tuple>;  
 
// tuple_element for const volatile  
template <size_t Index, class Tuple>  
   struct tuple_element<Index, const volatile Tuple>;  
 
// Helper typedef
template <size_t Index, class Tuple>  
   using tuple_element_t = typename tuple_element<Index, Tuple>::type; 

// Specialization for arrays  
template <size_t Index, class Elem, size_t Size>  
   struct tuple_element<Index, array<Elem, Size>>;  
  
// Specializations for pairs
// struct to determine type of element 0 in pair
template <class T1, class T2>
   struct tuple_element<0, pair<T1, T2>>;

// struct to determine type of element 1 in pair
template <class T1, class T2>
   struct tuple_element<1, pair<T1, T2>>;
```  
  
### <a name="parameters"></a>参数  
*索引*  
指定元素的索引。  
  
*Tuple*  
元组的类型。  
  
*Elem*  
数组元素的类型。  
  
*Size*  
数组大小。  

T1 一对中第一个元素的类型。
  
T2  
一对中第二个元素的类型。

## <a name="remarks"></a>备注  
此模板类 `tuple_element` 具有嵌套的 typedef `type`，它是元组类型 `Tuple` 索引 `Index` 处类型的同义词。  

此 typedef `tuple_element_t` 是 `tuple_element<Index, Tuple>::type` 的方便别名。  
  
数组的模板类专用化为接口提供 `array` 作为 `Size` 元素的元组，其中每个元素都具有相同的类型。 每个专用化具有嵌套的 typedef `type` ，它是 `Index` 的 `array`元素的类型的同义词，并且保留了任何 const-volatile 限定。  
  
每个 `pair` 类型的模板专用化都具有一个成员 typedef `type`，它是对中指定位置处元素类型的同义词，保留有任何恒定和/或可变的限定。 此 typedef `tuple_element_t` 是 `tuple_element<N, pair<T1, T2>>::type` 的方便别名。  
  
使用[get 函数&lt;实用工具&gt;](../standard-library/utility-functions.md#get)要返回其元素中指定的位置，或指定的类型。 
  
## <a name="example"></a>示例  
  
```cpp  
#include <tuple>  
#include <string>  
#include <iostream>  
  
using namespace std;  
typedef tuple<int, double, string> MyTuple;  
  
int main() {  
    MyTuple c0{ 0, 1.5, "Tail" };  
  
    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index  
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);  
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type  
  
    cout << val << " " << val2 << " " << val3 << endl;  
}  
```  
  
```Output  
0 1.5 Tail  
```  
  
## <a name="example"></a>示例  
  
```cpp  
#include <array>   
#include <iostream>   
  
using namespace std;  
typedef array<int, 4> MyArray;  
  
int main()  
{  
    MyArray c0 { 0, 1, 2, 3 };  
  
    for (const auto& e : c0)  
    {  
        cout << " " << e;  
    }  
    cout << endl;  
  
    // display first element " 0"   
    tuple_element<0, MyArray>::type val = c0.front();  
    cout << " " << val << endl;  
}  
```  
  
```Output  
 0 1 2 3  
 0  
```  
  
## <a name="example"></a>示例  
  
```cpp  
#include <utility>   
#include <iostream>   
  
using namespace std;  
  
typedef pair<int, double> MyPair;  
int main() {  
    MyPair c0(0, 1.333);  
  
    // display contents " 0 1"   
    cout << " " << get<0>(c0);  
    cout << " " << get<1>(c0) << endl;  
  
    // display first element " 0" by index  
    tuple_element<0, MyPair>::type val = get<0>(c0);  
    cout << " " << val;  
  
    // display second element by type   
    tuple_element<1, MyPair>::type val2 = get<double>(c0);  
    cout << " " << val2 << endl;  
}  
```  
  
```Output  
 0 1.333  
 0 1.333  
```  

## <a name="requirements"></a>要求  
 **标头：**\<tuple>  
 **标头：**\<array>（适用于数组专用化） **标头：**\<utility>（适用于对专用化） **命名空间：**std  
  
## <a name="see-also"></a>另请参阅  
[tuple ](../standard-library/tuple-class.md)

