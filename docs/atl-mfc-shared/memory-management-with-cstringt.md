---
title: "Memory Management with CStringT | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStringT"
  - "ATL::CStringT"
  - "ATL.CStringT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFixedStringT class, description of"
  - "CString objects, 内存管理"
  - "CStringT class, 内存管理"
  - "IAtlStringMgr class, using"
  - "内存 [C++], 用法"
  - "字符串 [C++], custom memory management"
  - "字符串 [C++], 内存管理"
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Memory Management with CStringT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

选件类 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 会用于模板选件类操作可变长度字符串。  保存这些字符串的内存传递字符串管理器对象分配和释放，与 `CStringT`每个实例。  MFC和ATL提供 `CStringT`的默认实例化，调用 `CString`、 `CStringA`和 `CStringW`，操作不同的字符类型字符串。  这些字符类型分别为类型 **TCHAR**、 `char`和 `wchar_t`。  这些默认字符串类型使用从处理堆的字符串管理器\(在ATL\)或CRT堆分配内存\(在MFC）。  对于典型的应用程序，此内存分配模式就足够了。  但是，在中，以便代码进行大量使用的字符串\(或多线程代码\)的默认内存管理器可能不好地执行。  本主题介绍如何重写 `CStringT`默认内存管理行为，创建为任务专门优化的分配器手头。  
  
-   [自定义字符串管理器\(基本方法的实现](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)  
  
-   [堆避免争用](../atl-mfc-shared/avoidance-of-heap-contention.md)  
  
-   [自定义字符串管理器\(高级方法的实现](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)  
  
-   [CFixedStringT:自定义字符串管理器的示例](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)  
  
## 请参阅  
 [CustomString示例](../top/visual-cpp-samples.md)