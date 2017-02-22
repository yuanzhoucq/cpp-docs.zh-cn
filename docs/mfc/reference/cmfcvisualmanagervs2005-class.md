---
title: "CMFCVisualManagerVS2005 Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCVisualManagerVS2005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManagerVS2005 class"
ms.assetid: ea39b9ae-327e-4a51-bce7-dc84c78f005b
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCVisualManagerVS2005 Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCVisualManagerVS2005` 为应用程序Microsoft Visual Studio 2005外观。  
  
## 语法  
  
```  
class CMFCVisualManagerVS2005 : public CMFCVisualManagerOffice2003  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCVisualManagerVS2005::GetDockingTabsBordersSize](../Topic/CMFCVisualManagerVS2005::GetDockingTabsBordersSize.md)|框架调用此方法，该方法绘制停靠和选项卡式窗格。  （重写 [CMFCVisualManager::GetDockingTabsBordersSize](../Topic/CMFCVisualManager::GetDockingTabsBordersSize.md)。）|  
|[CMFCVisualManagerVS2005::GetMDITabsBordersSize](../Topic/CMFCVisualManagerVS2005::GetMDITabsBordersSize.md)|在它绘制窗口之前，框架调用此方法来确定MDITabs窗口的边框大小。  （重写 [CMFCVisualManager::GetMDITabsBordersSize](../Topic/CMFCVisualManager::GetMDITabsBordersSize.md)。）|  
|[CMFCVisualManagerVS2005::GetPropertyGridGroupColor](../Topic/CMFCVisualManagerVS2005::GetPropertyGridGroupColor.md)|（重写 [CMFCVisualManagerOffice2003::GetPropertyGridGroupColor](../Topic/CMFCVisualManagerOffice2003::GetPropertyGridGroupColor.md)。）|  
|[CMFCVisualManagerVS2005::GetTabFrameColors](../Topic/CMFCVisualManagerVS2005::GetTabFrameColors.md)|（重写 [CMFCVisualManagerOffice2003::GetTabFrameColors](../Topic/CMFCVisualManagerOffice2003::GetTabFrameColors.md)。）|  
|[CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons](../Topic/CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons.md)|返回"自动隐藏"按钮是否在当前视觉管理器重叠。  （重写 [CMFCVisualManager::HasOverlappedAutoHideButtons](../Topic/CMFCVisualManager::HasOverlappedAutoHideButtons.md)。）|  
|[CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder.md)|（重写 [CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder.md)。）|  
|[CMFCVisualManagerVS2005::OnDrawCaptionButton](../Topic/CMFCVisualManagerVS2005::OnDrawCaptionButton.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawCaptionButton`。）|  
|[CMFCVisualManagerVS2005::OnDrawPaneCaption](../Topic/CMFCVisualManagerVS2005::OnDrawPaneCaption.md)|（重写 [CMFCVisualManagerOffice2003::OnDrawPaneCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawPaneCaption.md)。）|  
|[CMFCVisualManagerVS2005::OnDrawSeparator](../Topic/CMFCVisualManagerVS2005::OnDrawSeparator.md)|（重写 [CMFCVisualManagerOffice2003::OnDrawSeparator](../Topic/CMFCVisualManagerOffice2003::OnDrawSeparator.md)。）|  
|[CMFCVisualManagerVS2005::OnDrawTab](../Topic/CMFCVisualManagerVS2005::OnDrawTab.md)|（重写 [CMFCVisualManagerOffice2003::OnDrawTab](../Topic/CMFCVisualManagerOffice2003::OnDrawTab.md)。）|  
|[CMFCVisualManagerVS2005::OnDrawToolBoxFrame](../Topic/CMFCVisualManagerVS2005::OnDrawToolBoxFrame.md)|（重写 [CMFCVisualManager::OnDrawToolBoxFrame](../Topic/CMFCVisualManager::OnDrawToolBoxFrame.md)。）|  
|[CMFCVisualManagerVS2005::OnEraseTabsArea](../Topic/CMFCVisualManagerVS2005::OnEraseTabsArea.md)|（重写 [CMFCVisualManagerOffice2003::OnEraseTabsArea](../Topic/CMFCVisualManagerOffice2003::OnEraseTabsArea.md)。）|  
|[CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground.md)|（重写 [CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground.md)。）|  
|[CMFCVisualManagerVS2005::OnFillHighlightedArea](../Topic/CMFCVisualManagerVS2005::OnFillHighlightedArea.md)|（重写 [CMFCVisualManagerOffice2003::OnFillHighlightedArea](../Topic/CMFCVisualManagerOffice2003::OnFillHighlightedArea.md)。）|  
|[CMFCVisualManagerVS2005::OnFillMiniFrameCaption](../Topic/CMFCVisualManagerVS2005::OnFillMiniFrameCaption.md)|（重写 `CMFCVisualManagerOfficeXP::OnFillMiniFrameCaption`。）|  
|[CMFCVisualManagerVS2005::OnUpdateSystemColors](../Topic/CMFCVisualManagerVS2005::OnUpdateSystemColors.md)|（重写 [CMFCVisualManagerOffice2003::OnUpdateSystemColors](../Topic/CMFCVisualManagerOffice2003::OnUpdateSystemColors.md)。）|  
  
## 备注  
 使用CMFCVisualManagerVS2005选件类更改应用程序的视觉外观类似于 [!INCLUDE[vsprvsext](../../mfc/reference/includes/vsprvsext_md.md)]。  
  
 所有这些选件类的成员是从此选件类的上级派生的虚函数，[CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)。  
  
## 示例  
 下面的示例演示如何使用视觉管理器与2005。  此代码段是 [桌面通知演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#9](../../mfc/reference/codesnippet/CPP/cmfcvisualmanagervs2005-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)  
  
 [CMFCVisualManagerVS2005](../../mfc/reference/cmfcvisualmanagervs2005-class.md)  
  
## 要求  
 **标头:** afxvisualmanagervs2005.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerOfficeXP Class](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)   
 [CMFCVisualManagerWindows Class](../../mfc/reference/cmfcvisualmanagerwindows-class.md)   
 [CMFCVisualManagerOffice2003 Class](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)   
 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)