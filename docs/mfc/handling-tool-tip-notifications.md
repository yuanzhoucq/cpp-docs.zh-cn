---
title: "处理工具提示通知 | Microsoft Docs"
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
  - "CToolBarCtrl 类, 处理通知"
  - "通知, 工具提示"
  - "工具提示 [C++], 通知"
  - "TOOLTIPTEXT 结构"
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 处理工具提示通知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当指定 `TBSTYLE_TOOLTIPS` 样式时，创建工具栏并管理工具提示控件。  工具提示所描述包含工具栏按钮的行文本的小型弹出窗口。  工具提示仅用户隐藏，工具栏按钮上和叶节点中将光标放在它只为大约一半一秒。  工具提示在游标的显示。  
  
 在工具提示中显示的 **TTN\_NEEDTEXT** 通知消息之前，发送到工具栏的所有者窗口按钮检索的描述性文本。  如果工具栏的所有者窗口是窗口中，工具提示会显示 `CFrameWnd`，而没有任何特别小心，因为 `CFrameWnd` 具有 **TTN\_NEEDTEXT** 通知的默认处理程序。  如果工具栏的所有者窗口未从 `CFrameWnd`派生，例如对话框窗体视图，或必须将输入为所有者窗口的消息映射和提供消息映射处理程序的通知。  对所有者窗口的消息映射的类型如下所示：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/CPP/handling-tool-tip-notifications_1.cpp)]  
  
## 备注  
 `memberFxn`  
 要调用的，当文本用于此按钮所需的成员函数。  
  
 请注意工具提示的 id 始终为 0。  
  
 除了 **TTN\_NEEDTEXT** 通知外，工具提示控件可以发送下通知为工具栏控件：  
  
|通知|含义|  
|--------|--------|  
|**TTN\_NEEDTEXTA**|工具提示控件需要 ASCII 文本 \(仅适用于 Windows 95\)|  
|**TTN\_NEEDTEXTW**|工具提示控件需要 UNICODE 文本 \(仅限 Windows NT\)|  
|**TBN\_HOTITEMCHANGE**|指示热 \(突出显示\) 的项更改。|  
|**NM\_RCLICK**|指示用户右击该按钮。|  
|**TBN\_DRAGOUT**|指示用户单击按钮并将指针移到按钮。  它允许应用程序实现从工具栏按钮的拖放。  当收到通知时，此应用程序将启动拖放操作。|  
|**TBN\_DROPDOWN**|指示用户单击 **TBSTYLE\_DROPDOWN** 使用样式的按钮。|  
|**TBN\_GETOBJECT**|指示用户移到使用 **TBSTYLE\_DROPPABLE** 样式的按钮上方。|  
  
 有关一个示例处理程序函数和更多有关启用工具提示，请参见 [工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)。  
  
## 请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)