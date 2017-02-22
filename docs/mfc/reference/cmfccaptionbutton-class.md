---
title: "CMFCCaptionButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCCaptionButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCCaptionButton class"
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CMFCCaptionButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCCaptionButton` 选件类实现在停靠窗格或服务器框架窗口的标题栏中显示的按钮。  通常，框架自动创建声明按钮。  
  
## 语法  
  
```  
class CMFCCaptionButton : public CObject  
```  
  
## 成员  
  
### 构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCCaptionButton::CMFCCaptionButton](../Topic/CMFCCaptionButton::CMFCCaptionButton.md)|构造CMFCCaptionButton对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCCaptionButton::GetHit](../Topic/CMFCCaptionButton::GetHit.md)|返回此按钮表示的命令。|  
|[CMFCCaptionButton::GetIconID](../Topic/CMFCCaptionButton::GetIconID.md)|返回图像ID与按钮。|  
|[CMFCCaptionButton::GetRect](../Topic/CMFCCaptionButton::GetRect.md)|返回按钮占用的矩形。|  
|[CMFCCaptionButton::GetSize](../Topic/CMFCCaptionButton::GetSize.md)|返回按钮的宽度和高度。|  
|[CMFCCaptionButton::IsMiniFrameButton](../Topic/CMFCCaptionButton::IsMiniFrameButton.md)|指示标题栏高度是设置为要范围。|  
|[CMFCCaptionButton::Move](../Topic/CMFCCaptionButton::Move.md)|将按钮绘制位置和窗口显示状态。|  
|[CMFCCaptionButton::OnDraw](../Topic/CMFCCaptionButton::OnDraw.md)|绘制声明按钮。|  
|[CMFCCaptionButton::SetMiniFrameButton](../Topic/CMFCCaptionButton::SetMiniFrameButton.md)|设置标题栏的mini范围。|  
  
## 备注  
 可以从 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md) 派生选件类和使用受保护的方法，`AddButton`，添加标题按钮到要框架窗口。  
  
 CPaneFrameWnd.h定义声明按钮的两种类型的命令ID:  
  
-   `AFX_CAPTION_BTN_PIN`，显示固定按钮，当停靠窗格支持自动隐藏模式。  
  
-   `AFX_CAPTION_BTN_CLOSE`，显示 **关闭** 按钮，当窗格来关闭或隐藏。  
  
## 示例  
 下面的示例演示如何构造 `CMFCCaptionButton` 对象和设置标题栏的mini范围。  
  
 [!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/CPP/cmfccaptionbutton-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)  
  
## 要求  
 **标头:** afxcaptionbutton.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)