---
title: CMDIChildWndEx 类 |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMDIChildWndEx
- AFXMDICHILDWNDEX/CMDIChildWndEx
- AFXMDICHILDWNDEX/CMDIChildWndEx::ActivateTopLevelFrame
- AFXMDICHILDWNDEX/CMDIChildWndEx::AddPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::AddTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::AdjustDockingLayout
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnMDITabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnTaskBarTabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnWindowsList
- AFXMDICHILDWNDEX/CMDIChildWndEx::DockPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::DockPaneLeftOf
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableAutoHidePanes
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableDocking
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetDockingManager
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetDocumentName
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetFrameIcon
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetFrameText
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetRelatedTabGroup
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTabProxyWnd
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTaskbarPreviewWnd
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetToolbarButtonToolTipText
- AFXMDICHILDWNDEX/CMDIChildWndEx::InsertPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::InvalidateIconicBitmaps
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsPointNearDockSite
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsReadOnly
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsRegisteredWithTaskbarTabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTaskbarTabsSupportEnabled
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled
- AFXMDICHILDWNDEX/CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnGetIconicLivePreviewBitmap
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnGetIconicThumbnail
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnMoveMiniFrame
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnSetPreviewMode
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailActivate
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailStretch
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnUpdateFrameTitle
- AFXMDICHILDWNDEX/CMDIChildWndEx::PaneFromPoint
- AFXMDICHILDWNDEX/CMDIChildWndEx::RecalcLayout
- AFXMDICHILDWNDEX/CMDIChildWndEx::RegisterTaskbarTab
- AFXMDICHILDWNDEX/CMDIChildWndEx::RemovePaneFromDockManager
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetRelatedTabGroup
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabActive
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabOrder
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabProperties
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::ShowPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::UnregisterTaskbarTab
- AFXMDICHILDWNDEX/CMDIChildWndEx::UpdateTaskbarTabIcon
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWndEx [MFC], ActivateTopLevelFrame
- CMDIChildWndEx [MFC], AddPane
- CMDIChildWndEx [MFC], AddTabbedPane
- CMDIChildWndEx [MFC], AdjustDockingLayout
- CMDIChildWndEx [MFC], CanShowOnMDITabs
- CMDIChildWndEx [MFC], CanShowOnTaskBarTabs
- CMDIChildWndEx [MFC], CanShowOnWindowsList
- CMDIChildWndEx [MFC], DockPane
- CMDIChildWndEx [MFC], DockPaneLeftOf
- CMDIChildWndEx [MFC], EnableAutoHidePanes
- CMDIChildWndEx [MFC], EnableDocking
- CMDIChildWndEx [MFC], EnableTaskbarThumbnailClipRect
- CMDIChildWndEx [MFC], GetDockingManager
- CMDIChildWndEx [MFC], GetDocumentName
- CMDIChildWndEx [MFC], GetFrameIcon
- CMDIChildWndEx [MFC], GetFrameText
- CMDIChildWndEx [MFC], GetPane
- CMDIChildWndEx [MFC], GetRelatedTabGroup
- CMDIChildWndEx [MFC], GetTabbedPane
- CMDIChildWndEx [MFC], GetTabProxyWnd
- CMDIChildWndEx [MFC], GetTaskbarPreviewWnd
- CMDIChildWndEx [MFC], GetTaskbarThumbnailClipRect
- CMDIChildWndEx [MFC], GetToolbarButtonToolTipText
- CMDIChildWndEx [MFC], InsertPane
- CMDIChildWndEx [MFC], InvalidateIconicBitmaps
- CMDIChildWndEx [MFC], IsPointNearDockSite
- CMDIChildWndEx [MFC], IsReadOnly
- CMDIChildWndEx [MFC], IsRegisteredWithTaskbarTabs
- CMDIChildWndEx [MFC], IsTabbedPane
- CMDIChildWndEx [MFC], IsTaskbarTabsSupportEnabled
- CMDIChildWndEx [MFC], IsTaskbarThumbnailClipRectEnabled
- CMDIChildWndEx [MFC], m_dwDefaultTaskbarTabPropertyFlags
- CMDIChildWndEx [MFC], OnGetIconicLivePreviewBitmap
- CMDIChildWndEx [MFC], OnGetIconicThumbnail
- CMDIChildWndEx [MFC], OnMoveMiniFrame
- CMDIChildWndEx [MFC], OnPressTaskbarThmbnailCloseButton
- CMDIChildWndEx [MFC], OnSetPreviewMode
- CMDIChildWndEx [MFC], OnTaskbarTabThumbnailActivate
- CMDIChildWndEx [MFC], OnTaskbarTabThumbnailMouseActivate
- CMDIChildWndEx [MFC], OnTaskbarTabThumbnailStretch
- CMDIChildWndEx [MFC], OnUpdateFrameTitle
- CMDIChildWndEx [MFC], PaneFromPoint
- CMDIChildWndEx [MFC], RecalcLayout
- CMDIChildWndEx [MFC], RegisterTaskbarTab
- CMDIChildWndEx [MFC], RemovePaneFromDockManager
- CMDIChildWndEx [MFC], SetRelatedTabGroup
- CMDIChildWndEx [MFC], SetTaskbarTabActive
- CMDIChildWndEx [MFC], SetTaskbarTabOrder
- CMDIChildWndEx [MFC], SetTaskbarTabProperties
- CMDIChildWndEx [MFC], SetTaskbarThumbnailClipRect
- CMDIChildWndEx [MFC], ShowPane
- CMDIChildWndEx [MFC], UnregisterTaskbarTab
- CMDIChildWndEx [MFC], UpdateTaskbarTabIcon
ms.assetid: d39fec06-0bd6-4271-917d-35aae3b24d8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64e8b62f79a6294810fc30b1796958c6ca4a153a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073859"
---
# <a name="cmdichildwndex-class"></a>CMDIChildWndEx 类

`CMDIChildWndEx`类提供的功能的 Windows 多文档界面 (MDI) 子窗口。 它扩展的功能[CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)。 当 MDI 应用程序使用特定 MFC 类时，框架需要此类。

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

## <a name="syntax"></a>语法

```
class CMDIChildWndEx : public CMDIChildWnd
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMDIChildWndEx::ActivateTopLevelFrame](#activatetoplevelframe)|由框架在应用程序应从任务栏选项卡激活激活顶级框架在内部调用。|
|`CMDIChildWndEx::AddDockSite`|此方法不使用或实现。|
|[CMDIChildWndEx::AddPane](#addpane)|添加窗格。|
|[CMDIChildWndEx::AddTabbedPane](#addtabbedpane)|添加选项卡式的窗格。|
|[CMDIChildWndEx::AdjustDockingLayout](#adjustdockinglayout)|调整停靠布局。|
|[CMDIChildWndEx::CanShowOnMDITabs](#canshowonmditabs)||
|[CMDIChildWndEx::CanShowOnTaskBarTabs](#canshowontaskbartabs)|指示是否可以在 Windows 7 任务栏选项卡上显示此 MDI 子窗体的框架。|
|[CMDIChildWndEx::CanShowOnWindowsList](#canshowonwindowslist)|如果可以在中显示 MDI 子窗口名称，则返回 TRUE [CMFCWindowsManagerDialog 类](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)对话框。 否则返回 FALSE。|
|`CMDIChildWndEx::CreateObject`|由框架调用以创建此类类型的动态实例。|
|[CMDIChildWndEx::DockPane](#dockpane)|将停靠窗格。|
|[CMDIChildWndEx::DockPaneLeftOf](#dockpaneleftof)|将一个窗格停靠到另一个窗格的左侧。|
|[CMDIChildWndEx::EnableAutoHidePanes](#enableautohidepanes)|启用自动隐藏模式对于窗格停靠在指定窗口的边时。|
|[CMDIChildWndEx::EnableDocking](#enabledocking)|启用子窗口停靠到主框架。|
|[CMDIChildWndEx::EnableTaskbarThumbnailClipRect](#enabletaskbarthumbnailcliprect)|启用或禁用自动选择窗口的客户端区域将显示为该窗口在任务栏中的缩略图的一部分。|
|[CMDIChildWndEx::GetDockingManager](#getdockingmanager)||
|[CMDIChildWndEx::GetDocumentName](#getdocumentname)|返回的文档的 MDI 子窗口中显示的名称。|
|[CMDIChildWndEx::GetFrameIcon](#getframeicon)|由框架调用以检索 MDI 子窗口图标。|
|[CMDIChildWndEx::GetFrameText](#getframetext)|由框架调用以检索 MDI 子窗口的文本。|
|[CMDIChildWndEx::GetPane](#getpane)|查找窗格由指定的控件 id。|
|[CMDIChildWndEx::GetRelatedTabGroup](#getrelatedtabgroup)||
|[CMDIChildWndEx::GetTabbedPane](#gettabbedpane)|返回一个指向已转换为选项卡式文档嵌入停靠窗格。|
|[CMDIChildWndEx::GetTabProxyWnd](#gettabproxywnd)|返回选项卡上代理窗口实际注册到 Windows 7 任务栏选项卡。|
|[CMDIChildWndEx::GetTaskbarPreviewWnd](#gettaskbarpreviewwnd)|需要获取要在 Windows 7 任务栏选项卡缩略图上显示的子窗口 （通常是一个视图或拆分器窗口） 时由框架调用。|
|[CMDIChildWndEx::GetTaskbarThumbnailClipRect](#gettaskbarthumbnailcliprect)|需要选择窗口的工作区将显示为该窗口在任务栏中的缩略图的一部分时，由框架调用。|
|`CMDIChildWndEx::GetThisClass`|由框架调用以获取的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|[CMDIChildWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|由框架调用以检索工具栏按钮的工具提示。|
|[CMDIChildWndEx::InsertPane](#insertpane)|注册到停靠管理器指定窗格。|
|[CMDIChildWndEx::InvalidateIconicBitmaps](#invalidateiconicbitmaps)|使无效 MDI 子窗体的图标位图表示的形式。|
|[CMDIChildWndEx::IsPointNearDockSite](#ispointneardocksite)|确定指定的点是否在停靠站点附近。|
|[CMDIChildWndEx::IsReadOnly](#isreadonly)|如果在子窗口中显示的文档是只读的则返回 TRUE。 否则返回 FALSE。|
|[CMDIChildWndEx::IsRegisteredWithTaskbarTabs](#isregisteredwithtaskbartabs)|如果 MDI 子窗体已成功注册到 Windows 7 任务栏选项卡，则返回 TRUE。|
|[CMDIChildWndEx::IsTabbedPane](#istabbedpane)|如果 MDI 子窗口包含停靠窗格，则返回 TRUE。 否则返回 FALSE。|
|[CMDIChildWndEx::IsTaskbarTabsSupportEnabled](#istaskbartabssupportenabled)|指示是否可在 Windows 7 任务栏选项卡上显示 MDI 子窗体。|
|[CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled](#istaskbarthumbnailcliprectenabled)|指示是否启用或禁用自动选择窗口的客户端区域将显示为该窗口在任务栏中的缩略图的一部分。|
|[CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags](#m_dwdefaulttaskbartabpropertyflags)|与 Windows 7 任务栏选项卡，为其注册的标志，该框架传递给 SetTaskbarTabProperties 方法，当选项卡 （MDI 子级） 的组合。 默认值组合是 STPF_USEAPPTHUMBNAILWHENACTIVE &#124; STPF_USEAPPPEEKWHENACTIVE。|
|[CMDIChildWndEx::OnGetIconicLivePreviewBitmap](#ongeticoniclivepreviewbitmap)|需要获取的 MDI 子窗体的实时预览的位图时由框架调用。|
|[CMDIChildWndEx::OnGetIconicThumbnail](#ongeticonicthumbnail)|需要获取的 MDI 子窗体的图标缩略图的位图时由框架调用。|
|[CMDIChildWndEx::OnMoveMiniFrame](#onmoveminiframe)|由框架调用以移动微型框架窗口。|
|[CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton](#onpresstaskbarthmbnailclosebutton)|在用户按任务栏选项卡缩略图上的关闭按钮时由框架调用...|
|[CMDIChildWndEx::OnSetPreviewMode](#onsetpreviewmode)|由框架调用以进入或退出打印预览模式。|
|[CMDIChildWndEx::OnTaskbarTabThumbnailActivate](#ontaskbartabthumbnailactivate)|当任务栏选项卡缩略图应处理 WM_ACTIVATE 消息时由框架调用。|
|[CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate](#ontaskbartabthumbnailmouseactivate)|当任务栏选项卡缩略图应处理 WM_MOUSEACTIVATE 消息时由框架调用。|
|[CMDIChildWndEx::OnTaskbarTabThumbnailStretch](#ontaskbartabthumbnailstretch)|需要拉伸的 MDI 子窗体的 Windows 7 任务栏选项卡缩略图预览的位图时由框架调用。|
|[CMDIChildWndEx::OnUpdateFrameTitle](#onupdateframetitle)|由框架调用以更新框架标题。 （重写 `CMDIChildWnd::OnUpdateFrameTitle`。）|
|[CMDIChildWndEx::PaneFromPoint](#panefrompoint)|返回包含给定的点的窗格。|
|`CMDIChildWndEx::PreTranslateMessage`|在将窗口消息发送到 [TranslateMessage](../../mfc/reference/cwinapp-class.md) 和 [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) Windows 函数之前，由 [CWinApp](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) 类用于对此消息进行转换。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|
|[CMDIChildWndEx::RecalcLayout](#recalclayout)|重新计算窗口的布局。|
|[CMDIChildWndEx::RegisterTaskbarTab](#registertaskbartab)|注册 Windows 7 任务栏选项卡的 MDI 子窗体。|
|[CMDIChildWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)|从到停靠管理器中删除一个窗格。|
|[CMDIChildWndEx::SetRelatedTabGroup](#setrelatedtabgroup)||
|[CMDIChildWndEx::SetTaskbarTabActive](#settaskbartabactive)|激活相应的 Windows 7 任务栏选项卡。|
|[CMDIChildWndEx::SetTaskbarTabOrder](#settaskbartaborder)|将插入之前在 Windows 7 任务栏选项卡上指定的窗口的 MDI 子窗口。|
|[CMDIChildWndEx::SetTaskbarTabProperties](#settaskbartabproperties)|设置 Windows 7 任务栏选项卡的属性。|
|[CMDIChildWndEx::SetTaskbarThumbnailClipRect](#settaskbarthumbnailcliprect)|在内部由框架调用以设置剪辑矩形框来选择窗口的工作区将显示为该窗口在任务栏中的缩略图的一部分。|
|[CMDIChildWndEx::ShowPane](#showpane)||
|[CMDIChildWndEx::UnregisterTaskbarTab](#unregistertaskbartab)|从 Windows 7 任务栏选项卡中删除 MDI 子窗体。|
|[CMDIChildWndEx::UpdateTaskbarTabIcon](#updatetaskbartabicon)|更新 Windows 7 任务栏选项卡图标。|

## <a name="remarks"></a>备注

若要充分利用扩展坞功能 MDI 应用程序中，派生从应用程序的 MDI 子窗口类`CMDIChildWndEx`而不是[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)。

## <a name="example"></a>示例

以下示例从一个类从`CMDIChildWndEx`。 此代码片段来自[VisualStudioDemo 示例： MFC Visual Studio 应用程序](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#3](../../mfc/codesnippet/cpp/cmdichildwndex-class_1.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)

[CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md)

## <a name="requirements"></a>要求

**标头：** afxMDIChildWndEx.h

##  <a name="addpane"></a>  CMDIChildWndEx::AddPane

添加窗格。

```
BOOL AddPane(
    CBasePane* pControlBar,
    BOOL bTail = TRUE);
```

### <a name="parameters"></a>参数

*pControlBar*<br/>
[in]指向在窗格的指针。

*bTail*<br/>
[in]为 TRUE，则将窗格添加到窗格的列表的末尾，停靠管理器;否则为 FALSE。

### <a name="return-value"></a>返回值

如果窗格已成功注册到停靠管理器; 则为 TRUE否则为 FALSE。

##  <a name="addtabbedpane"></a>  CMDIChildWndEx::AddTabbedPane

添加选项卡式的窗格。

```
void AddTabbedPane(CDockablePane* pControlBar);
```

### <a name="parameters"></a>参数

*pControlBar*<br/>
[in]指向在窗格的指针。

##  <a name="adjustdockinglayout"></a>  CMDIChildWndEx::AdjustDockingLayout

调整停靠布局。

```
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```

### <a name="parameters"></a>参数

*hdwp*<br/>
[in]延迟的窗口位置结构的句柄。

##  <a name="canshowonmditabs"></a>  CMDIChildWndEx::CanShowOnMDITabs

```
virtual BOOL CanShowOnMDITabs();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="canshowonwindowslist"></a>  CMDIChildWndEx::CanShowOnWindowsList

指定是否可以在中显示 MDI 子窗口名称[CMFCWindowsManagerDialog 类](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)对话框。

```
virtual BOOL CanShowOnWindowsList();
```

### <a name="return-value"></a>返回值

如果窗口可以显示在**Windows**对话框; 否则为 FALSE。

### <a name="remarks"></a>备注

重写此方法在派生类中的，并返回 FALSE，如果窗口应不会显示在**Windows**对话框。 调用此函数可从`CMFCWindowsManagerDialog`。

##  <a name="dockpane"></a>  CMDIChildWndEx::DockPane

将停靠窗格。

```
void DockPane(
    CBasePane* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[in]指向在窗格的指针。

*nDockBarID*<br/>
[in]在窗格的 ID。

*lpRect*<br/>
[in]指向一个矩形的指针。

### <a name="remarks"></a>备注

*LpRect*未使用参数。

##  <a name="dockpaneleftof"></a>  CMDIChildWndEx::DockPaneLeftOf

将一个窗格停靠到另一个窗格的左侧。

```
BOOL DockPaneLeftOf(
    CPane* pBar,
    CPane* pLeftOf);
```

### <a name="parameters"></a>参数

*pBar*<br/>
指向要停靠的窗格的指针。

*pLeftOf*<br/>
指向用作引用的点的窗格的指针。

### <a name="return-value"></a>返回值

成功 TRUE、 FALSE 失败。

### <a name="remarks"></a>备注

此方法采用指定窗格*pBar*并将其停靠在左侧和右侧的窗格中指定的*pLeftOf*。

如果想要停靠在预定义顺序中的几个窗格，请调用此方法。

##  <a name="enableautohidepanes"></a>  CMDIChildWndEx::EnableAutoHidePanes

启用自动隐藏模式对于窗格停靠在指定窗口的边时。

```
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```

### <a name="parameters"></a>参数

*dwDockStyle*<br/>
[in]指定启用的主框架窗口的边。 使用一个或多个下列标志。

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE否则为 FALSE。

##  <a name="enabledocking"></a>  CMDIChildWndEx::EnableDocking

启用子窗口停靠到主框架。

```
BOOL EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>参数

*dwDockStyle*<br/>
[in]指定要启用的扩展对齐方式。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

调用此方法以启用停靠到主框架的对齐方式。 可以将传递 CBRS_ALIGN_ 标志的组合 (有关详细信息，请参阅[CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking))。

##  <a name="getdockingmanager"></a>  CMDIChildWndEx::GetDockingManager

```
CDockingManager* GetDockingManager();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getdocumentname"></a>  CMDIChildWndEx::GetDocumentName

返回的文档的 MDI 子窗口中显示的名称。

```
virtual LPCTSTR GetDocumentName(CObject** pObj);
```

### <a name="return-value"></a>返回值

指向包含文档的名称的字符串的指针。

### <a name="remarks"></a>备注

文档是 MDI 子窗口的显示内容。 通常情况下，该窗口显示从加载或保存到文件中的数据。 因此，文档的名称是文件的名称。 默认实现`GetDocumentName`返回的字符串从获取`CDocument::GetPathName`。

如果该窗口显示未从文件加载的文档，重写此方法在派生类中的，并返回唯一的文档标识符。

`GetDocumentName` 保存所有打开的文档的状态时，是由框架调用。 返回的字符串写入到注册表。

文档名称时该框架还原状态时更高版本，是从注册表中读取并传递给[CMDIFrameWndEx::CreateDocumentWindow](../../mfc/reference/cmdiframewndex-class.md#createdocumentwindow)。 重写此方法中的[CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)-派生的类和创建或打开具有此名称的文档并具有此名称在文件中读取。 如果文档不基于的文件，创建文档标识符本身所基于的文档。 仅当你想要保存和还原文档，您应执行上述操作。

### <a name="example"></a>示例

下面的示例演示 `GetDocumentName` 方法的用法。 此代码片段来自[VisualStudioDemo 示例： MFC Visual Studio 应用程序](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#17](../../mfc/codesnippet/cpp/cmdichildwndex-class_2.cpp)]

##  <a name="getframeicon"></a>  CMDIChildWndEx::GetFrameIcon

由框架调用以检索 MDI 子窗口的图标。

```
virtual HICON GetFrameIcon() const;
```

### <a name="return-value"></a>返回值

为窗口图标的句柄。

### <a name="remarks"></a>备注

由框架来确定包含 MDI 子框架窗口的 MDI 选项卡上显示哪些图标调用此方法。

默认情况下此方法返回的窗口图标。 重写`GetFrameIcon`在`CMDIChildWndEx`的派生类，以自定义此行为。

##  <a name="getframetext"></a>  CMDIChildWndEx::GetFrameText

由框架调用以检索 MDI 子窗口的文本。

```
virtual CString GetFrameText() const;
```

### <a name="return-value"></a>返回值

一个字符串，包含框架窗口文本。

### <a name="remarks"></a>备注

框架可以确定要包含 MDI 子框架窗口的 MDI 选项卡上显示哪些文本通过调用此方法。

默认情况下此方法返回窗口文本。 重写`GetFrameText`在`CMDIChildWndEx`的派生类，以自定义此行为。

##  <a name="getpane"></a>  CMDIChildWndEx::GetPane

查找窗格由指定的控件 id。

```
CBasePane* GetPane(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
[in]要查找窗格的控件 ID。

### <a name="return-value"></a>返回值

到窗格中，如果找到，否则为 NULL 指针。

##  <a name="getrelatedtabgroup"></a>  CMDIChildWndEx::GetRelatedTabGroup

```
CMFCTabCtrl* GetRelatedTabGroup();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="gettabbedpane"></a>  CMDIChildWndEx::GetTabbedPane

返回指向停靠的窗格中，属于一组的 MDI 选项卡式文档。

```
CDockablePane* GetTabbedPane() const;
```

### <a name="return-value"></a>返回值

指向停靠的窗格中，属于一组的 MDI 选项卡式文档。

##  <a name="gettoolbarbuttontooltiptext"></a>  CMDIChildWndEx::GetToolbarButtonToolTipText

由框架调用以检索工具栏按钮的工具提示。

```
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton*,
    CString&);
```

### <a name="return-value"></a>返回值

如果显示工具提示，则为 TRUE。 默认实现将返回 FALSE。

### <a name="remarks"></a>备注

如果你想要显示的工具栏按钮的自定义工具提示，重写此方法。

##  <a name="insertpane"></a>  CMDIChildWndEx::InsertPane

注册到停靠管理器指定窗格。

```
BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter = TRUE);
```

### <a name="parameters"></a>参数

*pControlBar*<br/>
[in]指向要插入的窗格的指针。

*pTarget*<br/>
[in]指向在相邻窗格的指针。

*bAfter*<br/>
[in]如果为 TRUE， *pControlBar*之后插入*pTarget*。 如果为 FALSE， *pControlBar*之前插入*pTarget*。

### <a name="return-value"></a>返回值

如果该方法成功，则 FALSE 否则，则为 TRUE。

##  <a name="ispointneardocksite"></a>  CMDIChildWndEx::IsPointNearDockSite

确定指定的点是否在停靠站点附近。

```
BOOL IsPointNearDockSite(
    CPoint point,
    DWORD& dwBarAlignment,
    BOOL& bOuterEdge) const;
```

### <a name="parameters"></a>参数

*点*<br/>
[in]指定的点。

*dwBarAlignment*<br/>
[in]指定的点是附近的边缘。 可能的值为 CBRS_ALIGN_LEFT、 CBRS_ALIGN_RIGHT、 CBRS_ALIGN_TOP 和 CBRS_ALIGN_BOTTOM

*bOuterEdge*<br/>
[in]在点附近的外边框的停靠站点中; 如果为 TRUEFALSE 否则为。

### <a name="return-value"></a>返回值

在点附近停靠站点中; 如果为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

在到停靠管理器中设置的敏感度内时，关键是附近停靠站点。 默认敏感度为 15 像素。

##  <a name="isreadonly"></a>  CMDIChildWndEx::IsReadOnly

指定子窗口中显示的文档是只读的。

```
virtual BOOL IsReadOnly();
```

### <a name="return-value"></a>返回值

如果文档是只读的; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

使用此函数以防止保存的只读的文档。

### <a name="example"></a>示例

下面的示例演示如何重写`IsReadOnly`方法。 此代码片段来自[VisualStudioDemo 示例： MFC Visual Studio 应用程序](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#2](../../mfc/codesnippet/cpp/cmdichildwndex-class_3.cpp)]

##  <a name="istabbedpane"></a>  CMDIChildWndEx::IsTabbedPane

指定 MDI 子窗口是否包含停靠窗格。

```
BOOL IsTabbedPane() const;
```

### <a name="return-value"></a>返回值

如果 MDI 子窗口包含停靠的窗格中的已转换为选项卡式文档，则为 TRUE否则为 FALSE。

##  <a name="onmoveminiframe"></a>  CMDIChildWndEx::OnMoveMiniFrame

由框架调用以移动微型框架窗口。

```
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```

### <a name="parameters"></a>参数

*pFrame*<br/>
[in]指向微型框架窗口的指针。

### <a name="return-value"></a>返回值

如果该方法成功，否则为 FALSE，则为 TRUE。

##  <a name="onsetpreviewmode"></a>  CMDIChildWndEx::OnSetPreviewMode

由框架调用以进入或退出打印预览模式。

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>参数

*bPreview*<br/>
[in]如果为 TRUE，则输入打印预览模式。 如果为 FALSE，则退出打印预览模式。

*pState*<br/>
[in]指向打印预览状态结构的指针。

##  <a name="onupdateframetitle"></a>  CMDIChildWndEx::OnUpdateFrameTitle

由框架调用以更新框架标题。

```
virtual void OnUpdateFrameTitle(BOOL bAddToTitle);
```

### <a name="parameters"></a>参数

*bAddToTitle*<br/>
[in]如果为 TRUE，则为标题添加文档名称。

##  <a name="panefrompoint"></a>  CMDIChildWndEx::PaneFromPoint

返回包含给定的点的窗格。

```
CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    bool bExactBar,
    CRuntimeClass* pRTCBarType) const;

CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    DWORD& dwAlignment,
    CRuntimeClass* pRTCBarType) const;
```

### <a name="parameters"></a>参数

*点*<br/>
[in]指定以屏幕坐标，以检查点。

*nSensitivity*<br/>
[in]搜索区域增加此数量。 如果给的定点落在更高的区域中，一个窗格，满足搜索条件。

*bExactBar*<br/>
[in]为 true，则忽略*nSensitivity*参数; 否则为 FALSE。

*pRTCBarType*<br/>
[in]如果不为 NULL，则方法会搜索仅指定类型的窗格。

*dwAlignment*<br/>
[in]如果指定点处找到一个窗格，则此参数将包含已接近指定点在窗格一侧。 有关详细信息，请参阅“备注”部分。

### <a name="return-value"></a>返回值

一个指向`CBasePane`-派生的对象，包含给定的时间，则为 NULL，如果不找到任何窗格。

### <a name="remarks"></a>备注

调用此方法以确定一个窗格中是否包含指定的条件，如运行时类和可见性根据指定的点。

该函数将返回并找到一个窗格时, *dwAlignment*包含指定点的对齐方式。 例如，如果点为最接近的窗格中，顶部*dwAlignment*设置为 CBRS_ALIGN_TOP。

##  <a name="recalclayout"></a>  CMDIChildWndEx::RecalcLayout

重新计算窗口的布局。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>参数

*bNotify*<br/>
[in]如果为 TRUE，在窗口的活动的就地项将接收此布局更改的通知。

##  <a name="removepanefromdockmanager"></a>  CMDIChildWndEx::RemovePaneFromDockManager

从到停靠管理器中删除一个窗格。

```
void RemovePaneFromDockManager(
    CBasePane* pControlBar,
    BOOL bDestroy,
    BOOL bAdjustLayout,
    BOOL bAutoHide,
    CBasePane* pBarReplacement);
```

### <a name="parameters"></a>参数

*pControlBar*<br/>
[in]指向要删除的窗格的指针。

*bDestroy*<br/>
[in]如果为 TRUE，将销毁已删除的窗格。

*bAdjustLayout*<br/>
[in]如果为 TRUE，则立即调整停靠布局。

*bAutoHide*<br/>
[in]如果为 TRUE，则停靠布局与自动隐藏栏列表。 如果为 FALSE，停靠布局与的正则窗格的列表。

*pBarReplacement*<br/>
[in]指向一个窗格，它将替换已删除的窗格的指针。

##  <a name="setrelatedtabgroup"></a>  CMDIChildWndEx::SetRelatedTabGroup

```
void SetRelatedTabGroup(CMFCTabCtrl* p);
```

### <a name="parameters"></a>参数

[in]*p*<br/>

### <a name="remarks"></a>备注

##  <a name="showpane"></a>  CMDIChildWndEx::ShowPane

```
void ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>参数

[in]*pBar*<br/>

[in]*bShow*<br/>

[in]*bDelay*<br/>

[in]*bActivate*<br/>

### <a name="remarks"></a>备注

##  <a name="updatetaskbartabicon"></a>  CMDIChildWndEx::UpdateTaskbarTabIcon

更新 Windows 7 任务栏选项卡图标。

```
virtual void UpdateTaskbarTabIcon(HICON hIcon);
```

### <a name="parameters"></a>参数

*hIcon*<br/>
若要在 Windows 7 任务栏选项卡上显示的图标句柄。

### <a name="remarks"></a>备注

##  <a name="unregistertaskbartab"></a>  CMDIChildWndEx::UnregisterTaskbarTab

从 Windows 7 任务栏选项卡中删除 MDI 子窗体。

```
void UnregisterTaskbarTab(BOOL bCheckRegisteredMDIChildCount = TRUE);
```

### <a name="parameters"></a>参数

*bCheckRegisteredMDIChildCount*<br/>
指定此函数是否需要检查的 MDI 选项卡中注册的 MDI 子级的个数。 如果此数字为 0，则此函数将删除的剪辑矩形从应用程序的任务栏缩略图。

### <a name="remarks"></a>备注

##  <a name="settaskbarthumbnailcliprect"></a>  CMDIChildWndEx::SetTaskbarThumbnailClipRect

由框架调用以设置剪辑矩形来选择窗口的工作区将显示为该窗口在任务栏中的缩略图的一部分。

```
virtual BOOL SetTaskbarThumbnailClipRect(CRect rect);
```

### <a name="parameters"></a>参数

*rect*<br/>
指定新的剪辑矩形。 如果矩形为空或 null，则会删除剪辑。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="settaskbartabproperties"></a>  CMDIChildWndEx::SetTaskbarTabProperties

设置 Windows 7 任务栏选项卡的属性。

```
void SetTaskbarTabProperties(DWORD dwFlags);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
STPFLAG 值的组合。 有关详细信息，请参阅[itaskbarlist4::settabproperties](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-itaskbarlist4-settabproperties)。

### <a name="remarks"></a>备注

##  <a name="settaskbartaborder"></a>  CMDIChildWndEx::SetTaskbarTabOrder

将插入 MDI 子窗体之前在 Windows 7 任务栏选项卡上指定的窗口。

```
void SetTaskbarTabOrder(CMDIChildWndEx* pWndBefore = NULL);
```

### <a name="parameters"></a>参数

*pWndBefore*<br/>
指向其缩略图插入到左侧的 MDI 子窗口的指针。 此窗口必须已注册通过`RegisterTaskbarTab`。 如果此值为 NULL，新的缩略图添加到列表的末尾。

### <a name="remarks"></a>备注

##  <a name="settaskbartabactive"></a>  CMDIChildWndEx::SetTaskbarTabActive

激活相应的 Windows 7 任务栏选项卡。

```
void SetTaskbarTabActive();
```

### <a name="remarks"></a>备注

##  <a name="registertaskbartab"></a>  CMDIChildWndEx::RegisterTaskbarTab

注册 Windows 7 任务栏选项卡的 MDI 子窗体。

```
virtual void RegisterTaskbarTab(CMDIChildWndEx* pWndBefore = NULL);
```

### <a name="parameters"></a>参数

*pWndBefore*<br/>
指向其缩略图插入到左侧的 MDI 子窗口的指针。 此窗口必须已注册通过`RegisterTaskbarTab`。 如果此值为 NULL，新的缩略图添加到列表的末尾。

### <a name="remarks"></a>备注

##  <a name="ontaskbartabthumbnailstretch"></a>  CMDIChildWndEx::OnTaskbarTabThumbnailStretch

需要拉伸的 MDI 子窗体的 Windows 7 任务栏选项卡缩略图预览的位图时由框架调用。

```
virtual BOOL OnTaskbarTabThumbnailStretch(
    HBITMAP hBmpDst,
    const CRect& rectDst,
    HBITMAP hBmpSrc,
    const CRect& rectSrc);
```

### <a name="parameters"></a>参数

*hBmpDst*<br/>
目标位图句柄。

*rectDst*<br/>
指定目标矩形。

*hBmpSrc*<br/>
源位图句柄。

*rectSrc*<br/>
指定源矩形。

### <a name="remarks"></a>备注

要求： afxmdichildwndex.h

##  <a name="ontaskbartabthumbnailmouseactivate"></a>  CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate

当任务栏选项卡缩略图应处理 WM_MOUSEACTIVATE 消息时由框架调用。

```
virtual int OnTaskbarTabThumbnailMouseActivate(
    CWnd* pDesktopWnd,
    UINT nHitTest,
    UINT message);
```

### <a name="parameters"></a>参数

*pDesktopWnd*<br/>
指定指向要激活的窗口的顶级父窗口的指针。 指针可能是暂时的不应存储。

*nHitTest*<br/>
指定命中测试区域代码。 命中的测试是一个测试，以便确定光标的位置。

*message*<br/>
指定鼠标消息号。

### <a name="remarks"></a>备注

默认实现将激活相关的 MDI 子框架。

##  <a name="ontaskbartabthumbnailactivate"></a>  CMDIChildWndEx::OnTaskbarTabThumbnailActivate

当任务栏选项卡缩略图应处理 WM_ACTIVATE 消息时由框架调用。

```
virtual void OnTaskbarTabThumbnailActivate(
    UINT nState,
    CWnd* pWndOther,
    BOOL bMinimized);
```

### <a name="parameters"></a>参数

*nState*<br/>
指定是否`CWnd`正在激活或停用。

*pWndOther*<br/>
指向`CWnd`正在激活或停用。 指针可以为 NULL，而且可能是临时。

*bMinimized*<br/>
指定的最小化的状态`CWnd`正在激活或停用。 值为 TRUE 指示窗口已最小化。

### <a name="remarks"></a>备注

默认实现将激活相关的 MDI 子框架。

##  <a name="onpresstaskbarthmbnailclosebutton"></a>  CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton

在用户按任务栏选项卡缩略图上的关闭按钮时由框架调用。

```
virtual void OnPressTaskbarThmbnailCloseButton();
```

### <a name="remarks"></a>备注

##  <a name="ongeticonicthumbnail"></a>  CMDIChildWndEx::OnGetIconicThumbnail

需要获取 MDI 子窗体的图标缩略图的位图时由框架调用。

```
virtual HBITMAP OnGetIconicThumbnail(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>参数

*nWidth*<br/>
指定所需位图的宽度。

*nHeight*<br/>
指定所需的位图的高度。

### <a name="remarks"></a>备注

##  <a name="ongeticoniclivepreviewbitmap"></a>  CMDIChildWndEx::OnGetIconicLivePreviewBitmap

需要获取的 MDI 子窗体的实时预览的位图时由框架调用。

```
virtual HBITMAP OnGetIconicLivePreviewBitmap(
    BOOL bIsMDIChildActive,
    CPoint& ptLocation);
```

### <a name="parameters"></a>参数

*bIsMDIChildActive*<br/>
如果位图的请求的当前处于活动状态的 MDI 子级以及主窗口没有最小化，则此参数为 TRUE。 在这种情况下处理的默认采用主窗口的快照。

*ptLocation*<br/>
在 main （最高级别） 中指定位图的位置窗口工作区坐标。 此时应由被调用方提供。

### <a name="return-value"></a>返回值

如果处理，则返回一个句柄对有效 32bpp 的位图，否则为空。

### <a name="remarks"></a>备注

重写此方法在派生类中的，返回的 MDI 子窗体的实时预览的有效 32bpp 位图。 仅当在 Windows 7 任务栏选项卡上显示 MDI 子窗体，调用此方法。 如果返回 NULL，MFC 调用默认处理程序，并获取使用位图`PrintClient`或`PrintWindow`。

##  <a name="m_dwdefaulttaskbartabpropertyflags"></a>  CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags

传递到框架的标志组合`SetTaskbarTabProperties`方法，选项卡 （MDI 子级） 被注册到 Windows 7 任务栏选项卡。

```
AFX_IMPORT_DATA static DWORD m_dwDefaultTaskbarTabPropertyFlags;
```

### <a name="remarks"></a>备注

默认值组合是 STPF_USEAPPTHUMBNAILWHENACTIVE &#124; STPF_USEAPPPEEKWHENACTIVE。

##  <a name="istaskbarthumbnailcliprectenabled"></a>  CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled

指示是否启用或禁用自动选择窗口的客户端区域将显示为该窗口在任务栏中的缩略图的一部分。

```
BOOL IsTaskbarThumbnailClipRectEnabled() const;
```

### <a name="return-value"></a>返回值

启用返回 TRUE，如果自动选择要显示的窗口的客户端区域的一部分;否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="istaskbartabssupportenabled"></a>  CMDIChildWndEx::IsTaskbarTabsSupportEnabled

指示是否可在 Windows 7 任务栏选项卡上显示 MDI 子窗体。

```
BOOL IsTaskbarTabsSupportEnabled();
```

### <a name="return-value"></a>返回值

如果在 Windows 7 任务栏选项卡; 上可以出现在 MDI 子窗体，则返回 TRUE如果不能在 Windows 7 任务栏选项卡上显示 MDI 子窗体，则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="isregisteredwithtaskbartabs"></a>  CMDIChildWndEx::IsRegisteredWithTaskbarTabs

如果 MDI 子窗体已成功注册到 Windows 7 任务栏选项卡，则返回 TRUE。

```
BOOL IsRegisteredWithTaskbarTabs();
```

### <a name="return-value"></a>返回值

MDI 子窗体是否已注册 Windows 7 任务栏选项卡; 如果为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="invalidateiconicbitmaps"></a>  CMDIChildWndEx::InvalidateIconicBitmaps

使无效 MDI 子窗体的图标位图表示的形式。

```
BOOL InvalidateIconicBitmaps();
```

### <a name="return-value"></a>返回值

如果禁用了 Windows 7 任务栏支持 FALSE 返回或 MDI 子窗体未注册到 Windows 7 任务栏选项卡;否则，则返回 TRUE。

### <a name="remarks"></a>备注

实时内容或 MDI 子窗体的大小已更改时，应调用。

##  <a name="gettaskbarthumbnailcliprect"></a>  CMDIChildWndEx::GetTaskbarThumbnailClipRect

需要选择窗口的工作区将显示为该窗口在任务栏中的缩略图的一部分时，由框架调用。

```
virtual CRect GetTaskbarThumbnailClipRect() const;
```

### <a name="return-value"></a>返回值

Windows 坐标中的矩形。 此矩形映射到最高级别框架的客户端区域中。 矩形应为空，若要清除的剪辑矩形。

### <a name="remarks"></a>备注

##  <a name="gettaskbarpreviewwnd"></a>  CMDIChildWndEx::GetTaskbarPreviewWnd

需要获取要在 Windows 7 任务栏选项卡缩略图上显示的子窗口 （通常是一个视图或拆分器窗口） 时由框架调用。

```
virtual CWnd* GetTaskbarPreviewWnd();
```

### <a name="return-value"></a>返回值

应返回到的有效指针`CWnd`与此 MDI 子窗体相关的对象，应在 Windows 7 任务栏选项卡上显示的预览。 默认实现将返回此 MDI 子窗体 AFX_IDW_PANE_FIRST 控件 id 的子窗口 (通常是`CView`的派生类)。

### <a name="remarks"></a>备注

##  <a name="gettabproxywnd"></a>  CMDIChildWndEx::GetTabProxyWnd

返回注册到 Windows 7 任务栏选项卡的选项卡代理窗口。

```
CMDITabProxyWnd* GetTabProxyWnd();
```

### <a name="return-value"></a>返回值

一个指向`CMDITabProxyWnd`对象，它注册到 Windows 7 任务栏选项卡。

### <a name="remarks"></a>备注

##  <a name="enabletaskbarthumbnailcliprect"></a>  CMDIChildWndEx::EnableTaskbarThumbnailClipRect

启用或禁用自动选择窗口的客户端区域将显示为该窗口在任务栏中的缩略图的一部分。

```
void EnableTaskbarThumbnailClipRect(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
指定是否启用 (TRUE)，或禁用 (FALSE) 自动选择要显示的窗口的客户端区域的一部分。

### <a name="remarks"></a>备注

##  <a name="canshowontaskbartabs"></a>  CMDIChildWndEx::CanShowOnTaskBarTabs

指示是否可以在 Windows 7 任务栏选项卡上显示此 MDI 子窗体的框架。

```
virtual BOOL CanShowOnTaskBarTabs();
```

### <a name="return-value"></a>返回值

如果可以在 Windows 7 任务栏缩略图上显示 MDI 子窗体的内容，则为 TRUE。

### <a name="remarks"></a>备注

重写此方法在派生类中的，并返回 FALSE 来禁用此 MDI 子窗体在 Windows 7 任务栏选项卡上的外观。

##  <a name="activatetoplevelframe"></a>  CMDIChildWndEx::ActivateTopLevelFrame

由框架调用以从任务栏选项卡激活应用程序时激活的最高级别框架。

```
virtual void ActivateTopLevelFrame();
```

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CMFCWindowsManagerDialog 类](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)<br/>
[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)
