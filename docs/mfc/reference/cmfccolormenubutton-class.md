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
ms.openlocfilehash: 22208aec505033d372f5a80ba2a9641b1bd15874
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367702"
---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton 类

该`CMFCColorMenuButton`类支持菜单命令或启动颜色选取器对话框的工具栏按钮。

## <a name="syntax"></a>语法

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC颜色菜单按钮：：CMFCColor菜单按钮](#cmfccolormenubutton)|构造 `CMFCColorMenuButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC颜色菜单按钮：：启用自动按钮](#enableautomaticbutton)|启用并禁用位于常规颜色按钮上方的"自动"按钮。 （标准系统自动按钮标记为**自动**.）|
|[CMFC颜色菜单按钮：：启用文档颜色](#enabledocumentcolors)|启用显示文档特定颜色而不是系统颜色。|
|[CMFC颜色菜单按钮：：启用其他按钮](#enableotherbutton)|启用并禁用位于常规颜色按钮下方的"其他"按钮。 （标准系统"其他"按钮标记为**更多颜色**。|
|[CMFCColor菜单按钮：：启用"关闭"](#enabletearoff)|能够撕下颜色窗格。|
|[CMFCColor菜单按钮：获取自动颜色](#getautomaticcolor)|检索当前自动颜色。|
|[CMFCColor菜单按钮：获取颜色](#getcolor)|检索当前按钮的颜色。|
|[CMFCColor菜单按钮：获取颜色乘 CmdID](#getcolorbycmdid)|检索对应于指定命令 ID 的颜色。|
|[CMFCColor菜单按钮：：打开更改家长](#onchangeparentwnd)|父窗口更改时由框架调用。|
|[CMFC颜色菜单按钮：：打开颜色对话](#opencolordialog)|打开颜色选择对话框。|
|[CMFCColor菜单按钮：：设置颜色](#setcolor)|设置当前颜色按钮的颜色。|
|[CMFC颜色菜单按钮：：设置颜色乘CmdID](#setcolorbycmdid)|设置指定颜色菜单按钮的颜色。|
|[CMFC颜色菜单按钮：：设置颜色名称](#setcolorname)|为指定颜色设置新名称。|
|[CMFCColor菜单按钮：：设置列数](#setcolumnsnumber)|设置`CMFCColorBar`对象显示的列数。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFCColor菜单按钮：：抄袭](#copyfrom)|将另一个工具栏按钮复制到当前按钮。|
|[CMFC颜色菜单按钮：：创建弹出菜单](#createpopupmenu)|创建颜色选取器对话框。|
|[CMFCColor菜单按钮：：空菜单允许](#isemptymenuallowed)|指示是否支持空菜单。|
|[CMFCColor菜单按钮：：开拉](#ondraw)|框架调用以在按钮上显示图像。|
|[CMFCColor菜单按钮：：在画上定制列表](#ondrawoncustomizelist)|在`CMFCColorMenuButton`工具栏自定义对话框列表中显示对象之前由框架调用。|

## <a name="remarks"></a>备注

要将原始菜单命令或工具栏按钮替换为`CMFCColorMenuButton`对象，请创建`CMFCColorMenuButton`对象，设置任何适当的[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)样式，然后调用`ReplaceButton`[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)的方法。 如果自定义工具栏，请调用[CMFCToolBars 自定义对话框：：替换按钮](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)方法。

颜色选取器对话框是在处理[CMFCColorMenuButton：：创建PopupMenu](#createpopupmenu)事件处理程序期间创建的。 事件处理程序使用WM_COMMAND消息通知父帧。 对象`CMFCColorMenuButton`将分配给原始菜单命令或工具栏按钮的控制 ID 发送。

## <a name="example"></a>示例

下面的示例演示如何使用`CMFCColorMenuButton`类中的各种方法创建和配置颜色菜单按钮。 在此示例中，首先创建对象`CPalette`，然后用于构造`CMFCColorMenuButton`类的对象。 然后`CMFCColorMenuButton`，通过启用其自动和其他按钮，并设置其颜色和列数来配置对象。 此代码是 Word [Pad 示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>要求

**标题：** afxcolormenu按钮.h

## <a name="cmfccolormenubuttoncmfccolormenubutton"></a><a name="cmfccolormenubutton"></a>CMFC颜色菜单按钮：：CMFCColor菜单按钮

构造 `CMFCColorMenuButton` 对象。

```
CMFCColorMenuButton();

CMFCColorMenuButton(
    UINT uiCmdID,
    LPCTSTR lpszText,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>参数

*乌伊CmdID*<br/>
[在]按钮命令 ID。

*lpszText*<br/>
[在]按钮文本。

*pPalette*<br/>
[在]指向按钮调色板的指针。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

第一个构造函数是默认构造函数。 对象的当前颜色和自动颜色被初始化为黑色（RGB（0，0，0）。

第二个构造函数将按钮初始化到对应于指定命令 ID 的颜色。

## <a name="cmfccolormenubuttoncopyfrom"></a><a name="copyfrom"></a>CMFCColor菜单按钮：：抄袭

将一个[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)派生对象复制到另一个对象。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>参数

*src*<br/>
[在]要复制的源按钮。

### <a name="remarks"></a>备注

重写此方法以复制从`CMFCColorMenuButton`对象派生的对象。

## <a name="cmfccolormenubuttoncreatepopupmenu"></a><a name="createpopupmenu"></a>CMFC颜色菜单按钮：：创建弹出菜单

创建颜色选取器对话框。

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>返回值

表示颜色选取器对话框的对象。

### <a name="remarks"></a>备注

当用户按下颜色菜单按钮时，框架将调用此方法。

## <a name="cmfccolormenubuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFC颜色菜单按钮：：启用自动按钮

启用并禁用位于常规颜色按钮上方的"自动"按钮。 （标准系统自动按钮标记为**自动**.）

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]指定按钮变为自动时显示的按钮文本。

*颜色 自动*<br/>
[在]指定新的自动颜色。

*b 启用*<br/>
[在]指定按钮是否自动。

### <a name="remarks"></a>备注

自动按钮应用当前默认颜色。

## <a name="cmfccolormenubuttonenabledocumentcolors"></a><a name="enabledocumentcolors"></a>CMFC颜色菜单按钮：：启用文档颜色

启用显示文档特定颜色而不是系统颜色。

```
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]指定按钮文本。

*b 启用*<br/>
[在]TRUE 显示特定于文档的颜色，或显示系统颜色的 FALSE。

### <a name="remarks"></a>备注

当用户单击颜色菜单按钮时，使用此方法显示当前文档颜色或系统调色板颜色。

## <a name="cmfccolormenubuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFC颜色菜单按钮：：启用其他按钮

启用并禁用位于常规颜色按钮下方的"其他"按钮。 （标准系统"其他"按钮标记为**更多颜色**。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]指定按钮文本。

*巴尔特·博拉尔德格*<br/>
[在]指定 TRUE 以`CMFCColorDialog`显示对话框，或指定 FALSE 以显示标准系统颜色对话框。

*b 启用*<br/>
[在]指定 TRUE 以显示"其他"按钮;否则，FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

## <a name="cmfccolormenubuttonenabletearoff"></a><a name="enabletearoff"></a>CMFCColor菜单按钮：：启用"关闭"

能够撕下颜色窗格。

```
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>参数

*uiID*<br/>
[在]指定拆解窗格的 ID。

*nVertDock 柱子*<br/>
[在]指定垂直停靠颜色窗格中处于撕扯状态的列数。

*n霍兹多克罗茨*<br/>
[在]指定处于撕下状态时水平停靠颜色窗格的行数。

### <a name="remarks"></a>备注

调用此方法，为按下`CMFCColorMenuButton`按钮时弹出的颜色窗格启用"撕掉"功能。

## <a name="cmfccolormenubuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColor菜单按钮：获取自动颜色

检索当前自动颜色。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>返回值

表示当前自动颜色的 RGB 颜色值。

### <a name="remarks"></a>备注

调用此方法以获取[由 CMFCColorMenuButton](#enableautomaticbutton)设置的自动颜色：启用自动按钮 。

## <a name="cmfccolormenubuttongetcolor"></a><a name="getcolor"></a>CMFCColor菜单按钮：获取颜色

检索当前按钮的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

按钮的颜色。

### <a name="remarks"></a>备注

## <a name="cmfccolormenubuttongetcolorbycmdid"></a><a name="getcolorbycmdid"></a>CMFCColor菜单按钮：获取颜色乘 CmdID

检索对应于指定命令 ID 的颜色。

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>参数

*乌伊CmdID*<br/>
[在]命令 ID。

### <a name="return-value"></a>返回值

对应于指定命令 ID 的颜色。

### <a name="remarks"></a>备注

当应用程序中有多个颜色按钮时，请使用此方法。 当用户单击颜色按钮时，该按钮将WM_COMMAND消息中的命令 ID 发送到其父级。 该方法`GetColorByCmdID`使用命令 ID 检索相应的颜色。

## <a name="cmfccolormenubuttonisemptymenuallowed"></a><a name="isemptymenuallowed"></a>CMFCColor菜单按钮：：空菜单允许

指示是否支持空菜单。

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>返回值

允许空菜单时非零;否则，零。

### <a name="remarks"></a>备注

默认情况下支持空菜单。 重写此方法以更改派生类中的此行为。

## <a name="cmfccolormenubuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCColor菜单按钮：：打开更改家长

父窗口更改时由框架调用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]指向新父窗口的指针。

### <a name="remarks"></a>备注

## <a name="cmfccolormenubuttonondraw"></a><a name="ondraw"></a>CMFCColor菜单按钮：：开拉

框架调用以在按钮上显示图像。

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
[在]指向设备上下文的指针。

*矩形*<br/>
[在]绑定要重绘的区域的矩形。

*pImage*<br/>
[在]指向工具栏图像列表。

*布霍兹*<br/>
[在]TRUE 指定工具栏处于水平停靠状态;否则，FALSE。 默认值为 TRUE。

*b 定制模式*<br/>
[在]TRUE 指定应用程序处于自定义模式;否则，FALSE。 默认值为 FALSE。

*b 高光*<br/>
[在]TRUE 以指定按钮突出显示;否则，FALSE。 默认值为 FALSE。

*bDraw边框*<br/>
[在]TRUE 以指定显示按钮的边框;否则，FALSE。 默认值为 TRUE。

*b格雷禁用按钮*<br/>
[在]TRUE 指定禁用的按钮为灰色（变暗）出;否则，FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

## <a name="cmfccolormenubuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCColor菜单按钮：：在画上定制列表

在`CMFCColorMenuButton`工具栏自定义对话框列表中显示对象之前由框架调用。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*矩形*<br/>
[在]绑定要绘制的按钮的矩形。

*b选定*<br/>
[在]TRUE 指定按钮处于所选状态;因此，该按钮将处于所选状态。否则，FALSE。

### <a name="return-value"></a>返回值

按钮的宽度。

### <a name="remarks"></a>备注

当`CMFCColorMenuButton`对象在工具栏自定义过程中显示在列表框中时，框架将调用此方法。

## <a name="cmfccolormenubuttonopencolordialog"></a><a name="opencolordialog"></a>CMFC颜色菜单按钮：：打开颜色对话

打开颜色选择对话框。

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>参数

*颜色 默认*<br/>
[在]在颜色对话框中选择的默认颜色。

*颜色 Res*<br/>
[出]返回用户从颜色对话框中选择的颜色。

### <a name="return-value"></a>返回值

如果用户选择新颜色，则非零;否则，零。

### <a name="remarks"></a>备注

单击菜单按钮时，调用此方法以打开颜色对话框。 如果返回值为非零，则用户选择的颜色存储在*颜色 Res*参数中。 使用[CMFCColorMenuButton：启用其他按钮](#enableotherbutton)方法在标准颜色对话框和[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)对话框之间切换。

## <a name="cmfccolormenubuttonsetcolor"></a><a name="setcolor"></a>CMFCColor菜单按钮：：设置颜色

设置当前颜色按钮的颜色。

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>参数

*Clr*<br/>
[在]RGB 颜色值。

*b 通知*<br/>
[在]TRUE 将*clr*参数颜色应用于任何关联的菜单按钮或工具栏按钮;否则，FALSE。

### <a name="remarks"></a>备注

调用此方法以更改当前颜色按钮的颜色。 如果*bNotify*参数为非零，则任何关联的弹出式菜单或工具栏上的相应按钮的颜色将更改为*clr*参数指定的颜色。

## <a name="cmfccolormenubuttonsetcolorbycmdid"></a><a name="setcolorbycmdid"></a>CMFC颜色菜单按钮：：设置颜色乘CmdID

设置指定颜色菜单按钮的颜色。

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>参数

*乌伊CmdID*<br/>
[在]颜色菜单按钮的资源 ID。

*颜色*<br/>
[在]RGB 颜色值。

## <a name="cmfccolormenubuttonsetcolorname"></a><a name="setcolorname"></a>CMFC颜色菜单按钮：：设置颜色名称

为指定颜色设置新名称。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]名称更改的颜色的 RGB 值。

*strName*<br/>
[在]颜色的新名称。

### <a name="remarks"></a>备注

## <a name="cmfccolormenubuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColor菜单按钮：：设置列数

设置要在颜色选择控件[（CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)对象）中显示的列数。

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>参数

*nColumns*<br/>
[在]要显示的列数。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog 类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)
