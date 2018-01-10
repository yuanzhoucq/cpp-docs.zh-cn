---
title: "CStringT 使用内存管理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringT
- ATL::CStringT
- ATL.CStringT
dev_langs: C++
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbf623344ec52abce28a08670e7f3cd09140563b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management-with-cstringt"></a>CStringT 使用内存管理
类[CStringT](../atl-mfc-shared/reference/cstringt-class.md)是模板类，用于操作长度可变字符字符串。 分配内存来保存这些字符串并将其关联的每个实例的字符串 manager 对象通过发布`CStringT`。 MFC 和 ATL 提供的默认实例化`CStringT`、 调用`CString`， `CStringA`，和`CStringW`，其操作的不同的字符类型的字符串。 这些字符类型属于类型**TCHAR**， `char`，和`wchar_t`分别。 这些默认字符串类型使用的字符串管理器，从进程堆 （在 ATL) 或 （在 MFC 中) 的 CRT 堆中分配内存。 对于典型应用程序，这种内存分配方案就足够了。 但是，为了进行密集型代码字符串 （或多线程的代码），它默认内存管理器可能无法以最佳方式执行的内容中进行使用。 本主题介绍如何重写的默认内存管理行为`CStringT`，专门创建的分配器适合手头的任务。  
  
-   [自定义字符串管理器的实现（基本方法）](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)  
  
-   [避免堆争用](../atl-mfc-shared/avoidance-of-heap-contention.md)  
  
-   [自定义字符串管理器的实现（高级方法）](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)  
  
-   [CFixedStringT： 示例的自定义字符串管理器](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)  
  
## <a name="see-also"></a>请参阅  
 [CustomString 示例](../visual-cpp-samples.md)

