---
title: 内存管理：示例
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], memory allocation
- data structures [MFC]
- arrays [MFC], allocating resources
- objects [MFC], allocating memory
- data structures [MFC], allocating memory
- examples [MFC], memory allocation
- heap allocation [MFC], examples
- memory allocation [MFC], arrays
- MFC, memory management
- struct memory allocation [MFC]
- types [MFC], memory allocation
- memory allocation [MFC], objects
- memory allocation [MFC], examples
- arrays [MFC], memory management
- frame allocation [MFC]
- memory allocation [MFC], data structures
ms.assetid: f10240f8-b698-4c83-9288-97a54318930b
ms.openlocfilehash: ca5056303f77f112e18ef09d606789a5b1c92acd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626318"
---
# <a name="memory-management-examples"></a>内存管理：示例

本文介绍 MFC 如何为三种典型类型的内存分配中的每一种执行帧分配和堆分配：

- [字节数组](#_core_allocation_of_an_array_of_bytes)

- [数据结构](#_core_allocation_of_a_data_structure)

- [对象](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a>字节数组的分配

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>在帧上分配字节数组

1. 定义数组，如下面的代码所示。 当数组变量退出其作用域时，将自动删除数组并回收其内存。

   [!code-cpp[NVC_MFC_Utilities#1](codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>在堆上分配字节数组（或任何基元数据类型）

1. 将**new**运算符用于此示例中所示的数组语法：

   [!code-cpp[NVC_MFC_Utilities#2](codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>从堆中解除分配数组

1. 按如下所示使用**delete**运算符：

   [!code-cpp[NVC_MFC_Utilities#3](codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a>数据结构的分配

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>在帧上分配数据结构

1. 定义结构变量，如下所示：

   [!code-cpp[NVC_MFC_Utilities#4](codesnippet/cpp/memory-management-examples_4.cpp)]

   当结构退出其作用域时，将回收该结构占用的内存。

#### <a name="to-allocate-data-structures-on-the-heap"></a>在堆上分配数据结构

1. 使用**new**在堆上分配数据结构，**删除**以释放它们，如以下示例所示：

   [!code-cpp[NVC_MFC_Utilities#5](codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a>对象的分配

#### <a name="to-allocate-an-object-on-the-frame"></a>在帧上分配对象

1. 声明对象，如下所示：

   [!code-cpp[NVC_MFC_Utilities#6](codesnippet/cpp/memory-management-examples_6.cpp)]

   当对象退出其作用域时，将自动调用对象的析构函数。

#### <a name="to-allocate-an-object-on-the-heap"></a>在堆上分配对象

1. 使用**new**运算符（它返回指向对象的指针）在堆上分配对象。 使用**delete**运算符删除它们。

   下面的堆和帧示例假设该 `CPerson` 构造函数不采用任何参数。

   [!code-cpp[NVC_MFC_Utilities#7](codesnippet/cpp/memory-management-examples_7.cpp)]

   如果构造函数的参数 `CPerson` 是指向**char**的指针，则帧分配的语句为：

   [!code-cpp[NVC_MFC_Utilities#8](codesnippet/cpp/memory-management-examples_8.cpp)]

   堆分配语句如下：

   [!code-cpp[NVC_MFC_Utilities#9](codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>另请参阅

[内存管理：堆分配](memory-management-heap-allocation.md)
