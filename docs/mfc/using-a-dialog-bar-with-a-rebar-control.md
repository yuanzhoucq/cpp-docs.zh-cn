---
title: "对 Rebar 控件使用对话栏 | Microsoft Docs"
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
  - "WM_EX_TRANSPARENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "对话栏, 用于 rebar 带区"
  - "rebar 控件, 对话栏"
  - "WS_EX_TRANSPARENT 样式"
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 对 Rebar 控件使用对话栏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如 [Rebar 和带区控件](../mfc/rebar-controls-and-bands.md)所述，每个带区只能包含一个子窗口 \(或控件\)。  如果希望多带区，每一子窗口可能是有限的。  方便工作区是创建具有多个控件的对话栏位资源比添加 rebar 带区 \(包含\) 到对话栏 rebar 控件。  
  
 通常，如果需要，对话栏显示带透明，将对话栏对象的 **WS\_EX\_TRANSPARENT** 扩展样式。  但是，**WS\_EX\_TRANSPARENT** 与适当对话栏，因为绘制背景的某些问题，您需要完成额外的工作有获得预期效果。  
  
 以下过程详细说明的必要步骤实现透明，而无需使用 **WS\_EX\_TRANSPARENT** 扩展样式。  
  
### 若要实现在 rebar 的一个透明对话栏中结合  
  
1.  使用 [添加类"对话框](../mfc/reference/adding-an-mfc-class.md)中，添加一个新类 \(例如，`CMyDlgBar`\) 实现对话栏对象。  
  
2.  将 `WM_ERASEBKGND` 消息的处理程序。  
  
3.  在新的处理程序，请修改现有代码以匹配以下示例：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/CPP/using-a-dialog-bar-with-a-rebar-control_1.cpp)]  
  
4.  将 `WM_MOVE` 消息的处理程序。  
  
5.  在新的处理程序，请修改现有代码以匹配以下示例：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/CPP/using-a-dialog-bar-with-a-rebar-control_2.cpp)]  
  
 新处理程序转发 `WM_ERASEBKGND` 消息到父窗口并强制重新绘制数据对话栏的透明度，在对话栏对象移动时间。  
  
## 请参阅  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控件](../mfc/controls-mfc.md)