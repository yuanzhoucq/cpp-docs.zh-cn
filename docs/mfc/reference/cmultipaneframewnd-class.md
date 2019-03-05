---
title: CMultiPaneFrameWnd 类
ms.date: 11/04/2016
f1_keywords:
- CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddRecentPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustPaneFrames
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CalcExpectedDockedRect
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeAttached
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeDockedToPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CheckGripperVisibility
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CloseMiniFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ConvertToTabbedDocument
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockRecentPaneToMainFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetCaptionText
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneContainerManager
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetFirstVisiblePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetVisiblePaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::InsertPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::LoadState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnDockToRecentPos
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnKillRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnPaneRecalcLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnSetRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnShowPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::PaneFromPoint
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemoveNonValidPanes
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemovePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ReplacePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SaveState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::Serialize
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetLastFocusedPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetPreDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentDockSiteInfo
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentTabRelatedInfo
helpviewer_keywords:
- CMultiPaneFrameWnd [MFC], AddPane
- CMultiPaneFrameWnd [MFC], AddRecentPane
- CMultiPaneFrameWnd [MFC], AdjustLayout
- CMultiPaneFrameWnd [MFC], AdjustPaneFrames
- CMultiPaneFrameWnd [MFC], CalcExpectedDockedRect
- CMultiPaneFrameWnd [MFC], CanBeAttached
- CMultiPaneFrameWnd [MFC], CanBeDockedToPane
- CMultiPaneFrameWnd [MFC], CheckGripperVisibility
- CMultiPaneFrameWnd [MFC], CloseMiniFrame
- CMultiPaneFrameWnd [MFC], ConvertToTabbedDocument
- CMultiPaneFrameWnd [MFC], DockFrame
- CMultiPaneFrameWnd [MFC], DockPane
- CMultiPaneFrameWnd [MFC], DockRecentPaneToMainFrame
- CMultiPaneFrameWnd [MFC], GetCaptionText
- CMultiPaneFrameWnd [MFC], GetPaneContainerManager
- CMultiPaneFrameWnd [MFC], GetFirstVisiblePane
- CMultiPaneFrameWnd [MFC], GetPane
- CMultiPaneFrameWnd [MFC], GetPaneCount
- CMultiPaneFrameWnd [MFC], GetVisiblePaneCount
- CMultiPaneFrameWnd [MFC], InsertPane
- CMultiPaneFrameWnd [MFC], LoadState
- CMultiPaneFrameWnd [MFC], OnDockToRecentPos
- CMultiPaneFrameWnd [MFC], OnKillRollUpTimer
- CMultiPaneFrameWnd [MFC], OnPaneRecalcLayout
- CMultiPaneFrameWnd [MFC], OnSetRollUpTimer
- CMultiPaneFrameWnd [MFC], OnShowPane
- CMultiPaneFrameWnd [MFC], PaneFromPoint
- CMultiPaneFrameWnd [MFC], RemoveNonValidPanes
- CMultiPaneFrameWnd [MFC], RemovePane
- CMultiPaneFrameWnd [MFC], ReplacePane
- CMultiPaneFrameWnd [MFC], SaveState
- CMultiPaneFrameWnd [MFC], Serialize
- CMultiPaneFrameWnd [MFC], SetDockState
- CMultiPaneFrameWnd [MFC], SetLastFocusedPane
- CMultiPaneFrameWnd [MFC], SetPreDockState
- CMultiPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CMultiPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
ms.assetid: 989a548e-0d70-46b7-a513-8cf740e1be3e
ms.openlocfilehash: bb420021ec5b9839091c42b5eae6e1d5b9f7f977
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281234"
---
# <a name="cmultipaneframewnd-class"></a>CMultiPaneFrameWnd 类

`CMultiPaneFrameWnd`类用于扩展[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)。 它可支持多个窗格。 而不是控件条的单个嵌入句柄`CMultiPaneFrameWnd`包含[CPaneContainerManager 类](../../mfc/reference/cpanecontainermanager-class.md)对象，它使用户能够将一个停靠`CMultiPaneFrameWnd`到另一个并动态创建多个浮动、 选项卡式windows。

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

## <a name="syntax"></a>语法

```
class CMultiPaneFrameWnd : public CPaneFrameWnd
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMultiPaneFrameWnd::AddPane](#addpane)|添加窗格。 (重写[CPaneFrameWnd::AddPane](../../mfc/reference/cpaneframewnd-class.md#addpane)。)|
|[CMultiPaneFrameWnd::AddRecentPane](#addrecentpane)||
|[CMultiPaneFrameWnd::AdjustLayout](#adjustlayout)|调整微型框架窗口的布局。 (重写[CPaneFrameWnd::AdjustLayout](../../mfc/reference/cpaneframewnd-class.md#adjustlayout)。)|
|[CMultiPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)|(重写[CPaneFrameWnd::AdjustPaneFrames](../../mfc/reference/cpaneframewnd-class.md#adjustpaneframes)。)|
|[CMultiPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|计算停靠窗口的预期的矩形。 (重写[CPaneFrameWnd::CalcExpectedDockedRect](../../mfc/reference/cpaneframewnd-class.md#calcexpecteddockedrect)。)|
|[CMultiPaneFrameWnd::CanBeAttached](#canbeattached)|确定是否当前窗格可以停靠到另一个窗格或框架窗口。 (重写[CPaneFrameWnd::CanBeAttached](../../mfc/reference/cpaneframewnd-class.md#canbeattached)。)|
|[CMultiPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|确定微型框架窗口是否可以停靠窗格。 (重写[CPaneFrameWnd::CanBeDockedToPane](../../mfc/reference/cpaneframewnd-class.md#canbedockedtopane)。)|
|[CMultiPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)|(重写[CPaneFrameWnd::CheckGripperVisibility](../../mfc/reference/cpaneframewnd-class.md#checkgrippervisibility)。)|
|[CMultiPaneFrameWnd::CloseMiniFrame](#closeminiframe)|（重写 `CPaneFrameWnd::CloseMiniFrame`。）|
|[CMultiPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|将窗格转换为选项卡式文档。 (重写[CPaneFrameWnd::ConvertToTabbedDocument](../../mfc/reference/cpaneframewnd-class.md#converttotabbeddocument)。)|
|[CMultiPaneFrameWnd::DockFrame](#dockframe)||
|[CMultiPaneFrameWnd::DockPane](#dockpane)|停靠窗格。 (重写[CPaneFrameWnd::DockPane](../../mfc/reference/cpaneframewnd-class.md#dockpane)。)|
|[CMultiPaneFrameWnd::DockRecentPaneToMainFrame](#dockrecentpanetomainframe)||
|[CMultiPaneFrameWnd::GetCaptionText](#getcaptiontext)|返回标题文本。 (重写[CPaneFrameWnd::GetCaptionText](../../mfc/reference/cpaneframewnd-class.md#getcaptiontext)。)|
|[CMultiPaneFrameWnd::GetPaneContainerManager](#getpanecontainermanager)|返回对内部容器管理器对象的引用。|
|[CMultiPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|返回包含在微型框架窗口中的第一个可见窗格。 (重写[CPaneFrameWnd::GetFirstVisiblePane](../../mfc/reference/cpaneframewnd-class.md#getfirstvisiblepane)。)|
|[CMultiPaneFrameWnd::GetPane](#getpane)|返回包含在微型框架窗口中的窗格。 (重写[CPaneFrameWnd::GetPane](../../mfc/reference/cpaneframewnd-class.md#getpane)。)|
|[CMultiPaneFrameWnd::GetPaneCount](#getpanecount)|返回包含在微型框架窗口中的窗格数。 (重写[CPaneFrameWnd::GetPaneCount](../../mfc/reference/cpaneframewnd-class.md#getpanecount)。)|
|[CMultiPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|返回包含在微型框架窗口中的可见窗格数。 (重写[CPaneFrameWnd::GetVisiblePaneCount](../../mfc/reference/cpaneframewnd-class.md#getvisiblepanecount)。)|
|[CMultiPaneFrameWnd::InsertPane](#insertpane)||
|[CMultiPaneFrameWnd::LoadState](#loadstate)|从注册表加载窗格的状态。 (重写[CPaneFrameWnd::LoadState](../../mfc/reference/cpaneframewnd-class.md#loadstate)。)|
|[CMultiPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|将微型框架窗口停靠在其最新的位置。 (重写[CPaneFrameWnd::OnDockToRecentPos](../../mfc/reference/cpaneframewnd-class.md#ondocktorecentpos)。)|
|[CMultiPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|停止汇总计时器。 (重写[CPaneFrameWnd::OnKillRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onkillrolluptimer)。)|
|[CMultiPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|调整微型框架窗口中窗格的布局。 (重写[CPaneFrameWnd::OnPaneRecalcLayout](../../mfc/reference/cpaneframewnd-class.md#onpanerecalclayout)。)|
|[CMultiPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|设置汇总计时器。 (重写[CPaneFrameWnd::OnSetRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onsetrolluptimer)。)|
|[CMultiPaneFrameWnd::OnShowPane](#onshowpane)|隐藏或显示微型框架窗口的窗格时，由框架进行调用。 (重写[CPaneFrameWnd::OnShowPane](../../mfc/reference/cpaneframewnd-class.md#onshowpane)。)|
|[CMultiPaneFrameWnd::PaneFromPoint](#panefrompoint)|如果窗格在微型框架窗口内包含用户提供的点，则返回窗格。 (重写[CPaneFrameWnd::PaneFromPoint](../../mfc/reference/cpaneframewnd-class.md#panefrompoint)。)|
|[CMultiPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|由框架调用以删除非有效窗格。 (重写[CPaneFrameWnd::RemoveNonValidPanes](../../mfc/reference/cpaneframewnd-class.md#removenonvalidpanes)。)|
|[CMultiPaneFrameWnd::RemovePane](#removepane)|从微型框架窗口删除窗格。 (重写[CPaneFrameWnd::RemovePane](../../mfc/reference/cpaneframewnd-class.md#removepane)。)|
|[CMultiPaneFrameWnd::ReplacePane](#replacepane)|用一个窗格替换另一个窗格。 (重写[CPaneFrameWnd::ReplacePane](../../mfc/reference/cpaneframewnd-class.md#replacepane)。)|
|[CMultiPaneFrameWnd::SaveState](#savestate)|将窗格的状态保存到注册表。 (重写[CPaneFrameWnd::SaveState](../../mfc/reference/cpaneframewnd-class.md#savestate)。)|
|[CMultiPaneFrameWnd::Serialize](#serialize)|（重写 `CPaneFrameWnd::Serialize`。）|
|[CMultiPaneFrameWnd::SetDockState](#setdockstate)|设置停靠状态。 (重写[CPaneFrameWnd::SetDockState](../../mfc/reference/cpaneframewnd-class.md#setdockstate)。)|
|[CMultiPaneFrameWnd::SetLastFocusedPane](#setlastfocusedpane)||
|[CMultiPaneFrameWnd::SetPreDockState](#setpredockstate)|设置预停靠状态。 (重写[CPaneFrameWnd::SetPreDockState](../../mfc/reference/cpaneframewnd-class.md#setpredockstate)。)|
|[CMultiPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)|(重写[CPaneFrameWnd::StoreRecentDockSiteInfo](../../mfc/reference/cpaneframewnd-class.md#storerecentdocksiteinfo)。)|
|[CMultiPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)|(重写[CPaneFrameWnd::StoreRecentTabRelatedInfo](../../mfc/reference/cpaneframewnd-class.md#storerecenttabrelatedinfo)。)|

## <a name="remarks"></a>备注

大多数此类中的方法中重写方法[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)类。

如果窗格使用 AFX_CBRS_AUTO_ROLLUP 样式，并且用户将该窗格停靠到窗格中多框架窗口，用户可以汇总而不考虑其他停靠窗格的样式设置窗口。

框架会自动创建`CMultiPaneFrameWnd`时用户中时浮动窗格使用 CBRS_FLOAT_MULTI 样式的对象。

有关派生的类从信息`CPaneFrameWnd`类，并动态创建，请参见[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)。

## <a name="example"></a>示例

下面的示例演示如何检索一个指向`CMultiPaneFrameWnd`对象。 此代码片段属于[设置窗格大小示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_SetPaneSize#4](../../mfc/reference/codesnippet/cpp/cmultipaneframewnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)

[CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)

## <a name="requirements"></a>要求

**标头：** afxMultiPaneFrameWnd.h

##  <a name="addpane"></a>  CMultiPaneFrameWnd::AddPane

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>参数

[in] *pWnd*<br/>

### <a name="remarks"></a>备注

##  <a name="addrecentpane"></a>  CMultiPaneFrameWnd::AddRecentPane

```
virtual BOOL AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>参数

[in] *pBar*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="adjustlayout"></a>  CMultiPaneFrameWnd::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>备注

##  <a name="adjustpaneframes"></a>  CMultiPaneFrameWnd::AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>备注

##  <a name="calcexpecteddockedrect"></a>  CMultiPaneFrameWnd::CalcExpectedDockedRect

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>参数

[in] *pWndToDock*<br/>
[in] *ptMouse*<br/>
[in] *rectResult*<br/>
[in] *bDrawTab*<br/>
[in] *ppTargetBar*<br/>

### <a name="remarks"></a>备注

##  <a name="canbeattached"></a>  CMultiPaneFrameWnd::CanBeAttached

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="canbedockedtopane"></a>  CMultiPaneFrameWnd::CanBeDockedToPane

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>参数

[in] *pDockingBar*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="checkgrippervisibility"></a>  CMultiPaneFrameWnd::CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>备注

##  <a name="closeminiframe"></a>  CMultiPaneFrameWnd::CloseMiniFrame

```
virtual void CloseMiniFrame();
```

### <a name="remarks"></a>备注

##  <a name="converttotabbeddocument"></a>  CMultiPaneFrameWnd::ConvertToTabbedDocument

```
virtual void ConvertToTabbedDocument();
```

### <a name="remarks"></a>备注

##  <a name="dockframe"></a>  CMultiPaneFrameWnd::DockFrame

```
virtual BOOL DockFrame(
    CPaneFrameWnd* pDockedFrame,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>参数

[in] *pDockedFrame*<br/>
[in]*dockMethod*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="dockpane"></a>  CMultiPaneFrameWnd::DockPane

```
virtual BOOL DockPane(CDockablePane* pDockedBar);
```

### <a name="parameters"></a>参数

[in] *pDockedBar*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="dockrecentpanetomainframe"></a>  CMultiPaneFrameWnd::DockRecentPaneToMainFrame

```
virtual void DockRecentPaneToMainFrame(CDockablePane* pBar);
```

### <a name="parameters"></a>参数

[in] *pBar*<br/>

### <a name="remarks"></a>备注

##  <a name="getcaptiontext"></a>  CMultiPaneFrameWnd::GetCaptionText

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getfirstvisiblepane"></a>  CMultiPaneFrameWnd::GetFirstVisiblePane

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getpane"></a>  CMultiPaneFrameWnd::GetPane

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getpanecontainermanager"></a>  CMultiPaneFrameWnd::GetPaneContainerManager

返回对内部容器管理器对象的引用。

```
CPaneContainerManager& GetPaneContainerManager();
```

### <a name="return-value"></a>返回值

对内部容器管理器对象的引用。

### <a name="remarks"></a>备注

此方法可用于访问内部[CPaneContainerManager 类](../../mfc/reference/cpanecontainermanager-class.md)对象。

##  <a name="getpanecount"></a>  CMultiPaneFrameWnd::GetPaneCount

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getvisiblepanecount"></a>  CMultiPaneFrameWnd::GetVisiblePaneCount

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="insertpane"></a>  CMultiPaneFrameWnd::InsertPane

```
virtual BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter);
```

### <a name="parameters"></a>参数

[in] *pControlBar*<br/>
[in] *pTarget*<br/>
[in] *bAfter*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="loadstate"></a>  CMultiPaneFrameWnd::LoadState

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

[in] *lpszProfileName*<br/>
[in] *uiID*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ondocktorecentpos"></a>  CMultiPaneFrameWnd::OnDockToRecentPos

```
virtual void OnDockToRecentPos();
```

### <a name="remarks"></a>备注

##  <a name="onkillrolluptimer"></a>  CMultiPaneFrameWnd::OnKillRollUpTimer

```
virtual void OnKillRollUpTimer();
```

### <a name="remarks"></a>备注

##  <a name="onpanerecalclayout"></a>  CMultiPaneFrameWnd::OnPaneRecalcLayout

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>备注

##  <a name="onsetrolluptimer"></a>  CMultiPaneFrameWnd::OnSetRollUpTimer

```
virtual void OnSetRollUpTimer();
```

### <a name="remarks"></a>备注

##  <a name="onshowpane"></a>  CMultiPaneFrameWnd::OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>参数

[in] *pBar*<br/>
[in] *bShow*<br/>

### <a name="remarks"></a>备注

##  <a name="panefrompoint"></a>  CMultiPaneFrameWnd::PaneFromPoint

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>参数

[in] *point*<br/>
[in] *nSensitivity*<br/>
[in] *bCheckVisibility*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="removenonvalidpanes"></a>  CMultiPaneFrameWnd::RemoveNonValidPanes

```
virtual void RemoveNonValidPanes();
```

### <a name="remarks"></a>备注

##  <a name="removepane"></a>  CMultiPaneFrameWnd::RemovePane

```
virtual void RemovePane(
    CBasePane* pBar,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = TRUE);
```

### <a name="parameters"></a>参数

[in] *pBar*<br/>
[in] *bDestroy*<br/>
[in] *bNoDelayedDestroy*<br/>

### <a name="remarks"></a>备注

##  <a name="replacepane"></a>  CMultiPaneFrameWnd::ReplacePane

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>参数

[in] *pBarOrg*<br/>
[in] *pBarReplaceWith*<br/>

### <a name="remarks"></a>备注

##  <a name="savestate"></a>  CMultiPaneFrameWnd::SaveState

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

[in] *lpszProfileName*<br/>
[in] *uiID*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="serialize"></a>  CMultiPaneFrameWnd::Serialize

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

[in] *ar*<br/>

### <a name="remarks"></a>备注

##  <a name="setdockstate"></a>  CMultiPaneFrameWnd::SetDockState

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>参数

[in] *pDockManager*<br/>

### <a name="remarks"></a>备注

##  <a name="setlastfocusedpane"></a>  CMultiPaneFrameWnd::SetLastFocusedPane

```
void SetLastFocusedPane(HWND hwnd);
```

### <a name="parameters"></a>参数

[in] *hwnd*<br/>

### <a name="remarks"></a>备注

##  <a name="setpredockstate"></a>  CMultiPaneFrameWnd::SetPreDockState

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>参数

[in] *preDockState*<br/>
[in] *pBarToDock*<br/>
[in]*dockMethod*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="storerecentdocksiteinfo"></a>  CMultiPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>参数

[in] *pBar*<br/>

### <a name="remarks"></a>备注

##  <a name="storerecenttabrelatedinfo"></a>  CMultiPaneFrameWnd::StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>参数

[in] *pDockingBar*<br/>
[in] *pTabbedBar*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)
