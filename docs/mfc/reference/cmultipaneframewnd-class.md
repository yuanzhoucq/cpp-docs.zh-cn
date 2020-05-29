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
ms.openlocfilehash: 047dd5ca2ca6705549e8f92de1550248e348ff52
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752789"
---
# <a name="cmultipaneframewnd-class"></a>CMultiPaneFrameWnd 类

该`CMultiPaneFrameWnd`类扩展[了 CPaneFramewnd 类](../../mfc/reference/cpaneframewnd-class.md)。 它可支持多个窗格。 包含一个[CPaneContainerManager Class](../../mfc/reference/cpanecontainermanager-class.md) `CMultiPaneFrameWnd`对象，该对象允许用户将一个句柄停靠到另一个`CMultiPaneFrameWnd`，并动态创建多个浮动的选项卡式窗口，而不是控件栏的单个嵌入句柄。

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMultiPaneFrameWnd : public CPaneFrameWnd
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C 多窗格框架：：添加窗格](#addpane)|添加窗格。 （覆盖[CPaneFramewnd：：添加窗格](../../mfc/reference/cpaneframewnd-class.md#addpane).）|
|[C 多窗格框架：：添加最新窗格](#addrecentpane)||
|[C 多窗格框架：：调整布局](#adjustlayout)|调整微型框架窗口的布局。 （覆盖[CPaneFramewnd：：调整布局](../../mfc/reference/cpaneframewnd-class.md#adjustlayout).）|
|[C 多窗格框架：：调整窗格框架](#adjustpaneframes)|（覆盖[CPaneFramewnd：调整窗格帧](../../mfc/reference/cpaneframewnd-class.md#adjustpaneframes)。|
|[C 多窗格框架：：钙化物多克](#calcexpecteddockedrect)|计算停靠窗口的预期矩形。 （覆盖[CPaneFramewnd：：Calc预期多克已重新](../../mfc/reference/cpaneframewnd-class.md#calcexpecteddockedrect)使用 .）|
|[C 多窗格框架：：可附加](#canbeattached)|确定当前窗格是否可以停靠到另一个窗格或框架窗口。 （覆盖[CPaneFramewnd：：可以附加](../../mfc/reference/cpaneframewnd-class.md#canbeattached).）|
|[C 多窗格框架：：可多克托帕](#canbedockedtopane)|确定微型框架窗口是否可以停靠到窗格。 （覆盖[CPaneframewnd：：可以装对窗格](../../mfc/reference/cpaneframewnd-class.md#canbedockedtopane).）|
|[C 多窗格框架：：检查夹持可见性](#checkgrippervisibility)|（覆盖[CPaneFramewnd：：检查夹持可见度](../../mfc/reference/cpaneframewnd-class.md#checkgrippervisibility).）|
|[C 多窗格框架：：关闭迷你框架](#closeminiframe)|（重写 `CPaneFrameWnd::CloseMiniFrame`。）|
|[C 多窗格框架：：转换到选项卡文档](#converttotabbeddocument)|将窗格转换为选项卡式文档。 （覆盖[CPaneframewnd：：转换到 Tabbed 文档](../../mfc/reference/cpaneframewnd-class.md#converttotabbeddocument).）|
|[C 多窗格框架：:DockFrame](#dockframe)||
|[C 多窗格框架：:Dockpane](#dockpane)|停靠窗格。 （覆盖[CPaneFramewnd：:Dockpane](../../mfc/reference/cpaneframewnd-class.md#dockpane).）|
|[C 多窗格框架：:D最近窗格到大型框架](#dockrecentpanetomainframe)||
|[C 多窗格框架：：获取字幕文本](#getcaptiontext)|返回标题文本。 （覆盖[CPaneFramewnd：获取字幕文本](../../mfc/reference/cpaneframewnd-class.md#getcaptiontext).）|
|[C 多窗格框架：：获取窗格容器管理器](#getpanecontainermanager)|返回对内部容器管理器对象的引用。|
|[C 多窗格框架：：获取第一个可见窗格](#getfirstvisiblepane)|返回包含在微型框架窗口中的第一个可见窗格。 （覆盖[CPaneFramewnd：获取第一个可见窗格](../../mfc/reference/cpaneframewnd-class.md#getfirstvisiblepane)。）|
|[C 多窗格框架：：获取窗格](#getpane)|返回包含在微型框架窗口中的窗格。 （覆盖[CPaneFramewnd：getPane](../../mfc/reference/cpaneframewnd-class.md#getpane).）|
|[C 多窗格框架：：获取窗格计数](#getpanecount)|返回包含在微型框架窗口中的窗格数。 （覆盖[CPaneFramewnd：获取窗格计数](../../mfc/reference/cpaneframewnd-class.md#getpanecount).）|
|[C 多窗格框架：：获取可见窗格计数](#getvisiblepanecount)|返回包含在微型框架窗口中的可见窗格数。 （覆盖[CPaneFramewnd：获取可见窗格计数](../../mfc/reference/cpaneframewnd-class.md#getvisiblepanecount)。|
|[C 多窗格框架：：插入窗格](#insertpane)||
|[C 多窗格框架：：加载状态](#loadstate)|从注册表加载窗格的状态。 （覆盖[CPaneFramewnd：：加载状态](../../mfc/reference/cpaneframewnd-class.md#loadstate).）|
|[C 多窗格框架：：在多克到最新Pos](#ondocktorecentpos)|将微型框架窗口停靠在其最新的位置。 （覆盖[CPaneframewnd：ondock 到最新Pos](../../mfc/reference/cpaneframewnd-class.md#ondocktorecentpos). ）|
|[C 多窗格框架：：在基基尔罗普普计时器上](#onkillrolluptimer)|停止汇总计时器。 （覆盖[CPaneframewnd：：在 KillrollupTimer](../../mfc/reference/cpaneframewnd-class.md#onkillrolluptimer)上。|
|[C 多窗格框架：：在窗格Recalc布局上](#onpanerecalclayout)|调整小型框架窗口中窗格的布局。 （覆盖[CPaneFramewnd：onPaneRecalclayout](../../mfc/reference/cpaneframewnd-class.md#onpanerecalclayout).）|
|[C 多窗格框架：：打开滚动计时器](#onsetrolluptimer)|设置汇总计时器。 （覆盖[CPaneframewnd：onSetrolluptimer](../../mfc/reference/cpaneframewnd-class.md#onsetrolluptimer).）|
|[C 多窗格框架：：在显示窗格上](#onshowpane)|隐藏或显示微型框架窗口的窗格时，由框架进行调用。 （覆盖[CPaneFramewnd：上显示窗格](../../mfc/reference/cpaneframewnd-class.md#onshowpane).）|
|[C 多窗格框架：:P从点](#panefrompoint)|如果窗格在微型框架窗口内包含用户提供的点，则返回窗格。 （覆盖[CPaneFramewnd：:P从点](../../mfc/reference/cpaneframewnd-class.md#panefrompoint). ）|
|[C 多窗格框架：：删除非有效窗格](#removenonvalidpanes)|由框架调用以删除非有效窗格。 （覆盖[CPaneFramewnd：：删除 NonValidPane.）](../../mfc/reference/cpaneframewnd-class.md#removenonvalidpanes)|
|[C 多窗格框架：：删除窗格](#removepane)|从微型框架窗口删除窗格。 （覆盖[CPaneFramewnd：：删除窗格](../../mfc/reference/cpaneframewnd-class.md#removepane).）|
|[C 多窗格框架：：替换窗格](#replacepane)|用一个窗格替换另一个窗格。 （覆盖[CPaneFramewnd：：替换窗格](../../mfc/reference/cpaneframewnd-class.md#replacepane).）|
|[C 多窗格框架：：保存状态](#savestate)|将窗格的状态保存到注册表。 （覆盖[CPaneFramewnd：：保存状态](../../mfc/reference/cpaneframewnd-class.md#savestate).）|
|[C 多窗格框架：：序列化](#serialize)|（重写 `CPaneFrameWnd::Serialize`。）|
|[C 多窗格框架：：SetDockstate](#setdockstate)|设置停靠状态。 （覆盖[CPaneFramewnd：setDockState](../../mfc/reference/cpaneframewnd-class.md#setdockstate).）|
|[C 多窗格框架：：设置最后聚焦窗格](#setlastfocusedpane)||
|[C 多窗格框架：：设置前坞州](#setpredockstate)|设置预停靠状态。 （覆盖[CPaneFramewnd：设置 PreDockState](../../mfc/reference/cpaneframewnd-class.md#setpredockstate).）|
|[C 多窗格框架：：存储最新网站信息](#storerecentdocksiteinfo)|（覆盖[CPaneFramewnd：：存储最近网站网站信息](../../mfc/reference/cpaneframewnd-class.md#storerecentdocksiteinfo).）|
|[C 多窗格框架：：存储最新标签相关信息](#storerecenttabrelatedinfo)|（覆盖[CPaneFramewnd：：存储最近标签相关信息](../../mfc/reference/cpaneframewnd-class.md#storerecenttabrelatedinfo).）|

## <a name="remarks"></a>备注

此类中的大多数方法重写[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)中的方法。

如果窗格使用AFX_CBRS_AUTO_ROLLUP样式，并且用户将该窗格停靠到多窗格框架窗口，则无论其他停靠窗格的样式设置如何，用户都可以向上滚动窗口。

当用户浮动使用CBRS_FLOAT_MULTI样式`CMultiPaneFrameWnd`的窗格时，框架会自动创建一个对象。

有关从`CPaneFrameWnd`类派生类并动态创建类的信息，请参阅[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)。

## <a name="example"></a>示例

下面的示例演示如何检索指向`CMultiPaneFrameWnd`对象的指针。 此代码段是["设置窗格大小"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_SetPaneSize#4](../../mfc/reference/codesnippet/cpp/cmultipaneframewnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)

[CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)

## <a name="requirements"></a>要求

**标题：** afx 多窗格框架.h

## <a name="cmultipaneframewndaddpane"></a><a name="addpane"></a>C 多窗格框架：：添加窗格

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>参数

[在]*pwnd*<br/>

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndaddrecentpane"></a><a name="addrecentpane"></a>C 多窗格框架：：添加最新窗格

```
virtual BOOL AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndadjustlayout"></a><a name="adjustlayout"></a>C 多窗格框架：：调整布局

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndadjustpaneframes"></a><a name="adjustpaneframes"></a>C 多窗格框架：：调整窗格框架

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndcalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>C 多窗格框架：：钙化物多克

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>参数

[在]*普恩德托多克*<br/>
[在]*ptMouse*<br/>
[在]*rectResult*<br/>
[在]*bDrawTab*<br/>
[在]*ppTargetBar*<br/>

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndcanbeattached"></a><a name="canbeattached"></a>C 多窗格框架：：可附加

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndcanbedockedtopane"></a><a name="canbedockedtopane"></a>C 多窗格框架：：可多克托帕

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>参数

[在]*pDockingBar*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndcheckgrippervisibility"></a><a name="checkgrippervisibility"></a>C 多窗格框架：：检查夹持可见性

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndcloseminiframe"></a><a name="closeminiframe"></a>C 多窗格框架：：关闭迷你框架

```
virtual void CloseMiniFrame();
```

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>C 多窗格框架：：转换到选项卡文档

```
virtual void ConvertToTabbedDocument();
```

### <a name="remarks"></a>备注

## <a name="cmultipaneframewnddockframe"></a><a name="dockframe"></a>C 多窗格框架：:DockFrame

```
virtual BOOL DockFrame(
    CPaneFrameWnd* pDockedFrame,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>参数

[在]*pDocked 框架*<br/>
[在]*基方法*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewnddockpane"></a><a name="dockpane"></a>C 多窗格框架：:Dockpane

```
virtual BOOL DockPane(CDockablePane* pDockedBar);
```

### <a name="parameters"></a>参数

[在]*pDockedBar*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewnddockrecentpanetomainframe"></a><a name="dockrecentpanetomainframe"></a>C 多窗格框架：:D最近窗格到大型框架

```
virtual void DockRecentPaneToMainFrame(CDockablePane* pBar);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndgetcaptiontext"></a><a name="getcaptiontext"></a>C 多窗格框架：：获取字幕文本

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndgetfirstvisiblepane"></a><a name="getfirstvisiblepane"></a>C 多窗格框架：：获取第一个可见窗格

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndgetpane"></a><a name="getpane"></a>C 多窗格框架：：获取窗格

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndgetpanecontainermanager"></a><a name="getpanecontainermanager"></a>C 多窗格框架：：获取窗格容器管理器

返回对内部容器管理器对象的引用。

```
CPaneContainerManager& GetPaneContainerManager();
```

### <a name="return-value"></a>返回值

对内部容器管理器对象的引用。

### <a name="remarks"></a>备注

此方法可用于访问内部[CPane 容器管理器类](../../mfc/reference/cpanecontainermanager-class.md)对象。

## <a name="cmultipaneframewndgetpanecount"></a><a name="getpanecount"></a>C 多窗格框架：：获取窗格计数

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndgetvisiblepanecount"></a><a name="getvisiblepanecount"></a>C 多窗格框架：：获取可见窗格计数

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndinsertpane"></a><a name="insertpane"></a>C 多窗格框架：：插入窗格

```
virtual BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter);
```

### <a name="parameters"></a>参数

[在]*p控制栏*<br/>
[在]*p目标*<br/>
[在]*b 后*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndloadstate"></a><a name="loadstate"></a>C 多窗格框架：：加载状态

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

[在]*lpsz配置文件名称*<br/>
[在]*uiID*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndondocktorecentpos"></a><a name="ondocktorecentpos"></a>C 多窗格框架：：在多克到最新Pos

```
virtual void OnDockToRecentPos();
```

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndonkillrolluptimer"></a><a name="onkillrolluptimer"></a>C 多窗格框架：：在基基尔罗普普计时器上

```
virtual void OnKillRollUpTimer();
```

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndonpanerecalclayout"></a><a name="onpanerecalclayout"></a>C 多窗格框架：：在窗格Recalc布局上

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndonsetrolluptimer"></a><a name="onsetrolluptimer"></a>C 多窗格框架：：打开滚动计时器

```
virtual void OnSetRollUpTimer();
```

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndonshowpane"></a><a name="onshowpane"></a>C 多窗格框架：：在显示窗格上

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>
[在]*b显示*<br/>

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndpanefrompoint"></a><a name="panefrompoint"></a>C 多窗格框架：:P从点

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>参数

[在]*点*<br/>
[在]*nSensitivity*<br/>
[在]*b 检查可见性*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndremovenonvalidpanes"></a><a name="removenonvalidpanes"></a>C 多窗格框架：：删除非有效窗格

```
virtual void RemoveNonValidPanes();
```

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndremovepane"></a><a name="removepane"></a>C 多窗格框架：：删除窗格

```
virtual void RemovePane(
    CBasePane* pBar,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = TRUE);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>
[在]*b破坏*<br/>
[在]*b 无延迟销毁*<br/>

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndreplacepane"></a><a name="replacepane"></a>C 多窗格框架：：替换窗格

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>参数

[在]*pBarOrg*<br/>
[在]*pbar 替换与*<br/>

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndsavestate"></a><a name="savestate"></a>C 多窗格框架：：保存状态

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

[在]*lpsz配置文件名称*<br/>
[在]*uiID*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndserialize"></a><a name="serialize"></a>C 多窗格框架：：序列化

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

[在]*阿尔*<br/>

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndsetdockstate"></a><a name="setdockstate"></a>C 多窗格框架：：SetDockstate

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>参数

[在]*pDock管理器*<br/>

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndsetlastfocusedpane"></a><a name="setlastfocusedpane"></a>C 多窗格框架：：设置最后聚焦窗格

```cpp
void SetLastFocusedPane(HWND hwnd);
```

### <a name="parameters"></a>参数

[在]*霍恩德*<br/>

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndsetpredockstate"></a><a name="setpredockstate"></a>C 多窗格框架：：设置前坞州

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>参数

[在]*前DockState*<br/>
[在]*pBartodock*<br/>
[在]*基方法*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>C 多窗格框架：：存储最新网站信息

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>

### <a name="remarks"></a>备注

## <a name="cmultipaneframewndstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>C 多窗格框架：：存储最新标签相关信息

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>参数

[在]*pDockingBar*<br/>
[在]*pTabbedBar*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFramewnd 类](../../mfc/reference/cpaneframewnd-class.md)
