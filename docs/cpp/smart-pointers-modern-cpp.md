---
title: 智能指针（现代 C++）
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: a18a5daa45f4f913b6b6dd714956f8592ca0a8d0
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246342"
---
# <a name="smart-pointers-modern-c"></a>智能指针（现代 C++）

In modern C++ programming, the Standard Library includes *smart pointers*, which are used to help ensure that programs are free of memory and resource leaks and are exception-safe.

## <a name="uses-for-smart-pointers"></a>智能指针的使用

Smart pointers are defined in the `std` namespace in the [\<memory>](../standard-library/memory.md) header file. They are crucial to the [RAII](objects-own-resources-raii.md) or *Resource Acquisition Is Initialization* programming idiom. 此习惯用法的主要目的是确保资源获取与对象初始化同时发生，从而能够创建该对象的所有资源并在某行代码中准备就绪。 实际上，RAII 的主要原则是为将任何堆分配资源（例如，动态分配内存或系统对象句柄）的所有权提供给其析构函数包含用于删除或释放资源的代码以及任何相关清理代码的堆栈分配对象。

大多数情况下，当初始化原始指针或资源句柄以指向实际资源时，会立即将指针传递给智能指针。 在现代 C++ 中，原始指针仅用于范围有限的小代码块、循环或者性能至关重要且不会混淆所有权的 Helper 函数中。

下面的示例将原始指针声明与智能指针声明进行了比较。

[!code-cpp[smart_pointers_intro#1](codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

如示例所示，智能指针是你在堆栈上声明的类模板，并可通过使用指向某个堆分配的对象的原始指针进行初始化。 在初始化智能指针后，它将拥有原始的指针。 这意味着智能指针负责删除原始指针指定的内存。 智能指针析构函数包括要删除的调用，并且由于在堆栈上声明了智能指针，当智能指针超出范围时将调用其析构函数，尽管堆栈上的某处将进一步引发异常。

通过使用熟悉的指针运算符（`->` 和 `*`）访问封装指针，智能指针类将重载这些运算符以返回封装的原始指针。

C++ 智能指针思路类似于在语言（如 C#）中创建对象的过程：创建对象后让系统负责在正确的时间将其删除。 不同之处在于，单独的垃圾回收器不在后台运行；按照标准 C++ 范围规则对内存进行管理，以使运行时环境更快速更有效。

> [!IMPORTANT]
>  请始终在单独的代码行上创建智能指针，而绝不在参数列表中创建智能指针，这样就不会由于某些参数列表分配规则而发生轻微泄露资源的情况。

The following example shows how a `unique_ptr` smart pointer type from the C++ Standard Library could be used to encapsulate a pointer to a large object.

[!code-cpp[smart_pointers_intro#2](codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

此示例演示如何使用智能指针执行以下关键步骤。

1. 将智能指针声明为一个自动（局部）变量。 (Do not use the **new** or `malloc` expression on the smart pointer itself.)

1. 在类型参数中，指定封装指针的指向类型。

1. Pass a raw pointer to a **new**-ed object in the smart pointer constructor. （某些实用工具函数或智能指针构造函数可为你执行此操作。）

1. 使用重载的 `->` 和 `*` 运算符访问对象。

1. 允许智能指针删除对象。

智能指针的设计原则是在内存和性能上尽可能高效。 例如，`unique_ptr` 中的唯一数据成员是封装的指针。 这意味着，`unique_ptr` 与该指针的大小完全相同，不是四个字节就是八个字节。 Accessing the encapsulated pointer by using the smart pointer overloaded * and -> operators is not significantly slower than accessing the raw pointers directly.

智能指针具有通过使用“点”表示法访问的成员函数。 For example, some C++ Standard Library smart pointers have a reset member function that releases ownership of the pointer. 如果你想要在智能指针超出范围之前释放其内存将很有用，这会很有用，如以下示例所示：

[!code-cpp[smart_pointers_intro#3](codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

智能指针通常提供直接访问其原始指针的方法。 C++ Standard Library smart pointers have a `get` member function for this purpose, and `CComPtr` has a public `p` class member. 通过提供对基础指针的直接访问，你可以使用智能指针管理你自己的代码中的内存，还能将原始指针传递给不支持智能指针的代码。

[!code-cpp[smart_pointers_intro#4](codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>Kinds of smart pointers

下一节总结了 Windows 编程环境中可用的不同类型的智能指针，并说明了何时使用它们。

### <a name="c-standard-library-smart-pointers"></a>C++ Standard Library smart pointers

使用这些智能指针作为将指针封装为纯旧 C++ 对象 (POCO) 的首选项。

- `unique_ptr`<br/>
   只允许基础指针的一个所有者。 除非你确信需要 `shared_ptr`，否则请将该指针用作 POCO 的默认选项。 可以移到新所有者，但不会复制或共享。 替换已弃用的 `auto_ptr`。 与 `boost::scoped_ptr` 比较。 `unique_ptr` is small and efficient; the size is one pointer and it supports rvalue references for fast insertion and retrieval from C++ Standard Library collections. 头文件：`<memory>`。 For more information, see [How to: Create and Use unique_ptr Instances](how-to-create-and-use-unique-ptr-instances.md) and [unique_ptr Class](../standard-library/unique-ptr-class.md).

- `shared_ptr`<br/>
   采用引用计数的智能指针。 如果你想要将一个原始指针分配给多个所有者（例如，从容器返回了指针副本又想保留原始指针时），请使用该指针。 直至所有 `shared_ptr` 所有者超出了范围或放弃所有权，才会删除原始指针。 大小为两个指针；一个用于对象，另一个用于包含引用计数的共享控制块。 头文件：`<memory>`。 For more information, see [How to: Create and Use shared_ptr Instances](how-to-create-and-use-shared-ptr-instances.md) and [shared_ptr Class](../standard-library/shared-ptr-class.md).

- `weak_ptr`<br/>
    结合 `shared_ptr` 使用的特例智能指针。 `weak_ptr` 提供对一个或多个 `shared_ptr` 实例拥有的对象的访问，但不参与引用计数。 如果你想要观察某个对象但不需要其保持活动状态，请使用该实例。 在某些情况下，需要断开 `shared_ptr` 实例间的循环引用。 头文件：`<memory>`。 For more information, see [How to: Create and Use weak_ptr Instances](how-to-create-and-use-weak-ptr-instances.md) and [weak_ptr Class](../standard-library/weak-ptr-class.md).

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>Smart pointers for COM objects (classic Windows programming)

当你使用 COM 对象时，请将接口指针包装到适当的智能指针类型中。 活动模板库 (ATL) 针对各种目的定义了多种智能指针。 你还可以使用 `_com_ptr_t` 智能指针类型，编译器在从 .tlb 文件创建包装器类时会使用该类型。 无需包含 ATL 标头文件时，它是最好的选择。

[CComPtr 类](../atl/reference/ccomptr-class.md)<br/>
除非你无法使用 ATL，否则使用此类型。 使用 `AddRef` 和 `Release` 方法执行引用计数。 For more information, see [How to: Create and Use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[CComQIPtr 类](../atl/reference/ccomqiptr-class.md)<br/>
类似于 `CComPtr`，但还提供了用于在 COM 对象上调用 `QueryInterface` 的简化语法。 For more information, see [How to: Create and Use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[CComHeapPtr 类](../atl/reference/ccomheapptr-class.md)<br/>
指向使用 `CoTaskMemFree` 释放内存的对象的智能指针。

[CComGITPtr 类](../atl/reference/ccomgitptr-class.md)<br/>
从全局接口表 (GIT) 获取的接口的智能指针。

[_com_ptr_t 类](com-ptr-t-class.md)<br/>
在功能上类似于 `CComQIPtr`，但不依赖于 ATL 标头。

### <a name="atl-smart-pointers-for-poco-objects"></a>ATL smart pointers for POCO objects

In addition to smart pointers for COM objects, ATL also defines smart pointers, and collections of smart pointers, for plain old C++ objects (POCO). In classic Windows programming, these types are useful alternatives to the C++ Standard Library collections, especially when code portability is not required or when you do not want to mix the programming models of the C++ Standard Library and ATL.

[CAutoPtr 类](../atl/reference/cautoptr-class.md)<br/>
通过转移副本所有权增强唯一所有权的智能指针。 等同于已弃用的 `std::auto_ptr` 类。

[CHeapPtr 类](../atl/reference/cheapptr-class.md)<br/>
Smart pointer for objects that are allocated by using the C [malloc](../c-runtime-library/reference/malloc.md) function.

[CAutoVectorPtr 类](../atl/reference/cautovectorptr-class.md)<br/>
使用 `new[]` 分配的数组的智能指针。

[CAutoPtrArray 类](../atl/reference/cautoptrarray-class.md)<br/>
封装一个 `CAutoPtr` 元素数组的类。

[CAutoPtrList 类](../atl/reference/cautoptrlist-class.md)<br/>
封装用于操作 `CAutoPtr` 节点列表的方法的类。

## <a name="see-also"></a>请参阅

[指针](pointers-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
