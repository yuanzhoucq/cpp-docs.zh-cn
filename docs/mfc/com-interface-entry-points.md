---
title: "COM 接口入口点 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM 接口, 入口点"
  - "入口点, COM 接口"
  - "MFC COM, COM 接口入口点"
  - "MFC, 管理状态数据"
  - "OLE, 接口入口点"
  - "状态管理, OLE/COM 接口"
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# COM 接口入口点
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于 COM 接口的成员函数，则调用导出的接口的方法时，请使用 [METHOD\_PROLOGUE](../Topic/METHOD_PROLOGUE.md) 宏保持适当的全局状态。  
  
 通常，实现的 `CCmdTarget`接口的成员函数 \- 派生的对象中使用此宏提供 `pThis` 指针的自动初始化。  例如：  
  
 [!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/CPP/com-interface-entry-points_1.cpp)]  
  
 有关其他信息，请参见位于 MFC\/OLE **IUnknown** 实现的 [技术说明 38](../mfc/tn038-mfc-ole-iunknown-implementation.md)。  
  
 `METHOD_PROLOGUE` 宏定义如下：  
  
 `#define METHOD_PROLOGUE(theClass, localClass) \`  
  
 `theClass* pThis = \`  
  
 `((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \`  
  
 `AFX_MANAGE_STATE(pThis->m_pModuleState) \`  
  
 与管理全局状态相关的宏进行部分是：  
  
 `AFX_MANAGE_STATE( pThis->m_pModuleState )`  
  
 在表达式中，*m\_pModuleState* 假定是包含对象的成员变量。  当对象实例化时，它由 `CCmdTarget` 基类实现并初始化为适当的值的 `COleObjectFactory`。  
  
## 请参阅  
 [管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)