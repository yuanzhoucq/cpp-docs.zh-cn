---
title: 指针 （C++）
ms.date: 11/19/2019
description: 有关 Microsoft C++中的原始指针和智能指针。
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 21dcc55048e9e378f370f25254e1910b05e49d69
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246424"
---
# <a name="pointers-c"></a>指针 （C++）

指针是一个变量，用于存储对象的内存地址。 指针广泛用于 C 和C++三个主要目的：

- 若要在堆上分配新对象，
- 将函数传递给其他函数
- 用于循环访问数组或其他数据结构中的元素。

在 C 样式编程中，*原始指针*用于所有这些方案。 但是，原始指针是许多严重编程错误的根源。 因此，强烈建议不要使用，除非它们提供显著的性能优势，并且没有任何明确的指针是负责删除对象的*所属指针*。 新式C++提供*智能指针*，用于分配对象、用于遍历数据结构的*迭代*器以及用于传递函数的*lambda 表达式*。 通过使用这些语言和库功能而不是原始指针，你将使程序更安全、更易于调试，更易于理解和维护。 有关详细信息，请参阅[智能指针](smart-pointers-modern-cpp.md)、[迭代](../standard-library/iterators.md)器和[Lambda 表达式](lambda-expressions-in-cpp.md)。

## <a name="in-this-section"></a>本节内容

- [原始指针](raw-pointers.md)
- [Const 和 volatile 指针](const-and-volatile-pointers.md)
- [new 和 delete 运算符](new-and-delete-operators.md)
- [智能指针](smart-pointers-modern-cpp.md)
- [如何：创建和使用 unique_ptr 实例](how-to-create-and-use-unique-ptr-instances.md)
- [如何：创建和使用 shared_ptr 实例](how-to-create-and-use-shared-ptr-instances.md)
- [如何：创建和使用 weak_ptr 实例](how-to-create-and-use-weak-ptr-instances.md)
- [如何：创建和使用 CComPtr 和 CComQIPtr 实例](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>另请参阅

[迭代器](../standard-library/iterators.md)</br>
[Lambda 表达式](lambda-expressions-in-cpp.md)
