---
title: "导出的 DLL 函数入口点 | Microsoft Docs"
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
  - "导出 DLL, 函数"
  - "MFC, 管理状态数据"
  - "状态管理, 导出的 DLL"
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 导出的 DLL 函数入口点
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于 DLL 的导出函数，则开关将 DLL 模块添加到调用的应用程序的 DLL 时，宏，请使用 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) 保持适当的全局状态。  
  
 当调用时，此宏将设置 `pModuleState`，指向包含全局数据对模块的 `AFX_MODULE_STATE` 结构的指针，作为函数的包含范围的余数的有效模块状态。  在离开包含宏的范围之后，上述的有效模块状态自动还原。  
  
 此交换通过构造在堆栈上的 **AFX\_MODULE\_STATE** 类实例来完成。  在其构造函数，此类获取一个指向当前模块状态并将其存储在成员变量，然后将 `pModuleState` 作为新的有效模块状态。  在此析构函数中，此类将其存储在成员变量的指针作为的有效模块状态。  
  
 如果有一个导出函数，例如启动在 DLL 的对话框的一个，需要以下代码添加到函数的开头：  
  
 [!code-cpp[NVC_MFCConnectionPoints#6](../mfc/codesnippet/CPP/exported-dll-function-entry-points_1.cpp)]  
  
 这将交换当前模块状态，从[AfxGetStaticModuleState](../Topic/AfxGetStaticModuleState.md)状态返回到当前作用域结束。  
  
 如果`AFX_MANAGE_STATE`宏没有使用会发生资源DLL中存在的问题。  默认情况下，MFC 使用主应用的资源句柄加载资源模板。  此模板实际存储在 DLL 。  根本原因是MFC的模块状态信息还没有被 `AFX_MANAGE_STATE` 宏切换。  资源句柄从 MFC 的模块状态恢复。  不使转换模块状态导致使用错误的资源句柄。  
  
 `AFX_MANAGE_STATE` 不需要放置到DLL的每个函数。  例如，`InitInstance` 可由应用程序的 MFC 代码调用，而无需 `AFX_MANAGE_STATE`，因为在 `InitInstance`之前 MFC自动切换模块状态然后切回在 `InitInstance` 返回之后。  上述情况同样适用于所有消息映射处理程序。  规则DLL实际上有一个特殊的主窗口过程在路由的任何消息之前自动切换模块状态。  
  
## 请参阅  
 [管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)