---
title: "tuple_size 类 &lt;utility&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tuple_size"
  - "std::tr1::tuple_size"
  - "std.tr1.tuple_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tuple_size 类 <utility> (TR1)"
ms.assetid: 36d04207-ed87-4c11-9875-150c59833b79
caps.latest.revision: 21
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tuple_size 类 &lt;utility&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包装 `pair` 元素计数。  
  
## 语法  
  
```  
template<class Tuple>  
struct tuple_size;  
  
template<class T1, class T2>  
struct tuple_size<pair<T1, T2>>   : integral_constant<size_t, 2>  
  
// size of const tuple  
template<class Tuple>  
struct tuple_size<const Tuple>;  
  
// size of volatile tuple  
template<class Tuple>  
struct tuple_size<volatile Tuple>;  
  
// size of const volatile tuple  
template<class Tuple>  
struct tuple_size<const volatile Tuple>;  
```  
  
#### 参数  
 `T1`  
 第一个 pair 元素的类型。  
  
 `T2`  
 第二个 pair 元素的类型。  
  
## 备注  
 此模板是模板类 [tuple\_size 类](../standard-library/tuple-size-class-tuple.md) 的专用化。 它拥有成员 `value`，该成员是值为 2 的整型常数表达式。  
  
## 示例  
  
```  
#include <utility>   
#include <iostream>   
  
using namespace std;  
  
typedef pair<int, double> MyPair;  
  
int main()  
{  
    MyPair c0(0, 1.1);  
  
    // display contents " 0 1.1"   
    cout << " " << get<0>(c0);  
    cout << " " << get<1>(c0) << endl;  
  
    // display size " 2"   
    cout << " " << tuple_size<MyPair>::value << endl;  
  
}  
  
/*  
Output:  
0 1.1  
2  
*/  
```  
  
## 要求  
 **标头：**\<utility\>  
  
 **命名空间：**std  
  
## 请参阅  
 [\<utility\>](../standard-library/utility.md)   
 [get 函数](../Topic/get%20Function%20%3Cutility%3E.md)   
 [tuple\_element 类](../standard-library/tuple-element-class-utility.md)