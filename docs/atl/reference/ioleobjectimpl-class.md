---
title: IOleObjectImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b82aa22c3cc1c217ba4dfd332c43f6663c94638e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761870"
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl 类

此类实现`IUnknown`是通过该容器与控件进行通信的主体接口。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<class T>  
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>参数

*T*  
您的类，派生自`IOleObjectImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IOleObjectImpl::Advise](#advise)|建立与该控件的通知连接。|
|[IOleObjectImpl::Close](#close)|从运行加载到控件状态更改。|
|[IOleObjectImpl::DoVerb](#doverb)|指示要执行一个其枚举操作的控件。|
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|告知要放弃为维护任何撤消状态的控件。|
|[IOleObjectImpl::DoVerbHide](#doverbhide)|指示要从视图中删除其用户界面的控件。|
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|在运行控件和安装其窗口，但不会安装该控件的用户界面。|
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|导致要在单独的窗口将打开编辑的控件。|
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|当用户双击该控件，则执行指定的操作。 该控件定义的操作，通常以激活控件就地。|
|[IOleObjectImpl::DoVerbShow](#doverbshow)|向用户显示的新插入的控件。|
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|被控制就地激活，并显示控件的用户界面，如菜单和工具栏。|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|枚举控件的通知连接。|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|枚举操作的控件。|
|[IOleObjectImpl::GetClientSite](#getclientsite)|检索控件的客户端的站点。|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|从剪贴板检索数据。 ATL 实现返回 E_NOTIMPL。|
|[IOleObjectImpl::GetExtent](#getextent)|检索控件的显示区域的范围。|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|检索控件的状态。|
|[IOleObjectImpl::GetMoniker](#getmoniker)|检索控件的名字对象。 ATL 实现返回 E_NOTIMPL。|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|检索控件的类标识符。|
|[IOleObjectImpl::GetUserType](#getusertype)|检索控件的用户类型名称。|
|[IOleObjectImpl::InitFromData](#initfromdata)|初始化从所选数据控件。 ATL 实现返回 E_NOTIMPL。|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|检查该控件是最新的。 ATL 实现返回 S_OK。|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|调用[DoVerbDiscardUndo](#doverbdiscardundo)放弃撤消状态后。|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|调用[DoVerbHide](#doverbhide)控件隐藏后。|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|调用[DoVerbInPlaceActivate](#doverbinplaceactivate)就地激活控件之后。|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|调用[DoVerbOpen](#doverbopen)进行编辑的单独窗口中打开该控件后。|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|调用[DoVerbShow](#doverbshow)控件变得可见后。|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|调用[DoVerbUIActivate](#doverbuiactivate)激活控件的用户界面后。|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|调用[DoVerbDiscardUndo](#doverbdiscardundo)撤消之前，状态将被丢弃。|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|调用[DoVerbHide](#doverbhide)隐藏该控件之前。|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|调用[DoVerbInPlaceActivate](#doverbinplaceactivate)就地激活控件之前。|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|调用[DoVerbOpen](#doverbopen)已为编辑的单独窗口中打开该控件之前。|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|调用[DoVerbShow](#doverbshow)控件变得可见之前。|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|调用[DoVerbUIActivate](#doverbuiactivate)控件的用户界面已被激活之前。|
|[IOleObjectImpl::SetClientSite](#setclientsite)|该控件将告知其客户端站点容器中。|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|如果任何到控件的应用程序，建议配色方案。 ATL 实现返回 E_NOTIMPL。|
|[IOleObjectImpl::SetExtent](#setextent)|设置控件的显示区域的范围。|
|[IOleObjectImpl::SetHostNames](#sethostnames)|通知控件容器应用程序和容器文档的名称。|
|[IOleObjectImpl::SetMoniker](#setmoniker)|其名字对象是可告知控件。 ATL 实现返回 E_NOTIMPL。|
|[IOleObjectImpl::Unadvise](#unadvise)|删除与该控件的通知连接。|
|[IOleObjectImpl::Update](#update)|更新控件。 ATL 实现返回 S_OK。|

## <a name="remarks"></a>备注

[IOleObject](/windows/desktop/api/oleidl/nn-oleidl-ioleobject)接口是通过该容器与控件进行通信的主体接口。 类`IOleObjectImpl`提供默认实现此接口并实现`IUnknown`信息发送给转储调试中的设备生成。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>要求

**标头：** atlctl.h

##  <a name="advise"></a>  IOleObjectImpl::Advise

建立与该控件的通知连接。

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>备注

请参阅[IOleObject::Advise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-advise) Windows SDK 中。

##  <a name="close"></a>  IOleObjectImpl::Close

从运行加载到控件状态更改。

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>备注

停用该控件并销毁控件窗口，如果它存在。 如果该控件类数据成员[CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave)为 TRUE 并*dwSaveOption*参数为 OLECLOSE_SAVEIFDIRTY 或 OLECLOSE_PROMPTSAVE，控件属性关闭之前保存。

指针位于控件类数据成员[CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite)并[CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)会被释放，和数据成员[CComControlBase::m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd)， [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)，和[CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex)设置为 FALSE。

请参阅[IOleObject::Close](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-close) Windows SDK 中。

##  <a name="doverb"></a>  IOleObjectImpl::DoVerb

指示要执行一个其枚举操作的控件。

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

具体取决于值`iVerb`，其中一个 ATL`DoVerb`帮助程序函数调用，如下所示：

|*iVerb*值|名为 DoVerb 帮助器函数|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

请参阅[IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) Windows SDK 中。

##  <a name="doverbdiscardundo"></a>  IOleObjectImpl::DoVerbDiscardUndo

告知要放弃为维护任何撤消状态的控件。

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>参数

*prcPosRec*  
[in]指针到矩形容器想要绘制到的控件。

*hwndParent*  
[in]包含控件的窗口的句柄。

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="doverbhide"></a>  IOleObjectImpl::DoVerbHide

停用和删除控件的用户界面，并隐藏控件。

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>参数

*prcPosRec*  
[in]指针到矩形容器想要绘制到的控件。

*hwndParent*  
[in]包含控件的窗口的句柄。 不使用 ATL 实现中。

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="doverbinplaceactivate"></a>  IOleObjectImpl::DoVerbInPlaceActivate

在运行控件和安装其窗口，但不会安装该控件的用户界面。

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>参数

*prcPosRec*  
[in]指针到矩形容器想要绘制到的控件。

*hwndParent*  
[in]包含控件的窗口的句柄。 不使用 ATL 实现中。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

通过调用激活就地控件[CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate)。 除非控件类数据成员`m_bWindowOnly`为 TRUE 时，`DoVerbInPlaceActivate`首次尝试激活该控件作为无窗口控件 (仅当容器支持的可能[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless))。 如果失败，该函数尝试激活具有扩展功能的控件 (仅当容器支持的可能[IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex))。 如果失败，该函数尝试激活具有任何扩展功能的控件 (仅当容器支持的可能[IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite))。 如果激活成功，该函数将通知容器控件已激活。

##  <a name="doverbopen"></a>  IOleObjectImpl::DoVerbOpen

导致要在单独的窗口将打开编辑的控件。

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>参数

*prcPosRec*  
[in]指针到矩形容器想要绘制到的控件。

*hwndParent*  
[in]包含控件的窗口的句柄。

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="doverbprimary"></a>  IOleObjectImpl::DoVerbPrimary

定义当用户双击该控件时所执行的操作。

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>参数

*prcPosRec*  
[in]指针到矩形容器想要绘制到的控件。

*hwndParent*  
[in]包含控件的窗口的句柄。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

默认情况下，设置要显示的属性页。 您可以覆盖此控件类来调用不同的行为上双击; 中例如，播放视频或转处于就地活动状态。

##  <a name="doverbshow"></a>  IOleObjectImpl::DoVerbShow

指示要使控件可见的容器。

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>参数

*prcPosRec*  
[in]指针到矩形容器想要绘制到的控件。

*hwndParent*  
[in]包含控件的窗口的句柄。 不使用 ATL 实现中。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="doverbuiactivate"></a>  IOleObjectImpl::DoVerbUIActivate

激活控件的用户界面，并通知该容器通过复合菜单替换为其菜单。

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>参数

*prcPosRec*  
[in]指针到矩形容器想要绘制到的控件。

*hwndParent*  
[in]包含控件的窗口的句柄。 不使用 ATL 实现中。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="enumadvise"></a>  IOleObjectImpl::EnumAdvise

提供了针对此控件的已注册通知连接的枚举。

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>备注

请参阅[IOleObject::EnumAdvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumadvise) Windows SDK 中。

##  <a name="enumverbs"></a>  IOleObjectImpl::EnumVerbs

通过调用提供的针对此控件的已注册操作 （谓词） 枚举`OleRegEnumVerbs`。

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>备注

可以将谓词添加到你的项目的.rgs 文件。 有关示例，请参阅 CIRCCTL。在 RGS [CIRC](../../visual-cpp-samples.md)示例。

请参阅[ioleobject:: Enumverbs](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumverbs) Windows SDK 中。

##  <a name="getclientsite"></a>  IOleObjectImpl::GetClientSite

将指针放在控件类数据成员[CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite)成*ppClientSite*并递增指针的引用计数。

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>备注

请参阅[IOleObject::GetClientSite](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getclientsite) Windows SDK 中。

##  <a name="getclipboarddata"></a>  IOleObjectImpl::GetClipboardData

从剪贴板检索数据。

```
STDMETHOD(GetClipboardData)(    
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleObject::GetClipboardData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) Windows SDK 中。

##  <a name="getextent"></a>  IOleObjectImpl::GetExtent

检索正在运行控件的显示尺寸以 HIMETRIC 为单位 （每个单位为 0.01 毫米）。

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>备注

大小存储在控件类数据成员[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。

请参阅[IOleObject::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getextent) Windows SDK 中。

##  <a name="getmiscstatus"></a>  IOleObjectImpl::GetMiscStatus

返回一个指向该控件的已注册的状态信息通过调用`OleRegGetMiscStatus`。

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>备注

状态信息包括支持的控件和呈现数据的行为。 可以将状态信息添加到你的项目的.rgs 文件。

请参阅[IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) Windows SDK 中。

##  <a name="getmoniker"></a>  IOleObjectImpl::GetMoniker

检索控件的名字对象。

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleObject::GetMoniker](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmoniker) Windows SDK 中。

##  <a name="getuserclassid"></a>  IOleObjectImpl::GetUserClassID

返回控件的类标识符。

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>备注

请参阅[IOleObject::GetUserClassID](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getuserclassid) Windows SDK 中。

##  <a name="getusertype"></a>  IOleObjectImpl::GetUserType

通过调用返回控件的用户类型名称`OleRegGetUserType`。

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>备注

用户类型名称用于在用户界面元素，如菜单和对话框中显示。 可以更改项目的.rgs 文件中的用户类型名称。

请参阅[IOleObject::GetUserType](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getusertype) Windows SDK 中。

##  <a name="initfromdata"></a>  IOleObjectImpl::InitFromData

初始化从所选数据控件。

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleObject::InitFromData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-initfromdata) Windows SDK 中。

##  <a name="isuptodate"></a>  IOleObjectImpl::IsUpToDate

检查该控件是最新的。

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IOleObject::IsUpToDate](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-isuptodate) Windows SDK 中。

##  <a name="onpostverbdiscardundo"></a>  IOleObjectImpl::OnPostVerbDiscardUndo

调用[DoVerbDiscardUndo](#doverbdiscardundo)放弃撤消状态后。

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

使用重写此方法执行后放弃撤消状态所需的代码。

##  <a name="onpostverbhide"></a>  IOleObjectImpl::OnPostVerbHide

调用[DoVerbHide](#doverbhide)控件隐藏后。

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

重写此方法，则隐藏该控件后执行所需的代码。

##  <a name="onpostverbinplaceactivate"></a>  IOleObjectImpl::OnPostVerbInPlaceActivate

调用[DoVerbInPlaceActivate](#doverbinplaceactivate)就地激活控件之后。

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

使用重写此方法就地激活控件后执行所需的代码。

##  <a name="onpostverbopen"></a>  IOleObjectImpl::OnPostVerbOpen

调用[DoVerbOpen](#doverbopen)进行编辑的单独窗口中打开该控件后。

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

重写此方法，你想进行编辑的单独窗口中打开该控件后执行的代码。

##  <a name="onpostverbshow"></a>  IOleObjectImpl::OnPostVerbShow

调用[DoVerbShow](#doverbshow)控件变得可见后。

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

使用重写此方法所需控件变得可见后执行的代码。

##  <a name="onpostverbuiactivate"></a>  IOleObjectImpl::OnPostVerbUIActivate

调用[DoVerbUIActivate](#doverbuiactivate)激活控件的用户界面后。

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

重写此方法所需执行激活控件的用户界面后的代码。

##  <a name="onpreverbdiscardundo"></a>  IOleObjectImpl::OnPreVerbDiscardUndo

调用[DoVerbDiscardUndo](#doverbdiscardundo)撤消之前，状态将被丢弃。

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要防止被放弃的撤消状态，请重写此方法返回的错误 HRESULT。

##  <a name="onpreverbhide"></a>  IOleObjectImpl::OnPreVerbHide

调用[DoVerbHide](#doverbhide)隐藏该控件之前。

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要防止控件被隐藏，重写此方法返回的错误 HRESULT。

##  <a name="onpreverbinplaceactivate"></a>  IOleObjectImpl::OnPreVerbInPlaceActivate

调用[DoVerbInPlaceActivate](#doverbinplaceactivate)就地激活控件之前。

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要防止控件被就地激活，重写此方法返回的错误 HRESULT。

##  <a name="onpreverbopen"></a>  IOleObjectImpl::OnPreVerbOpen

调用[DoVerbOpen](#doverbopen)已为编辑的单独窗口中打开该控件之前。

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要防止控件被打开以进行编辑的单独窗口中，重写此方法返回的错误 HRESULT。

##  <a name="onpreverbshow"></a>  IOleObjectImpl::OnPreVerbShow

调用[DoVerbShow](#doverbshow)控件变得可见之前。

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要防止控件被设置为可见，请重写此方法返回的错误 HRESULT。

##  <a name="onpreverbuiactivate"></a>  IOleObjectImpl::OnPreVerbUIActivate

调用[DoVerbUIActivate](#doverbuiactivate)控件的用户界面已被激活之前。

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要防止激活控件的用户界面，重写此方法返回的错误 HRESULT。

##  <a name="setclientsite"></a>  IOleObjectImpl::SetClientSite

该控件将告知其客户端站点容器中。

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>备注

该方法随后返回 S_OK。

请参阅[IOleObject::SetClientSite](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setclientsite) Windows SDK 中。

##  <a name="setcolorscheme"></a>  IOleObjectImpl::SetColorScheme

如果任何到控件的应用程序，建议配色方案。

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) Windows SDK 中。

##  <a name="setextent"></a>  IOleObjectImpl::SetExtent

设置控件的显示区域的范围。

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>备注

否则为`SetExtent`将指向的值存储`psizel`中的控件类数据成员[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。 此值为以 HIMETRIC 为单位 （每个单位为 0.01 毫米）。

如果该控件类数据成员[CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural)为 TRUE，`SetExtent`还存储指向的值`psizel`中的控件类数据成员[CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

如果该控件类数据成员[CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize)为 TRUE，`SetExtent`调用`SendOnDataChange`和`SendOnViewChange`通知注册控件大小都有建议持有者的所有通知接收器更改。

请参阅[IOleObject::SetExtent](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setextent) Windows SDK 中。

##  <a name="sethostnames"></a>  IOleObjectImpl::SetHostNames

通知控件容器应用程序和容器文档的名称。

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IOleObject::SetHostNames](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-sethostnames) Windows SDK 中。

##  <a name="setmoniker"></a>  IOleObjectImpl::SetMoniker

其名字对象是可告知控件。

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleObject::SetMoniker](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setmoniker) Windows SDK 中。

##  <a name="unadvise"></a>  IOleObjectImpl::Unadvise

删除通知连接存储在控件类`m_spOleAdviseHolder`数据成员。

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>备注

请参阅[IOleObject::Unadvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-unadvise) Windows SDK 中。

##  <a name="update"></a>  IOleObjectImpl::Update

更新控件。

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IOleObject::Update](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-update) Windows SDK 中。

## <a name="see-also"></a>请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)   
[ActiveX 控件接口](/windows/desktop/com/activex-controls-interfaces)   
[类概述](../../atl/atl-class-overview.md)
