---
title: 内存管理与 CStringT
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: bf1f99b92761c84d59b6f7bfb9aef67d7e097893
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222025"
---
# <a name="memory-management-with-cstringt"></a>内存管理与 CStringT

类[CStringT](../atl-mfc-shared/reference/cstringt-class.md)是用于操作可变长度字符串的模板类。 保存这些字符串的内存是通过与每个实例关联的字符串管理器对象分配和释放的 `CStringT` 。 MFC 和 ATL 提供的默认实例化 `CStringT` （称为 `CString` 、 `CStringA` 和 `CStringW` ）可操作不同字符类型的字符串。 这些字符类型分别为 TCHAR、 **`char`** 和类型 **`wchar_t`** 。 这些默认字符串类型使用字符串管理器，该管理器从进程堆（在 ATL 中）或 CRT 堆（在 MFC 中）分配内存。 对于典型的应用程序，此内存分配方案是足够的。 但对于使用字符串（或多线程代码）的代码，默认内存管理器可能不会以最佳方式执行。 本主题介绍如何覆盖的默认内存管理行为，并 `CStringT` 为手头的任务创建专门优化的分配器。

- [自定义字符串管理器的实现（基本方法）](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [避免堆争用](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [自定义字符串管理器的实现（高级方法）](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT：自定义字符串管理器的示例](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>另请参阅

[CustomString 示例](../overview/visual-cpp-samples.md)
