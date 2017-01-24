---
title: "与用户界面对象关联的消息类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.uiobject.msgs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "消息类型和用户界面对象"
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 与用户界面对象关联的消息类型
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下表显示了使用的对象类型以及与它们关联的消息类型。  
  
### 用户界面对象及关联的消息  
  
|对象 ID|消息|  
|-----------|--------|  
|类名，表示包含窗口|适合 [CWnd](../../mfc/reference/cwnd-class.md) 导出类的 Windows 消息：对话框、窗口、子窗口、MDI 子窗口或最顶端框架窗口。|  
|菜单或快捷键标识符|-   **COMMAND** 消息（执行程序函数）。<br />-   **UPDATE\_COMMAND\_UI** 消息（动态更新菜单项）。|  
|控件标识符|选定控件类型的控件通知消息。|  
  
## 请参阅  
 [将消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)