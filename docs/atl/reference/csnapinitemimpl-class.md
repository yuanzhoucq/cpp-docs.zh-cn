---
title: "CSnapInItemImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f1355173bafcf026a7f1bfba771a7769b202c92c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl 类
此类提供用于实现管理单元中节点对象的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, BOOL bIsExtension = FALSE>  
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`CSnapInItemImpl`。  
  
 *bIsExtension*  
 **TRUE**如果对象是管理单元扩展; 否则为**FALSE**。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|将菜单项添加到上下文菜单。|  
|[CSnapInItemImpl::Command](#command)|由控制台选择自定义菜单项时调用。|  
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|将页添加到管理单元的属性表。|  
|[CSnapInItemImpl::FillData](#filldata)|副本上的管理单元中对象的信息复制到指定的流。|  
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|检索**RESULTDATAITEM**管理单元的结构。|  
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|确定使用结果窗格视图的类型。|  
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|检索**SCOPEDATAITEM**管理单元的结构。|  
|[CSnapInItemImpl::Notify](#notify)|由控制台以管理单元在用户所采取的操作通知调用。|  
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|调用以查看管理单元中节点是否支持属性页。|  
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|修改管理单元中对象的菜单插入标志。|  
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|设置指定的工具栏按钮的信息。|  
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|更新的上下文菜单项的状态。|  
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|更新指定的工具栏按钮的状态。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|管理单元中对象的名称。|  
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Windows **RESULTDATAITEM**使用结构`CSnapInItemImpl`对象。|  
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Windows **SCOPEDATAITEM**使用结构`CSnapInItemImpl`对象。|  
  
## <a name="remarks"></a>备注  
 `CSnapInItemImpl`提供了管理单元中节点对象，例如添加菜单项和工具栏，以及转发到相应的处理程序函数的管理单元节点的命令的基本实现。 这些功能使用多个不同的接口来实现，并将类型映射。 默认实现处理方法是确定正确的派生类的实例，然后将消息转发给正确的实例发送到节点对象的通知。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CSnapInItem`  
  
 `CSnapInItemImpl`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlsnap.h  
  
##  <a name="addmenuitems"></a>CSnapInItemImpl::AddMenuItems  
 此方法实现的 Win32 函数[IExtendContextMenu::AddMenuItems](http://msdn.microsoft.com/library/aa814841)。  
  
```
AddMenuItems(  
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>参数  
 *piCallback*  
 [in]指向**IContextMenuCallback** ，可以将项添加到上下文菜单。  
  
 `pInsertionAllowed`  
 [在中，out]标识 Microsoft 管理控制台 MMC 定义菜单项插入点可用。 这可以是以下标志的组合：  
  
- **CCM_INSERTIONALLOWED_TOP**可以在上下文菜单的顶部插入项。  
  
- **CCM_INSERTIONALLOWED_NEW**可以创建新的子菜单中插入项。  
  
- **CCM_INSERTIONALLOWED_TASK**可以任务子菜单中插入项。  
  
- **CCM_INSERTIONALLOWED_VIEW**中工具栏视图菜单或结果窗格中的上下文菜单的视图子菜单中，可以插入项。  
  
 `type`  
 [in]指定的对象的类型。 它可以具有以下值之一：  
  
- **CCT_SCOPE**作用域窗格中上下文的数据对象。  
  
- **CCT_RESULT**结果窗格中上下文的数据对象。  
  
- **CCT_SNAPIN_MANAGER**管理器管理单元中上下文的数据对象。  
  
- **CCT_UNINITIALIZED**数据对象具有无效的类型。  
  
##  <a name="command"></a>CSnapInItemImpl::Command  
 此方法实现的 Win32 函数[IExtendContextMenu::Command](http://msdn.microsoft.com/library/aa814842)。  
  
```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>参数  
 *lCommandID*  
 [in]指定菜单项的命令标识符。  
  
 `type`  
 [in]指定的对象的类型。 它可以具有以下值之一：  
  
- **CCT_SCOPE**作用域窗格中上下文的数据对象。  
  
- **CCT_RESULT**结果窗格中上下文的数据对象。  
  
- **CCT_SNAPIN_MANAGER**管理器管理单元中上下文的数据对象。  
  
- **CCT_UNINITIALIZED**数据对象具有无效的类型。  
  
##  <a name="createpropertypages"></a>CSnapInItemImpl::CreatePropertyPages  
 此方法实现的 Win32 函数[IExtendPropertySheet::CreatePropertyPages](http://msdn.microsoft.com/library/aa814846)。  
  
```
CreatePropertyPages(  
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>参数  
 *lpProvider*  
 [in]指向**IPropertySheetCallback**接口。  
  
 *句柄*  
 [in]指定使用的句柄到路由**MMCN_PROPERTY_CHANGE**到适当的数据类的通知消息。  
  
 *pUnk*  
 [in]指向**IExtendPropertySheet**包含有关节点的上下文信息的对象上的接口。  
  
 `type`  
 [in]指定的对象的类型。 它可以具有以下值之一：  
  
- **CCT_SCOPE**作用域窗格中上下文的数据对象。  
  
- **CCT_RESULT**结果窗格中上下文的数据对象。  
  
- **CCT_SNAPIN_MANAGER**管理器管理单元中上下文的数据对象。  
  
- **CCT_UNINITIALIZED**数据对象具有无效的类型。  
  
##  <a name="csnapinitemimpl"></a>CSnapInItemImpl::CSnapInItemImpl  
 构造 `CSnapInItemImpl` 对象。  
  
```
CSnapInItemImpl();
```  
  
##  <a name="filldata"></a>CSnapInItemImpl::FillData  
 调用此函数可检索项目的信息。  
  
```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 [in]剪贴板格式 （文本、 多格式文本或与 OLE 项的多格式文本）。  
  
 `pStream`  
 [in]指向包含的对象数据的流的指针。  
  
### <a name="remarks"></a>备注  
 若要正确实现此函数，请将正确的信息复制到流 ( `pStream`)，则根据指定的剪贴板格式`cf`。  
  
##  <a name="getresultviewtype"></a>CSnapInItemImpl::GetResultViewType  
 调用此函数可检索管理单元中对象的结果窗格中的视图的类型。  
  
```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```  
  
### <a name="parameters"></a>参数  
 *读*  
 [out]指向的地址返回的视图类型的指针。  
  
 *pViewOptions*  
 [out]指向**MMC_VIEW_OPTIONS**枚举，为控制台提供了由所属的管理单元签入指定的选项。 此值可以是以下项之一：  
  
- **MMC_VIEW_OPTIONS_NOLISTVIEWS** = 0x00000001 告知控制台以避免从提供标准列表视图中的新选项**视图**菜单。 允许将仅在结果视图窗格中显示其自己的自定义视图的管理单元接。 这是在此时间定义的唯一选项标志。  
  
- **MMC_VIEW_OPTIONS_NONE** = 0 允许的默认视图选项。  
  
##  <a name="getscopepaneinfo"></a>CSnapInItemImpl::GetScopePaneInfo  
 调用此函数可检索**SCOPEDATAITEM**管理单元的结构。  
  
```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```  
  
### <a name="parameters"></a>参数  
 *pScopeDataItem*  
 [out]指向的指针**SCOPEDATAITEM**结构`CSnapInItemImpl`对象。  
  
##  <a name="getresultpaneinfo"></a>CSnapInItemImpl::GetResultPaneInfo  
 调用此函数可检索**RESULTDATAITEM**管理单元的结构。  
  
```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```  
  
### <a name="parameters"></a>参数  
 *pResultDataItem*  
 [out]指向的指针**RESULTDATAITEM**结构`CSnapInItemImpl`对象。  
  
##  <a name="m_bstrdisplayname"></a>CSnapInItemImpl::m_bstrDisplayName  
 包含节点项显示的字符串。  
  
```
CComBSTR m_bstrDisplayName;
```  
  
##  <a name="m_scopedataitem"></a>CSnapInItemImpl::m_scopeDataItem  
 `SCOPEDATAITEM`的管理单元中数据对象的结构。  
  
```
SCOPEDATAITEM m_scopeDataItem;
```  
  
##  <a name="m_resultdataitem"></a>CSnapInItemImpl::m_resultDataItem  
 [RESULTDATAITEM](http://msdn.microsoft.com/library/aa815165)的管理单元中数据对象的结构。  
  
```
RESULTDATAITEM m_resultDataItem;
```  
  
##  <a name="notify"></a>CSnapInItemImpl::Notify  
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
 `event`  
 [in]标识用户所执行的操作。 可能会出现以下通知：  
  
- **MMCN_ACTIVATE**发送时窗口将被激活，然后停用。  
  
- **MMCN_ADD_IMAGES**发送将映像添加到结果窗格中。  
  
- **MMCN_BTN_CLICK**发送当用户单击一个工具栏按钮。  
  
- **MMCN_CLICK**当用户单击鼠标按钮在列表视图项上的时发送。  
  
- **MMCN_DBLCLICK**当用户双击鼠标按钮在列表视图项上的时发送。  
  
- **MMCN_DELETE**发送通知的管理单元，该对象应删除。  
  
- **MMCN_EXPAND**文件夹需要要展开或收缩时发送。  
  
- **MMCN_MINIMIZED** Sent 当窗口是正在最小化或最大化。  
  
- **MMCN_PROPERTY_CHANGE**发送通知即将更改的管理单元中对象的视图的管理单元对象。  
  
- **MMCN_REMOVE_CHILDREN**发送时的管理单元，则必须删除它具有指定节点下添加的整个子树。  
  
- **MMCN_RENAME**发送重命名的查询的第一个时间和第二个时间进行重命名。  
  
- **MMCN_SELECT**发送时选择作用域或结果视图窗格中的项。  
  
- **MMCN_SHOW**选择或取消选择了第一次作用域项时发送。  
  
- **MMCN_VIEW_CHANGE**时管理单元可以更新所有视图发生更改时发送。  
  
 `arg`  
 [in]取决于通知类型。  
  
 `param`  
 [in]取决于通知类型。  
  
 *pComponentData*  
 [out]指向的对象实现**IComponentData**。 此参数是**NULL**如果不从转发通知**IComponentData::Notify**。  
  
 *pComponent*  
 [out]指向实现的对象的指针**IComponent**。 此参数是**NULL**如果不从转发通知**IComponent::Notify**。  
  
 `type`  
 [in]指定的对象的类型。 它可以具有以下值之一：  
  
- **CCT_SCOPE**作用域窗格中上下文的数据对象。  
  
- **CCT_RESULT**结果窗格中上下文的数据对象。  
  
- **CCT_SNAPIN_MANAGER**管理器管理单元中上下文的数据对象。  
  
- **CCT_UNINITIALIZED**数据对象具有无效的类型。  
  
##  <a name="querypagesfor"></a>CSnapInItemImpl::QueryPagesFor  
 调用以查看管理单元中节点是否支持属性页。  
  
```
QueryPagesFor(DATA_OBJECT_TYPES type);
```  
  
##  <a name="setmenuinsertionflags"></a>CSnapInItemImpl::SetMenuInsertionFlags  
 调用此函数可修改的菜单插入标志，指定`pInsertionAllowed`，管理单元中的对象。  
  
```
void SetMenuInsertionFlags(  
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```  
  
### <a name="parameters"></a>参数  
 *bBeforeInsertion*  
 [in]如果项添加到上下文菜单中; 之前，应调用该函数则不为否则为 0。  
  
 `pInsertionAllowed`  
 [在中，out]标识 Microsoft 管理控制台 MMC 定义菜单项插入点可用。 这可以是以下标志的组合：  
  
- **CCM_INSERTIONALLOWED_TOP**可以在上下文菜单的顶部插入项。  
  
- **CCM_INSERTIONALLOWED_NEW**可以创建新的子菜单中插入项。  
  
- **CCM_INSERTIONALLOWED_TASK**可以任务子菜单中插入项。  
  
- **CCM_INSERTIONALLOWED_VIEW**中工具栏视图菜单或结果窗格中的上下文菜单的视图子菜单中，可以插入项。  
  
### <a name="remarks"></a>备注  
 如果你正在开发主管理单元中，你可以重置任何作为一种限制的第三方扩展可以添加的菜单项的类型的插入标志。 例如，主管理单元在可以清除**CCM_INSERTIONALLOWED_NEW**标志来禁止扩展添加自己创建新的菜单项。  
  
 不应尝试将中的位`pInsertionAllowed`，最初已清除。 MMC 的未来版本可能会使用 bits 当前未定义因此不应更改当前未定义的位。  
  
##  <a name="settoolbarbuttoninfo"></a>CSnapInItemImpl::SetToolbarButtonInfo  
 调用此函数可创建工具栏之前修改的所管理单元中的对象，任何工具栏按钮样式。  
  
```
void SetToolbarButtonInfo(  
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]工具栏按钮要设置的 ID。  
  
 `fsState`  
 [in]按钮状态标志。 可以是一个或多个以下：  
  
- `TBSTATE_CHECKED`该按钮具有**TBSTYLE_CHECKED**样式，是否已按下。  
  
- `TBSTATE_ENABLED`按钮接受用户输入。 不具有此状态的按钮不接受用户输入，并显示为灰色。  
  
- `TBSTATE_HIDDEN`按钮不可见，并且不能接受用户输入。  
  
- `TBSTATE_INDETERMINATE`按钮为灰色。  
  
- `TBSTATE_PRESSED`已按下按钮。  
  
- `TBSTATE_WRAP`按钮后跟换行符。 按钮还必须具有`TBSTATE_ENABLED`。  
  
 *fsType*  
 [in]按钮状态标志。 可以是一个或多个以下：  
  
- `TBSTYLE_BUTTON`创建一个标准的推送按钮。  
  
- `TBSTYLE_CHECK`创建在每次用户单击它时按下并不按下状态之间切换按钮。 该按钮处于按下状态时具有不同的背景色。  
  
- `TBSTYLE_CHECKGROUP`创建一个组中的另一个按钮按下前将保持按下的复选按钮。  
  
- `TBSTYLE_GROUP`创建一个组中的另一个按钮按下前将保持按下的按钮。  
  
- `TBSTYLE_SEP`创建一个分隔符，提供按钮组之间的小间距。 具有此样式按钮不接收用户输入。  
  
##  <a name="updatemenustate"></a>CSnapInItemImpl::UpdateMenuState  
 调用此函数可修改菜单项之前插入到管理单元中对象的上下文菜单。  
  
```
void UpdateMenuState(  
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]要设置的菜单项的 ID。  
  
 `pBuf`  
 [in]指向要更新的菜单项的字符串的指针。  
  
 `flags`  
 [in]指定新的状态标志。 这可以是以下标志的组合：  
  
- **MF_POPUP**指定这是该上下文菜单中的子菜单。 可以将菜单项、 插入点和进一步子菜单添加到此子菜单使用其**lCommandID**作为其**IInsertionPointID**。  
  
- **MF_BITMAP**和`MF_OWNERDRAW`这些标志不允许使用，并且会在返回值导致`E_INVALIDARG`。  
  
- **MF_SEPARATOR**绘制水平的分隔线。 仅**IContextMenuProvider**允许添加菜单项与**MF_SEPARATOR**设置。  
  
- **MF_CHECKED**放置菜单项旁边的复选标记。  
  
- **MF_DISABLED**禁用菜单项，因此不能选择它，但标志没有呈灰色它。  
  
- `MF_ENABLED`实现菜单项，因此它可以被选择，从其显示为灰色状态中还原它。  
  
- **MF_GRAYED**禁用菜单项，因此不能同时选择灰它。  
  
- **MF_MENUBARBREAK**函数相同**MF_MENUBREAK**表示菜单栏的标志。 下拉列表菜单、 子菜单，或快捷菜单，新列与旧列用分隔垂直的行。  
  
- **MF_MENUBREAK**将项放置在新行 （表示菜单栏） 上或在新列 （对于下拉菜单中，子菜单或快捷菜单） 中无需分隔列。  
  
- **MF_UNCHECKED**不会施加一个项 （默认值） 旁边的复选标记。  
  
 下面的标志组不能一起使用：  
  
- **MF_DISABLED**， `MF_ENABLED`，和**MF_GRAYED**。  
  
- **MF_MENUBARBREAK**和**MF_MENUBREAK**。  
  
- **MF_CHECKED**和**MF_UNCHECKED**。  
  
##  <a name="updatetoolbarbutton"></a>CSnapInItemImpl::UpdateToolbarButton  
 调用此函数可修改工具栏按钮，该管理单元对象，它显示之前。  
  
```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```  
  
### <a name="parameters"></a>参数  
 `id`  
 指定要更新工具栏按钮的按钮 ID。  
  
 `fsState`  
 指定的工具栏按钮状态。 如果要设置此状态，则返回**TRUE**。 这可以是以下标志的组合：  
  
- **启用**按钮接受用户输入。 不具有此状态的按钮不接受用户输入，并显示为灰色。  
  
- **检查**按钮有**检查**样式，是否已按下。  
  
- **HIDDEN**按钮不可见，并且不能接受用户输入。  
  
- **不确定**按钮显示为灰色。  
  
- **BUTTONPRESSED**按下了按钮。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
