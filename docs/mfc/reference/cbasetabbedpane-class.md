---
title: CBaseTabbedPane 类
ms.date: 11/04/2016
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
ms.openlocfilehash: d7ffaa7274a8ed12944cdbc5dcbbdcb8fd3fd2b9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259290"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane 类

扩展 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 的功能以支持创建选项卡式窗口。

## <a name="syntax"></a>语法

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CBaseTabbedPane::AddTab](#addtab)|将一个新选项卡添加到选项卡式窗格。|
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定空的选项卡式的窗格是否可被销毁。|
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|应用从注册表加载到选项卡式窗格的选项卡设置。|
|[CBaseTabbedPane::CanFloat](#canfloat)|确定是否可以浮动窗格。 (重写[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。)|
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|确定选项卡式窗格的标题是否应作为活动选项卡显示相同的文本。|
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(重写[CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。)|
|[CBaseTabbedPane::DetachPane](#detachpane)|将一个或多个可停靠窗格转换为 MDI 选项卡式文档。|
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|启用或禁用同步的能力选项卡式窗格的标题文本活动选项卡上的标签文本。|
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|将内部的 tab 键顺序还原到默认状态。|
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|返回时选项卡由一个从零开始的选项卡索引驻留在选项卡中的窗格。|
|||
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|返回由窗格 ID 标识的窗格|
|[CBaseTabbedPane::FloatTab](#floattab)|仅当窗格中当前驻留在拆离的选项卡中时浮动窗格。|
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|在窗格中返回选项卡的默认顺序。|
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|检索指向第一个显示的选项卡。|
|[CBaseTabbedPane::GetMinSize](#getminsize)|检索的最小允许大小的窗格。 (重写[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。)|
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|返回的句柄窗格图标。 (重写[CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon)。)|
|[CBaseTabbedPane::GetPaneList](#getpanelist)|在选项卡式窗格中返回所包含的窗格的列表。|
|[CBaseTabbedPane::GetTabArea](#gettabarea)|返回顶部和底部选项卡区域的边界矩形。|
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|在选项卡窗口中返回选项卡的计数。|
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|获取基础 （包装） 选项卡窗口。|
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|返回显示选项卡的计数。|
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|确定是否可以切换到自动隐藏模式，选项卡式的窗格。|
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|确定如果只显示一个选项卡是否隐藏选项卡式的窗格。|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|在序列化期间在内部使用。|
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|重新计算在窗格的布局信息。 (重写[cpane:: Recalclayout](../../mfc/reference/cpane-class.md#recalclayout)。)|
|[CBaseTabbedPane::RemovePane](#removepane)|从选项卡式窗格中删除一个窗格。|
|`CBaseTabbedPane::SaveSiblingBarIDs`|在序列化期间在内部使用。|
|`CBaseTabbedPane::Serialize`|(重写[cdockablepane:: Serialize](cdockablepane-class.md)。)|
|`CBaseTabbedPane::SerializeTabWindow`|在序列化期间在内部使用。|
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|确定是否将自动销毁选项卡式的控件条。|
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|切换停靠窗格之间显示和自动隐藏模式。 (重写[CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)。)|
|[CBaseTabbedPane::ShowTab](#showtab)|显示或隐藏选项卡。|

## <a name="remarks"></a>备注

此类是一个抽象类，并不能实例化。 它实现的服务的通用于所有类型的选项卡式窗格。

目前，库包含两个选项卡式的窗格中派生的类：[CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)并[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

一个`CBaseTabbedPane`对象包装到指针[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)对象。 [CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)随后将成为子窗口的选项卡式窗格。

有关如何创建选项卡式的窗格的详细信息，请参阅[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)， [CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)，并[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>要求

**标头：** afxBaseTabbedPane.h

##  <a name="addtab"></a>  CBaseTabbedPane::AddTab

将一个新选项卡添加到选项卡式窗格。

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>参数

*pNewBar*<br/>
[in、 out]指向添加窗格的指针。 调用此方法后，此指针可能变为无效。 有关详细信息，请参阅“备注”部分。

*bVisible*<br/>
[in]将选项卡可见，则为 TRUE否则为 FALSE。

*bSetActive*<br/>
[in]若要使活动选项卡; 的选项卡，则返回 TRUE否则为 FALSE。

*bDetachable*<br/>
[in]为 TRUE，则使选项卡的可拆分;否则为 FALSE。

### <a name="return-value"></a>返回值

如果窗格已成功添加为一个选项卡，并且已不在过程中会被销毁，则为 TRUE。 如果要添加的窗格是类型的对象，则为 FALSE `CBaseTabbedPane`。 有关详细信息，请参阅“备注”部分。

### <a name="remarks"></a>备注

调用此方法以添加为选项卡式窗格上的新选项卡的窗格。 如果*pNewBar*指向类型的对象`CBaseTabbedPane`，所有选项卡复制到选项卡式窗格上，然后*pNewBar*被销毁。 因此， *pNewBar*变为无效指针，不应使用。

##  <a name="allowdestroyemptytabbedpane"></a>  CBaseTabbedPane::AllowDestroyEmptyTabbedPane

指定空的选项卡式的窗格是否可被销毁。

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>返回值

如果可销毁一个空的选项卡式的窗格; 则为 TRUE否则为 FALSE。 默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

如果不允许空的选项卡式的窗格要销毁，framework 隐藏窗格。

##  <a name="applyrestoredtabinfo"></a>  CBaseTabbedPane::ApplyRestoredTabInfo

从注册表加载选项卡设置，并将其应用到选项卡式窗格。

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>参数

*bUseTabIndexes*<br/>
[in]由框架在内部使用此参数。

### <a name="remarks"></a>备注

重新加载注册表中的停靠状态信息时，由框架调用此方法。 此方法获取有关 tab 键顺序和选项卡式窗格的选项卡名称的信息。

##  <a name="canfloat"></a>  CBaseTabbedPane::CanFloat

指定是否可以浮动选项卡式的窗格。

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>返回值

如果可以浮动窗格; 则为 TRUE否则为 FALSE。

##  <a name="cansetcaptiontexttotabname"></a>  CBaseTabbedPane::CanSetCaptionTextToTabName

确定选项卡式窗格的标题是否应作为活动选项卡显示相同的文本。

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>返回值

如果选项卡式窗格的标题文本设置为活动选项卡; 的文本，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

该方法用于确定是否显示的文本上选项卡式的窗格标题重复项的活动选项卡的标签。您可以启用或禁用此功能通过调用[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)。

##  <a name="converttotabbeddocument"></a>  CBaseTabbedPane::ConvertToTabbedDocument

将一个或多个可停靠窗格转换为 MDI 选项卡式文档。

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>参数

*bActiveTabOnly*<br/>
[in]在转换选项卡式窗格中，指定为 TRUE，则转换仅活动选项卡。指定为 FALSE，则将在窗格中的所有制表符都转换。

##  <a name="detachpane"></a>  CBaseTabbedPane::DetachPane

分离窗格从选项卡式窗格。

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[in]指向要分离的窗格。

*bHide*<br/>
[in]布尔参数，用于指定它分离之后，该框架是否隐藏窗格。

### <a name="return-value"></a>返回值

如果框架已成功分离窗格; 则为 TRUEFalse *pBar*为 NULL 或引用不是在选项卡式窗格中的窗格。

### <a name="remarks"></a>备注

框架在可能的情况浮动分离窗格。 有关详细信息，请参阅[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。

##  <a name="enablesetcaptiontexttotabname"></a>  CBaseTabbedPane::EnableSetCaptionTextToTabName

启用或禁用同步的能力选项卡式窗格的标题文本活动选项卡上的标签文本。

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
[in]为 TRUE，则与活动选项卡标题中，同步的选项卡式的窗格标题否则为 FALSE。

##  <a name="filldefaulttabsorderarray"></a>  CBaseTabbedPane::FillDefaultTabsOrderArray

将内部的 tab 键顺序还原到默认状态。

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>备注

该框架将 Outlook 栏还原到初始状态时，调用此方法。

##  <a name="findpanebyid"></a>  CBaseTabbedPane::FindPaneByID

返回由窗格 ID 标识的窗格

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>参数

*uBarID*<br/>
[in]指定要查找窗格的 ID。

### <a name="return-value"></a>返回值

指向找到它; 如果窗格中的指针否则，为 NULL。

### <a name="remarks"></a>备注

此方法比较在窗格中的所有选项卡，并返回具有指定 ID 的一个*uBarID*参数。

##  <a name="findbarbytabnumber"></a>  CBaseTabbedPane::FindBarByTabNumber

返回驻留在一个选项卡的窗格。

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>参数

*nTabNum*<br/>
[in]指定要检索的选项卡的从零开始索引。

*bGetWrappedBar*<br/>
[in]为 TRUE，则返回窗格而不是重试。 窗格中的基础 （包装） 的窗口否则为 FALSE。 这仅适用于窗格派生自[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)。

### <a name="return-value"></a>返回值

如果找到，则返回指向要搜索的窗格中的有效指针; 在窗格否则，为 NULL。

### <a name="remarks"></a>备注

调用此方法以检索驻留在由指定的选项卡中的窗格*nTabNum*参数。

##  <a name="floattab"></a>  CBaseTabbedPane::FloatTab

仅当窗格中当前驻留在拆离的选项卡中时浮动窗格。

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[in、 out]指向为浮动窗格的指针。

*nTabID*<br/>
[in]指定为浮动选项卡的从零开始的索引。

*dockMethod*<br/>
[in]指定要使用可使窗格浮动的方法。 有关详细信息，请参阅“备注”部分。

*bHide*<br/>
[in]为 TRUE，则浮点; 之前隐藏窗格否则为 FALSE。

### <a name="return-value"></a>返回值

如果将浮动窗格; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

调用此方法以浮动窗格中当前驻留在拆离的选项卡。

如果你想要以编程方式分离窗格中，指定为 DM_SHOW *dockMethod*参数。 如果你想要浮动在相同的位置之前浮动窗格中，指定作为 DM_DBL_CLICK *dockMethod*参数。

##  <a name="getdefaulttabsorder"></a>  CBaseTabbedPane::GetDefaultTabsOrder

在窗格中返回选项卡的默认顺序。

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>返回值

一个`CArray`对象，它在窗格中指定选项卡的默认顺序。

### <a name="remarks"></a>备注

Outlook 栏重置为初始状态时，框架将调用此方法。

##  <a name="getfirstvisibletab"></a>  CBaseTabbedPane::GetFirstVisibleTab

检索指向第一个显示的选项卡。

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>参数

*iTabNum*<br/>
[in]对整数的引用。 此方法将写入第一个显示的选项卡的从零开始的索引到此参数，则为-1 如果未显示选项卡上找到。

### <a name="return-value"></a>返回值

如果成功，指向第一个显示选项卡;否则，为 NULL。

##  <a name="getminsize"></a>  CBaseTabbedPane::GetMinSize

检索的最小允许大小的窗格。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>参数

*size*<br/>
[out]一个`CSize`对象填充的最小允许大小。

### <a name="remarks"></a>备注

如果处于活动状态的最小窗格大小一致处理 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))，*大小*填入的最小允许大小为活动选项卡。否则为*大小*的返回值填充[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。

##  <a name="getpaneicon"></a>  CBaseTabbedPane::GetPaneIcon

检索的最小允许大小的窗格。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>参数

*size*<br/>
[out]一个`CSize`对象填充的最小允许大小。

### <a name="remarks"></a>备注

如果处于活动状态的最小窗格大小一致处理 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))，*大小*填入的最小允许大小为活动选项卡。否则为*大小*的返回值填充[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。

##  <a name="getpanelist"></a>  CBaseTabbedPane::GetPaneList

在选项卡式窗格中返回所包含的窗格的列表。

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>参数

*lst*<br/>
[out]一个`CObList`充满选项卡式窗格中包含的窗格。

*pRTCFilter*<br/>
[in]如果不为 NULL，返回的列表包含属于指定的运行时类的窗格。

##  <a name="gettabarea"></a>  CBaseTabbedPane::GetTabArea

返回顶部和底部选项卡区域的边界矩形。

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>参数

*rectTabAreaTop*<br/>
[out]接收上部选项卡区域的屏幕坐标。

*rectTabAreaBottom*<br/>
[out]接收较低的选项卡区域的屏幕坐标。

### <a name="remarks"></a>备注

调用此方法来确定的上限和下限的选项卡区域的屏幕坐标中的边界矩形。

##  <a name="gettabsnum"></a>  CBaseTabbedPane::GetTabsNum

在选项卡窗口中返回选项卡的计数。

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>返回值

在选项卡式窗格中的选项卡的数目。

##  <a name="getunderlyingwindow"></a>  CBaseTabbedPane::GetUnderlyingWindow

获取基础 （包装） 选项卡窗口。

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>返回值

指向基础的选项卡窗口的指针。

##  <a name="getvisibletabsnum"></a>  CBaseTabbedPane::GetVisibleTabsNum

返回可见选项卡的计数。

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>返回值

可见选项卡，将是大于或等于零的数目。

### <a name="remarks"></a>备注

调用此方法来确定在选项卡式窗格中的可见选项卡的数目。

##  <a name="hasautohidemode"></a>  Cbasetabbedpane:: Hasautohidemode

确定选项卡式窗格是否可以切换为自动隐藏模式。

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>返回值

如果窗格可以切换到自动隐藏模式，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

如果禁用自动隐藏模式，则没有 pin 按钮将显示在选项卡式的窗格标题。

##  <a name="ishidesingletab"></a>  CBaseTabbedPane::IsHideSingleTab

确定如果只显示一个选项卡是否隐藏选项卡式的窗格。

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>返回值

如果只有一个可见选项卡; 时未显示选项卡窗口，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

如果因为只有一个选项卡处于打开状态，不显示的窗格，可以调用此方法以确定是否在选项卡式的窗格是否正常工作。

##  <a name="removepane"></a>  CBaseTabbedPane::RemovePane

从选项卡式窗格中删除一个窗格。

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[in、 out]指向删除选项卡式窗格中的窗格的指针。

### <a name="return-value"></a>返回值

如果已成功从选项卡式窗格删除窗格和选项卡式的窗格是否仍然有效，则为 TRUE。 如果已从选项卡式窗格中删除的最后一个窗格和选项卡式的窗格即将被销毁，则为 FALSE。 如果返回值为 FALSE，不要使用选项卡式的窗格任何更多。

### <a name="remarks"></a>备注

调用此方法来删除指定的窗格*pBar*选项卡式窗格中的参数。

##  <a name="setautodestroy"></a>  CBaseTabbedPane::SetAutoDestroy

确定是否将自动销毁选项卡式的控件条。

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*bAutoDestroy*<br/>
[in]如果选项卡式的窗格动态创建的您无法控制其生存期内; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

设置自动销毁模式设置为 TRUE，如果动态创建选项卡式的窗格和您无法控制其生存期。 如果自动销毁模式为 TRUE 时，将由框架自动销毁选项卡式的窗格。

##  <a name="showtab"></a>  CBaseTabbedPane::ShowTab

显示或隐藏选项卡。

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[in]指向要显示或隐藏的窗格的指针。

*bShow*<br/>
[in]为 TRUE，则显示窗格;如果为 FALSE，则若要隐藏窗格。

*bDelay*<br/>
[in]为 TRUE，则延迟的选项卡布局中; 调整否则为 FALSE。

*bActivate*<br/>
[in]若要使活动选项卡; 的选项卡，则返回 TRUE否则为 FALSE。

### <a name="return-value"></a>返回值

如果选项卡已显示或隐藏成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

当调用此方法时，窗格显示或隐藏的具体取决于值*bShow*参数。 如果隐藏选项卡，并且它是基础的选项卡窗口中的最后一个可见选项卡，则隐藏选项卡式的窗格。 如果没有以前没有的选项卡可见时显示一个选项卡，，显示选项卡式的窗格。

##  <a name="recalclayout"></a>  CBaseTabbedPane::RecalcLayout

重新计算在窗格的布局信息。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>备注

如果窗格浮动的此方法会通知框架，以调整大小的窗格为微型框架的当前大小。

如果停靠窗格中，此方法没有任何影响。

##  <a name="setautohidemode"></a>  CBaseTabbedPane::SetAutoHideMode

在选项卡式窗格中的可插拔窗格的设置自动隐藏模式。

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>参数

*bMode*<br/>
[in]如果启用了自动隐藏模式，则为如果为 FALSE，则若要启用正则停靠模式。

*dwAlignment*<br/>
[in]指定要创建的自动隐藏窗格的对齐方式。 有关可能的值的列表，请参阅[CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment)。

*pCurrAutoHideBar*<br/>
[in、 out]指向当前的自动隐藏工具栏的指针。 可以为 NULL。

*bUseTimer*<br/>
[in]指定是否要使用自动隐藏效果，当用户切换到自动隐藏模式下，窗格中，或若要立即隐藏窗格。

### <a name="return-value"></a>返回值

自动隐藏工具栏时切换到自动隐藏模式，则为 NULL，如果创建没有工具栏创建指向的指针。

### <a name="remarks"></a>备注

在用户选择固定按钮可以切换选项卡式的窗格，为自动隐藏模式或正则停靠模式时，框架将调用此方法。

自动隐藏模式设置为在选项卡式窗格中每个可拆分窗格。 将忽略非可拆分的窗格。 有关详细信息，请参阅[:: Enabletabdetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)。

调用此方法以编程方式切换到自动隐藏模式的选项卡式的窗格。 必须将窗格停靠到主框架窗口 ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider)必须返回到的有效指针[CPaneDivider](../../mfc/reference/cpanedivider-class.md))。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)
