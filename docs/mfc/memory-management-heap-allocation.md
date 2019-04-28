---
title: 内存管理：堆分配
ms.date: 11/04/2016
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
ms.openlocfilehash: 93eee5cbfe1cd49042a9080f06657e751640de69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219472"
---
# <a name="memory-management-heap-allocation"></a>内存管理：堆分配

堆是为程序的内存分配需求保留的。 它是程序代码和堆栈之外的区域。 典型的 C 程序使用的函数**malloc**并**免费**来分配和释放堆内存。 MFC 的调试版本提供了修改后的版本的C++内置运算符**新**并**删除**来分配和释放堆内存中的对象。

当你使用**新**并**删除**而不是**malloc**并**免费**，可以利用类库的内存管理调试增强功能，这可能有助于在检测内存泄漏。 生成的 MFC，标准版本的发行版本程序时**新**并**删除**运算符提供一种高效的方式来分配和释放内存 （发行版的 MFC不提供这些运算符的修改的版本）。

请注意，堆上分配的对象的总大小仅受系统的可用虚拟内存的限制。

## <a name="see-also"></a>请参阅

[内存管理](../mfc/memory-management.md)
