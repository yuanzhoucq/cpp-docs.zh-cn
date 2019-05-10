---
title: 避免堆争用
ms.date: 11/04/2016
helpviewer_keywords:
- heap contention
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
ms.openlocfilehash: 45510607a63759aad9444959716bef164eda1492
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209996"
---
# <a name="avoidance-of-heap-contention"></a>避免堆争用

由 MFC 和 ATL 提供的默认字符串管理器是在全局堆之上的简单包装器。 此全局堆是完全线程安全的这意味着多个线程可以分配和释放从它同时而不损坏堆的内存。 若要帮助提供线程安全性，堆必须序列化到其自身的访问。 通常，这被实现与关键节或类似的锁定机制。 只要两个线程尝试同时访问堆，一个线程被阻止，直到完成其他线程的请求。 对于许多应用程序，这种情况很少发生和堆的锁定机制的性能影响可以忽略不计。 但是，对于经常从多个线程访问堆的应用程序堆的锁定争用会导致应用程序运行速度慢于如果它是单线程 （甚至在计算机上具有多个 Cpu）。

使用的应用程序[CStringT](../atl-mfc-shared/reference/cstringt-class.md)堆争用尤其易受因为操作`CStringT`经常需要重新分配字符串缓冲区的对象。

若要缓解这一堆争用线程之间的一种方法是让每个线程从专用的线程本地堆中分配的字符串。 只要将字符串分配与特定线程的分配器仅在该线程中，分配器不需要是线程安全。

## <a name="example"></a>示例

下面的示例说明了分配其自己专用的非线程安全堆来的字符串，该线程上使用一个线程的过程：

[!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/cpp/avoidance-of-heap-contention_1.cpp)]

## <a name="comments"></a>注释

无法使用此相同的线程过程运行多个线程，但由于每个线程都具有其自己的堆不存在争用线程之间。 此外，每个堆都不是线程安全的这一事实使性能明显提升即使正在运行的线程只是一个副本。 这是不使用成本高昂的互锁的操作来防范并发访问堆的结果。

有关更复杂的线程过程，可能会很方便存储线程本地存储 (TLS) 槽中的线程的字符串管理器指向的指针。 这允许其他函数所调用的线程过程访问线程的字符串管理器。

## <a name="see-also"></a>请参阅

[使用 CStringT 进行内存管理](../atl-mfc-shared/memory-management-with-cstringt.md)
