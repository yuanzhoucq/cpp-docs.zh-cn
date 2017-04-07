---
title: "CMFCColorMenuButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorMenuButton class
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
caps.latest.revision: 29
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
ms.openlocfilehash: a9b1e7a3dbfe4d98b3d51850723eb22ec1f9da06
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton 类
`CMFCColorMenuButton`类支持的菜单命令或工具栏按钮用于启动颜色选取器对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCColorMenuButton : public CMFCToolBarMenuButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|构造 `CMFCColorMenuButton` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|启用和禁用定位在正则颜色按钮上方的"自动"按钮。 (标准系统自动按钮标记为**自动**。)|  
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|可用特定于文档而不是系统颜色的颜色的显示。|  
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|启用和禁用位于常规彩色按钮的下方的"其他"按钮。 ("Other"按钮被标记为标准系统**其他颜色...**.)|  
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|启用可移走颜色窗格的能力。|  
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|检索当前的自动颜色。|  
|[CMFCColorMenuButton::GetColor](#getcolor)|检索当前按钮的颜色。|  
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|检索与指定的命令 ID 相对应的颜色|  
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|父窗口更改时由框架调用。|  
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|将打开颜色选择对话框。|  
|[CMFCColorMenuButton::SetColor](#setcolor)|设置当前的颜色按钮的颜色。|  
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|设置指定的颜色菜单按钮的颜色。|  
|[CMFCColorMenuButton::SetColorName](#setcolorname)|设置指定的颜色的新名称。|  
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|设置所显示的列数`CMFCColorBar`对象。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|将另一个工具栏按钮复制到当前按钮。|  
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|创建颜色选取器对话框。|  
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|指示是否支持空菜单。|  
|[CMFCColorMenuButton::OnDraw](#ondraw)|由框架可在按钮上显示图像调用。|  
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|由框架之前调用`CMFCColorMenuButton`工具栏自定义对话框中的列表中显示对象。|  
  
## <a name="remarks"></a>备注  
 若要将菜单命令或工具栏按钮与原始`CMFCColorMenuButton`对象，请创建`CMFCColorMenuButton`对象，该对象设置任何相应的[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)样式，然后调用`ReplaceButton`方法[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)类。 如果自定义工具栏，请调用[CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)方法。  
  
 颜色选取器对话框中创建的处理过程[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)事件处理程序。 事件处理程序通知与父框架`WM_COMMAND`消息。 `CMFCColorMenuButton`对象发送分配给原始菜单命令或工具栏按钮的控件 ID。  
  
## <a name="example"></a>示例  
 下面的示例演示如何创建和使用中的各种方法配置颜色菜单按钮`CMFCColorMenuButton`类。 在示例中，`CPalette`首次创建对象并将其用于构造的对象`CMFCColorMenuButton`类。 `CMFCColorMenuButton`对象然后配置通过启用其自动和其他按钮，并设置其颜色和列数。 此代码摘自[Word 板示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&5;](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad #&6;](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
 [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxcolormenubutton.h  
  
##  <a name="cmfccolormenubutton"></a>CMFCColorMenuButton::CMFCColorMenuButton  
 构造 `CMFCColorMenuButton` 对象。  
  
```  
CMFCColorMenuButton();

 
CMFCColorMenuButton(
    UINT uiCmdID,  
    LPCTSTR lpszText,  
    CPalette* pPalette=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 按钮的命令 id。  
  
 [in] `lpszText`  
 该按钮的文本。  
  
 [in] `pPalette`  
 一个指向该按钮的颜色调色板。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 第一个构造函数是默认构造函数。 对象的当前颜色和自动颜色都初始化为黑色 (RGB （0，0，0）)。  
  
 第二个构造函数将初始化为与指定的命令 ID 相对应的颜色按钮  
  
##  <a name="copyfrom"></a>CMFCColorMenuButton::CopyFrom  
 将复制一个[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)-到另一个派生对象。  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
 若要复制的源按钮。  
  
### <a name="remarks"></a>备注  
 重写此方法为派生自的复制对象`CMFCColorMenuButton`对象。  
  
##  <a name="createpopupmenu"></a>CMFCColorMenuButton::CreatePopupMenu  
 创建颜色选取器对话框。  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>返回值  
 一个表示颜色选取器对话框中的对象。  
  
### <a name="remarks"></a>备注  
 当用户按颜色菜单按钮，将由框架调用此方法。  
  
##  <a name="enableautomaticbutton"></a>CMFCColorMenuButton::EnableAutomaticButton  
 启用和禁用定位在正则颜色按钮上方的"自动"按钮。 (标准系统自动按钮标记为**自动**。)  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLabel`  
 指定按钮文本时该按钮即变为自动显示。  
  
 [in] `colorAutomatic`  
 指定新的自动颜色。  
  
 [in] `bEnable`  
 指定按钮是否为自动。  
  
### <a name="remarks"></a>备注  
 自动按钮将应用当前的默认颜色。  
  
##  <a name="enabledocumentcolors"></a>CMFCColorMenuButton::EnableDocumentColors  
 可用特定于文档而不是系统颜色的颜色的显示。  
  
```  
void EnableDocumentColors(
    LPCTSTR lpszLabel,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLabel`  
 指定按钮文本。  
  
 [in] `bEnable`  
 `TRUE`若要显示特定于文档的颜色或`FALSE`以显示系统颜色。  
  
### <a name="remarks"></a>备注  
 使用此方法以显示当前文档颜色或系统调色板的颜色，当用户单击颜色菜单按钮。  
  
##  <a name="enableotherbutton"></a>CMFCColorMenuButton::EnableOtherButton  
 启用和禁用位于常规彩色按钮的下方的"其他"按钮。 ("Other"按钮被标记为标准系统**其他颜色...**.)  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLabel`  
 指定按钮文本。  
  
 [in] `bAltColorDlg`  
 指定`TRUE`显示`CMFCColorDialog`对话框中，或`FALSE`以显示标准系统颜色对话框。  
  
 [in] `bEnable`  
 指定`TRUE`若要显示"other"按钮; 否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="enabletearoff"></a>CMFCColorMenuButton::EnableTearOff  
 启用可移走颜色窗格的能力。  
  
```  
void EnableTearOff(
    UINT uiID,  
    int nVertDockColumns=-1,  
    int nHorzDockRows=-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiID`  
 指定拖曳窗格中的 ID。  
  
 [in] `nVertDockColumns`  
 在分离式状态的垂直停靠的颜色窗格中指定列的数。  
  
 [in] `nHorzDockRows`  
 指定在状态下分离式水平固定的颜色窗格中的行数。  
  
### <a name="remarks"></a>备注  
 调用此方法可启用时将弹出颜色窗格中的"拖曳"功能`CMFCColorMenuButton`按下按钮。  
  
##  <a name="getautomaticcolor"></a>CMFCColorMenuButton::GetAutomaticColor  
 检索当前的自动颜色。  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个表示当前的自动颜色的 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
 调用此方法以获取将由自动颜色[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)。  
  
##  <a name="getcolor"></a>CMFCColorMenuButton::GetColor  
 检索当前按钮的颜色。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 该按钮的颜色。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcolorbycmdid"></a>CMFCColorMenuButton::GetColorByCmdID  
 检索与指定的命令 ID 相对应的颜色  
  
```  
static COLORREF GetColorByCmdID(UINT uiCmdID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 命令 id。  
  
### <a name="return-value"></a>返回值  
 颜色对应于指定的命令 id。  
  
### <a name="remarks"></a>备注  
 当应用程序中有多个颜色按钮时，请使用此方法。 当用户单击颜色按钮时，该按钮发送其命令 ID`WM_COMMAND`与父对象的消息。 `GetColorByCmdID`方法使用的命令 ID 来检索对应的颜色。  
  
##  <a name="isemptymenuallowed"></a>CMFCColorMenuButton::IsEmptyMenuAllowed  
 指示是否支持空菜单。  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果为空，则为非菜单允许;否则为为零。  
  
### <a name="remarks"></a>备注  
 默认情况下支持空菜单。 重写此方法可以更改此行为在派生类中。  
  
##  <a name="onchangeparentwnd"></a>CMFCColorMenuButton::OnChangeParentWnd  
 父窗口更改时由框架调用。  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 指向新的父窗口的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondraw"></a>CMFCColorMenuButton::OnDraw  
 由框架可在按钮上显示图像调用。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz=TRUE,  
    BOOL bCustomizeMode=FALSE,  
    BOOL bHighlight=FALSE,  
    BOOL bDrawBorder=TRUE,  
    BOOL bGrayDisabledButtons=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 限定要重绘的区域的矩形。  
  
 [in] `pImages`  
 指向的工具栏图像列表。  
  
 [in] `bHorz`  
 `TRUE`若要指定工具栏是按水平停靠状态，则否则为`FALSE`。 默认值为 `TRUE`。  
  
 [in] `bCustomizeMode`  
 `TRUE`若要指定应用程序是在自定义模式;否则为`FALSE`。 默认值为 `FALSE`。  
  
 [in] `bHighlight`  
 `TRUE`若要指定，将突出显示按钮;否则为`FALSE`。 默认值为 `FALSE`。  
  
 [in] `bDrawBorder`  
 `TRUE`若要指定，将显示该按钮的边框。否则为`FALSE`。 默认值为 `TRUE`。  
  
 [in] `bGrayDisabledButtons`  
 `TRUE`若要指定禁用按钮将灰显 （变暗）否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondrawoncustomizelist"></a>CMFCColorMenuButton::OnDrawOnCustomizeList  
 由框架之前调用`CMFCColorMenuButton`工具栏自定义对话框中的列表中显示对象。  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 限定按钮要绘制的矩形。  
  
 [in] `bSelected`  
 `TRUE`指定该按钮处于选定状态，则否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 该按钮的宽度。  
  
### <a name="remarks"></a>备注  
 由框架调用此方法时`CMFCColorMenuButton`工具栏自定义过程的列表框中显示对象。  
  
##  <a name="opencolordialog"></a>CMFCColorMenuButton::OpenColorDialog  
 将打开颜色选择对话框。  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>参数  
 [in] `colorDefault`  
 在颜色对话框中选择默认颜色。  
  
 [out] `colorRes`  
 返回用户从颜色对话框中选择的颜色。  
  
### <a name="return-value"></a>返回值  
 非零，如果用户选择一种新颜色。否则为为零。  
  
### <a name="remarks"></a>备注  
 单击菜单按钮时，调用此方法以打开颜色对话框。 返回值不为零，如果用户选择的颜色将存储在`colorRes`参数。 使用[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)方法之间标准颜色对话框中进行切换和[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)对话框。  
  
##  <a name="setcolor"></a>CMFCColorMenuButton::SetColor  
 设置当前的颜色按钮的颜色。  
  
```  
virtual void SetColor(
    COLORREF clr,  
    BOOL bNotify=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `clr`  
 RGB 颜色值。  
  
 [in] `bNotify`  
 `TRUE`若要将应用`clr`参数颜色设为任何关联的菜单按钮或工具栏按钮; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法可以更改颜色按钮的颜色。 如果`bNotify`参数为非零值，任何关联的弹出菜单或工具栏上的相应按钮的颜色更改为指定的颜色`clr`参数。  
  
##  <a name="setcolorbycmdid"></a>CMFCColorMenuButton::SetColorByCmdID  
 设置指定的颜色菜单按钮的颜色。  
  
```  
static void SetColorByCmdID(
    UINT uiCmdID,  
    COLORREF color);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 颜色菜单按钮资源 ID。  
  
 [in] `color`  
 RGB 颜色值。  
  
##  <a name="setcolorname"></a>CMFCColorMenuButton::SetColorName  
 设置指定的颜色的新名称。  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 其名称将更改颜色的 RGB 值。  
  
 [in] `strName`  
 颜色的新名称。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setcolumnsnumber"></a>CMFCColorMenuButton::SetColumnsNumber  
 设置要显示颜色选择控件中的列数 ( [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)对象)。  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>参数  
 [in] `nColumns`  
 要显示的列数。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarsCustomizeDialog 类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)   
 [CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)

