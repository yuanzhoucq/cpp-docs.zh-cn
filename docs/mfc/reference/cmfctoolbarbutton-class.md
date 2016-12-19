---
title: "CMFCToolBarButton Class | Microsoft Docs"
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
  - "CMFCToolBarButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarButton class"
ms.assetid: 8a6ecffb-86b0-4f5c-8211-a9146b463efd
caps.latest.revision: 34
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供按钮功能。工具栏。  
  
## 语法  
  
```  
class CMFCToolBarButton : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarButton::CMFCToolBarButton](../Topic/CMFCToolBarButton::CMFCToolBarButton.md)|构造和初始化 `CMFCToolBarButton` 对象。|  
|`CMFCToolBarButton::~CMFCToolBarButton`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarButton::CanBeDropped](../Topic/CMFCToolBarButton::CanBeDropped.md)|指定用户是否在工具栏可以确定按钮或菜单在自定义项时。|  
|[CMFCToolBarButton::CanBeStored](../Topic/CMFCToolBarButton::CanBeStored.md)|指定是否可以存储按钮。|  
|[CMFCToolBarButton::CanBeStretched](../Topic/CMFCToolBarButton::CanBeStretched.md)|指定用户是否在自定义过程中拉伸按钮。|  
|[CMFCToolBarButton::CompareWith](../Topic/CMFCToolBarButton::CompareWith.md)|此实例与提供的 `CMFCToolBarButton` 对象进行比较。|  
|[CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md)|复制另一个工具栏按钮的属性设置为当前按钮。|  
|[CMFCToolBarButton::CreateFromOleData](../Topic/CMFCToolBarButton::CreateFromOleData.md)|创建从提供的 `COleDataObject` 对象的一 `CMFCToolBarButton` 对象。|  
|`CMFCToolBarButton::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|[CMFCToolBarButton::EnableWindow](../Topic/CMFCToolBarButton::EnableWindow.md)|启用或禁用鼠标和键盘输入。|  
|[CMFCToolBarButton::ExportToMenuButton](../Topic/CMFCToolBarButton::ExportToMenuButton.md)|复制从工具栏按钮文本添加到菜单。|  
|[CMFCToolBarButton::GetClipboardFormat](../Topic/CMFCToolBarButton::GetClipboardFormat.md)|检索应用程序的全局剪贴板格式。|  
|[CMFCToolBarButton::GetHwnd](../Topic/CMFCToolBarButton::GetHwnd.md)|检索与工具栏按钮的窗口句柄。|  
|[CMFCToolBarButton::GetImage](../Topic/CMFCToolBarButton::GetImage.md)|检索按钮的图像索引。|  
|[CMFCToolBarButton::GetInvalidateRect](../Topic/CMFCToolBarButton::GetInvalidateRect.md)|检索按钮的工作区的区域必须重绘。|  
|[CMFCToolBarButton::GetParentWnd](../Topic/CMFCToolBarButton::GetParentWnd.md)|检索按钮的父窗口。|  
|[CMFCToolBarButton::GetProtectedCommands](../Topic/CMFCToolBarButton::GetProtectedCommands.md)|检索用户无法自定义命令的列表。|  
|[CMFCToolBarButton::GetTextSize](../Topic/CMFCToolBarButton::GetTextSize.md)|检索按钮的文本范围。|  
|[CMFCToolBarButton::HasFocus](../Topic/CMFCToolBarButton::HasFocus.md)|确定按钮是否具有当前输入焦点。|  
|[CMFCToolBarButton::HaveHotBorder](../Topic/CMFCToolBarButton::HaveHotBorder.md)|确定按钮的边框是否显示，当用户选择按钮。|  
|[CMFCToolBarButton::IsDrawImage](../Topic/CMFCToolBarButton::IsDrawImage.md)|确定映像是否在按钮显示。|  
|[CMFCToolBarButton::IsDrawText](../Topic/CMFCToolBarButton::IsDrawText.md)|确定文本标签是否在按钮显示。|  
|[CMFCToolBarButton::IsDroppedDown](../Topic/CMFCToolBarButton::IsDroppedDown.md)|确定按钮是否显示子菜单。|  
|[CMFCToolBarButton::IsEditable](../Topic/CMFCToolBarButton::IsEditable.md)|确定按钮是否可以自定义。|  
|[CMFCToolBarButton::IsExtraSize](../Topic/CMFCToolBarButton::IsExtraSize.md)|确定按钮是否可以显示了一个扩展的边框。|  
|[CMFCToolBarButton::IsFirstInGroup](../Topic/CMFCToolBarButton::IsFirstInGroup.md)|确定按钮是否在第一个位置在其按钮组中。|  
|[CMFCToolBarButton::IsHidden](../Topic/CMFCToolBarButton::IsHidden.md)|确定按钮是否为隐藏的。|  
|[CMFCToolBarButton::IsHorizontal](../Topic/CMFCToolBarButton::IsHorizontal.md)|确定按钮是否位于一水平toolbar。|  
|[CMFCToolBarButton::IsLastInGroup](../Topic/CMFCToolBarButton::IsLastInGroup.md)|指定按钮是否在最后位置在其按钮组中。|  
|[CMFCToolBarButton::IsLocked](../Topic/CMFCToolBarButton::IsLocked.md)|确定按钮是否处于锁定\(非自定义项\)的工具栏。|  
|[CMFCToolBarButton::IsOwnerOf](../Topic/CMFCToolBarButton::IsOwnerOf.md)|确定按钮是否提供的窗口句柄的所有者。|  
|[CMFCToolBarButton::IsVisible](../Topic/CMFCToolBarButton::IsVisible.md)|确定工具栏按钮是否可见。|  
|[CMFCToolBarButton::IsWindowVisible](../Topic/CMFCToolBarButton::IsWindowVisible.md)|确定按钮的基础窗口句柄是否可见。|  
|[CMFCToolBarButton::NotifyCommand](../Topic/CMFCToolBarButton::NotifyCommand.md)|指定按钮是否处理 [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) 消息。|  
|[CMFCToolBarButton::OnAddToCustomizePage](../Topic/CMFCToolBarButton::OnAddToCustomizePage.md)|调用由结构，当按钮添加到 **自定义** 对话框。|  
|[CMFCToolBarButton::OnBeforeDrag](../Topic/CMFCToolBarButton::OnBeforeDrag.md)|指定按钮是否可以拖动。|  
|[CMFCToolBarButton::OnBeforeDrop](../Topic/CMFCToolBarButton::OnBeforeDrop.md)|指定用户是否可以将在目标工具栏上的按钮。|  
|[CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md)|调用由结构计算该按钮的大小指定的设备上下文和停靠状态的。|  
|[CMFCToolBarButton::OnCancelMode](../Topic/CMFCToolBarButton::OnCancelMode.md)|调用由框架处理 [WM\_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) 消息。|  
|[CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md)|调用由结构，当按钮插入新工具栏。|  
|[CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)|调用由结构，当用户单击鼠标按钮。|  
|[CMFCToolBarButton::OnClickUp](../Topic/CMFCToolBarButton::OnClickUp.md)|调用由结构，当用户松开鼠标按钮。|  
|[CMFCToolBarButton::OnContextHelp](../Topic/CMFCToolBarButton::OnContextHelp.md)|调用由结构，当父工具栏处理 `WM_HELPHITTEST` 消息。|  
|[CMFCToolBarButton::OnCtlColor](../Topic/CMFCToolBarButton::OnCtlColor.md)|调用由结构，当父工具栏处理 `WM_CTLCOLOR` 消息。|  
|[CMFCToolBarButton::OnCustomizeMenu](../Topic/CMFCToolBarButton::OnCustomizeMenu.md)|当应用程序显示在父工具栏，都有一个快捷菜单使按钮修改表所提供的菜单。|  
|[CMFCToolBarButton::OnDblClk](../Topic/CMFCToolBarButton::OnDblClk.md)|调用由结构，当父工具栏处理 [WM\_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606) 消息。|  
|[CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md)|使用指定的样式和选项，调用由框架绘制按钮。|  
|[CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md)|调用由框架绘制在 **自定义** 对话框的 **命令** 窗格的按钮。|  
|[CMFCToolBarButton::OnGetCustomToolTipText](../Topic/CMFCToolBarButton::OnGetCustomToolTipText.md)|调用由框架检索按钮的自定义工具提示文本。|  
|[CMFCToolBarButton::OnGlobalFontsChanged](../Topic/CMFCToolBarButton::OnGlobalFontsChanged.md)|调用由框架，如果全局字体已更改。|  
|[CMFCToolBarButton::OnMove](../Topic/CMFCToolBarButton::OnMove.md)|调用由结构，当父工具栏移动。|  
|[CMFCToolBarButton::OnShow](../Topic/CMFCToolBarButton::OnShow.md)|调用由结构，当按钮变为可见或不可见。|  
|[CMFCToolBarButton::OnSize](../Topic/CMFCToolBarButton::OnSize.md)|调用由框架，在父工具栏更改时其大小或位置和这种更改需要按钮更改范围。|  
|[CMFCToolBarButton::OnToolHitTest](../Topic/CMFCToolBarButton::OnToolHitTest.md)|调用由结构，当父工具栏必须确定一个点是否位于按钮的边框。|  
|[CMFCToolBarButton::OnUpdateToolTip](../Topic/CMFCToolBarButton::OnUpdateToolTip.md)|调用由结构，当父工具栏更新其工具提示文本。|  
|[CMFCToolBarButton::PrepareDrag](../Topic/CMFCToolBarButton::PrepareDrag.md)|调用由结构，当按钮将执行拖放操作。|  
|[CMFCToolBarButton::Rect](../Topic/CMFCToolBarButton::Rect.md)|检索按钮的边框。|  
|[CMFCToolBarButton::ResetImageToDefault](../Topic/CMFCToolBarButton::ResetImageToDefault.md)|将设置为默认值与按钮的图像。|  
|[CMFCToolBarButton::SaveBarState](../Topic/CMFCToolBarButton::SaveBarState.md)|保存工具栏按钮的状态。|  
|[CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md)|读取存档或写入的此对象到存档。  （重写 [CObject::Serialize](../Topic/CObject::Serialize.md)。）|  
|[CMFCToolBarButton::SetACCData](../Topic/CMFCToolBarButton::SetACCData.md)|填充可访问性数据的提供的 `CAccessibilityData` 对象从工具栏按钮。|  
|[CMFCToolBarButton::SetClipboardFormatName](../Topic/CMFCToolBarButton::SetClipboardFormatName.md)|对全局剪贴板格式重命名。|  
|[CMFCToolBarButton::SetImage](../Topic/CMFCToolBarButton::SetImage.md)|将按钮的图像索引。|  
|[CMFCToolBarButton::SetProtectedCommands](../Topic/CMFCToolBarButton::SetProtectedCommands.md)|设置用户无法自定义命令的列表。|  
|[CMFCToolBarButton::SetRadio](../Topic/CMFCToolBarButton::SetRadio.md)|调用由结构，当按钮将其选中状态。|  
|[CMFCToolBarButton::SetRect](../Topic/CMFCToolBarButton::SetRect.md)|设置按钮的边框。|  
|[CMFCToolBarButton::SetStyle](../Topic/CMFCToolBarButton::SetStyle.md)|设置按钮的样式。|  
|[CMFCToolBarButton::SetVisible](../Topic/CMFCToolBarButton::SetVisible.md)|指定按钮是否可见。|  
|[CMFCToolBarButton::Show](../Topic/CMFCToolBarButton::Show.md)|显示或隐藏按钮。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarButton::m\_bImage](../Topic/CMFCToolBarButton::m_bImage.md)|指定映像是否在按钮显示。|  
|[CMFCToolBarButton::m\_bText](../Topic/CMFCToolBarButton::m_bText.md)|指定文本标签是否在按钮显示。|  
|[CMFCToolBarButton::m\_bTextBelow](../Topic/CMFCToolBarButton::m_bTextBelow.md)|指定文本标签是否在按钮的图像下显示。|  
|[CMFCToolBarButton::m\_bUserButton](../Topic/CMFCToolBarButton::m_bUserButton.md)|指定按钮是否具有用户定义的图像。|  
|[CMFCToolBarButton::m\_bWholeText](../Topic/CMFCToolBarButton::m_bWholeText.md)|指定按钮是否显示其全文标签，即使它不适合边框。|  
|[CMFCToolBarButton::m\_bWrap](../Topic/CMFCToolBarButton::m_bWrap.md)|指定在分隔符旁边的按钮是否在下一行带来。|  
|[CMFCToolBarButton::m\_bWrapText](../Topic/CMFCToolBarButton::m_bWrapText.md)|指定多行文本标签是否启用。|  
|[CMFCToolBarButton::m\_nID](../Topic/CMFCToolBarButton::m_nID.md)|按钮的命令ID。|  
|[CMFCToolBarButton::m\_nStyle](../Topic/CMFCToolBarButton::m_nStyle.md)|按钮的样式。|  
|[CMFCToolBarButton::m\_strText](../Topic/CMFCToolBarButton::m_strText.md)|按钮的文本标签。|  
  
## 备注  
 `CMFCToolbarButton` 对象是位于工具栏上的控件。  其行为类似于普通的按钮。  可以将图像和文本标签。此对象。  工具栏按钮也有命令ID.  当用户单击工具栏按钮时，框架执行此ID指定的命令。  
  
 通常，工具栏按钮可以自定义:用户可以从一个工具栏上的按钮到另一个副本，粘贴，删除，并编辑文本标签和图像。  若要防止用户自定义工具栏，可以通过两种方式之一可以锁定工具栏。  用于设置 `bLocked` 标志传递给 `TRUE`，当您调用 [CMFCToolBar::LoadToolBar](../Topic/CMFCToolBar::LoadToolBar.md)时，使用 [CMFCToolBarButton::SetProtectedCommands](../Topic/CMFCToolBarButton::SetProtectedCommands.md) 方法，或添加单个按钮的命令ID到全局列表保护的命令。  
  
 `CMFCToolBarButton` 对象从工具栏图像的全局集合中的图像在应用程序中。  这些集合由父工具栏，[CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)维护。  有关更多信息，请参见 [CMFCToolBarImages Class](../../mfc/reference/cmfctoolbarimages-class.md)。  
  
 当用户单击工具栏按钮时，其父工具栏处理鼠标消息和传达相应的操作到按钮。  如果按钮具有有效的命令ID，父工具栏 `WM_COMMAND` 信息发送到父帧。  
  
 `CMFCToolBarButton` 选件类是其他工具栏按钮选件类的基类，例如 [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md)、 [CMFCToolBarEditBoxButton Class](../../mfc/reference/cmfctoolbareditboxbutton-class.md)和 [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)。  
  
## 示例  
 通过在 `CMFCToolBarButton` 选件类，中的各种方法下面的示例演示如何配置 `CMFCToolBarButton` 对象。  示例阐释如何启用鼠标和键盘输入，将该按钮的图像索引，则将按钮的边框，并使按钮可见。  此代码段是 [选项卡控件示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_TabControl#1](../../mfc/reference/codesnippet/CPP/cmfctoolbarbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_TabControl#2](../../mfc/reference/codesnippet/CPP/cmfctoolbarbutton-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
## 要求  
 **标头:** afxtoolbarbutton.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarImages Class](../../mfc/reference/cmfctoolbarimages-class.md)   
 [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)   
 [CMFCToolBarButton::NotifyCommand](../Topic/CMFCToolBarButton::NotifyCommand.md)