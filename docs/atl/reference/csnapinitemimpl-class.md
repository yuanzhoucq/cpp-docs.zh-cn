---
title: CSnapInItemImpl 类
ms.date: 11/04/2016
f1_keywords:
- CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::AddMenuItems
- ATLSNAP/ATL::CSnapInItemImpl::Command
- ATLSNAP/ATL::CSnapInItemImpl::CreatePropertyPages
- ATLSNAP/ATL::CSnapInItemImpl::FillData
- ATLSNAP/ATL::CSnapInItemImpl::GetResultPaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::GetResultViewType
- ATLSNAP/ATL::CSnapInItemImpl::GetScopePaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::Notify
- ATLSNAP/ATL::CSnapInItemImpl::QueryPagesFor
- ATLSNAP/ATL::CSnapInItemImpl::SetMenuInsertionFlags
- ATLSNAP/ATL::CSnapInItemImpl::SetToolbarButtonInfo
- ATLSNAP/ATL::CSnapInItemImpl::UpdateMenuState
- ATLSNAP/ATL::CSnapInItemImpl::UpdateToolbarButton
- ATLSNAP/ATL::CSnapInItemImpl::m_bstrDisplayName
- ATLSNAP/ATL::CSnapInItemImpl::m_resultDataItem
- ATLSNAP/ATL::CSnapInItemImpl::m_scopeDataItem
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
ms.openlocfilehash: 1e4f98dabd2d27b21dbe3e197f32e27ccca9d2d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330718"
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl 类

此类提供了实现入网节点对象的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`CSnapInItemImpl`。

*bIs 扩展*<br/>
如果对象是卡入扩展，则为 TRUE;如果对象是卡入扩展。否则 FALSE。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[快照项目：：卡内普内项目](#csnapinitemimpl)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[快照项目：：添加菜单项](#addmenuitems)|将菜单项添加到上下文菜单。|
|[快照项目：：命令](#command)|选择自定义菜单项时，控制台调用。|
|[快照项目：：创建属性页](#createpropertypages)|将页面添加到管理单元的属性表。|
|[快照项目：：填充数据](#filldata)|将管理单元对象上的信息复制到指定的流中。|
|[快照项目：：获取结果窗格信息](#getresultpaneinfo)|检索卡入`RESULTDATAITEM`的结构。|
|[快照项目：：获取结果视图类型](#getresultviewtype)|确定结果窗格使用的视图类型。|
|[快照项目：：获取ScopePane信息](#getscopepaneinfo)|检索卡入`SCOPEDATAITEM`的结构。|
|[快照项目：：通知](#notify)|由控制台调用以通知用户执行的操作的卡入。|
|[快照项目：：查询页面](#querypagesfor)|已调用以查看管理单元节点是否支持属性页。|
|[快照项目：：设置Menu插入标记](#setmenuinsertionflags)|修改插入对象的菜单插入标志。|
|[快照项目：：设置工具栏按钮信息](#settoolbarbuttoninfo)|设置指定工具栏按钮的信息。|
|[快照项目：：更新菜单状态](#updatemenustate)|更新上下文菜单项的状态。|
|[快照项目：：更新工具栏按钮](#updatetoolbarbutton)|更新指定工具栏按钮的状态。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[快照项目：：m_bstrDisplayName](#m_bstrdisplayname)|卡入对象的名称。|
|[快照项目：：m_resultDataItem](#m_resultdataitem)|`CSnapInItemImpl`对象使用的 Windows`RESULTDATAITEM`结构。|
|[快照项目：：m_scopeDataItem](#m_scopedataitem)|`CSnapInItemImpl`对象使用的 Windows`SCOPEDATAITEM`结构。|

## <a name="remarks"></a>备注

`CSnapInItemImpl`为入卡节点对象提供了基本实现，例如添加菜单项和工具栏，以及将入卡节点的命令转发到相应的处理程序函数。 这些要素使用几个不同的接口和映射类型实现。 默认实现通过确定派生类的正确实例，然后将消息转发到正确的实例来处理发送到节点对象的通知。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>要求

**标题：** atlsnap.h

## <a name="csnapinitemimpladdmenuitems"></a><a name="addmenuitems"></a>快照项目：：添加菜单项

此方法实现 Win32 函数[IExtendContextMenu：：addMenuitem](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems)。

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>参数

*皮卡背*<br/>
[在]指向 可以`IContextMenuCallback`向上下文菜单添加项的 的 指针。

*p 允许插入*<br/>
[进出]标识可以使用的 Microsoft 管理控制台 （MMC） 定义的菜单项插入点。 这可以是以下标志的组合：

- CCM_INSERTIONALLOWED_TOP项可以插入到上下文菜单的顶部。

- CCM_INSERTIONALLOWED_NEW项可以插入到"创建新"子菜单中。

- CCM_INSERTIONALLOWED_TASK项可以插入到任务子菜单中。

- CCM_INSERTIONALLOWED_VIEW项可以插入工具栏视图菜单或结果窗格上下文菜单的"查看子菜单"。

*type*<br/>
[在]指定对象的类型。 可以具有以下一个值：

- CCT_SCOPE范围窗格上下文的数据对象。

- CCT_RESULT结果窗格上下文的数据对象。

- CCT_SNAPIN_MANAGER用于管理单元上下文的数据对象。

- CCT_UNINITIALIZED数据对象的类型无效。

## <a name="csnapinitemimplcommand"></a><a name="command"></a>快照项目：：命令

此方法实现 Win32 函数[IExtendContextMenu：：命令](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command)。

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>参数

*lCommandID*<br/>
[在]指定菜单项的命令标识符。

*type*<br/>
[在]指定对象的类型。 可以具有以下一个值：

- CCT_SCOPE范围窗格上下文的数据对象。

- CCT_RESULT结果窗格上下文的数据对象。

- CCT_SNAPIN_MANAGER用于管理单元上下文的数据对象。

- CCT_UNINITIALIZED数据对象的类型无效。

## <a name="csnapinitemimplcreatepropertypages"></a><a name="createpropertypages"></a>快照项目：：创建属性页

此方法实现 Win32 函数[IExtend属性表：：创建属性页](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2)。

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>参数

*lpProvider*<br/>
[在]指向接口的`IPropertySheetCallback`指针。

*处理*<br/>
[在]指定用于将MMCN_PROPERTY_CHANGE通知消息路由到相应数据类的句柄。

*朋 克*<br/>
[在]指向对象上的`IExtendPropertySheet`接口的指针，该接口包含有关节点的上下文信息。

*type*<br/>
[在]指定对象的类型。 可以具有以下一个值：

- CCT_SCOPE范围窗格上下文的数据对象。

- CCT_RESULT结果窗格上下文的数据对象。

- CCT_SNAPIN_MANAGER用于管理单元上下文的数据对象。

- CCT_UNINITIALIZED数据对象的类型无效。

## <a name="csnapinitemimplcsnapinitemimpl"></a><a name="csnapinitemimpl"></a>快照项目：：卡内普内项目

构造 `CSnapInItemImpl` 对象。

```
CSnapInItemImpl();
```

## <a name="csnapinitemimplfilldata"></a><a name="filldata"></a>快照项目：：填充数据

调用此函数是为了检索有关项的信息。

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>参数

*Cf*<br/>
[在]剪贴板的格式（文本、富文本或带有 OLE 项的富文本）。

*pStream*<br/>
[在]指向包含对象数据的流的指针。

### <a name="remarks"></a>备注

要正确实现此功能，请根据*cf*指示的剪贴板格式将正确的信息复制到流 *（pStream）* 中。

## <a name="csnapinitemimplgetresultviewtype"></a><a name="getresultviewtype"></a>快照项目：：获取结果视图类型

调用此函数以检索管理单元对象的结果窗格的视图类型。

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>参数

*ppView类型*<br/>
[出]指向返回视图类型的地址。

*p查看选项*<br/>
[出]指向MMC_VIEW_OPTIONS枚举的指针，该枚举为控制台提供由所属管理单元指定的选项。 此值可以为下列值之一：

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x0000001 告诉控制台不要在 **"视图"** 菜单中显示标准列表视图选项。 允许管理单元仅在结果视图窗格中显示其自己的自定义视图。 这是此时定义的唯一选项标志。

- MMC_VIEW_OPTIONS_NONE = 0 允许默认视图选项。

## <a name="csnapinitemimplgetscopepaneinfo"></a><a name="getscopepaneinfo"></a>快照项目：：获取ScopePane信息

调用此函数以检索管理`SCOPEDATAITEM`单元的结构。

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>参数

*pScope数据项目*<br/>
[出]指向对象`SCOPEDATAITEM`结构的`CSnapInItemImpl`指针。

## <a name="csnapinitemimplgetresultpaneinfo"></a><a name="getresultpaneinfo"></a>快照项目：：获取结果窗格信息

调用此函数以检索管理`RESULTDATAITEM`单元的结构。

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>参数

*pResult数据项目*<br/>
[出]指向对象`RESULTDATAITEM`结构的`CSnapInItemImpl`指针。

## <a name="csnapinitemimplm_bstrdisplayname"></a><a name="m_bstrdisplayname"></a>快照项目：：m_bstrDisplayName

包含为节点项显示的字符串。

```
CComBSTR m_bstrDisplayName;
```

## <a name="csnapinitemimplm_scopedataitem"></a><a name="m_scopedataitem"></a>快照项目：：m_scopeDataItem

卡`SCOPEDATAITEM`入数据对象的结构。

```
SCOPEDATAITEM m_scopeDataItem;
```

## <a name="csnapinitemimplm_resultdataitem"></a><a name="m_resultdataitem"></a>快照项目：：m_resultDataItem

入卡数据对象的[RESULTDATAITEM](/windows/win32/api/mmc/ns-mmc-resultdataitem)结构。

```
RESULTDATAITEM m_resultDataItem;
```

## <a name="csnapinitemimplnotify"></a><a name="notify"></a>快照项目：：通知

当用户对卡入对象执行操作时调用。

```
STDMETHOD(Notify)(
    MMC_NOTIFY_TYPE event,
    long arg,
    long param,
    IComponentData* pComponentData,
    IComponent* pComponent,
    DATA_OBJECT_TYPES type) = 0;
```

### <a name="parameters"></a>参数

*event*<br/>
[在]标识用户执行的操作。 以下通知是可能的：

- MMCN_ACTIVATE激活和停用窗口时已发送。

- MMCN_ADD_IMAGES已发送以将图像添加到结果窗格。

- MMCN_BTN_CLICK当用户单击其中一个工具栏按钮时已发送。

- MMCN_CLICK当用户单击列表视图项目上的鼠标按钮时已发送。

- 当用户双击列表视图项目上的鼠标按钮时，MMCN_DBLCLICK已发送。

- MMCN_DELETE 已发送通知管理单元该对象应删除。

- MMCN_EXPAND文件夹需要展开或收缩时已发送。

- MMCN_MINIMIZED窗口最小化或最大化时发送。

- MMCN_PROPERTY_CHANGE已发送通知卡入对象，即卡入对象的视图即将更改。

- MMCN_REMOVE_CHILDREN当管理单元必须删除它在指定节点下方添加的整个子树时，已发送。

- MMCN_RENAME 首次发送用于查询重命名，第二次进行重命名。

- MMCN_SELECT在选择范围或结果视图窗格中的项时已发送。

- MMCN_SHOW首次选择或取消选择示波器项时已发送。

- MMCN_VIEW_CHANGE在发生更改时，当管理单元可以更新所有视图时，已发送。

*精 氨 酸*<br/>
[在]取决于通知类型。

*参数*<br/>
[在]取决于通知类型。

*p组件数据*<br/>
[出]指向实现`IComponentData`的对象的指针。 如果未从`IComponentData::Notify`转发通知，则此参数为 NULL。

*p组件*<br/>
[出]指向实现`IComponent`的对象的指针。 如果未从`IComponent::Notify`转发通知，则此参数为 NULL。

*type*<br/>
[在]指定对象的类型。 可以具有以下一个值：

- CCT_SCOPE范围窗格上下文的数据对象。

- CCT_RESULT结果窗格上下文的数据对象。

- CCT_SNAPIN_MANAGER用于管理单元上下文的数据对象。

- CCT_UNINITIALIZED数据对象的类型无效。

## <a name="csnapinitemimplquerypagesfor"></a><a name="querypagesfor"></a>快照项目：：查询页面

已调用以查看管理单元节点是否支持属性页。

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

## <a name="csnapinitemimplsetmenuinsertionflags"></a><a name="setmenuinsertionflags"></a>快照项目：：设置Menu插入标记

调用此函数以修改插入对象（由*p插入允许*）指定的菜单插入标志。

```
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>参数

*b 插入前*<br/>
[在]在将项添加到上下文菜单之前调用函数时，应不为零;否则 0。

*p 允许插入*<br/>
[进出]标识可以使用的 Microsoft 管理控制台 （MMC） 定义的菜单项插入点。 这可以是以下标志的组合：

- CCM_INSERTIONALLOWED_TOP项可以插入到上下文菜单的顶部。

- CCM_INSERTIONALLOWED_NEW项可以插入到"创建新"子菜单中。

- CCM_INSERTIONALLOWED_TASK项可以插入到任务子菜单中。

- CCM_INSERTIONALLOWED_VIEW项可以插入工具栏视图菜单或结果窗格上下文菜单的"查看子菜单"。

### <a name="remarks"></a>备注

如果要开发主插入，可以重置任何插入标志，以限制第三方扩展可以添加的菜单项类型。 例如，主管理单元可以清除CCM_INSERTIONALLOWED_NEW标志，以防止扩展添加自己的"创建新"菜单项。

不应尝试在 p*插入中*设置最初清除的位。 MMC 的未来版本可能使用当前未定义的位，因此不应更改当前未定义的位。

## <a name="csnapinitemimplsettoolbarbuttoninfo"></a><a name="settoolbarbuttoninfo"></a>快照项目：：设置工具栏按钮信息

调用此函数以在创建工具栏之前修改卡入对象的任何工具栏按钮样式。

```
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>参数

*id*<br/>
[在]要设置的工具栏按钮的 ID。

*fsState*<br/>
[在]按钮的状态标志。 可以是以下一种或多项：

- TBSTATE_CHECKED 按钮具有TBSTYLE_CHECKED样式，正在按下。

- TBSTATE_ENABLED 该按钮接受用户输入。 没有此状态的按钮不接受用户输入，并且为灰色。

- TBSTATE_HIDDEN 该按钮不可见，无法接收用户输入。

- TBSTATE_INDETERMINATE 该按钮为灰色。

- TBSTATE_PRESSED 按下按钮。

- TBSTATE_WRAP按钮后面的换行符。 该按钮还必须具有TBSTATE_ENABLED。

*fsType*<br/>
[在]按钮的状态标志。 可以是以下一种或多项：

- TBSTYLE_BUTTON 创建标准按钮。

- TBSTYLE_CHECK 创建一个按钮，每次用户单击按下状态和非按下状态之间切换。 当按钮处于按下状态时，其背景颜色不同。

- TBSTYLE_CHECKGROUP 创建一个检查按钮，直到按下组中的另一个按钮。

- TBSTYLE_GROUP 创建一个按钮，直到按下组中的另一个按钮。

- TBSTYLE_SEP 创建分隔符，在按钮组之间提供一个小间隙。 具有此样式的按钮不会接收用户输入。

## <a name="csnapinitemimplupdatemenustate"></a><a name="updatemenustate"></a>快照项目：：更新菜单状态

调用此函数以在菜单项插入到卡入对象的上下文菜单之前对其进行修改。

```
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>参数

*id*<br/>
[在]要设置的菜单项的 ID。

*普布夫*<br/>
[在]要更新的菜单项的字符串的指针。

*标志*<br/>
[在]指定新的状态标志。 这可以是以下标志的组合：

- MF_POPUP指定这是上下文菜单中的子菜单。 菜单项、插入点和进一步子菜单可以使用其`lCommandID`作为`IInsertionPointID`添加到此子菜单。

- MF_BITMAP和MF_OWNERDRAW这些标志是不允许的，并且将导致返回值E_INVALIDARG。

- MF_SEPARATOR绘制水平分界线。 只允许`IContextMenuProvider`添加设置MF_SEPARATOR菜单项。

- MF_CHECKED在菜单项旁边放置复选标记。

- MF_DISABLED禁用菜单项，因此无法选择，但标志不会将其灰暗。

- MF_ENABLED 启用菜单项以便可以选择，将其从灰状态还原。

- MF_GRAYED禁用菜单项，使其变灰，使其无法选择。

- MF_MENUBARBREAK 功能与菜单栏的MF_MENUBREAK标志相同。 对于下拉菜单、子菜单或快捷菜单，新列由垂直线与旧列分隔。

- MF_MENUBREAK将项目放在新行（菜单栏）或新列（对于下拉菜单、子菜单或快捷菜单）中，而不分隔列。

- MF_UNCHECKED不会在项目旁边放置复选标记（默认值）。

以下标志组不能一起使用：

- MF_DISABLED、MF_ENABLED和MF_GRAYED。

- MF_MENUBARBREAK和MF_MENUBREAK。

- MF_CHECKED和MF_UNCHECKED。

## <a name="csnapinitemimplupdatetoolbarbutton"></a><a name="updatetoolbarbutton"></a>快照项目：：更新工具栏按钮

调用此函数以在显示卡入对象之前修改该按钮的工具栏按钮。

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>参数

*id*<br/>
指定要更新的工具栏按钮的按钮 ID。

*fsState*<br/>
指定工具栏按钮状态。 如果要设置此状态，则返回 TRUE。 这可以是以下标志的组合：

- 启用 该按钮接受用户输入。 没有此状态的按钮不接受用户输入，并且为灰色。

- 正在按下的"检查"按钮具有"检查"样式。

- 隐藏 该按钮不可见，无法接收用户输入。

- 不确定 按钮为灰色。

- 按钮按下按钮。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
