---
title: 指针 (C++)
ms.date: 11/19/2019
description: 关于微软C++的原始指针和智能指针。
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 485cee667fa288bff76fdeac7c9f229355c276d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371919"
---
# <a name="pointers-c"></a>指针 (C++)

指针是存储对象的内存地址的变量。 指针在 C 和C++中广泛使用，主要有三个目的：

- 在堆上分配新对象，
- 将函数传递给其他函数
- 迭代数组或其他数据结构中的元素。

在 C 样式的编程中，*原始指针*用于所有这些方案。 但是，原始指针是许多严重编程错误的根源。 因此，强烈建议不使用它们，除非它们提供了显著的性能优势，并且对于哪个指针是负责删除对象的*拥有指针*没有歧义。 现代C++提供用于分配对象的*智能指针*、用于遍历数据结构的*迭代器*以及用于传递函数*的 lambda 表达式*。 通过使用这些语言和库工具而不是原始指针，可以使程序更安全、更易于调试以及更易于理解和维护。 有关详细信息，请参阅[智能指针](smart-pointers-modern-cpp.md)、[迭代器](../standard-library/iterators.md)和[Lambda 表达式](lambda-expressions-in-cpp.md)。

## <a name="in-this-section"></a>在本节中

- [原始指针](raw-pointers.md)
- [Const 和易失性指针](const-and-volatile-pointers.md)
- [新建运算符和删除运算符](new-and-delete-operators.md)
- [智能指针](smart-pointers-modern-cpp.md)
- [如何：创建和使用unique_ptr实例](how-to-create-and-use-unique-ptr-instances.md)
- [如何：创建和使用shared_ptr实例](how-to-create-and-use-shared-ptr-instances.md)
- [如何：创建和使用weak_ptr实例](how-to-create-and-use-weak-ptr-instances.md)
- [如何：创建和使用 CComPtr 和 CComQIPtr 实例](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>另请参阅

[迭代器](../standard-library/iterators.md)</br>
[Lambda 表达式](lambda-expressions-in-cpp.md)
