---
title: "CMFCColorButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
dev_langs: C++
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
caps.latest.revision: "34"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cedbcd404e0f9dd575fe19486e97382e5975196c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton 类
`CMFCColorButton`和[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)类一起用于实现颜色选取器控件。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCColorButton : public CMFCButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|构造一个新`CMFCColorButton`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|启用和禁用位于常规颜色按钮上方的"自动"按钮。 (标准系统自动按钮标记为**自动**。)|  
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|启用和禁用位于常规颜色按钮下方的"其他"按钮。 ("其他"按钮标记为标准系统**其他颜色**。)|  
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|检索当前的自动颜色。|  
|[CMFCColorButton::GetColor](#getcolor)|检索按钮的颜色。|  
|[CMFCColorButton::SetColor](#setcolor)|设置按钮的颜色。|  
|[CMFCColorButton::SetColorName](#setcolorname)|设置颜色名称。|  
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|在颜色选取器对话框中设置列的数。|  
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|指定显示在颜色选取器对话框中的特定于文档的颜色的列表。|  
|[CMFCColorButton::SetPalette](#setpalette)|指定的标准显示颜色的调色板。|  
|[CMFCColorButton::SizeToContent](#sizetocontent)|该按钮控件，具体取决于其文本和图像的大小的大小更改。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|指示是否在 Windows XP 的视觉样式中显示当前颜色按钮。|  
|[CMFCColorButton::OnDraw](#ondraw)|由框架调用以显示该按钮的图像。|  
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|由框架调用以显示按钮的边框。|  
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|由框架调用以显示聚焦框，在按钮获得焦点时。|  
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|将要显示颜色选取器对话框中时，由框架调用。|  
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|初始化`m_pPalette`受保护的数据成员指定的调色板或默认系统调色板。|  
|[CMFCColorButton::UpdateColor](#updatecolor)|当用户选择一种颜色从调色板颜色选取器对话框中，由框架调用。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|`m_bAltColorDlg`|一个布尔值。 如果`TRUE`，框架显示[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)颜色对话框中时*其他*单击按钮时，或者如果`FALSE`，系统颜色对话框。 默认值为 `TRUE`。 有关详细信息，请参阅[CMFCColorButton::EnableOtherButton](#enableotherbutton)。|  
|`m_bAutoSetFocus`|一个布尔值。 如果`TRUE`，框架将焦点设置在颜色菜单上显示的菜单时，或如果`FALSE`，不会更改焦点。 默认值为 `TRUE`。|  
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|指示是否为颜色按钮启用自定义模式。|  
|`m_Color`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。 包含当前选定的颜色。|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。 包含当前所选的默认颜色。|  
|`m_Colors`|A [CArray](../../mfc/reference/carray-class.md)的[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。 包含当前可用的颜色。|  
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md)的[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。 包含当前文档颜色。|  
|`m_nColumns`|一个整数。 包含要在颜色选择菜单中的颜色的网格中显示列的数。|  
|`m_pPalette`|指向的指针[CPalette](../../mfc/reference/cpalette-class.md)。 包含当前颜色选择菜单中可用的颜色。|  
|`m_pPopup`|指向的指针[CMFCColorPopupMenu 类](../../mfc/reference/cmfccolorpopupmenu-class.md)对象。 单击颜色按钮时显示颜色选择菜单。|  
|`m_strAutoColorText`|一个字符串。 颜色选择菜单中的"自动"按钮的标签。|  
|`m_strDocColorsText`|一个字符串。 显示文档颜色颜色选择菜单中的按钮的标签。|  
|`m_strOtherText`|一个字符串。 颜色选择菜单中的"其他"按钮的标签。|  
  
## <a name="remarks"></a>备注  
 默认情况下，`CMFCColorButton`类的行为方式如打开一个颜色选取器对话框中的按钮。 颜色选取器对话框中包含小颜色按钮和一个"其他"按钮，可以显示自定义颜色选取器的数组。 ("其他"按钮标记为标准系统**其他颜色**。)当用户选择一种新颜色，`CMFCColorButton`对象将反映的更改并显示所选的颜色。  
  
 直接在代码中，或通过使用创建颜色按钮控件**ClassWizard**工具和对话框模板。 如果直接创建颜色按钮控件，添加`CMFCColorButton`变量与你的应用程序，然后调用构造函数和`Create`方法`CMFCColorButton`对象。 如果你使用**ClassWizard**，添加`CButton`变量与你的应用程序，然后将更改从变量的类型`CButton`到`CMFCColorButton`。  
  
 颜色选取器对话框中 ( [CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)) 显示[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)方法时，框架会调用`OnLButtonDown`事件处理程序。 [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)可以重写方法，以支持自定义颜色选择。  
  
 `CMFCColorButton`对象通知一种颜色更改通过将其发送其父级`WM_COMMAND | BN_CLICKED`通知。 使用父[CMFCColorButton::GetColor](#getcolor)方法来检索当前颜色。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法中的配置的颜色按钮`CMFCColorButton`类。 这些方法设置的颜色按钮和列，其数颜色，并启用自动和其他按钮。 此示例摘自[状态栏演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头：** afxcolorbutton.h  
  
##  <a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton  
 构造一个新`CMFCColorButton`对象。  
  
```  
CMFCColorButton();
```  
  
##  <a name="enableautomaticbutton"></a>CMFCColorButton::EnableAutomaticButton  
 启用或禁用颜色选取器控件的"自动"按钮并设置自动 （默认值） 颜色。  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLabel`  
 指定的自动按钮的文本。  
  
 [in] `colorAutomatic`  
 一个指定的自动按钮的默认颜色的 RGB 值。  
  
 [in] `bEnable`  
 指定是否启用或禁用自动按钮。  
  
### <a name="remarks"></a>备注  
  
##  <a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton  
 启用或禁用"其他"按钮，该按钮显示下方常规颜色按钮。  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLabel`  
 指定按钮的文本。  
  
 [in] `bAltColorDlg`  
 指定是否[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)用户单击按钮时打开对话框或系统颜色对话框。  
  
 [in] `bEnable`  
 指定是否启用或禁用"其他"按钮。  
  
### <a name="remarks"></a>备注  
 单击"其他"按钮以显示颜色对话框。 如果*bAltColorDlg*参数是`TRUE`、 [CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)会显示出来; 否则，系统颜色对话框中会显示。  
  
##  <a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor  
 检索当前的自动 （默认值） 颜色。  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 表示当前的自动颜色的 RGB 值。  
  
### <a name="remarks"></a>备注  
 通过设置当前的自动配色[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)方法。  
  
##  <a name="getcolor"></a>CMFCColorButton::GetColor  
 检索当前所选的颜色。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 RGB 值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme  
 指示是否在 Windows XP 的视觉样式中显示当前颜色按钮。  
  
```  
BOOL IsDrawXPTheme() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果支持视觉样式和当前的颜色按钮显示在 Windows XP; 的视觉样式否则为`FALSE`。  
  
##  <a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode  
 设置为自定义模式的颜色按钮。  
  
```  
BOOL m_bEnabledInCustomizeMode;  
```  
  
### <a name="remarks"></a>备注  
 如果你需要将颜色按钮添加到自定义对话框的页 （或允许用户可以在自定义过程中的另一个颜色选择），通过设置启用按钮`m_bEnabledInCustomizeMode`成员`TRUE`。 默认情况下，此成员设置为`FALSE`。  
  
##  <a name="ondraw"></a>CMFCColorButton::OnDraw  
 由框架调用以呈现按钮的图像。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 用于呈现按钮的图像的设备上下文的点。  
  
 [in] `rect`  
 限定按钮的矩形。  
  
 [in] `uiState`  
 指定按钮的可视状态。  
  
### <a name="remarks"></a>备注  
 重写此方法以自定义呈现进程。  
  
##  <a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder  
 由框架调用以显示按钮的边框。  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 用于绘制边框的设备上下文的点。  
  
 [in] `rectClient`  
 通过指定的设备上下文中的矩形`pDC`定义要绘制的按钮的边界的参数。  
  
 [in] `uiState`  
 指定按钮的可视状态。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义颜色按钮的边框外观。  
  
##  <a name="ondrawfocusrect"></a>CMFCColorButton::OnDrawFocusRect  
 由框架调用以显示聚焦框，在按钮获得焦点时。  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 用于绘制聚焦框的设备上下文的点。  
  
 [in] `rectClient`  
 通过指定的设备上下文中的矩形`pDC`参数定义按钮的边界。  
  
### <a name="remarks"></a>备注  
 重写此方法以自定义的焦点矩形的外观。  
  
##  <a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup  
 在弹出窗口颜色栏会显示之前调用。  
  
```  
virtual void OnShowColorPopup();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="rebuildpalette"></a>CMFCColorButton::RebuildPalette  
 初始化`m_pPalette`受保护的数据成员指定的调色板或默认系统调色板。  
  
```  
void RebuildPalette(CPalette* pPal);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pPal`|指向逻辑调色板的指针或`NULL`。 如果`NULL`，使用默认系统调色板。|  
  
##  <a name="setcolor"></a>CMFCColorButton::SetColor  
 指定按钮的颜色。  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 RGB 值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setcolorname"></a>CMFCColorButton::SetColorName  
 指定的一种颜色的名称。  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 颜色的 RGB 值。  
  
 [in] `strName`  
 颜色的名称。  
  
### <a name="remarks"></a>备注  
 颜色名称的列表是每个应用程序全局设置。 因此，此方法将传输到其参数[CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname)。  
  
##  <a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber  
 定义在用户的颜色选择过程中向用户显示的颜色表中显示的列数。  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>参数  
 [in] `nColumns`  
 指定列的数。  
  
### <a name="remarks"></a>备注  
 用户可以从显示的预定义颜色表的弹出窗口颜色栏选择一种颜色。 使用此方法用于定义表中的列数。  
  
##  <a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors  
 指定一组颜色和集的名称。 使用显示的一组颜色[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)对象。  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLabel`  
 指定与在文档颜色组中显示的标签。  
  
 [in] `lstColors`  
 对的 RGB 值列表的引用。  
  
### <a name="remarks"></a>备注  
 A`CMFCColorButton`对象保留的数据库传输到的 RGB 值列表[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)对象。 这些颜色时显示颜色栏，则将显示其标签指定由某个特殊部分`lpszLabel`参数。  
  
##  <a name="setpalette"></a>CMFCColorButton::SetPalette  
 指定要在弹出窗口颜色栏上显示的标准颜色。  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>参数  
 [in] `pPalette`  
 指向一个调色板的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="sizetocontent"></a>CMFCColorButton::SizeToContent  
 调整大小以适应其文本和图像的按钮控件。  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bCalcOnly`  
 如果不为零，计算按钮控件的新大小，但未更改的实际大小。  
  
### <a name="return-value"></a>返回值  
 A`CSize`指定新的按钮控件大小的对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="updatecolor"></a>CMFCColorButton::UpdateColor  
 当用户选择一种颜色从颜色栏中，当用户单击此颜色按钮显示时，由框架调用。  
  
```  
virtual void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 由用户选定的颜色。  
  
### <a name="remarks"></a>备注  
 `UpdateColor`函数当前所选的按钮的颜色更改，并通过发送通知其父级`WM_COMMAND`消息`BN_CLICKED`标准通知。 使用[CMFCColorButton::GetColor](#getcolor)方法来检索所选的颜色。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)   
 [CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [CPalette 类](../../mfc/reference/cpalette-class.md)   
 [CArray 类](../../mfc/reference/carray-class.md)   
 [CList 类](../../mfc/reference/clist-class.md)   
 [CString](../../atl-mfc-shared/reference/cstringt-class.md)
