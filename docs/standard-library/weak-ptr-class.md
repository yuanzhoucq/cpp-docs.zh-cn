---
title: weak_ptr 类
ms.date: 07/29/2019
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
ms.openlocfilehash: d4ba30f737bc570a4ee700b3a317b5feebe8a50a
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682413"
---
# <a name="weakptr-class"></a>weak_ptr 类

回绕弱链接指针。

## <a name="syntax"></a>语法

```cpp
template<class T> class weak_ptr;
```

### <a name="parameters"></a>参数

*关心*\
由弱指针控制的类型。

## <a name="remarks"></a>备注

此模板类描述指向由一个或多个[shared_ptr](shared-ptr-class.md)对象管理的资源的对象。 指向某个资源的对象不会影响资源的引用计数。`weak_ptr` 当管理该`shared_ptr`资源的最后一个对象被销毁时, 将释放该资源, 即使`weak_ptr`存在指向该资源的对象也是如此。 此行为对于避免数据结构中的循环至关重要。

在以下情况下 `weak_ptr` 对象将指向某个资源：如果该对象是从拥有该资源的 `shared_ptr` 对象构造而成；如果是从指向该资源的 `weak_ptr` 对象构造而成；或者使用 [operator=](#op_eq) 将该资源分配到了该对象。 `weak_ptr`对象不提供对它所指向的资源的直接访问权限。 需要使用该资源的代码可通过一个 `shared_ptr` 对象来执行该操作，该对象通过调用成员函数 [lock](#lock) 创建并拥有该资源。 当对象指向的资源已被释放时, 对象已过期, 因为所有`shared_ptr`拥有该资源的对象已被销毁。 `weak_ptr` 调用已过期的 `weak_ptr` 对象上的 `lock` 将创建一个空 shared_ptr 对象。

空的 weak_ptr 对象不会指向任何资源, 而且没有控制块。 其成员函数 `lock` 将返回一个空 shared_ptr 对象。

当两个或多个由 `shared_ptr` 对象控制的资源保留有相互引用的 `shared_ptr` 对象时，会发生循环。 例如，具有三个元素的循环的链接列表有一个头节点 `N0`；该节点保留有一个拥有下一个节点 `N1` 的 `shared_ptr` 对象；该节点保留有一个拥有下一个节点 `N2` 的 `shared_ptr` 对象；反过来，该节点保留有一个拥有头节点 `N0` 的 `shared_ptr` 对象，由此形成闭合循环。 在这种情况下, 引用计数永远不会变为零, 并且永远不会释放循环中的节点。 若要消除循环，最后一个节点 `N2` 应保留指向 `N0` 的 `weak_ptr` 对象，而不是 `shared_ptr` 对象。 由于对象不拥有`N0` , 因此不会`N0`影响的引用计数, 并且当程序对头节点的最后一个引用被销毁时, 还会销毁列表中的节点。 `weak_ptr`

## <a name="members"></a>成员

|||
|-|-|
| **构造函数** | |
|[weak_ptr](#weak_ptr)|构造一个 `weak_ptr`。|
| **析构函数** | |
|[~ weak_ptr](#tilde-weak_ptr)|构造一个 `weak_ptr`。|
| **Typedefs** | |
|[element_type](#element_type)|元素的类型。|
| **成员函数** | |
|[expired](#expired)|测试所属权是否已过期。|
|[lock](#lock)|获取资源的独占所属权。|
|[owner_before](#owner_before)|如果  此`weak_ptr`值在提供的指针之前 (或小于), 则返回 true。|
|[reset](#reset)|释放所拥有的资源。|
|[swap](#swap)|交换两个 `weak_ptr` 对象。|
|[use_count](#use_count)|计算对象的`shared_ptr`数量。|
| **运算符** | |
|[operator=](#op_eq)|替换所拥有的资源。|

## <a name="element_type"></a>element_type

元素的类型。

```cpp
typedef T element_type; // through C++17
using element_type = remove_extent_t<T>; // C++20
```

### <a name="remarks"></a>备注

该类型是模板参数 `T` 的同义词。

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

## <a name="expired"></a>期限

测试所有权是否已过期, 即是否已删除引用的对象。

```cpp
bool expired() const noexcept;
```

### <a name="remarks"></a>备注

如果`*this`已过期, 则成员函数将返回 true, 否则返回**false**。

### <a name="example"></a>示例

```cpp
// std__memory__weak_ptr_expired.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="lock"></a>住

获取一个`shared_ptr` , 它共享资源的所有权。

```cpp
shared_ptr<T> lock() const noexcept;
```

### <a name="remarks"></a>备注

`*this`如果`*this`已过期, 则成员函数返回一个空的[shared_ptr](shared-ptr-class.md)对象; 否则它`shared_ptr<T>`将返回一个对象, 该对象拥有指向的资源。 返回一个与的原子执行`expired() ? shared_ptr<T>() : shared_ptr<T>(*this)`等效的值。

### <a name="example"></a>示例

```cpp
// std__memory__weak_ptr_lock.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="op_eq"></a>operator =

替换所拥有的资源。

```cpp
weak_ptr& operator=(const weak_ptr& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& ptr) noexcept;
```

### <a name="parameters"></a>参数

*以外*\
由参数 shared 或弱指针控制的类型。

*ptr*\
要复制的弱指针或共享指针。

### <a name="remarks"></a>备注

这些运算符都释放当前指向`*this`的资源, 并将由*ptr*命名的资源的所有权分配给`*this`。 如果运算符失败, 则它将`*this`保持不变。 每个运算符都具有等效`weak_ptr(ptr).swap(*this)`于的效果。

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

如果  此`weak_ptr`值在提供的指针之前 (或小于), 则返回 true。

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr) const noexcept;

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr) const noexcept;
```

### <a name="parameters"></a>参数

*ptr*\
`shared_ptr` 对`weak_ptr`或的左值引用。

### <a name="remarks"></a>备注

如果  `*this`在*ptr*之前对进行排序, 则模板成员函数返回 true。

## <a name="reset"></a>&

释放所拥有的资源。

```cpp
void reset() noexcept;
```

### <a name="remarks"></a>备注

该成员函数将释放指向的`*this`资源, 并将其转换`*this`为`weak_ptr`空的对象。

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

## <a name="swap"></a>购

交换两个 `weak_ptr` 对象。

```cpp
void swap(weak_ptr& wp) noexcept;
```

还包括专用化:

```cpp
template<class T>
void swap(weak_ptr<T>& a, weak_ptr<T>& b) noexcept;
```

### <a name="parameters"></a>参数

*wp*\
要交换的弱指针。

### <a name="remarks"></a>备注

`*this` `*this`在之后,最初指向的资源由wp指向,而由wp最初指向的资源由指向。`swap` 函数不会更改这两个资源的引用计数, 也不会引发任何异常。 模板专用化的效果等效于`a.swap(b)`。

### <a name="example"></a>示例

```cpp
// std__memory__weak_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

对拥有共享资源`shared_ptr`的对象的数目进行计数。

```cpp
long use_count() const noexcept;
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
constexpr weak_ptr() noexcept;

weak_ptr(const weak_ptr& wp) noexcept;

weak_ptr(weak_ptr&& wp) noexcept;

template <class Other>
weak_ptr(const weak_ptr<Other>& wp) noexcept;

template <class Other>
weak_ptr(weak_ptr<Other>&& sp) noexcept;

template <class Other>
weak_ptr(const shared_ptr<Other>& sp) noexcept;
```

### <a name="parameters"></a>参数

*以外*\
由参数共享/弱指针控制的类型。 除非_其他\*_ 构造函数与兼容`element_type*`, 否则这些构造函数不参与重载决策。

*wp*\
要复制的弱指针。

*sp*\
要复制的共享指针。

### <a name="remarks"></a>备注

默认构造函数构造一个空`weak_ptr`对象。 如果参数指针为空, 则采用参数的`weak_ptr`构造函数将构造一个空对象。 否则, 它们将构造`weak_ptr`一个指向由参数命名的资源的对象。 不会更改共享对象的引用计数。

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

## <a name="tilde-weak_ptr"></a>~ weak_ptr

销毁 `weak_ptr`。

```cpp
~weak_ptr();
```

### <a name="remarks"></a>备注

析构函数会销毁`weak_ptr`此函数, 但不会对其存储指针指向的对象的引用计数产生任何影响。

## <a name="see-also"></a>请参阅

[头文件引用](cpp-standard-library-header-files.md)\
[\<memory>](memory.md)\
[shared_ptr 类](shared-ptr-class.md)
