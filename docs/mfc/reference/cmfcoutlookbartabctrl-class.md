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
ms.openlocfilehash: 01effb8cb1142db0bcae6f9c456e4a3b3abd69e8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269930"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class

在 Microsoft Outlook 中具有 **“导航窗格”** 可视外观的选项卡控件。
有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。
## <a name="syntax"></a>语法

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|默认构造函数。|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|为 Outlook 栏中的新选项卡中添加一个 Windows 控件。|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|由框架调用以确定用户时，将显示编辑框的尺寸将重命名一个选项卡。（重写 `CMFCBaseTabCtrl::CalcRectEdit`。）|
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|由框架调用以确定如果不是当前可见，可以显示更少的 Outlook 栏选项卡页按钮的大小调整操作过程。|
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|由框架调用以确定如果不是当前可见，可以显示多个 Outlook 栏选项卡页按钮的大小调整操作过程。|
|[CMFCOutlookBarTabCtrl::Create](#create)|创建 Outlook 栏选项卡控件。|
|`CMFCOutlookBarTabCtrl::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|指定是否启用动画时所发生的活动选项卡之间切换。|
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|指定用户是否可以修改上的 Outlook 栏选项卡按钮的文本标签。 (重写[CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit)。)|
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|由框架调用以启用允许用户滚动浏览 Outlook 栏窗格上的按钮的按钮。|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|标识包含指定的点的窗格。 (重写[CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd)。)|
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|返回 Outlook 选项卡控件的边框大小。|
|`CMFCOutlookBarTabCtrl::GetTabArea`|检索的大小和选项卡控件的选项卡区域的位置。 (重写[CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea)。)|
|`CMFCOutlookBarTabCtrl::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|确定是否启用动画时所发生的活动选项卡之间切换。|
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|确定 Outlook 栏选项卡控件是否在模拟 Microsoft Outlook 2003 模式下。|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|确定点是否在选项卡区域内。 (重写[CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea)。)|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|确定选项卡是否可拆分。 (重写[CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable)。)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|插入或删除一个选项卡时，由框架调用。 （重写 `CMFCBaseTabCtrl::OnChangeTabs`。）|
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|由框架调用以减少可见的选项卡页按钮的数目。|
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|由框架调用以增加可见的选项卡页按钮的数目。|
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|显示**导航窗格选项**对话框。|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|重新计算选项卡控件的内部布局。 (重写[CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout)。)|
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|设置活动选项卡。(重写[CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab)。)|
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|设置 Outlook 选项卡控件的边框大小。|
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|设置上的 Outlook 栏选项卡按钮的文本标签的对齐方式。|
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|设置包含在 Outlook 2003 模式下的 Outlook 栏底部显示的图标的位图 (请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md))。|
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>备注

若要创建一个 Outlook 栏，停靠支持，请使用`CMFCOutlookBar`要托管的 Outlook 栏选项卡控件对象。 有关详细信息，请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="example"></a>示例

下面的示例演示如何初始化`CMFCOutlookBarTabCtrl`对象，并使用各种方法中的`CMFCOutlookBarTabCtrl`类。 该示例演示如何以启用上的 Outlook 栏选项卡页按钮的文本标签的就地编辑、 启用动画、 启用滚动句柄，使用户可以滚动浏览 Outlook 栏窗格上的按钮，设置 Outlook 选项卡 cont 的边框大小rol 和组上的 Outlook 栏选项卡按钮的文本标签的对齐方式。 此代码片段属于[Outlook 演示示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>要求

**标头：** afxoutlookbartabctrl.h

##  <a name="addcontrol"></a>  CMFCOutlookBarTabCtrl::AddControl

为 Outlook 栏中的新选项卡中添加一个 Windows 控件。

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
[in]指向要添加的控件的指针。

*lpszName*<br/>
[in]指定选项卡的名称。

*bDetachable*<br/>
[in]如果为 TRUE，将创建页为可拆分。

*nImageID*<br/>
[in]在新选项卡中显示的图像的内部图像列表中的图像索引。

*dwControlBarStyle*<br/>
[in]指定已包装的停靠窗格 AFX_ CBRS_ * 样式。

### <a name="remarks"></a>备注

使用此函数作为新页的 outlook 栏添加一个控件。

此函数在内部调用上[cmfcbasetabctrl:: Addtab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)。

如果您设置*bDetachable*为 TRUE，`AddControl`会在内部创建`CDockablePaneAdapter`对象，并包装添加的控件。 它会自动设置为运行时类的选项卡式窗口的运行时类`CMFCOutlookBar`和运行时类在浮动帧的`CMultiPaneFrameWnd`。

### <a name="example"></a>示例

下面的示例演示如何使用`AddControl`中的方法`CMFCOutlookBarTabCtrl`类。 此代码片段属于[Outlook 演示示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

##  <a name="canshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowFewerPageButtons

在调整大小操作，以确定是否比当前可见，也可以显示更少的 Outlook 栏选项卡页按钮过程由框架调用。

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>返回值

如果多个按钮，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

Outlook 栏选项卡控件动态添加或删除从具体取决于如何太多空间可显示的选项卡。 该框架使用此方法可帮助完成该过程。

##  <a name="canshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowMorePageButtons

在调整大小操作，以确定是否比当前可见，也可以显示多个 Outlook 栏选项卡页按钮过程由框架调用。

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>返回值

如果按钮不是当前可见，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

Outlook 栏选项卡控件动态添加或删除的显示，具体取决于多少空间是可用的选项卡。 该框架使用此方法可帮助完成该过程。

##  <a name="create"></a>  CMFCOutlookBarTabCtrl::Create

创建 Outlook 栏选项卡控件。

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*rect*<br/>
[in]指定的初始大小和位置，以像素为单位。

*pParentWnd*<br/>
[in]指向父窗口。 不能为 NULL。

*nID*<br/>
[in]控件 id。

### <a name="return-value"></a>返回值

如果成功，则创建控件，非零值否则为 0。

### <a name="remarks"></a>备注

通常情况下，outlook 栏选项卡控件时，会创建[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)控制 WM_CREATE 消息的过程。

##  <a name="enableanimation"></a>  CMFCOutlookBarTabCtrl::EnableAnimation

指定是否启用动画时所发生的活动选项卡之间切换。

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
[in]指定是否应启用或禁用动画。

### <a name="remarks"></a>备注

调用此函数可启用和禁用动画。 当用户打开选项卡页时，页面的标题幻灯片向上或向下如果启用动画。 如果禁用了动画，页面将立即变为活动状态。

默认情况下已启用动画。

##  <a name="enableinplaceedit"></a>  CMFCOutlookBarTabCtrl::EnableInPlaceEdit

指定用户是否可以修改 Outlook 栏选项卡页按钮上的文本标签。

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
如果为 TRUE，则启用就地编辑的文本标签。 如果为 FALSE，则禁用就地编辑。

### <a name="remarks"></a>备注

调用此函数可启用或禁用就地编辑的选项卡页按钮上的文本标签。 默认情况下禁用就地编辑。

##  <a name="enablescrollbuttons"></a>  CMFCOutlookBarTabCtrl::EnableScrollButtons

由框架调用以启用滚动句柄，允许用户滚动浏览 Outlook 栏窗格上的按钮。

```
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
[in]确定是否显示滚动按钮。

*bIsUp*<br/>
[in]确定是否显示顶部的滚动条。

*bIsDown*<br/>
[in]确定是否显示底部滚动条。

### <a name="remarks"></a>备注

启用滚动按钮的显示功能。 活动选项卡更改要还原的滚动按钮时，由框架调用此方法。

##  <a name="getbordersize"></a>  CMFCOutlookBarTabCtrl::GetBorderSize

返回 Outlook 选项卡控件的边框大小。

```
int GetBorderSize() const;
```

### <a name="return-value"></a>返回值

边框的大小，以像素为单位。

##  <a name="getvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::GetVisiblePageButtons

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isanimation"></a>  CMFCOutlookBarTabCtrl::IsAnimation

指定是否启用动画时所发生的活动选项卡之间切换。

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>返回值

如果启用动画，则非零值否则为 0。

### <a name="remarks"></a>备注

调用[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)函数来启用或禁用动画。

##  <a name="ismode2003"></a>  CMFCOutlookBarTabCtrl::IsMode2003

确定 Outlook 栏选项卡控件是否在模拟 Microsoft Outlook 2003 模式下。

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>返回值

Outlook 栏选项卡控件在 Outlook 2003 模式下; 如果为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

通过设置此值[CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003)。

##  <a name="onshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowFewerPageButtons

由框架调用以减少可见的选项卡页按钮的数目。

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>备注

此方法在调整大小时该控件调整可见的页面选项卡按钮的数目。

##  <a name="onshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowMorePageButtons

由框架调用以增加可见的选项卡页按钮的数目。

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>备注

此方法调整控件的大小调整时，会显示的选项卡页按钮的数目。

##  <a name="onshowoptions"></a>  CMFCOutlookBarTabCtrl::OnShowOptions

显示**导航窗格选项**对话框。

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>备注

**导航窗格选项**对话框的允许用户选择的选项卡页按钮显示，以及所显示的顺序。

由框架调用此方法，当用户选择**导航窗格选项**从控件的自定义菜单的菜单项。

##  <a name="setactivetab"></a>  CMFCOutlookBarTabCtrl::SetActiveTab

设置活动选项卡。活动选项卡是处于打开状态，并使用其可见的内容。

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>参数

*iTab*<br/>
[in]若要打开的选项卡的从零开始的索引。

### <a name="return-value"></a>返回值

如果已成功，则打开指定的选项卡，非零值否则为 0。

### <a name="remarks"></a>备注

设置活动选项卡上的视觉效果取决于您是否已启用动画。 有关详细信息，请参阅[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)。

##  <a name="setbordersize"></a>  CMFCOutlookBarTabCtrl::SetBorderSize

设置 Outlook 选项卡控件的边框大小。

```
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>参数

*nBorderSize*<br/>
[in]以像素为单位指定新的边框大小。

### <a name="remarks"></a>备注

设置新边框大小并重新计算 outlook 窗口布局。

##  <a name="setpagebuttontextalign"></a>  CMFCOutlookBarTabCtrl::SetPageButtonTextAlign

设置上的 Outlook 栏选项卡按钮的文本标签的对齐方式。

```
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>参数

*uiAlign*<br/>
[in]指定的文本对齐方式。

*bRedraw*<br/>
[in]如果为 TRUE，则将重绘 outlook 窗口。

### <a name="remarks"></a>备注

使用此函数更改页面按钮的文本对齐方式。

*uiAlign*可以是下列值之一：

|返回的常量|含义|
|--------------|-------------|
|TA_LEFT|左的对齐|
|TA_CENTER|居中对齐|
|TA_RIGHT|右对齐|

默认值为 TA_CENTER。

##  <a name="settoolbarimagelist"></a>  CMFCOutlookBarTabCtrl::SetToolbarImageList

设置包含在 Outlook 2003 模式下的 Outlook 栏底部显示的图标的位图。

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>参数

*uiID*<br/>
[in]指定要加载图像的资源 ID。

*cx*<br/>
[in]在图像列表中，以像素为单位指定的图像的宽度。

*clrTransp*<br/>
[in]一个指定透明颜色的 RGB 值。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE否则返回 FALSE。

### <a name="remarks"></a>备注

使用此函数将附加图像列表将在 Microsoft Office 2003 模式下的工具栏按钮显示的图像。 映像索引应对应于页的索引。

如果未在 Microsoft Office 2003 模式下，不应调用此方法。 有关详细信息，请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

##  <a name="setvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::SetVisiblePageButtons

```
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>参数

[in] *nVisiblePageButtons*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarPane 类](../../mfc/reference/cmfcoutlookbarpane-class.md)
