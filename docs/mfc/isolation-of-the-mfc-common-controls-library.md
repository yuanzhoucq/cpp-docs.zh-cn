---
title: "隔离 MFC 公共控件库 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MFC, Common Controls library
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: effc8b927aadc821e189837ab3506f05cb426e93
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>隔离 MFC 公共控件库
公用控件库现在在 MFC 中处于隔离状态，通过在其清单中指定版本，允许不同模块（如用户 DLL）使用不同版本的公用控件库。  
  
 MFC 应用程序 （或由 MFC 调用用户代码） 调用公共控件库 Api 通过包装函数名为`Afx` *FunctionName*，其中*FunctionName*是一个常见的名称控件 API。 这些包装器函数是在 afxcomctl32.h 和 afxcomctl32.inl 中定义的。  
  
 你可以使用[AFX_COMCTL32_IF_EXISTS](reference/run-time-object-model-services.md#afx_comctl32_if_exists)和[AFX_COMCTL32_IF_EXISTS2](reference/run-time-object-model-services.md#afx_comctl32_if_exists2)宏 (在中定义 afxcomctl32.h)，以确定公共控件库是否实现而不是调用某些 API[GetProcAddress](../build/getprocaddress.md)。  
  
 从技术上说，您可以通过包装器类 `CComCtlWrapper`（在 afxcomctl32.h 中定义）调用公共控件库 API。 `CComCtlWrapper` 还负责加载和卸载 comctl32.dll。 MFC 模块状态包含指向 `CComCtlWrapper` 实例的指针。 您可以使用 `afxComCtlWrapper` 宏来访问包装器类。  
  
 请注意，直接（不使用 MFC 包装器函数）从 MFC 应用程序或用户 DLL 调用公共控件 API 在大多数情况下有用，因为 MFC 应用程序或用户 DLL 将绑定到其在清单中请求的公共控件库。 但是，MFC 代码本身必须使用包装器，因为 MFC 代码可能是从使用不同公共控件库版本的用户 DLL 调用的。

