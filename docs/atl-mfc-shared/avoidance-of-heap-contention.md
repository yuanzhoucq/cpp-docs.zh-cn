---
title: 避免堆争用 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- heap contention
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 731fcb2328f789e5c487dc56510bbd6f7ec049ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="avoidance-of-heap-contention"></a>避免堆争用
MFC 和 ATL 提供的默认字符串经理都在全局堆之上的简单包装器。 此全局堆是完全线程安全的这意味着多个线程可以分配和释放从它同时不会损坏堆的内存。 若要帮助提供线程安全性，堆必须序列化到其自身的访问。 这通常被实现的关键部分或类似的锁定机制。 两个线程尝试同时访问堆，每当一个线程阻止，直到完成其他线程的请求。 对于许多应用程序，这种情况很少发生，并且堆的锁定机制的性能影响可以忽略不计。 但是，对于应用程序经常从多个线程访问堆堆的锁争用会导致更慢速度如果它是单线程方式 （甚至在具有多个 Cpu 的计算机） 上运行该应用程序。  
  
 应用程序使用[CStringT](../atl-mfc-shared/reference/cstringt-class.md)特别容易出现堆争用因为对操作`CStringT`经常需要的对象的字符串缓冲区重新分配。  
  
 减轻堆争用线程之间的一种方法是为每个线程分配专用的线程本地堆中的字符串。 只要将字符串分配与仅在该线程中使用特定线程的分配器，分配器不需要是线程安全。  
  
## <a name="example"></a>示例  
 下面的示例阐释了分配自己专用的非线程安全堆，以供该线程上的字符串的线程过程：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/cpp/avoidance-of-heap-contention_1.cpp)]  
  
## <a name="comments"></a>注释  
 无法使用此相同的线程过程运行多个线程，但由于每个线程都有自己的堆没有在线程之间没有任何争用。 此外，每个堆都不是线程安全的事实使性能明显提升，即使只是一份线程正在运行。 这是不使用成本高昂的联锁的操作以防止并发访问堆的结果。  
  
 有关更复杂的线程过程，则可能很方便存储线程本地存储 (TLS) 槽中的线程的字符串管理器指向的指针。 这允许其他函数调用的线程的过程以访问线程的字符串管理器。  
  
## <a name="see-also"></a>请参阅  
 [使用 CStringT 进行内存管理](../atl-mfc-shared/memory-management-with-cstringt.md)

