---
title: "CMFCColorBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCColorBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorBar class"
  - "CMFCColorBar::m_bInternal data member"
  - "CMFCColorBar::m_bIsEnabled data member"
  - "CMFCColorBar::m_bIsTearOff data member"
  - "CMFCColorBar::m_BoxSize data member"
  - "CMFCColorBar::m_bShowDocColorsWhenDocked data member"
  - "CMFCColorBar::m_bStdColorDlg data member"
  - "CMFCColorBar::m_ColorAutomatic data member"
  - "CMFCColorBar::m_ColorNames data member"
  - "CMFCColorBar::m_colors data member"
  - "CMFCColorBar::m_ColorSelected data member"
  - "CMFCColorBar::m_lstDocColors data member"
  - "CMFCColorBar::m_nCommandID data member"
  - "CMFCColorBar::m_nHorzMargin data member"
  - "CMFCColorBar::m_nHorzOffset data member"
  - "CMFCColorBar::m_nNumColumns data member"
  - "CMFCColorBar::m_nNumColumnsVert data member"
  - "CMFCColorBar::m_nNumRowsHorz data member"
  - "CMFCColorBar::m_nRowHeight data member"
  - "CMFCColorBar::m_nVertMargin data member"
  - "CMFCColorBar::m_nVertOffset data member"
  - "CMFCColorBar::m_Palette data member"
  - "CMFCColorBar::m_pParentBtn data member"
  - "CMFCColorBar::m_pParentRibbonBtn data member"
  - "CMFCColorBar::m_pWndPropList data member"
  - "CMFCColorBar::m_strAutoColor data member"
  - "CMFCColorBar::m_strDocColors data member"
  - "CMFCColorBar::m_strOtherColor data member"
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# CMFCColorBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCColorBar` 选件类表示可以选择在文档或应用程序的颜色的停靠控件条。  
  
## 语法  
  
```  
class CMFCColorBar : public CMFCPopupMenuBar  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorBar::CMFCColorBar](../Topic/CMFCColorBar::CMFCColorBar.md)|构造 `CMFCColorBar` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorBar::ContextToSize](../Topic/CMFCColorBar::ContextToSize.md)|计算需要包含在对有色人种的、控件中的按钮的垂直和水平边距然后调整这些按钮的位置。|  
|[CMFCColorBar::CreateControl](../Topic/CMFCColorBar::CreateControl.md)|创建到有色人种的、控件的窗口中，附加到 `CMFCColorBar` 对象，然后调整控件包含颜色指定的调色板。|  
|[CMFCColorBar::Create](../Topic/CMFCColorBar::Create.md)|创建到有色人种的可控制窗口并将它附加到 `CMFCColorBar` 对象。|  
|[CMFCColorBar::EnableAutomaticButton](../Topic/CMFCColorBar::EnableAutomaticButton.md)|显示或隐藏自动按钮。|  
|[CMFCColorBar::EnableOtherButton](../Topic/CMFCColorBar::EnableOtherButton.md)|启用或禁用允许用户选择多颜色对话框的显示。|  
|[CMFCColorBar::GetColor](../Topic/CMFCColorBar::GetColor.md)|检索当前选定的颜色。|  
|[CMFCColorBar::GetCommandID](../Topic/CMFCColorBar::GetCommandID.md)|检索当前到有色人种的、控件的命令ID。|  
|[CMFCColorBar::GetHighlightedColor](../Topic/CMFCColorBar::GetHighlightedColor.md)|检索表示的颜色颜色按钮具有焦点;即按钮是 *快捷的*。|  
|[CMFCColorBar::GetHorzMargin](../Topic/CMFCColorBar::GetHorzMargin.md)|检索水平边距，位于左侧或右侧颜色单元格和客户端区域边界之间的空间。|  
|[CMFCColorBar::GetVertMargin](../Topic/CMFCColorBar::GetVertMargin.md)|检索垂直边距，位于顶部之间的空格或底部颜色单元格和客户端区域边界。|  
|[CMFCColorBar::IsTearOff](../Topic/CMFCColorBar::IsTearOff.md)|指示当前到有色人种的、是否可停靠。|  
|[CMFCColorBar::SetColor](../Topic/CMFCColorBar::SetColor.md)|设置当前选定的颜色。|  
|[CMFCColorBar::SetColorName](../Topic/CMFCColorBar::SetColorName.md)|设置一个新名称一个指定的颜色。|  
|[CMFCColorBar::SetCommandID](../Topic/CMFCColorBar::SetCommandID.md)|设置为有色人种的、控件的新命令ID。|  
|[CMFCColorBar::SetDocumentColors](../Topic/CMFCColorBar::SetDocumentColors.md)|将当前文件颜色的列表。|  
|[CMFCColorBar::SetHorzMargin](../Topic/CMFCColorBar::SetHorzMargin.md)|设置水平边距，位于左侧或右侧颜色单元格和客户端区域边界之间的空间。|  
|[CMFCColorBar::SetVertMargin](../Topic/CMFCColorBar::SetVertMargin.md)|设置垂直边距，位于顶部之间的空格或底部颜色单元格和客户端区域边界。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorBar::AdjustLocations](../Topic/CMFCColorBar::AdjustLocations.md)|调整颜色按钮的位置到有色人种的、控件。|  
|[CMFCColorBar::AllowChangeTextLabels](../Topic/CMFCColorBar::AllowChangeTextLabels.md)|表示颜色按钮文本标签是否可以更改。|  
|[CMFCColorBar::AllowShowOnList](../Topic/CMFCColorBar::AllowShowOnList.md)|指示对有色人种的、控件对象是否可以显示在工具栏中自定义项时进程列表。|  
|[CMFCColorBar::CalcSize](../Topic/CMFCColorBar::CalcSize.md)|调用由框架作为布局计算过程的一部分。|  
|[CMFCColorBar::CreatePalette](../Topic/CMFCColorBar::CreatePalette.md)|Initalizes具有颜色的一个调色板在指定的颜色。|  
|[CMFCColorBar::GetColorGridSize](../Topic/CMFCColorBar::GetColorGridSize.md)|计算行数和列数到有色人种的、控件的网格。|  
|[CMFCColorBar::GetExtraHeight](../Topic/CMFCColorBar::GetExtraHeight.md)|计算当前到有色人种的、需要显示其他用户界面元素\(例如 **其他** 按钮的其他高度，文档颜色，依此类推。|  
|[CMFCColorBar::InitColors](../Topic/CMFCColorBar::InitColors.md)|初始化颜色的颜色在指定的调色板或系统默认调色板。|  
|[CMFCColorBar::OnKey](../Topic/CMFCColorBar::OnKey.md)|调用由结构，当用户按一个键盘按钮。|  
|[CMFCColorBar::OnSendCommand](../Topic/CMFCColorBar::OnSendCommand.md)|调用由框架关闭弹出控件层次结构。|  
|[CMFCColorBar::OnUpdateCmdUI](../Topic/CMFCColorBar::OnUpdateCmdUI.md)|调用由框架启用或禁用对有色人种的、控件的用户界面项目中的项之前显示。|  
|[CMFCColorBar::OpenColorDialog](../Topic/CMFCColorBar::OpenColorDialog.md)|打开颜色对话框。|  
|[CMFCColorBar::Rebuild](../Topic/CMFCColorBar::Rebuild.md)|完全重新绘制到有色人种的、控件。|  
|[CMFCColorBar::SelectPalette](../Topic/CMFCColorBar::SelectPalette.md)|设置指定的设备上下文的逻辑调色板当前到有色人种的、控件的父按钮的调色板。|  
|[CMFCColorBar::SetPropList](../Topic/CMFCColorBar::SetPropList.md)|设置 `m_pWndPropList` 保护的数据成员设置为指定的指针属性网格控件。|  
|[CMFCColorBar::ShowCommandMessageString](../Topic/CMFCColorBar::ShowCommandMessageString.md)|请求拥有对有色人种的可控制更新在状态栏中显示消息行的框架窗口。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|`m_bInternal`|确定的布尔型字段鼠标事件是否处理。  通常，鼠标事件处理时，此字段为 `TRUE` 时，而且自模式是 `FALSE`。|  
|`m_bIsEnabled`|指示的布尔控件是否启用。|  
|`m_bIsTearOff`|指示的布尔值为有色人种的可控制是否支持停靠。|  
|`m_BoxSize`|在对有色人种的、网格指定单元格范围内的 [CSize](../../atl-mfc-shared/reference/csize-class.md) 对象。|  
|`m_bShowDocColorsWhenDocked`|指示是否显示文档颜色的布尔值，如果对有色人种的、停靠。  有关更多信息，请参见 [CMFCColorBar::SetDocumentColors](../Topic/CMFCColorBar::SetDocumentColors.md)。|  
|`m_bStdColorDlg`|指示是否显示标准的系统颜色对话框或 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) 对话框的布尔值。  有关更多信息，请参见 [CMFCColorBar::EnableOtherButton](../Topic/CMFCColorBar::EnableOtherButton.md)。|  
|`m_ColorAutomatic`|存储当前自动颜色的 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)。  有关更多信息，请参见 [CMFCColorBar::EnableOtherButton](../Topic/CMFCColorBar::EnableOtherButton.md)。|  
|`m_ColorNames`|关联集RGB的 [CMap](../../mfc/reference/cmap-class.md) 对象颜色与其名称。|  
|`m_colors`|的 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值 [CArray](../../mfc/reference/carray-class.md) 包含颜色到有色人种的、控件中显示。|  
|`m_ColorSelected`|为color用户从到有色人种的、控件当前选择的 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值。|  
|`m_lstDocColors`|的 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值 [CList](../../mfc/reference/clist-class.md) 包含颜色当前用于文档。|  
|`m_nCommandID`|为color按钮的命令ID的无符号整数。|  
|`m_nHorzMargin`|是在颜色之间的水平边距的整数在颜色网格按。|  
|`m_nHorzOffset`|对颜色按钮的中心的水平扭曲的整数。  除了颜色外，因此，如果按钮显示文本或图像此值是有意义的。|  
|`m_nNumColumns`|是列号在颜色设置为有色人种的、控制栅的整数。|  
|`m_nNumColumnsVert`|是列号在颜色垂直针对网格的整数。|  
|`m_nNumRowsHorz`|是列号在颜色水平针对网格的整数。|  
|`m_nRowHeight`|为color行高的整数在颜色网格按。|  
|`m_nVertMargin`|是在颜色之间的垂直边距的整数在颜色网格按。|  
|`m_nVertOffset`|对颜色按钮的中心的垂直偏移量的整数。  除了颜色外，因此，如果按钮显示文本或图像此值是有意义的。|  
|`m_Palette`|出于有色人种的、控件颜色的 [CPalette](../../mfc/reference/cpalette-class.md)。|  
|`m_pParentBtn`|为了使当前按钮的父级的 [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) 对象的指针。  如果颜色工具栏中的按钮控件层次结构或在color属性网格控件中，此值是有意义的。|  
|`m_pParentRibbonBtn`|访问在功能区上以及当前按钮的父按钮的 [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) 对象的指针。  如果颜色工具栏中的按钮控件层次结构或在color属性网格控件中，此值是有意义的。|  
|`m_pWndPropList`|为 [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) 对象的指针。|  
|`m_strAutoColor`|是文本在 **自动** 按钮显示的 [CString](../../atl-mfc-shared/reference/cstringt-class.md)。  有关更多信息，请参见 [CMFCColorBar::EnableAutomaticButton](../Topic/CMFCColorBar::EnableAutomaticButton.md)。|  
|`m_strDocColors`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) 是文本中的文档中显示彩色按钮。  有关更多信息，请参见 [CMFCColorBar::SetDocumentColors](../Topic/CMFCColorBar::SetDocumentColors.md)。|  
|`m_strOtherColor`|是文本在 *另一个* 按钮显示的 [CString](../../atl-mfc-shared/reference/cstringt-class.md)。  有关更多信息，请参见 [CMFCColorBar::EnableOtherButton](../Topic/CMFCColorBar::EnableOtherButton.md)。|  
  
## 备注  
 通常，不能直接创建一 `CMFCColorBar` 对象。  相反，[CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md) \(用于菜单和工具栏\)或 [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md) 创建 `CMFCColorBar` 对象。  
  
 `CMFCColorBar` 选件类提供以下功能:  
  
-   自动调整列表文档颜色。  
  
-   与文档一起保存状态并恢复其状态。  
  
-   管理“auto”按钮。  
  
-   使用 [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md) 控件选择自定义颜色。  
  
-   （如果它使用创建 [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md)\)，支持“拖曳”状态。  
  
 合并 `CMFCColorBar` 功能集成到应用程序中:  
  
1.  创建标准菜单按钮并将其分配ID，例如ID\_CHAR\_COLOR。  
  
2.  在框架窗口选件类，请重写 [CFrameWndEx::OnShowPopupMenu](../Topic/CFrameWndEx::OnShowPopupMenu.md) 方法并将 [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md) 对象替换常规菜单按钮\(通过调用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)）。  
  
3.  将所有样式并在 [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md) 创建时启用或禁用 `CMFCColorBar` 对象的功能。  框架调用 `CreatePopupMenu` 方法后，`CMFCColorMenuButton` 对象动态创建 `CMFCColorBar` 对象。  
  
 当用户单击以有色人种的可控制按钮时，框架使用 `ON_COMMAND` 宏注意到有色人种的、控件的父级。  在宏中，命令ID参数是可以分配给在步骤1中的值\(在此示例中的ID\_CHAR\_COLOR于有色人种的可控制按钮）。  有关更多信息，请参见 [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md)、 [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md)、 [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md)、 [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md)和 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md) 选件类。  
  
## 示例  
 通过在 `CMFCColorBar` 选件类，中的各种方法下面的示例演示如何配置为有色人种的区别不同。  方法设置水平和垂直边距，启用另一个按钮，创建对有色人种的、控件的窗口中，并将当前选定的颜色。  此示例是 [新的控件示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/CPP/cmfccolorbar-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/CPP/cmfccolorbar-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)  
  
 [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)  
  
## 要求  
 **标头:** afxcolorbar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)