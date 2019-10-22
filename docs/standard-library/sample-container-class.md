---
title: Sample Container 类
ms.date: 11/04/2016
helpviewer_keywords:
- container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
ms.openlocfilehash: 404e372e65af8b93ae4f6f2827a73ef64336690a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688976"
---
# <a name="sample-container-class"></a>Sample Container 类

> [!NOTE]
> 本主题在 Microsoft C++文档中作为在C++标准库中使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

描述一个对象，该对象控制不同长度的元素序列，通常为 `Ty` 类型。 此序列根据实际容器类型以不同方式存储。

容器构造函数或成员函数可调用构造函数 **Ty**(**const Ty.** ) 或函数 **Ty::operator =** (**const Ty.** )。 如果此类调用引发异常，容器对象必须维护其完整性并重新引发它所捕获到的任何异常。 引发这些异常中的其中一个异常后，可放心交换、分配、删除或销毁容器对象。 一般情况下，你无法预测由容器对象控制的序列状态。

其他注意事项：

- 如果表达式 `~Ty` 引发异常，则容器对象的结果状态为 undefined。

- 如果容器存储分配器对象*al*，而*al*引发异常而不是作为对 `al.allocate` 的调用的结果，则容器对象的结果状态为 undefined。

- 如果容器存储函数对象 *comp* 来确定如何对受控序列进行排序，且 *comp* 引发任何类型的异常，则容器对象的结果状态将不确定。

如下面几段中所述，由 C++ 标准库定义的容器类满足一些附加要求。

即使在出现上述异常的情况下，Container 类模板[列表](../standard-library/list-class.md)也可提供确定性且有用的行为。 例如，如果在单个或多个元素插入过程中引发异常，容器将保持不变并重新引发异常。

对于 C++标准库定义的所有容器类，如果在对以下成员函数的调用期间引发异常，`insert`、`push_back` 或 `push_front`，则容器将保持不变并重新引发异常。

对于 C++标准库定义的所有容器类，调用以下成员函数时不会引发异常： `pop_back`，`pop_front`。

仅当复制操作（分配或复制构造）引发异常时，成员函数 [erase](../standard-library/container-class-erase.md) 才会引发异常。

此外，复制由成员函数返回的迭代器时不会引发异常。

成员函数 [swap](../standard-library/container-class-swap.md) 对由 C++ 标准库定义的所有容器类做出其他承诺：

- 仅当容器存储分配器对象 al 且在复制中 `al` 引发异常时，成员函数才引发异常。

- 引用、指针和迭代器（指定要交换的受控序列元素）仍将有效。

由 C++标准库容器定义的容器类对象可为其通过类型为 `Alloc`（通常是一个模板参数）的存储对象控制的序列，分配和释放存储空间。 此类分配器对象必须与类 `allocator<Ty>` 的对象具有相同的外部接口。 具体而言，`Alloc` 的类型必须与 `Alloc::rebind<value_type>::other` 相同

对于 C++标准库定义的所有容器类，成员函数 `Alloc get_allocator const;` 返回存储的分配器对象的副本。 请注意，分配容器对象时*不*会复制存储的分配器对象。 所有构造函数都会初始化存储在 `allocator` 中的值，以在构造函数不包含分配器参数的情况下 `Alloc`。

根据 C++ 标准，由 C++ 标准库定义的容器类可假设：

- 类 `Alloc` 的所有对象都相等。

- 类型 `Alloc::const_pointer` 与 `const Ty *` 相同。

- 类型 `Alloc::const_reference` 与 `const Ty&` 相同。

- 类型 `Alloc::pointer` 与 `Ty *` 相同。

- 类型 `Alloc::reference` 与 `Ty&` 相同。

但在此实现中，容器并没有做出这种简单化假设。 因此，它们可正常处理更加复杂的分配器对象：

- 类 `Alloc` 的所有对象无需相等。 （可维护多个池的存储空间）

- 类型 `Alloc::const_pointer` 不需要与 `const Ty *` 相同。 （常量指针可以为类。）

- 类型 `Alloc::pointer` 不需要与 `Ty *` 相同。 （指针可以为类。）

## <a name="requirements"></a>要求

**标头**：\<sample container>

## <a name="see-also"></a>请参阅

[\<sample container>](../standard-library/sample-container.md)
