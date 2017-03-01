---
title: "&lt;tuple&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tuple/std::operator!=
- tuple/std::operator>
- tuple/std::operator>=
- tuple/std::operator<
- tuple/std::operator<=
- tuple/std::operator==
ms.assetid: f25752dc-d3e2-4e12-b5ac-9a8682ca60ed
caps.latest.revision: 13
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 9d8418ee3cd3d2ff0295b7cfa8beb063000ebc2f
ms.lasthandoff: 02/24/2017

---
# <a name="lttuplegt-operators"></a>&lt;tuple&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>operator!=  
 比较 `tuple` 对象是否不相等。  
  
```  
template <class T1, class T2, ..., class TN,  
    class U1, class U2, ..., class UN>  
bool operator!=(const tuple<T1, T2, ..., TN>& tpl1,  
    const tuple<U1, U2, ..., UN>& tpl2);
```  
  
### <a name="parameters"></a>参数  
 `TN`  
 第 N 个元组元素的类型。  
  
### <a name="remarks"></a>备注  
 如果 `N` 为 0，则函数返回 false，否则返回 `get<0>(tpl1) != get<0>(tpl2) || get<1>(tpl1) != get<1>(tpl2) || ... || get<N - 1>(tpl1) == get<N - 1>(tpl2)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__tuple__operator_ne.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main() {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1 = std::make_tuple(4, 5, 6, 7);   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
// display results of comparisons   
    std::cout << std::boolalpha << " " << (c0 != c0);   
    std::cout << std::endl;   
    std::cout << std::boolalpha << " " << (c0 != c1);   
    std::cout << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
false  
true  
```  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>operator&lt;  
 比较 `tuple` 对象是否更小。  
  
```  
template <class T1, class T2, ..., class TN,  
    class U1, class U2, ..., class UN>  
bool operator<(const tuple<T1, T2, ..., TN>& tpl1,  
    const tuple<U1, U2, ..., UN>& tpl2);
```  
  
### <a name="parameters"></a>参数  
 `TN`  
 第 N 个元组元素的类型。  
  
### <a name="remarks"></a>备注  
 如果 `N` 大于 0，且 `tpl1` 中的第一个不同值小于 `tpl2` 中的相应值，则函数返回 ture，否则返回 false。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__tuple__operator_lt.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main() {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1 = std::make_tuple(4, 5, 6, 7);   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
// display results of comparisons   
    std::cout << std::boolalpha << " " << (c0 < c0);   
    std::cout << std::endl;   
    std::cout << std::boolalpha << " " << (c0 < c1);   
    std::cout << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
false  
true  
```  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>operator&lt;=  
 比较 `tuple` 对象，条件为小于或等于。  
  
```  
template <class T1, class T2, ..., class TN,  
    class U1, class U2, ..., class UN>  
bool operator<=(const tuple<T1, T2, ..., TN>& tpl1,  
    const tuple<U1, U2, ..., UN>& tpl2);
```  
  
### <a name="parameters"></a>参数  
 `TN`  
 第 N 个元组元素的类型。  
  
### <a name="remarks"></a>备注  
 该函数返回 `!(tpl2 < tpl1)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__tuple__operator_le.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main() {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1 = std::make_tuple(4, 5, 6, 7);   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
// display results of comparisons   
    std::cout << std::boolalpha << " " << (c0 <= c0);   
    std::cout << std::endl;   
    std::cout << std::boolalpha << " " << (c1 <= c0);   
    std::cout << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
true  
false  
```  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>operator==  
 比较 `tuple` 对象是否相等。  
  
```  
template <class T1, class T2, ..., class TN,  
    class U1, class U2, ..., class UN>  
bool operator==(const tuple<T1, T2, ..., TN>& tpl1,  
    const tuple<U1, U2, ..., UN>& tpl2);
```  
  
### <a name="parameters"></a>参数  
 `TN`  
 第 N 个元组元素的类型。  
  
### <a name="remarks"></a>备注  
 如果 `N` 为 0，则函数返回 true，否则返回 `get<0>(tpl1) == get<0>(tpl2) && get<1>(tpl1) == get<1>(tpl2) && ... && get<N - 1>(tpl1) == get<N - 1>(tpl2)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__tuple__operator_eq.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main() {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1 = std::make_tuple(4, 5, 6, 7);   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
// display results of comparisons   
    std::cout << std::boolalpha << " " << (c0 == c0);   
    std::cout << std::endl;   
    std::cout << std::boolalpha << " " << (c0 == c1);   
    std::cout << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
true  
false  
```  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>operator&gt;  
 比较 `tuple` 对象是否更大。  
  
```  
template <class T1, class T2, ..., class TN,  
    class U1, class U2, ..., class UN>  
bool operator>(const tuple<T1, T2, ..., TN>& tpl1,  
    const tuple<U1, U2, ..., UN>& tpl2);
```  
  
### <a name="parameters"></a>参数  
 `TN`  
 第 N 个元组元素的类型。  
  
### <a name="remarks"></a>备注  
 该函数返回 `tpl2 < tpl1`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__tuple__operator_gt.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main() {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1 = std::make_tuple(4, 5, 6, 7);   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
// display results of comparisons   
    std::cout << std::boolalpha << " " << (c0 > c0);   
    std::cout << std::endl;   
    std::cout << std::boolalpha << " " << (c1 > c0);   
    std::cout << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
false  
true  
```  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>operator&gt;=  
 比较 `tuple` 对象是否更大或相等。  
  
```  
template <class T1, class T2, ..., class TN,  
    class U1, class U2, ..., class UN>  
bool operator>=(const tuple<T1, T2, ..., TN>& tpl1,  
    const tuple<U1, U2, ..., UN>& tpl2);
```  
  
### <a name="parameters"></a>参数  
 `TN`  
 第 N 个元组元素的类型。  
  
### <a name="remarks"></a>备注  
 该函数返回 `!(tpl1 < tpl2)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__tuple__operator_ge.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main() {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1 = std::make_tuple(4, 5, 6, 7);   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
// display results of comparisons   
    std::cout << std::boolalpha << " " << (c0 >= c0);   
    std::cout << std::endl;   
    std::cout << std::boolalpha << " " << (c0 >= c1);   
    std::cout << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
true  
false  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<tuple>](../standard-library/tuple.md)


