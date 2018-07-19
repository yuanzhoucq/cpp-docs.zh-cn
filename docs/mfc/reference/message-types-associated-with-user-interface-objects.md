---
title: 消息与用户界面对象关联的类型 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.uiobject.msgs
dev_langs:
- C++
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7ecc948910dd618f343134b0e9e3133539d9e1f
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335475"
---
# <a name="message-types-associated-with-user-interface-objects"></a>与用户界面对象关联的消息类型
下表显示了类型的对象配合使用，并与之相关联的消息的类型。  
  
### <a name="user-interface-objects-and-associated-messages"></a>用户界面对象和关联的消息  
  
|对象 ID|消息|  
|---------------|--------------|  
|表示包含窗口的类名称|Windows 消息适合于[CWnd](../../mfc/reference/cwnd-class.md)-派生的类: 对话框、 窗口、 子窗口、 MDI 子窗口或最顶层框架窗口。|  
|菜单或快捷键标识符|命令消息 （执行程序函数）。<br />-UPDATE_COMMAND_UI 消息 （动态更新菜单项）。|  
|控件标识符|选定的控件类型的控件通知消息。|  
  
## <a name="see-also"></a>请参阅  
 [消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)
