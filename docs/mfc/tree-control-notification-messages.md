---
title: "树控件通知消息 | Microsoft Docs"
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
  - "CTreeCtrl 类, 通知"
  - "消息, 通知"
  - "通知, CTreeCtrl"
  - "通知, 树控件"
  - "树控件, 通知消息"
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 树控件通知消息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

树控件 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 发送通知消息。**WM\_NOTIFY** 以下消息：  
  
|通知消息|说明|  
|----------|--------|  
|**TVN\_BEGINDRAG**|指示拖放操作的开始。|  
|**TVN\_BEGINLABELEDIT**|将通知开始就地编辑标签|  
|**TVN\_BEGINRDRAG**|使用鼠标右键，终止拖放操作的开始，|  
|**TVN\_DELETEITEM**|标志着特定中删除项|  
|**TVN\_ENDLABELEDIT**|信号的结束编辑标签|  
|**TVN\_GETDISPINFO**|请求树控件需要显示的项的信息。|  
|**TVN\_ITEMEXPANDED**|子项父项的列表展开或折叠的信号|  
|**TVN\_ITEMEXPANDING**|子项的父项列表会展开或折叠的信号|  
|**TVN\_KEYDOWN**|信号键盘事件|  
|**TVN\_SELCHANGE**|信号从中选择一项更改为另一个架构|  
|**TVN\_SELCHANGING**|指示选定项即将从一项变为另一项|  
|**TVN\_GETDISPINFO**|更新的信息通知为维护项|  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)