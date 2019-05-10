---
title: CMFCColorMenuButton 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- CMFCColorMenuButton [MFC], CMFCColorMenuButton
- CMFCColorMenuButton [MFC], EnableAutomaticButton
- CMFCColorMenuButton [MFC], EnableDocumentColors
- CMFCColorMenuButton [MFC], EnableOtherButton
- CMFCColorMenuButton [MFC], EnableTearOff
- CMFCColorMenuButton [MFC], GetAutomaticColor
- CMFCColorMenuButton [MFC], GetColor
- CMFCColorMenuButton [MFC], GetColorByCmdID
- CMFCColorMenuButton [MFC], OnChangeParentWnd
- CMFCColorMenuButton [MFC], OpenColorDialog
- CMFCColorMenuButton [MFC], SetColor
- CMFCColorMenuButton [MFC], SetColorByCmdID
- CMFCColorMenuButton [MFC], SetColorName
- CMFCColorMenuButton [MFC], SetColumnsNumber
- CMFCColorMenuButton [MFC], CopyFrom
- CMFCColorMenuButton [MFC], CreatePopupMenu
- CMFCColorMenuButton [MFC], IsEmptyMenuAllowed
- CMFCColorMenuButton [MFC], OnDraw
- CMFCColorMenuButton [MFC], OnDrawOnCustomizeList
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
ms.openlocfilehash: 5fccfbca9fe8c31070f3eb9f208c09cb3722b9b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403719"
---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton 类

`CMFCColorMenuButton`类支持的菜单命令或启动颜色选取器对话框中的工具栏按钮。

## <a name="syntax"></a>语法

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|构造 `CMFCColorMenuButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|启用和禁用置于常规颜色按钮上方的"自动"按钮。 (标准系统自动按钮标记为**自动**。)|
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|可用特定于文档的而不是系统颜色的颜色的显示。|
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|启用和禁用置于常规颜色按钮之下的"其他"按钮。 ("其他"按钮标记为标准系统**更多颜色**。)|
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|使可移走颜色窗格的功能。|
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|检索当前的自动颜色。|
|[CMFCColorMenuButton::GetColor](#getcolor)|检索当前按钮的颜色。|
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|检索与指定的命令 ID 相对应的颜色|
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|父窗口更改时由框架调用。|
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|将打开颜色选择对话框。|
|[CMFCColorMenuButton::SetColor](#setcolor)|设置当前的颜色按钮的颜色。|
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|设置指定的颜色菜单按钮的颜色。|
|[CMFCColorMenuButton::SetColorName](#setcolorname)|设置指定颜色的新名称。|
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|设置的情况下显示的列数`CMFCColorBar`对象。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|将另一个工具栏按钮复制到当前按钮。|
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|创建颜色选取器对话框。|
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|指示是否支持空菜单。|
|[CMFCColorMenuButton::OnDraw](#ondraw)|由框架调用以在按钮上显示的图像。|
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|由框架之前调用`CMFCColorMenuButton`对象显示在工具栏自定义对话框的列表。|

## <a name="remarks"></a>备注

若要将菜单命令或工具栏按钮与原始`CMFCColorMenuButton`对象，请创建`CMFCColorMenuButton`对象，设置相应的任何[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)样式，然后调用`ReplaceButton`方法[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)类。 如果自定义工具栏，请调用[CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)方法。

颜色选取器对话框中创建的处理期间[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)事件处理程序。 事件处理程序会通知并 WM_COMMAND 消息与父框架。 `CMFCColorMenuButton`对象发送给原始的菜单命令或工具栏按钮的控件 ID。

## <a name="example"></a>示例

下面的示例演示如何创建和使用中的各种方法配置颜色菜单按钮`CMFCColorMenuButton`类。 在示例中，`CPalette`对象是首次创建，然后用于构造的对象`CMFCColorMenuButton`类。 `CMFCColorMenuButton`对象然后配置通过启用其自动和其他按钮，并设置其颜色和列数。 此代码摘自[Word Pad 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>要求

**标头：** afxcolormenubutton.h

##  <a name="cmfccolormenubutton"></a>  CMFCColorMenuButton::CMFCColorMenuButton

构造 `CMFCColorMenuButton` 对象。

```
CMFCColorMenuButton();

CMFCColorMenuButton(
    UINT uiCmdID,
    LPCTSTR lpszText,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>参数

*uiCmdID*<br/>
[in]按钮命令 id。

*lpszText*<br/>
[in]按钮文本。

*pPalette*<br/>
[in]指向按钮的颜色调色板的指针。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

第一个构造函数是默认构造函数。 对象的当前颜色和自动颜色都初始化为黑色 (RGB （0，0，0）)。

第二个构造函数初始化的按钮的颜色对应于指定的命令 id。

##  <a name="copyfrom"></a>  CMFCColorMenuButton::CopyFrom

将一个复制[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)-到另一个派生的对象。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>参数

*src*<br/>
[in]若要复制的源按钮。

### <a name="remarks"></a>备注

重写此方法对复制对象的派生自`CMFCColorMenuButton`对象。

##  <a name="createpopupmenu"></a>  CMFCColorMenuButton::CreatePopupMenu

创建颜色选取器对话框。

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>返回值

一个对象，表示颜色选取器对话框。

### <a name="remarks"></a>备注

在用户按颜色菜单按钮时，由框架调用此方法。

##  <a name="enableautomaticbutton"></a>  CMFCColorMenuButton::EnableAutomaticButton

启用和禁用置于常规颜色按钮上方的"自动"按钮。 (标准系统自动按钮标记为**自动**。)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[in]指定自动按钮后显示的按钮文本。

*colorAutomatic*<br/>
[in]指定新的自动颜色。

*bEnable*<br/>
[in]指定按钮是否为自动。

### <a name="remarks"></a>备注

自动按钮应用当前的默认颜色。

##  <a name="enabledocumentcolors"></a>  CMFCColorMenuButton::EnableDocumentColors

可用特定于文档的而不是系统颜色的颜色的显示。

```
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[in]指定的按钮文本。

*bEnable*<br/>
[in]若要显示特定于文档的颜色或为 FALSE，则显示系统颜色为 TRUE。

### <a name="remarks"></a>备注

使用此方法以显示当前文档颜色或系统调色板的颜色，当用户单击颜色菜单按钮。

##  <a name="enableotherbutton"></a>  CMFCColorMenuButton::EnableOtherButton

启用和禁用置于常规颜色按钮之下的"其他"按钮。 ("其他"按钮标记为标准系统**更多颜色**。)

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[in]指定的按钮文本。

*bAltColorDlg*<br/>
[in]指定 TRUE，则显示`CMFCColorDialog`对话框中或为 FALSE，则显示标准系统颜色对话框。

*bEnable*<br/>
[in]指定为 TRUE，则显示"其他"按钮;否则为 FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

##  <a name="enabletearoff"></a>  CMFCColorMenuButton::EnableTearOff

使可移走颜色窗格的功能。

```
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>参数

*uiID*<br/>
[in]指定分离式窗格中的 ID。

*nVertDockColumns*<br/>
[in]在处于拖曳状态的垂直停靠的颜色窗格中指定列的数。

*nHorzDockRows*<br/>
[in]指定在拖曳状态的水平停靠的颜色窗格的行数。

### <a name="remarks"></a>备注

调用此方法以启用弹出时的颜色窗格的"分离"功能`CMFCColorMenuButton`按下按钮。

##  <a name="getautomaticcolor"></a>  CMFCColorMenuButton::GetAutomaticColor

检索当前的自动颜色。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>返回值

一个表示当前的自动颜色的 RGB 颜色值。

### <a name="remarks"></a>备注

调用此方法以获取通过设置的自动颜色[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)。

##  <a name="getcolor"></a>  CMFCColorMenuButton::GetColor

检索当前按钮的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

按钮的颜色。

### <a name="remarks"></a>备注

##  <a name="getcolorbycmdid"></a>  CMFCColorMenuButton::GetColorByCmdID

检索与指定的命令 ID 相对应的颜色

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>参数

*uiCmdID*<br/>
[in]命令 id。

### <a name="return-value"></a>返回值

颜色对应于指定的命令 id。

### <a name="remarks"></a>备注

当应用程序中有多个颜色按钮时，请使用此方法。 当用户单击颜色按钮时，按钮将其命令 ID 的 WM_COMMAND 消息中发送到其父级。 `GetColorByCmdID`方法使用的命令 ID 来检索对应的颜色。

##  <a name="isemptymenuallowed"></a>  CMFCColorMenuButton::IsEmptyMenuAllowed

指示是否支持空菜单。

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>返回值

如果允许空菜单; 非零值否则为为零。

### <a name="remarks"></a>备注

默认情况下支持空菜单。 重写此方法以更改此行为在派生类中。

##  <a name="onchangeparentwnd"></a>  CMFCColorMenuButton::OnChangeParentWnd

父窗口更改时由框架调用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
[in]指向新的父窗口的指针。

### <a name="remarks"></a>备注

##  <a name="ondraw"></a>  CMFCColorMenuButton::OnDraw

由框架调用以在按钮上显示的图像。

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

*pDC*<br/>
[in]指向设备上下文的指针。

*rect*<br/>
[in]限定要重绘的区域的矩形。

*pImages*<br/>
[in]指向工具栏图像的列表。

*bHorz*<br/>
[in]指定工具栏处于水平停靠状态，则为 TRUE否则为 FALSE。 默认值为 TRUE。

*bCustomizeMode*<br/>
[in]为 TRUE，则指定该应用程序中自定义模式;否则为 FALSE。 默认值为 FALSE。

*bHighlight*<br/>
[in]为 TRUE，则指定的按钮将突出显示;否则为 FALSE。 默认值为 FALSE。

*bDrawBorder*<br/>
[in]为 TRUE，则指定，将显示按钮的边框;否则为 FALSE。 默认值为 TRUE。

*bGrayDisabledButtons*<br/>
[in]为 TRUE，则指定 out; 禁用的按钮将灰显 （变暗）否则为 FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

##  <a name="ondrawoncustomizelist"></a>  CMFCColorMenuButton::OnDrawOnCustomizeList

由框架之前调用`CMFCColorMenuButton`对象显示在工具栏自定义对话框的列表。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

*rect*<br/>
[in]限定要绘制的按钮的矩形。

*bSelected*<br/>
[in]TRUE 指定按钮处于选中状态;否则为 FALSE。

### <a name="return-value"></a>返回值

按钮的宽度。

### <a name="remarks"></a>备注

由框架调用此方法时`CMFCColorMenuButton`工具栏自定义过程的列表框中显示对象。

##  <a name="opencolordialog"></a>  CMFCColorMenuButton::OpenColorDialog

将打开颜色选择对话框。

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>参数

*colorDefault*<br/>
[in]在颜色对话框中选择默认颜色。

*colorRes*<br/>
[out]返回用户选择从颜色对话框中的颜色。

### <a name="return-value"></a>返回值

如果用户选择一种新颜色; 非零值否则为为零。

### <a name="remarks"></a>备注

单击菜单按钮时，调用此方法以打开颜色对话框。 返回值为非零值，如果用户选择的颜色将存储在*colorRes*参数。 使用[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)方法的标准颜色对话框框之间进行切换并[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)对话框。

##  <a name="setcolor"></a>  CMFCColorMenuButton::SetColor

设置当前的颜色按钮的颜色。

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>参数

*clr*<br/>
[in]RGB 颜色值。

*bNotify*<br/>
[in]为 true，则应用*clr*参数颜色与任何关联的菜单按钮或工具栏按钮; 否则为 FALSE。

### <a name="remarks"></a>备注

调用此方法可以更改当前颜色按钮的颜色。 如果*bNotify*参数为非零值，在任何相关联的弹出菜单或工具栏上的相应按钮的颜色更改为指定的颜色*clr*参数。

##  <a name="setcolorbycmdid"></a>  CMFCColorMenuButton::SetColorByCmdID

设置指定的颜色菜单按钮的颜色。

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>参数

*uiCmdID*<br/>
[in]颜色菜单按钮的资源 ID。

*color*<br/>
[in]RGB 颜色值。

##  <a name="setcolorname"></a>  CMFCColorMenuButton::SetColorName

设置指定颜色的新名称。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>参数

*color*<br/>
[in]其名称将更改颜色的 RGB 值。

*strName*<br/>
[in]新颜色的名称。

### <a name="remarks"></a>备注

##  <a name="setcolumnsnumber"></a>  CMFCColorMenuButton::SetColumnsNumber

设置要显示的颜色选择控件中的列数 ( [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)对象)。

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>参数

*nColumns*<br/>
[in]要显示的列数。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog 类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)
