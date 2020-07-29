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
ms.openlocfilehash: ecf60fbdd11f540d12c1bfab047bbb80a3cb83e8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228591"
---
# <a name="memory-management-heap-allocation"></a>内存管理：堆分配

堆是为程序的内存分配需求保留的。 它是程序代码和堆栈之外的区域。 典型的 C 程序使用**malloc**和**free**来分配和释放堆内存。 MFC 的调试版本提供了修改后版本的 c + + 内置运算符 **`new`** ，并 **`delete`** 在堆内存中分配和释放对象。

使用 **`new`** 和 **`delete`** 而不是**malloc**和**free**时，可以利用类库的内存管理调试增强功能，这在检测内存泄漏时非常有用。 使用 MFC 的发行版生成程序时，和运算符的标准版本 **`new`** **`delete`** 提供了一种有效的方法来分配和释放内存（MFC 的发布版本不提供这些运算符的修改版本）。

请注意，堆上分配的对象的总大小仅受系统的可用虚拟内存的限制。

## <a name="see-also"></a>另请参阅

[内存管理](memory-management.md)
