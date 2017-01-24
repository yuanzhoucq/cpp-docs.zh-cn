---
title: "CMFCDropDownToolbarButton Class | Microsoft Docs"
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
  - "CMFCDropDownToolbarButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDropDownToolbarButton class"
  - "OnCancelMode method"
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
caps.latest.revision: 31
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDropDownToolbarButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

的工具栏按钮的类型的行为与普通按钮，在单击。  但是，将打开一下拉式工具栏\([CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)，如果用户按并使工具栏按钮在上。  
  
## 语法  
  
```  
class CMFCDropDownToolbarButton : public CMFCToolBarButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../Topic/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton.md)|构造 `CMFCDropDownToolbarButton` 对象。|  
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCDropDownToolbarButton::CopyFrom](../Topic/CMFCDropDownToolbarButton::CopyFrom.md)|复制另一个工具栏按钮的属性设置为当前按钮。  （重写 [CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md)。）|  
|`CMFCDropDownToolbarButton::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|[CMFCDropDownToolbarButton::DropDownToolbar](../Topic/CMFCDropDownToolbarButton::DropDownToolbar.md)|打开一下拉式工具栏。|  
|[CMFCDropDownToolbarButton::ExportToMenuButton](../Topic/CMFCDropDownToolbarButton::ExportToMenuButton.md)|复制从工具栏按钮文本添加到菜单。  （重写 [CMFCToolBarButton::ExportToMenuButton](../Topic/CMFCToolBarButton::ExportToMenuButton.md)。）|  
|[CMFCDropDownToolbarButton::GetDropDownToolBar](../Topic/CMFCDropDownToolbarButton::GetDropDownToolBar.md)|检索与按钮的下拉式工具栏。|  
|`CMFCDropDownToolbarButton::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCDropDownToolbarButton::IsDropDown](../Topic/CMFCDropDownToolbarButton::IsDropDown.md)|确定下拉式工具栏是否当前打开。|  
|[CMFCDropDownToolbarButton::IsExtraSize](../Topic/CMFCDropDownToolbarButton::IsExtraSize.md)|确定按钮是否可以显示了一个扩展的边框。  （重写 [CMFCToolBarButton::IsExtraSize](../Topic/CMFCToolBarButton::IsExtraSize.md)。）|  
|[CMFCDropDownToolbarButton::OnCalculateSize](../Topic/CMFCDropDownToolbarButton::OnCalculateSize.md)|调用由结构计算该按钮的大小指定的设备上下文和停靠状态的。  （重写 [CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md)。）|  
|`CMFCDropDownToolbarButton::OnCancelMode`|调用由框架处理 [WM\_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) 消息。  （重写 `CMCToolBarButton::OnCancelMode`。）|  
|[CMFCDropDownToolbarButton::OnChangeParentWnd](../Topic/CMFCDropDownToolbarButton::OnChangeParentWnd.md)|调用由结构，当按钮插入新工具栏。  （重写 [CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md)。）|  
|[CMFCDropDownToolbarButton::OnClick](../Topic/CMFCDropDownToolbarButton::OnClick.md)|调用由结构，当用户单击鼠标按钮。  （重写 [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)。）|  
|[CMFCDropDownToolbarButton::OnClickUp](../Topic/CMFCDropDownToolbarButton::OnClickUp.md)|调用由结构，当用户松开鼠标按钮。  （重写 [CMFCToolBarButton::OnClickUp](../Topic/CMFCToolBarButton::OnClickUp.md)。）|  
|[CMFCDropDownToolbarButton::OnContextHelp](../Topic/CMFCDropDownToolbarButton::OnContextHelp.md)|调用由结构，当父工具栏处理 `WM_HELPHITTEST` 消息。  （重写 [CMFCToolBarButton::OnContextHelp](../Topic/CMFCToolBarButton::OnContextHelp.md)。）|  
|[CMFCDropDownToolbarButton::OnCustomizeMenu](../Topic/CMFCDropDownToolbarButton::OnCustomizeMenu.md)|当应用程序显示在父工具栏，中的快捷菜单修改所提供的菜单。  （重写 [CMFCToolBarButton::OnCustomizeMenu](../Topic/CMFCToolBarButton::OnCustomizeMenu.md)。）|  
|[CMFCDropDownToolbarButton::OnDraw](../Topic/CMFCDropDownToolbarButton::OnDraw.md)|使用指定的样式和选项，调用由框架绘制按钮。  （重写 [CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md)。）|  
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](../Topic/CMFCDropDownToolbarButton::OnDrawOnCustomizeList.md)|调用由框架绘制在 **自定义** 对话框的 **命令** 窗格的按钮。  （重写 [CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md)。）|  
|[CMFCDropDownToolbarButton::Serialize](../Topic/CMFCDropDownToolbarButton::Serialize.md)|读取存档或写入的此对象到存档。  （重写 [CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md)。）|  
|[CMFCDropDownToolbarButton::SetDefaultCommand](../Topic/CMFCDropDownToolbarButton::SetDefaultCommand.md)|设置框架使用的默认命令当用户单击按钮。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCDropDownToolbarButton::m\_uiShowBarDelay](../Topic/CMFCDropDownToolbarButton::m_uiShowBarDelay.md)|指定用户必须启用鼠标按钮在上的时间长度，在下拉式工具栏显示前。|  
  
## 备注  
 `CMFCDropDownToolBarButton` 与一个普通按钮的不同之处在于有一个小的箭头按钮在右下角的。  在用户选择一个按钮从下拉式工具栏后，该结构显示其在顶级工具栏按钮\(带有小箭头的按钮的图标在右下角）。  
  
 有关如何实现一下拉式工具栏的信息，请参见 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)。  
  
 `CMFCDropDownToolBarButton` 对象可以为 [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md) 对象导出和显示为具有弹出菜单的一个菜单按钮。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)  
  
## 要求  
 **标头:** afxdropdowntoolbar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)