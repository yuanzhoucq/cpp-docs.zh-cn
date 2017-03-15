---
title: "&lt;array&gt; 运算符 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::array::operator!=
- array/std::array::operator!=
- std::array::operator<
- array/std::array::operator<
- std::array::operator<=
- array/std::array::operator<=
- std::array::operator>
- array/std::array::operator>
- std::array::operator>=
- array/std::array::operator>=
- std::array::operator==
- array/std::array::operator==
ms.assetid: c8f46282-f179-4909-9a01-639cb8e18c27
caps.latest.revision: 12
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: f293f074f2b8e2334dc70fbebba8e6f4c17efecc
ms.openlocfilehash: 43cbdb4fe2baeab24508161ae0ce9785f5a8cbab
ms.lasthandoff: 02/24/2017

---
# <a name="ltarraygt-operators"></a>&lt;array&gt; 运算符
\<array> 标头包含这些 `array` 非成员比较模板函数。  
  
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 数组比较，不等于。  
  
```  
template <Ty, std::size_t N>  
bool operator!=(
    const array<Ty, N>& left,  
    const array<Ty, N>& right);
```  
  
### <a name="parameters"></a>参数  
 `Ty`  
 元素的类型。  
  
 `N`  
 数组大小。  
  
 `left`  
 要比较的左容器。  
  
 `right`  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 此模板函数返回 `!(left == right)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__operator_ne.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    Myarray c1 = {4, 5, 6, 7};   
  
// display contents " 4 5 6 7"   
    for (Myarray::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " " << *it;   
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
4 5 6 7  
false  
true  
```  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>  operator&lt;  
 数组的比较，小于。  
  
```  
template <Ty, std::size_t N>  
bool operator<(
    const array<Ty, N>& left,  
    const array<Ty, N>& right);
```  
  
### <a name="parameters"></a>参数  
 `Ty`  
 元素的类型。  
  
 `N`  
 数组大小。  
  
 `left`  
 要比较的左容器。  
  
 `right`  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 该模板函数重载 `operator<` 以比较模板类 [array 类](../standard-library/array-class-stl.md)的两个对象。 该函数返回 `lexicographical_compare(left.begin(), left.end(), right.begin())`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__operator_lt.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    Myarray c1 = {4, 5, 6, 7};   
  
// display contents " 4 5 6 7"   
    for (Myarray::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " " << *it;   
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
4 5 6 7  
false  
true  
```  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>  operator&lt;=  
 数组的比较，小于或等于。  
  
```  
template <Ty, std::size_t N>  
bool operator<=(
    const array<Ty, N>& left,  
    const array<Ty, N>& right);
```  
  
### <a name="parameters"></a>参数  
 `Ty`  
 元素的类型。  
  
 `N`  
 数组大小。  
  
 `left`  
 要比较的左容器。  
  
 `right`  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 此模板函数返回 `!(right < left)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__operator_le.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    Myarray c1 = {4, 5, 6, 7};   
  
// display contents " 4 5 6 7"   
    for (Myarray::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " " << *it;   
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
4 5 6 7  
true  
false  
```  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 数组比较，等于。  
  
```  
template <Ty, std::size_t N>  
bool operator==(
    const array<Ty, N>& left,  
    const array<Ty, N>& right);
```  
  
### <a name="parameters"></a>参数  
 `Ty`  
 元素的类型。  
  
 `N`  
 数组大小。  
  
 `left`  
 要比较的左容器。  
  
 `right`  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 该模板函数重载 `operator==` 以比较模板类 [array 类](../standard-library/array-class-stl.md)的两个对象。 该函数返回 `equal(left.begin(), left.end(), right.begin())`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__operator_eq.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    Myarray c1 = {4, 5, 6, 7};   
  
// display contents " 4 5 6 7"   
    for (Myarray::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " " << *it;   
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
4 5 6 7  
true  
false  
```  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>  operator&gt;  
 数组比较，大于。  
  
```  
template <Ty, std::size_t N>  
bool operator>(
    const array<Ty, N>& left,  
    const array<Ty, N>& right);
```  
  
### <a name="parameters"></a>参数  
 `Ty`  
 元素的类型。  
  
 `N`  
 数组大小。  
  
 `left`  
 要比较的左容器。  
  
 `right`  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 此模板函数返回 `(right < left)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__operator_gt.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    Myarray c1 = {4, 5, 6, 7};   
  
// display contents " 4 5 6 7"   
    for (Myarray::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " " << *it;   
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
4 5 6 7  
false  
true  
```  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>  operator&gt;=  
 数组比较，大于或等于。  
  
```  
template <Ty, std::size_t N>  
bool operator>=(
    const array<Ty, N>& left,  
    const array<Ty, N>& right);
```  
  
### <a name="parameters"></a>参数  
 `Ty`  
 元素的类型。  
  
 `N`  
 数组大小。  
  
 `left`  
 要比较的左容器。  
  
 `right`  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 此模板函数返回 `!(left < right)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__operator_ge.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    Myarray c1 = {4, 5, 6, 7};   
  
// display contents " 4 5 6 7"   
    for (Myarray::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " " << *it;   
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
4 5 6 7  
true  
false  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<array>](../standard-library/array.md)


