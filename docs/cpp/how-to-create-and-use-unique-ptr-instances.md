---
title: 如何：创建和使用 unique_ptr 实例
ms.custom: how-to
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
ms.openlocfilehash: 4b3362f71d1ccab0efb03d7e8705c6b3f25f9780
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246528"
---
# <a name="how-to-create-and-use-unique_ptr-instances"></a>如何：创建和使用 unique_ptr 实例

[Unique_ptr](../standard-library/unique-ptr-class.md)不共享其指针。 不能将其复制到另一个 `unique_ptr`，通过值传递给函数，也不能C++在需要进行副本的任何标准库算法中使用。 只能移动 `unique_ptr`。 这意味着，内存资源所有权将转移到另一 `unique_ptr`，并且原始 `unique_ptr` 不再拥有此资源。 我们建议你将对象限制为由一个所有者所有，因为多个所有权会使程序逻辑变得复杂。 因此，当你需要用于纯C++对象的智能指针时，请使用 `unique_ptr`，当你构造 `unique_ptr`时，请使用[make_unique](../standard-library/memory-functions.md#make_unique) helper 函数。

下图演示了两个 `unique_ptr` 实例之间的所有权转换。

![移动唯一&#95;ptr 的所有权](media/unique_ptr.png "移动唯一&#95;ptr 的所有权")

`unique_ptr` 是在C++标准库的 `<memory>` 标头中定义的。 它与原始指针一样高效，并且可在标准库容器中C++使用。 将 `unique_ptr` 实例添加到C++标准库容器是高效的，因为 `unique_ptr` 的移动构造函数无需进行复制操作。

## <a name="example-1"></a>示例 1

以下示例演示如何创建 `unique_ptr` 实例并在函数之间传递这些实例。

[!code-cpp[stl_smart_pointers#210](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

这些示例说明了 `unique_ptr` 的基本特征：可移动，但不可复制。 “移动”将所有权转移到新 `unique_ptr` 并重置旧 `unique_ptr`。

## <a name="example-2"></a>示例 2

以下示例演示如何创建 `unique_ptr` 实例并在向量中使用这些实例。

[!code-cpp[stl_smart_pointers#211](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

在 range for 循环中，注意 `unique_ptr` 通过引用来传递。 如果你尝试通过此处的值传递，由于删除了 `unique_ptr` 复制构造函数，编译器将引发错误。

## <a name="example-3"></a>示例 3

以下示例演示如何初始化类成员 `unique_ptr`。

[!code-cpp[stl_smart_pointers#212](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example-4"></a>示例 4

您可以使用[make_unique](../standard-library/memory-functions.md#make_unique)来创建一个到数组的 `unique_ptr`，但不能使用 `make_unique` 来初始化数组元素。

[!code-cpp[stl_smart_pointers#213](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

有关更多示例，请参阅[make_unique](../standard-library/memory-functions.md#make_unique)。

## <a name="see-also"></a>另请参阅

[智能指针（现代 C++）](smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)
