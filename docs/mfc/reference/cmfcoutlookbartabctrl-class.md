---
title: CMFCOutlookBarTabCtrl Class
ms.date: 10/18/2018
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
ms.openlocfilehash: 309b74126f57e76aa6399f57382d88fee4400700
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369665"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class

在 Microsoft Outlook 中具有 **“导航窗格”** 可视外观的选项卡控件。
有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|默认构造函数。|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCOutlookBarTabCtrl：：添加控制](#addcontrol)|在 Outlook 栏中将 Windows 控件添加为新选项卡。|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|由框架调用以确定用户重命名选项卡时显示的编辑框的尺寸。 `CMFCBaseTabCtrl::CalcRectEdit`|
|[CMFCOutlookBarTabCtrl：：可以显示更少的页面按钮](#canshowfewerpagebuttons)|框架在调整大小操作期间调用，以确定显示的 Outlook 栏选项卡页按钮是否少于当前可见按钮。|
|[CMFCOutlookBarTabCtrl：：可以显示更多页面按钮](#canshowmorepagebuttons)|框架在调整大小操作期间调用，以确定显示的 Outlook 栏选项卡页按钮是否比当前可见数多。|
|[CMFCOutlookBarTabCtrl：：创建](#create)|创建 Outlook 栏选项卡控件。|
|`CMFCOutlookBarTabCtrl::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFCOutlookBarTabCtrl：：启用动画](#enableanimation)|指定是否启用活动选项卡之间切换期间发生的动画。|
|[CMFCOutlookBartabCtrl：：启用原点编辑](#enableinplaceedit)|指定用户是否可以修改 Outlook 栏选项卡按钮上的文本标签。 （覆盖[CMFCBaseTabctrl：启用位置编辑](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).）|
|[CMFCOutlookBarTabCtrl：：启用ScrollButton](#enablescrollbuttons)|由框架调用以启用允许用户滚动浏览 Outlook 栏窗格上的按钮的按钮。|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|标识包含指定点的窗格。 （覆盖[CMFCBaseTabctrl：查找目标](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).）|
|[CMFCOutlookBarTabCtrl：获取边界大小](#getbordersize)|返回 Outlook 选项卡控件的边框大小。|
|`CMFCOutlookBarTabCtrl::GetTabArea`|检索选项卡控件的选项卡区域的大小和位置。 （覆盖[CMFCBaseTabCtrl：getTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).）|
|`CMFCOutlookBarTabCtrl::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCOutlookBarTabCtrl：：获取可见页面按钮](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl：动画](#isanimation)|确定是否启用了在活动选项卡之间切换期间发生的动画。|
|[CMFCOutlookBarTabCtrl：isMode2003](#ismode2003)|确定 Outlook 栏选项卡控件是否处于模拟 Microsoft Outlook 2003 的模式。|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|确定点是否位于选项卡区域内。 （覆盖[CMFCBaseTabctrl：isPtinTab区域](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).）|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|确定选项卡是否可拆卸。 （覆盖[CMFCBaseTabCtrl：可分离的 Tab](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|插入或删除选项卡时由框架调用。 （重写 `CMFCBaseTabCtrl::OnChangeTabs`。）|
|[CMFCOutlookBarTabCtrl：：在显示少点页面按钮](#onshowfewerpagebuttons)|框架调用以减少可见的选项卡页按钮数。|
|[CMFCOutlookBarTabCtrl：：在显示更多页面按钮](#onshowmorepagebuttons)|由框架调用以增加可见的选项卡页按钮数。|
|[CMFCOutlookBarTabCtrl：：在显示选项上](#onshowoptions)|显示**导航窗格选项**对话框。|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|重新计算选项卡控件的内部布局。 （覆盖[CMFCBaseTabCtrl：recalclayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).）|
|[CMFCOutlookBarTabCtrl：：设置活动选项卡](#setactivetab)|设置活动选项卡.（覆盖[CMFCBaseTabCtrl：：设置活动选项卡](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).）|
|[CMFCOutlookBarTabCtrl：：设置边框大小](#setbordersize)|设置 Outlook 选项卡控件的边框大小。|
|[CMFCOutlookBarTabCtrl：：设置页面按钮文本对齐](#setpagebuttontextalign)|设置 Outlook 栏选项卡按钮上文本标签的对齐方式。|
|[CMFCOutlookBarTabCtrl：：设置工具栏图片列表](#settoolbarimagelist)|设置包含 Outlook 2003 模式下 Outlook 栏底部显示的图标的位图（请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)）。|
|[CMFCOutlookBarTabCtrl：：设置可见页面按钮](#setvisiblepagebuttons)||

## <a name="remarks"></a>备注

要创建具有停靠支持的 Outlook 栏，请使用对象`CMFCOutlookBar`承载 Outlook 栏选项卡控件。 有关详细信息，请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="example"></a>示例

下面的示例演示如何初始化`CMFCOutlookBarTabCtrl`对象并在`CMFCOutlookBarTabCtrl`类中使用各种方法。 该示例演示如何在 Outlook 栏的选项卡页按钮上启用文本标签的就地编辑、启用动画、启用允许用户滚动"Outlook"栏窗格上的按钮的滚动控点、设置 Outlook 选项卡控件的边框大小以及设置 Outlook 栏选项卡按钮上文本标签的对齐方式。 此代码段是 Outlook[演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>要求

**标题：** afxoutlookbartabctrl.h

## <a name="cmfcoutlookbartabctrladdcontrol"></a><a name="addcontrol"></a>CMFCOutlookBarTabCtrl：：添加控制

在 Outlook 栏中将 Windows 控件添加为新选项卡。

```
void AddControl(
    CWnd* pWndCtrl,
    LPCTSTR lpszName,
    int nImageID=-1,
    BOOL bDetachable=TRUE,
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```

### <a name="parameters"></a>参数

*pWndCtrl*<br/>
[在]指向要添加的控件的指针。

*lpsz名称*<br/>
[在]指定选项卡的名称。

*b 可拆卸*<br/>
[在]如果为 TRUE，则页面将创建为可拆卸页面。

*nImageID*<br/>
[在]要在新选项卡中显示的图像的内部图像列表中的图像索引。

*dwControlBar样式*<br/>
[在]为包装的停靠窗格指定AFX_CBRS_* 样式。

### <a name="remarks"></a>备注

使用此函数将控件添加为 Outlook 栏的新页。

此功能在[CMFCBaseTabCtrl 上内部调用：：AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)。

如果将*bDetach*设置为 TRUE，`AddControl`则内部创建`CDockablePaneAdapter`对象并包装添加的控件。 它会自动将选项卡式窗口的运行时类设置到 的`CMFCOutlookBar`运行时类，将浮动帧的运行时类设置到`CMultiPaneFrameWnd`。

### <a name="example"></a>示例

下面的示例演示如何在`AddControl``CMFCOutlookBarTabCtrl`类中使用 方法。 此代码段是 Outlook[演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

## <a name="cmfcoutlookbartabctrlcanshowfewerpagebuttons"></a><a name="canshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl：：可以显示更少的页面按钮

框架在调整大小操作期间调用，以确定显示的 Outlook 栏选项卡页按钮是否少于当前可见按钮。

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>返回值

如果有多个按钮，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

Outlook 栏选项卡控件会根据可用空间的可用空间量动态添加或删除显示选项卡。 框架使用此方法来帮助该过程。

## <a name="cmfcoutlookbartabctrlcanshowmorepagebuttons"></a><a name="canshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl：：可以显示更多页面按钮

框架在调整大小操作期间调用，以确定显示的 Outlook 栏选项卡页按钮是否比当前可见数多。

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>返回值

如果当前看不到按钮，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

Outlook 栏选项卡控件会根据可用空间的可用空间量动态添加或删除选项卡。 框架使用此方法来帮助该过程。

## <a name="cmfcoutlookbartabctrlcreate"></a><a name="create"></a>CMFCOutlookBarTabCtrl：：创建

创建 Outlook 栏选项卡控件。

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*矩形*<br/>
[在]指定初始大小和位置（以像素为单位）。

*pparentwnd*<br/>
[在]指向父窗口。 不能为 NULL。

*nID*<br/>
[在]控件 ID。

### <a name="return-value"></a>返回值

如果控件已成功创建，则非零;否则 0。

### <a name="remarks"></a>备注

通常，当[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)控制进程的WM_CREATE消息时，将创建 Outlook 栏选项卡控件。

## <a name="cmfcoutlookbartabctrlenableanimation"></a><a name="enableanimation"></a>CMFCOutlookBarTabCtrl：：启用动画

指定是否启用活动选项卡之间切换期间发生的动画。

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]指定是启用还是禁用动画。

### <a name="remarks"></a>备注

调用此函数以启用和禁用动画。 当用户打开选项卡页时，如果启用了动画，该页的标题将向上或向下滑动。 如果禁用动画，页面将立即变为活动状态。

默认情况下，动画已启用。

## <a name="cmfcoutlookbartabctrlenableinplaceedit"></a><a name="enableinplaceedit"></a>CMFCOutlookBartabCtrl：：启用原点编辑

指定用户是否可以修改 Outlook 栏选项卡页按钮上的文本标签。

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
如果为 TRUE，则启用文本标签的就地编辑。 如果 FALSE，则禁用就地编辑。

### <a name="remarks"></a>备注

调用此函数以启用或禁用选项卡页按钮上文本标签的就地编辑。 默认情况下，将禁用就地编辑。

## <a name="cmfcoutlookbartabctrlenablescrollbuttons"></a><a name="enablescrollbuttons"></a>CMFCOutlookBarTabCtrl：：启用ScrollButton

框架调用以启用允许用户滚动在 Outlook 栏窗格上的按钮的滚动控点。

```
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]确定是否显示滚动按钮。

*bIsUp*<br/>
[在]确定是否显示顶部滚动条。

*bIsDown*<br/>
[在]确定是否显示底部滚动条。

### <a name="remarks"></a>备注

启用滚动按钮的显示。 当活动选项卡更改以还原滚动按钮时，框架将调用此方法。

## <a name="cmfcoutlookbartabctrlgetbordersize"></a><a name="getbordersize"></a>CMFCOutlookBarTabCtrl：获取边界大小

返回 Outlook 选项卡控件的边框大小。

```
int GetBorderSize() const;
```

### <a name="return-value"></a>返回值

边框大小（以像素为单位）。

## <a name="cmfcoutlookbartabctrlgetvisiblepagebuttons"></a><a name="getvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl：：获取可见页面按钮

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcoutlookbartabctrlisanimation"></a><a name="isanimation"></a>CMFCOutlookBarTabCtrl：动画

指定是否启用活动选项卡之间切换期间发生的动画。

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>返回值

如果启用了动画，则非零;否则 0。

### <a name="remarks"></a>备注

调用[CMFCOutlookBarTabCtrl：：启用动画](#enableanimation)功能以启用或禁用动画。

## <a name="cmfcoutlookbartabctrlismode2003"></a><a name="ismode2003"></a>CMFCOutlookBarTabCtrl：isMode2003

确定 Outlook 栏选项卡控件是否处于模拟 Microsoft Outlook 2003 的模式。

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>返回值

如果 Outlook 栏选项卡控件处于 Outlook 2003 模式，则为 TRUE;如果 Outlook 栏选项卡控件处于 Outlook 2003 模式，则为 TRUE。否则 FALSE;

### <a name="remarks"></a>备注

此值由[CMFCOutlookBar 设置：setMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003)。

## <a name="cmfcoutlookbartabctrlonshowfewerpagebuttons"></a><a name="onshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl：：在显示少点页面按钮

框架调用以减少可见的选项卡页按钮数。

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>备注

此方法调整控件调整大小时可见页选项卡按钮的数量。

## <a name="cmfcoutlookbartabctrlonshowmorepagebuttons"></a><a name="onshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl：：在显示更多页面按钮

由框架调用以增加可见的选项卡页按钮数。

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>备注

此方法调整调整控件调整大小时可见的选项卡页按钮数。

## <a name="cmfcoutlookbartabctrlonshowoptions"></a><a name="onshowoptions"></a>CMFCOutlookBarTabCtrl：：在显示选项上

显示 **"导航窗格选项**"对话框。

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>备注

**"导航窗格选项"** 对话框允许用户选择要显示的选项卡页按钮及其显示顺序。

当用户从控件的自定义菜单中选择**导航窗格选项**菜单项时，框架将调用此方法。

## <a name="cmfcoutlookbartabctrlsetactivetab"></a><a name="setactivetab"></a>CMFCOutlookBarTabCtrl：：设置活动选项卡

设置活动选项卡。活动选项卡是打开的选项卡，其内容可见。

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>参数

*iTab*<br/>
[在]要打开的选项卡的零基索引。

### <a name="return-value"></a>返回值

如果指定的选项卡已成功打开，则非零;否则 0。

### <a name="remarks"></a>备注

设置活动选项卡的视觉效果取决于是否已启用动画。 有关详细信息，请参阅[CMFCOutlookBarTabCtrl：：启用动画](#enableanimation)。

## <a name="cmfcoutlookbartabctrlsetbordersize"></a><a name="setbordersize"></a>CMFCOutlookBarTabCtrl：：设置边框大小

设置 Outlook 选项卡控件的边框大小。

```
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>参数

*n边框大小*<br/>
[在]指定以像素为单位的新边框大小。

### <a name="remarks"></a>备注

设置新的边框大小并重新计算 Outlook 窗口布局。

## <a name="cmfcoutlookbartabctrlsetpagebuttontextalign"></a><a name="setpagebuttontextalign"></a>CMFCOutlookBarTabCtrl：：设置页面按钮文本对齐

设置 Outlook 栏选项卡按钮上文本标签的对齐方式。

```
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>参数

*乌伊·马利*<br/>
[在]指定文本对齐方式。

*bredraw*<br/>
[在]如果为 TRUE，则将重绘 Outlook 窗口。

### <a name="remarks"></a>备注

使用此函数可以更改页面按钮的文本对齐方式。

*uiAlign*可以是以下值之一：

|返回的常量|含义|
|--------------|-------------|
|TA_LEFT|左对齐|
|TA_CENTER|中心对齐|
|TA_RIGHT|右对齐|

默认值为TA_CENTER。

## <a name="cmfcoutlookbartabctrlsettoolbarimagelist"></a><a name="settoolbarimagelist"></a>CMFCOutlookBarTabCtrl：：设置工具栏图片列表

设置包含 Outlook 2003 模式下 Outlook 栏底部显示的图标的位图。

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>参数

*uiID*<br/>
[在]指定要加载的图像的资源 ID。

*残雪*<br/>
[在]指定图像列表中图像的宽度（以像素为单位）。

*clrTransp*<br/>
[在]指定透明颜色的 RGB 值。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE;否则返回 FALSE。

### <a name="remarks"></a>备注

使用此功能可以附加图像列表，其图像将在 Microsoft Office 2003 模式下显示在工具栏按钮上。 图像索引应对应于页面索引。

如果不是在 Microsoft Office 2003 模式下，则不应调用此方法。 有关详细信息，请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="cmfcoutlookbartabctrlsetvisiblepagebuttons"></a><a name="setvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl：：设置可见页面按钮

```
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>参数

[在]*n 可见页面按钮*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarPane 类](../../mfc/reference/cmfcoutlookbarpane-class.md)
