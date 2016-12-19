---
title: "隔离 MFC 公共控件库 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC, 公共控件库"
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 隔离 MFC 公共控件库
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

公共控库件现在独立于 MFC 库，允许不同的模块 \(例如 DLL\) 用户使用常用控件库的不同版本通过manifests指定版本。  
  
 MFC 应用程序 \(MFC 或调用用户代码\) 调用公共控件 API 库通过包装功能名称 `Afx`*FunctionName*，其中 *FunctionName* 为公共控件 API 的名称。  这些包装函数在 afxcomctl32.h 和 afxcomctl32.inl 定义。  
  
 可以使用 [AFX\_COMCTL32\_IF\_EXISTS](../Topic/AFX_COMCTL32_IF_EXISTS.md) [AFX\_COMCTL32\_IF\_EXISTS2](../Topic/AFX_COMCTL32_IF_EXISTS2.md) 和宏 \(在 afxcomctl32.h 定义\) 确定公共控件库是否实现某些 API 而不是调用 [GetProcAddress](../build/getprocaddress.md)。  
  
 从技术上说，通过包装类，`CComCtlWrapper` \(定义在 afxcomctl32.h\)调用公共控件 API 库。  `CComCtlWrapper` 负责加载和卸载 comctl32.dll。  MFC 模块状态包含指向 `CComCtlWrapper`实例的指针。  可以使用 `afxComCtlWrapper` 宏访问包装器类。  
  
 注意直接 从 MFC 应用程序或用户 DLL调用公共控件 API，\(不使用 MFC 包装函数\) 在许多情况下将发生，因为 MFC 应用程序或用户 DLL将公共控件库请求绑定到其清单。  但是，MFC 代码必须使用包装，因为可能会使用不同的公用控件库版本，调用用户 DLL 。