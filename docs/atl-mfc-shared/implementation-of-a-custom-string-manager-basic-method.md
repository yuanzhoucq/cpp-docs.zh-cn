---
title: 自定义字符串管理器的实现 (基本方法)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: 92c1c46f5251980f9cefb55e052e9aff395e0e60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491313"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>自定义字符串管理器的实现 (基本方法)

为字符串数据自定义内存分配方案的最简单方法是使用 ATL 提供`CAtlStringMgr`的类, 但提供自己的内存分配例程。 的构造函数`CAtlStringMgr`采用单个参数: `IAtlMemMgr`指向对象的指针。 `IAtlMemMgr`是一个抽象基类, 它提供到堆的泛型接口。 `IAtlMemMgr`使用接口`CAtlStringMgr`可以分配、重新分配和释放用于存储字符串数据的内存。 您可以自行实现`IAtlMemMgr`接口, 也可以使用五个由 ATL 提供的内存管理器类之一。 ATL 提供的内存管理器只是包装现有的内存分配设施:

- [CCRTHeap](../atl/reference/ccrtheap-class.md)包装标准 CRT 堆函数 ([malloc](../c-runtime-library/reference/malloc.md)、 [free](../c-runtime-library/reference/free.md)和[realloc](../c-runtime-library/reference/realloc.md))

- [CWin32Heap](../atl/reference/cwin32heap-class.md)使用[HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc)、 [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree)和[HeapRealloc](/windows/win32/api/heapapi/nf-heapapi-heaprealloc)包装 Win32 堆句柄

- [CLocalHeap](../atl/reference/clocalheap-class.md)包装 Win32 Api:[LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)、 [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree)和[LocalRealloc](/windows/win32/api/winbase/nf-winbase-localrealloc)

- [CGlobalHeap](../atl/reference/cglobalheap-class.md)包装 Win32 Api:[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)、 [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)和[GlobalRealloc](/windows/win32/api/winbase/nf-winbase-globalrealloc)。

- [CComHeap](../atl/reference/ccomheap-class.md)包装 COM 任务分配器 Api:[CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)、 [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)和[CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

出于字符串内存管理的目的, 最有用的类是`CWin32Heap`因为它允许您创建多个独立的堆。 例如, 如果想要对字符串使用单独的堆, 则可以执行以下操作:

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

若要使用此专用字符串管理器管理`CString`变量的内存, 请将指向该管理器的指针作为参数传递给该`CString`变量的构造函数:

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>请参阅

[使用 CStringT 进行内存管理](../atl-mfc-shared/memory-management-with-cstringt.md)
