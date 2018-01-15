---
title: "shared_ptr 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::shared_ptr
- memory/std::shared_ptr::element_type
- memory/std::shared_ptr::get
- memory/std::shared_ptr::owner_before
- memory/std::shared_ptr::reset
- memory/std::shared_ptr::swap
- memory/std::shared_ptr::unique
- memory/std::shared_ptr::use_count
- memory/std::shared_ptr::operator boolean-type
- memory/std::shared_ptr::operator*
- memory/std::shared_ptr::operator=
- memory/std::shared_ptr::operator->
dev_langs: C++
helpviewer_keywords:
- std::shared_ptr [C++]
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
ms.assetid: 1469fc51-c658-43f1-886c-f4530dd84860
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03876821780ec2f4e2258b9553e936bfdda13c17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="sharedptr-class"></a>shared_ptr 类
将引用计数智能指针回绕在动态分配的对象周围。  
  
## <a name="syntax"></a>语法  
```
template <class T>
class shared_ptr; 
```  
  
## <a name="remarks"></a>备注  
 shared_ptr 类描述使用引用计数来管理资源的对象。 `shared_ptr` 对象有效保留一个指向其拥有的资源的指针或保留一个 null 指针。 资源可由多个 `shared_ptr` 对象拥有；当拥有特定资源的最后一个 `shared_ptr` 对象被销毁后，资源将释放。  
  
 在重新分配或重置资源后，`shared_ptr` 将停止拥有该资源。  
  
 模板参数 `T` 可能是一个不完整的类型，针对某些成员函数的情况除外。  
  
 当从类型 `shared_ptr<T>` 的资源指针或 `G*` 中构造 `shared_ptr<G>` 对象时，指针类型 `G*` 必须可转换为 `T*`。 如果不是这样，则代码将不进行编译。 例如:  
  
```cpp  
#include <memory>  
using namespace std;  
  
class F {};  
class G : public F {};  
  
shared_ptr<G> sp0(new G);   // okay, template parameter G and argument G*  
shared_ptr<G> sp1(sp0);     // okay, template parameter G and argument shared_ptr<G>  
shared_ptr<F> sp2(new G);   // okay, G* convertible to F*  
shared_ptr<F> sp3(sp0);     // okay, template parameter F and argument shared_ptr<G>  
shared_ptr<F> sp4(sp2);     // okay, template parameter F and argument shared_ptr<F>  
shared_ptr<int> sp5(new G); // error, G* not convertible to int*  
shared_ptr<int> sp6(sp2);   // error, template parameter int and argument shared_ptr<F>  
```  
  
 一个 `shared_ptr` 对象拥有一个资源：  
  
-   如果已使用指向该资源的指针构造它，  
  
-   如果已从拥有该资源的 `shared_ptr` 对象构造它，  
  
-   如果已从指向该资源的 [weak_ptr 类](../standard-library/weak-ptr-class.md) 对象构造它，或  
  
-   如果已使用 [shared_ptr::operator=](#op_eq) 或通过调用成员函数 [shared_ptr::reset](#reset) 将该资源的所有权分配给它。  
  
 拥有资源的 `shared_ptr` 对象共享控制块。 控制块包含：  
  
-   拥有该资源的 `shared_ptr` 对象的数目，  
  
-   指向该资源的 `weak_ptr` 对象的数目；  
  
-   该资源的删除器（如果有），  
  
-   控制块的自定义分配器（如果有）。  
  
 使用 null 指针初始化的 `shared_ptr` 对象具有控制块且不为空。 在 `shared_ptr` 对象释放资源之后，它将不再拥有该资源。 在 `weak_ptr` 对象释放资源之后，它将不再指向该资源。  
  
 当拥有资源的 `shared_ptr` 对象的数目变为零时，可通过删除该资源或将其地址传递给删除器来释放资源，这取决于最初创建资源所有权的方式。 当拥有资源的 `shared_ptr` 对象的数目数为零，并且指向该资源的 `weak_ptr` 对象的数目为零时，可使用控制块的自定义分配器（如果有）来释放控制块。  
  
 空 `shared_ptr` 对象不拥有任何资源和控制块。  
  
 删除器是一个拥有成员函数 `operator()` 的函数对象。 其类型必须是可复制构造的，而且其副本构造函数和析构函数不得引发异常。 它接受一个参数（即要删除的对象）。  
  
 一些函数具有一个参数列表，此列表定义了生成的 `shared_ptr<T>` 或 `weak_ptr<T>` 对象的属性。 您可通过多种方法指定此类参数列表：  
  
 无参数 - 生成的对象是一个空 `shared_ptr` 对象或者一个空 `weak_ptr` 对象。  
  
 `ptr` -- 一个指向要管理的资源的类型 `Other*` 的指针。 `T` 必须是完整类型。 如果函数失败（因为无法分配控制块），则将计算表达式 `delete ptr` 的结果。  
  
 `ptr, dtor` - 一个指向要管理的资源的类型 `Other*` 的指针和一个针对该资源的删除器。 如果函数失败（因为无法分配控制块），则调用必须经过良好定义的 `dtor(ptr)`。  
  
 `ptr, dtor, alloc` - 一个指向要管理的资源的类型 `Other*` 的指针、一个针对资源的删除器和一个用于管理必须分配和释放的任何存储的分配器。 如果函数失败（因为无法分配控制块），则调用必须经过良好定义的 `dtor(ptr)`。  
  
 `sp` - 一个拥有要管理的资源的 `shared_ptr<Other>` 对象。  
  
 `wp` - 一个指向要管理的资源的 `weak_ptr<Other>` 对象。  
  
 `ap` - 一个拥有指向要管理的资源的指针的 `auto_ptr<Other>` 对象。 如果函数成功，则调用 `ap.release()`；否则保持 `ap` 不变。  
  
 在所有情况下，指针类型 `Other*` 必须可转换为 `T*`。  
  
## <a name="thread-safety"></a>线程安全  
 多个线程可以同时读取和写入不同的 `shared_ptr` 对象，即使这些对象是共享所有权的副本。  
  
## <a name="members"></a>成员  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[shared_ptr](#shared_ptr)|构造一个 `shared_ptr`。|  
|[shared_ptr::~shared_ptr](#dtorshared_ptr)|销毁 `shared_ptr`。|  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[element_type](#element_type)|元素的类型。|  
|[get](#get)|获取拥有的资源的地址。|  
|[owner_before](#owner_before)|如果此 `shared_ptr` 排在提供的指针之前（或小于该指针），则返回 true。|  
|[reset](#reset)|替换拥有的资源。|  
|[swap](#swap)|交换两个 `shared_ptr` 对象。|  
|[unique](#unique)|测试拥有的资源是否是唯一的。|  
|[use_count](#use_count)|计算资源所有者的数目。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[shared_ptr::operator boolean-type](#op_boolean-type)|测试拥有的资源是否存在。|  
|[shared_ptr::operator*](#op_star)|获取指定的值。|  
|[shared_ptr::operator=](#op_eq)|替换拥有的资源。|  
|[shared_ptr::operator-&gt;](#operator-_gt)|获取指向指定的值的指针。|  
  
## <a name="requirements"></a>惠?  
 **标头：**\<memory>  
  
 **命名空间：** std  
  
##  <a name="element_type"></a>  shared_ptr::element_type  
 元素的类型。  
  
```  
typedef T element_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `T` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__shared_ptr_element_type.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::shared_ptr<int>::element_type val = *sp0;

    std::cout << "*sp0 == " << val << std::endl;

    return (0);
}

```  
  
```Output  
*sp0 == 5  
```  
  
##  <a name="get"></a>  shared_ptr::get  
 获取拥有的资源的地址。  
  
```  
T *get() const;
```  
  
### <a name="remarks"></a>备注  
 此成员函数返回已有资源的地址。 如果该对象没有资源，则返回 0。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__shared_ptr_get.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "sp0.get() == 0 == " << std::boolalpha
        << (sp0.get() == 0) << std::endl;
    std::cout << "*sp1.get() == " << *sp1.get() << std::endl;

    return (0);
}

```  
  
```Output  
sp0.get() == 0 == true  
*sp1.get() == 5  
```  
  
##  <a name="shared_ptr__operator_boolean-type"></a>  shared_ptr::operator boolean-type  
 测试拥有的资源是否存在。  
  
```  
operator boolean-type() const;
```  
  
### <a name="remarks"></a>备注  
 此运算符返回可转换为 `bool` 的类型的值。 当 `bool` 时，转换为 `true` 的结果为 `get() != 0`，否则为 `false`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__shared_ptr_operator_bool.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;
    std::cout << "(bool)sp1 == " << std::boolalpha
        << (bool)sp1 << std::endl;

    return (0);
}

```  
  
```Output  
(bool)sp0 == false  
(bool)sp1 == true  
```  
  
##  <a name="op_star"></a>shared_ptr::operator*  
 获取指定的值。  
  
```  
T& operator*() const;
```  
  
### <a name="remarks"></a>备注  
 间接运算符返回 `*get()`。 因此存储指针不能为 null。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__shared_ptr_operator_st.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}

```  
  
```Output  
*sp0 == 5  
```  
  
##  <a name="op_eq"></a>shared_ptr::operator=  
 替换拥有的资源。  
  
```  
shared_ptr& operator=(const shared_ptr& sp);

template <class Other>  
shared_ptr& operator=(const shared_ptr<Other>& sp);

template <class Other>  
shared_ptr& operator=(auto_ptr<Other>& ap);

template <class Other>  
shared_ptr& operator=(auto_ptr<Other>& ap);

template <class Other>  
shared_ptr& operator=(auto_ptr<Other>&& ap);

template <class Other, class Deletor>  
shared_ptr& operator=(unique_ptr<Other, Deletor>&& ap);
```  
  
### <a name="parameters"></a>参数  
 `sp`  
 要复制的共享指针。  
  
 `ap`  
 要复制的自动指针。  
  
### <a name="remarks"></a>备注  
 这些运算符均会递减 `*this` 当前拥有资源的引用计数，并将操作数序列命名的资源所有权分配给 `*this`。 如果引用计数降至零，则释放资源。 如果运算符操作失败，则不会改变 `*this`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__shared_ptr_operator_as.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));
    std::auto_ptr<int> ap(new int(10));

    sp0 = sp1;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    sp0 = ap;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}

```  
  
```Output  
*sp0 == 5  
*sp0 == 10  
```  
  
##  <a name="shared_ptr__operator-_gt"></a>shared_ptr::operator-&gt;  
 获取指向指定的值的指针。  
  
```  
T * operator->() const;
```  
  
### <a name="remarks"></a>备注  
 选择运算符返回 `get()`，以便让表达式 `sp->member` 的行为与 `(sp.get())->member` 相同，其中 `sp` 是类 `shared_ptr<T>` 的对象。 因此，存储指针不能为空且 `T` 必须是类、结构或成员为 `member` 的联合类型。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__shared_ptr_operator_ar.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
typedef std::pair<int, int> Mypair;
int main()
{
    std::shared_ptr<Mypair> sp0(new Mypair(1, 2));

    std::cout << "sp0->first == " << sp0->first << std::endl;
    std::cout << "sp0->second == " << sp0->second << std::endl;

    return (0);
}
  
```  
  
```Output  
sp0->first == 1  
sp0->second == 2  
```  
  
##  <a name="owner_before"></a>  shared_ptr::owner_before  
 如果此 `shared_ptr` 排在提供的指针之前（或小于该指针），则返回 true。  
  
```  
template <class Other>  
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>  
bool owner_before(const weak_ptr<Other>& ptr);
```  
  
### <a name="parameters"></a>参数  
 `ptr`  
 对 `shared_ptr` 或 `weak_ptr` 的 `lvalue` 引用。  
  
### <a name="remarks"></a>备注  
 如果模板成员函数返回 true`*this`是`ordered before` `ptr`。  
  
##  <a name="reset"></a>  shared_ptr::reset  
 替换拥有的资源。  
  
```  
void reset();

template <class Other>  
void reset(Other *ptr;);

template <class Other, class D>  
void reset(Other *ptr, D dtor);

template <class Other, class D, class A>  
void reset(Other *ptr, D dtor, A alloc);
```  
  
### <a name="parameters"></a>参数  
 `Other`  
 由自变量指针控制的类型。  
  
 `D`  
 删除器的类型。  
  
 `ptr`  
 要复制的指针。  
  
 `dtor`  
 要复制的删除器。  
  
 `A`  
 分配器的类型。  
  
 `alloc`  
 要复制的分配器。  
  
### <a name="remarks"></a>备注  
 这些运算符均会递减 `*this` 当前拥有资源的引用计数，并将操作数序列命名的资源所有权分配给 `*this`。 如果引用计数降至零，则释放资源。 如果运算符操作失败，则不会改变 `*this`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__shared_ptr_reset.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};  
  
int main()
{
    std::shared_ptr<int> sp(new int(5));

    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset();
    std::cout << "(bool)sp == " << std::boolalpha
        << (bool)sp << std::endl;

    sp.reset(new int(10));
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset(new int(15), deleter());
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    return (0);
}
  
```  
  
```Output  
*sp == 5  
(bool)sp == false  
*sp == 10  
*sp == 15  
```  
  
##  <a name="shared_ptr"></a>  shared_ptr::shared_ptr  
 构造一个 `shared_ptr`。  
  
```  
shared_ptr();

shared_ptr(nullptr_t);

shared_ptr(const shared_ptr& sp);

shared_ptr(shared_ptr&& sp);

template <class Other>  
explicit shared_ptr(Other* ptr);

template <class Other, class D>  
shared_ptr(Other* ptr, D dtor);

template <class D>  
shared_ptr(nullptr_t ptr, D dtor);

template <class Other, class D, class A>  
shared_ptr(Other* ptr, D dtor, A  alloc);

template <class D, class A>  
shared_ptr(nullptr_t ptr, D dtor, A alloc);

template <class Other>  
shared_ptr(const shared_ptr<Other>& sp);

template <class Other>  
shared_ptr(const weak_ptr<Other>& wp);

template <class &>  
shared_ptr(std::auto_ptr<Other>& ap);

template <class &>  
shared_ptr(std::auto_ptr<Other>&& ap);

template <class Other, class D>  
shared_ptr(unique_ptr<Other, D>&& up);

template <class Other>  
shared_ptr(const shared_ptr<Other>& sp, T* ptr);

template <class Other, class D>  
shared_ptr(const unique_ptr<Other, D>& up) = delete;  
```  
  
### <a name="parameters"></a>参数  
 `Other`  
 由自变量指针控制的类型。  
  
 `ptr`  
 要复制的指针。  
  
 `D`  
 删除器的类型。  
  
 `A`  
 分配器的类型。  
  
 `dtor`  
 删除器。  
  
 `ator`  
 分配器。  
  
 `sp`  
 要复制的智能指针。  
  
 `wp`  
 弱指针。  
  
 `ap`  
 要复制的自动指针。  
  
### <a name="remarks"></a>备注  
 每个构造函数都将构造一个对象，该对象拥有由操作数序列命名的资源。 如果 `wp.expired()`，构造函数 `shared_ptr(const weak_ptr<Other>& wp)` 引发类型 [bad_weak_ptr 类](../standard-library/bad-weak-ptr-class.md) 的异常对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__shared_ptr_construct.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};
  
int main()
{
    std::shared_ptr<int> sp0;
    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    std::shared_ptr<int> sp2(new int(10), deleter());
    std::cout << "*sp2 == " << *sp2 << std::endl;

    std::shared_ptr<int> sp3(sp2);
    std::cout << "*sp3 == " << *sp3 << std::endl;

    std::weak_ptr<int> wp(sp3);
    std::shared_ptr<int> sp4(wp);
    std::cout << "*sp4 == " << *sp4 << std::endl;

    std::auto_ptr<int> ap(new int(15));
    std::shared_ptr<int> sp5(ap);
    std::cout << "*sp5 == " << *sp5 << std::endl;

    return (0);
}

```  
  
```Output  
(bool)sp0 == false  
*sp1 == 5  
*sp2 == 10  
*sp3 == 10  
*sp4 == 10  
*sp5 == 15  
```  
  
##  <a name="dtorshared_ptr"></a>  shared_ptr::~shared_ptr  
 销毁 `shared_ptr`。  
  
```  
~shared_ptr();
```  
  
### <a name="remarks"></a>备注  
 析构函数递减 `*this` 当前拥有的资源的引用计数。 如果引用计数降至零，则释放资源。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__shared_ptr_destroy.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << "use count == " << sp1.use_count() << std::endl;

    {
        std::shared_ptr<int> sp2(sp1);
        std::cout << "*sp2 == " << *sp2 << std::endl;
        std::cout << "use count == " << sp1.use_count() << std::endl;
    }

    // check use count after sp2 is destroyed   
    std::cout << "use count == " << sp1.use_count() << std::endl;

    return (0);
}
  
```  
  
```Output  
*sp1 == 5  
use count == 1  
*sp2 == 5  
use count == 2  
use count == 1  
```  
  
##  <a name="swap"></a>  shared_ptr::swap  
 交换两个 `shared_ptr` 对象。  
  
```  
void swap(shared_ptr& sp);
```  
  
### <a name="parameters"></a>参数  
 `sp`  
 要交换的共享指针。  
  
### <a name="remarks"></a>备注  
 成员函数将保留最初由 `*this` 拥有随后由 `sp` 拥有的资源，以及最初由 `sp` 拥有随后为 `*this` 所有的资源。 此函数不会更改两个资源的引用计数，也不会引发任何异常。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__shared_ptr_swap.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
  
```  
  
```Output  
*sp1 == 5  
*sp1 == 10  
*sp1 == 5  
  
*wp1 == 5  
*wp1 == 10  
*wp1 == 5  
```  
  
##  <a name="unique"></a>  shared_ptr::unique  
 测试拥有的资源是否是唯一的。  
  
```  
bool unique() const;
```  
  
### <a name="remarks"></a>备注  
 如果其他 `shared_ptr` 对象没有为 `*this` 所有的资源，成员函数将返回 `true`，否则返回 `false`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__shared_ptr_unique.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    return (0);
}

```  
  
```Output  
sp1.unique() == true  
sp1.unique() == false  
```  
  
##  <a name="use_count"></a>  shared_ptr::use_count  
 计算资源所有者的数目。  
  
```  
long use_count() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回 `shared_ptr` 对象的数量，该对象拥有为 `*this` 所有的资源。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__shared_ptr_use_count.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    return (0);
}

```  
  
```Output  
sp1.use_count() == 1  
sp1.use_count() == 2  
```  
  
## <a name="see-also"></a>请参阅  
 [weak_ptr 类](../standard-library/weak-ptr-class.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




