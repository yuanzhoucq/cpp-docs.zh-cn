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
ms.openlocfilehash: 27f3e8a17a9538a72a6592177a88a9b415b1a27c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297798"
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl 类

此类提供用于实现管理单元中节点对象的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`CSnapInItemImpl`。

*bIsExtension*<br/>
如果对象是一个管理单元扩展; 则为 TRUE否则为 FALSE。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|将菜单项添加到上下文菜单。|
|[CSnapInItemImpl::Command](#command)|当选择了自定义菜单项时，由控制台调用。|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|将页添加到管理单元的属性表。|
|[CSnapInItemImpl::FillData](#filldata)|复制到指定流中管理单元中对象的信息。|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|检索`RESULTDATAITEM`的管理单元中的结构。|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|确定使用结果窗格视图的类型。|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|检索`SCOPEDATAITEM`的管理单元中的结构。|
|[CSnapInItemImpl::Notify](#notify)|由控制台的管理单元中的用户执行的操作的通知调用。|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|调用以查看管理单元中节点是否支持属性页。|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|修改管理单元中对象的菜单插入标志。|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|设置指定的工具栏按钮的信息。|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|更新一个上下文菜单项的状态。|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|更新指定的工具栏按钮的状态。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|管理单元中对象的名称。|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Windows`RESULTDATAITEM`结构，可由`CSnapInItemImpl`对象。|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Windows`SCOPEDATAITEM`结构，可由`CSnapInItemImpl`对象。|

## <a name="remarks"></a>备注

`CSnapInItemImpl` 提供了管理单元中节点对象，如添加菜单项和工具栏，以及在转发到相应的处理程序函数的管理单元节点的命令的基本实现。 这些功能使用多个不同的接口实现，并将类型映射。 默认实现处理通知发送到的节点对象，方法是确定正确的派生类实例，然后将消息转发到正确的实例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>要求

**标头：** atlsnap.h

##  <a name="addmenuitems"></a>  CSnapInItemImpl::AddMenuItems

此方法实现的 Win32 函数[IExtendContextMenu::AddMenuItems](/windows/desktop/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems)。

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>参数

*piCallback*<br/>
[in]指向`IContextMenuCallback`，可以将项添加到上下文菜单。

*pInsertionAllowed*<br/>
[in、 out]标识 Microsoft 管理控制台 MMC 定义菜单项的插入点，可以使用。 这可以是下列标志的组合：

- 可以在上下文菜单的顶部插入 CCM_INSERTIONALLOWED_TOP 项。

- 创建新的子菜单中，可以插入 CCM_INSERTIONALLOWED_NEW 项。

- 可以在任务子菜单中插入 CCM_INSERTIONALLOWED_TASK 项。

- 在工具栏上的视图菜单中或在结果窗格上下文菜单的视图子菜单中，可以插入 CCM_INSERTIONALLOWED_VIEW 项。

*type*<br/>
[in]指定的对象的类型。 它可以具有以下值之一：

- 作用域窗格上下文的 CCT_SCOPE 数据对象。

- 结果窗格中上下文的 CCT_RESULT 数据对象。

- CCT_SNAPIN_MANAGER 数据管理器管理单元中上下文的对象。

- CCT_UNINITIALIZED 数据对象具有无效的类型。

##  <a name="command"></a>  CSnapInItemImpl::Command

此方法实现的 Win32 函数[IExtendContextMenu::Command](/windows/desktop/api/mmc/nf-mmc-iextendcontextmenu-command)。

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>参数

*lCommandID*<br/>
[in]指定菜单项的命令标识符。

*type*<br/>
[in]指定的对象的类型。 它可以具有以下值之一：

- 作用域窗格上下文的 CCT_SCOPE 数据对象。

- 结果窗格中上下文的 CCT_RESULT 数据对象。

- CCT_SNAPIN_MANAGER 数据管理器管理单元中上下文的对象。

- CCT_UNINITIALIZED 数据对象具有无效的类型。

##  <a name="createpropertypages"></a>  CSnapInItemImpl::CreatePropertyPages

此方法实现的 Win32 函数[IExtendPropertySheet::CreatePropertyPages](/windows/desktop/api/mmc/nn-mmc-iextendpropertysheet2)。

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>参数

*lpProvider*<br/>
[in]指向`IPropertySheetCallback`接口。

*handle*<br/>
[in]指定用于 MMCN_PROPERTY_CHANGE 通知消息路由到相应的数据类的句柄。

*pUnk*<br/>
[in]指向`IExtendPropertySheet`上包含的节点的上下文信息的对象的接口。

*type*<br/>
[in]指定的对象的类型。 它可以具有以下值之一：

- 作用域窗格上下文的 CCT_SCOPE 数据对象。

- 结果窗格中上下文的 CCT_RESULT 数据对象。

- CCT_SNAPIN_MANAGER 数据管理器管理单元中上下文的对象。

- CCT_UNINITIALIZED 数据对象具有无效的类型。

##  <a name="csnapinitemimpl"></a>  CSnapInItemImpl::CSnapInItemImpl

构造 `CSnapInItemImpl` 对象。

```
CSnapInItemImpl();
```

##  <a name="filldata"></a>  CSnapInItemImpl::FillData

此函数调用以检索有关项目的信息。

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>参数

*cf*<br/>
[in]剪贴板格式 （文本、 格式文本或与 OLE 项的多格式文本）。

*pStream*<br/>
[in]指向包含对象数据的流的指针。

### <a name="remarks"></a>备注

若要正确实现此函数，请将正确的信息复制到流 (*pStream*)，具体指示的剪贴板格式取决于*cf*。

##  <a name="getresultviewtype"></a>  CSnapInItemImpl::GetResultViewType

调用此函数可检索管理单元中对象的结果窗格中的视图的类型。

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>参数

*ppViewType*<br/>
[out]指向返回的视图类型的地址。

*pViewOptions*<br/>
[out]指向 MMC_VIEW_OPTIONS 枚举为控制台提供了由拥有管理单元指定的选项。 此值可以是以下值之一：

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 指示控制台以避免在演示中的标准列表视图选择**视图**菜单。 允许的管理单元仅在结果视图窗格中显示其自己的自定义视图。 这是在此时间定义的唯一选项标志。

- MMC_VIEW_OPTIONS_NONE = 0 允许默认视图选项。

##  <a name="getscopepaneinfo"></a>  CSnapInItemImpl::GetScopePaneInfo

调用此函数可检索`SCOPEDATAITEM`的管理单元中的结构。

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>参数

*pScopeDataItem*<br/>
[out]一个指向`SCOPEDATAITEM`结构的`CSnapInItemImpl`对象。

##  <a name="getresultpaneinfo"></a>  CSnapInItemImpl::GetResultPaneInfo

调用此函数可检索`RESULTDATAITEM`的管理单元中的结构。

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>参数

*pResultDataItem*<br/>
[out]一个指向`RESULTDATAITEM`结构的`CSnapInItemImpl`对象。

##  <a name="m_bstrdisplayname"></a>  CSnapInItemImpl::m_bstrDisplayName

包含节点项显示的字符串。

```
CComBSTR m_bstrDisplayName;
```

##  <a name="m_scopedataitem"></a>  CSnapInItemImpl::m_scopeDataItem

`SCOPEDATAITEM`管理单元中的数据对象的结构。

```
SCOPEDATAITEM m_scopeDataItem;
```

##  <a name="m_resultdataitem"></a>  CSnapInItemImpl::m_resultDataItem

[RESULTDATAITEM](/windows/desktop/api/mmc/ns-mmc-resultdataitem)管理单元中的数据对象的结构。

```
RESULTDATAITEM m_resultDataItem;
```

##  <a name="notify"></a>  CSnapInItemImpl::Notify

当在由用户执行的管理单元中对象时调用。

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
[in]标识用户所执行的操作。 可能会出现以下通知：

- MMCN_ACTIVATE 发送是一个窗口时激活和停用。

- MMCN_ADD_IMAGES 发送，以将图像添加到结果窗格。

- 当用户单击其中一个工具栏按钮时发送 MMCN_BTN_CLICK。

- 当用户单击鼠标按钮在列表视图项上的时，将发送 MMCN_CLICK。

- 当用户双击鼠标按钮在列表视图项上的时，将发送 MMCN_DBLCLICK。

- MMCN_DELETE 发送通知的管理单元，该对象应删除。

- MMCN_EXPAND 发送文件夹需要增加或减少时。

- MMCN_MINIMIZED 发送是一个窗口时最小化或最大化。

- MMCN_PROPERTY_CHANGE 发送通知即将更改管理单元中对象的视图的管理单元对象。

- MMCN_REMOVE_CHILDREN 发送管理单元中，则必须删除整个子树时它已添加了以下指定的节点。

- MMCN_RENAME 发送第一次重命名查询和第二次执行重命名。

- MMCN_SELECT 发送时的作用域或结果视图窗格中的项处于选中状态。

- MMCN_SHOW 发送时的作用域项是选择或取消选择第一次。

- 当管理单元中时，可以更新所有视图发生更改时发送 MMCN_VIEW_CHANGE。

*arg*<br/>
[in]取决于通知类型。

*param*<br/>
[in]取决于通知类型。

*pComponentData*<br/>
[out]指向对象实现的指针`IComponentData`。 此参数为 NULL，如果不从转发通知`IComponentData::Notify`。

*pComponent*<br/>
[out]指向实现的对象的指针`IComponent`。 此参数为 NULL，如果不从转发通知`IComponent::Notify`。

*type*<br/>
[in]指定的对象的类型。 它可以具有以下值之一：

- 作用域窗格上下文的 CCT_SCOPE 数据对象。

- 结果窗格中上下文的 CCT_RESULT 数据对象。

- CCT_SNAPIN_MANAGER 数据管理器管理单元中上下文的对象。

- CCT_UNINITIALIZED 数据对象具有无效的类型。

##  <a name="querypagesfor"></a>  CSnapInItemImpl::QueryPagesFor

调用以查看管理单元中节点是否支持属性页。

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

##  <a name="setmenuinsertionflags"></a>  CSnapInItemImpl::SetMenuInsertionFlags

调用此函数可修改由指定的菜单插入标志*pInsertionAllowed*，管理单元中的对象。

```
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>参数

*bBeforeInsertion*<br/>
[in]如果项被添加到上下文菜单中; 之前，应调用的函数，非零值否则为 0。

*pInsertionAllowed*<br/>
[in、 out]标识 Microsoft 管理控制台 MMC 定义菜单项的插入点，可以使用。 这可以是下列标志的组合：

- 可以在上下文菜单的顶部插入 CCM_INSERTIONALLOWED_TOP 项。

- 创建新的子菜单中，可以插入 CCM_INSERTIONALLOWED_NEW 项。

- 可以在任务子菜单中插入 CCM_INSERTIONALLOWED_TASK 项。

- 在工具栏上的视图菜单中或在结果窗格上下文菜单的视图子菜单中，可以插入 CCM_INSERTIONALLOWED_VIEW 项。

### <a name="remarks"></a>备注

如果你正在开发主管理单元中，可以重置任何作为一种方法限制使用第三方扩展可以添加的菜单项的类型的插入标志。 例如，主要单元可以清除 CCM_INSERTIONALLOWED_NEW 标志可阻止扩展添加自己创建新的菜单项。

不应尝试将中的位*pInsertionAllowed*的最初已清除。 MMC 的未来版本可能会使用当前未定义，因此不应更改当前未定义的位的位。

##  <a name="settoolbarbuttoninfo"></a>  CSnapInItemImpl::SetToolbarButtonInfo

调用此函数可修改任何工具栏按钮样式，该管理单元对象，然后才能创建工具栏。

```
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>参数

*id*<br/>
[in]若要设置的工具栏按钮的 ID。

*fsState*<br/>
[in]按钮状态标志。 可以是一个或多项操作：

- TBSTATE_CHECKED 按钮具有 TBSTYLE_CHECKED 样式和已按下。

- TBSTATE_ENABLED 按钮接受用户输入。 不具有此状态的按钮不接受用户输入，并就会变灰。

- TBSTATE_HIDDEN 按钮不可见，并且不能接受用户输入。

- TBSTATE_INDETERMINATE 按钮就会变灰。

- TBSTATE_PRESSED 已按下按钮。

- 该按钮后跟 TBSTATE_WRAP 一个换行符。 该按钮还必须具有 TBSTATE_ENABLED。

*fsType*<br/>
[in]按钮状态标志。 可以是一个或多项操作：

- TBSTYLE_BUTTON 创建标准的推送按钮。

- TBSTYLE_CHECK 创建一个按钮，每次按下并不按下状态之间切换用户单击它。 该按钮处于按下状态时具有不同的背景色。

- TBSTYLE_CHECKGROUP 创建直到按下的组中的另一个按钮，按下保持复选按钮。

- TBSTYLE_GROUP 创建直到按下的组中的另一个按钮，按下某个按钮保持。

- TBSTYLE_SEP 创建分隔符，提供按钮组较小的差异。 包含此样式的按钮不会接收用户输入。

##  <a name="updatemenustate"></a>  CSnapInItemImpl::UpdateMenuState

调用此函数可修改的菜单项，然后插入到管理单元中对象的上下文菜单。

```
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>参数

*id*<br/>
[in]要设置的菜单项的 ID。

*pBuf*<br/>
[in]指向要更新的菜单项的字符串的指针。

*flags*<br/>
[in]指定新的状态标志。 这可以是下列标志的组合：

- MF_POPUP 指定这是上下文菜单中的子菜单。 菜单项、 插入点，以及进一步子菜单可能添加到此子菜单使用其`lCommandID`作为其`IInsertionPointID`。

- MF_BITMAP 和 MF_OWNERDRAW 这些标志不允许使用并将导致返回值为 E_INVALIDARG。

- MF_SEPARATOR 绘制水平的分隔线。 仅`IContextMenuProvider`允许添加 MF_SEPARATOR 设置菜单项。

- MF_CHECKED 将菜单项旁边的复选标记。

- MF_DISABLED 禁用菜单项，因此无法选择它，但该标志没有呈灰色它。

- MF_ENABLED 启用菜单项，以便它可以被选择，从灰色状态还原。

- MF_GRAYED 禁用菜单项，因此不能选择该应用它。

- MF_MENUBARBREAK 函数 MF_MENUBREAK 相同标记的菜单栏。 下拉列表菜单、 子菜单或快捷菜单，新列与旧列分隔条竖直线。

- MF_MENUBREAK 将项放置在新行 （表示菜单栏） 上或在无需分隔列的新列 （适用于下拉列表菜单、 子菜单或快捷菜单）。

- MF_UNCHECKED 不会施加 （默认值） 的项旁边的复选标记。

不能一起使用的标志的以下组：

- MF_DISABLED、 MF_ENABLED 和 MF_GRAYED。

- MF_MENUBARBREAK 和 MF_MENUBREAK。

- MF_CHECKED 和 MF_UNCHECKED。

##  <a name="updatetoolbarbutton"></a>  CSnapInItemImpl::UpdateToolbarButton

调用此函数可显示前修改工具栏按钮，管理单元中对象。

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>参数

*id*<br/>
指定要更新的工具栏按钮的按钮 ID。

*fsState*<br/>
指定工具栏按钮状态。 如果要设置此状态，则返回 TRUE。 这可以是下列标志的组合：

- 已启用该按钮接受用户输入。 不具有此状态的按钮不接受用户输入，并就会变灰。

- 检查该按钮具有选中的样式和已按下。

- 隐藏按钮不可见，并且不能接受用户输入。

- 不确定按钮就会变灰。

- BUTTONPRESSED 已按下按钮。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
