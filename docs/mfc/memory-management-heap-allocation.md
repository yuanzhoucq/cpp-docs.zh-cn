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
ms.openlocfilehash: 1f0b07a0a3439faba71078af1e2d7d1559a42b41
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626286"
---
# <a name="memory-management-heap-allocation"></a>内存管理：堆分配

堆是为程序的内存分配需求保留的。 它是程序代码和堆栈之外的区域。 典型的 C 程序使用**malloc**和**free**来分配和释放堆内存。 MFC 的调试版本提供了修改版本的 c + + 内置运算符**new**和**delete** ，用于在堆内存中分配和释放对象。

使用**new**和**delete**而不是**malloc**和**free**时，可以利用类库的内存管理调试增强功能，这在检测内存泄漏时非常有用。 使用 MFC 的发行版生成程序时，**新**的和**delete**运算符的标准版本提供了一种有效的方法来分配和释放内存（MFC 的发行版本不提供这些运算符的修改版本）。

请注意，堆上分配的对象的总大小仅受系统的可用虚拟内存的限制。

## <a name="see-also"></a>另请参阅

[内存管理](memory-management.md)
