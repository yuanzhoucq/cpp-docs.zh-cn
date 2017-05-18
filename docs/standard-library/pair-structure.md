---
title: "pair 结构 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- utility/std::pair
- pair
dev_langs:
- C++
helpviewer_keywords:
- pair class
ms.assetid: 539d3d67-80a2-4170-b347-783495d42109
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: f9f6574029dd40d0c8c2a2ff2a5f73f4744f5ffe
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="pair-structure"></a>pair 结构
一种结构，该结构提供了将两个对象视为单个对象的的功能。  
  
## <a name="syntax"></a>语法  
```  
struct pair
{
    typedef T1 first_type;
    typedef T2 second_type;
    T1 first;
    T2 second;
    constexpr pair();
    constexpr pair(
        const T1& Val1,
        const T2& Val2);

    template <class Other1, class Other2>
    constexpr pair(const pair<Other1, Other2>& Right);

    template <class Other1, class Other2>
    constexpr pair(const pair <Other1 Val1, Other2 Val2>&& Right);

    template <class Other1, class Other2>
    constexpr pair(Other1&& Val1, Other2&& Val2);
};
```  
#### <a name="parameters"></a>参数  
 `Val1`  
 初始化 `pair` 的第一个元素的值。  
  
 `Val2`  
 初始化 `pair` 的第二个元素的值。  
  
 `Right`  
 一个对，其值将用于初始化另一对的元素。  
  
## <a name="return-value"></a>返回值  
 第一个（默认）构造函数将该对的第一个元素初始化为类型 **T1** 的默认值，将第二个元素初始化为类型 **T2** 的默认值。  
  
 第二个构造函数将该对的第一个元素初始化为 `Val1`，将第二个元素初始化为 *Val2。*  
  
 第三个（模板）构造函数将该对的第一个元素初始化为 `Right`. **first** 并将第二个元素初始化为 `Right`. **second**。  
  
 第四个构造函数使用[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md) 将该对的第一个元素初始化为 `Val1`，将第二个元素初始化为 *Val2*。  
  
## <a name="remarks"></a>备注  
 模板结构分别存储类型为 **T1** 和 **T2** 的一对对象。 类型 **first_type** 等同于模板参数 **T1**，且类型 **second_type** 等同于模板参数 **T2**。 **T1** 和 **T2** 每个只需要提供一个默认构造函数、单自变量构造函数和析构函数。 类型为 `pair` 的所有成员都是公共的，因为该类型声明为 `struct` 而不是 **class**。 对的两种最常见用法是作为返回两个值的函数的返回类型以及作为关联容器类 [map 类](../standard-library/map-class.md)和 [multimap 类](../standard-library/multimap-class.md)的元素，这些类具有与每个元素相关联的键和值类型。 后者满足对关联容器的要求，且具有形式为 `pair`< **const**`key_type`, `mapped_type`> 的值类型。  
  
## <a name="example"></a>示例  
  
```cpp  
// utility_pair.cpp  
// compile with: /EHsc  
#include <utility>  
#include <map>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Using the constructor to declare and initialize a pair  
   pair <int, double> p1 ( 10, 1.1e-2 );  
  
   // Compare using the helper function to declare and initialize a pair  
   pair <int, double> p2;  
   p2 = make_pair ( 10, 2.22e-1 );  
  
   // Making a copy of a pair  
   pair <int, double> p3 ( p1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
  
   // Using a pair for a map element  
   map <int, int> m1;  
   map <int, int>::iterator m1_Iter;  
  
   typedef pair <int, int> Map_Int_Pair;  
  
   m1.insert ( Map_Int_Pair ( 1, 10 ) );  
   m1.insert ( Map_Int_Pair ( 2, 20 ) );  
   m1.insert ( Map_Int_Pair ( 3, 30 ) );  
  
   cout << "The element pairs of the map m1 are:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " ( " << m1_Iter -> first << ", "  
           << m1_Iter -> second << " )";  
   cout   << "." << endl;  
  
   // Using pair as a return type for a function  
   pair< map<int,int>::iterator, bool > pr1, pr2;  
   pr1 = m1.insert ( Map_Int_Pair ( 4, 40 ) );  
   pr2 = m1.insert ( Map_Int_Pair (1, 10 ) );  
  
   if( pr1.second == true )  
   {  
      cout << "The element (4,40) was inserted successfully in m1."  
           << endl;  
   }  
   else     
   {  
      cout << "The element with a key value of\n"  
           << " ( (pr1.first) -> first ) = " << ( pr1.first ) -> first   
           << " is already in m1,\n so the insertion failed." << endl;  
   }  
  
   if( pr2.second == true )  
   {  
      cout << "The element (1,10) was inserted successfully in m1."  
           << endl;  
   }  
   else     
   {  
      cout << "The element with a key value of\n"  
           << " ( (pr2.first) -> first ) = " << ( pr2.first ) -> first   
           << " is already in m1,\n so the insertion failed." << endl;  
   }  
}  
\* Output:   
The pair p1 is: ( 10, 0.011 ).  
The pair p2 is: ( 10, 0.222 ).  
The pair p3 is: ( 10, 0.011 ).  
The element pairs of the map m1 are: ( 1, 10 ) ( 2, 20 ) ( 3, 30 ).  
The element (4,40) was inserted successfully in m1.  
The element with a key value of  
 ( (pr2.first) -> first ) = 1 is already in m1,  
 so the insertion failed.  
*\  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<utility>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




