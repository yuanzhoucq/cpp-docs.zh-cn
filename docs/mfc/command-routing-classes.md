---
title: "命令传送类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.command"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令传送, 类"
  - "MFC, 命令传送"
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 命令传送类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当用户使用鼠标通过选择菜单或控件条按钮与应用程序交互时，您的应用程序发送来自受影响的用户界面对象的信息到适当的命令目标对象。  命令目标类来自 `CCmdTarget` 包括 [CWinApp](../mfc/reference/cwinapp-class.md), [CWnd](../mfc/reference/cwnd-class.md), [CDocTemplate](../mfc/reference/cdoctemplate-class.md), [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md),以及从它们派生的类。  框架支持自动的路由命令，以便命令可以由应用程序中当前活动的最适当的对象处理。  
  
 类 `CCmdUI` 对象传递到命令目标的更新 UI \([ON\_UPDATE\_COMMAND\_UI](../Topic/ON_UPDATE_COMMAND_UI.md)\) 句柄来允许您针对特定命令更新用户界面的状态 \(例如，从菜单项查看或移除检查\)。  调用 `CCmdUI` 对象的成员函数来更新 UI 对象的状态。  此过程是相同的，无论与特定命令关联的用户界面对象是菜单项或按钮或两者。  
  
 [CCmdTarget](../mfc/reference/ccmdtarget-class.md)  
 用作所有对象类的基类服务，可接收和响应消息。  
  
 [CCmdUI](../mfc/reference/ccmdui-class.md)  
 为更新用户界面对象提供可编程的接口，如菜单项或控件条按钮。  此命令目标对象启用，禁用，检查，并\/或 清除用户界面对象及此对象。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)