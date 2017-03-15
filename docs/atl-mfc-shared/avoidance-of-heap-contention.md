---
title: "Avoidance of Heap Contention | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "heap contention"
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Avoidance of Heap Contention
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC和ATL提供的默认字符串管理器是简单的包装在全局堆的顶部。  此全局堆是完全线程安全的，这意味着多个线程可以从同时分配和释放内存，而无需堆损坏。  为了帮助提供线程安全，堆必须序列化对自身进行访问。  这通常是通过一个临界区或类似的闭锁器。  每当两个线程同时尝试访问堆，一个线程阻塞，直至其他线程的请求完成。  对于许多应用程序，此情况极少发生，但堆的闭锁器的性能影响可忽略的。  但是，对于应用程序访问从多个线程争用的堆的堆上的锁可能会经常导致应用程序运行慢，则单线程的\(即使在具有多个CPU的计算机）。  
  
 使用 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 的应用程序特别容易受到堆争用，因为在 `CStringT` 对象的操作通常需要字符串缓冲区的重新发布。  
  
 一种缓解线程之间的堆争用具有每个线程从私钥将字符串，线程本地堆。  只要字符串随特定线程的分配器该线程仅使用，该赋值程序不需要是线程安全的。  
  
## 示例  
 下面的示例演示分配自己的私有非线程安全的堆为该线程的字符串使用的线程过程:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/CPP/avoidance-of-heap-contention_1.cpp)]  
  
## 注释  
 多个线程可以运行使用这个线程过程，但，因为每个线程具有自己的堆不在线程之间的争用。  此外，该条件每个堆都不是线程安全的对性能的增加，即使线程的一个副本运行。  这是堆的结果不使用昂贵联锁操作可防止同时访问。  
  
 对于一个更复杂的线程过程，存储指向线程的字符串管理器在线程本地存储\(TLS\)槽可能很方便。  这允许线程过程调用的其他函数访问线程的字符串管理器。  
  
## 请参阅  
 [Memory Management with CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)