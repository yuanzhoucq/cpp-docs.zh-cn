---
title: "CMFCToolBarEditBoxButton Class | Microsoft Docs"
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
  - "OnDrawOnCustomizeList"
  - "OnDraw"
  - "CMFCToolBarEditBoxButton::OnDrawOnCustomizeList"
  - "CMFCToolBarEditBoxButton.SetACCData"
  - "CMFCToolBarEditBoxButton::OnDraw"
  - "OnCalculateSize"
  - "SetACCData"
  - "CMFCToolBarEditBoxButton"
  - "CMFCToolBarEditBoxButton::SetACCData"
  - "CMFCToolBarEditBoxButton::Serialize"
  - "CMFCToolBarEditBoxButton.OnDraw"
  - "CMFCToolBarEditBoxButton.OnDrawOnCustomizeList"
  - "CMFCToolBarEditBoxButton::OnCalculateSize"
  - "Serialize"
  - "CMFCToolBarEditBoxButton.Serialize"
  - "CMFCToolBarEditBoxButton.OnCalculateSize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarEditBoxButton class"
  - "OnCalculateSize method"
  - "OnDraw method"
  - "OnDrawOnCustomizeList method"
  - "Serialize method"
  - "SetACCData method"
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
caps.latest.revision: 28
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarEditBoxButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含编辑控件的工具栏按钮\([CEdit Class](../../mfc/reference/cedit-class.md)）。  
  
## 语法  
  
```  
class CMFCToolBarEditBoxButton : public CMFCToolBarButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](../Topic/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton.md)|构造 `CMFCToolBarEditBoxButton` 对象。|  
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarEditBoxButton::CanBeStretched](../Topic/CMFCToolBarEditBoxButton::CanBeStretched.md)|指定用户是否在自定义过程中拉伸按钮。  （重写 [CMFCToolBarButton::CanBeStretched](../Topic/CMFCToolBarButton::CanBeStretched.md)。）|  
|[CMFCToolBarEditBoxButton::CopyFrom](../Topic/CMFCToolBarEditBoxButton::CopyFrom.md)|复制另一个工具栏按钮的属性设置为当前按钮。  （重写 [CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md)。）|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::CreateEdit](../Topic/CMFCToolBarEditBoxButton::CreateEdit.md)|创建新在按钮的编辑控件。|  
|`CMFCToolBarEditBoxButton::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|[CMFCToolBarEditBoxButton::GetByCmd](../Topic/CMFCToolBarEditBoxButton::GetByCmd.md)|检索在具有指定的命令ID.的应用程序的第一 `CMFCToolBarEditBoxButton` 对象|  
|[CMFCToolBarEditBoxButton::GetContentsAll](../Topic/CMFCToolBarEditBoxButton::GetContentsAll.md)|检索文本的第一个编辑框具有指定的命令ID.的工具栏控件|  
|[CMFCToolBarEditBoxButton::GetContextMenuID](../Topic/CMFCToolBarEditBoxButton::GetContextMenuID.md)|检索与按钮快捷菜单的资源ID。|  
|[CMFCToolBarEditBoxButton::GetEditBorder](../Topic/CMFCToolBarEditBoxButton::GetEditBorder.md)|检索编辑框按钮的编辑器部件的边框。|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::GetEditBox](../Topic/CMFCToolBarEditBoxButton::GetEditBox.md)|返回指向该按钮嵌入的编辑控件。|  
|[CMFCToolBarEditBoxButton::GetHwnd](../Topic/CMFCToolBarEditBoxButton::GetHwnd.md)|检索与工具栏按钮的窗口句柄。  （重写 [CMFCToolBarButton::GetHwnd](../Topic/CMFCToolBarButton::GetHwnd.md)。）|  
|[CMFCToolBarEditBoxButton::GetInvalidateRect](../Topic/CMFCToolBarEditBoxButton::GetInvalidateRect.md)|检索按钮的工作区的区域必须重绘。  （重写 [CMFCToolBarButton::GetInvalidateRect](../Topic/CMFCToolBarButton::GetInvalidateRect.md)。）|  
|`CMFCToolBarEditBoxButton::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCToolBarEditBoxButton::HaveHotBorder](../Topic/CMFCToolBarEditBoxButton::HaveHotBorder.md)|确定按钮的边框是否显示，当用户单击按钮。  （重写 [CMFCToolBarButton::HaveHotBorder](../Topic/CMFCToolBarButton::HaveHotBorder.md)。）|  
|[CMFCToolBarEditBoxButton::IsFlatMode](../Topic/CMFCToolBarEditBoxButton::IsFlatMode.md)|确定是否编辑框按钮有平面样式。|  
|[CMFCToolBarEditBoxButton::NotifyCommand](../Topic/CMFCToolBarEditBoxButton::NotifyCommand.md)|指定按钮是否处理 [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) 消息。  （重写 [CMFCToolBarButton::NotifyCommand](../Topic/CMFCToolBarButton::NotifyCommand.md)。）|  
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](../Topic/CMFCToolBarEditBoxButton::OnAddToCustomizePage.md)|调用由结构，当按钮添加到 **自定义** 对话框。  （重写 [CMFCToolBarButton::OnAddToCustomizePage](../Topic/CMFCToolBarButton::OnAddToCustomizePage.md)。）|  
|`CMFCToolBarEditBoxButton::OnCalculateSize`|调用由结构计算该按钮的大小指定的设备上下文和停靠状态的。  （重写 [CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md)。）|  
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](../Topic/CMFCToolBarEditBoxButton::OnChangeParentWnd.md)|调用由结构，当按钮插入新工具栏。  （重写 [CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md)。）|  
|[CMFCToolBarEditBoxButton::OnClick](../Topic/CMFCToolBarEditBoxButton::OnClick.md)|调用由结构，当用户单击鼠标按钮。  （重写 [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)。）|  
|[CMFCToolBarEditBoxButton::OnCtlColor](../Topic/CMFCToolBarEditBoxButton::OnCtlColor.md)|调用由结构，当父工具栏处理 `WM_CTLCOLOR` 消息。  （重写 [CMFCToolBarButton::OnCtlColor](../Topic/CMFCToolBarButton::OnCtlColor.md)。）|  
|`CMFCToolBarEditBoxButton::OnDraw`|使用指定的样式和选项，调用由框架绘制按钮。  （重写 [CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md)。）|  
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|调用由框架绘制在 **自定义** 对话框的 **命令** 窗格的按钮。  （重写 [CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md)。）|  
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](../Topic/CMFCToolBarEditBoxButton::OnGlobalFontsChanged.md)|调用由框架，如果全局字体已更改。  （重写 [CMFCToolBarButton::OnGlobalFontsChanged](../Topic/CMFCToolBarButton::OnGlobalFontsChanged.md)。）|  
|[CMFCToolBarEditBoxButton::OnMove](../Topic/CMFCToolBarEditBoxButton::OnMove.md)|调用由结构，当父工具栏移动。  （重写 [CMFCToolBarButton::OnMove](../Topic/CMFCToolBarButton::OnMove.md)。）|  
|[CMFCToolBarEditBoxButton::OnShow](../Topic/CMFCToolBarEditBoxButton::OnShow.md)|调用由结构，当按钮变为可见或不可见。  （重写 [CMFCToolBarButton::OnShow](../Topic/CMFCToolBarButton::OnShow.md)。）|  
|[CMFCToolBarEditBoxButton::OnSize](../Topic/CMFCToolBarEditBoxButton::OnSize.md)|调用由结构，当父工具栏更改更改的按钮调整其大小或位置和此更改原因。  （重写 [CMFCToolBarButton::OnSize](../Topic/CMFCToolBarButton::OnSize.md)。）|  
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](../Topic/CMFCToolBarEditBoxButton::OnUpdateToolTip.md)|调用由结构，当父工具栏更新其工具提示文本。  （重写 [CMFCToolBarButton::OnUpdateToolTip](../Topic/CMFCToolBarButton::OnUpdateToolTip.md)。）|  
|`CMFCToolBarEditBoxButton::Serialize`|读取存档或写入的此对象到存档。  （重写 [CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md)。）|  
|`CMFCToolBarEditBoxButton::SetACCData`|填充可访问性数据的提供的 `CAccessibilityData` 对象从工具栏按钮。  （重写 [CMFCToolBarButton::SetACCData](../Topic/CMFCToolBarButton::SetACCData.md)。）|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContents](../Topic/CMFCToolBarEditBoxButton::SetContents.md)|将按钮的编辑控件的文本。|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContentsAll](../Topic/CMFCToolBarEditBoxButton::SetContentsAll.md)|查找具有指定的命令ID的编辑控件按钮，并将该按钮编辑控件的文本。|  
|[CMFCToolBarEditBoxButton::SetContextMenuID](../Topic/CMFCToolBarEditBoxButton::SetContextMenuID.md)|指定与按钮快捷菜单的资源ID。|  
|[CMFCToolBarEditBoxButton::SetFlatMode](../Topic/CMFCToolBarEditBoxButton::SetFlatMode.md)|指定的平面样式外观在应用程序的编辑框按钮。|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetStyle](../Topic/CMFCToolBarEditBoxButton::SetStyle.md)|指定按钮的样式。  （重写 [CMFCToolBarButton::SetStyle](../Topic/CMFCToolBarButton::SetStyle.md)。）|  
  
## 备注  
 若要添加编辑框按钮添加到工具栏，请执行以下步骤:  
  
 1.  保留虚拟资源ID在父工具栏资源的按钮。  
  
 2.  构造 `CMFCToolBarEditBoxButton` 对象。  
  
 3.  使用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)，在处理 `AFX_WM_RESETTOOLBAR` 消息的消息处理程序，请在新的组合框按钮替换虚假的按钮。  
  
 有关更多信息，请参见 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  
  
## 示例  
 下面的示例在 `CMFCToolBarEditBoxButton` 选件类演示如何使用各种方法。  该示例演示如何指定用户在自定义过程中拉伸按钮，指定按钮的边框显示，当用户单击按钮，将textbox控件中的文本，指定平面样式外观在应用程序的编辑框按钮，并指定工具栏的样式编辑框控件时。  
  
 [!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/CPP/cmfctoolbareditboxbutton-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)  
  
## 要求  
 **标头:** afxtoolbareditboxbutton.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)