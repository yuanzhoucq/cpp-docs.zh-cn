---
title: "function 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- function
- functional/std::function
- functional/std::function::result_type
- functional/std::function::assign
- functional/std::function::swap
- functional/std::function::target
- functional/std::function::target_type
- functional/std::function::operator unspecified
- functional/std::function::operator()
dev_langs:
- C++
helpviewer_keywords:
- function class
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
caps.latest.revision: 26
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
ms.openlocfilehash: 0c79b2b4d1ac2e9df7f38708ff232d70392cce15
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="function-class"></a>function 类
可调用对象的包装器。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <class Fty>
class function  // Fty of type Ret(T1, T2, ..., TN)  
    : public unary_function<T1, Ret>       // when Fty is Ret(T1)  
    : public binary_function<T1, T2, Ret>  // when Fty is Ret(T1, T2)  
{
public:
    typedef Ret result_type;

    function();
    function(nullptr_t);
    function(const function& right);
    template <class Fty2>
        function(Fty2 fn);
    template <class Fty2, class Alloc>
        function(reference_wrapper<Fty2>, const Alloc& Ax);

    template <class Fty2, class Alloc>
        void assign(Fty2, const Alloc& Ax);
    template <class Fty2, class Alloc>
        void assign(reference_wrapper<Fty2>, const Alloc& Ax);
    function& operator=(nullptr_t);
    function& operator=(const function&);
    template <class Fty2>
        function& operator=(Fty2);
    template <class Fty2>
        function& operator=(reference_wrapper<Fty2>);

    void swap(function&);
    explicit operator bool() const;

    result_type operator()(T1, T2, ....., TN) const;
    const std::type_info& target_type() const;
    template <class Fty2>
        Fty2 *target();

    template <class Fty2>
        const Fty2 *target() const;

    template <class Fty2>
        void operator==(const Fty2&) const = delete;
    template <class Fty2>
        void operator!=(const Fty2&) const = delete;
};
```  
  
### <a name="parameters"></a>参数  
 `Fty`  
 要包装的函数类型。  
  
 `Ax`  
 allocator 函数。  
  
## <a name="remarks"></a>备注  
 模板类是调用签名为 `Ret(T1, T2, ..., TN)` 的调用包装器。 你可以使用它在统一包装器中包含各种可调用对象。  
  
 一些成员函数接受命名所需目标对象的操作数。 你可以通过几种方式指定此类操作数：  
  
 `fn` -- 可调用对象`fn`；调用后，`function` 对象保存 `fn` 的副本  
  
 `fnref` -- 由 `fnref.get()` 命名的可调用对象名称；调用后，`function`对象保留对 `fnref.get()` 的引用  
  
 `right` -- 可调用对象（如有），由 `function` 对象 `right` 保留  
  
 `npc` -- 空指针；调用后，`function` 对象为空  
  
 在所有情况下，`INVOKE(f, t1, t2, ..., tN)`其中 `f` 是可调用对象，`t1, t2, ..., tN` 分别是类型 `T1, T2, ..., TN` 的左值，必须格式标准，并且如果 `Ret` 有效，则可转换为 `Ret`。  
  
 空 `function` 对象不包含可调用对象或对可调用对象的引用。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[函数](#function)|构造一个包装器，该包装器或者为空，或者存储具有固定签名的任意类型的可调用对象。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[result_type](#result_type)|存储的可调对象的返回类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[assign](#assign)|将可调用对象分配给此函数对象。|  
|[swap](#swap)|交换两个可调用对象。|  
|[目标](#target)|测试存储的可调用对象是否可按指定方式调用。|  
|[target_type](#target_type)|获取有关可调用对象的类型信息。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[function::operator 未指定](#op_unspecified)|测试存储的可调用对象是否存在。|  
|[function::operator()](#op_call)|调用可调用的对象。|  
|[function::operator=](#op_eq)|替换存储的可调用对象。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<functional>  
  
 **命名空间：** std  
  
##  <a name="assign"></a>  function::assign  
 将可调用对象分配给此函数对象。  
  
```  
template <class Fx, class Alloc>  
    void assign(
        Fx _Func,   
        const Alloc& Ax);

template <class Fx, class Alloc>  
    void assign(
        reference_wrapper<Fx> _Fnref,   
        const Alloc& Ax);
```  
  
### <a name="parameters"></a>参数  
 `_Func`  
 可调用的对象。  
  
 `_Fnref`  
 包含可调用对象的引用包装器。  
  
 `Ax`  
 分配器对象。  
  
### <a name="remarks"></a>备注  
 每个成员函数使用作为 `operand` 传递的可调用对象替换由 `*this` 保留的`callable object`。 两者都使用分配器对象 `Ax` 分配存储。  
  
##  <a name="function"></a>  function::function  
 构造一个包装器，该包装器或者为空，或者存储具有固定签名的任意类型的可调用对象。  
  
```  
function();
function(nullptr_t npc);
function(const function& right);
template <class Fx>  
    function(Fx _Func);
template <class Fx>  
    function(reference_wrapper<Fx> _Fnref);
template <class Fx, class Alloc>  
    function(
        Fx _Func,   
        const Alloc& Ax);

template <class Fx, class Alloc>  
    function(
        reference_wrapper<Fx> _Fnref,   
        const Alloc& Ax);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 要复制的函数对象。  
  
 `Fx`  
 可调用对象的类型。  
  
 `_Func`  
 要包装的可调用对象。  
  
 `Alloc`  
 分配器类型。  
  
 `Ax`  
 分配器。  
  
 `_Fnref`  
 要包装的可调用对象引用。  
  
### <a name="remarks"></a>备注  
 前两个构造函数构造一个空 `function` 对象。 接下来的三个构造函数构造一个 `function` 对象，它保存作为操作数传递的可调用对象。 最后两个构造函数使用分配器对象 Ax 分配存储。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__function_function.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
#include <vector>  
  
int square(int val)  
{  
    return val * val;  
}  
  
class multiply_by  
{  
public:  
    explicit multiply_by(const int n) : m_n(n) { }  
  
    int operator()(const int x) const  
    {  
        return m_n * x;  
    }  
  
private:  
    int m_n;  
};  
  
int main()   
{   
  
    typedef std::vector< std::function<int (int)> > vf_t;  
  
    vf_t v;  
    v.push_back(square);  
    v.push_back(std::negate<int>());  
    v.push_back(multiply_by(3));  
  
    for (vf_t::const_iterator i = v.begin(); i != v.end(); ++i)  
    {  
        std::cout << (*i)(10) << std::endl;  
    }  
  
    std::function<int (int)> f = v[0];  
    std::function<int (int)> g;  
  
    if (f) {  
        std::cout << "f is non-empty (correct)." << std::endl;  
    } else {  
        std::cout << "f is empty (can't happen)." << std::endl;  
    }  
  
    if (g) {  
        std::cout << "g is non-empty (can't happen)." << std::endl;  
    } else {  
        std::cout << "g is empty (correct)." << std::endl;  
    }  
  
    return 0;   
}  
```  
  
```Output  
100  
-10  
30  
f is non-empty (correct).  
g is empty (correct).  
```  
  
##  <a name="op_unspecified"></a>  function::operator 未指定  
 测试存储的可调用对象是否存在。  
  
```  
operator unspecified();
```   
  
### <a name="remarks"></a>备注  
 仅当对象不为空时，运算符才返回一个可转换为 `bool` 的值，且该值为 true。 可将它用于测试对象是否为空。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__function_operator_bool.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val)   
    {   
    return (-val);   
    }   
  
int main()   
    {   
    std::function<int (int)> fn0;   
    std::cout << std::boolalpha << "not empty == " << (bool)fn0 << std::endl;   
  
    std::function<int (int)> fn1(neg);   
    std::cout << std::boolalpha << "not empty == " << (bool)fn1 << std::endl;   
  
    return (0);   
    }    
```  
  
```Output  
not empty == false  
not empty == true  
```  
  
##  <a name="op_call"></a>  function::operator()  
 调用可调用的对象。  
  
```  
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```  
  
### <a name="parameters"></a>参数  
 `TN`  
 第 N 个调用参数的类型。  
  
 `tN`  
 第 N 个调用参数。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 `INVOKE(fn, t1, t2, ..., tN, Ret)`，其中 `fn` 是存储于 `*this` 中的目标对象。 可以使用它来调用包装的可调用对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__function_operator_call.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val)   
    {   
    return (-val);   
    }   
  
int main()   
    {   
    std::function<int (int)> fn1(neg);   
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;   
    std::cout << "val == " << fn1(3) << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
empty == false  
val == -3  
```  
  
##  <a name="op_eq"></a>  function::operator=  
 替换存储的可调用对象。  
  
```  
function& operator=(null_ptr_type npc);
function& operator=(const function& right);
template <class Fty>  
    function& operator=(Fty fn);
template <class Fty>  
    function& operator=(reference_wrapper<Fty> fnref);
```  
  
### <a name="parameters"></a>参数  
 `npc`  
 空指针常量。  
  
 `right`  
 要复制的函数对象。  
  
 `fn`  
 要包装的可调用对象。  
  
 `fnref`  
 要包装的可调用对象引用。  
  
### <a name="remarks"></a>备注  
 每个运算符使用作为操作数传递的可调用对象替换由 `*this` 保留的可调用对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__function_operator_as.cpp   
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
    fn1 = 0;   
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;   
  
    fn1 = neg;   
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;   
    std::cout << "val == " << fn1(3) << std::endl;   
  
    fn1 = fn0;   
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;   
    std::cout << "val == " << fn1(3) << std::endl;   
  
    fn1 = std::cref(fn1);   
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;   
    std::cout << "val == " << fn1(3) << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
empty == false  
val == -3  
empty == true  
empty == false  
val == -3  
empty == false  
val == -3  
empty == false  
val == -3  
```  
  
##  <a name="result_type"></a>  function::result_type  
 存储的可调对象的返回类型。  
  
```  
typedef Ret result_type;  
```  
  
### <a name="remarks"></a>备注  
 typedef 是模板调用签名内类型 `Ret` 的同义词。 你可以使用它来确定包装的可调用对象的返回类型。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__function_result_type.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val)   
    {   
    return (-val);   
    }   
  
int main()   
    {   
    std::function<int (int)> fn1(neg);   
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;   
  
    std::function<int (int)>::result_type val = fn1(3);   
    std::cout << "val == " << val << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
empty == false  
val == -3  
```  
  
##  <a name="swap"></a>  function::swap  
 交换两个可调用对象。  
  
```  
void swap(function& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 要进行交换的函数对象。  
  
### <a name="remarks"></a>备注  
 成员函数在 `*this` 和 `right` 之间交换目标对象。 它定时执行此操作且不引发异常。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__function_swap.cpp   
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
  
    fn0.swap(fn1);   
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
  
##  <a name="target"></a>  function::target  
 测试存储的可调用对象是否可按指定方式调用。  
  
```  
template <class Fty2>  
    Fty2 *target();
template <class Fty2>  
    const Fty2 *target() const;
```  
  
### <a name="parameters"></a>参数  
 `Fty2`  
 要测试的目标可调用对象类型。  
  
### <a name="remarks"></a>备注  
 类型 `Fty2` 必须对参数类型 `T1, T2, ..., TN` 和返回类型 `Ret` 可调用。 如果 `target_type() == typeid(Fty2)`，则成员模板函数返回目标对象的地址；否则返回 0。  
  
 对于类型 `Fty2, T1, T2, ..., TN` 的各自的左值 `fn, t1, t2, ..., tN`，如果 `INVOKE(fn, t1, t2, ..., tN)` 格式标准，并且如果 `Ret` 并非 `void` 且可转换为 `Ret`，则类型 `Fty2` 对于参数类型 `T1, T2, ..., TN` 和返回类型 `Ret` 可调用。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__function_target.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val)   
    {   
    return (-val);   
    }   
  
int main()   
    {   
    typedef int (*Myfun)(int);   
    std::function<int (int)> fn0(neg);   
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;   
    std::cout << "no target == " << (fn0.target<Myfun>() == 0) << std::endl;   
  
    Myfun *fptr = fn0.target<Myfun>();   
    std::cout << "val == " << (*fptr)(3) << std::endl;   
  
    std::function<int (int)> fn1;   
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;   
    std::cout << "no target == " << (fn1.target<Myfun>() == 0) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
empty == false  
no target == false  
val == -3  
empty == true  
no target == true  
```  
  
##  <a name="target_type"></a>  function::target_type  
 获取有关可调用对象的类型信息。  
  
```  
const std::type_info& target_type() const;
```  
  
### <a name="remarks"></a>备注  
 如果 `*this` 为空，则成员函数将返回 `typeid(void)`；否则它将返回 `typeid(T)`，其中 `T` 是目标对象的类型。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__function_target_type.cpp   
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
    std::cout << "type == " << fn0.target_type().name() << std::endl;   
  
    std::function<int (int)> fn1;   
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;   
    std::cout << "type == " << fn1.target_type().name() << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
empty == false  
type == int (__cdecl*)(int)  
empty == true  
type == void  
```  
  
## <a name="see-also"></a>另请参阅  
 [mem_fn](../standard-library/functional-functions.md#mem_fn)   
 [reference_wrapper 类](../standard-library/reference-wrapper-class.md)

