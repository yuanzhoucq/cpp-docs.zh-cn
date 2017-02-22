---
title: "tuple_size 类 &lt;元祖&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "tuple_size 类 <元祖> (TR1)"
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# tuple_size 类 &lt;元祖&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

报告的元素数的 `tuple` 包含。  
  
## <a name="syntax"></a>语法  
  
```  
// TEMPLATE STRUCT tuple_size  
template <class Tuple>  
struct tuple_size;  
 
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
 `Tuple`  
 元组的类型。  
  
## <a name="remarks"></a>备注  
 模板类拥有成员 `value` ，它是其值是元组类型的范围的整型常量表达式 `Tuple`。  
  
## <a name="example"></a>示例  
  
```  
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
  
/*  
Output:  
0 1.5 2 3.7  
4  
*/  
```  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 元组>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>请参阅  
 [\< 元组>](../standard-library/tuple.md)   
 [元组](../standard-library/tuple-class.md)  
 [tuple_element 类](../standard-library/tuple-element-class-tuple.md)
