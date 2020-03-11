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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883638"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane 类

扩展 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 的功能以支持创建选项卡式窗口。

## <a name="syntax"></a>语法

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CBaseTabbedPane：： AddTab](#addtab)|向选项卡式窗格添加新选项卡。|
|[CBaseTabbedPane：： AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定是否可以销毁空的选项卡式窗格。|
|[CBaseTabbedPane：： ApplyRestoredTabInfo](#applyrestoredtabinfo)|将从注册表加载的选项卡设置应用到选项卡式窗格。|
|[CBaseTabbedPane：： CanFloat](#canfloat)|确定窗格是否可以浮动。 （重写[CBasePane：： CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。）|
|[CBaseTabbedPane：： CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|确定选项卡式窗格的标题是否应显示与活动选项卡相同的文本。|
|[CBaseTabbedPane：： ConvertToTabbedDocument](#converttotabbeddocument)|（重写[CDockablePane：： ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。）|
|[CBaseTabbedPane：:D etachPane](#detachpane)|将一个或多个可停靠的窗格转换为 MDI 选项卡式文档。|
|[CBaseTabbedPane：： EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|启用或禁用选项卡式窗格与活动选项卡上的标签文本同步标题文本的功能。|
|[CBaseTabbedPane：： FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|将内部选项卡顺序还原为默认状态。|
|[CBaseTabbedPane：： FindBarByTabNumber](#findbarbytabnumber)|当选项卡由从零开始的选项卡索引标识时，返回位于选项卡中的窗格。|
|||
|[CBaseTabbedPane：： FindPaneByID](#findpanebyid)|返回由窗格 ID 标识的窗格。|
|[CBaseTabbedPane：： FloatTab](#floattab)|仅当窗格中当前驻留在拆离的选项卡中时浮动窗格。|
|[CBaseTabbedPane：： GetDefaultTabsOrder](#getdefaulttabsorder)|返回窗格中选项卡的默认顺序。|
|[CBaseTabbedPane：： GetFirstVisibleTab](#getfirstvisibletab)|检索指向第一个显示的选项卡的指针。|
|[CBaseTabbedPane：： GetMinSize](#getminsize)|检索窗格允许的最小大小。 （重写[CPane：： GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。）|
|[CBaseTabbedPane：： GetPaneIcon](#getpaneicon)|返回窗格图标的句柄。 （重写[CBasePane：： GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon)。）|
|[CBaseTabbedPane：： GetPaneList](#getpanelist)|返回包含在选项卡式窗格中的窗格的列表。|
|[CBaseTabbedPane：： GetTabArea](#gettabarea)|返回 "上" 和 "下" 选项卡区域的边框。|
|[CBaseTabbedPane：： GetTabsNum](#gettabsnum)|返回选项卡窗口中选项卡的计数。|
|[CBaseTabbedPane：： GetUnderlyingWindow](#getunderlyingwindow)|获取基础（已包装）选项卡窗口。|
|[CBaseTabbedPane：： GetVisibleTabsNum](#getvisibletabsnum)|返回显示的选项卡的计数。|
|[CBaseTabbedPane：： HasAutoHideMode](#hasautohidemode)|确定选项卡式窗格是否可以切换为自动隐藏模式。|
|[CBaseTabbedPane：： IsHideSingleTab](#ishidesingletab)|确定在只显示一个选项卡时是否隐藏选项卡式窗格。|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|在序列化过程中供内部使用。|
|[CBaseTabbedPane：： RecalcLayout](#recalclayout)|重新计算窗格的布局信息。 （重写[CPane：： RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout)。）|
|[CBaseTabbedPane：： RemovePane](#removepane)|从选项卡式窗格中删除窗格。|
|`CBaseTabbedPane::SaveSiblingBarIDs`|在序列化过程中供内部使用。|
|`CBaseTabbedPane::Serialize`|（重写[CDockablePane：：串行化](cdockablepane-class.md)。）|
|`CBaseTabbedPane::SerializeTabWindow`|在序列化过程中供内部使用。|
|[CBaseTabbedPane：： SetAutoDestroy](#setautodestroy)|确定是否将自动销毁选项卡式控件条。|
|[CBaseTabbedPane：： SetAutoHideMode](#setautohidemode)|在显示和自动隐藏模式之间切换停靠窗格。 （重写[CDockablePane：： SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)。）|
|[CBaseTabbedPane：： Showtab "](#showtab)|显示或隐藏选项卡。|

## <a name="remarks"></a>备注

此类是一个抽象类，不能进行实例化。 它实现了所有类型的选项卡式窗格通用的服务。

当前，库包含两个派生的选项卡式窗格类： [CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)和[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

`CBaseTabbedPane` 对象包装指向[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)对象的指针。 然后， [CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)将成为选项卡式窗格的子窗口。

有关如何创建选项卡式窗格的详细信息，请参阅[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)、 [CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)和[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>要求

**标头：** afxBaseTabbedPane

##  <a name="addtab"></a>CBaseTabbedPane：： AddTab

向选项卡式窗格添加新选项卡。

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>parameters

*pNewBar*<br/>
[in，out]指向要添加的窗格的指针。 调用此方法后，此指针可能变为无效。 有关详细信息，请参见“备注”部分。

*bVisible*<br/>
中若要使选项卡可见，则为 TRUE;否则为 FALSE。

*bSetActive*<br/>
中若要使选项卡成为活动选项卡，则为 TRUE;否则为 FALSE。

*bDetachable*<br/>
中若要使选项卡可分离，则为 TRUE;否则为 FALSE。

### <a name="return-value"></a>返回值

如果已成功将窗格添加为选项卡并且未在进程中销毁，则为 TRUE。 如果要添加的窗格是 `CBaseTabbedPane`类型的对象，则为 FALSE。 有关详细信息，请参见“备注”部分。

### <a name="remarks"></a>备注

调用此方法可将窗格添加为选项卡式窗格上的新选项卡。 如果*pNewBar*指向 `CBaseTabbedPane`类型的对象，则会将其所有选项卡复制到选项卡式窗格，然后*pNewBar*销毁。 因此， *pNewBar*将成为无效指针，不应使用。

##  <a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane：： AllowDestroyEmptyTabbedPane

指定是否可以销毁空的选项卡式窗格。

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>返回值

如果可以销毁空的选项卡式窗格，则为 TRUE;否则为 FALSE。 默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

如果不允许销毁空的选项卡式窗格，框架将改为隐藏该窗格。

##  <a name="applyrestoredtabinfo"></a>CBaseTabbedPane：： ApplyRestoredTabInfo

从注册表加载选项卡设置并将它们应用于选项卡式窗格。

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>parameters

*bUseTabIndexes*<br/>
中此参数由框架在内部使用。

### <a name="remarks"></a>备注

在从注册表重新加载停靠状态信息时，框架会调用此方法。 方法获取有关选项卡式窗格的选项卡顺序和选项卡名称的信息。

##  <a name="canfloat"></a>CBaseTabbedPane：： CanFloat

指定选项卡式窗格是否可以浮动。

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>返回值

如果窗格可以浮动，则为 TRUE;否则为 FALSE。

##  <a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane：： CanSetCaptionTextToTabName

确定选项卡式窗格的标题是否应显示与活动选项卡相同的文本。

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>返回值

如果选项卡式窗格的标题文本设置为活动选项卡的文本，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

方法用于确定选项卡式窗格标题上显示的文本是否复制活动选项卡的标签。可以通过调用[CBaseTabbedPane：： EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)启用或禁用此功能。

##  <a name="converttotabbeddocument"></a>CBaseTabbedPane：： ConvertToTabbedDocument

将一个或多个可停靠的窗格转换为 MDI 选项卡式文档。

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>parameters

*bActiveTabOnly*<br/>
中转换选项卡式窗格时，将指定为 TRUE 以仅转换活动选项卡。指定 FALSE 可转换窗格中的所有选项卡。

##  <a name="detachpane"></a>CBaseTabbedPane：:D etachPane

从选项卡式窗格中分离窗格。

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>parameters

*pBar*<br/>
中指向要分离的窗格的指针。

*bHide*<br/>
中布尔参数，指定框架在分离后是否隐藏窗格。

### <a name="return-value"></a>返回值

如果框架成功分离窗格，则为 TRUE;如果*pBar*为 NULL 或引用不在选项卡式窗格中的窗格，则为 FALSE。

### <a name="remarks"></a>备注

如果可能，框架将浮动分离的窗格。 有关详细信息，请参阅[CBasePane：： CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。

##  <a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane：： EnableSetCaptionTextToTabName

启用或禁用选项卡式窗格与活动选项卡上的标签文本同步标题文本的功能。

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>parameters

*bEnable*<br/>
中若要使选项卡式窗格标题与活动选项卡标题同步，则为 TRUE;否则为 FALSE。

##  <a name="filldefaulttabsorderarray"></a>CBaseTabbedPane：： FillDefaultTabsOrderArray

将内部选项卡顺序还原为默认状态。

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>备注

当框架将 Outlook 栏还原到初始状态时，将调用此方法。

##  <a name="findpanebyid"></a>CBaseTabbedPane：： FindPaneByID

返回由窗格 ID 标识的窗格。

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>parameters

*uBarID*<br/>
中指定要查找的窗格的 ID。

### <a name="return-value"></a>返回值

如果找到该窗格，则为指向它的指针;否则为 NULL。

### <a name="remarks"></a>备注

此方法比较窗格中的所有选项卡，并返回 ID 由*uBarID*参数指定的选项卡。

##  <a name="findbarbytabnumber"></a>CBaseTabbedPane：： FindBarByTabNumber

返回驻留在选项卡中的窗格。

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>parameters

*nTabNum*<br/>
中指定要检索的选项卡的从零开始的索引。

*bGetWrappedBar*<br/>
中若要返回窗格的基础（已包装）窗口而不是窗格本身，则为 TRUE;否则为 FALSE。 这仅适用于从[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)派生的窗格。

### <a name="return-value"></a>返回值

如果找到了窗格，则返回指向正在搜索的窗格的有效指针;否则为 NULL。

### <a name="remarks"></a>备注

调用此方法可检索驻留在由*nTabNum*参数指定的选项卡中的窗格。

##  <a name="floattab"></a>CBaseTabbedPane：： FloatTab

仅当窗格中当前驻留在拆离的选项卡中时浮动窗格。

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>parameters

*pBar*<br/>
[in，out]指向要浮动的窗格的指针。

*nTabID*<br/>
中指定要浮动的选项卡的从零开始的索引。

*dockMethod*<br/>
中指定要用于使窗格浮动的方法。 有关详细信息，请参见“备注”部分。

*bHide*<br/>
中若要在浮动前隐藏窗格，则为 TRUE;否则为 FALSE。

### <a name="return-value"></a>返回值

如果窗格浮动，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

调用此方法以浮动当前驻留在可分离选项卡中的窗格。

如果要以编程方式分离窗格，请为*dockMethod*参数指定 DM_SHOW。 如果希望将窗格置于之前浮动的同一位置，请将 DM_DBL_CLICK 指定为*dockMethod*参数。

##  <a name="getdefaulttabsorder"></a>CBaseTabbedPane：： GetDefaultTabsOrder

返回窗格中选项卡的默认顺序。

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>返回值

一个 `CArray` 对象，该对象指定窗格中选项卡的默认顺序。

### <a name="remarks"></a>备注

当 Outlook 面板重置为初始状态时，框架会调用此方法。

##  <a name="getfirstvisibletab"></a>CBaseTabbedPane：： GetFirstVisibleTab

检索指向第一个显示的选项卡的指针。

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>parameters

*iTabNum*<br/>
中对整数的引用。 此方法将第一个显示的选项卡的从零开始的索引写入此参数，如果未找到任何显示的选项卡，则为-1。

### <a name="return-value"></a>返回值

如果成功，则返回指向第一个显示的选项卡的指针;否则为 NULL。

##  <a name="getminsize"></a>CBaseTabbedPane：： GetMinSize

检索窗格允许的最小大小。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>parameters

size<br/>
弄使用最小允许大小填充的 `CSize` 对象。

### <a name="remarks"></a>备注

如果最小窗格大小的一致性处理处于活动状态（ [CPane：： m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)），则使用活动选项卡的最小允许大小填充*大小*。否则，将使用[CPane：： GetMinSize](../../mfc/reference/cpane-class.md#getminsize)的返回值填充*大小*。

##  <a name="getpaneicon"></a>CBaseTabbedPane：： GetPaneIcon

检索窗格允许的最小大小。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>parameters

size<br/>
弄使用最小允许大小填充的 `CSize` 对象。

### <a name="remarks"></a>备注

如果最小窗格大小的一致性处理处于活动状态（ [CPane：： m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)），则使用活动选项卡的最小允许大小填充*大小*。否则，将使用[CPane：： GetMinSize](../../mfc/reference/cpane-class.md#getminsize)的返回值填充*大小*。

##  <a name="getpanelist"></a>CBaseTabbedPane：： GetPaneList

返回包含在选项卡式窗格中的窗格的列表。

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>parameters

*.lst*<br/>
弄使用选项卡式窗格中包含的窗格填充的 `CObList`。

*pRTCFilter*<br/>
中如果不为 NULL，则返回的列表仅包含指定运行时类的窗格。

##  <a name="gettabarea"></a>CBaseTabbedPane：： GetTabArea

返回 "上" 和 "下" 选项卡区域的边框。

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>parameters

*rectTabAreaTop*<br/>
弄接收上部选项卡区域的屏幕坐标。

*rectTabAreaBottom*<br/>
弄接收下部选项卡区域的屏幕坐标。

### <a name="remarks"></a>备注

调用此方法可确定上方和下方选项卡区域的边框（以屏幕坐标表示）。

##  <a name="gettabsnum"></a>CBaseTabbedPane：： GetTabsNum

返回选项卡窗口中选项卡的计数。

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>返回值

选项卡式窗格中选项卡的数目。

##  <a name="getunderlyingwindow"></a>CBaseTabbedPane：： GetUnderlyingWindow

获取基础（已包装）选项卡窗口。

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>返回值

指向基础选项卡窗口的指针。

##  <a name="getvisibletabsnum"></a>CBaseTabbedPane：： GetVisibleTabsNum

返回可见选项卡的计数。

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>返回值

可见选项卡的数目，将大于或等于零。

### <a name="remarks"></a>备注

调用此方法可确定选项卡式窗格中的可见选项卡的数目。

##  <a name="hasautohidemode"></a>CBaseTabbedPane：： HasAutoHideMode

确定选项卡式窗格是否可以切换为自动隐藏模式。

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>返回值

如果窗格可以切换到自动隐藏模式，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果自动隐藏模式处于禁用状态，则在选项卡式窗格标题上不显示任何 "固定" 按钮。

##  <a name="ishidesingletab"></a>CBaseTabbedPane：： IsHideSingleTab

确定在只显示一个选项卡时是否隐藏选项卡式窗格。

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>返回值

如果在只有一个可见选项卡时未显示 "选项卡" 窗口，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果未显示该窗格是因为只有一个选项卡处于打开状态，则可以调用此方法来确定选项卡式窗格是否正常工作。

##  <a name="removepane"></a>CBaseTabbedPane：： RemovePane

从选项卡式窗格中删除窗格。

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>parameters

*pBar*<br/>
[in，out]指向要从选项卡式窗格中删除的窗格的指针。

### <a name="return-value"></a>返回值

如果已成功从选项卡式窗格中删除窗格，并且选项卡式窗格仍然有效，则为 TRUE。 如果已从选项卡式窗格中删除最后一个窗格，并且选项卡式窗格将被销毁，则为 FALSE。 如果返回值为 FALSE，请不要再使用选项卡式窗格。

### <a name="remarks"></a>备注

调用此方法可从选项卡式窗格中删除由*pBar*参数指定的窗格。

##  <a name="setautodestroy"></a>CBaseTabbedPane：： SetAutoDestroy

确定是否将自动销毁选项卡式控件条。

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>parameters

*bAutoDestroy*<br/>
中如果动态创建了选项卡式窗格并且未控制其生存期，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果动态创建选项卡式窗格，并在未控制其生存期的情况下，请将自动销毁模式设置为 TRUE。 如果自动销毁模式为 TRUE，则框架将自动销毁选项卡式窗格。

##  <a name="showtab"></a>CBaseTabbedPane：： Showtab "

显示或隐藏选项卡。

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>parameters

*pBar*<br/>
中指向要显示或隐藏的窗格的指针。

*bShow*<br/>
中若要显示窗格，则为 TRUE;若要隐藏窗格，则为 FALSE。

*bDelay*<br/>
中如果延迟调整选项卡布局，则为 TRUE;否则为 FALSE。

*bActivate*<br/>
中若要使选项卡成为活动选项卡，则为 TRUE;否则为 FALSE。

### <a name="return-value"></a>返回值

如果选项卡已成功显示或隐藏，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

调用此方法时，将显示或隐藏一个窗格，具体取决于*bShow*参数的值。 如果隐藏某个选项卡，并且它是基础选项卡窗口中的最后一个可见选项卡，则会隐藏选项卡式窗格。 如果在之前没有可见选项卡的情况下显示选项卡，则显示选项卡式窗格。

##  <a name="recalclayout"></a>CBaseTabbedPane：： RecalcLayout

重新计算窗格的布局信息。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>备注

如果该窗格是浮动窗格，则此方法将通知框架将窗格大小调整为最小框架的当前大小。

如果停靠该窗格，则此方法不执行任何操作。

##  <a name="setautohidemode"></a>CBaseTabbedPane：： SetAutoHideMode

在选项卡式窗格中设置可分离窗格的自动隐藏模式。

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>parameters

*bMode*<br/>
中若要启用自动隐藏模式，则为 TRUE;若要启用常规停靠模式，则为 FALSE。

*dwAlignment*<br/>
中指定要创建的自动隐藏窗格的对齐方式。 有关可能值的列表，请参阅[CPane：： MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment)。

*pCurrAutoHideBar*<br/>
[in，out]指向当前自动隐藏工具栏的指针。 可以为 NULL。

*bUseTimer*<br/>
中指定当用户将窗格切换为自动隐藏模式时是否使用自动隐藏效果，或立即隐藏窗格。

### <a name="return-value"></a>返回值

一个指针，指向在切换到自动隐藏模式时创建的自动隐藏工具栏; 如果不创建任何工具栏，则为 NULL。

### <a name="remarks"></a>备注

当用户选择 "固定" 按钮以将选项卡式窗格切换为自动隐藏模式或常规停靠模式时，框架会调用此方法。

为选项卡式窗格中的每个可分离窗格设置自动隐藏模式。 将忽略不可分离的窗格。 有关详细信息，请参阅[CMFCBaseTabCtrl：： EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)。

调用此方法可通过编程方式将选项卡式窗格切换为自动隐藏模式。 窗格必须停靠到主框架窗口（ [CDockablePane：： GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider)必须返回指向[CPaneDivider](../../mfc/reference/cpanedivider-class.md)的有效指针）。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
