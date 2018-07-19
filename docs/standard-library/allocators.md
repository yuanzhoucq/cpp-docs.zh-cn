---
title: Allocators | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc84748e35807ef0f270fe8fbbd7560a9a18e3b2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963490"
---
# <a name="allocators"></a>Allocators

C++ 标准库使用分配器处理存储在容器中的元素的分配和释放。 除 std:: array 外的所有 C++ 标准库容器都具有一个类型为 `allocator<Type>` 的模板参数，其中 `Type` 表示容器元素的类型。 例如，vector 类声明如下：

```cpp
template <
    class Type,
    class Allocator = allocator<Type>
>
class vector
```

C++ 标准库提供分配器的默认实现。 在 C++11 及更高版本中，默认分配器更新以公开较小接口；新的分配器称为*最小的分配器*。 具体而言，最小分配器的 `construct()` 成员支持移动语义，从而可以极大地提高性能。 在大多数情况下，此默认分配器应该是够用的。 在 C++11 中，所有采用分配器类型参数的标准库类型和函数均支持最小分配器接口，包括 `std::function`、`shared_ptr, allocate_shared()` 和 `basic_string`。  有关默认分配器的详细信息，请参阅 [allocator](../standard-library/allocator-class.md) 类。

## <a name="writing-your-own-allocator-c11"></a>编写你自己的分配器 (C++11)

默认分配器使用**新**并**删除**来分配和释放内存。 如果想使用内存分配的不同方法（例如，使用共享内存），则必须创建自己的分配器。 如果面向的 C++11，并且需要编写新的自定义分配器，如有可能，使其成为最小分配器。 即使已实现旧式分配器，也请考虑将其修改成*最小分配器*以利用更有效的 `construct()` 方法，后者将自动提供给你。

最小分配器所需的样本要少得多，并使你能够将重点放在 `allocate` 和 `deallocate` 成员函数，它们可以执行所有工作。 创建最小分配器时，除以下示例中所示成员外，请勿实现其他任何成员：

1. 转换复制构造函数（请参见示例）

1. operator==

1. operator!=

1. allocate

1. 释放

将提供给你的 C++11 默认 `construct()` 成员可完美执行转发操作并启用移动语义；它在许多情况下相较旧版本要高效得多。

> [!WARNING]
> 在编译时，C++ 标准库使用 allocator_traits 类来检测显式提供了哪些成员，并为任何不存在的成员提供默认实现。 请勿通过向分配器提供 allocator_traits 的专用化来干扰此机制！

下面的示例演示使用 `malloc` 和 `free` 的分配器的最小实现。 请注意新的异常类型 `std::bad_array_new_length` 的使用，该异常在数组大小小于零或大于允许的最大值时引发。

```cpp
#pragma once
#include <stdlib.h> //size_t, malloc, free
#include <new> // bad_alloc, bad_array_new_length
#include <memory>
template <class T>
struct Mallocator
{
    typedef T value_type;
    Mallocator() noexcept {} //default ctor not required by C++ Standard Library

    // A converting copy constructor:
    template<class U> Mallocator(const Mallocator<U>&) noexcept {}
    template<class U> bool operator==(const Mallocator<U>&) const noexcept
    {
        return true;
    }
    template<class U> bool operator!=(const Mallocator<U>&) const noexcept
    {
        return false;
    }
    T* allocate(const size_t n) const;
    void deallocate(T* const p, size_t) const noexcept;
};

template <class T>
T* Mallocator<T>::allocate(const size_t n) const
{
    if (n == 0)
    {
        return nullptr;
    }
    if (n > static_cast<size_t>(-1) / sizeof(T))
    {
        throw std::bad_array_new_length();
    }
    void* const pv = malloc(n * sizeof(T));
    if (!pv) { throw std::bad_alloc(); }
    return static_cast<T*>(pv);
}

template<class T>
void Mallocator<T>::deallocate(T * const p, size_t) const noexcept
{
    free(p);
}
```

## <a name="writing-your-own-allocator-c03"></a>编写你自己的分配器 (C++03)

在 C++03 中，任何与 C++ 标准库容器一起使用的分配器必须实现以下类型的定义：

|||
|-|-|
|`const_pointer`|`rebind`|
|`const_reference`|`reference`|
|`difference_type`|`size_type`|
|`pointer`|`value_type`|

除此以外，任何与 C++ 标准库容器一起使用的分配器必须实现以下方法：

|||
|-|-|
|构造函数|`deallocate`|
|复制构造函数|`destroy`|
|析构函数|`max_size`|
|`address`|`operator==`|
|`allocate`|`operator!=`|
|`construct`||

有关这些类型定义和方法的详细信息，请参阅 [allocator 类](../standard-library/allocator-class.md)。

## <a name="see-also"></a>请参阅

[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
