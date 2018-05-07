---
title: 内存管理： 堆分配 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory [MFC], detecting leaks
- delete operator [MFC], using with debug MFC
- heap allocation [MFC], described
- memory allocation [MFC], heap memory
- memory leaks [MFC], detecting
- new operator [MFC], using with debug MFC
- heap allocation [MFC]
- detecting memory leaks [MFC]
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99df4a50f021e0981354a5d316606729bb824d94
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="memory-management-heap-allocation"></a>内存管理：堆分配
堆是为程序的内存分配需求保留的。 它是程序代码和堆栈之外的区域。 典型的 C 程序使用函数`malloc`和**免费**分配和释放堆内存。 MFC 的调试版本提供了 c + + 内置运算符的修改的版本**新**和**删除**分配和释放堆内存中的对象。  
  
 当你使用**新**和**删除**而不是`malloc`和**免费**，可以利用类库的内存管理调试增强功能可在检测内存泄漏很有用。 在你生成您的程序与 MFC，标准版本的发行版时**新**和**删除**运算符提供了一种高效的方式来分配和释放内存 （MFC 发行版本不提供这些运算符的修改的版本）。  
  
 请注意，堆上分配的对象的总大小仅受系统的可用虚拟内存的限制。  
  
## <a name="see-also"></a>请参阅  
 [内存管理](../mfc/memory-management.md)

