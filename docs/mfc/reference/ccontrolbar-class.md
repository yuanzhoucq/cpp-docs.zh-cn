---
title: "CControlBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CControlBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CControlBar class"
  - "control bars [C++], 基类"
  - "dialog bars, 基类"
  - "OLE resize bars"
  - "OLE resize bars, 基类"
  - "状态栏, 基类"
  - "工具栏 [C++], 基类"
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CControlBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控件条的基类 [CStatusBar](../../mfc/reference/cstatusbar-class.md)、[CToolBar](../../mfc/reference/ctoolbar-class.md)、[CDialogBar](../../mfc/reference/cdialogbar-class.md)、[CReBar](../../mfc/reference/crebar-class.md)和 [COleResizeBar](../../mfc/reference/coleresizebar-class.md)。  
  
## 语法  
  
```  
class CControlBar : public CWnd  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|描述|  
|--------|--------|  
|[CControlBar::CControlBar](../Topic/CControlBar::CControlBar.md)|构造 `CControlBar` 对象。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CControlBar::CalcDynamicLayout](../Topic/CControlBar::CalcDynamicLayout.md)|返回一个动态控件条的范围作为 [CSize](../../atl-mfc-shared/reference/csize-class.md) 对象。|  
|[CControlBar::CalcFixedLayout](../Topic/CControlBar::CalcFixedLayout.md)|返回控件条的范围作为 [CSize](../../atl-mfc-shared/reference/csize-class.md) 对象。|  
|[CControlBar::CalcInsideRect](../Topic/CControlBar::CalcInsideRect.md)|返回控制条区域的当前尺寸；包括边框。|  
|[CControlBar::DoPaint](../Topic/CControlBar::DoPaint.md)|呈现控件条的边框和手柄。|  
|[CControlBar::DrawBorders](../Topic/CControlBar::DrawBorders.md)|呈现控件条的边框。|  
|[CControlBar::DrawGripper](../Topic/CControlBar::DrawGripper.md)|呈现控件条的抓手。|  
|[CControlBar::EnableDocking](../Topic/CControlBar::EnableDocking.md)|允许控制条停靠或是浮动。|  
|[CControlBar::GetBarStyle](../Topic/CControlBar::GetBarStyle.md)|检索控件条样式设置。|  
|[CControlBar::GetBorders](../Topic/CControlBar::GetBorders.md)|检索控件条的边框值。|  
|[CControlBar::GetCount](../Topic/CControlBar::GetCount.md)|返回控件条中非`HWND` 元素数。|  
|[CControlBar::GetDockingFrame](../Topic/CControlBar::GetDockingFrame.md)|返回指向控制条停靠的帧。|  
|[CControlBar::IsFloating](../Topic/CControlBar::IsFloating.md)|如果相关控件条是一个未静差控件条，返回一个非零值。|  
|[CControlBar::OnUpdateCmdUI](../Topic/CControlBar::OnUpdateCmdUI.md)|调用命令 UI 处理程序。|  
|[CControlBar::SetBarStyle](../Topic/CControlBar::SetBarStyle.md)|修改控件条样式设置。|  
|[CControlBar::SetBorders](../Topic/CControlBar::SetBorders.md)|设置控件条的边框值。|  
|[CControlBar::SetInPlaceOwner](../Topic/CControlBar::SetInPlaceOwner.md)|更改控件条的就地所有者。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[CControlBar::m\_bAutoDelete](../Topic/CControlBar::m_bAutoDelete.md)|如果非零，`CControlBar` 对象在窗口控制条被销毁时被删除。|  
|[CControlBar::m\_pInPlaceOwner](../Topic/CControlBar::m_pInPlaceOwner.md)|控件条的就地所有者。|  
  
## 备注  
 控件条通常对齐框架窗口的左侧或右侧的窗口。  它可以包含可以是任何 `HWND`的子项基于控件，是 windows 生成并响应 windows 消息，或非`HWND`\-基本项，不是 windows 和应用程序代码或结构代码管理。  列表框和编辑控件是 `HWND`的示例基于控件；状态栏窗格和位图按钮是非`HWND`的示例基于控件。  
  
 控制条窗口通常是父框架窗口的子窗口并通常是同级对客户端视图或框架窗口的 MDI 客户端。  `CControlBar` 对象使用有关父窗口的客户端矩形的信息来确定自身。  然后通知父窗口关于在父窗口的客户端区有多少空间仍未分配。  
  
 有关 `CControlBar` 的更多信息，请参见。  
  
-   [控件条](../../mfc/control-bars.md)  
  
-   [技术说明 31:控制条](../../mfc/tn031-control-bars.md)。  
  
-   知识库文章 Q242577:PRB:更新命令 UI 处理程序不使用菜单的附加到对话框  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CControlBar`  
  
## 要求  
 **页眉：**afxext.h  
  
## 请参阅  
 [MFC 示例 CTRLBARS](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CToolBar Class](../../mfc/reference/ctoolbar-class.md)   
 [CDialogBar Class](../../mfc/reference/cdialogbar-class.md)   
 [CStatusBar Class](../../mfc/reference/cstatusbar-class.md)   
 [CReBar Class](../../mfc/reference/crebar-class.md)