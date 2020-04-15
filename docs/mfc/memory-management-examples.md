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
ms.openlocfilehash: 3a1e647175b7b5294e672efbf234e3ae2853e411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367849"
---
# <a name="memory-management-examples"></a>内存管理：示例

本文介绍 MFC 如何对三种典型的内存分配执行帧分配和堆分配：

- [字节数组](#_core_allocation_of_an_array_of_bytes)

- [数据结构](#_core_allocation_of_a_data_structure)

- [对象](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a>字节数组的分配

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>在帧上分配字节数组

1. 定义数组，如以下代码所示。 当数组变量退出其范围时，阵列将自动删除，其内存将回收。

   [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>在堆上分配字节数组（或任何基元数据类型）

1. 将**新**运算符与此示例中所示的数组语法一起使用：

   [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>从堆中取消分配数组

1. 使用**删除**运算符，如下所示：

   [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a>数据结构的分配

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>在帧上分配数据结构

1. 定义结构变量，如下所示：

   [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]

   当结构退出其作用域时，将回收结构占用的内存。

#### <a name="to-allocate-data-structures-on-the-heap"></a>在堆上分配数据结构

1. 使用**new**在堆上分配数据结构**并删除**以取消分配它们，如以下示例所示：

   [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a>对象的分配

#### <a name="to-allocate-an-object-on-the-frame"></a>在帧上分配对象

1. 声明对象如下：

   [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]

   当对象退出其范围时，将自动调用对象的析构函数。

#### <a name="to-allocate-an-object-on-the-heap"></a>在堆上分配对象

1. 使用返回指向对象的指针**的新**运算符在堆上分配对象。 使用**删除**运算符删除它们。

   以下堆和帧示例假定`CPerson`构造函数不采用任何参数。

   [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]

   如果构造函数的`CPerson`参数是指向**char**的指针，则帧分配的语句为：

   [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]

   堆分配的语句是：

   [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>另请参阅

[内存管理：堆分配](../mfc/memory-management-heap-allocation.md)
