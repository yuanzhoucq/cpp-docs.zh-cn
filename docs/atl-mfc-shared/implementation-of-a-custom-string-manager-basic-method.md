---
title: "Implementation of a Custom String Manager (Basic Method) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAtlStringMgr class, using"
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementation of a Custom String Manager (Basic Method)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

最简单的方法自定义字符串数据的内存分配模式将使用ATL提供了 **CAtlStringMgr** 选件类，但提供自己的内存分配例程。  **CAtlStringMgr** 的构造函数采用单个参数:为 `IAtlMemMgr` 对象的指针。  `IAtlMemMgr` 是一个泛型接口使堆的抽象基类。  使用 `IAtlMemMgr` 接口，**CAtlStringMgr** 分配，重新分配，并释放使用的内存存储字符串数据。  您可以实现 `IAtlMemMgr` 接口，或者使用之一个ATL提供的内存管理器选件类。  ATL提供的内存管理器包装现有内存分配结构:  
  
-   [CCRTHeap](../atl/reference/ccrtheap-class.md) 包装标准CRT堆函数\([malloc](../c-runtime-library/reference/malloc.md)、 [免](../c-runtime-library/reference/free.md)和 [realloc](../c-runtime-library/reference/realloc.md)\)  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md) 使用 [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597)、 [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701)和 [HeapRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366704)，用于包装Win32堆处理，  
  
-   [CLocalHeap](../atl/reference/clocalheap-class.md) 包装Win32 API: [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723)、 [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730)和 [LocalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)  
  
-   [CGlobalHeap](../atl/reference/cglobalheap-class.md) 包装Win32 API: [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)、 [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)和 [GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590)。  
  
-   [CComHeap](../atl/reference/ccomheap-class.md) 包装COM任务分配程序API: [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)、 [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)和 [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)  
  
 用于字符串内存管理的目的，因为它允许您创建多个独立堆，最有用的选件类是 `CWin32Heap`。  例如，因此，如果要针对字符串使用单独堆，您可以执行以下操作:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/CPP/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 若要使用此私有字符串管理器管理 `CString` 变量的内存，请通过指向该管理器作为参数传递给 `CString` 变量的构造函数:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/CPP/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## 请参阅  
 [Memory Management with CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)