---
title: "CMFCDropDownToolBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCDropDownToolBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDropDownToolBar class"
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
caps.latest.revision: 37
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 39
---
# CMFCDropDownToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

显示的工具栏当用户按住顶级工具栏按钮。  
  
## 语法  
  
```  
class CMFCDropDownToolBar : public CMFCToolBar  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](../Topic/CMFCDropDownToolBar::AllowShowOnPaneMenu.md)|（重写 `CPane::AllowShowOnPaneMenu`。）|  
|[CMFCDropDownToolBar::LoadBitmap](../Topic/CMFCDropDownToolBar::LoadBitmap.md)|（重写 [CMFCToolBar::LoadBitmap](../Topic/CMFCToolBar::LoadBitmap.md)。）|  
|[CMFCDropDownToolBar::LoadToolBar](../Topic/CMFCDropDownToolBar::LoadToolBar.md)|（重写 [CMFCToolBar::LoadToolBar](../Topic/CMFCToolBar::LoadToolBar.md)。）|  
|[CMFCDropDownToolBar::OnLButtonUp](../Topic/CMFCDropDownToolBar::OnLButtonUp.md)||  
|[CMFCDropDownToolBar::OnMouseMove](../Topic/CMFCDropDownToolBar::OnMouseMove.md)||  
|[CMFCDropDownToolBar::OnSendCommand](../Topic/CMFCDropDownToolBar::OnSendCommand.md)|（重写 `CMFCToolBar::OnSendCommand`。）|  
|[CMFCDropDownToolBar::OnUpdateCmdUI](../Topic/CMFCDropDownToolBar::OnUpdateCmdUI.md)|（重写 [CMFCToolBar::OnUpdateCmdUI](http://msdn.microsoft.com/zh-cn/571a38ab-2a56-4968-9796-273516126f80)。）|  
  
### 备注  
 `CMFCDropDownToolBar` 对象合并工具栏的可视外观与一个弹出菜单的行为。  当用户按和存放一个下拉式工具栏按钮\(请参见 [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)\)时，一下拉式工具栏显示，因此，用户可以选择按钮从下拉式工具栏滚动到并释放鼠标按钮。  在用户选择在下拉式工具栏后面的一个按钮，该按钮显示为在顶部的工具栏中当前按钮。  
  
 一下拉式工具栏无法自定义或停靠，因此，它不具有拖曳状态。  
  
 下面的插图显示了 `CMFCDropDownToolBar` 对象:  
  
 ![CMFCDropDownToolbar 示例](../../mfc/reference/media/cmfcdropdown.png "CMFCDropDown")  
  
 您创建一 `CMFCDropDownToolBar` 对象创建普通工具栏的方式\(请参见 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)）。  
  
 插入下拉式工具栏到父工具栏中:  
  
 1.  保留虚拟资源ID在父工具栏资源的按钮。  
  
 2.  创建包含下拉式工具栏上的某个 `CMFCDropDownToolBarButton` 对象\(有关更多信息，请参见 [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../Topic/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton.md)）。  
  
 3.  使用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)，请 `CMFCDropDownToolBarButton` 对象替换虚假的按钮。  
  
 有关工具栏按钮的更多信息，请参见 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  有关下拉式工具栏的示例，请参见示例项目VisualStudioDemo。  
  
## 示例  
 下面的示例在 `CMFCDropDownToolBar` 选件类演示如何使用 `Create` 方法。  此代码段是 [Visual Studio演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/CPP/cmfcdropdowntoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/CPP/cmfcdropdowntoolbar-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)  
  
## 要求  
 **标头:** afxdropdowntoolbar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::Create](../Topic/CMFCToolBar::Create.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)   
 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)