---
title: "array 类（C++ 标准库）| Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- array
- array/std::array
- array/std::array::const_iterator
- array/std::array::const_pointer
- array/std::array::const_reference
- array/std::array::const_reverse_iterator
- array/std::array::difference_type
- array/std::array::iterator
- array/std::array::pointer
- array/std::array::reference
- array/std::array::reverse_iterator
- array/std::array::size_type
- array/std::array::value_type
- array/std::array::assign
- array/std::array::at
- array/std::array::back
- array/std::array::begin
- array/std::array::cbegin
- array/std::array::cend
- array/std::array::crbegin
- array/std::array::crend
- array/std::array::data
- array/std::array::empty
- array/std::array::end
- array/std::array::fill
- array/std::array::front
- array/std::array::max_size
- array/std::array::rbegin
- array/std::array::rend
- array/std::array::size
- array/std::array::swap
- array/std::array::operator=
- array/std::array::operator[]
- array/std::array::const_iterator
- array/std::array::const_pointer
- array/std::array::const_reference
- array/std::array::const_reverse_iterator
- array/std::array::difference_type
- array/std::array::iterator
- array/std::array::pointer
- array/std::array::reference
- array/std::array::reverse_iterator
- array/std::array::size_type
- array/std::array::value_type
- array/std::array::assign
- array/std::array::at
- array/std::array::back
- array/std::array::begin
- array/std::array::cbegin
- array/std::array::cend
- array/std::array::crbegin
- array/std::array::crend
- array/std::array::data
- array/std::array::empty
- array/std::array::end
- array/std::array::fill
- array/std::array::front
- array/std::array::max_size
- array/std::array::rbegin
- array/std::array::rend
- array/std::array::size
- array/std::array::swap
dev_langs:
- C++
helpviewer_keywords:
- array class
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
caps.latest.revision: 22
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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 9ac4c0becd32ca50e4f56fb38218b4c69cc4d0bd
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="array-class-c-standard-library"></a>array 类（C++ 标准库）
描述了一个对象，此对象控制类型 `Ty` 的元素的长度序列 `N`。 此序列存储为 `Ty` 的数组，包含在 `array<Ty, N>` 对象中。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Ty, std::size_t N>  
class array;  
```  
  
#### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`Ty`|元素的类型。|  
|`N`|元素数量。|  
  
## <a name="members"></a>成员  
  
|||  
|-|-|  
|类型定义|描述|  
|[const_iterator](#const_iterator)|受控序列的常量迭代器的类型。|  
|[const_pointer](#const_pointer)|元素的常量指针的类型。|  
|[const_reference](#const_reference)|元素的常量引用的类型。|  
|[const_reverse_iterator](#const_reverse_iterator)|受控序列的常量反向迭代器的类型。|  
|[difference_type](#difference_type)|两个元素间的带符号距离的类型。|  
|[iterator](#iterator)|受控序列的迭代器的类型。|  
|[pointer](#pointer)|指向元素的指针的类型。|  
|[reference](#reference)|元素的引用的类型。|  
|[reverse_iterator](#reverse_iterator)|受控序列的反向迭代器的类型。|  
|[size_type](#size_type)|两个元素间的无符号距离的类型。|  
|[value_type](#value_type)|元素的类型。|  
  
|||  
|-|-|  
|成员函数|描述|  
|[array](#array)|构造一个数组对象。|  
|[assign](#assign)|替换所有元素。|  
|[at](#at)|访问指定位置处的元素。|  
|[back](#back)|访问最后一个元素。|  
|[begin](#begin)|指定受控序列的开头。|  
|[cbegin](#cbegin)|返回一个随机访问常量迭代器，它指向数组中的第一个元素。|  
|[cend](#cend)|返回一个随机访问常量迭代器，它指向刚超过数组末尾的位置。|  
|[crbegin](#crbegin)|返回一个指向反向数据中第一个元素的常量迭代器。|  
|[crend](#crend)|返回一个指向反向数组末尾的常量迭代器。|  
|[data](#data)|获取第一个元素的地址。|  
|[empty](#empty)|测试元素是否存在。|  
|[end](#end)|指定受控序列的末尾。|  
|[fill](#fill)|将所有元素替换为指定值。|  
|[front](#front)|访问第一个元素。|  
|[max_size](#max_size)|对元素数进行计数。|  
|[rbegin](#rbegin)|指定反向受控序列的开头。|  
|[rend](#rend)|指定反向受控序列的末尾。|  
|[size](#size)|对元素数进行计数。|  
|[swap](#swap)|交换两个容器的内容。|  
  
|||  
|-|-|  
|运算符|说明|  
|[array::operator=](#op_eq)|替换受控序列。|  
|[array::operator[]](#op_at)|访问指定位置处的元素。|  
  
## <a name="remarks"></a>备注  
 此类型具有默认的构造函数 `array()` 和默认的赋值运算符 `operator=`，并且满足 `aggregate` 的要求。 因此，可使用聚合初始化表达式来初始化类型 `array<Ty, N>` 的对象。 例如，  
  
```  
array<int, 4> ai = { 1, 2, 3 };  
```  
  
 创建包含四个整数值的对象 `ai`，分别将前三个元素初始化为值 1、2 和 3，并将第四个元素初始化为 0。  
  
## <a name="requirements"></a>要求  
 **Header:** \<array>  
  
 **命名空间：** std  
  
##  <a name="array"></a>  array::array  
 构造一个数组对象。  
  
```  
array();

array(const array& right);
```  
  
### <a name="parameters"></a>参数  
*right*  
 要插入的对象或范围。  
  
### <a name="remarks"></a>备注  
默认构造函数 `array()` 将受控序列保留为未初始化（或默认已初始化）。 使用它来指定未初始化的控制序列。  
  
复制构造函数 `array(const array& right)` 使用序列 [*right*`.begin()`, *right*`.end()`) 来初始化受控序列。 使用它来指定初始受控序列，该序列是由数组对象 *right* 控制的序列副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_array.cpp   
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
  
    Myarray c1(c0);   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
```  
  
##  <a name="assign"></a>  array::assign  
Obsolete in C++11，由 [fill](#fill) 替代。 替换所有元素。  
  
```  
void assign(const Ty& val);
```  
  
### <a name="parameters"></a>参数  
 `val`  
 要指派的值。  
  
### <a name="remarks"></a>备注  
 成员函数将 `*this` 控制的序列替换为值 `N` 的重复 `val` 元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_assign.cpp   
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
  
    Myarray c1;   
    c1.assign(4);   
  
// display contents " 4 4 4 4"   
    for (Myarray::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
4 4 4 4  
```  
  
##  <a name="at"></a>  array::at  
 访问指定位置处的元素。  
  
```  
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```  
  
### <a name="parameters"></a>参数  
 `off`  
 要访问的元素的位置。  
  
### <a name="remarks"></a>备注  
 成员函数返回对受控序列中 `off` 位置处的元素的引用。 如果该位置无效，则该函数将引发 `out_of_range` 类的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_at.cpp   
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
  
// display odd elements " 1 3"   
    std::cout << " " << c0.at(1);   
    std::cout << " " << c0.at(3);   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
##  <a name="back"></a>  array::back  
 访问最后一个元素。  
  
```  
reference back();

constexpr const_reference back() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数返回对受控序列的最后一个元素的引用，受控序列必须为非空。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_back.cpp   
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
  
// display last element " 3"   
    std::cout << " " << c0.back();   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
3  
```  
  
##  <a name="begin"></a>  array::begin  
 指定受控序列的开头。  
  
```  
iterator begin() noexcept;  
const_iterator begin() const noexcept;  
```  
  
### <a name="remarks"></a>备注  
 该成员函数返回一个随机访问迭代器，指向序列的第一个元素（或刚超出空序列末尾的位置）。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_begin.cpp   
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
  
// display first element " 0"   
    Myarray::iterator it2 = c0.begin();   
    std::cout << " " << *it2;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="cbegin"></a>  array::cbegin  
 返回确定范围中第一个元素地址的 `const` 迭代器。  
  
```  
const_iterator cbegin() const noexcept;  
```  
  
### <a name="return-value"></a>返回值  
 `const` 随机访问迭代器，指向范围的第一个元素，或刚超出空范围末尾的位置（对于空范围，`cbegin() == cend()`）。  
  
### <a name="remarks"></a>备注  
 由于使用 `cbegin` 的返回值，因此不能修改范围中的元素。  
  
 可以使用此成员函数替代 `begin()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在此示例中，将 `Container` 视为支持 `begin()` 和 `cbegin()` 的可修改的 (non- `const`) 任何类型的容器。  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>  array::cend  
 返回一个 `const` 迭代器，此迭代器用于发现刚超出范围中最后一个元素的位置。  
  
```  
const_iterator cend() const noexcept;  
```  
  
### <a name="return-value"></a>返回值  
 指向刚超出范围末尾的位置的随机访问迭代器。  
  
### <a name="remarks"></a>备注  
 `cend` 用于测试迭代器是否超过了其范围的末尾。  
  
 可以使用此成员函数替代 `end()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在此示例中，将 `Container` 视为支持 `end()` 和 `cend()` 的可修改的任何类型的（非- `const`）容器。  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 不应对 `cend` 返回的值取消引用。  
  
##  <a name="const_iterator"></a>  array::const_iterator  
 受控序列的常量迭代器的类型。  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述可用作受控序列的常量随机访问迭代器的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_const_iterator.cpp  
// compile with: /EHsc /W4  
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> MyArray;   
  
int main()   
{   
    MyArray c0 = {0, 1, 2, 3};   
  
    // display contents " 0 1 2 3"   
    std::cout << "it1:";  
    for ( MyArray::const_iterator it1 = c0.begin();   
          it1 != c0.end();   
          ++it1 ) {  
       std::cout << " " << *it1;   
    }  
    std::cout << std::endl;   
  
    // display first element " 0"   
    MyArray::const_iterator it2 = c0.begin();   
    std::cout << "it2:";  
    std::cout << " " << *it2;   
    std::cout << std::endl;   
  
    return (0);   
}  
  
```  
  
```Output  
it1: 0 1 2 3                                  
  
it2: 0  
  
```  
  
##  <a name="const_pointer"></a>  array::const_pointer  
 元素的常量指针的类型。  
  
```  
typedef const Ty *const_pointer;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述了可用作指向序列中元素的常量指针的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_const_pointer.cpp   
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
  
// display first element " 0"   
    Myarray::const_pointer ptr = &*c0.begin();   
    std::cout << " " << *ptr;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="const_reference"></a>  array::const_reference  
 元素的常量引用的类型。  
  
```  
typedef const Ty& const_reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型将可作为常量引用的对象描述为受控序列中的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_const_reference.cpp   
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
  
// display first element " 0"   
    Myarray::const_reference ref = *c0.begin();   
    std::cout << " " << ref;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="const_reverse_iterator"></a>  array::const_reverse_iterator  
 受控序列的常量反向迭代器的类型。  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述为可用作受控序列的常量反向迭代器的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_const_reverse_iterator.cpp   
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
  
// display last element " 3"   
    Myarray::const_reverse_iterator it2 = c0.rbegin();   
    std::cout << " " << *it2;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
3  
```  
  
##  <a name="crbegin"></a>  array::crbegin  
 返回一个指向反向数据中第一个元素的常量迭代器。  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 发现反向数组中的第一个元素或发现曾是非反向数组中的最后一个元素的元素的常量反向随机访问迭代器。  
  
### <a name="remarks"></a>备注  
 返回值为 `crbegin` 时，无法修改数组对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// array_crbegin.cpp  
// compile with: /EHsc  
#include <array>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   array<int, 2> v1 = {1, 2};  
   array<int, 2>::iterator v1_Iter;  
   array<int, 2>::const_reverse_iterator v1_rIter;  
  
   v1_Iter = v1.begin( );  
   cout << "The first element of array is "  
        << *v1_Iter << "." << endl;  
  
   v1_rIter = v1.crbegin( );  
   cout << "The first element of the reversed array is "  
        << *v1_rIter << "." << endl;  
}  
```  
  
```Output  
The first element of array is 1.  
The first element of the reversed array is 2.  
```  
  
##  <a name="crend"></a>  array::crend  
 返回用于寻址反向数组中最后一个元素之后的位置的常量迭代器。  
  
```  
const_reverse_iterator crend() const noexcept;  
```  
  
### <a name="return-value"></a>返回值  
 用于寻址反向数组中最后一个元素之后的位置（非反向数组中第一个元素之前的位置）的常量反向随机存取迭代器。  
  
### <a name="remarks"></a>备注  
 `crend` 与反向数组一起使用，就像 [array::cend](#cend) 与数组一起使用一样。  
  
 如果返回值为 `crend`（适当递减），则不能修改数组对象。  
  
 `crend` 可用于测试反向迭代器是否已到达其数组末尾。  
  
 不应对 `crend` 返回的值取消引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// array_crend.cpp  
// compile with: /EHsc  
#include <array>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   array<int, 2> v1 = {1, 2};  
   array<int, 2>::const_reverse_iterator v1_rIter;  
  
   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )  
      cout << *v1_rIter << endl;  
}  
```  
  
```Output  
2  
1  
```  
  
##  <a name="data"></a>  array::data  
 获取第一个元素的地址。  
  
```  
Ty *data();

const Ty *data() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数返回受控序列中的第一个元素的地址。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_data.cpp   
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
  
// display first element " 0"   
    Myarray::pointer ptr = c0.data();   
    std::cout << " " << *ptr;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="difference_type"></a>  array::difference_type  
 两个元素间的带符号距离的类型。  
  
```  
typedef std::ptrdiff_t difference_type;  
```  
  
### <a name="remarks"></a>备注  
 带符号的整数类型描述一个可表示受控序列中任意两个元素的地址之间的差异的对象。 它是类型 `std::ptrdiff_t`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_difference_type.cpp   
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
  
// display distance first-last " -4"   
    Myarray::difference_type diff = c0.begin() - c0.end();   
    std::cout << " " << diff;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
-4  
```  
  
##  <a name="empty"></a>  array::empty  
 测试元素是否存在。  
  
```  
constexpr bool empty() const;
```  
  
### <a name="remarks"></a>备注  
 仅当 `N == 0` 时，此成员函数才返回 true。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_empty.cpp   
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
  
// display whether c0 is empty " false"   
    std::cout << std::boolalpha << " " << c0.empty();   
    std::cout << std::endl;   
  
    std::array<int, 0> c1;   
  
// display whether c1 is empty " true"   
    std::cout << std::boolalpha << " " << c1.empty();   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
false  
true  
```  
  
##  <a name="end"></a>  array::end  
 指定受控序列的末尾。  
  
```  
reference end();

const_reference end() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个随机访问迭代器，它指向刚超出序列末尾的位置。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_end.cpp   
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
  
// display last element " 3"   
    Myarray::iterator it2 = c0.end();   
    std::cout << " " << *--it2;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
3  
```  
  
##  <a name="fill"></a>  array::fill  
 清除数组并将指定的元素复制到该空数组。  
  
```  
void fill(const Type& val);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|`val`|要插入到数组中的元素的值。|  
  
### <a name="remarks"></a>备注  
 `fill` 将数组的每个元素替换为指定的值。  
  
### <a name="example"></a>示例  
  
```cpp  
// array_fill.cpp  
// compile with: /EHsc  
#include <array>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   array<int, 2> v1 = {1, 2};  
   array<int, 2>::iterator iter;  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
  
   v1.fill(3);  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
}  
```  
  
##  <a name="front"></a>  array::front  
 访问第一个元素。  
  
```  
reference front();

constexpr const_reference front() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数返回对受控序列的第一个元素的引用，该元素必须为非空。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_front.cpp   
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
  
// display first element " 0"   
    std::cout << " " << c0.front();   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="iterator"></a>  array::iterator  
 受控序列的迭代器的类型。  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述可用作受控序列的随机访问迭代器的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_iterator.cpp   
// compile with: /EHsc /W4  
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> MyArray;   
  
int main()   
{   
    MyArray c0 = {0, 1, 2, 3};   
  
    // display contents " 0 1 2 3"   
    std::cout << "it1:";  
    for ( MyArray::iterator it1 = c0.begin();   
          it1 != c0.end();   
          ++it1 ) {  
       std::cout << " " << *it1;   
    }  
    std::cout << std::endl;   
  
    // display first element " 0"   
    MyArray::iterator it2 = c0.begin();   
    std::cout << "it2:";  
    std::cout << " " << *it2;   
    std::cout << std::endl;   
  
    return (0);   
}  
  
```  
  
```Output  
it1: 0 1 2 3                                  
  
it2: 0  
  
```  
  
##  <a name="max_size"></a>  array::max_size  
 对元素数进行计数。  
  
```  
constexpr size_type max_size() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数返回 `N`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_max_size.cpp   
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
  
// display (maximum) size " 4"   
    std::cout << " " << c0.max_size();   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
4  
```  
  
##  <a name="op_at"></a>  array::operator[]  
 访问指定位置处的元素。  
  
```  
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```  
  
### <a name="parameters"></a>参数  
 `off`  
 要访问的元素的位置。  
  
### <a name="remarks"></a>备注  
 成员函数返回对受控序列中 `off` 位置处的元素的引用。 如果该位置无效，则该行为未定义。  
  
此外，还为获取 `array` 的元素的引用提供非成员 [get](array-functions.md#get) 函数。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_operator_sub.cpp   
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
  
// display odd elements " 1 3"   
    std::cout << " " << c0[1];   
    std::cout << " " << c0[3];   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
1 3  
```  
  
##  <a name="op_eq"></a>  array::operator=  
 替换受控序列。  
  
```  
array <Value>%  operator=(array <Value>% right);
```  
  
### <a name="parameters"></a>参数  
 右  
 用于复制的容器。  
  
### <a name="remarks"></a>备注  
 成员运算符将 `right` 的每个元素分配给相应受控序列的元素，然后返回 `*this`。 用它将受控序列替换为 `right` 中的受控序列的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_operator_as.cpp   
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
  
    Myarray c1;   
    c1 = c0;   
  
// display copied contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
```  
  
##  <a name="pointer"></a>  array::pointer  
 指向元素的指针的类型。  
  
```  
typedef Ty *pointer;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述了可用作指向序列中元素的指针的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_pointer.cpp   
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
  
// display first element " 0"   
    Myarray::pointer ptr = &*c0.begin();   
    std::cout << " " << *ptr;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="rbegin"></a>  array::rbegin  
 指定反向受控序列的开头。  
  
```  
reverse_iterator rbegin()noexcept;  
const_reverse_iterator rbegin() const noexcept;  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个反向迭代器，它指向刚超出受控序列末尾的位置。 因此，它指定反向序列的开头。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_rbegin.cpp   
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
  
// display last element " 3"   
    Myarray::const_reverse_iterator it2 = c0.rbegin();   
    std::cout << " " << *it2;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
3  
```  
  
##  <a name="reference"></a>  array::reference  
 元素的引用的类型。  
  
```  
typedef Ty& reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述了可用作对受控序列中元素的引用的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_reference.cpp   
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
  
// display first element " 0"   
    Myarray::reference ref = *c0.begin();   
    std::cout << " " << ref;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="rend"></a>  array::rend  
 指定反向受控序列的末尾。  
  
```  
reverse_iterator rend()noexcept;  
const_reverse_iterator rend() const noexcept;  
```  
  
### <a name="remarks"></a>备注  
 该成员函数返回一个反向迭代器，指向序列的第一个元素（或刚超出空序列末尾的位置）。 因此，它指定反向序列的末尾。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_rend.cpp   
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
  
// display first element " 0"   
    Myarray::const_reverse_iterator it2 = c0.rend();   
    std::cout << " " << *--it2;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="reverse_iterator"></a>  array::reverse_iterator  
 受控序列的反向迭代器的类型。  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述为可用作受控序列的反向迭代器的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_reverse_iterator.cpp   
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
  
// display last element " 3"   
    Myarray::reverse_iterator it2 = c0.rbegin();   
    std::cout << " " << *it2;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
3  
```  
  
##  <a name="size"></a>  array::size  
 对元素数进行计数。  
  
```  
constexpr size_type size() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数返回 `N`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_size.cpp   
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
  
// display size " 4"   
    std::cout << " " << c0.size();   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
4  
```  
  
##  <a name="size_type"></a>  array::size_type  
 两个元素间的无符号距离的类型。  
  
```  
typedef std::size_t size_type;  
```  
  
### <a name="remarks"></a>备注  
 无符号的整数类型描述可表示任何受控序列长度的对象。 它是类型 `std::size_t`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_size_type.cpp   
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
  
// display distance last-first " 4"   
    Myarray::size_type diff = c0.end() - c0.begin();   
    std::cout << " " << diff;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
4  
```  
  
##  <a name="swap"></a>  array::swap  
将此数组的内容交换到另一个数组。  
  
```  
void swap(array& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 要与其交换内容的数组。  
  
### <a name="remarks"></a>备注  
成员函数交换 `*this` 和 `right` 之间的受控序列。 它执行与 `N` 成正比的多个元素分配和构造函数调用。  

此外还提供交换两个 `array` 实例的非成员 [swap](array-functions.md#swap) 函数。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_swap.cpp   
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
    c0.swap(c1);   
  
// display swapped contents " 4 5 6 7"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    swap(c0, c1);   
  
// display swapped contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
4 5 6 7  
0 1 2 3  
```  
  
##  <a name="value_type"></a>  array::value_type  
 元素的类型。  
  
```  
typedef Ty value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Ty`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__array__array_value_type.cpp   
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
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        {   
        Myarray::value_type val = *it;   
        std::cout << " " << val;   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<array>](../standard-library/array.md)


