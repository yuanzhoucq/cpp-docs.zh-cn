---
title: CMFCOutlookBarPane 类
ms.date: 11/04/2016
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
ms.openlocfilehash: 9ef6a06a4889119e39e72a9e495e5d4f9e17cf56
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505152"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane 类

有关更多详细信息, 请参阅位于 Visual Studio 安装的**VC\\atlmfc\\src\\mfc**文件夹中的源代码。

从可插入到 Outlook 栏 ( [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)) 的[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)派生的控件。 Outlook 栏窗格包含一列大按钮。 如果按钮列表大于窗格，用户可以上下滚动按钮列表。 当用户将 Outlook 栏中的一个窗格与 Outlook 栏分离时，此窗格可以浮动或停靠在主框架窗口中。

## <a name="syntax"></a>语法

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|默认构造函数。|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCOutlookBarPane::AddButton](#addbutton)|将按钮添加到 Outlook 栏窗格。|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|确定窗格是否可以停靠到另一个窗格或框架窗口中。 (重写[CBasePane:: CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached)。)|
|`CMFCOutlookBarPane::CanBeRestored`|确定系统是否可以在自定义后将工具栏还原到其原始状态。 (重写[CMFCToolBar:: CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)。)|
|[CMFCOutlookBarPane::ClearAll](#clearall)|释放 Outlook 栏窗格中图像所使用的资源。|
|[CMFCOutlookBarPane::Create](#create)|创建 Outlook 栏窗格。|
|`CMFCOutlookBarPane::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCOutlookBarPane::Dock`|由框架调用, 用于停靠 Outlook 栏窗格。 （重写 `CPane::Dock`。）|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|指定 Outlook 栏窗格上的滚动箭头是按页面还是按按钮前进按钮列表。|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|返回 Outlook 栏窗格的常规 (非选定) 文本颜色。|
|`CMFCOutlookBarPane::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|确定是否为 Outlook 栏窗格加载了背景图像。|
|`CMFCOutlookBarPane::IsChangeState`|确定浮动窗格是否可停靠。 （重写 `CPane::IsChangeState`。）|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|确定当按钮突出显示并显示背景图像时, 按钮边框是否为灰色。|
|`CMFCOutlookBarPane::OnBeforeFloat`|当窗格要浮动时由框架调用。 (重写[CPane:: OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat)。)|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|删除具有指定命令 ID 的按钮。|
|`CMFCOutlookBarPane::RestoreOriginalstate`|还原工具栏的原始状态。 (重写[CMFCToolBar:: RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate)。)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|设置背景色。|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|设置背景图像。|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|将 Outlook 栏窗格重置为原始按钮集。|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|设置 Outlook 栏窗格中的按钮周围所用的填充的像素数。|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|设置 Outlook 栏窗格中的常规文本和突出显示文本的颜色。|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|设置 Outlook 栏窗格的透明颜色。|
|`CMFCOutlookBarPane::SmartUpdate`|在内部用于更新 Outlook 栏。 （重写 `CMFCToolBar::SmartUpdate`。）|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|指定在自定义模式下显示哪些快捷菜单项。|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|从 Outlook 栏窗格中删除所有按钮。 (重写[CMFCToolBar:: RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons)。)|

## <a name="remarks"></a>备注

有关如何实现 Outlook 面板的信息, 请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

有关 Outlook 栏的示例, 请参阅 OutlookDemo 示例项目。

## <a name="example"></a>示例

下面的示例演示如何使用`CMFCOutlookBarPane`类的各种方法。 该示例演示如何创建 Outlook 栏窗格, 启用页面滚动模式, 启用停靠, 并设置 Outlook 栏的背景色。 此代码片段是[Outlook 多视图示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>要求

**标头:** afxoutlookbarpane

##  <a name="addbutton"></a>CMFCOutlookBarPane:: AddButton

将按钮添加到 Outlook 栏窗格。

```
BOOL AddButton(
    UINT uiImage,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    UINT uiImage,
    UINT uiLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    LPCTSTR szBmpFileName,
    LPCTSTR szLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HBITMAP hBmp,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HICON hIcon,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1,
    BOOL bAlphaBlend=FALSE);
```

### <a name="parameters"></a>参数

*uiImage*<br/>
中指定位图的资源标识符。

*lpszLabel*<br/>
中指定按钮的文本。

*iIdCommand*<br/>
中指定按钮控件的 ID。

*iInsertAt*<br/>
中指定 outlook 栏页面上用于插入按钮的从零开始的索引。

*uiLabel*<br/>
中字符串资源 ID。

*szBmpFileName*<br/>
中指定要加载的磁盘映像文件的名称。

*szLabel*<br/>
中指定按钮的文本。

*hBmp*<br/>
中按钮位图的句柄。

*hIcon*<br/>
中按钮图标的句柄。

### <a name="return-value"></a>返回值

如果成功添加了按钮, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

使用此方法将新按钮插入到 Outlook 栏的页面中。 可以从应用程序资源或磁盘文件加载按钮的图像。

如果由*uiPageID*指定的页面 ID 为-1, 则该按钮将插入到第一页中。

如果由*iInsertAt*指定的索引为-1, 则在页面末尾添加按钮。

##  <a name="canbeattached"></a>CMFCOutlookBarPane:: CanBeAttached

有关更多详细信息, 请参阅位于 Visual Studio 安装的**VC\\atlmfc\\src\\mfc**文件夹中的源代码。

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="clearall"></a>  CMFCOutlookBarPane::ClearAll

释放 Outlook 栏窗格上的图像所使用的资源。

```
void ClearAll();
```

### <a name="remarks"></a>备注

此方法直接调用[CMFCToolBarImages:: Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), 此方法在 Outlook 栏窗格使用的图像上调用。

##  <a name="create"></a>CMFCOutlookBarPane:: Create

创建 Outlook 栏窗格。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
中指定 Outlook 栏窗格控件的父窗口。 不得为 NULL。

*dwStyle*<br/>
中窗口样式。  有关窗口样式的列表, 请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*uiID*<br/>
中控件 ID。 必须是唯一的, 才能保存控件的状态。

*dwControlBarStyle*<br/>
中指定用于定义 Outlook 栏窗格控件与 Outlook 栏分离时的行为的特殊样式。

### <a name="return-value"></a>返回值

如果方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

若要构造`CMFCOutlookBarPane`对象, 请首先调用构造函数, 然后调用`Create`, 它将创建 Outlook 栏窗格控件, `CMFCOutlookBarPane`并将其附加到对象。

有关详细信息`dwControlBarStyle` , 请参阅[CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)。

##  <a name="enablecontextmenuitems"></a>CMFCOutlookBarPane:: EnableContextMenuItems

指定在自定义模式下显示哪些快捷菜单项。

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>参数

*pButton*<br/>
中指向用户单击的工具栏按钮的指针。

*pPopup*<br/>
中指向快捷菜单的指针。

### <a name="return-value"></a>返回值

如果应显示快捷菜单, 则返回 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

重写此方法以修改框架在自定义模式下显示的框架标准快捷菜单。

默认实现检查自定义模式 ( [CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)), 如果它设置为 TRUE, 则禁用除**Delete**之外的所有快捷菜单项。 然后, 它只是将输入参数传递`CMFCToolBar::EnableContextMenuItems`给。

> [!NOTE]
> *上下文菜单*是快捷菜单的同义词。

##  <a name="enablepagescrollmode"></a>CMFCOutlookBarPane:: EnablePageScrollMode

指定 Outlook 栏窗格上的滚动箭头是按页面还是按按钮前进按钮列表。

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>参数

*bPageScroll*<br/>
中如果为 TRUE, 则启用页面滚动模式。 如果为 FALSE, 则禁用页面滚动模式。

##  <a name="getregularcolor"></a>CMFCOutlookBarPane:: GetRegularColor

返回 Outlook 栏窗格的常规 (即非选定) 文本颜色。

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>返回值

作为 RGB 颜色值的当前文本颜色。

### <a name="remarks"></a>备注

使用[CMFCOutlookBarPane:: SetTextColor](#settextcolor)设置 Outlook 栏的当前 (常规和选定的) 文本颜色。 可以通过使用 COLOR_WINDOW 索引调用[GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor)函数来获取默认文本颜色。

##  <a name="isbackgroundtexture"></a>CMFCOutlookBarPane:: IsBackgroundTexture

确定是否为 Outlook 栏窗格加载了背景图像。

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>返回值

如果有要显示的背景图像, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

可以通过调用[CMFCOutlookBarPane:: SetBackImage](#setbackimage)函数来添加背景图像。

如果没有背景图像, 背景将使用[CMFCOutlookBarPane:: SetBackColor](#setbackcolor)指定的颜色进行绘制。

##  <a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane:: IsDrawShadedHighlight

确定当按钮突出显示并显示背景图像时, 按钮边框是否为灰色。

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>返回值

如果按钮的边框为阴影, 则为 TRUE;否则为 FALSE。

##  <a name="removeallbuttons"></a>CMFCOutlookBarPane:: RemoveAllButtons

从 Outlook 栏窗格中删除所有按钮。

```
virtual void RemoveAllButtons();
```

##  <a name="removebutton"></a>CMFCOutlookBarPane:: RemoveButton

删除具有指定命令 ID 的按钮。

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>参数

*iIdCommand*<br/>
中指定要删除的按钮的命令 ID。

### <a name="return-value"></a>返回值

如果成功删除了按钮, 则为 TRUE;如果指定的命令 ID 无效, 则为 FALSE。

##  <a name="setbackcolor"></a>CMFCOutlookBarPane:: SetBackColor

设置 Outlook 面板的背景色。

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>参数

*color*<br/>
中指定新的背景色。

### <a name="remarks"></a>备注

调用此函数可设置 Outlook 栏的当前背景色。 仅当没有背景图像时才使用背景色。

##  <a name="setbackimage"></a>CMFCOutlookBarPane:: SetBackImage

设置背景图像。

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>参数

*uiImageID*<br/>
中指定映像资源 ID。

### <a name="remarks"></a>备注

调用此方法可设置 Outlook 面板的背景图像。 通过嵌入的[CMFCToolBarImages 类](../../mfc/reference/cmfctoolbarimages-class.md)对象管理背景图像的列表。

##  <a name="setdefaultstate"></a>CMFCOutlookBarPane:: SetDefaultState

将 Outlook 栏窗格重置为原始按钮集。

```
void SetDefaultState();
```

### <a name="remarks"></a>备注

此方法会将 Outlook 栏按钮还原到原始集。 此方法类似于`CMFCOutlookBarPane::RestoreOriginalstate`, 只不过它不会触发 Outlook bar 窗格的重绘。

##  <a name="setextraspace"></a>CMFCOutlookBarPane:: SetExtraSpace

设置 Outlook 栏窗格中的按钮周围所用的填充的像素数。

```
void SetExtraSpace()
```

##  <a name="settextcolor"></a>CMFCOutlookBarPane:: SetTextColor

设置 Outlook 栏窗格中的常规文本和突出显示文本的颜色。

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>参数

*clrRegText*<br/>
中指定非选定文本的新颜色。

*clrSelText*<br/>
中指定所选文本的新颜色。

##  <a name="settransparentcolor"></a>CMFCOutlookBarPane:: SetTransparentColor

设置 Outlook 栏窗格的透明颜色。

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>参数

*color*<br/>
指定新的透明色。

### <a name="remarks"></a>备注

显示透明图像需要透明色。 在图像中出现此颜色时, 将改为使用背景色进行绘制。  不会混合背景图像和前景图像。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
