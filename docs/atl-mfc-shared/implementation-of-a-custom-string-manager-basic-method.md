---
title: 实现的自定义字符串管理器 （基本方法）
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: 4e3ffcdcd034fea81734aaeb87e4c33d81647f66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537808"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>实现的自定义字符串管理器 （基本方法）

字符串数据是使用 ATL 提供自定义的内存分配方案的最简单方法`CAtlStringMgr`类，但提供你自己的内存分配例程。 构造函数`CAtlStringMgr`采用单个参数： 一个指向`IAtlMemMgr`对象。 `IAtlMemMgr` 是一个提供到某一堆的泛型接口的抽象基类。 使用`IAtlMemMgr`接口，`CAtlStringMgr`分配、 重新分配，并释放用于存储字符串数据的内存。 可实现`IAtlMemMgr`接口，或使用五个 ATL 提供的内存管理器类之一。 ATL 提供的内存管理器只包装现有的内存分配功能：

- [CCRTHeap](../atl/reference/ccrtheap-class.md)包装标准 CRT 堆函数 ([malloc](../c-runtime-library/reference/malloc.md)，[免费](../c-runtime-library/reference/free.md)，并且[realloc](../c-runtime-library/reference/realloc.md))

- [CWin32Heap](../atl/reference/cwin32heap-class.md) Win32 堆处理，使用可包装[HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc)， [HeapFree](/windows/desktop/api/heapapi/nf-heapapi-heapfree)，并[HeapRealloc](/windows/desktop/api/heapapi/nf-heapapi-heaprealloc)

- [CLocalHeap](../atl/reference/clocalheap-class.md)包装了 Win32 Api: [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc)， [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree)，并[LocalRealloc](/windows/desktop/api/winbase/nf-winbase-localrealloc)

- [CGlobalHeap](../atl/reference/cglobalheap-class.md)包装了 Win32 Api: [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc)， [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree)，并且[GlobalRealloc](/windows/desktop/api/winbase/nf-winbase-globalrealloc)。

- [CComHeap](../atl/reference/ccomheap-class.md)包装的 COM 任务分配器 Api: [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc)， [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree)，并[CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

以进行字符串内存管理，最有用的类是`CWin32Heap`因为它允许您创建多个独立的堆。 例如，如果你想要的字符串只需使用单独的堆，可以执行以下操作：

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

若要使用此专用字符串管理器来管理内存`CString`变量，向管理器作为参数传递指针`CString`变量的构造函数：

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>请参阅

[使用 CStringT 进行内存管理](../atl-mfc-shared/memory-management-with-cstringt.md)

