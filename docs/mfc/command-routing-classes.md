---
title: "命令传送类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.command
dev_langs: C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c7e49c92b909abb01f3daec9e16f0e08b2a31c89
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="command-routing-classes"></a>命令传送类
当用户通过用鼠标选择菜单或控件条按钮与应用程序交互时，应用程序会将来自受影响的用户界面对象的消息发送到合适的命令目标对象。 命令目标类派生自`CCmdTarget`包括[CWinApp](../mfc/reference/cwinapp-class.md)， [CWnd](../mfc/reference/cwnd-class.md)， [CDocTemplate](../mfc/reference/cdoctemplate-class.md)， [CDocument](../mfc/reference/cdocument-class.md)， [CView](../mfc/reference/cview-class.md)，并从这些类派生。 框架支持自动命令传送，以便让命令可以由应用程序中当前处于活动状态的最合适的对象处理。  
  
 类的对象`CCmdUI`将传递到命令目标的更新命令 UI ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) 处理程序，以允许您更新特定命令的用户界面的状态 （例如，为检查或删除从菜单项检查）。 您可调用 `CCmdUI` 对象的成员函数以更新 UI 对象的状态。 无论与特定命令关联的 UI 对象是菜单项、按钮还是这两者，此过程都是相同。  
  
 [CCmdTarget](../mfc/reference/ccmdtarget-class.md)  
 充当可接收和响应消息的所有对象类的基类的服务。  
  
 [CCmdUI](../mfc/reference/ccmdui-class.md)  
 提供用于更新用户界面对象（如菜单项或控件条按钮）的编程接口。 命令目标对象启用、禁用、检查和/或清除带有此对象的用户界面对象。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

