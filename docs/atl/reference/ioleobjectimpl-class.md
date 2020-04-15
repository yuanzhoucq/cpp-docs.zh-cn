---
title: IOleObjectImpl 类
ms.date: 11/04/2016
f1_keywords:
- IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl::Advise
- ATLCTL/ATL::IOleObjectImpl::Close
- ATLCTL/ATL::IOleObjectImpl::DoVerb
- ATLCTL/ATL::IOleObjectImpl::DoVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::DoVerbHide
- ATLCTL/ATL::IOleObjectImpl::DoVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::DoVerbOpen
- ATLCTL/ATL::IOleObjectImpl::DoVerbPrimary
- ATLCTL/ATL::IOleObjectImpl::DoVerbShow
- ATLCTL/ATL::IOleObjectImpl::DoVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::EnumAdvise
- ATLCTL/ATL::IOleObjectImpl::EnumVerbs
- ATLCTL/ATL::IOleObjectImpl::GetClientSite
- ATLCTL/ATL::IOleObjectImpl::GetClipboardData
- ATLCTL/ATL::IOleObjectImpl::GetExtent
- ATLCTL/ATL::IOleObjectImpl::GetMiscStatus
- ATLCTL/ATL::IOleObjectImpl::GetMoniker
- ATLCTL/ATL::IOleObjectImpl::GetUserClassID
- ATLCTL/ATL::IOleObjectImpl::GetUserType
- ATLCTL/ATL::IOleObjectImpl::InitFromData
- ATLCTL/ATL::IOleObjectImpl::IsUpToDate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::SetClientSite
- ATLCTL/ATL::IOleObjectImpl::SetColorScheme
- ATLCTL/ATL::IOleObjectImpl::SetExtent
- ATLCTL/ATL::IOleObjectImpl::SetHostNames
- ATLCTL/ATL::IOleObjectImpl::SetMoniker
- ATLCTL/ATL::IOleObjectImpl::Unadvise
- ATLCTL/ATL::IOleObjectImpl::Update
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
ms.openlocfilehash: 86d82aea2e92eb99903284abe4ac03478369616c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326528"
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl 类

此类实现`IUnknown`并且是容器与控件通信的主体接口。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IOleObjectImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IOleObjectimpl：：建议](#advise)|与控件建立咨询连接。|
|[IOleObjectimpl：关闭](#close)|将控制状态从运行更改为加载。|
|[IOleObjectimpl：:DoVerb](#doverb)|告诉控件执行其枚举操作之一。|
|[IOleObjectimpl：:DoVerb丢弃Undo](#doverbdiscardundo)|告诉控件放弃它维护的任何撤消状态。|
|[IOleObjectimpl：:DoVerbHide](#doverbhide)|告诉控件从视图中删除其用户界面。|
|[IOleobjectimpl：:Doverbinplace激活](#doverbinplaceactivate)|运行控件并安装其窗口，但不会安装控件的用户界面。|
|[IOleObjectimpl：:DoVerbOpen](#doverbopen)|导致在单独的窗口中打开编辑控件。|
|[IOleObjectimpl：:DoVerb主要](#doverbprimary)|当用户双击控件时执行指定的操作。 控件定义操作，通常是为了就地激活控件。|
|[IOleObjectimpl：:DoVerbshow](#doverbshow)|向用户显示新插入的控件。|
|[IOleObjectimpl：:DoVerbUI激活](#doverbuiactivate)|就地激活控件并显示控件的用户界面，如菜单和工具栏。|
|[IOleObjectimpl：：枚举建议](#enumadvise)|枚举控件的咨询连接。|
|[IOleObjectimpl：：枚举](#enumverbs)|枚举控件的操作。|
|[IOleObjectimpl：：获取客户端网站](#getclientsite)|检索控件的客户端站点。|
|[IOleObjectimpl：：获取夹板数据](#getclipboarddata)|从剪贴板检索数据。 ATL 实现返回E_NOTIMPL。|
|[IOleObjectimpl：：获取范围](#getextent)|检索控件显示区域的范围。|
|[IOleObjectimpl：：获取Misc状态](#getmiscstatus)|检索控件的状态。|
|[IOleObjectimpl：：GetMoniker](#getmoniker)|检索控件的绰号。 ATL 实现返回E_NOTIMPL。|
|[IOleObjectimpl：：获取用户类ID](#getuserclassid)|检索控件的类标识符。|
|[IOleObjectimpl：：获取用户类型](#getusertype)|检索控件的用户类型名称。|
|[IOleObjectimpl：：从数据中](#initfromdata)|从所选数据初始化控件。 ATL 实现返回E_NOTIMPL。|
|[IOleobjectimpl：：至前](#isuptodate)|检查控件是否为最新控件。 ATL 实现返回S_OK。|
|[IOleObjectimpl：：在后空音丢弃undo](#onpostverbdiscardundo)|在丢弃撤消状态后由[DoVerbDiscardUndo](#doverbdiscardundo)调用。|
|[IOleobjectimpl：：在后音隐藏](#onpostverbhide)|在控件隐藏后由[DoVerbHide](#doverbhide)调用。|
|[IOleobjectimpl：：在后空音位置激活](#onpostverbinplaceactivate)|在控件激活到位后，[由 DoVerbInPlace 调用](#doverbinplaceactivate)。|
|[IOleObjectimpl：：在PostVerbopen上](#onpostverbopen)|在打开控件以在单独的窗口中编辑控件后[，DoVerbOpen](#doverbopen)调用。|
|[IOleObjectimpl：：在后场Verbshow](#onpostverbshow)|在控件变得可见后由[DoVerbShow](#doverbshow)调用。|
|[IOleObjectimpl：：在后空音激活](#onpostverbuiactivate)|在激活控件的用户界面后，[由 DoVerbUIActivate](#doverbuiactivate)调用。|
|[IOleObjectimpl：：在Preverbimplundo](#onpreverbdiscardundo)|在丢弃撤消状态之前由[DoVerbDiscardUndo](#doverbdiscardundo)调用。|
|[IOleobjectimpl：：在上Verbverbhide](#onpreverbhide)|在隐藏控件之前由[DoVerbHide](#doverbhide)调用。|
|[IOleobjectimpl：：在预置位置激活](#onpreverbinplaceactivate)|在控件激活到位之前，[由 DoVerbInPlace 调用](#doverbinplaceactivate)。|
|[IOleObjectimpl：：在Preverbopen上](#onpreverbopen)|在打开控件以在单独的窗口中编辑之前由[DoVerbOpen](#doverbopen)调用。|
|[IOleObjectimpl：：在Preverbshow上](#onpreverbshow)|在控件变得可见之前由[DoVerbShow](#doverbshow)调用。|
|[IOleObjectimpl：：在Verbui激活上](#onpreverbuiactivate)|在激活控件的用户界面之前，[由 DoVerbUIActivate](#doverbuiactivate)调用。|
|[IOleObjectimpl：：设置客户端网站](#setclientsite)|告诉控件有关其在容器中的客户端站点。|
|[IOleObjectimpl：：设置颜色方案](#setcolorscheme)|向控件的应用程序（如果有）建议配色方案。 ATL 实现返回E_NOTIMPL。|
|[IOleObjectimpl：：设置范围](#setextent)|设置控件的显示区域的范围。|
|[IOleObjectimpl：：设置主机名](#sethostnames)|告诉控件容器应用程序和容器文档的名称。|
|[IOleObjectimpl：：SetMoniker](#setmoniker)|告诉控件其名字是什么。 ATL 实现返回E_NOTIMPL。|
|[IOleObjectimpl：：不建议](#unadvise)|删除与控件的咨询连接。|
|[IOleObjectimpl：：更新](#update)|更新控件。 ATL 实现返回S_OK。|

## <a name="remarks"></a>备注

[IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject)接口是容器与控件通信的主要接口。 类`IOleObjectImpl`通过在调试生成中向转储设备发送`IUnknown`信息来提供此接口的默认实现和实现。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="ioleobjectimpladvise"></a><a name="advise"></a>IOleObjectimpl：：建议

与控件建立咨询连接。

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>备注

请参阅[IOleObject：：](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise)在 Windows SDK 中提供建议。

## <a name="ioleobjectimplclose"></a><a name="close"></a>IOleObjectimpl：关闭

将控制状态从运行更改为加载。

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>备注

停用控件并销毁控制窗口（如果存在）。 如果控制类数据成员[CComControlBase：：m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave)为 TRUE，*并且 dwSaveOption*参数是OLECLOSE_SAVEIFDIRTY或OLECLOSE_PROMPTSAVE，则控件属性在关闭前保存。

控制类数据成员[CComControlBase：：m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite)和[CComControlBase：m_spAdviseSink）](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)中持有的指针被释放，数据成员[CComControlBase：：：m_bNegotiatedWnd、CComControlBase：m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd)和[CComControlBase：m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex)设置为 FALSE。 [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)

请参阅[IOleObject：关闭](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close)Windows SDK。

## <a name="ioleobjectimpldoverb"></a><a name="doverb"></a>IOleObjectimpl：:DoVerb

告诉控件执行其枚举操作之一。

```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```

### <a name="remarks"></a>备注

根据 的值`iVerb`，其中一个 ATL`DoVerb`帮助器函数的调用如下所示：

|*iVerb*价值|多维尔布帮助器函数称为|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[多维尔布·丢弃Undo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[多维尔布](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[多维尔布林广场激活](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[多维尔布打开](#doverbopen)|
|OLEIVERB_PRIMARY|[多维尔布小学](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase：:DoVerb属性](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[多维尔布秀](#doverbshow)|
|OLEIVERB_UIACTIVATE|[多维尔布UI激活](#doverbuiactivate)|

请参阅[IOleObject：:DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)在 Windows SDK 中。

## <a name="ioleobjectimpldoverbdiscardundo"></a><a name="doverbdiscardundo"></a>IOleObjectimpl：:DoVerb丢弃Undo

告诉控件放弃它维护的任何撤消状态。

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>参数

*prcPosRec*<br/>
[在]指向容器希望控件绘制到的矩形的指针。

*hwnd 家长*<br/>
[在]包含控件的窗口的句柄。

### <a name="return-value"></a>返回值

返回S_OK。

## <a name="ioleobjectimpldoverbhide"></a><a name="doverbhide"></a>IOleObjectimpl：:DoVerbHide

停用并删除控件的用户界面，并隐藏控件。

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>参数

*prcPosRec*<br/>
[在]指向容器希望控件绘制到的矩形的指针。

*hwnd 家长*<br/>
[在]包含控件的窗口的句柄。 ATL 实现中未使用。

### <a name="return-value"></a>返回值

返回S_OK。

## <a name="ioleobjectimpldoverbinplaceactivate"></a><a name="doverbinplaceactivate"></a>IOleobjectimpl：:Doverbinplace激活

运行控件并安装其窗口，但不会安装控件的用户界面。

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>参数

*prcPosRec*<br/>
[在]指向容器希望控件绘制到的矩形的指针。

*hwnd 家长*<br/>
[在]包含控件的窗口的句柄。 ATL 实现中未使用。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

通过调用[CComControlBase：：在原位置激活激活](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate)控件。 除非控件类的数据成员`m_bWindowOnly`为 TRUE，`DoVerbInPlaceActivate`否则首先尝试将控件激活为无窗口控件（仅当容器支持[IOleInPlaceSite 无窗口](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)时才可能）。 如果失败，该函数将尝试使用扩展功能激活控件（仅当容器支持[IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)时才可能）。 如果失败，该函数将尝试激活没有扩展功能的控件（仅当容器支持[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)时才可能）。 如果激活成功，该函数将通知容器控件已激活。

## <a name="ioleobjectimpldoverbopen"></a><a name="doverbopen"></a>IOleObjectimpl：:DoVerbOpen

导致在单独的窗口中打开编辑控件。

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>参数

*prcPosRec*<br/>
[在]指向容器希望控件绘制到的矩形的指针。

*hwnd 家长*<br/>
[在]包含控件的窗口的句柄。

### <a name="return-value"></a>返回值

返回S_OK。

## <a name="ioleobjectimpldoverbprimary"></a><a name="doverbprimary"></a>IOleObjectimpl：:DoVerb主要

定义用户双击控件时执行的操作。

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>参数

*prcPosRec*<br/>
[在]指向容器希望控件绘制到的矩形的指针。

*hwnd 家长*<br/>
[在]包含控件的窗口的句柄。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

默认情况下，设置为显示属性页。 您可以在控件类中重写此行为，以在双击时调用其他行为;但是，在双击时，可以重写此行为。例如，播放视频或就地活动。

## <a name="ioleobjectimpldoverbshow"></a><a name="doverbshow"></a>IOleObjectimpl：:DoVerbshow

告诉容器使控件可见。

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>参数

*prcPosRec*<br/>
[在]指向容器希望控件绘制到的矩形的指针。

*hwnd 家长*<br/>
[在]包含控件的窗口的句柄。 ATL 实现中未使用。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ioleobjectimpldoverbuiactivate"></a><a name="doverbuiactivate"></a>IOleObjectimpl：:DoVerbUI激活

激活控件的用户界面，并通知容器其菜单正在被复合菜单替换。

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>参数

*prcPosRec*<br/>
[在]指向容器希望控件绘制到的矩形的指针。

*hwnd 家长*<br/>
[在]包含控件的窗口的句柄。 ATL 实现中未使用。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ioleobjectimplenumadvise"></a><a name="enumadvise"></a>IOleObjectimpl：：枚举建议

提供此控件的已注册咨询连接的枚举。

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>备注

请参阅[IOleObject：：Windows](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) SDK 中的 Enum 建议。

## <a name="ioleobjectimplenumverbs"></a><a name="enumverbs"></a>IOleObjectimpl：：枚举

通过调用`OleRegEnumVerbs`提供此控件的已注册操作（动词）的枚举。

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>备注

您可以将谓词添加到项目的 .rgs 文件中。 例如，请参阅 CIRCCTL。[保监会](../../overview/visual-cpp-samples.md)样本中的RGS。

请参阅[IOleObject：：Windows](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) SDK 中的枚举Verbs。

## <a name="ioleobjectimplgetclientsite"></a><a name="getclientsite"></a>IOleObjectimpl：：获取客户端网站

将指针放入控制类数据成员[CComControlBase：：：m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite)到*ppClientSite*中，并在指针上增加引用计数。

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>备注

请参阅[IOleObject：获取](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite)Windows SDK 中的客户端站点。

## <a name="ioleobjectimplgetclipboarddata"></a><a name="getclipboarddata"></a>IOleObjectimpl：：获取夹板数据

从剪贴板检索数据。

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅 IOleObject：获取 Windows SDK 中的["剪贴板数据](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata)"。

## <a name="ioleobjectimplgetextent"></a><a name="getextent"></a>IOleObjectimpl：：获取范围

以 HIMETRIC 单位（每单位 0.01 毫米）检索正在运行的控件的显示大小。

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>备注

大小存储在控制类数据成员[CComControlBase：m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。

请参阅[IOleObject：获取](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent)Windows SDK 中的范围。

## <a name="ioleobjectimplgetmiscstatus"></a><a name="getmiscstatus"></a>IOleObjectimpl：：获取Misc状态

通过调用`OleRegGetMiscStatus`返回指向控件的已注册状态信息的指针。

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>备注

状态信息包括控件和表示数据支持的行为。 您可以将状态信息添加到项目的 .rgs 文件中。

请参阅[IOleObject：获取](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus)Windows SDK 中的 Misc 身份。

## <a name="ioleobjectimplgetmoniker"></a><a name="getmoniker"></a>IOleObjectimpl：：GetMoniker

检索控件的绰号。

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleObject：在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker)Windows SDK 中获取 Moniker。

## <a name="ioleobjectimplgetuserclassid"></a><a name="getuserclassid"></a>IOleObjectimpl：：获取用户类ID

返回控件的类标识符。

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>备注

请参阅[IOleObject：获取](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid)Windows SDK 中的UserClassID。

## <a name="ioleobjectimplgetusertype"></a><a name="getusertype"></a>IOleObjectimpl：：获取用户类型

通过调用`OleRegGetUserType`返回控件的用户类型名称。

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>备注

用户名用于在用户界面元素（如菜单和对话框）中显示。 您可以在项目的 .rgs 文件中更改用户名类型名称。

请参阅[IOleObject：获取](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype)Windows SDK 中的用户类型。

## <a name="ioleobjectimplinitfromdata"></a><a name="initfromdata"></a>IOleObjectimpl：：从数据中

从所选数据初始化控件。

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleObject：Windows SDK 中来自数据的 Initit。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata)

## <a name="ioleobjectimplisuptodate"></a><a name="isuptodate"></a>IOleobjectimpl：：至前

检查控件是否为最新控件。

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

请参阅[IOleObject：Windows SDK 中的"IsUpDate"。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate)

## <a name="ioleobjectimplonpostverbdiscardundo"></a><a name="onpostverbdiscardundo"></a>IOleObjectimpl：：在后空音丢弃undo

在丢弃撤消状态后由[DoVerbDiscardUndo](#doverbdiscardundo)调用。

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

使用要在丢弃撤消状态后执行的代码重写此方法。

## <a name="ioleobjectimplonpostverbhide"></a><a name="onpostverbhide"></a>IOleobjectimpl：：在后音隐藏

在控件隐藏后由[DoVerbHide](#doverbhide)调用。

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

使用隐藏控件后要执行的代码覆盖此方法。

## <a name="ioleobjectimplonpostverbinplaceactivate"></a><a name="onpostverbinplaceactivate"></a>IOleobjectimpl：：在后空音位置激活

在控件激活到位后，[由 DoVerbInPlace 调用](#doverbinplaceactivate)。

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

使用要在控件就地激活后执行的代码覆盖此方法。

## <a name="ioleobjectimplonpostverbopen"></a><a name="onpostverbopen"></a>IOleObjectimpl：：在PostVerbopen上

在打开控件以在单独的窗口中编辑控件后[，DoVerbOpen](#doverbopen)调用。

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

在打开控件以在单独的窗口中编辑后，使用要执行的代码覆盖此方法。

## <a name="ioleobjectimplonpostverbshow"></a><a name="onpostverbshow"></a>IOleObjectimpl：：在后场Verbshow

在控件变得可见后由[DoVerbShow](#doverbshow)调用。

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

使用要在控件变得可见后执行的代码重写此方法。

## <a name="ioleobjectimplonpostverbuiactivate"></a><a name="onpostverbuiactivate"></a>IOleObjectimpl：：在后空音激活

在激活控件的用户界面后，[由 DoVerbUIActivate](#doverbuiactivate)调用。

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

使用要在激活控件的用户界面后执行的代码覆盖此方法。

## <a name="ioleobjectimplonpreverbdiscardundo"></a><a name="onpreverbdiscardundo"></a>IOleObjectimpl：：在Preverbimplundo

在丢弃撤消状态之前由[DoVerbDiscardUndo](#doverbdiscardundo)调用。

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

为了防止丢弃撤消状态，请重写此方法以返回错误 HRESULT。

## <a name="ioleobjectimplonpreverbhide"></a><a name="onpreverbhide"></a>IOleobjectimpl：：在上Verbverbhide

在隐藏控件之前由[DoVerbHide](#doverbhide)调用。

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

为了防止隐藏控件，重写此方法以返回错误 HRESULT。

## <a name="ioleobjectimplonpreverbinplaceactivate"></a><a name="onpreverbinplaceactivate"></a>IOleobjectimpl：：在预置位置激活

在控件激活到位之前，[由 DoVerbInPlace 调用](#doverbinplaceactivate)。

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

为了防止在就位激活控件，重写此方法以返回错误 HRESULT。

## <a name="ioleobjectimplonpreverbopen"></a><a name="onpreverbopen"></a>IOleObjectimpl：：在Preverbopen上

在打开控件以在单独的窗口中编辑之前由[DoVerbOpen](#doverbopen)调用。

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

为了防止在单独的窗口中打开控件进行编辑，重写此方法以返回错误 HRESULT。

## <a name="ioleobjectimplonpreverbshow"></a><a name="onpreverbshow"></a>IOleObjectimpl：：在Preverbshow上

在控件变得可见之前由[DoVerbShow](#doverbshow)调用。

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

为了防止控件变得可见，重写此方法以返回错误 HRESULT。

## <a name="ioleobjectimplonpreverbuiactivate"></a><a name="onpreverbuiactivate"></a>IOleObjectimpl：：在Verbui激活上

在激活控件的用户界面之前，[由 DoVerbUIActivate](#doverbuiactivate)调用。

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

为了防止激活控件的用户界面，重写此方法以返回错误 HRESULT。

## <a name="ioleobjectimplsetclientsite"></a><a name="setclientsite"></a>IOleObjectimpl：：设置客户端网站

告诉控件有关其在容器中的客户端站点。

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>备注

然后，该方法返回S_OK。

请参阅[IOleObject：在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite)Windows SDK 中设置客户端站点。

## <a name="ioleobjectimplsetcolorscheme"></a><a name="setcolorscheme"></a>IOleObjectimpl：：设置颜色方案

向控件的应用程序（如果有）建议配色方案。

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleObject：在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme)Windows SDK 中设置颜色方案。

## <a name="ioleobjectimplsetextent"></a><a name="setextent"></a>IOleObjectimpl：：设置范围

设置控件的显示区域的范围。

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>备注

否则，`SetExtent`将控制类数据成员`psizel`[CComControlBase：：m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)中指向的值存储。 此值以 HIMETRIC 单位（单位 0.01 毫米）为单位。

如果控制类数据成员[CComControlBase：：m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural)为`SetExtent`TRUE，则还会将控制类`psizel`数据成员[CComControlBase：：m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)中指向的值存储。

如果控制类数据成员[CComControlBase：：m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize)为`SetExtent`TRUE，请呼叫`SendOnDataChange`并`SendOnViewChange`通知向通知持有人注册的所有通知接收器控制大小已更改。

请参阅[IOleObject：在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent)Windows SDK 中设置范围。

## <a name="ioleobjectimplsethostnames"></a><a name="sethostnames"></a>IOleObjectimpl：：设置主机名

告诉控件容器应用程序和容器文档的名称。

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

请参阅[IOleObject：在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames)Windows SDK 中设置主机名。

## <a name="ioleobjectimplsetmoniker"></a><a name="setmoniker"></a>IOleObjectimpl：：SetMoniker

告诉控件其名字是什么。

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleObject：在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker)Windows SDK 中设置 Moniker。

## <a name="ioleobjectimplunadvise"></a><a name="unadvise"></a>IOleObjectimpl：：不建议

删除存储在控制类`m_spOleAdviseHolder`的数据成员中的咨询连接。

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>备注

请参阅[IOleObject：：](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise)在 Windows SDK 中取消建议。

## <a name="ioleobjectimplupdate"></a><a name="update"></a>IOleObjectimpl：：更新

更新控件。

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

请参阅[IOleObject：：](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update)在 Windows SDK 中更新。

## <a name="see-also"></a>另请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控制接口](/windows/win32/com/activex-controls-interfaces)<br/>
[类概述](../../atl/atl-class-overview.md)
