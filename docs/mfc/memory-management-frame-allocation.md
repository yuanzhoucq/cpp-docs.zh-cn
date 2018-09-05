---
title: 内存管理： 帧分配 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory leaks [MFC], frame allocation
- memory [MFC], detecting leaks
- memory [MFC], reclaiming
- memory allocation [MFC], frames
- frame variables [MFC], automatic deletion of
- scope [MFC], frame variables
- heap allocation [MFC], vs. frame allocation
- variables [MFC], frame variables
- memory leaks [MFC], detecting
- memory, releasing [MFC]
- stack frames [MFC]
- memory leaks [MFC], allocating objects on the frame
- detecting memory leaks [MFC]
- frame allocation [MFC]
- frame variables [MFC]
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56eff6cede20508ea59463039b4f0e41d416cac1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686347"
---
# <a name="memory-management-frame-allocation"></a>内存管理：帧分配
只要调用函数，帧分配就会从已设置的“堆栈帧”中采用其名称。 堆栈帧是一个内存区域，可暂时存储函数的参数以及为函数定义的所有局部变量。 帧变量通常称为“自动”变量，因为编译器会自动为其分配空间。  
  
 帧分配有两个关键特性。 第一个特性是，当您定义局部变量时，会在堆栈帧上分配足够的空间来容纳整个变量，即使它是一个大型数组或数据结构。 第二个特性是，帧变量在超出范围时会自动被删除：  
  
 [!code-cpp[NVC_MFC_Utilities#10](../mfc/codesnippet/cpp/memory-management-frame-allocation_1.cpp)]  
  
 对于局部函数变量，当函数存在时会发生此范围转换，但如果使用嵌套括号，则帧变量的范围会比函数的范围小。 此自动删除帧变量的功能是非常重要的。 在简单的基元类型的情况下 (如**int**或**字节**)，数组或数据结构，自动删除功能仅回收变量所使用的内存。 由于变量超出了范围，因此无法访问它。 不过，对于 C++ 对象，自动删除过程会更复杂一点。  
  
 在将某个对象定义为帧变量时，会在遇到定义的位置自动调用其构造函数。 如果对象超出范围，则在回收此对象的内存之前将自动调用其析构函数。 此自动构造和析构非常方便，但您必须意识到自动调用，特别是对于析构函数。  
  
 在帧上分配对象的主要好处是可自动删除这些对象。 在帧上分配对象时，不必担心忘记导致内存泄漏的对象。 (有关内存泄漏的详细信息，请参阅文章[在 MFC 中检测内存泄漏](/previous-versions/visualstudio/visual-studio-2010/c99kz476\(v=vs.100\))。)帧分配的缺点是无法在帧变量的范围之外使用这些变量。 选择帧分配还是堆分配所依据的另一个因素是：对于大型结构和对象，通常更好的选择是使用堆而不是存储堆栈，因为堆栈空间通常是有限的。  
  
## <a name="see-also"></a>请参阅  
 [内存管理](../mfc/memory-management.md)

