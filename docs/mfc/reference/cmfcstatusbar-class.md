---
title: "CMFCStatusBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCStatusBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCStatusBar class"
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
caps.latest.revision: 36
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCStatusBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCStatusBar` 选件类实现状态栏类似于 `CStatusBar` 选件类。  但是，`CMFCStatusBar` 选件类具有 `CStatusBar` 选件类未提供的功能，例如能够为显示图像、动画和进度栏;并能够响应鼠标双击。  
  
## 语法  
  
```  
class CMFCStatusBar : public CPane  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCStatusBar::CalcFixedLayout](../Topic/CMFCStatusBar::CalcFixedLayout.md)|（重写 [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)。）|  
|[CMFCStatusBar::CommandToIndex](../Topic/CMFCStatusBar::CommandToIndex.md)||  
|[CMFCStatusBar::Create](../Topic/CMFCStatusBar::Create.md)|创建一个控件条并将它附加到 [CPane](../../mfc/reference/cpane-class.md) 对象。  （重写 [CPane::Create](../Topic/CPane::Create.md)。）|  
|[CMFCStatusBar::CreateEx](../Topic/CMFCStatusBar::CreateEx.md)|创建一个控件条并将它附加到 [CPane](../../mfc/reference/cpane-class.md) 对象。  （重写 [CPane::CreateEx](../Topic/CPane::CreateEx.md)。）|  
|[CMFCStatusBar::DoesAllowDynInsertBefore](../Topic/CMFCStatusBar::DoesAllowDynInsertBefore.md)|确定另一个窗格是否可以动态插入此窗格和父框架。  （重写 [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md)。）|  
|[CMFCStatusBar::EnablePaneDoubleClick](../Topic/CMFCStatusBar::EnablePaneDoubleClick.md)|启用或禁用处理在状态栏上双击。|  
|[CMFCStatusBar::EnablePaneProgressBar](../Topic/CMFCStatusBar::EnablePaneProgressBar.md)|显示在指定的窗格的一个进度栏。|  
|[CMFCStatusBar::GetCount](../Topic/CMFCStatusBar::GetCount.md)|返回窗格数在状态栏中。|  
|[CMFCStatusBar::GetDrawExtendedArea](../Topic/CMFCStatusBar::GetDrawExtendedArea.md)||  
|[CMFCStatusBar::GetExtendedArea](../Topic/CMFCStatusBar::GetExtendedArea.md)||  
|[CMFCStatusBar::GetItemID](../Topic/CMFCStatusBar::GetItemID.md)||  
|[CMFCStatusBar::GetItemRect](../Topic/CMFCStatusBar::GetItemRect.md)||  
|[CMFCStatusBar::GetPaneInfo](../Topic/CMFCStatusBar::GetPaneInfo.md)||  
|[CMFCStatusBar::GetPaneProgress](../Topic/CMFCStatusBar::GetPaneProgress.md)||  
|[CMFCStatusBar::GetPaneStyle](../Topic/CMFCStatusBar::GetPaneStyle.md)|返回窗格样式。  （重写 [CBasePane::GetPaneStyle](../Topic/CBasePane::GetPaneStyle.md)。）|  
|[CMFCStatusBar::GetPaneText](../Topic/CMFCStatusBar::GetPaneText.md)||  
|[CMFCStatusBar::GetPaneWidth](../Topic/CMFCStatusBar::GetPaneWidth.md)|返回宽度，以像素，状态栏中指定的窗格。|  
|[CMFCStatusBar::GetTipText](../Topic/CMFCStatusBar::GetTipText.md)|返回状态栏中指定的窗格的工具提示文本。|  
|[CMFCStatusBar::InvalidatePaneContent](../Topic/CMFCStatusBar::InvalidatePaneContent.md)|无效指定的窗格并重画其内容。|  
|[CMFCStatusBar::PreCreateWindow](../Topic/CMFCStatusBar::PreCreateWindow.md)|调用由框架在Windows窗口中先前创建附加到此 `CWnd` 对象。  （重写 [CWnd::PreCreateWindow](../Topic/CWnd::PreCreateWindow.md)。）|  
|[CMFCStatusBar::SetDrawExtendedArea](../Topic/CMFCStatusBar::SetDrawExtendedArea.md)||  
|[CMFCStatusBar::SetIndicators](../Topic/CMFCStatusBar::SetIndicators.md)||  
|[CMFCStatusBar::SetPaneAnimation](../Topic/CMFCStatusBar::SetPaneAnimation.md)|动画分发到指定的窗格。|  
|[CMFCStatusBar::SetPaneBackgroundColor](../Topic/CMFCStatusBar::SetPaneBackgroundColor.md)|设置状态栏中指定的窗格的背景色。|  
|[CMFCStatusBar::SetPaneIcon](../Topic/CMFCStatusBar::SetPaneIcon.md)|设置状态栏中指定的窗格的指示器图标。|  
|[CMFCStatusBar::SetPaneInfo](../Topic/CMFCStatusBar::SetPaneInfo.md)||  
|[CMFCStatusBar::SetPaneProgress](../Topic/CMFCStatusBar::SetPaneProgress.md)|设置进度栏的活动进程状态栏中指定的窗格中。|  
|[CMFCStatusBar::SetPaneStyle](../Topic/CMFCStatusBar::SetPaneStyle.md)|设置窗格的样式。  （重写 [CBasePane::SetPaneStyle](../Topic/CBasePane::SetPaneStyle.md)。）|  
|[CMFCStatusBar::SetPaneText](../Topic/CMFCStatusBar::SetPaneText.md)||  
|[CMFCStatusBar::SetPaneTextColor](../Topic/CMFCStatusBar::SetPaneTextColor.md)|设置状态栏中指定的窗格的文本颜色。|  
|[CMFCStatusBar::SetPaneWidth](../Topic/CMFCStatusBar::SetPaneWidth.md)|设置在状态栏中指定的窗格的像素宽度。|  
|[CMFCStatusBar::SetTipText](../Topic/CMFCStatusBar::SetTipText.md)|设置状态栏中指定的窗格的工具提示文本。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCStatusBar::OnDrawPane](../Topic/CMFCStatusBar::OnDrawPane.md)|调用由框架，则重绘状态栏的窗格。|  
  
## 备注  
 下图显示状态栏以从 [状态栏演示示例](../../top/visual-cpp-samples.md) 应用程序的。  
  
 ![CMFCStatusBar 示例](../../mfc/reference/media/cmfcstatusbar.png "CMFCStatusBar")  
  
## 示例  
 下面的示例演示应用程序使用缩放在 `CMFCStatusBar` 选件类中的各种方法的局部变量。  这些变量在StatusBarDemoView.h声明。  主框架在MainFrm.h声明，文档在StatusBarDemoDoc.h声明，因此，视图。StatusBarDemoView.h声明。  此代码段是 [状态栏演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_1.h)]  
  
## 示例  
 下面的示例演示 `CMFCStatusBar` 对象演示如何获取引用传递介绍MainFrm.h的 `GetStatusBar` 然后调用方法从 `GetStatusBar` 方法的此方法在StatusBarDemoView.h。  此代码段是 [状态栏演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_2.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_3.h)]  
  
## 示例  
 下面的示例演示如何调用 `CMFCStatusBar` 选件类中的各种方法。StatusBarDemoView.cpp。  常数。MainFrm.h声明。  此示例演示如何设置图标，设置状态栏窗格的工具提示文本，显示在指定的窗格的一个进度栏，将动画分发到指定的窗格中，设置文本和状态栏窗格的宽度，并将进度栏的当前进度显示状态栏窗格中。  此代码段是 [状态栏演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_4.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_5.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_6.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_7.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_8.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_9.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)  
  
## 要求  
 **标头:** afxstatusbar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)   
 [CStatusBar Class](../../mfc/reference/cstatusbar-class.md)