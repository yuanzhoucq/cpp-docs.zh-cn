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
ms.openlocfilehash: ce7c48263ed511545757c94d61552e6206e74a00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352860"
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
|[CBaseTabbed窗格：：添加选项卡](#addtab)|将新选项卡添加到选项卡式窗格中。|
|[CBaseTabbed 窗格：：允许销毁空表板窗格](#allowdestroyemptytabbedpane)|指定是否可以销毁空选项卡式窗格。|
|[CBaseTabbed窗格：：应用已还原的选项卡信息](#applyrestoredtabinfo)|将从注册表加载的选项卡设置应用于选项卡式窗格。|
|[CBaseTabbed窗格：：可以浮动](#canfloat)|确定窗格是否可以浮动。 （覆盖[CBasePane：：可以浮动](../../mfc/reference/cbasepane-class.md#canfloat). ）|
|[CBaseTabbed窗格：：可以设置标题文本标签名称](#cansetcaptiontexttotabname)|确定选项卡式窗格的标题是否应显示与活动选项卡相同的文本。|
|[CBaseTabbed窗格：：转换到选项卡文档](#converttotabbeddocument)|（覆盖[可停靠窗格：：转换为 Tabbed 文档](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。）|
|[CBaseTabbedPane：:D埃塔奇帕内](#detachpane)|将一个或多个可停靠窗格转换为 MDI 选项卡式文档。|
|[CBaseTabbed窗格：：启用设置标题文本标签名称](#enablesetcaptiontexttotabname)|启用或禁用选项卡式窗格将标题文本与活动选项卡上的标签文本同步的能力。|
|[CBaseTabbed窗格：：填充默认选项卡顺序数组](#filldefaulttabsorderarray)|将内部选项卡顺序还原为默认状态。|
|[CBaseTabbed窗格：：查找巴比塔号](#findbarbytabnumber)|当选项卡由零基选项卡索引标识时，返回驻留在选项卡中的窗格。|
|||
|[CBaseTabbed窗格：：查找窗格ByID](#findpanebyid)|返回窗格 ID 标识的窗格。|
|[CBaseTabbed窗格：：浮动选项卡](#floattab)|仅当窗格中当前驻留在拆离的选项卡中时浮动窗格。|
|[CBaseTabbed窗格：：获取默认选项卡订单](#getdefaulttabsorder)|返回窗格中的选项卡的默认顺序。|
|[CBaseTabbed窗格：：获取第一个可见点选项卡](#getfirstvisibletab)|检索指向第一个显示的选项卡的指针。|
|[CBaseTabbed窗格：：获取最小尺寸](#getminsize)|检索窗格的最小允许大小。 （覆盖[CPane：获取最小值](../../mfc/reference/cpane-class.md#getminsize)。|
|[CBaseTabbed窗格：：获取窗格图标](#getpaneicon)|将句柄返回到窗格图标。 （覆盖[CBasePane：获取窗格](../../mfc/reference/cbasepane-class.md#getpaneicon).）|
|[CBaseTabbed窗格：：获取窗格列表](#getpanelist)|返回选项卡式窗格中包含的窗格的列表。|
|[CBaseTabbed窗格：：获取塔布区域](#gettabarea)|返回顶部和底部选项卡区域的边界矩形。|
|[CBaseTabbed窗格：：获取TabsNum](#gettabsnum)|返回选项卡窗口中的选项卡计数。|
|[CBaseTabbed窗格：：获取基础窗口](#getunderlyingwindow)|获取基础（包装）选项卡窗口。|
|[CBaseTabbed窗格：：获取可见的TabsNum](#getvisibletabsnum)|返回显示的选项卡的计数。|
|[CBaseTabbed窗格：：具有自动隐藏模式](#hasautohidemode)|确定是否可以将选项卡式窗格切换到自动隐藏模式。|
|[CBaseTabbed窗格：：IsHide单一选项卡](#ishidesingletab)|确定如果只显示一个选项卡，选项卡窗格是否隐藏。|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|在序列化期间在内部使用。|
|[CBaseTabbed窗格：：Recalclayout](#recalclayout)|重新计算窗格的布局信息。 （覆盖[CPane：Recalclayout](../../mfc/reference/cpane-class.md#recalclayout).）|
|[CBaseTabbed 窗格：：删除窗格](#removepane)|从选项卡式窗格中删除窗格。|
|`CBaseTabbedPane::SaveSiblingBarIDs`|在序列化期间在内部使用。|
|`CBaseTabbedPane::Serialize`|（覆盖[可停靠窗格：：序列化](cdockablepane-class.md)。|
|`CBaseTabbedPane::SerializeTabWindow`|在序列化期间在内部使用。|
|[CBaseTabbed窗格：：设置自动销毁](#setautodestroy)|确定 Tabbed 控制栏是否将自动销毁。|
|[CBaseTabbed窗格：：设置自动隐藏模式](#setautohidemode)|在显示模式和自动隐藏模式之间切换停靠窗格。 （覆盖[可停靠窗格：设置自动隐藏模式](../../mfc/reference/cdockablepane-class.md#setautohidemode)。|
|[CBaseTabbed窗格：：显示选项卡](#showtab)|显示或隐藏选项卡。|

## <a name="remarks"></a>备注

此类是抽象类，无法实例化。 它实现各种选项卡式窗格共有的服务。

目前，该库包括两个派生的选项卡式窗格类[：CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)和[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

`CBaseTabbedPane`对象将指针环绕到[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)对象。 [然后，CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)将成为选项卡式窗格的子窗口。

有关如何创建选项卡式窗格的详细信息，请参阅[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)[、CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)和[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[可装窗格](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>要求

**标题：** afxBaseTabbedPane.h

## <a name="cbasetabbedpaneaddtab"></a><a name="addtab"></a>CBaseTabbed窗格：：添加选项卡

将新选项卡添加到选项卡式窗格中。

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>参数

*pNewBar*<br/>
[进出]指向要添加的窗格的指针。 调用此方法后，此指针可能会无效。 有关详细信息，请参见“备注”部分。

*b可见*<br/>
[在]TRUE 使选项卡可见;否则，FALSE。

*bSetActive*<br/>
[在]TRUE 使选项卡成为活动选项卡;否则，FALSE。

*b 可拆卸*<br/>
[在]TRUE 使选项卡可拆卸;否则，FALSE。

### <a name="return-value"></a>返回值

如果窗格已成功添加为选项卡，并且在此过程中未销毁，则为 TRUE。 如果正在添加的窗格是类型`CBaseTabbedPane`的对象，则 FALSE。 有关详细信息，请参见“备注”部分。

### <a name="remarks"></a>备注

调用此方法将窗格添加为选项卡式窗格上的新选项卡。 如果*pNewBar*指向类型`CBaseTabbedPane`的对象，则其所有选项卡都将复制到选项卡式窗格中，然后*pNewBar*被销毁。 因此 *，pNewBar*成为无效的指针，不应使用。

## <a name="cbasetabbedpaneallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CBaseTabbed 窗格：：允许销毁空表板窗格

指定是否可以销毁空选项卡式窗格。

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>返回值

如果可以销毁空选项卡式窗格，则为 TRUE;否则，FALSE。 默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

如果不允许销毁空选项卡式窗格，则框架将隐藏该窗格。

## <a name="cbasetabbedpaneapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a>CBaseTabbed窗格：：应用已还原的选项卡信息

从注册表加载选项卡设置，并将它们应用于选项卡式窗格。

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>参数

*bUseTabIndexs*<br/>
[在]此参数由框架在内部使用。

### <a name="remarks"></a>备注

当框架从注册表重新加载停靠状态信息时，会调用此方法。 该方法获取有关选项卡式窗格的选项卡顺序和选项卡名称的信息。

## <a name="cbasetabbedpanecanfloat"></a><a name="canfloat"></a>CBaseTabbed窗格：：可以浮动

指定选项卡式窗格是否可以浮动。

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>返回值

如果窗格可以浮动，则为 TRUE;否则，FALSE。

## <a name="cbasetabbedpanecansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CBaseTabbed窗格：：可以设置标题文本标签名称

确定选项卡式窗格的标题是否应显示与活动选项卡相同的文本。

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>返回值

如果选项卡式窗格的标题文本设置为活动选项卡的文本，则为 TRUE;如果选项卡式窗格的标题文本设置为活动选项卡的文本，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

该方法用于确定选项卡式窗格标题中显示的文本是否复制活动选项卡的标签。您可以通过调用[CBaseTabbedPane：：启用设置标题文本标签名称](#enablesetcaptiontexttotabname)来启用或禁用此功能。

## <a name="cbasetabbedpaneconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CBaseTabbed窗格：：转换到选项卡文档

将一个或多个可停靠窗格转换为 MDI 选项卡式文档。

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>参数

*b 活动标签*<br/>
[在]转换选项卡式窗格时，指定 TRUE 以仅转换活动选项卡。 指定 FALSE 以转换窗格中的所有选项卡。

## <a name="cbasetabbedpanedetachpane"></a><a name="detachpane"></a>CBaseTabbedPane：:D埃塔奇帕内

从选项卡式窗格分离窗格。

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[在]指向要分离的窗格。

*bHide*<br/>
[在]布尔参数，用于指定框架在分离后是否隐藏窗格。

### <a name="return-value"></a>返回值

如果框架成功分离窗格，则为 TRUE;如果框架成功分离窗格，则为 TRUE。如果*pBar*为 NULL 或引用不在选项卡式窗格中的窗格，则 FALSE。

### <a name="remarks"></a>备注

如果可能，框架将浮动分离的窗格。 有关详细信息，请参阅[CBasePane：：可以浮动](../../mfc/reference/cbasepane-class.md#canfloat)。

## <a name="cbasetabbedpaneenablesetcaptiontexttotabname"></a><a name="enablesetcaptiontexttotabname"></a>CBaseTabbed窗格：：启用设置标题文本标签名称

启用或禁用选项卡式窗格将标题文本与活动选项卡上的标签文本同步的能力。

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 将选项卡式窗格标题与活动选项卡标题同步;否则，FALSE。

## <a name="cbasetabbedpanefilldefaulttabsorderarray"></a><a name="filldefaulttabsorderarray"></a>CBaseTabbed窗格：：填充默认选项卡顺序数组

将内部选项卡顺序还原为默认状态。

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>备注

当框架将 Outlook 栏还原到初始状态时，将调用此方法。

## <a name="cbasetabbedpanefindpanebyid"></a><a name="findpanebyid"></a>CBaseTabbed窗格：：查找窗格ByID

返回窗格 ID 标识的窗格。

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>参数

*乌巴里德*<br/>
[在]指定要查找的窗格的 ID。

### <a name="return-value"></a>返回值

找到窗格的指针;如果找到该窗格，则指向该窗格的指针。否则，NULL。

### <a name="remarks"></a>备注

此方法比较窗格中的所有选项卡，并返回具有*uBarID*参数指定的 ID 的选项卡。

## <a name="cbasetabbedpanefindbarbytabnumber"></a><a name="findbarbytabnumber"></a>CBaseTabbed窗格：：查找巴比塔号

返回驻留在选项卡中的窗格。

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>参数

*nTabNum*<br/>
[在]指定要检索的选项卡的零基索引。

*bGet包装条*<br/>
[在]TRUE 返回窗格的基础（包装）窗口，而不是窗格本身;否则 FALSE。 这仅适用于从[CdockAblePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)派生的窗格。

### <a name="return-value"></a>返回值

如果找到窗格，则返回指向要搜索的窗格的有效指针;如果找到窗格，则会返回该指针。否则，NULL。

### <a name="remarks"></a>备注

调用此方法以检索驻留在*nTabNum*参数指定的选项卡中的窗格。

## <a name="cbasetabbedpanefloattab"></a><a name="floattab"></a>CBaseTabbed窗格：：浮动选项卡

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
[进出]指向窗格的指针以浮动。

*nTabID*<br/>
[在]指定要浮动的选项卡的零基索引。

*基方法*<br/>
[在]指定用于使窗格浮动的方法。 有关详细信息，请参见“备注”部分。

*bHide*<br/>
[在]TRUE 以在浮动前隐藏窗格;否则，FALSE。

### <a name="return-value"></a>返回值

如果窗格浮动，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

调用此方法以浮动当前驻留在可拆卸选项卡中的窗格。

如果要以编程方式分离窗格，请为*dockMethod*参数指定DM_SHOW。 如果要将窗格浮动到以前浮动的相同位置，请指定DM_DBL_CLICK作为*dockMethod*参数。

## <a name="cbasetabbedpanegetdefaulttabsorder"></a><a name="getdefaulttabsorder"></a>CBaseTabbed窗格：：获取默认选项卡订单

返回窗格中的选项卡的默认顺序。

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>返回值

指定`CArray`窗格中选项卡的默认顺序的对象。

### <a name="remarks"></a>备注

当 Outlook 栏重置为初始状态时，框架调用此方法。

## <a name="cbasetabbedpanegetfirstvisibletab"></a><a name="getfirstvisibletab"></a>CBaseTabbed窗格：：获取第一个可见点选项卡

检索指向第一个显示的选项卡的指针。

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>参数

*伊塔布纳姆*<br/>
[在]对整数的引用。 此方法将第一个显示选项卡的零基索引写入此参数，如果没有找到显示的选项卡，则为 -1。

### <a name="return-value"></a>返回值

如果成功，则指向第一个显示选项卡的指针;如果成功，则指向第一个显示的选项卡。否则，NULL。

## <a name="cbasetabbedpanegetminsize"></a><a name="getminsize"></a>CBaseTabbed窗格：：获取最小尺寸

检索窗格的最小允许大小。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>参数

*大小*<br/>
[出]以`CSize`最小允许大小填充的对象。

### <a name="remarks"></a>备注

如果最小窗格大小的一致处理处于活动状态[（CPane：：m_bHandleMinSize），](../../mfc/reference/cpane-class.md#m_bhandleminsize)*则大小*将填充活动选项卡的最小允许大小。否则，*大小*将填充[CPane：getMinSize](../../mfc/reference/cpane-class.md#getminsize)的返回值。

## <a name="cbasetabbedpanegetpaneicon"></a><a name="getpaneicon"></a>CBaseTabbed窗格：：获取窗格图标

检索窗格的最小允许大小。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>参数

*大小*<br/>
[出]以`CSize`最小允许大小填充的对象。

### <a name="remarks"></a>备注

如果最小窗格大小的一致处理处于活动状态[（CPane：：m_bHandleMinSize），](../../mfc/reference/cpane-class.md#m_bhandleminsize)*则大小*将填充活动选项卡的最小允许大小。否则，*大小*将填充[CPane：getMinSize](../../mfc/reference/cpane-class.md#getminsize)的返回值。

## <a name="cbasetabbedpanegetpanelist"></a><a name="getpanelist"></a>CBaseTabbed窗格：：获取窗格列表

返回选项卡式窗格中包含的窗格的列表。

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>参数

*Lst*<br/>
[出]`CObList`填充选项卡式窗格中的窗格。

*pRTC过滤器*<br/>
[在]如果它不是 NULL，则返回的列表仅包含指定运行时类的窗格。

## <a name="cbasetabbedpanegettabarea"></a><a name="gettabarea"></a>CBaseTabbed窗格：：获取塔布区域

返回顶部和底部选项卡区域的边界矩形。

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>参数

*rectTabAreaTop*<br/>
[出]接收上部选项卡区域的屏幕坐标。

*rectTab区域底部*<br/>
[出]接收下部选项卡区域的屏幕坐标。

### <a name="remarks"></a>备注

调用此方法以确定上部和下部选项卡区域在屏幕坐标中的边界矩形。

## <a name="cbasetabbedpanegettabsnum"></a><a name="gettabsnum"></a>CBaseTabbed窗格：：获取TabsNum

返回选项卡窗口中的选项卡计数。

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>返回值

选项卡式窗格中的选项卡数。

## <a name="cbasetabbedpanegetunderlyingwindow"></a><a name="getunderlyingwindow"></a>CBaseTabbed窗格：：获取基础窗口

获取基础（包装）选项卡窗口。

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>返回值

指向基础选项卡窗口的指针。

## <a name="cbasetabbedpanegetvisibletabsnum"></a><a name="getvisibletabsnum"></a>CBaseTabbed窗格：：获取可见的TabsNum

返回可见选项卡的计数。

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>返回值

可见选项卡的数量，该选项卡大于或等于零。

### <a name="remarks"></a>备注

调用此方法以确定选项卡式窗格中的可见选项卡数。

## <a name="cbasetabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CBaseTabbed窗格：：具有自动隐藏模式

确定选项卡式窗格是否可以切换为自动隐藏模式。

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>返回值

如果窗格可以切换到自动隐藏模式，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

如果禁用自动隐藏模式，则选项卡式窗格标题上不显示引脚按钮。

## <a name="cbasetabbedpaneishidesingletab"></a><a name="ishidesingletab"></a>CBaseTabbed窗格：：IsHide单一选项卡

确定如果只显示一个选项卡，选项卡窗格是否隐藏。

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>返回值

如果选项卡窗口在只有一个可见选项卡时未显示，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

如果未显示窗格，因为只有一个选项卡处于打开状态，则可以调用此方法以确定选项卡式窗格是否正常工作。

## <a name="cbasetabbedpaneremovepane"></a><a name="removepane"></a>CBaseTabbed 窗格：：删除窗格

从选项卡式窗格中删除窗格。

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[进出]指向窗格的指针，用于从选项卡式窗格中删除。

### <a name="return-value"></a>返回值

如果窗格已成功从选项卡式窗格中删除，并且选项卡式窗格仍然有效，则为 TRUE。 如果最后一个窗格已从选项卡式窗格中删除，并且选项卡式窗格即将销毁，则 FALSE。 如果返回值为 FALSE，则不要再使用选项卡式窗格。

### <a name="remarks"></a>备注

调用此方法从选项卡式窗格中删除*pBar*参数指定的窗格。

## <a name="cbasetabbedpanesetautodestroy"></a><a name="setautodestroy"></a>CBaseTabbed窗格：：设置自动销毁

确定 Tabbed 控制栏是否将自动销毁。

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*bAuto销毁*<br/>
[在]如果选项卡式窗格是动态创建的，并且您不控制其生存期，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

如果动态创建选项卡式窗格，并且未控制其生存期，则将自动销毁模式设置为 TRUE。 如果自动销毁模式为 TRUE，则框架将自动销毁选项卡式窗格。

## <a name="cbasetabbedpaneshowtab"></a><a name="showtab"></a>CBaseTabbed窗格：：显示选项卡

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
[在]指向要显示或隐藏窗格的指针。

*b显示*<br/>
[在]TRUE 以显示窗格;FALSE 以隐藏窗格。

*bDelay*<br/>
[在]TRUE 以延迟选项卡布局的调整;否则，FALSE。

*b 激活*<br/>
[在]TRUE 使选项卡成为活动选项卡;否则，FALSE。

### <a name="return-value"></a>返回值

如果选项卡已显示或已成功隐藏，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

调用此方法时，会显示或隐藏窗格，具体取决于*bShow*参数的值。 如果隐藏选项卡，并且它是基础选项卡窗口中的最后一个可见选项卡，则选项卡式窗格将隐藏。 如果在以前没有可见的选项卡时显示选项卡，将显示选项卡式窗格。

## <a name="cbasetabbedpanerecalclayout"></a><a name="recalclayout"></a>CBaseTabbed窗格：：Recalclayout

重新计算窗格的布局信息。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>备注

如果窗格是浮动的，此方法会通知框架将窗格的大小调整到小型框架的当前大小。

如果窗格已停靠，则此方法不执行任何操作。

## <a name="cbasetabbedpanesetautohidemode"></a><a name="setautohidemode"></a>CBaseTabbed窗格：：设置自动隐藏模式

设置选项卡式窗格中可拆卸窗格的自动隐藏模式。

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>参数

*bMode*<br/>
[在]TRUE 以启用自动隐藏模式;FALSE 以启用常规停靠模式。

*dwalignment*<br/>
[在]指定要创建的自动隐藏窗格的对齐方式。 有关可能值的列表，请参阅[CPane：：移动。](../../mfc/reference/cpane-class.md#movebyalignment)

*pCurrAutoHidebar*<br/>
[进出]指向当前自动隐藏工具栏的指针。 可以为 NULL。

*bUseTimer*<br/>
[在]指定用户将窗格切换到自动隐藏模式时是否使用自动隐藏效果，还是立即隐藏窗格。

### <a name="return-value"></a>返回值

切换到自动隐藏模式时创建的指向自动隐藏工具栏的指针;如果未创建工具栏，则指向 NULL。

### <a name="remarks"></a>备注

当用户选择按键按钮将选项卡式窗格切换到自动隐藏模式或常规停靠模式时，框架将调用此方法。

为选项卡式窗格中的每个可拆卸窗格设置自动隐藏模式。 不可拆卸的窗格将被忽略。 有关详细信息，请参阅[CMFCBaseTabCtrl：：启用Tabdetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)。

调用此方法以编程方式将选项卡式窗格切换到自动隐藏模式。 窗格必须停靠到主框架窗口[（CDockablePane：：GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider)必须返回指向[CPaneDivider](../../mfc/reference/cpanedivider-class.md)的有效指针）。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
