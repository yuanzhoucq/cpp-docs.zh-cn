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
ms.openlocfilehash: b23aa9e30c130cea8c84290b62cc19794376d4c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374098"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane 类

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

派生的控件[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)可插入到 Outlook 栏 ( [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md))。 Outlook 栏窗格包含一列大按钮。 如果按钮列表大于窗格，用户可以上下滚动按钮列表。 当用户将 Outlook 栏中的一个窗格与 Outlook 栏分离时，此窗格可以浮动或停靠在主框架窗口中。

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
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|确定是否可将窗格停靠到另一个窗格或框架窗口。 (重写[CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached)。)|
|`CMFCOutlookBarPane::CanBeRestored`|确定是否在系统可以还原工具栏到其原始状态后自定义。 (重写[CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)。)|
|[CMFCOutlookBarPane::ClearAll](#clearall)|释放由 Outlook 栏窗格中的图像的资源。|
|[CMFCOutlookBarPane::Create](#create)|创建 Outlook 栏窗格。|
|`CMFCOutlookBarPane::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCOutlookBarPane::Dock`|由框架调用以将 Outlook 栏窗格停靠。 （重写 `CPane::Dock`。）|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|指定是否在 Outlook 栏窗格上的滚动箭头前进按钮列表页上，或按钮。|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|返回 Outlook 栏窗格的常规 （非选择） 的文本颜色。|
|`CMFCOutlookBarPane::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|确定是否加载 Outlook 栏窗格的背景图像。|
|`CMFCOutlookBarPane::IsChangeState`|确定是否在停靠浮动窗格。 （重写 `CPane::IsChangeState`。）|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|确定按钮将突出显示并显示背景图像时按钮边框是否为阴影。|
|`CMFCOutlookBarPane::OnBeforeFloat`|当窗格时有关为浮点数，由框架调用。 (重写[CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat)。)|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|删除具有指定的命令 ID 的按钮|
|`CMFCOutlookBarPane::RestoreOriginalstate`|还原工具栏的原始状态。 (重写[CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate)。)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|设置背景色。|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|设置背景图像。|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|将 Outlook 栏窗格重置为原始组按钮。|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|设置的 Outlook 栏窗格中的按钮周围使用的填充的像素数。|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|在 Outlook 栏窗格中设置常规和突出显示的文本的颜色。|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|设置 Outlook 栏窗格中的透明颜色。|
|`CMFCOutlookBarPane::SmartUpdate`|在内部用于更新 Outlook 栏。 （重写 `CMFCToolBar::SmartUpdate`。）|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|指定的快捷菜单项显示在自定义模式。|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|从 Outlook 栏窗格中删除所有按钮。 (重写[CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons)。)|

## <a name="remarks"></a>备注

有关如何实现 Outlook 栏的信息，请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

Outlook 栏的示例，请参阅 OutlookDemo 示例项目。

## <a name="example"></a>示例

下面的示例演示如何使用各种方法`CMFCOutlookBarPane`类。 该示例演示如何创建 Outlook 栏窗格、 启用页滚动模式、 停靠、 启用和设置 Outlook 栏的背景色。 此代码片段属于[Outlook 多视图示例](../../overview/visual-cpp-samples.md)。

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

**标头：** afxoutlookbarpane.h

##  <a name="addbutton"></a>  CMFCOutlookBarPane::AddButton

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
[in]指定位图的资源标识符。

*lpszLabel*<br/>
[in]指定按钮的文本。

*iIdCommand*<br/>
[in]指定按钮控件的 id。

*iInsertAt*<br/>
[in]在 outlook 栏在该处插入该按钮的页上指定的从零开始的索引。

*uiLabel*<br/>
[in]一个字符串资源 id。

*szBmpFileName*<br/>
[in]指定要加载的磁盘图像文件的名称。

*szLabel*<br/>
[in]指定按钮的文本。

*hBmp*<br/>
[in]位图的句柄的按钮。

*hIcon*<br/>
[in]为按钮的图标的句柄。

### <a name="return-value"></a>返回值

如果成功，则添加一个按钮，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法用于将一个新按钮插入到 Outlook 栏的页面。 从应用程序资源或磁盘文件，可以加载按钮的图像。

如果由指定的页 ID *uiPageID*为-1，按钮插入到的第一页。

如果指定的索引*iInsertAt*为-1，该按钮将添加到页的末尾。

##  <a name="canbeattached"></a>  CMFCOutlookBarPane::CanBeAttached

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="clearall"></a>  CMFCOutlookBarPane::ClearAll

释放由 Outlook 栏窗格上的映像的资源。

```
void ClearAll();
```

### <a name="remarks"></a>备注

此方法直接调用[CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear)，这种行为称为 Outlook 栏窗格使用的映像上。

##  <a name="create"></a>  CMFCOutlookBarPane::Create

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
[in]指定 Outlook 栏窗格控件的父窗口。 不能为 NULL。

*dwStyle*<br/>
[in]窗口样式。  窗口样式的列表，请参阅[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*uiID*<br/>
[in]控件 id。 必须为唯一以启用对保存的控件的状态。

*dwControlBarStyle*<br/>
[in]指定特殊从 Outlook 栏分离时定义的行为的 Outlook 栏窗格控件的样式。

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

若要构造`CMFCOutlookBarPane`对象，第一次调用构造函数中，，然后调用`Create`，它创建的 Outlook 栏窗格控件并将其附加到`CMFCOutlookBarPane`对象。

有关详细信息`dwControlBarStyle`请参阅[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。

##  <a name="enablecontextmenuitems"></a>  CMFCOutlookBarPane::EnableContextMenuItems

指定的快捷菜单项显示在自定义模式。

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>参数

*pButton*<br/>
[in]指向用户可单击的工具栏按钮的指针。

*pPopup*<br/>
[in]指向快捷菜单的指针。

### <a name="return-value"></a>返回值

如果应显示的快捷菜单，则将返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

重写此方法以修改该框架在自定义模式中显示的 framework 标准快捷方式菜单。

默认实现将检查自定义模式 ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode))，以及它是否设置为 TRUE，则所有的快捷方式菜单项除外**删除**。 然后，它只需输入传递的参数传递到`CMFCToolBar::EnableContextMenuItems`。

> [!NOTE]
> *上下文菜单*是快捷菜单的同义词。

##  <a name="enablepagescrollmode"></a>  CMFCOutlookBarPane::EnablePageScrollMode

指定是否在 Outlook 栏窗格上的滚动箭头前进按钮按页或按钮的按钮的列表。

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>参数

*bPageScroll*<br/>
[in]如果为 TRUE，则启用页滚动模式。 如果为 FALSE，禁用页滚动模式。

##  <a name="getregularcolor"></a>  CMFCOutlookBarPane::GetRegularColor

返回正常 (即，未选定) Outlook 栏窗格的文本颜色。

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>返回值

当前为 RGB 颜色值的文本颜色。

### <a name="remarks"></a>备注

使用[CMFCOutlookBarPane::SetTextColor](#settextcolor)设置 Outlook 栏的当前 （常规和所选） 的文本颜色。 你可以通过调用获取的默认文本颜色[GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor) COLOR_WINDOW 索引的函数。

##  <a name="isbackgroundtexture"></a>  CMFCOutlookBarPane::IsBackgroundTexture

确定是否加载 Outlook 栏窗格的背景图像。

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>返回值

背景图像以显示; 如果为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

可以通过调用添加背景图像[CMFCOutlookBarPane::SetBackImage](#setbackimage)函数。

如果没有背景图像，与使用指定的颜色绘制背景[CMFCOutlookBarPane::SetBackColor](#setbackcolor)。

##  <a name="isdrawshadedhighlight"></a>  CMFCOutlookBarPane::IsDrawShadedHighlight

确定按钮将突出显示并显示背景图像时按钮边框是否为阴影。

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>返回值

如果按钮的边框显示为灰色; 则为 TRUE否则为 FALSE。

##  <a name="removeallbuttons"></a>  CMFCOutlookBarPane::RemoveAllButtons

从 Outlook 栏窗格中删除所有按钮。

```
virtual void RemoveAllButtons();
```

##  <a name="removebutton"></a>  CMFCOutlookBarPane::RemoveButton

删除具有指定的命令 ID 的按钮

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>参数

*iIdCommand*<br/>
[in]指定要删除某个按钮的命令 ID。

### <a name="return-value"></a>返回值

如果成功移除了该按钮; 则为 TRUE如果指定的命令 ID 无效，则为 FALSE。

##  <a name="setbackcolor"></a>  CMFCOutlookBarPane::SetBackColor

设置 Outlook 栏的背景色。

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>参数

*color*<br/>
[in]指定新背景色。

### <a name="remarks"></a>备注

调用此函数可设置 Outlook 栏的当前背景色。 仅当没有背景图像使用的背景色。

##  <a name="setbackimage"></a>  CMFCOutlookBarPane::SetBackImage

设置背景图像。

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>参数

*uiImageID*<br/>
[in]指定映像资源 id。

### <a name="remarks"></a>备注

调用此方法以设置 Outlook 栏的背景图像。 托管的背景图像列表的嵌入[CMFCToolBarImages 类](../../mfc/reference/cmfctoolbarimages-class.md)对象。

##  <a name="setdefaultstate"></a>  CMFCOutlookBarPane::SetDefaultState

将 Outlook 栏窗格重置为原始组按钮。

```
void SetDefaultState();
```

### <a name="remarks"></a>备注

此方法将 Outlook 栏按钮还原为原始集。 此方法就像`CMFCOutlookBarPane::RestoreOriginalstate`，只不过它不会触发 Outlook 栏窗格重绘。

##  <a name="setextraspace"></a>  CMFCOutlookBarPane::SetExtraSpace

设置的 Outlook 栏窗格中的按钮周围使用的填充的像素数。

```
void SetExtraSpace()
```

##  <a name="settextcolor"></a>  CMFCOutlookBarPane::SetTextColor

在 Outlook 栏窗格中设置常规和突出显示的文本的颜色。

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>参数

*clrRegText*<br/>
[in]指定未选定文本的新颜色。

*clrSelText*<br/>
[in]指定所选文本的新颜色。

##  <a name="settransparentcolor"></a>  CMFCOutlookBarPane::SetTransparentColor

设置 Outlook 栏窗格中的透明颜色。

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>参数

*color*<br/>
指定新的透明颜色。

### <a name="remarks"></a>备注

显示透明图像所需的透明颜色。 改为使用的背景色绘制图像中此颜色的任何匹配项。  没有任何值混合处理的前景色和背景图像。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
