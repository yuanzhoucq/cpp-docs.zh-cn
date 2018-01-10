---
title: "COM 接口入口点 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 010df3546a6ac2b6276281c39efdd76abd5ec222
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="com-interface-entry-points"></a>COM 接口入口点
对于 COM 接口的成员函数，使用[METHOD_PROLOGUE](com-interface-entry-points.md#method_prologue)宏维护适当的全局状态时调用导出接口的方法。  
  
 通常，由 `CCmdTarget` 派生的对象实现的接口的成员函数已使用此宏提供 `pThis` 指针的自动初始化。 例如:  
  
 [!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/cpp/com-interface-entry-points_1.cpp)]  
  
 有关其他信息，请参阅[技术说明 38](../mfc/tn038-mfc-ole-iunknown-implementation.md)有关 MFC/OLE **IUnknown**实现。  
  
 按如下方式定义 `METHOD_PROLOGUE` 宏：  
  
 `#define METHOD_PROLOGUE(theClass, localClass) \`  
  
 `theClass* pThis = \`  
  
 `((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \`  
  
 `AFX_MANAGE_STATE(pThis->m_pModuleState) \`  
  
 与管理全局状态相关的宏的部分是：  
  
 `AFX_MANAGE_STATE( pThis->m_pModuleState )`  
  
 在此表达式中， *m_pModuleState*被假定为包含对象的成员变量。 它由 `CCmdTarget` 基类实现，并在实例化对象时由 `COleObjectFactory` 初始化为适当的值。  
  
## <a name="see-also"></a>请参阅  
 [管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)

