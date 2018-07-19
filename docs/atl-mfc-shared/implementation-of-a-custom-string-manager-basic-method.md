---
title: 实现的自定义字符串管理器 （基本方法） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c393489b8b4d0353ae37a21132f66e0618b3b794
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884579"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>实现的自定义字符串管理器 （基本方法）
字符串数据是使用 ATL 提供自定义的内存分配方案的最简单方法`CAtlStringMgr`类，但提供你自己的内存分配例程。 构造函数`CAtlStringMgr`采用单个参数： 一个指向`IAtlMemMgr`对象。 `IAtlMemMgr` 是一个提供到某一堆的泛型接口的抽象基类。 使用`IAtlMemMgr`接口，`CAtlStringMgr`分配、 重新分配，并释放用于存储字符串数据的内存。 可实现`IAtlMemMgr`接口，或使用五个 ATL 提供的内存管理器类之一。 ATL 提供的内存管理器只包装现有的内存分配功能：  
  
-   [CCRTHeap](../atl/reference/ccrtheap-class.md)包装标准 CRT 堆函数 ([malloc](../c-runtime-library/reference/malloc.md)，[免费](../c-runtime-library/reference/free.md)，并且[realloc](../c-runtime-library/reference/realloc.md))  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md) Win32 堆处理，使用可包装[HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597)， [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701)，并[HeapRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366704)  
  
-   [CLocalHeap](../atl/reference/clocalheap-class.md)包装了 Win32 Api: [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723)， [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730)，并[LocalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)  
  
-   [CGlobalHeap](../atl/reference/cglobalheap-class.md)包装了 Win32 Api: [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)， [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)，并且[GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590)。  
  
-   [CComHeap](../atl/reference/ccomheap-class.md)包装的 COM 任务分配器 Api: [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)， [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)，并[CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)  
  
 以进行字符串内存管理，最有用的类是`CWin32Heap`因为它允许您创建多个独立的堆。 例如，如果你想要的字符串只需使用单独的堆，可以执行以下操作：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 若要使用此专用字符串管理器来管理内存`CString`变量，向管理器作为参数传递指针`CString`变量的构造函数：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [使用 CStringT 进行内存管理](../atl-mfc-shared/memory-management-with-cstringt.md)

