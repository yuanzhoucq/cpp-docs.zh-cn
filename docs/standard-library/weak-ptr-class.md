---
title: weak_ptr 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::weak_ptr
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
- memory/std::weak_ptr::operator=
dev_langs:
- C++
helpviewer_keywords:
- std::weak_ptr [C++]
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4aa0f8e94e0797badbae2a409ae1ce02caea6e81
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707518"
---
# <a name="weakptr-class"></a>weak_ptr 类

回绕弱链接指针。

## <a name="syntax"></a>语法

```cpp
template<class _Ty>
   class weak_ptr {
public:
   typedef Ty element_type;
   weak_ptr();
   weak_ptr(const weak_ptr&);
   template <class Other>
      weak_ptr(const weak_ptr<Other>&);
   template <class Other>
      weak_ptr(const shared_ptr<Other>&);
   weak_ptr& operator=(const weak_ptr&);
   template <class Other>
      weak_ptr& operator=(const weak_ptr<Other>&);
   template <class Other>
      weak_ptr& operator=(shared_ptr<Other>&);
   void swap(weak_ptr&);
   void reset();
   long use_count() const;
   bool expired() const;
   shared_ptr<Ty> lock() const;
   };
```

### <a name="parameters"></a>参数

*Ty*<br/>
由弱指针控制的类型。

## <a name="remarks"></a>备注

此模板类描述了一个对象，此对象指向由一个或多个 [shared_ptr 类](../standard-library/shared-ptr-class.md)对象管理的资源的。 指向某个资源的 `weak_ptr` 对象不会影响资源的引用计数。 因此，当最后一个管理该资源 `shared_ptr` 的对象被销毁时，则即使存在指向该资源的 `weak_ptr` 对象，该资源也将被释放。 这对于避免数据结构中的循环至关重要。

在以下情况下 `weak_ptr` 对象将指向某个资源：如果该对象是从拥有该资源的 `shared_ptr` 对象构造而成；如果是从指向该资源的 `weak_ptr` 对象构造而成；或者使用 [operator=](#op_eq) 将该资源分配到了该对象。 `weak_ptr` 对象不提供直接访问其所指向的资源的权限。 需要使用该资源的代码可通过一个 `shared_ptr` 对象来执行该操作，该对象通过调用成员函数 [lock](#lock) 创建并拥有该资源。 `weak_ptr` 对象在其所指向的资源被释放时已过期，因为所有拥有该资源的 `shared_ptr` 对象已被销毁。 调用已过期的 `weak_ptr` 对象上的 `lock` 将创建一个空 shared_ptr 对象。

空 weak_ptr 对象不会指向任何资源，而且没有控制块。 其成员函数 `lock` 将返回一个空 shared_ptr 对象。

当两个或多个由 `shared_ptr` 对象控制的资源保留有相互引用的 `shared_ptr` 对象时，会发生循环。 例如，具有三个元素的循环的链接列表有一个头节点 `N0`；该节点保留有一个拥有下一个节点 `N1` 的 `shared_ptr` 对象；该节点保留有一个拥有下一个节点 `N2` 的 `shared_ptr` 对象；反过来，该节点保留有一个拥有头节点 `N0` 的 `shared_ptr` 对象，由此形成闭合循环。 在此情况下，没有引用计数将变为零，并且不会释放循环中的节点。 若要消除循环，最后一个节点 `N2` 应保留指向 `N0` 的 `weak_ptr` 对象，而不是 `shared_ptr` 对象。 由于 `weak_ptr` 对象不拥有 `N0`，因此不会影响 `N0` 的引用计数，并且销毁该程序对头节点的最后一个引用时，也将销毁列表中的节点。

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[weak_ptr](#weak_ptr)|构造一个 `weak_ptr`。|

### <a name="methods"></a>方法

|||
|-|-|
|[element_type](#element_type)|元素的类型。|
|[expired](#expired)|测试所属权是否已过期。|
|[lock](#lock)|获取资源的独占所属权。|
|[owner_before](#owner_before)|返回 **，则返回 true**如果此`weak_ptr`排序之前 (或小于) 所提供的指针。|
|[reset](#reset)|释放所拥有的资源。|
|[swap](#swap)|交换两个 `weak_ptr` 对象。|
|[use_count](#use_count)|指定 `shared_ptr` 对象的计数。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator=](#op_eq)|替换所拥有的资源。|

## <a name="requirements"></a>要求

**标头：**\<memory>

**命名空间：** std

## <a name="element_type"></a>element_type

元素的类型。

```cpp
typedef Ty element_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 `Ty` 的同义词。

### <a name="example"></a>示例

```cpp
// std__memory__weak_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::weak_ptr<int>::element_type val = *wp0.lock();

    std::cout << "*wp0.lock() == " << val << std::endl;

    return (0);
    }

```

```Output
*wp0.lock() == 5
```

## <a name="expired"></a>expired

测试所属权是否已过期。

```cpp
bool expired() const;
```

### <a name="remarks"></a>备注

此成员函数返回 **，则返回 true**如果`*this`已过期，否则**false**。

### <a name="example"></a>示例

```cpp
// std__memory__weak_ptr_expired.cpp
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
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}

```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="lock"></a>lock

获取资源的独占所属权。

```cpp
shared_ptr<Ty> lock() const;
```

### <a name="remarks"></a>备注

此成员函数返回空 shared_ptr 对象，如果`*this`已过期; 否则返回[shared_ptr 类](../standard-library/shared-ptr-class.md)\<Ty > 对象，它拥有的资源`*this`指向。

### <a name="example"></a>示例

```cpp
// std__memory__weak_ptr_lock.cpp
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
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="op_eq"></a>operator=

替换所拥有的资源。

```cpp
weak_ptr& operator=(const weak_ptr& wp);

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& wp);

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>参数

*其他*<br/>
由参数共享/弱指针控制的类型。

*wp*<br/>
要复制的弱指针。

*sp*<br/>
要复制的共享指针。

### <a name="remarks"></a>备注

这些运算符均会释放 `*this` 当前指向的资源，并将操作数序列命名的资源所有权分配给 `*this`。 如果运算符操作失败，则不会改变 `*this`。

### <a name="example"></a>示例

```cpp
// std__memory__weak_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::shared_ptr<int> sp1(new int(10));
    wp0 = sp1;
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::weak_ptr<int> wp1;
    wp1 = wp0;
    std::cout << "*wp1.lock() == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
*wp0.lock() == 10
*wp1.lock() == 10
```

## <a name="owner_before"></a>owner_before

返回 **，则返回 true**如果此`weak_ptr`排序之前 (或小于) 所提供的指针。

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr);
```

### <a name="parameters"></a>参数

*ptr*<br/>
对 `shared_ptr` 或 `weak_ptr` 的 `lvalue` 引用。

### <a name="remarks"></a>备注

模板成员函数返回 **，则返回 true**如果`*this`是`ordered before` `ptr`。

## <a name="reset"></a>reset

释放所拥有的资源。

```cpp
void reset();
```

### <a name="remarks"></a>备注

该成员函数将释放 `*this` 指向的资源，并将 `*this` 转换到空的 weak_ptr 对象。

### <a name="example"></a>示例

```cpp
// std__memory__weak_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp(new int(5));
    std::weak_ptr<int> wp(sp);
    std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    wp.reset();
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    return (0);
}

```

```Output
*wp.lock() == 5
wp.expired() == false
wp.expired() == true
```

## <a name="swap"></a>swap

交换两个 `weak_ptr` 对象。

```cpp
void swap(weak_ptr& wp);
```

### <a name="parameters"></a>参数

*wp*<br/>
要交换的弱指针。

### <a name="remarks"></a>备注

成员函数将保留最初由指向的资源`*this`且随后由*wp*，并通过最初指向的资源*wp*且随后由`*this`. 此函数不会更改两个资源的引用计数，也不会引发任何异常。

### <a name="example"></a>示例

```cpp
// std__memory__weak_ptr_swap.cpp
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

## <a name="use_count"></a>use_count

指定 `shared_ptr` 对象的计数。

```cpp
long use_count() const;
```

### <a name="remarks"></a>备注

成员函数将返回拥有 `*this` 指向的资源的 `shared_ptr` 对象数量。

### <a name="example"></a>示例

```cpp
// std__memory__weak_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    return (0);
}

```

```Output
wp.use_count() == 1
wp.use_count() == 2
```

## <a name="weak_ptr"></a>weak_ptr

构造一个 `weak_ptr`。

```cpp
weak_ptr();

weak_ptr(const weak_ptr& wp);

template <class Other>
weak_ptr(const weak_ptr<Other>& wp);

template <class Other>
weak_ptr(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>参数

*其他*<br/>
由参数共享/弱指针控制的类型。

*wp*<br/>
要复制的弱指针。

*sp*<br/>
要复制的共享指针。

### <a name="remarks"></a>备注

每个构造函数都将构造指向由操作数序列命名的资源的对象。

### <a name="example"></a>示例

```cpp
// std__memory__weak_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp0;
    std::cout << "wp0.expired() == " << std::boolalpha
        << wp0.expired() << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp1(sp1);
    std::cout << "*wp1.lock() == "
        << *wp1.lock() << std::endl;

    std::weak_ptr<int> wp2(wp1);
    std::cout << "*wp2.lock() == "
        << *wp2.lock() << std::endl;

    return (0);
}

```

```Output
wp0.expired() == true
*wp1.lock() == 5
*wp2.lock() == 5
```

## <a name="see-also"></a>请参阅

[shared_ptr 类](../standard-library/shared-ptr-class.md)<br/>
