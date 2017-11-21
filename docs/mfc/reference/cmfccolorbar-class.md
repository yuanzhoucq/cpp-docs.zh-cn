---
title: "CMFCColorBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorBar
- AFXCOLORBAR/CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::ContextToSize
- AFXCOLORBAR/CMFCColorBar::CreateControl
- AFXCOLORBAR/CMFCColorBar::Create
- AFXCOLORBAR/CMFCColorBar::EnableAutomaticButton
- AFXCOLORBAR/CMFCColorBar::EnableOtherButton
- AFXCOLORBAR/CMFCColorBar::GetColor
- AFXCOLORBAR/CMFCColorBar::GetCommandID
- AFXCOLORBAR/CMFCColorBar::GetHighlightedColor
- AFXCOLORBAR/CMFCColorBar::GetHorzMargin
- AFXCOLORBAR/CMFCColorBar::GetVertMargin
- AFXCOLORBAR/CMFCColorBar::IsTearOff
- AFXCOLORBAR/CMFCColorBar::SetColor
- AFXCOLORBAR/CMFCColorBar::SetColorName
- AFXCOLORBAR/CMFCColorBar::SetCommandID
- AFXCOLORBAR/CMFCColorBar::SetDocumentColors
- AFXCOLORBAR/CMFCColorBar::SetHorzMargin
- AFXCOLORBAR/CMFCColorBar::SetVertMargin
- AFXCOLORBAR/CMFCColorBar::AdjustLocations
- AFXCOLORBAR/CMFCColorBar::AllowChangeTextLabels
- AFXCOLORBAR/CMFCColorBar::AllowShowOnList
- AFXCOLORBAR/CMFCColorBar::CalcSize
- AFXCOLORBAR/CMFCColorBar::CreatePalette
- AFXCOLORBAR/CMFCColorBar::GetColorGridSize
- AFXCOLORBAR/CMFCColorBar::GetExtraHeight
- AFXCOLORBAR/CMFCColorBar::InitColors
- AFXCOLORBAR/CMFCColorBar::OnKey
- AFXCOLORBAR/CMFCColorBar::OnSendCommand
- AFXCOLORBAR/CMFCColorBar::OnUpdateCmdUI
- AFXCOLORBAR/CMFCColorBar::OpenColorDialog
- AFXCOLORBAR/CMFCColorBar::Rebuild
- AFXCOLORBAR/CMFCColorBar::SelectPalette
- AFXCOLORBAR/CMFCColorBar::SetPropList
- AFXCOLORBAR/CMFCColorBar::ShowCommandMessageString
dev_langs: C++
helpviewer_keywords:
- CMFCColorBar [MFC], CMFCColorBar
- CMFCColorBar [MFC], ContextToSize
- CMFCColorBar [MFC], CreateControl
- CMFCColorBar [MFC], Create
- CMFCColorBar [MFC], EnableAutomaticButton
- CMFCColorBar [MFC], EnableOtherButton
- CMFCColorBar [MFC], GetColor
- CMFCColorBar [MFC], GetCommandID
- CMFCColorBar [MFC], GetHighlightedColor
- CMFCColorBar [MFC], GetHorzMargin
- CMFCColorBar [MFC], GetVertMargin
- CMFCColorBar [MFC], IsTearOff
- CMFCColorBar [MFC], SetColor
- CMFCColorBar [MFC], SetColorName
- CMFCColorBar [MFC], SetCommandID
- CMFCColorBar [MFC], SetDocumentColors
- CMFCColorBar [MFC], SetHorzMargin
- CMFCColorBar [MFC], SetVertMargin
- CMFCColorBar [MFC], AdjustLocations
- CMFCColorBar [MFC], AllowChangeTextLabels
- CMFCColorBar [MFC], AllowShowOnList
- CMFCColorBar [MFC], CalcSize
- CMFCColorBar [MFC], CreatePalette
- CMFCColorBar [MFC], GetColorGridSize
- CMFCColorBar [MFC], GetExtraHeight
- CMFCColorBar [MFC], InitColors
- CMFCColorBar [MFC], OnKey
- CMFCColorBar [MFC], OnSendCommand
- CMFCColorBar [MFC], OnUpdateCmdUI
- CMFCColorBar [MFC], OpenColorDialog
- CMFCColorBar [MFC], Rebuild
- CMFCColorBar [MFC], SelectPalette
- CMFCColorBar [MFC], SetPropList
- CMFCColorBar [MFC], ShowCommandMessageString
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 031a26d0b7b461c64bd111d26811ccf4031694c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar 类
`CMFCColorBar`类表示可在文档或应用程序中选择颜色的停靠控件条。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCColorBar : public CMFCPopupMenuBar  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|构造 `CMFCColorBar` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCColorBar::ContextToSize](#contexttosize)|计算所需包含颜色栏控件上的按钮，然后调整这些按钮的位置的水平和垂直边距。|  
|[CMFCColorBar::CreateControl](#createcontrol)|创建一个颜色栏控件窗口，将其附加到`CMFCColorBar`对象，并调整其大小要包含的指定的调色板的控件。|  
|[CMFCColorBar::Create](#create)|创建颜色栏控件窗口，并将其附加到`CMFCColorBar`对象。|  
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|显示或隐藏自动按钮。|  
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|启用或禁用可让用户选择多个颜色对话框中的显示。|  
|[CMFCColorBar::GetColor](#getcolor)|检索当前所选的颜色。|  
|[CMFCColorBar::GetCommandID](#getcommandid)|检索当前颜色栏控件的命令 ID。|  
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|检索表示的颜色按钮具有焦点，则颜色按钮，即是*热*。|  
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|检索的水平边缘，这是左侧或正确的颜色单元格和客户端区域边界之间的空间。|  
|[CMFCColorBar::GetVertMargin](#getvertmargin)|检索的垂直边缘，即顶部或底部颜色单元格的客户端区域边界之间的空间。|  
|[CMFCColorBar::IsTearOff](#istearoff)|指示当前颜色栏是否可停靠。|  
|[CMFCColorBar::SetColor](#setcolor)|设置当前选定的颜色。|  
|[CMFCColorBar::SetColorName](#setcolorname)|设置指定的颜色的新名称。|  
|[CMFCColorBar::SetCommandID](#setcommandid)|设置颜色栏控件的新命令 ID。|  
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|设置当前文档中使用的颜色的列表。|  
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|设置水平边距，这是左侧或正确的颜色单元格和客户端区域边界之间的空间。|  
|[CMFCColorBar::SetVertMargin](#setvertmargin)|设置的垂直边缘，即顶部或底部颜色单元格的客户端区域边界之间的空间。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCColorBar::AdjustLocations](#adjustlocations)|调整颜色栏控件上的颜色按钮的位置。|  
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|指示是否可以更改颜色按钮的文本标签。|  
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|指示是否颜色栏控件对象可以出现在工具栏列表自定义过程。|  
|[CMFCColorBar::CalcSize](#calcsize)|由框架作为布局计算过程的一部分调用。|  
|[CMFCColorBar::CreatePalette](#createpalette)|初始化与指定的颜色数组中的颜色的调色板。|  
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|计算行和在颜色栏控件的网格中的列的数。|  
|[CMFCColorBar::GetExtraHeight](#getextraheight)|计算当前颜色栏显示其他用户界面元素，如所需的其他高度**其他**按钮、 文档颜色等。|  
|[CMFCColorBar::InitColors](#initcolors)|初始化数组中指定的调色板或系统默认调色板的颜色的颜色。|  
|[CMFCColorBar::OnKey](#onkey)|当用户按下键盘按钮时，由框架调用。|  
|[CMFCColorBar::OnSendCommand](#onsendcommand)|由框架调用以关闭弹出窗口控件的层次结构。|  
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|由框架调用以启用或禁用颜色栏控件的用户界面项之前显示该项。|  
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|打开颜色对话框。|  
|[CMFCColorBar::Rebuild](#rebuild)|完全重绘颜色栏控件。|  
|[CMFCColorBar::SelectPalette](#selectpalette)|将指定的设备上下文逻辑调色板设置为当前颜色栏控件的父按钮的调色板。|  
|[CMFCColorBar::SetPropList](#setproplist)|集`m_pWndPropList`保护指向属性网格控件的指定指针的数据成员。|  
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|请求拥有要更新在状态栏中的消息行的颜色栏控件的框架窗口。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|`m_bInternal`|确定是否处理鼠标事件布尔字段。 此字段时，通常情况下，处理鼠标事件`TRUE`和自定义模式是`FALSE`。|  
|`m_bIsEnabled`|一个布尔值，该值指示控件是否已启用。|  
|`m_bIsTearOff`|一个布尔值，该值指示是否颜色栏控件支持停靠。|  
|`m_BoxSize`|A [CSize](../../atl-mfc-shared/reference/csize-class.md)对象，它指定在颜色栏网格中的单元格的大小。|  
|`m_bShowDocColorsWhenDocked`|一个布尔值，该值指示是否停靠在颜色栏时显示文档的颜色。 有关详细信息，请参阅[CMFCColorBar::SetDocumentColors](#setdocumentcolors)。|  
|`m_bStdColorDlg`|一个布尔值，该值指示是否显示标准系统颜色对话框中或[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)对话框。 有关详细信息，请参阅[CMFCColorBar::EnableOtherButton](#enableotherbutton)。|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)存储当前自动颜色。 有关详细信息，请参阅[CMFCColorBar::EnableOtherButton](#enableotherbutton)。|  
|`m_ColorNames`|[CMap](../../mfc/reference/cmap-class.md)对象关联一组的 RGB 颜色由其名称。|  
|`m_colors`|A [CArray](../../mfc/reference/carray-class.md)的[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)包含颜色栏控件中显示的颜色的值。|  
|`m_ColorSelected`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值是用户当前已选择从颜色栏控件的颜色。|  
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md)的[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)包含当前正用于在文档中的颜色的值。|  
|`m_nCommandID`|是的颜色按钮的命令 ID 的无符号的整数。|  
|`m_nHorzMargin`|一个整数，表示颜色的网格中的颜色按钮之间的水平间距。|  
|`m_nHorzOffset`|一个整数，表示为中心的颜色按钮的水平偏移量。 如果按钮显示的文本或图像除了一种颜色，则此值至关重要。|  
|`m_nNumColumns`|一个整数，表示的颜色的颜色栏控件网格中的列数。|  
|`m_nNumColumnsVert`|一个整数，表示在垂直方向的颜色的网格中的列数。|  
|`m_nNumRowsHorz`|一个整数，表示在水平方向的颜色的网格中的列数。|  
|`m_nRowHeight`|一个整数，表示在网格中的颜色的颜色按钮的行的高度。|  
|`m_nVertMargin`|一个整数，表示颜色的网格中的颜色按钮之间的垂直间距。|  
|`m_nVertOffset`|一个整数，表示为中心的颜色按钮的垂直偏移量。 如果按钮显示的文本或图像除了一种颜色，则此值至关重要。|  
|`m_Palette`|A [CPalette](../../mfc/reference/cpalette-class.md)颜色栏控件中使用的颜色。|  
|`m_pParentBtn`|指向的指针[CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)是当前的按钮的父级的对象。 如果颜色按钮在工具栏控件的层次结构或在颜色属性网格控件中，此值是重要的。|  
|`m_pParentRibbonBtn`|指向的指针[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)对象，是功能区上和当前按钮的父按钮。 如果颜色按钮在工具栏控件的层次结构或在颜色属性网格控件中，此值是重要的。|  
|`m_pWndPropList`|指向的指针[CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)对象。|  
|`m_strAutoColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示显示的文本**自动**按钮。 有关详细信息，请参阅[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)。|  
|`m_strDocColors`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示在文档颜色按钮显示的文本。 有关详细信息，请参阅[CMFCColorBar::SetDocumentColors](#setdocumentcolors)。|  
|`m_strOtherColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示显示的文本*其他*按钮。 有关详细信息，请参阅[CMFCColorBar::EnableOtherButton](#enableotherbutton)。|  
  
## <a name="remarks"></a>备注  
 通常情况下，你不创建`CMFCColorBar`直接对象。 相反， [CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)（在菜单和工具栏中使用） 或[CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)创建`CMFCColorBar`对象。  
  
 `CMFCColorBar`类提供了以下功能：  
  
-   自动调整文档颜色的列表。  
  
-   保存并还原其状态，以及文档状态。  
  
-   管理"自动"按钮。  
  
-   使用[CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)选择自定义颜色的控件。  
  
-   支持"拖曳"状态 (如果它由使用创建[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md))。  
  
 若要将合并`CMFCColorBar`功能集成到你的应用程序：  
  
1.  创建一个常规菜单按钮，并将其分配的 ID，例如 ID_CHAR_COLOR。  
  
2.  在框架窗口类，重写[CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu)方法，并将常规菜单按钮与其[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)对象 (通过调用[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton))。  
  
3.  设置所有的样式以及启用或禁用的功能`CMFCColorBar`对象期间[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)创建。 `CMFCColorMenuButton`对象动态创建`CMFCColorBar`对象后框架调用`CreatePopupMenu`方法。  
  
 当用户单击颜色栏控件按钮时，框架将使用`ON_COMMAND`宏来通知颜色栏控件的父级。 在宏，命令 ID 参数是分配到在步骤 1 (在此示例中的 ID_CHAR_COLOR) 中的颜色栏控件按钮的值。 有关详细信息，请参阅[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)， [CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)， [CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)， [CFrameWndEx 类](../../mfc/reference/cframewndex-class.md)，和[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)类。  
  
## <a name="example"></a>示例  
 下面的示例演示如何通过使用中的各种方法配置一个颜色栏`CMFCColorBar`类。 方法设置水平和垂直边距、 启用其他按钮，创建颜色栏控件窗口和设置当前选定的颜色。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)  
  
 [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxcolorbar.h  
  
##  <a name="adjustlocations"></a>CMFCColorBar::AdjustLocations  
 调整颜色栏控件上的颜色按钮的位置。  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>备注  
 由框架在调用此方法`WM_SIZE`消息处理。  
  
##  <a name="allowchangetextlabels"></a>CMFCColorBar::AllowChangeTextLabels  
 指示是否可以更改颜色按钮的文本标签。  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>返回值  
 总是为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法始终返回`FALSE`，这意味着文本标签不能修改。 重写此方法以启用修改文本标签。  
  
##  <a name="allowshowonlist"></a>CMFCColorBar::AllowShowOnList  
 指示是否颜色栏控件对象可以出现在工具栏列表自定义过程。  
  
```  
virtual BOOL AllowShowOnList() const;  
```  
  
### <a name="return-value"></a>返回值  
 总是为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法始终返回`TRUE`，这意味着框架可以在自定义过程下显示的颜色栏控件。 重写此方法以实现不同的行为。  
  
##  <a name="calcsize"></a>CMFCColorBar::CalcSize  
 由框架作为布局计算过程的一部分调用。  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>参数  
 [in] `bVertDock`  
 `TRUE`若要指定颜色栏控件垂直; 停靠`FALSE`指定水平停靠颜色栏控件。  
  
### <a name="return-value"></a>返回值  
 在颜色栏控件中的颜色按钮的数组的大小。  
  
##  <a name="cmfccolorbar"></a>CMFCColorBar::CMFCColorBar  
 构造 `CMFCColorBar` 对象。  
  
```  
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors,  
    CList<COLORREF,COLORREF>& lstDocColors,  
    int nColumns,  
    int nRowsDockHorz,  
    int nColDockVert,  
    COLORREF colorAutomatic,  
    UINT nCommandID,  
    CMFCColorButton* pParentBtn);

 
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors,  
    CList<COLORREF,COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic,  
    UINT nCommandID,  
    CMFCRibbonColorButton* pParentRibbonBtn);

 
CMFCColorBar(
    CMFCColorBar& src,  
    UINT uiCommandID);
```  
  
### <a name="parameters"></a>参数  
 [in] `colors`  
 框架在颜色栏控件显示的颜色的数组。  
  
 [in] `color`  
 初始选定的颜色。  
  
 [in] `lpszAutoColor`  
 文本标签*自动*（默认值） 颜色按钮，或`NULL`。  
  
 自动按钮的标准标签是**自动**。  
  
 [in] `lpszOtherColor`  
 文本标签*其他*按钮，用于显示其他颜色选项，或`NULL`。  
  
 其他按钮的标准标签是**其他颜色...**.  
  
 [in] `lpszDocColors`  
 文档颜色按钮文本标签。 文档调色板列出所有文档当前使用的颜色。  
  
 [in] `lstDocColors`  
 该文档当前使用的颜色的列表。  
  
 [in] `nColumns`  
 颜色数组具有的列数。  
  
 [in] `nRowsDockHorz`  
 在颜色栏具有时水平停靠的行数。  
  
 [in] `nColDockVert`  
 在颜色栏具有垂直停靠时的列数。  
  
 [in] `colorAutomatic`  
 单击自动按钮时，将应用框架默认颜色。  
  
 [in] `nCommandID`  
 颜色栏控件命令 id。  
  
 [in] `pParentBtn`  
 指向父按钮的指针。  
  
 [in] `src`  
 现有`CMFCColorBar`要复制到新对象`CMFCColorBar`对象。  
  
 [in] `uiCommandID`  
 命令 ID。  
  
##  <a name="contexttosize"></a>CMFCColorBar::ContextToSize  
 计算所必须包含在颜色栏控件上的按钮，并且这些按钮的位置调整水平和垂直边距。  
  
```  
void ContextToSize(
    BOOL bSquareButtons = TRUE,   
    BOOL bCenterButtons = TRUE);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `bSquareButtons`|`TRUE`若要指定形状的颜色栏控件上的按钮是正方形;否则为`FALSE`。 默认值为 `TRUE`。|  
|[in] `bCenterButtons`|`TRUE`若要指定，颜色栏控件按钮的表面上内容居中;否则为`FALSE`。 默认值为 `TRUE`。|  
  
### <a name="remarks"></a>备注  
  
##  <a name="create"></a>CMFCColorBar::Create  
 创建颜色栏控件窗口，并将其附加到`CMFCColorBar`对象。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle,  
    UINT nID,  
    CPalette* pPalette=NULL,  
    int nColumns=0,  
    int nRowsDockHorz=0,  
    int nColDockVert=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParentWnd`  
 向父窗口的指针。  
  
 [in] `dwStyle`  
 按位组合 (OR)[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。  
  
 [in] `nID`  
 命令 ID。  
  
 [in] `pPalette`  
 指向一个颜色的调色板。 默认值为 `NULL`。  
  
 [in] `nColumns`  
 在颜色栏控件中的列数。 默认值为 0。  
  
 [in] `nRowsDockHorz`  
 在颜色栏控件时水平停靠的行数。 默认值为 0。  
  
 [in] `nColDockVert`  
 在颜色栏控件垂直停靠停靠时中的列数。 默认值为 0。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 若要构造`CMFCColorBar`对象，请调用类构造函数，则此方法。 `Create`方法创建 Windows 控件，并初始化颜色的列表。  
  
##  <a name="createcontrol"></a>CMFCColorBar::CreateControl  
 创建一个颜色栏控件窗口，将其附加到`CMFCColorBar`对象，并调整其大小控制窗口，以包含指定的调色板的颜色。  
  
```  
virtual BOOL CreateControl(
    CWnd* pParentWnd,  
    const CRect& rect,  
    UINT nID,  
    int nColumns=-1,  
    CPalette* pPalette=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParentWnd`  
 向父窗口的指针。 不能为 `NULL`。  
  
 [in] `rect`  
 指定在哪里可以绘制颜色栏控件边界矩形。  
  
 [in] `nID`  
 控件 id。  
  
 [in] `nColumns`  
 理想的颜色栏控件中的列数。 此方法修改该编号，以适应指定的调色板的颜色。 默认值为-1，这意味着未指定此参数。  
  
 [in] `pPalette`  
 指针到调色板的颜色，或`NULL`。 如果此参数为`NULL`，如同 20 颜色指定，此方法计算颜色栏控件的大小。 默认值为 `NULL`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法使用`rect`， `nColumns`，和`pPalette`参数来计算的适当数量或行和列在颜色栏控件，然后调用[CMFCColorBar::Create](#create)方法。  
  
##  <a name="createpalette"></a>CMFCColorBar::CreatePalette  
 初始化与指定的颜色数组中的颜色的调色板。  
  
```  
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,   
    CPalette& palette);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `arColors`|颜色数组。|  
|[in] `palette`|颜色的调色板。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `TRUE`；否则为 `FALSE`。  
  
##  <a name="enableautomaticbutton"></a>CMFCColorBar::EnableAutomaticButton  
 显示或隐藏自动按钮。  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLabel`  
 文本标签*自动*（默认值） 颜色按钮，或`NULL`。  
  
 自动按钮的标准标签是**自动**。  
  
 [in] `colorAutomatic`  
 单击自动按钮时，将应用框架默认颜色。  
  
 [in] `bEnable`  
 `TRUE`若要启用自动按钮;`FALSE`若要禁用自动按钮。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 如果删除的自动按钮的文本标签`lpszLabel`参数是`NULL`或`bEnable`参数是`FALSE`。  
  
##  <a name="enableotherbutton"></a>CMFCColorBar::EnableOtherButton  
 启用或禁用可让用户选择多个颜色对话框中的显示。  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLabel`  
 文本标签*其他*按钮，用于显示其他颜色选项，或`NULL`。  
  
 此按钮的标准标签是**其他颜色...**.  
  
 [in] `bAltColorDlg`  
 `TRUE`若要显示[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)对话框;`FALSE`以显示标准[CColorDialog](../../mfc/reference/ccolordialog-class.md)对话框。 默认值为 `TRUE`。  
  
 [in] `bEnable`  
 `TRUE`若要启用按钮;`FALSE`禁用按钮。 默认值为 `TRUE`。  
  
##  <a name="getcolor"></a>CMFCColorBar::GetColor  
 检索当前所选的颜色。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前选定的颜色。  
  
##  <a name="getcolorgridsize"></a>CMFCColorBar::GetColorGridSize  
 计算行和在颜色栏控件的网格中的列的数。  
  
```  
CSize GetColorGridSize(BOOL bVertDock) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `bVertDock`|`TRUE`若要执行计算的垂直停靠的颜色栏控件;否则，请执行计算的水平停靠的控件。|  
  
### <a name="return-value"></a>返回值  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)对象，其`cx`组件包含列数以及其`cy`组件包含的行数。  
  
##  <a name="getcommandid"></a>CMFCColorBar::GetCommandID  
 检索当前颜色栏控件的命令 ID。  
  
```  
UINT GetCommandID() const;  
```  
  
### <a name="return-value"></a>返回值  
 命令 id。  
  
### <a name="remarks"></a>备注  
 当用户选择一种新颜色时，框架会将命令 ID 发送`WM_COMMAND`消息通知的父`CMFCColorBar`对象。  
  
##  <a name="getextraheight"></a>CMFCColorBar::GetExtraHeight  
 计算当前颜色栏显示其他用户界面元素，如所需的其他高度**其他**按钮或文档的颜色。  
  
```  
int GetExtraHeight(int nNumColumns) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `nNumColumns`|如果颜色栏控件包含文档颜色，要在文档颜色的网格中显示的列数。 否则，不使用此值。|  
  
### <a name="return-value"></a>返回值  
 需要计算额外高度。  
  
##  <a name="gethighlightedcolor"></a>CMFCColorBar::GetHighlightedColor  
 检索表示的颜色按钮具有焦点，则颜色按钮，即是*热*。  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 RGB 值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gethorzmargin"></a>CMFCColorBar::GetHorzMargin  
 检索的水平边缘，这是左侧或正确的颜色单元格和客户端区域边界之间的空间。  
  
```  
int GetHorzMargin();
```  
  
### <a name="return-value"></a>返回值  
 水平的边距。  
  
##  <a name="getvertmargin"></a>CMFCColorBar::GetVertMargin  
 检索的垂直边缘，即顶部或底部颜色单元格的客户端区域边界之间的空间。  
  
```  
int GetVertMargin() const;  
```  
  
### <a name="return-value"></a>返回值  
 垂直边距。  
  
##  <a name="initcolors"></a>CMFCColorBar::InitColors  
 初始化使用指定的调色板中的颜色或使用系统默认调色板的颜色的数组。  
  
```  
static int InitColors(
    CPalette* pPalette,   
    CArray<COLORREF, COLORREF>& arColors);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pPalette`|调色板对象、 指针或`NULL`。 如果此参数为`NULL`，此方法使用默认调色板的操作系统。|  
|[in] `arColors`|颜色数组。|  
  
### <a name="return-value"></a>返回值  
 中的颜色数组的元素数。  
  
##  <a name="istearoff"></a>CMFCColorBar::IsTearOff  
 指示当前颜色栏是否可停靠。  
  
```  
BOOL IsTearOff() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果当前颜色栏控件是可停靠;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果颜色栏控件是可停靠，它可以中拉出的控件条和停靠在另一个位置。  
  
##  <a name="onkey"></a>CMFCColorBar::OnKey  
 当用户按下键盘按钮时，由框架调用。  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>参数  
 [in] `nChar`  
 用户按下键的虚拟键代码。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法可处理指定的键;，否则为`FALSE`。  
  
##  <a name="onsendcommand"></a>CMFCColorBar::OnSendCommand  
 由框架调用以关闭弹出控件的层次结构。  
  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pButton`|指向驻留在工具栏的控件。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `TRUE`；否则为 `FALSE`。  
  
##  <a name="onupdatecmdui"></a>CMFCColorBar::OnUpdateCmdUI  
 由框架调用以启用或禁用颜色栏控件的用户界面项之前显示该项。  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>参数  
 [in] `pTarget`  
 指向包含要更新的用户界面项的窗口的指针。  
  
 [in] `bDisableIfNoHndler`  
 `TRUE`若要禁用的用户界面项，如果没有处理的消息映射; 中定义否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当你的应用程序的用户单击用户界面项时，该项必须知道是否它应显示为已启用或禁用。 命令消息的目标提供此信息通过实现`ON_UPDATE_COMMAND_UI`命令处理程序。 使用此方法有助于处理命令。 有关详细信息，请参阅[CCmdUI 类](../../mfc/reference/ccmdui-class.md)。  
  
##  <a name="opencolordialog"></a>CMFCColorBar::OpenColorDialog  
 打开颜色对话框。  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>参数  
 [in] `colorDefault`  
 颜色对话框中打开时默认选择颜色。  
  
 [out] `colorRes`  
 用户选择了颜色。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果用户选择一种颜色;，`FALSE`如果用户已取消颜色对话框。  
  
### <a name="remarks"></a>备注  
  
##  <a name="rebuild"></a>CMFCColorBar::Rebuild  
 完全重绘颜色栏控件。  
  
```  
virtual void Rebuild();
```  
  
##  <a name="selectpalette"></a>CMFCColorBar::SelectPalette  
 将指定的设备上下文逻辑调色板设置为当前颜色栏控件的父按钮的调色板。  
  
```  
CPalette* SelectPalette(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pDC`|当前颜色栏控件的父按钮的设备上下文的指针。|  
  
### <a name="return-value"></a>返回值  
 指向替换为当前颜色栏控件的父按钮调色板调色板。  
  
##  <a name="setcolor"></a>CMFCColorBar::SetColor  
 设置当前选定的颜色。  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 RGB 颜色值。  
  
##  <a name="setcolorname"></a>CMFCColorBar::SetColorName  
 设置指定的颜色的新名称。  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 一种颜色的 RGB 值。  
  
 [in] `strName`  
 指定颜色新名称。  
  
### <a name="remarks"></a>备注  
 此方法会在所有指定的颜色的名称更改`CMFCColorBar`你的应用程序中的对象。  
  
##  <a name="setcommandid"></a>CMFCColorBar::SetCommandID  
 设置颜色栏控件的新命令 ID。  
  
```  
void SetCommandID(UINT nCommandID);
```  
  
### <a name="parameters"></a>参数  
 [in] `nCommandID`  
 命令 id。  
  
### <a name="remarks"></a>备注  
 调用此方法用于修改颜色栏控件的命令 ID 以及用于通知的 ID 已更改的控件的父窗口。  
  
##  <a name="setdocumentcolors"></a>CMFCColorBar::SetDocumentColors  
 设置当前文档中使用的颜色的列表。  
  
```  
void SetDocumentColors(
    LPCTSTR lpszCaption,  
    CList<COLORREF,COLORREF>& lstDocColors,  
    BOOL bShowWhenDocked=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszCaption`  
 不停靠颜色栏控件时显示的标题。  
  
 [in] `lstDocColors`  
 替换当前的文档颜色的颜色列表。  
  
 [in] `bShowWhenDocked`  
 `TRUE`要在颜色栏控件停靠; 后显示文档颜色否则为`FALSE`。 默认值为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 *文档颜色*是当前正用于在文档中的颜色。 框架自动维护文档颜色的列表，但你可以使用此方法可以修改的列表。  
  
##  <a name="sethorzmargin"></a>CMFCColorBar::SetHorzMargin  
 设置水平边距，这是左侧或正确的颜色单元格的工作区的边界之间的空间。  
  
```  
void SetHorzMargin(int nHorzMargin);
```  
  
### <a name="parameters"></a>参数  
 [in] `nHorzMargin`  
 水平的边距，以像素为单位。  
  
### <a name="remarks"></a>备注  
 默认情况下， [CMFCColorBar::CMFCColorBar](#cmfccolorbar)构造函数将水平边距设置为 4 像素。  
  
##  <a name="setproplist"></a>CMFCColorBar::SetPropList  
 集`m_pWndPropList`保护指向属性网格控件的指定指针的数据成员。  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pWndList`|为属性网格控件对象的指针。|  
  
##  <a name="setvertmargin"></a>CMFCColorBar::SetVertMargin  
 设置的垂直边缘，即顶部或底部颜色单元格的客户端区域边界之间的空间。  
  
```  
void SetVertMargin(int nVertMargin);
```  
  
### <a name="parameters"></a>参数  
 [in] `nVertMargin`  
 垂直的边距，以像素为单位。  
  
### <a name="remarks"></a>备注  
 默认情况下， [CMFCColorBar::CMFCColorBar](#cmfccolorbar)构造函数设置为 4 像素的垂直边距。  
  
##  <a name="showcommandmessagestring"></a>CMFCColorBar::ShowCommandMessageString  
 请求拥有要更新在状态栏中的消息行的颜色栏控件的框架窗口。  
  
```  
virtual void ShowCommandMessageString(UINT uiCmdId);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdId`  
 命令 id。 （忽略此参数。）  
  
### <a name="remarks"></a>备注  
 此方法可发送`WM_SETMESSAGESTRING`颜色栏控件的所有者的消息。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
