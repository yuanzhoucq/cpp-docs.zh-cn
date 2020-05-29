---
title: CMFCOutlookBar 类
ms.date: 06/25/2018
f1_keywords:
- CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar::AllowDestroyEmptyTabbedPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanAcceptPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanSetCaptionTextToTabName
- AFXOUTLOOKBAR/CMFCOutlookBar::Create
- AFXOUTLOOKBAR/CMFCOutlookBar::CreateCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::DoesAllowDynInsertBefore
- AFXOUTLOOKBAR/CMFCOutlookBar::FloatTab
- AFXOUTLOOKBAR/CMFCOutlookBar::GetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::GetTabArea
- AFXOUTLOOKBAR/CMFCOutlookBar::IsMode2003
- AFXOUTLOOKBAR/CMFCOutlookBar::OnAfterAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnBeforeAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnScroll
- AFXOUTLOOKBAR/CMFCOutlookBar::RemoveCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::SetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::SetMode2003
helpviewer_keywords:
- CMFCOutlookBar [MFC], AllowDestroyEmptyTabbedPane
- CMFCOutlookBar [MFC], CanAcceptPane
- CMFCOutlookBar [MFC], CanSetCaptionTextToTabName
- CMFCOutlookBar [MFC], Create
- CMFCOutlookBar [MFC], CreateCustomPage
- CMFCOutlookBar [MFC], DoesAllowDynInsertBefore
- CMFCOutlookBar [MFC], FloatTab
- CMFCOutlookBar [MFC], GetButtonsFont
- CMFCOutlookBar [MFC], GetTabArea
- CMFCOutlookBar [MFC], IsMode2003
- CMFCOutlookBar [MFC], OnAfterAnimation
- CMFCOutlookBar [MFC], OnBeforeAnimation
- CMFCOutlookBar [MFC], OnScroll
- CMFCOutlookBar [MFC], RemoveCustomPage
- CMFCOutlookBar [MFC], SetButtonsFont
- CMFCOutlookBar [MFC], SetMode2003
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
ms.openlocfilehash: fe328cb0d857ff9154624d218b1b56362890ce81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369653"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar 类

在 Microsoft Outlook 2000 或 Outlook 2003 中具有 **“导航窗格”** 可视外观的选项卡式窗格。 该`CMFCOutlookBar`对象包含一个[CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)对象和一系列选项卡。 选项卡可以是[CMFCOutlookBarPane 类](../../mfc/reference/cmfcoutlookbarpane-class.md)对象或`CWnd`派生对象。 对于用户，Outlook 栏显示为一系列按钮和一个显示区域。 用户单击按钮时，将显示相应控件或按钮窗格。

## <a name="syntax"></a>语法

```cpp
class CMFCOutlookBar : public CBaseTabbedPane
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCOutlookBar::CMFCOutlookBar`|默认构造函数。|
|`CMFCOutlookBar::~CMFCOutlookBar`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定是否可以销毁空选项卡式窗格。 （覆盖[CBaseTabbed 窗格：：允许销毁空表板](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane)窗格 。|
|[CMFCOutlookBar：：接受窗格](#canacceptpane)|确定是否可以将另一个窗格停靠到 Outlook 栏窗格。 （覆盖可停靠窗格：：可接受窗格。|
|[CMFCOutlookbar：：canset标题文本标签名称](#cansetcaptiontexttotabname)|确定选项卡式窗格的标题是否显示与活动选项卡相同的文本。（覆盖[CBaseTabbed 窗格：：CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).）|
|[CMFCOutlookBar：创建](#create)|创建 Outlook 栏控件。|
|[CMFCOutlookBar：创建自定义页面](#createcustompage)|创建自定义 Outlook 栏选项卡。|
|`CMFCOutlookBar::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFC观景栏：:DoesAllowDynInsert之前](#doesallowdyninsertbefore)|确定用户是否可以停靠 Outlook 栏外边缘的控制栏。|
|[CMFCOutlookBar：浮动选项卡](#floattab)|浮动窗格，但前提是窗格当前驻留在可拆卸选项卡中。（覆盖[CBaseTabbedPane：：FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).|
|[CMFCOutlookBar：获取按钮字体](#getbuttonsfont)|返回 Outlook 栏按钮上文本的字体。|
|[CMFCOutlookBar：GetTabArea](#gettabarea)|返回 Outlook 栏上选项卡区域的大小和位置。 （覆盖[CBaseTabbed 窗格：获取 Tab 区域](../../mfc/reference/cbasetabbedpane-class.md#gettabarea)。）|
|`CMFCOutlookBar::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCOutlookBar：isMode2003](#ismode2003)|确定 Outlook 栏的行为是否与 Microsoft Office Outlook 2003 的行为仿一致（请参阅备注）。|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|由[CMFCOutlookBarTabCtrl 调用：：](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)使用动画设置活动选项卡后设置活动选项卡。|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|由[CMFCOutlookBarTabCtrl 调用：：](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)在使用动画将选项卡页设置为活动选项卡之前设置活动选项卡。|
|[CMFCOutlookBar::OnScroll](#onscroll)|如果 Outlook 栏向上或向下滚动，则由框架调用。|
|[CMFCOutlookBar：删除自定义页面](#removecustompage)|删除自定义 Outlook 栏选项卡。|
|[CMFCOutlookBar：：设置按钮字体](#setbuttonsfont)|设置 Outlook 栏按钮上的文本字体。|
|[CMFCOutlookBar：SetMode2003](#setmode2003)|指定 Outlook 栏的行为是否与 Outlook 2003 的行为仿一致（请参阅备注）。|

## <a name="remarks"></a>备注

有关 Outlook 栏的示例，请参阅[OutlookDemo 示例：MFC OutlookDemo 应用程序](../../overview/visual-cpp-samples.md)。

## <a name="implementing-the-outlook-bar"></a>实现 Outlook 栏

若要在应用程序中使用 `CMFCOutlookBar` 控件，请执行以下步骤：

1. 将 `CMFCOutlookBar` 对象嵌入主框架窗口类。

    ```cpp
    class CMainFrame : public CMDIFrameWnd
    {
        // ...
        CMFCOutlookBar m_wndOutlookBar;
        CMFCOutlookBarPane m_wndOutlookPane;
        // ...
    };
    ```

1. 在主帧中处理WM_CREATE消息时，调用[CMFCOutlookBar：：创建](#create)方法来创建 Outlook 栏选项卡控件。

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. 使用`CMFCOutlookBarTabCtrl`[CBaseTabbedPane 获取指向基础的指针：：获取基础窗口](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)。

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. 为包含按钮的每个选项卡创建一个[CMFCOutlookBarPane 类](../../mfc/reference/cmfcoutlookbarpane-class.md)对象。

    ```cpp
    m_wndOutlookPane.Create(&m_wndOutlookBar,
        AFX_DEFAULT_TOOLBAR_STYLE,
        ID_OUTLOOK_PANE_GENERAL,
        AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);

    // make the Outlook pane detachable (enable docking)
    m_wndOutlookPane.EnableDocking(CBRS_ALIGN_ANY);

    // add buttons
    m_wndOutlookPane.AddButton(theApp.LoadIcon (IDR_MAINFRAME),
        "About",
        ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON),
        "Open",
        ID_FILE_OPEN);
    ```

1. 调用[CMFCOutlookBarTabCtrl：：AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)以添加每个新选项卡。将*可分离*参数设置为 FALSE 以使页面不可拆卸。 或者，使用[CMFCOutlookBarTabCtrl：：添加控制](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol)以添加可拆卸页面。

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. 要将`CWnd`派生控件（例如[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)）添加为选项卡，请创建控件并调用[CMFCOutlookBarTabctrl：：addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)将其添加到 Outlook 栏。

> [!NOTE]
> 您应该对每个[CMFCOutlookBarPane 类](../../mfc/reference/cmfcoutlookbarpane-class.md)对象和每个`CWnd`派生对象使用唯一控件 ID。

要在运行时动态添加或删除新页面，请使用[CMFCOutlookBar：：创建自定义页](#createcustompage)和[CMFCOutlookBar：：删除自定义页](#removecustompage)。

## <a name="outlook-2003-mode"></a>展望 2003 模式

在 Outlook 2003 模式下，选项卡按钮位于 Outlook 栏窗格的底部。 当没有足够的空间来显示按钮时，它们将作为图标显示在窗格底部的工具栏类似区域中。

使用[CMFCOutlookBar：setMode2003](#setmode2003)启用 Outlook 2003 模式。 使用[CMFCOutlookBarTabCtrl：：设置工具栏图像列表](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist)来设置包含 Outlook 栏底部显示的图标的位图。 位图中的图标必须由选项卡索引排序。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[可装窗格](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)

## <a name="requirements"></a>要求

**标题：** afxOutlookbar.h

## <a name="cmfcoutlookbarallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CMFCOutlookBar：：允许销毁空单板

指定是否可以销毁空选项卡式窗格。

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>返回值

如果可以销毁空选项卡式窗格，则为 TRUE;否则，FALSE。 默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

如果无法销毁空选项卡式窗格，则框架将隐藏它。

## <a name="cmfcoutlookbarcanacceptpane"></a><a name="canacceptpane"></a>CMFCOutlookBar：：接受窗格

确定是否可以将另一个窗格停靠到 Outlook 栏窗格。

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>参数

*pBar*<br/>
[在]指向另一个要停靠到此窗格的窗格的指针。

### <a name="return-value"></a>返回值

如果另一个窗格可以停靠到 Outlook 栏窗格，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

如果 Outlook 栏处于 Outlook 2003 模式，则不支持停靠，因此返回值为 FALSE。

如果*pBar*参数为 NULL，则此方法返回 FALSE。

否则，此方法将充当基本方法[CBasePane：：canAcceptPane，](../../mfc/reference/cbasepane-class.md#canacceptpane)只不过即使未启用停靠，Outlook 栏仍可以启用另一个 Outlook 栏停靠在它上。

## <a name="cmfcoutlookbarcansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CMFCOutlookbar：：canset标题文本标签名称

确定选项卡式窗格的标题是否显示与活动选项卡相同的文本。

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>返回值

如果 Outlook 栏标题自动设置为活动选项卡的文本，则为 TRUE;如果 Outlook 窗口标题自动设置为活动选项卡的文本，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

使用[CBaseTabbed 窗格：：启用设置标题文本标签名称](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname)以启用或禁用此功能。

在 Outlook 2003 模式下，此设置始终处于启用状态。

## <a name="cmfcoutlookbarcreate"></a><a name="create"></a>CMFCOutlookBar：创建

创建 Outlook 栏控件。

```cpp
virtual BOOL Create(
    LPCTSTR lpszCaption,
    CWnd* pParentWnd,
    const RECT& rect,
    UINT nID,
    DWORD dwStyle,
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>参数

*lpszCaption*<br/>
[在]指定窗口标题。

*pparentwnd*<br/>
[在]指定指向父窗口的指针。 值不得为 NULL。

*矩形*<br/>
[在]指定以像素为单位的 Outlook 栏大小和位置。

*nID*<br/>
[在]指定控件 ID。 必须与应用程序中使用的其他控件指示的不同。

*dwStyle*<br/>
[在]指定所需的控制栏样式。 有关可能的值，请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*dwControlBar样式*<br/>
[在]指定特殊库定义的样式。

*pContext*<br/>
[在]创建上下文。

### <a name="return-value"></a>返回值

如果方法成功，则非零;否则 0。

### <a name="remarks"></a>备注

分两步`CMFCOutlookBar`构造对象。 首先调用构造函数，然后调用`Create`，这将创建 Outlook 栏控件并将其附加到`CMFCOutlookBar`对象。

请参阅[CBasePane：为](../../mfc/reference/cbasepane-class.md#createex) *dwControlBarStyle*指定的可用库定义样式的列表创建Ex。

### <a name="example"></a>示例

下面的示例演示如何使用`Create``CMFCOutlookBar`类的方法。 此代码段是 Outlook[多视图示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

## <a name="cmfcoutlookbarcreatecustompage"></a><a name="createcustompage"></a>CMFCOutlookBar：创建自定义页面

创建自定义 Outlook 栏选项卡。

```cpp
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,
    BOOL bActivatePage=TRUE,
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,
    BOOL bEnableTextLabels=TRUE);
```

### <a name="parameters"></a>参数

*lpszPage名称*<br/>
[在]页面标签。

*b 激活页面*<br/>
[在]如果为 TRUE，则页面在创建时变为活动状态。

*启用的停靠*<br/>
[在]CBRS_ALIGN_标志的组合，用于指定分离页面时启用的停靠侧。

*b 启用文本标签*<br/>
[在]如果为 TRUE，则为驻留在页面上的按钮启用文本标签。

### <a name="return-value"></a>返回值

指向新创建的页面的指针，如果创建失败，则指向 NULL。

### <a name="remarks"></a>备注

使用此方法使用户能够创建自定义 Outlook 栏页。 每个应用程序最多可以创建 100 页。 页面控件指示码从 0xF000 开始。 如果自定义 Outlook 栏页总数超过 100，则创建将失败。

使用[CMFCOutlookBar：删除自定义页面](#removecustompage)以删除自定义页面。

## <a name="cmfcoutlookbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFC观景栏：:DoesAllowDynInsert之前

指定用户是否可以停靠 Outlook 栏外边缘的窗格。

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>返回值

默认实现返回 FALSE。

### <a name="remarks"></a>备注

当框架查找停靠`DoesAllowDynInsertBefore`动态窗格的位置时，将调用该方法。 如果函数返回 FALSE，则框架不允许在窗格的外边缘停靠任何动态窗格。

通常，您将创建 Outlook 栏作为静态非浮动控件。 您可以在派生类中重写此函数，并返回 TRUE 以更改此行为。

> [!NOTE]
> 由于动态窗格在停靠时检查停靠静态窗格的状态，因此应尽可能将动态窗格停靠在静态窗格之后。

## <a name="cmfcoutlookbarfloattab"></a><a name="floattab"></a>CMFCOutlookBar：浮动选项卡

浮动窗格。

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[在]指向窗格的指针以浮动。

*nTabID*<br/>
[在]要浮动的选项卡的零基索引。

*基方法*<br/>
[在]指定用于使窗格浮动的方法。  有关详细信息，请参阅[CBaseTabbedPane：：FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。

*bHide*<br/>
[在]TRUE 以在浮动前隐藏窗格;否则，FALSE。 与此方法的基类版本不同，此参数没有默认值。

### <a name="return-value"></a>返回值

如果窗格浮动，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法类似于[CBaseTabbedPane：：FloatTab，](../../mfc/reference/cbasetabbedpane-class.md#floattab)只不过它不允许 Outlook 栏控件上的最后一个剩余选项卡浮动。

## <a name="cmfcoutlookbargetbuttonsfont"></a><a name="getbuttonsfont"></a>CMFCOutlookBar：获取按钮字体

返回 Outlook 栏的页面按钮选项卡上的文本字体。

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>返回值

指向用于在 Outlook 栏页按钮选项卡上显示文本的字体对象的指针。

### <a name="remarks"></a>备注

使用此函数可以检索用于在 Outlook 页按钮选项卡上显示文本的字体。 您可以通过调用[CMFCOutlookBar 来设置字体：设置ButtonsFont](#setbuttonsfont)。

## <a name="cmfcoutlookbargettabarea"></a><a name="gettabarea"></a>CMFCOutlookBar：GetTabArea

确定 Outlook 栏上选项卡区域的大小和位置。

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>参数

*rectTabAreaTop*<br/>
[出]当函数返回时，包含顶部选项卡区域的大小和位置（在客户端坐标中）。

*rectTab区域底部*<br/>
[出]当函数返回时，包含底部选项卡区域的大小和位置（在客户端坐标中）。

### <a name="remarks"></a>备注

框架调用此方法以确定与目标窗格的停靠类型。 当框架确定用户拖动窗格以停靠在目标窗格的选项卡区域时，它会尝试将第一个窗格添加为目标窗格的新选项卡。 否则，它将尝试将第一个窗格停靠在目标窗格的相应一侧。 框架创建一个带有滑块的新容器，以适应其他停靠窗格。

如果 Outlook`GetTabArea`栏是静态的，则 默认实现返回 Outlook 栏的整个工作区;如果 Outlook 栏是静态的，则默认实现返回 Outlook 栏的整个工作区。也就是说，如果 Outlook 栏无法浮动。 否则，它将返回页面按钮在 Outlook 栏控件的顶部和底部获取的区域。

在派生的`CMFCOutlookBar`类中重写此方法以更改此行为。

## <a name="cmfcoutlookbarismode2003"></a><a name="ismode2003"></a>CMFCOutlookBar：isMode2003

指定 Outlook 栏的行为是否与 Microsoft Office Outlook 2003 的行为仿一。

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>返回值

如果 Outlook 栏在 Microsoft Office 2003 模式下运行，则非零;否则 0。

### <a name="remarks"></a>备注

您可以使用[CMFCOutlookBar：：setMode2003](#setmode2003)启用此模式。

## <a name="cmfcoutlookbaronafteranimation"></a><a name="onafteranimation"></a>CMFCOutlookBar：在动画之后

由[CMFCOutlookBarTabCtrl 调用：：](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)使用动画设置活动选项卡后设置活动选项卡。

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>参数

*nPage*<br/>
[在]已变为活动的选项卡页的零基索引。

### <a name="remarks"></a>备注

设置活动选项卡的视觉效果取决于是否已启用动画。 有关详细信息，请参阅[CMFCOutlookBarTabCtrl：：启用动画](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation)。

## <a name="cmfcoutlookbaronbeforeanimation"></a><a name="onbeforeanimation"></a>CMFCOutlookBar：：在动画前打开

由[CMFCOutlookBarTabCtrl 调用：：](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)在使用动画将选项卡页设置为活动选项卡之前设置活动选项卡。

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>参数

*nPage*<br/>
[在]即将设置为活动的选项卡页的零基索引。

### <a name="return-value"></a>返回值

如果应在设置新的活动选项卡时使用动画，则返回 TRUE;如果应禁用动画，则返回 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcoutlookbaronscroll"></a><a name="onscroll"></a>CMFCOutlookbar：：OnScroll

如果 Outlook 栏向上或向下滚动，则由框架调用。

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>参数

*b向下*<br/>
[在]如果 Outlook 栏向下滚动，则为 TRUE;如果"Outlook"栏向上滚动，则为 TRUE。

### <a name="remarks"></a>备注

## <a name="cmfcoutlookbarremovecustompage"></a><a name="removecustompage"></a>CMFCOutlookBar：删除自定义页面

删除自定义 Outlook 栏选项卡页。

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>参数

*uiPage*<br/>
[在]父 Outlook 窗口中页面的基于零的索引。

*p目标Wnd*<br/>
[在]指针到父 Outlook 窗口。

### <a name="return-value"></a>返回值

如果自定义页已成功删除，则非零;否则 0。

### <a name="remarks"></a>备注

调用此函数以删除自定义页面。 删除页面时，其控制 ID 将返回到可用 ID 池。

您必须提供指向[CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)对象的指针，其中要删除的页面当前驻留。 请注意，用户可以在不同的 Outlook 栏之间移动可拆卸页面，但有关自定义页面的信息位于已为其调用 CMFCOutlookBar 的 Outlook 栏对象中[：：：创建自定义页](#createcustompage)。

使用[CBaseTabbed 窗格：获取基础窗口](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)以获取指向 Outlook 窗口的指针。

## <a name="cmfcoutlookbarsetbuttonsfont"></a><a name="setbuttonsfont"></a>CMFCOutlookBar：：设置按钮字体

设置 Outlook 栏按钮上的文本字体。

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>参数

*pFont*<br/>
[在]指定新字体。

*bredraw*<br/>
[在]如果为 TRUE，则将重绘 Outlook 栏。

### <a name="remarks"></a>备注

使用此方法可为 Outlook 选项卡页按钮上显示的文本设置字体。

## <a name="cmfcoutlookbarsetmode2003"></a><a name="setmode2003"></a>CMFCOutlookBar：SetMode2003

指定 Outlook 栏的行为是否与 Outlook 2003 的行为仿一。

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>参数

*bMode2003*<br/>
[在]如果为 TRUE，则启用 Office 2003 模式。

### <a name="remarks"></a>备注

使用此函数可启用或禁用 Office 2003 模式。 在此模式下，Outlook 栏具有附加工具栏，带有自定义按钮。 Outlook 栏的行为符合 Microsoft Office 2003 中 Outlook 栏的行为。

默认情况下，此模式已禁用。

> [!NOTE]
> 必须在[CMFCOutlookBar：：：创建](#create)之前调用此功能。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CBaseTabbedPane 类](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[CMFCOutlookBarPane 类](../../mfc/reference/cmfcoutlookbarpane-class.md)
