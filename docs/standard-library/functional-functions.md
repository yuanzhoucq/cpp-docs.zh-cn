---
title: "&lt;functional&gt; 函数 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- functional/std::bind
- xfunctional/std::bind1st
- xfunctional/std::bind2nd
- xfunctional/std::bit_and
- xfunctional/std::bit_not
- xfunctional/std::bit_or
- xfunctional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- xfunctional/std::mem_fn
- xfunctional/std::mem_fun_ref
- xfunctional/std::not1
- xfunctional/std::not2
- xfunctional/std::ptr_fun
- functional/std::ref
- functional/std::swap
dev_langs: C++
helpviewer_keywords:
- std::bind [C++]
- std::bind1st
- std::bind2nd
- std::bit_and [C++]
- std::bit_not [C++]
- std::bit_or [C++]
- std::bit_xor [C++]
- std::cref [C++]
- 
- std::mem_fn [C++]
- std::mem_fun [C++]
- std::mem_fun_ref [C++]
- std::not1
- std::not2
- std::ptr_fun [C++]
- std::ref [C++]
- 
- std::swap [C++]
- 
- std::bind [C++]
- std::bind1st
- std::bind2nd
- std::bit_and [C++]
- std::bit_not [C++]
- std::bit_or [C++]
- std::bit_xor [C++]
- std::cref [C++]
- std::mem_fn [C++]
- std::mem_fun [C++]
- std::mem_fun_ref [C++]
- std::not1
- std::not2
- std::ptr_fun [C++]
- std::ref [C++]
- std::swap [C++]
ms.assetid: c34d0b45-50a7-447a-9368-2210d06339a4
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f8ebfab21459083e49576eb07331fe206299d96a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ltfunctionalgt-functions"></a>&lt;functional&gt; 函数
||||  
|-|-|-|  
|[bind](#bind)|[bind1st](#bind1st)|[bind2nd](#bind2nd)|  
|[bit_and](#bit_and)|[bit_not](#bit_not)|[bit_or](#bit_or)|  
|[bit_xor](#bit_xor)|[cref](#cref)|[mem_fn](#mem_fn)|  
|[mem_fun](#mem_fun)|[mem_fun_ref](#mem_fun_ref)|[not1](#not1)|  
|[not2](#not2)|[ptr_fun](#ptr_fun)|[ref](#ref)|  
|[swap](#swap)|  
  
##  <a name="bind"></a>  bind  
 将自变量绑定到可调用对象。  
  
```  
template <class Fty, class T1, class T2, ..., class TN>  
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);

template <class Ret, class Fty, class T1, class T2, ..., class TN>  
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);
```  
  
### <a name="parameters"></a>参数  
 `Fty`  
 要调用的对象的类型。  
  
 `TN`  
 第 N 个调用参数的类型。  
  
 `fn`  
 要调用的对象。  
  
 `tN`  
 第 N 个调用参数。  
  
### <a name="remarks"></a>备注  
 类型 `Fty, T1, T2, ..., TN` 必须可构造副本，并且对于某些值 `w1, w2, ..., wN` 而言，`INVOKE(fn, t1, ..., tN)` 必须是有效的表达式。  
  
 第一个模板函数返回具有弱结果类型的转发调用包装器 `g`。 效果`g(u1, u2, ..., uM)`是`INVOKE(f, v1, v2, ..., vN, ` [result_of](../standard-library/result-of-class.md)`<Fty cv (V1, V2, ..., VN)>::type)`，其中`cv`是的 cv-限定符`g`值和绑定参数的类型和`v1, v2, ..., vN`被确定为以下指定。 你可以使用它将参数绑定到可调用的对象，从而使可调用对象具有定制的参数列表。  
  
 第二个模板函数返回转移调用包装器 `g`，该包装器具有作为 `Ret` 的同义词的嵌套类型 `result_type`。 `g(u1, u2, ..., uM)` 产生的作用是 `INVOKE(f, v1, v2, ..., vN, Ret)`，其中 `cv` 是 `g` 的 cv 限定符，绑定参数 `v1, v2, ..., vN` 的值和类型按以下指定内容确定。 你可以使用它将参数绑定到可调用的对象，从而使可调用对象具有定制的参数列表和指定的返回类型。  
  
 绑定参数 `v1, v2, ..., vN` 及其对应类型 `V1, V2, ..., VN` 的值取决于在对调用包装器 `g` 的 `bind` 和 cv 限定符 `cv` 调用过程中的类型 `Ti` 的对应参数 `ti` 的类型，如下所示：  
  
 如果 `ti` 类型为 `reference_wrapper<T>`，则参数 `vi` 为 `ti.get()`，其类型 `Vi` 为 `T&`；  
  
 如果 `std::is_bind_expression<Ti>::value` 的值为 `true`，则参数 `vi` 为 `ti(u1, u2, ..., uM)`，其类型 `Vi` 为 `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type`；  
  
 如果 `std::is_placeholder<Ti>::value` 的值 `j` 不为零，则参数 `vi` 为 `uj`，其类型 `Vi` 为 `Uj&`；  
  
 否则参数 `vi` 为 `ti`，其类型 `Vi` 为 `Ti` `cv` `&`。  
  
 例如，给定函数 `f(int, int)` 后，表达式 `bind(f, _1, 0)` 返回转移调用包装器 `cw`，使得 `cw(x)` 调用 `f(x, 0)`。 表达式 `bind(f, 0, _1)` 返回转移调用包装器 `cw`，使得 `cw(x)` 调用 `f(0, x)`。  
  
 除 `fn` 参数之外，对 `bind` 调用过程中的参数数量必须等于可传递给可调用对象 `fn` 的参数数量。 因此，`bind(cos, 1.0)` 是正确的，`bind(cos)` 和 `bind(cos, _1, 0.0)` 都不正确。  
  
 函数调用由 `bind` 返回的调用包装器的过程中的参数数量必须至少与对 `bind` 调用过程中的所有占位符参数的 `is_placeholder<PH>::value` 的最大编号值一样大。 因此，`bind(cos, _2)(0.0, 1.0)` 是正确的（并返回 `cos(1.0)`），而 `bind(cos, _2)(0.0)` 不正确。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__bind.cpp   
// compile with: /EHsc   
#include <functional>   
#include <algorithm>   
#include <iostream>   
  
using namespace std::placeholders;   
  
void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

void product(double x, double y)
{
    std::cout << x << "*" << y << " == " << x * y << std::endl;
}

int main()
{
    double arg[] = { 1, 2, 3 };

    std::for_each(&arg[0], arg + 3, square);
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(square, _1));

    return (0);
}

```  
  
```Output  
1^2 == 1  
2^2 == 4  
3^2 == 9  
  
1*2 == 2  
2*2 == 4  
3*2 == 6  
  
1^2 == 1  
2^2 == 4  
3^2 == 9  
```  
  
##  <a name="bind1st"></a>  bind1st  
 一种帮助程序模板类，用于创建适配器，通过将二元函数的第一个自变量绑定到指定的值，将二元函数对象转换为一元函数对象。  
  
```  
template <class Operation, class Type>  
binder1st <Operation> bind1st (const Operation& func, const Type& left);
```  
  
### <a name="parameters"></a>参数  
 `func`  
 要转换为一元函数对象的二元函数对象。  
  
 `left`  
 要将二元函数对象的第一个参数绑定到的值。  
  
### <a name="return-value"></a>返回值  
 得到的二元函数对象的第一个参数绑定到值的一元函数对象`left`。  
  
### <a name="remarks"></a>备注  
 函数绑定器是一种函数适配器，可返回函数对象，因而可在某些类型的函数组合中用于构造更复杂和功能更强大的表达式。  
  
 如果 `func` 是 `Operation` 类型的对象且 `c` 是常量，则 `bind1st` ( `func`, `c`) 等效于 [binder1st](../standard-library/binder1st-class.md) 类构造函数 `binder1st`< `Operation`> ( `func`, `c`) 且更具便捷性。  
  
### <a name="example"></a>示例  
  
```cpp  
// functional_bind1st.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
// Creation of a user-defined function object  
// that inherits from the unary_function base class  
class greaterthan5: unary_function<int, bool>  
{  
public:  
    result_type operator()(argument_type i)  
    {  
        return (result_type)(i > 5);  
    }  
};  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 5; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( " ;  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    // Count the number of integers > 10 in the vector  
    vector<int>::iterator::difference_type result1a;  
    result1a = count_if(v1.begin(), v1.end(), bind1st(less<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1a << "." << endl;  
  
    // Compare: counting the number of integers > 5 in the vector  
    // with a user defined function object  
    vector<int>::iterator::difference_type result1b;  
    result1b = count_if(v1.begin(), v1.end(), greaterthan5());  
    cout << "The number of elements in v1 greater than 5 is: "  
         << result1b << "." << endl;  
  
    // Count the number of integers < 10 in the vector  
    vector<int>::iterator::difference_type result2;  
    result2 = count_if(v1.begin(), v1.end(), bind2nd(less<int>(), 10));  
    cout << "The number of elements in v1 less than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
```Output  
The vector v1 = ( 0 5 10 15 20 25 )  
The number of elements in v1 greater than 10 is: 3.  
The number of elements in v1 greater than 5 is: 4.  
The number of elements in v1 less than 10 is: 2.  
```  
  
##  <a name="bind2nd"></a>  bind2nd  
 一种帮助程序模板类，用于创建适配器，通过将二元函数的第二个自变量绑定到指定的值，将二元函数对象转换为一元函数对象。  
  
```  
template <class Operation, class Type>  
binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```  
  
### <a name="parameters"></a>参数  
 `func`  
 要转换为一元函数对象的二元函数对象。  
  
 `right`  
 要将二元函数对象的第二个参数绑定到的值。  
  
### <a name="return-value"></a>返回值  
 得到的二元函数对象的第二个参数绑定到值的一元函数对象`right`。  
  
### <a name="remarks"></a>备注  
 函数绑定器是一种函数适配器，可返回函数对象，因而可在某些类型的函数组合中用于构造更复杂和功能更强大的表达式。  
  
 如果 `func` 是 **Operation** 类型的对象且 `c` 是常量，则 `bind2nd` ( `func`, `c` ) 等效于 [binder2nd](../standard-library/binder2nd-class.md) 类构造函数 **binder2nd\<Operation>** ( `func`, `c` ) 且更具便捷性。  
  
### <a name="example"></a>示例  
  
```cpp  
// functional_bind2nd.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
// Creation of a user-defined function object  
// that inherits from the unary_function base class  
class greaterthan15: unary_function<int, bool>  
{  
public:  
    result_type operator()(argument_type i)  
    {  
        return (result_type)(i > 15);  
    }  
};  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 5; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    // Count the number of integers > 10 in the vector  
    vector<int>::iterator::difference_type result1a;  
    result1a = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1a << "." << endl;  
  
    // Compare counting the number of integers > 15 in the vector  
    // with a user-defined function object  
    vector<int>::iterator::difference_type result1b;  
    result1b = count_if(v1.begin(), v1.end(), greaterthan15());  
    cout << "The number of elements in v1 greater than 15 is: "  
         << result1b << "." << endl;  
  
    // Count the number of integers < 10 in the vector  
    vector<int>::iterator::difference_type result2;  
    result2 = count_if(v1.begin(), v1.end(), bind1st(greater<int>(), 10));  
    cout << "The number of elements in v1 less than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
```Output  
The vector v1 = ( 0 5 10 15 20 25 )  
The number of elements in v1 greater than 10 is: 3.  
The number of elements in v1 greater than 15 is: 2.  
The number of elements in v1 less than 10 is: 2.  
```  
  
##  <a name="bit_and"></a>  bit_and  
 对其参数执行按位 AND 运算（二元 `operator&`）的预定义函数对象。  
  
```  
template <class Type = void>  
struct bit_and : public binary_function<Type, Type, Type> {  
    Type operator()(
    const Type& Left,   
    const Type& Right) const; 
 };  
 
// specialized transparent functor for operator& 
template <>
struct bit_and<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const  ->
        decltype(std::forward<T>(Left) & std::forward<U>(Right));
};
```  
  
### <a name="parameters"></a>参数  
 `Type`, `T`, `U`  
 支持 `operator&` 接受指定或推断类型的操作数的任何类型。  
  
 `Left`  
 按位 AND 运算的左操作数。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `T` 的左值和右值引用参数。  
  
 `Right`  
 按位 AND 运算的右操作数。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `U` 的左值和右值引用参数。  
  
### <a name="return-value"></a>返回值  
 `Left & Right` 的结果。 专专用化模板可完美转移结果，该结果具有由 `operator&` 返回的类型。  
  
### <a name="remarks"></a>备注  
 `bit_and` 函子被限制为基本数据类型的整型类型，或限制为实现二元 `operator&` 的用户定义的类型。  
  
##  <a name="bit_not"></a>  bit_not  
 对其参数执行按位求补 (NOT) 运算（一元 `operator~`）的预定义函数对象。  
  
```  
template <class Type = void>  
struct bit_not : public unary_function<Type, Type>   
 {  
    Type operator()(const Type& Right) const; 
 };  
 
// specialized transparent functor for operator~  
template <>  
struct bit_not<void>   
 {  
    template <class Type>  
    auto operator()(Type&& Right) const  ->  decltype(~std::forward<Type>(Right));
 };  
```  
  
### <a name="parameters"></a>参数  
 `Type`  
 支持一元 `operator~` 的类型。  
  
 `Right`  
 按位求补运算的操作数。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `Type` 的左值或右值引用参数。  
  
### <a name="return-value"></a>返回值  
 `~ Right` 的结果。 专专用化模板可完美转移结果，该结果具有由 `operator~` 返回的类型。  
  
### <a name="remarks"></a>备注  
 `bit_not` 函子被限制为基本数据类型的整型类型，或限制为实现二元 `operator~` 的用户定义的类型。  
  
##  <a name="bit_or"></a>  bit_or  
 对其参数执行按位 OR 运算 (`operator|`) 的预定义函数对象。  
  
```  
template <class Type = void>  
struct bit_or : public binary_function<Type, Type, Type> {  
    Type operator()(
    const Type& Left,   
    const Type& Right) const; 
 };  
 
// specialized transparent functor for operator|  
template <>
struct bit_or<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        ->  decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```  
  
### <a name="parameters"></a>参数  
 `Type`, `T`, `U`  
 支持 `operator|` 接受指定或推断类型的操作数的任何类型。  
  
 `Left`  
 按位或运算的左操作数。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `T` 的左值和右值引用参数。  
  
 `Right`  
 按位或运算的右操作数。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `U` 的左值和右值引用参数。  
  
### <a name="return-value"></a>返回值  
 `Left | Right` 的结果。 专专用化模板可完美转移结果，该结果具有由 `operator|` 返回的类型。  
  
### <a name="remarks"></a>备注  
 `bit_or` 函子被限制为基本数据类型的整型类型，或限制为实现 `operator|` 的用户定义的类型。  
  
##  <a name="bit_xor"></a>  bit_xor  
 对其参数执行按位 XOR 运算（二元 `operator^`）的预定义函数对象。  
  
```  
template <class Type = void>  
struct bit_xor : public binary_function<Type, Type, Type> {  
    Type operator()(
    const Type& Left,   
    const Type& Right) const; 
 };  
 
// specialized transparent functor for operator^  
template <>
struct bit_xor<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) ^ std::forward<U>(Right));
};
```  
  
### <a name="parameters"></a>参数  
 `Type`, `T`, `U`  
 支持 `operator^` 接受指定或推断类型的操作数的任何类型。  
  
 `Left`  
 按位 XOR 运算的左操作数。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `T` 的左值和右值引用参数。  
  
 `Right`  
 按位 XOR 运算的右操作数。 未专用化的模板采用 `Type` 类型的左值引用参数。 专用化的模板可完美转移推断类型 `U` 的左值和右值引用参数。  
  
### <a name="return-value"></a>返回值  
 `Left ^ Right` 的结果。 专专用化模板可完美转移结果，该结果具有由 `operator^` 返回的类型。  
  
### <a name="remarks"></a>备注  
 `bit_xor` 函子被限制为基本数据类型的整型类型，或限制为实现二元 `operator^` 的用户定义的类型。  
  
##  <a name="cref"></a>  cref  
 从变量构造常量 `reference_wrapper`。  
  
```  
template <class Ty>  
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>  
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```  
  
### <a name="parameters"></a>参数  
 `Ty`  
 要包装的参数的类型。  
  
 `arg`  
 要包装的参数。  
  
### <a name="remarks"></a>备注  
 第一个函数返回 `reference_wrapper<const Ty>(arg.get())`。 可以使用它来包装常量引用。 第二个函数返回 `reference_wrapper<const Ty>(arg)`。 可以使用它将包装的引用重新包装为常量引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__cref.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val)   
    {   
    return (-val);   
    }   
  
int main()   
    {   
    int i = 1;   
  
    std::cout << "i = " << i << std::endl;   
    std::cout << "cref(i) = " << std::cref(i) << std::endl;   
    std::cout << "cref(neg)(i) = "   
        << std::cref(&neg)(i) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
i = 1  
cref(i) = 1  
cref(neg)(i) = -1  
```  
  
##  <a name="mem_fn"></a>  mem_fn  
 生成一个简单的调用包装器。  
  
```  
template <class Ret, class Ty>  
unspecified mem_fn(Ret Ty::*pm);
```  
  
### <a name="parameters"></a>参数  
 `Ret`  
 包装函数的返回类型。  
  
 `Ty`  
 成员函数指针的类型。  
  
### <a name="remarks"></a>备注  
 模板函数返回一个简单的调用包装器 `cw`，具有弱结果类型，使得表达式 `cw(t, a2, ..., aN)` 等效于 `INVOKE(pm, t, a2, ..., aN)`。 该包装器不会引发任何异常。  
  
 仅当类型 `Ty` 是指向具有不带参数的 cv 限定符 `cv` 的成员函数的指针时，返回的调用包装器从 `std::unary_function<cv Ty*, Ret>` 派生（因此将嵌套类型 `result_type` 定义为`Ret` 的同义词，将嵌套类型 `argument_type` 定义为 `cv Ty*` 的同义词）。  
  
 仅当类型 `Ty` 是指向具有带有一个 `T2` 类型参数的 cv 限定符 `cv` 的成员函数的指针时，返回的调用包装器从 `std::binary_function<cv Ty*, T2, Ret>` 派生（因此将嵌套类型 `result_type` 定义为 `Ret` 的同义词，将嵌套类型 `first argument_type` 定义为 `cv Ty*` 的同义词，将嵌套类型 `second argument_type` 定义为 `T2` 的同义词）。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__mem_fn.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
class Funs   
    {   
public:   
    void square(double x)   
        {   
        std::cout << x << "^2 == " << x * x << std::endl;   
        }   
  
    void product(double x, double y)   
        {   
        std::cout << x << "*" << y << " == " << x * y << std::endl;   
        }   
    };   
  
int main()   
    {   
    Funs funs;   
  
    std::mem_fn(&Funs::square)(funs, 3.0);   
    std::mem_fn(&Funs::product)(funs, 3.0, 2.0);   
  
    return (0);   
    }  
  
```  
  
```Output  
3^2 == 9  
3*2 == 6  
```  
  
##  <a name="mem_fun"></a>  mem_fun  
 帮助程序模板函数，在使用指针自变量进行初始化的情况下，用来构造成员函数的函数对象适配器。  
  
```  
template <class Result, class Type>  
mem_fun_t<Result, Type> mem_fun (Result(Type::* pmem)());

template <class Result, class Type, class Arg>  
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pmem)(Arg));

template <class Result, class Type>  
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pmem)() const);

template <class Result, class Type, class Arg>  
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pmem)(Arg) const);
```  
  
### <a name="parameters"></a>参数  
 `pmem`  
 一个指针，指向要转换为函数对象的 **Type** 类成员函数。  
  
### <a name="return-value"></a>返回值  
 类型 `mem_fun_t` 或 `mem_fun1_t` 的 **const** 或 **non_const** 函数对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// functional_mem_fun.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
class StoreVals     
{  
    int val;  
public:  
    StoreVals() { val = 0; }  
    StoreVals(int j) { val = j; }  
  
    bool display() { cout << val << " "; return true; }  
    int squareval() { val *= val; return val; }  
    int lessconst(int k) {val -= k; return val; }  
};  
  
int main( )  
{  
    vector<StoreVals *> v1;  
  
    StoreVals sv1(5);  
    v1.push_back(&sv1);  
    StoreVals sv2(10);  
    v1.push_back(&sv2);  
    StoreVals sv3(15);  
    v1.push_back(&sv3);  
    StoreVals sv4(20);  
    v1.push_back(&sv4);  
    StoreVals sv5(25);  
    v1.push_back(&sv5);  
  
    cout << "The original values stored are: " ;  
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));  
    cout << endl;  
  
    // Use of mem_fun calling member function through a pointer  
    // square each value in the vector using squareval ()  
    for_each(v1.begin(), v1.end(), mem_fun<int, StoreVals>(&StoreVals::squareval));     
    cout << "The squared values are: " ;  
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));  
    cout << endl;  
  
    // Use of mem_fun1 calling member function through a pointer  
    // subtract 5 from each value in the vector using lessconst ()  
    for_each(v1.begin(), v1.end(),   
        bind2nd (mem_fun1<int, StoreVals,int>(&StoreVals::lessconst), 5));     
    cout << "The squared values less 5 are: " ;  
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));  
    cout << endl;  
}  
```  
  
##  <a name="mem_fun_ref"></a>  mem_fun_ref  
 帮助程序模板函数，在使用引用参数进行初始化的情况下，用来构造成员函数的函数对象适配器。  
  
```  
template <class Result, class Type>  
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pmem)());

template <class Result, class Type, class Arg>  
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pmem)(Arg));

template <class Result, class Type>  
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pmem)() const);

template <class Result, class Type, class Arg>  
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pmem)(Arg) const);
```  
  
### <a name="parameters"></a>参数  
 `pmem`  
 一个指针，指向要转换为函数对象的 `Type` 类成员函数。  
  
### <a name="return-value"></a>返回值  
 类型 `mem_fun_ref_t` 或 `mem_fun1_ref_t` 的 `const` 或 `non_const` 函数对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// functional_mem_fun_ref.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
class NumVals  
   {  
   int val;  
   public:  
   NumVals ( ) { val = 0; }  
   NumVals ( int j ) { val = j; }  
  
   bool display ( ) { cout << val << " "; return true; }  
   bool isEven ( ) { return ( bool )  !( val %2 ); }  
   bool isPrime( )  
   {  
      if (val < 2) { return true; }  
      for (int i = 2; i <= val / i; ++i)  
      {  
         if (val % i == 0) { return false; }  
      }  
      return true;  
   }  
};  
  
int main( )  
{  
   vector <NumVals> v1 ( 13 ), v2 ( 13 );  
   vector <NumVals>::iterator v1_Iter, v2_Iter;  
   int i, k;  
  
   for ( i = 0; i < 13; i++ ) v1 [ i ] = NumVals ( i+1 );  
   for ( k = 0; k < 13; k++ ) v2 [ k ] = NumVals ( k+1 );  
  
   cout << "The original values stored in v1 are: " ;  
   for_each( v1.begin( ), v1.end( ),   
   mem_fun_ref ( &NumVals::display ) );  
   cout << endl;  
  
   // Use of mem_fun_ref calling member function through a reference  
   // remove the primes in the vector using isPrime ( )  
   v1_Iter = remove_if ( v1.begin( ),  v1.end( ),   
      mem_fun_ref ( &NumVals::isPrime ) );     
   cout << "With the primes removed, the remaining values in v1 are: " ;  
   for_each( v1.begin( ), v1_Iter,   
   mem_fun_ref ( &NumVals::display ) );  
   cout << endl;  
  
   cout << "The original values stored in v2 are: " ;  
   for_each( v2.begin( ), v2.end( ),   
   mem_fun_ref ( &NumVals::display ) );  
   cout << endl;  
  
   // Use of mem_fun_ref calling member function through a reference  
   // remove the even numbers in the vector v2 using isEven ( )  
   v2_Iter = remove_if ( v2.begin( ),  v2.end( ),   
      mem_fun_ref ( &NumVals::isEven ) );     
   cout << "With the even numbers removed, the remaining values are: " ;  
   for_each( v2.begin( ),  v2_Iter,   
   mem_fun_ref ( &NumVals::display ) );  
   cout << endl;  
}  
```  
  
```Output  
The original values stored in v1 are: 1 2 3 4 5 6 7 8 9 10 11 12 13   
With the primes removed, the remaining values in v1 are: 4 6 8 9 10 12   
The original values stored in v2 are: 1 2 3 4 5 6 7 8 9 10 11 12 13   
With the even numbers removed, the remaining values are: 1 3 5 7 9 11 13   
```  
  
##  <a name="not1"></a>  not1  
 返回一元谓词的补集。  
  
```  
template <class UnaryPredicate>  
unary_negate<UnaryPredicate> not1(const UnaryPredicate& pred);
```  
  
### <a name="parameters"></a>参数  
 `pred`  
 要求反的一元谓词。  
  
### <a name="return-value"></a>返回值  
 已修改的一元谓词的求反的一元谓词。  
  
### <a name="remarks"></a>备注  
 如果 `unary_negate` 从一元谓词 **Pred**( *x*) 进行构造，则它返回 **!Pred**( *x*)。  
  
### <a name="example"></a>示例  
  
```cpp  
// functional_not1.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 7; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    vector<int>::iterator::difference_type result1;  
    // Count the elements greater than 10  
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
  
    vector<int>::iterator::difference_type result2;  
    // Use the negator to count the elements less than or equal to 10  
    result2 = count_if(v1.begin(), v1.end(),  
        not1(bind2nd(greater<int>(), 10)));  
  
    cout << "The number of elements in v1 not greater than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
```Output  
The vector v1 = ( 0 5 10 15 20 25 30 35 )  
The number of elements in v1 greater than 10 is: 5.  
The number of elements in v1 not greater than 10 is: 3.  
```  
  
##  <a name="not2"></a>  not2  
 返回二元谓词的补集。  
  
```  
template <class BinaryPredicate>  
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```  
  
### <a name="parameters"></a>参数  
 `func`  
 要进行求反的二元谓词。  
  
### <a name="return-value"></a>返回值  
 已修改的二元谓词的求反的二元谓词。  
  
### <a name="remarks"></a>备注  
 如果 `binary_negate` 从二元谓词 **BinPred**( *x*, *y*) 进行构造，则它返回 ! **BinPred**( *x*, *y*).  
  
### <a name="example"></a>示例  
  
```cpp  
// functional_not2.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <cstdlib>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   v1.push_back( 6262 );  
   v1.push_back( 6262 );  
   for ( i = 0 ; i < 5 ; i++ )  
   {  
      v1.push_back( rand( ) );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   // use default binary predicate less<int>( )  
   sort( v1.begin( ), v1.end( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order,   
   // use the binary_negate helper function not2  
   sort( v1.begin( ), v1.end( ), not2(less<int>( ) ) );  
   cout << "Resorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Original vector v1 = ( 6262 6262 41 18467 6334 26500 19169 )  
Sorted vector v1 = ( 41 6262 6262 6334 18467 19169 26500 )  
Resorted vector v1 = ( 26500 19169 18467 6334 6262 6262 41 )  
```  
  
##  <a name="ptr_fun"></a>  ptr_fun  
 帮助程序模板函数，用于将一元和二元函数指针分别转换为一元和二元自适应函数。  
  
```  
template <class Arg, class Result>  
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>  
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```  
  
### <a name="parameters"></a>参数  
 `pfunc`  
 要转换为自适应函数的一元或二元函数指针。  
  
### <a name="return-value"></a>返回值  
 第一个模板函数返回一元函数 [pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md) < `Arg`, **Result**>(* `pfunc`)。  
  
 第二个模板函数返回二元函数 [pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md) \< **Arg1**, **Arg2**, **Result**>(* `pfunc`)。  
  
### <a name="remarks"></a>备注  
 函数指针是一个函数对象，且可能会被传递到期望将函数作为参数的任何 C++ 标准库算法，但它不可调适。 若要将其与适配器配合使用（如向其绑定值或与求反器配合使用），则必须将其与可促成这种调适的嵌套类型一起提供。 通过 `ptr_fun` 帮助程序函数转换一元和二元函数指针可允许函数适配器使用一元和二元函数指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]  
  
##  <a name="ref"></a>  ref  
 从变量构造常量 `reference_wrapper` 。  
  
```  
template <class Ty>  
reference_wrapper<Ty> ref(Ty& arg);

template <class Ty>  
reference_wrapper<Ty> ref(reference_wrapper<Ty>& arg);
```  
  
### <a name="return-value"></a>返回值  
 对 `arg`的引用；具体而言，是指对 `reference_wrapper<Ty>(arg)`的引用。  
  
### <a name="example"></a>示例  
  下面的示例定义了两个函数：一个绑定到字符串变量，另一个绑定到通过调用 `ref`计算的字符串变量的引用。 当变量的值发生更改时，第一个函数将继续使用旧值，而第二个函数将使用新值。  
  
```cpp  
#include <algorithm>  
#include <functional>  
#include <iostream>  
#include <iterator>  
#include <ostream>  
#include <string>  
#include <vector>  
using namespace std;  
using namespace std;  
using namespace std::placeholders;  
  
bool shorter_than(const string& l, const string& r) {  
    return l.size() < r.size();  
}  
  
int main() {  
    vector<string> v_original;  
    v_original.push_back("tiger");  
    v_original.push_back("cat");  
    v_original.push_back("lion");  
    v_original.push_back("cougar");  
  
    copy(v_original.begin(), v_original.end(), ostream_iterator<string>(cout, " "));  
    cout << endl;  
  
    string s("meow");  
  
    function<bool (const string&)> f = bind(shorter_than, _1, s);  
    function<bool (const string&)> f_ref = bind(shorter_than, _1, ref(s));  
  
    vector<string> v;  
  
    // Remove elements that are shorter than s ("meow")  
  
    v = v_original;  
    v.erase(remove_if(v.begin(), v.end(), f), v.end());  
  
    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));  
    cout << endl;  
  
    // Now change the value of s.  
    // f_ref, which is bound to ref(s), will use the  
    // new value, while f is still bound to the old value.  
  
    s = "kitty";  
  
    // Remove elements that are shorter than "meow" (f is bound to old value of s)  
  
    v = v_original;  
    v.erase(remove_if(v.begin(), v.end(), f), v.end());  
  
    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));  
    cout << endl;  
  
    // Remove elements that are shorter than "kitty" (f_ref is bound to ref(s))  
  
    v = v_original;  
    v.erase(remove_if(v.begin(), v.end(), f_ref), v.end());  
  
    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));  
    cout << endl;  
}  
```  
  
```Output  
tiger cat lion cougar  
tiger lion cougar  
tiger lion cougar  
tiger cougar  
```  
  
##  <a name="swap"></a>  swap  
 交换两个 `function` 对象。  
  
```  
template <class Fty>  
void swap(function<Fty>& f1, function<Fty>& f2);
```  
  
### <a name="parameters"></a>参数  
 `Fty`  
 由函数对象控制的类型。  
  
 `f1`  
 第一个函数对象。  
  
 `f2`  
 第二个函数对象。  
  
### <a name="remarks"></a>备注  
 该函数返回 `f1.swap(f2)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__swap.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val)   
    {   
    return (-val);   
    }   
  
int main()   
    {   
    std::function<int (int)> fn0(neg);   
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;   
    std::cout << "val == " << fn0(3) << std::endl;   
  
    std::function<int (int)> fn1;   
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;   
    std::cout << std::endl;   
  
    swap(fn0, fn1);   
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;   
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;   
    std::cout << "val == " << fn1(3) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
empty == false  
val == -3  
empty == true  
  
empty == true  
empty == false  
val == -3  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<functional>](../standard-library/functional.md)

