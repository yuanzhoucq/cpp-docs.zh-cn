---
title: CPaneDivider 类
ms.date: 11/04/2016
f1_keywords:
- CPaneDivider
- AFXPANEDIVIDER/CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::AddPaneContainer
- AFXPANEDIVIDER/CPaneDivider::AddPane
- AFXPANEDIVIDER/CPaneDivider::AddRecentPane
- AFXPANEDIVIDER/CPaneDivider::CalcExpectedDockedRect
- AFXPANEDIVIDER/CPaneDivider::CalcFixedLayout
- AFXPANEDIVIDER/CPaneDivider::CheckVisibility
- AFXPANEDIVIDER/CPaneDivider::CreateEx
- AFXPANEDIVIDER/CPaneDivider::DoesAllowDynInsertBefore
- AFXPANEDIVIDER/CPaneDivider::DoesContainFloatingPane
- AFXPANEDIVIDER/CPaneDivider::FindPaneContainer
- AFXPANEDIVIDER/CPaneDivider::FindTabbedPane
- AFXPANEDIVIDER/CPaneDivider::GetDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::GetFirstPane
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividerStyle
- AFXPANEDIVIDER/CPaneDivider::GetRootContainerRect
- AFXPANEDIVIDER/CPaneDivider::GetWidth
- AFXPANEDIVIDER/CPaneDivider::Init
- AFXPANEDIVIDER/CPaneDivider::InsertPane
- AFXPANEDIVIDER/CPaneDivider::IsAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::IsDefault
- AFXPANEDIVIDER/CPaneDivider::IsHorizontal
- AFXPANEDIVIDER/CPaneDivider::Move
- AFXPANEDIVIDER/CPaneDivider::NotifyAboutRelease
- AFXPANEDIVIDER/CPaneDivider::OnShowPane
- AFXPANEDIVIDER/CPaneDivider::ReleaseEmptyPaneContainers
- AFXPANEDIVIDER/CPaneDivider::RemovePane
- AFXPANEDIVIDER/CPaneDivider::ReplacePane
- AFXPANEDIVIDER/CPaneDivider::RepositionPanes
- AFXPANEDIVIDER/CPaneDivider::Serialize
- AFXPANEDIVIDER/CPaneDivider::SetAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::SetPaneContainerManager
- AFXPANEDIVIDER/CPaneDivider::ShowWindow
- AFXPANEDIVIDER/CPaneDivider::StoreRecentDockSiteInfo
- AFXPANEDIVIDER/CPaneDivider::StoreRecentTabRelatedInfo
- AFXPANEDIVIDER/CPaneDivider::GetPanes
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividers
- AFXPANEDIVIDER/CPaneDivider::m_nDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::m_pSliderRTC
helpviewer_keywords:
- CPaneDivider [MFC], CPaneDivider
- CPaneDivider [MFC], AddPaneContainer
- CPaneDivider [MFC], AddPane
- CPaneDivider [MFC], AddRecentPane
- CPaneDivider [MFC], CalcExpectedDockedRect
- CPaneDivider [MFC], CalcFixedLayout
- CPaneDivider [MFC], CheckVisibility
- CPaneDivider [MFC], CreateEx
- CPaneDivider [MFC], DoesAllowDynInsertBefore
- CPaneDivider [MFC], DoesContainFloatingPane
- CPaneDivider [MFC], FindPaneContainer
- CPaneDivider [MFC], FindTabbedPane
- CPaneDivider [MFC], GetDefaultWidth
- CPaneDivider [MFC], GetFirstPane
- CPaneDivider [MFC], GetPaneDividerStyle
- CPaneDivider [MFC], GetRootContainerRect
- CPaneDivider [MFC], GetWidth
- CPaneDivider [MFC], Init
- CPaneDivider [MFC], InsertPane
- CPaneDivider [MFC], IsAutoHideMode
- CPaneDivider [MFC], IsDefault
- CPaneDivider [MFC], IsHorizontal
- CPaneDivider [MFC], Move
- CPaneDivider [MFC], NotifyAboutRelease
- CPaneDivider [MFC], OnShowPane
- CPaneDivider [MFC], ReleaseEmptyPaneContainers
- CPaneDivider [MFC], RemovePane
- CPaneDivider [MFC], ReplacePane
- CPaneDivider [MFC], RepositionPanes
- CPaneDivider [MFC], Serialize
- CPaneDivider [MFC], SetAutoHideMode
- CPaneDivider [MFC], SetPaneContainerManager
- CPaneDivider [MFC], ShowWindow
- CPaneDivider [MFC], StoreRecentDockSiteInfo
- CPaneDivider [MFC], StoreRecentTabRelatedInfo
- CPaneDivider [MFC], GetPanes
- CPaneDivider [MFC], GetPaneDividers
- CPaneDivider [MFC], m_nDefaultWidth
- CPaneDivider [MFC], m_pSliderRTC
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
ms.openlocfilehash: 0ebac4e18f65d789d5196266d57184744ad5ad28
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753626"
---
# <a name="cpanedivider-class"></a>CPaneDivider 类

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

类`CPaneDivider`划分两个窗格，划分两组窗格，或从主框架窗口的工作区分隔一组窗格。

## <a name="syntax"></a>语法

```
class CPaneDivider : public CBasePane
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CPaneDivider：CPaneDivider](#cpanedivider)||

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPaneDivider：：添加窗格容器](#addpanecontainer)||
|[CPaneDivider：：添加窗格](#addpane)||
|[CPaneDivider：：添加最新窗格](#addrecentpane)||
|[CPaneDivider：：卡尔西德多克雷茨](#calcexpecteddockedrect)||
|[CPaneDivider：：钙固定布局](#calcfixedlayout)|（覆盖[CBasePane：：CalcFixed 布局](../../mfc/reference/cbasepane-class.md#calcfixedlayout).）|
|[CPaneDivider：：检查可见性](#checkvisibility)||
|[CPaneDivider：：创建Ex](#createex)|（覆盖[CBasePane：createEx](../../mfc/reference/cbasepane-class.md#createex).）|
|[CPaneDivider：:D允许在之前插入](#doesallowdyninsertbefore)|（覆盖[CBasePane：:DoesAllowDynInsert 之前](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).）|
|[CPaneDivider：:D包含浮动窗格](#doescontainfloatingpane)||
|[CPaneDivider：：查找窗格容器](#findpanecontainer)||
|[CPaneDivider：：查找标签窗格](#findtabbedpane)||
|[CPaneDivider：获取默认宽度](#getdefaultwidth)||
|[CPaneDivider：获取第一窗格](#getfirstpane)||
|[CPaneDivider：：获取窗格分线器样式](#getpanedividerstyle)||
|[CPaneDivider：：获取根容器重新完成](#getrootcontainerrect)||
|[CPaneDivider：获取宽度](#getwidth)||
|[CPaneDivider：：Init](#init)||
|[CPaneDivider：：插入窗格](#insertpane)||
|[CPaneDivider：：是自动隐藏模式](#isautohidemode)|（覆盖[CBasePane：是自动隐藏模式](../../mfc/reference/cbasepane-class.md#isautohidemode)。|
|[CPaneDivider：默认](#isdefault)||
|[CPaneDivider：是水平的](#ishorizontal)|（覆盖[CBasePane：是水平](../../mfc/reference/cbasepane-class.md#ishorizontal)的 。）|
|[CPaneDivider：：移动](#move)||
|[CPaneDivider：：通知发布](#notifyaboutrelease)||
|[CPaneDivider：：在显示窗格上](#onshowpane)||
|[CPaneDivider：：释放空窗格容器](#releaseemptypanecontainers)||
|[CPaneDivider：：删除窗格](#removepane)||
|[CPaneDivider：：替换窗格](#replacepane)||
|[CPaneDivider：：重新定位窗格](#repositionpanes)||
|[CPaneDivider：序列化](#serialize)|（重写 `CBasePane::Serialize`。）|
|[CPaneDivider：：设置自动隐藏模式](#setautohidemode)||
|[CPaneDivider：：设置窗格容器管理器](#setpanecontainermanager)||
|[CPaneDivider：：显示窗口](#showwindow)||
|[CPaneDivider：：存储最新网站信息](#storerecentdocksiteinfo)||
|[CPaneDivider：：存储最新标签相关信息](#storerecenttabrelatedinfo)||

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPaneDivider：：获取窗格](#getpanes)|返回驻留在[CPane 容器类](../../mfc/reference/cpanecontainer-class.md)中的窗格的列表。 此方法应仅针对默认窗格分隔符调用。|
|[CPaneDivider：：获取窗格分频器](#getpanedividers)|返回驻留在[CPane 容器类](../../mfc/reference/cpanecontainer-class.md)中的窗格分隔符的列表。 此方法应仅针对默认窗格分隔符调用。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CPaneDivider：m_nDefaultWidth](#m_ndefaultwidth)|指定应用程序中所有窗格分隔符的默认宽度（以像素为单位）。|
|[CPaneDivider：：m_pSliderRTC](#m_psliderrtc)|保存指向有关派生对象的运行时类信息的`CPaneDivider`指针。|

## <a name="remarks"></a>备注

当窗格停靠`CPaneDivider`时，框架会自动创建对象。

有两种类型的窗格分隔符：

- 当一组窗格停靠在主框架窗口的一侧时，将创建默认窗格分隔符。 默认窗格分隔符包含指向[CPaneContainerManager 类](../../mfc/reference/cpanecontainermanager-class.md)的指针，并将窗格组上的大多数操作（例如调整窗格大小或停靠另一个窗格或容器）重定向到容器管理器。 每个停靠窗格都维护指向其默认窗格分隔符的指针。

- 常规窗格分隔符只需在容器中划分两个窗格。 有关详细信息，请参阅[CPane 容器类](../../mfc/reference/cpanecontainer-class.md)。

## <a name="example"></a>示例

下面的示例演示如何从 `CWorkspaceBar` 对象获取 `CPaneDivider` 对象。 此代码段是[MDI 选项卡演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)\
•&nbsp;[CMD目标](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[Cwnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CPaneDivider](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>要求

**标题：** afxPaneDivider.h

## <a name="cpanedividersetautohidemode"></a><a name="setautohidemode"></a>CPaneDivider：：设置自动隐藏模式

```cpp
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>参数

[在]*bMode*<br/>

### <a name="remarks"></a>备注

## <a name="cpanedividersetpanecontainermanager"></a><a name="setpanecontainermanager"></a>CPaneDivider：：设置窗格容器管理器

```cpp
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>参数

[在]*p*<br/>

### <a name="remarks"></a>备注

## <a name="cpanedivideraddpane"></a><a name="addpane"></a>CPaneDivider：：添加窗格

```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>

### <a name="remarks"></a>备注

## <a name="cpanedivideraddpanecontainer"></a><a name="addpanecontainer"></a>CPaneDivider：：添加窗格容器

```
virtual BOOL AddPaneContainer(
    CPaneContainerManager& barContainerManager,
    BOOL bOuterEdge);

virtual BOOL AddPaneContainer(
    CDockablePane* pTargetBar,
    CPaneContainerManager& barContainerManager,
    DWORD dwAlignment);
```

### <a name="parameters"></a>参数

[在]*酒吧容器管理器*<br/>
[在]*bouterEdge*<br/>
[在]*p目标栏*<br/>
[在]*dwalignment*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedivideraddrecentpane"></a><a name="addrecentpane"></a>CPaneDivider：：添加最新窗格

```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CPaneDivider：：卡尔西德多克雷茨

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

## <a name="cpanedividercalcfixedlayout"></a><a name="calcfixedlayout"></a>CPaneDivider：：钙固定布局

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

[在]*b 拉伸*<br/>
[在]*布霍兹*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividercheckvisibility"></a><a name="checkvisibility"></a>CPaneDivider：：检查可见性

```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividercpanedivider"></a><a name="cpanedivider"></a>CPaneDivider：CPaneDivider

```
CPaneDivider();

CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>参数

[在]*b默认滑块*<br/>
[在]*p 父级*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividercreateex"></a><a name="createex"></a>CPaneDivider：：创建Ex

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext);
```

### <a name="parameters"></a>参数

[在]*dwStyleEx*<br/>
[在]*dwStyle*<br/>
[在]*rect*<br/>
[在]*pparentwnd*<br/>
[在]*nID*<br/>
[在]*pContext*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividerdoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CPaneDivider：:D允许在之前插入

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividerdoescontainfloatingpane"></a><a name="doescontainfloatingpane"></a>CPaneDivider：:D包含浮动窗格

```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividerfindpanecontainer"></a><a name="findpanecontainer"></a>CPaneDivider：：查找窗格容器

```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>
[在]*b左栏*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividerfindtabbedpane"></a><a name="findtabbedpane"></a>CPaneDivider：：查找标签窗格

```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>参数

[在]*nID*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividergetdefaultwidth"></a><a name="getdefaultwidth"></a>CPaneDivider：获取默认宽度

```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividergetfirstpane"></a><a name="getfirstpane"></a>CPaneDivider：获取第一窗格

```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividergetpanedividers"></a><a name="getpanedividers"></a>CPaneDivider：：获取窗格分频器

返回驻留在[CPane 容器类](../../mfc/reference/cpanecontainer-class.md)中的窗格分隔符的列表。 此方法应仅针对默认窗格分隔符调用。

```cpp
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>参数

*lstSliders*<br/>
[出]包含驻留在窗格容器中的窗格分隔符的列表。

### <a name="remarks"></a>备注

此方法应仅针对默认窗格分隔符调用。 默认窗格分隔符是调整整个窗格容器大小的分隔符。

## <a name="cpanedividergetpanedividerstyle"></a><a name="getpanedividerstyle"></a>CPaneDivider：：获取窗格分线器样式

```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividergetpanes"></a><a name="getpanes"></a>CPaneDivider：：获取窗格

返回驻留在[CPane 容器类](../../mfc/reference/cpanecontainer-class.md)中的窗格的列表。 应仅调用此方法来检索默认窗格分隔符。

```cpp
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>参数

*lstBars*<br/>
[出]包含驻留在窗格容器中的窗格的列表。

### <a name="remarks"></a>备注

此方法应仅针对默认窗格分隔符调用。 默认窗格分隔符是调整整个窗格容器大小的分隔符。

## <a name="cpanedividergetrootcontainerrect"></a><a name="getrootcontainerrect"></a>CPaneDivider：：获取根容器重新完成

```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividergetwidth"></a><a name="getwidth"></a>CPaneDivider：获取宽度

```
int GetWidth() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividerinit"></a><a name="init"></a>CPaneDivider：：Init

```cpp
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>参数

[在]*b默认滑块*<br/>
[在]*p 父级*<br/>

### <a name="remarks"></a>备注

## <a name="cpanedividerinsertpane"></a><a name="insertpane"></a>CPaneDivider：：插入窗格

```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>参数

[在]*pBarto插入*<br/>
[在]*p目标栏*<br/>
[在]*dwalignment*<br/>
[在]*lpRect*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividerisautohidemode"></a><a name="isautohidemode"></a>CPaneDivider：：是自动隐藏模式

```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividerisdefault"></a><a name="isdefault"></a>CPaneDivider：默认

```
BOOL IsDefault() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividerishorizontal"></a><a name="ishorizontal"></a>CPaneDivider：是水平的

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividerm_ndefaultwidth"></a><a name="m_ndefaultwidth"></a>CPaneDivider：m_nDefaultWidth

指定应用程序中所有窗格分隔符的默认宽度（以像素为单位）。

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

## <a name="cpanedividermove"></a><a name="move"></a>CPaneDivider：：移动

```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>参数

[在]*pt偏移*<br/>
[在]*b 调整布局*<br/>

### <a name="remarks"></a>备注

## <a name="cpanedividerm_psliderrtc"></a><a name="m_psliderrtc"></a>CPaneDivider：：m_pSliderRTC

保存指向有关派生对象的运行时类信息的`CPaneDivider`指针。

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>备注

如果创建自定义窗格分隔符，请设置此成员变量。 这使框架能够在绘制窗格时创建窗格分隔符。

### <a name="example"></a>示例

下面的示例演示如何设置`m_pSliderRTC`成员变量：

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

## <a name="cpanedividernotifyaboutrelease"></a><a name="notifyaboutrelease"></a>CPaneDivider：：通知发布

```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>备注

## <a name="cpanedivideronshowpane"></a><a name="onshowpane"></a>CPaneDivider：：在显示窗格上

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>
[在]*b显示*<br/>

### <a name="remarks"></a>备注

## <a name="cpanedividerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a>CPaneDivider：：释放空窗格容器

```cpp
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>备注

## <a name="cpanedividerremovepane"></a><a name="removepane"></a>CPaneDivider：：删除窗格

```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>

### <a name="remarks"></a>备注

## <a name="cpanedividerreplacepane"></a><a name="replacepane"></a>CPaneDivider：：替换窗格

```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>参数

[在]*pBarto 替换*<br/>
[在]*pbarto 替换为*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpanedividerrepositionpanes"></a><a name="repositionpanes"></a>CPaneDivider：：重新定位窗格

```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>参数

[在]*重新*<br/>
[在]*hdwp*<br/>

### <a name="remarks"></a>备注

## <a name="cpanedividerserialize"></a><a name="serialize"></a>CPaneDivider：序列化

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

[在]*阿尔*<br/>

### <a name="remarks"></a>备注

## <a name="cpanedividershowwindow"></a><a name="showwindow"></a>CPaneDivider：：显示窗口

```cpp
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>参数

[在]*nCmdShow*<br/>

### <a name="remarks"></a>备注

## <a name="cpanedividerstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CPaneDivider：：存储最新网站信息

```cpp
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>

### <a name="remarks"></a>备注

## <a name="cpanedividerstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CPaneDivider：：存储最新标签相关信息

```cpp
void StoreRecentTabRelatedInfo(
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
[CPaneContainerManager 类](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[CPaneContainer 类](../../mfc/reference/cpanecontainer-class.md)<br/>
[CDockingManager 类](../../mfc/reference/cdockingmanager-class.md)<br/>
[CBasePane 类](../../mfc/reference/cbasepane-class.md)
