---
title: "树控件拖放操作 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CTreeCtrl 类, 拖放操作"
  - "拖放, CTreeCtrl"
  - "树控件, 拖放操作"
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 树控件拖放操作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

树控件 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 发送通知，当用户开始拖动项。   [TVN\_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773504) 控件发送通知消息，当用户以鼠标左键和 [TVN\_BEGINRDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773509) 通知消息时开始拖动项，当用户以右键时开始拖动。  可以防止树控件发送这些通知使树控件 **TVS\_DISABLEDRAGDROP** 样式。  
  
 可以获取的图像在拖动操作过程演示通过调用 [CreateDragImage](../Topic/CTreeCtrl::CreateDragImage.md) 成员函数。  树控件创建基于项标签的一个将的位图拖动。  然后生成控件树列表，位图图像添加到该对象，并返回指向 [CImageList](../mfc/reference/cimagelist-class.md) 对象。  
  
 必须提供实际上将项的代码。  这通常需要使用图像列表的函数将的和功能处理 [WM\_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) [WM\_LBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms645608) \(和或 [WM\_RBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms646243)\) 发送，在拖动操作开始之后。  有关图像列表功能的更多信息，请参见" *MFC 参考"中的* [CImageList](../mfc/reference/cimagelist-class.md) [图像列表](http://msdn.microsoft.com/library/windows/desktop/bb761389) 和 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中。  有关将树的更多信息，请参见 [将树视图项](http://msdn.microsoft.com/library/windows/desktop/bb760017)控制项，还在 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)]中。  
  
 如果在树控件的项是拖放操作的目标，您需要知道鼠标光标时在目标项。  通过查看 [HitTest](../Topic/CTreeCtrl::HitTest.md) 调用成员函数。  在指定点和整数或包含的鼠标光标当前坐标 [TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448) 结构的地址。  当函数返回时，将整数或结构包含指示鼠标光标位置的标志与树控件相关。  如果光标通过在树控件中选择项，结构包含项的句柄。  
  
 可以指示项为拖放操作的目标。通过调用 [SetItem](../Topic/CTreeCtrl::SetItem.md) 成员函数将状态转换为 `TVIS_DROPHILITED` 值。  具有此状态的项位于样式绘制以指示拖放目标。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)