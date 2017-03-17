---
title: "CMFCColorButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorButton::m_Color data member
- CMFCColorButton::m_bAutoSetFocus data member
- CMFCColorButton::m_pPopup data member
- CMFCColorButton::m_nColumns data member
- CMFCColorButton class
- CMFCColorButton::m_strAutoColorText data member
- CMFCColorButton::m_bAltColorDlg data member
- CMFCColorButton::m_strDocColorsText data member
- CMFCColorButton::m_strOtherText data member
- CMFCColorButton::m_pPalette data member
- CMFCColorButton::m_lstDocColors data member
- CMFCColorButton::m_ColorAutomatic data member
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
caps.latest.revision: 34
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6a9290d396c8ce5ccafa2ae556b21ff89806d830
ms.lasthandoff: 02/24/2017

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
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|启用和禁用定位在正则颜色按钮上方的"自动"按钮。 (标准系统自动按钮标记为**自动**。)|  
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|启用和禁用位于常规彩色按钮的下方的"其他"按钮。 ("Other"按钮被标记为标准系统**其他颜色...**.)|  
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|检索当前的自动颜色。|  
|[CMFCColorButton::GetColor](#getcolor)|检索一个按钮的颜色。|  
|[CMFCColorButton::SetColor](#setcolor)|设置按钮的颜色。|  
|[CMFCColorButton::SetColorName](#setcolorname)|设置颜色名称。|  
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|在颜色选取器对话框中设置列的数。|  
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|指定显示在颜色选取器对话框中的特定于文档的颜色的列表。|  
|[CMFCColorButton::SetPalette](#setpalette)|指定一个标准显示颜色的调色板。|  
|[CMFCColorButton::SizeToContent](#sizetocontent)|更改该按钮控件，具体取决于它的文本和图像的大小的大小。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|指示是否在 Windows XP 的视觉样式中显示颜色按钮。|  
|[CMFCColorButton::OnDraw](#ondraw)|由框架后，才会显示该按钮的图像调用。|  
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|由要显示该按钮的边框的框架调用。|  
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|由框架以显示聚焦框按钮具有焦点时调用。|  
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|要显示颜色选取器对话框中时由框架调用。|  
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|初始化`m_pPalette`受保护的数据成员与默认系统调色板或指定的调色板。|  
|[CMFCColorButton::UpdateColor](#updatecolor)|当用户选择一种颜色从调色板颜色选取器对话框中，由框架调用。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|`m_bAltColorDlg`|一个布尔值。 如果`TRUE`，框架显示[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)颜色对话框中*其他*单击按钮时，或者如果`FALSE`，系统颜色对话框。 默认值为 `TRUE`。 有关详细信息，请参阅[CMFCColorButton::EnableOtherButton](#enableotherbutton)。|  
|`m_bAutoSetFocus`|一个布尔值。 如果`TRUE`，框架将焦点设置在颜色菜单上显示菜单上，或者如果`FALSE`，不会更改焦点。 默认值为 `TRUE`。|  
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|指示是否为颜色按钮启用自定义模式。|  
|`m_Color`|一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。 包含当前所选的颜色。|  
|`m_ColorAutomatic`|一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。 包含当前所选的默认颜色。|  
|`m_Colors`|一个[CArray](../../mfc/reference/carray-class.md)的[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。 包含当前可用的颜色。|  
|`m_lstDocColors`|一个[CList](../../mfc/reference/clist-class.md)的[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。 包含当前文档颜色。|  
|`m_nColumns`|一个整数。 包含要显示颜色选择菜单中的颜色的网格中的列数。|  
|`m_pPalette`|一个指向[CPalette](../../mfc/reference/cpalette-class.md)。 包含当前颜色选择菜单中可用的颜色。|  
|`m_pPopup`|一个指向[CMFCColorPopupMenu 类](../../mfc/reference/cmfccolorpopupmenu-class.md)对象。 单击颜色按钮时显示颜色选择菜单。|  
|`m_strAutoColorText`|一个字符串。 颜色选择菜单中的"自动"按钮的标签。|  
|`m_strDocColorsText`|一个字符串。 显示文档颜色的颜色选择菜单中的按钮的标签。|  
|`m_strOtherText`|一个字符串。 颜色选择菜单中的"其他"按钮的标签。|  
  
## <a name="remarks"></a>备注  
 默认情况下，`CMFCColorButton`类作为一个推送按钮来打开颜色选取器对话框中的行为。 颜色选取器对话框中包含的小尺寸彩色按钮和一个"other"按钮，可以显示自定义颜色选择器的数组。 ("Other"按钮被标记为标准系统**其他颜色...**.)当用户选择一种新颜色，`CMFCColorButton`对象反映出的更改并显示所选的颜色。  
  
 直接在代码中，或通过使用创建的颜色按钮控件**ClassWizard**工具和对话框模板。 如果您直接创建颜色按钮控件，将添加`CMFCColorButton`变量与你的应用程序中，，然后调用构造函数和`Create`方法`CMFCColorButton`对象。 如果您使用**ClassWizard**，添加`CButton`变量与您的应用程序，然后将更改从变量的类型`CButton`到`CMFCColorButton`。  
  
 颜色选取器对话框中 ( [CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)) 显示的[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)方法，当框架调用`OnLButtonDown`事件处理程序。 [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)可以重写方法，以支持自定义颜色选择。  
  
 `CMFCColorButton`对象通知一种颜色更改通过将其发送其父级`WM_COMMAND | BN_CLICKED`通知。 父级使用[CMFCColorButton::GetColor](#getcolor)方法来检索当前的颜色。  
  
## <a name="example"></a>示例  
 下面的示例演示如何通过使用各种方法中的配置的颜色按钮`CMFCColorButton`类。 这些方法将颜色按钮和列，其数目的颜色设置并启用自动和其他按钮。 此示例摘自[状态栏演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo #&10;](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo #&11;](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头︰** afxcolorbutton.h  
  
##  <a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton  
 构造一个新`CMFCColorButton`对象。  
  
```  
CMFCColorButton();
```  
  
##  <a name="enableautomaticbutton"></a>CMFCColorButton::EnableAutomaticButton  
 启用或禁用颜色选取器控件的"自动"按钮并为您设置自动 （默认值）。  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLabel`  
 指定自动按钮的文本。  
  
 [in] `colorAutomatic`  
 一个指定自动按钮的默认颜色的 RGB 值。  
  
 [in] `bEnable`  
 指定是否启用或禁用自动按钮。  
  
### <a name="remarks"></a>备注  
  
##  <a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton  
 启用或禁用了"other"按钮，这会出现常规彩色按钮的下方。  
  
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
 指定是否启用或禁用"other"按钮。  
  
### <a name="remarks"></a>备注  
 单击"其他"按钮以显示一个颜色对话框。 如果*bAltColorDlg*参数是`TRUE`、 [CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)会显示出来; 否则，将显示系统颜色对话框。  
  
##  <a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor  
 检索当前的 automatic （默认值） 颜色。  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 表示当前的自动颜色 RGB 值。  
  
### <a name="remarks"></a>备注  
 通过设置当前的自动颜色[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)方法。  
  
##  <a name="getcolor"></a>CMFCColorButton::GetColor  
 检索当前所选的颜色。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 RGB 值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme  
 指示是否在 Windows XP 的视觉样式中显示颜色按钮。  
  
```  
BOOL IsDrawXPTheme() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果支持视觉样式和当前的颜色按钮显示在 Windows XP; 的视觉样式否则为`FALSE`。  
  
##  <a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode  
 将颜色按钮设置为自定义模式。  
  
```  
BOOL m_bEnabledInCustomizeMode;  
```  
  
### <a name="remarks"></a>备注  
 如果需要将颜色按钮添加到自定义对话框的页面 （或允许用户进行自定义期间的另一个颜色选项），通过设置启用该按钮`m_bEnabledInCustomizeMode`成员`TRUE`。 默认情况下，此成员设置为`FALSE`。  
  
##  <a name="ondraw"></a>CMFCColorButton::OnDraw  
 由框架以呈现按钮的图像调用。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向以用于呈现按钮的图像的设备上下文。  
  
 [in] `rect`  
 限定按钮的矩形。  
  
 [in] `uiState`  
 指定按钮的视觉状态。  
  
### <a name="remarks"></a>备注  
 重写此方法以自定义呈现过程。  
  
##  <a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder  
 由显示按钮的边框的框架调用。  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向用来绘制边框的设备上下文。  
  
 [in] `rectClient`  
 在由指定的设备上下文的矩形`pDC`参数，用于定义要绘制的按钮的边界。  
  
 [in] `uiState`  
 指定按钮的视觉状态。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义颜色按钮的边框外观。  
  
##  <a name="ondrawfocusrect"></a>CMFCColorButton::OnDrawFocusRect  
 由框架以显示聚焦框按钮具有焦点时调用。  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 用于绘制聚焦框的设备上下文的点。  
  
 [in] `rectClient`  
 在由指定的设备上下文的矩形`pDC`参数定义按钮的边界。  
  
### <a name="remarks"></a>备注  
 重写此方法以自定义聚焦框的外观。  
  
##  <a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup  
 在弹出窗口颜色栏会显示之前调用。  
  
```  
virtual void OnShowColorPopup();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="rebuildpalette"></a>CMFCColorButton::RebuildPalette  
 初始化`m_pPalette`受保护的数据成员与默认系统调色板或指定的调色板。  
  
```  
void RebuildPalette(CPalette* pPal);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pPal`|一个指向逻辑调色板或`NULL`。 如果`NULL`，使用默认系统调色板。|  
  
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
 指定一种颜色的名称。  
  
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
 颜色名称的列表是每个应用程序的全局设置。 因此，此方法会将传输到其参数[CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname)。  
  
##  <a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber  
 定义在用户的颜色选择过程中向用户显示的颜色表中显示的列数。  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>参数  
 [in] `nColumns`  
 指定列的数。  
  
### <a name="remarks"></a>备注  
 用户可以从显示一个表，预定义颜色的一个弹出窗口颜色栏选择一种颜色。 使用此方法用于定义表中的列数。  
  
##  <a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors  
 指定一组颜色和集的名称。 使用显示的一组颜色[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)对象。  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLabel`  
 指定要使用的一组文档颜色来显示标签。  
  
 [in] `lstColors`  
 对的 RGB 值列表的引用。  
  
### <a name="remarks"></a>备注  
 一个`CMFCColorButton`对象维护的数据库传输到的 RGB 值列表[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)对象。 显示颜色栏时，请通过指定其标签的某个特殊部分中所示这些颜色`lpszLabel`参数。  
  
##  <a name="setpalette"></a>CMFCColorButton::SetPalette  
 指定要在弹出窗口颜色栏中显示的标准颜色。  
  
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
 如果非零值，来计算按钮控件的新大小，但未更改的实际大小。  
  
### <a name="return-value"></a>返回值  
 一个`CSize`指定新的按钮控件大小的对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="updatecolor"></a>CMFCColorButton::UpdateColor  
 当用户选择一种颜色从颜色栏显示在用户单击颜色按钮时由框架调用。  
  
```  
virtual void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 由用户选择一种颜色。  
  
### <a name="remarks"></a>备注  
 `UpdateColor`函数更改当前所选的按钮的颜色，并通过发送通知其父级`WM_COMMAND`消息`BN_CLICKED`标准通知。 使用[CMFCColorButton::GetColor](#getcolor)方法来检索所选的颜色。  
  
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

