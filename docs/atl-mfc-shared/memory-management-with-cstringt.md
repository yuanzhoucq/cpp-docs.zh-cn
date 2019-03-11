---
title: 使用 CStringT 进行内存管理
ms.date: 11/04/2016
f1_keywords:
- CStringT
- ATL::CStringT
- ATL.CStringT
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: 189d15df17ac28528ebbcc41879871e3426f48fb
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748627"
---
# <a name="memory-management-with-cstringt"></a>使用 CStringT 进行内存管理

类[CStringT](../atl-mfc-shared/reference/cstringt-class.md)是模板类，用于以处理可变长度字符串。 要保存这些字符串的内存进行分配和释放通过关联与每个实例的字符串管理器对象`CStringT`。 MFC 和 ATL 提供的默认实例化`CStringT`，称为`CString`， `CStringA`，和`CStringW`，该操作的不同字符类型的字符串。 这些字符类型属于类型 TCHAR， **char**，和`wchar_t`分别。 这些默认字符串类型使用的字符串管理器从进程堆 （在 ATL) 或 （在 MFC 中) 的 CRT 堆中分配内存。 对于典型的应用程序，此内存分配方案已足够。 但是，从而使密集型代码的字符串 （或多线程的代码） 的默认内存管理器可能无法以最佳方式执行的内容中进行使用。 本主题介绍如何重写的默认内存管理行为`CStringT`，专门创建的分配器适合手头的任务。

- [自定义字符串管理器的实现（基本方法）](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [避免堆争用](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [自定义字符串管理器的实现（高级方法）](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT:自定义字符串管理器的一个示例](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>请参阅

[CustomString 示例](../visual-cpp-samples.md)
