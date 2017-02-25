---
title: "树控件父项和子项 | Microsoft Docs"
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
  - "树控件中的子项"
  - "CTreeCtrl 类, 父项和子项"
  - "CTreeCtrl 中的父项"
  - "树控件, 父项和子项"
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 树控件父项和子项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在树控件 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 的所有列表项可以有子项，调用子项，与之关联。  有一个或多个子项的项调用父项。  子项在其父项目下显示、缩进指示它是辅助给父级。  没有父级的项位于层次结构顶部和调用根项。  
  
 在任意给定时间，子项父项列表的状态都可以展开或折叠。  在展开时，子状态项在父项目下显示。  当折叠时，子项就不会显示。  列表会自动切换在折叠和展开状态之间，当用户双击父项或时，具有 **TVS\_HASBUTTONS**，则父样式，那么，当用户单击按钮与父项。  应用程序可以展开或折叠子项可通过使用 [展开](../Topic/CTreeCtrl::Expand.md) 成员函数。  
  
 您添加一项。树控件通过调用成员函数。[InsertItem](../Topic/CTreeCtrl::InsertItem.md) 此函数返回 **HTREEITEM** 类型的句柄，唯一标识项。  在添加项时，必须指定新的父项的句柄。  如果指定 **NULL** 或 **TVI\_ROOT** 值而不是父项中处理 [TVINSERTSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb773452) 结构或 `hParent` 参数，该项将添加为根项。  
  
 子项，当父项的列表将展开或折叠时，树控件发送通知消息。[TVN\_ITEMEXPANDING](http://msdn.microsoft.com/library/windows/desktop/bb773537) 通知提供了机会阻止更改或设置依赖于子列表项状态父项的所有特性。  在将列表的状态后，树控件发送通知消息。[TVN\_ITEMEXPANDED](http://msdn.microsoft.com/library/windows/desktop/bb773533)  
  
 如果子项列表展开时，则缩进相对于父项。  使用 [GetIndent](../Topic/CTreeCtrl::GetIndent.md) 成员函数，则可以设置数量缩进使用 [SetIndent](../Topic/CTreeCtrl::SetIndent.md) 成员函数或检索当前量。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)