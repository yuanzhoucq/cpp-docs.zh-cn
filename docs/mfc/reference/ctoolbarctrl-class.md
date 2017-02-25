---
title: "CToolBarCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CToolBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBarCtrl class"
  - "工具提示 [C++], 通知"
  - "工具栏控件 [MFC], CToolBarCtrl class"
  - "Windows common controls [C++], CToolBarCtrl"
ms.assetid: 8f2f8ad2-05d7-4975-8715-3f2eed795248
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CToolBarCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows工具栏公共控件的功能。  
  
## 语法  
  
```  
class CToolBarCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CToolBarCtrl::CToolBarCtrl](../Topic/CToolBarCtrl::CToolBarCtrl.md)|构造 `CToolBarCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CToolBarCtrl::AddBitmap](../Topic/CToolBarCtrl::AddBitmap.md)|添加一个或多个位图按钮图像到按钮图像列表可用于工具栏控件。|  
|[CToolBarCtrl::AddButtons](../Topic/CToolBarCtrl::AddButtons.md)|添加一个或多个按钮添加到工具栏控件。|  
|[CToolBarCtrl::AddString](../Topic/CToolBarCtrl::AddString.md)|添加一个新字符串，作为资源ID，为内部的工具栏上的列表的字符串。|  
|[CToolBarCtrl::AddStrings](../Topic/CToolBarCtrl::AddStrings.md)|添加一个新字符串，通过，为Null分隔的字符串缓冲区的指针，对内部的工具栏上的列表的字符串。|  
|[CToolBarCtrl::AutoSize](../Topic/CToolBarCtrl::AutoSize.md)|调整工具栏控件。|  
|[CToolBarCtrl::ChangeBitmap](../Topic/CToolBarCtrl::ChangeBitmap.md)|更改一个按钮的位图在当前工具栏控件。|  
|[CToolBarCtrl::CheckButton](../Topic/CToolBarCtrl::CheckButton.md)|选中或清除在工具栏控件的特定按钮。|  
|[CToolBarCtrl::CommandToIndex](../Topic/CToolBarCtrl::CommandToIndex.md)|检索按钮的从零开始的索引与指定的顺序标识符。|  
|[CToolBarCtrl::Create](../Topic/CToolBarCtrl::Create.md)|创建一个工具栏控件并将它附加到 `CToolBarCtrl` 对象。|  
|[CToolBarCtrl::CreateEx](../Topic/CToolBarCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建一个工具栏控件并将它附加到 `CToolBarCtrl` 对象。|  
|[CToolBarCtrl::Customize](../Topic/CToolBarCtrl::Customize.md)|显示自定义工具栏"对话框。|  
|[CToolBarCtrl::DeleteButton](../Topic/CToolBarCtrl::DeleteButton.md)|从控件中删除工具栏按钮。|  
|[CToolBarCtrl::EnableButton](../Topic/CToolBarCtrl::EnableButton.md)|启用或禁用了toolbar控件的指定的按钮。|  
|[CToolBarCtrl::GetAnchorHighlight](../Topic/CToolBarCtrl::GetAnchorHighlight.md)|检索设置为工具栏的定位点突出显示。|  
|[CToolBarCtrl::GetBitmap](../Topic/CToolBarCtrl::GetBitmap.md)|检索位图的索引与工具栏上的按钮。|  
|[CToolBarCtrl::GetBitmapFlags](../Topic/CToolBarCtrl::GetBitmapFlags.md)|获取标志与工具栏的位图。|  
|[CToolBarCtrl::GetButton](../Topic/CToolBarCtrl::GetButton.md)|检索有关指定的按钮的信息在工具栏控件。|  
|[CToolBarCtrl::GetButtonCount](../Topic/CToolBarCtrl::GetButtonCount.md)|当前检索按钮的计数在工具栏控件。|  
|[CToolBarCtrl::GetButtonInfo](../Topic/CToolBarCtrl::GetButtonInfo.md)|检索一个按钮的信息在工具栏。|  
|[CToolBarCtrl::GetButtonSize](../Topic/CToolBarCtrl::GetButtonSize.md)|检索当前宽度和高度工具栏按钮，以像素为单位。|  
|[CToolBarCtrl::GetColorScheme](../Topic/CToolBarCtrl::GetColorScheme.md)|检索当前工具栏控件的配色方案。|  
|[CToolBarCtrl::GetDisabledImageList](../Topic/CToolBarCtrl::GetDisabledImageList.md)|检索图像列表工具栏控件使用显示禁用的按钮。|  
|[CToolBarCtrl::GetDropTarget](../Topic/CToolBarCtrl::GetDropTarget.md)|检索工具栏控件的 [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) 接口。|  
|[CToolBarCtrl::GetExtendedStyle](../Topic/CToolBarCtrl::GetExtendedStyle.md)|检索工具栏控件的扩展样式。|  
|[CToolBarCtrl::GetHotImageList](../Topic/CToolBarCtrl::GetHotImageList.md)|检索图像列表工具栏控件使用显示“快捷”按钮。  当鼠标指针悬停在上时，一个快捷按钮突出显示。|  
|[CToolBarCtrl::GetHotItem](../Topic/CToolBarCtrl::GetHotItem.md)|检索快捷项的索引工具栏上的。|  
|[CToolBarCtrl::GetImageList](../Topic/CToolBarCtrl::GetImageList.md)|检索图像列表工具栏控件使用显示在其默认状态的按钮。|  
|[CToolBarCtrl::GetInsertMark](../Topic/CToolBarCtrl::GetInsertMark.md)|检索工具栏的当前插入标记。|  
|[CToolBarCtrl::GetInsertMarkColor](../Topic/CToolBarCtrl::GetInsertMarkColor.md)|检索使用的颜色绘制工具栏中插入标记。|  
|[CToolBarCtrl::GetItemRect](../Topic/CToolBarCtrl::GetItemRect.md)|检索一个按钮的边框在工具栏控件的。|  
|[CToolBarCtrl::GetMaxSize](../Topic/CToolBarCtrl::GetMaxSize.md)|检索所有的总大小可见按钮和分隔符在工具栏。|  
|[CToolBarCtrl::GetMaxTextRows](../Topic/CToolBarCtrl::GetMaxTextRows.md)|检索文本行的最大数在工具栏按钮公开的。|  
|[CToolBarCtrl::GetMetrics](../Topic/CToolBarCtrl::GetMetrics.md)|检索工具栏控件的指标。|  
|[CToolBarCtrl::GetPadding](../Topic/CToolBarCtrl::GetPadding.md)|检索当前工具栏控件的水平和垂直填充。|  
|[CToolBarCtrl::GetPressedImageList](../Topic/CToolBarCtrl::GetPressedImageList.md)|检索图像列出当前工具栏控件使用个表示按下状态的按钮。|  
|[CToolBarCtrl::GetRect](../Topic/CToolBarCtrl::GetRect.md)|检索一个指定的工具栏按钮的边框。|  
|[CToolBarCtrl::GetRows](../Topic/CToolBarCtrl::GetRows.md)|检索行数工具栏当前显示的按钮。|  
|[CToolBarCtrl::GetState](../Topic/CToolBarCtrl::GetState.md)|检索有关指定的按钮的状态信息在一个工具栏控件，例如是否已启用，按下或签出。|  
|[CToolBarCtrl::GetString](../Topic/CToolBarCtrl::GetString.md)|检索工具栏字符串。|  
|[CToolBarCtrl::GetStyle](../Topic/CToolBarCtrl::GetStyle.md)|检索样式将用于工具栏控件。|  
|[CToolBarCtrl::GetToolTips](../Topic/CToolBarCtrl::GetToolTips.md)|检索工具提示控件的句柄，如果有，与工具栏控件。|  
|[CToolBarCtrl::HideButton](../Topic/CToolBarCtrl::HideButton.md)|隐藏或显示在工具栏控件的指定的按钮。|  
|[CToolBarCtrl::HitTest](../Topic/CToolBarCtrl::HitTest.md)|确定一个点位置。工具栏控件。|  
|[CToolBarCtrl::Indeterminate](../Topic/CToolBarCtrl::Indeterminate.md)|设置或清除指定的按钮不确定的\(灰色\)状态在工具栏控件的。|  
|[CToolBarCtrl::InsertButton](../Topic/CToolBarCtrl::InsertButton.md)|插入工具栏中的按钮控件。|  
|[CToolBarCtrl::InsertMarkHitTest](../Topic/CToolBarCtrl::InsertMarkHitTest.md)|检索点插入标记信息在工具栏。|  
|[CToolBarCtrl::IsButtonChecked](../Topic/CToolBarCtrl::IsButtonChecked.md)|指示在工具栏控件的指定的按钮是否已选中。|  
|[CToolBarCtrl::IsButtonEnabled](../Topic/CToolBarCtrl::IsButtonEnabled.md)|指示在工具栏控件的指定的按钮是否启用。|  
|[CToolBarCtrl::IsButtonHidden](../Topic/CToolBarCtrl::IsButtonHidden.md)|指示在工具栏控件的指定的按钮是否为隐藏的。|  
|[CToolBarCtrl::IsButtonHighlighted](../Topic/CToolBarCtrl::IsButtonHighlighted.md)|检查工具栏按钮的突出显示状态。|  
|[CToolBarCtrl::IsButtonIndeterminate](../Topic/CToolBarCtrl::IsButtonIndeterminate.md)|通知指定的按钮的状态在工具栏控件是否是不确定的\(灰色）。|  
|[CToolBarCtrl::IsButtonPressed](../Topic/CToolBarCtrl::IsButtonPressed.md)|指示在工具栏控件的指定的按钮是否按。|  
|[CToolBarCtrl::LoadImages](../Topic/CToolBarCtrl::LoadImages.md)|加载位图到工具栏控件的图像中列出。|  
|[CToolBarCtrl::MapAccelerator](../Topic/CToolBarCtrl::MapAccelerator.md)|映射快捷键字符为工具栏按钮。|  
|[CToolBarCtrl::MarkButton](../Topic/CToolBarCtrl::MarkButton.md)|设置特定按钮的突出显示状态。工具栏控件的。|  
|[CToolBarCtrl::MoveButton](../Topic/CToolBarCtrl::MoveButton.md)|从索引按钮移动到另一个。|  
|[CToolBarCtrl::PressButton](../Topic/CToolBarCtrl::PressButton.md)|按或版本在工具栏控件的指定的按钮。|  
|[CToolBarCtrl::ReplaceBitmap](../Topic/CToolBarCtrl::ReplaceBitmap.md)|用一个新的位图替换在当前工具栏控件的现有的位图。|  
|[CToolBarCtrl::RestoreState](../Topic/CToolBarCtrl::RestoreState.md)|还原工具栏控件的状态。|  
|[CToolBarCtrl::SaveState](../Topic/CToolBarCtrl::SaveState.md)|保存工具栏控件的状态。|  
|[CToolBarCtrl::SetAnchorHighlight](../Topic/CToolBarCtrl::SetAnchorHighlight.md)|设置为工具栏的定位点突出显示。|  
|[CToolBarCtrl::SetBitmapSize](../Topic/CToolBarCtrl::SetBitmapSize.md)|设置要添加的数字复制图像的大小到工具栏控件。|  
|[CToolBarCtrl::SetButtonInfo](../Topic/CToolBarCtrl::SetButtonInfo.md)|将现有按钮的信息在工具栏。|  
|[CToolBarCtrl::SetButtonSize](../Topic/CToolBarCtrl::SetButtonSize.md)|设置要添加的按钮的大小到工具栏控件。|  
|[CToolBarCtrl::SetButtonStructSize](../Topic/CToolBarCtrl::SetButtonStructSize.md)|指定 `TBBUTTON` 结构的大小。|  
|[CToolBarCtrl::SetButtonWidth](../Topic/CToolBarCtrl::SetButtonWidth.md)|设置在工具栏控件的最小值和最大值按钮宽度。|  
|[CToolBarCtrl::SetCmdID](../Topic/CToolBarCtrl::SetCmdID.md)|指定的按钮时，设置要发送的命令ID给所有者窗口。|  
|[CToolBarCtrl::SetColorScheme](../Topic/CToolBarCtrl::SetColorScheme.md)|设置当前工具栏控件的配色方案。|  
|[CToolBarCtrl::SetDisabledImageList](../Topic/CToolBarCtrl::SetDisabledImageList.md)|设置图像列表工具栏控件将使用显示禁用的按钮。|  
|[CToolBarCtrl::SetDrawTextFlags](../Topic/CToolBarCtrl::SetDrawTextFlags.md)|将Win32函数 [DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498)，的标志用于绘制在指定的矩形的文本，已设置基于标志如何设置。|  
|[CToolBarCtrl::SetExtendedStyle](../Topic/CToolBarCtrl::SetExtendedStyle.md)|设置工具栏控件的扩展样式。|  
|[CToolBarCtrl::SetHotImageList](../Topic/CToolBarCtrl::SetHotImageList.md)|设置图像列表工具栏控件将使用显示“快捷”按钮。|  
|[CToolBarCtrl::SetHotItem](../Topic/CToolBarCtrl::SetHotItem.md)|设置工具栏上的快捷项目。|  
|[CToolBarCtrl::SetImageList](../Topic/CToolBarCtrl::SetImageList.md)|设置图像列表工具栏将使用显示其默认状态的按钮。|  
|[CToolBarCtrl::SetIndent](../Topic/CToolBarCtrl::SetIndent.md)|将第一个按钮的缩进在工具栏控件。|  
|[CToolBarCtrl::SetInsertMark](../Topic/CToolBarCtrl::SetInsertMark.md)|设置工具栏按钮的当前插入标记。|  
|[CToolBarCtrl::SetInsertMarkColor](../Topic/CToolBarCtrl::SetInsertMarkColor.md)|设置用于的颜色绘制工具栏中插入标记。|  
|[CToolBarCtrl::SetMaxTextRows](../Topic/CToolBarCtrl::SetMaxTextRows.md)|设置文本行的最大数在工具栏按钮公开的。|  
|[CToolBarCtrl::SetMetrics](../Topic/CToolBarCtrl::SetMetrics.md)|设置工具栏控件的指标。|  
|[CToolBarCtrl::SetOwner](../Topic/CToolBarCtrl::SetOwner.md)|设置窗口接收从工具栏控件的通知消息。|  
|[CToolBarCtrl::SetPadding](../Topic/CToolBarCtrl::SetPadding.md)|设置当前工具栏控件的水平和垂直填充。|  
|[CToolBarCtrl::SetPressedImageList](../Topic/CToolBarCtrl::SetPressedImageList.md)|设置图像列出当前工具栏控件使用个表示按下状态的按钮。|  
|[CToolBarCtrl::SetRows](../Topic/CToolBarCtrl::SetRows.md)|设置要在工具栏上显示的按钮。|  
|[CToolBarCtrl::SetState](../Topic/CToolBarCtrl::SetState.md)|设置指定的按钮的状态在工具栏控件。|  
|[CToolBarCtrl::SetStyle](../Topic/CToolBarCtrl::SetStyle.md)|设置工具栏控件的样式。|  
|[CToolBarCtrl::SetToolTips](../Topic/CToolBarCtrl::SetToolTips.md)|关联工具提示控件与工具栏控件。|  
|[CToolBarCtrl::SetWindowTheme](../Topic/CToolBarCtrl::SetWindowTheme.md)|设置工具栏控件的视觉样式。|  
  
## 备注  
 此控件\(并 `CToolBarCtrl` 选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  
  
 Windows工具栏公共控件。包含一个或多个按钮的矩形子窗口。  这些按钮可以显示位图图像，字符串或两个。  当用户选择该按钮时，其发送命令信息到工具栏的所有者窗口。  通常，在工具栏上的按钮对应于应用程序的菜单中的项;它们提供直接访问方式应用程序的命令。  
  
 `CToolBarCtrl` 对象包含几个重要内部数据结构:按钮位图图像列表或图像列表，按钮标签字符串列表和的 `TBBUTTON` 结构列表关联图像和字符串包含按钮的位置、样式、状态和命令ID。  每个这些数据结构组件的从零开始的索引引用。  在使用 `CToolBarCtrl` 对象之前，您必须将这些数据结构。  字符串列表可以为该按钮标签只使用;不能从工具栏检索字符串。  
  
 若要使用 `CToolBarCtrl` 对象，则通常执行以下步骤:  
  
1.  构造 `CToolBarCtrl` 对象。  
  
2.  调用 [创建](../Topic/CToolBarCtrl::Create.md) 创建工具栏Windows公共控件并将其附加到 `CToolBarCtrl` 对象。  指示工具栏样式使用样式，例如透明工具栏的支持下拉式样式按钮的工具栏上的 **TBSTYLE\_TRANSPARENT** 或 **TBSTYLE\_DROPDOWN**。  
  
3.  标识您希望在显示的工具栏中的按钮:  
  
    -   为按钮若要使用位图图像，添加按钮位图到工具栏通过调用 [AddBitmap](../Topic/CToolBarCtrl::AddBitmap.md)。  
  
    -   若要使用图像显示的图像。按钮列表中，指定图像通过调用 [SetImageList](../Topic/CToolBarCtrl::SetImageList.md)、 [SetHotImageList](../Topic/CToolBarCtrl::SetHotImageList.md)或 [SetDisabledImageList](../Topic/CToolBarCtrl::SetDisabledImageList.md)列表。  
  
    -   为按钮若要使用字符串标签，请添加到工具栏通过调用 [AddString](../Topic/CToolBarCtrl::AddString.md) 和 [AddStrings](../Topic/CToolBarCtrl::AddStrings.md)。  
  
4.  添加按钮结构到工具栏通过调用 [AddButtons](../Topic/CToolBarCtrl::AddButtons.md)。  
  
5.  如果希望工具栏的工具提示在不是 `CFrameWnd`的所有者窗口，则按需要处理工具栏上的所有者窗口的 **TTN\_NEEDTEXT** 消息 [处理工具提示通知](../../mfc/handling-tool-tip-notifications.md)如中所述。  如果工具栏的父窗口 `CFrameWnd`从派生，工具提示显示，而无需从您的任何执行任何额外的工作，因为 `CFrameWnd` 提供了默认的处理程序。  
  
6.  如果您希望您的用户可以自定义工具栏，处理自定义在所有者窗口的通知消息。[处理自定义通知](../../mfc/handling-customization-notifications.md)所述。  
  
 可以使用 [SaveState](../Topic/CToolBarCtrl::SaveState.md) 保存一个工具栏控件的当前状态在注册表中 [RestoreState](../Topic/CToolBarCtrl::RestoreState.md) 的恢复信息的状态以前存储在注册表。  除了保存到应用程序中使用的之间toolbar状态外，应用程序通常存储为状态，在用户开始自定义工具栏之前，以防用户后若要还原工具栏到其原始状态。  
  
## 对于Internet Explorer 4.0版和更高版本支持  
 若要支持在Internet Explorer中引入的功能，版本4.0和更高版本，MFC提供图像列表支持和工具栏控件的透明和平面样式。  
  
 透明工具栏允许客户端在工具栏下方通过显示。  若要创建透明工具栏中，使用 **TBSTYLE\_FLAT** 和 **TBSTYLE\_TRANSPARENT** 样式。  透明工具栏在快捷跟踪功能;也就是说，当鼠标指针移动到在"工具栏中的快捷按钮，该按钮的外观更改。  在 **TBSTYLE\_FLAT** 样式创建的工具栏将包含不透明的按钮。  
  
 图像列表支持控件的默认行为、快捷图像和禁用图像的更大的灵活性。  使用 [GetImageList](../Topic/CToolBarCtrl::GetImageList.md)、 [GetHotImageList](../Topic/CToolBarCtrl::GetHotImageList.md)和 [GetDisabledImageList](../Topic/CToolBarCtrl::GetDisabledImageList.md) 以透明工具栏根据自身的状态操作图像:  
  
 有关使用 `CToolBarCtrl`的更多信息，请参见 [控件](../../mfc/controls-mfc.md) 和 [使用CToolBarCtrl](../../mfc/using-ctoolbarctrl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolBarCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [MFC示例CMNCTRL1](../../top/visual-cpp-samples.md)   
 [MFC示例MFCIE](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CToolBar Class](../../mfc/reference/ctoolbar-class.md)