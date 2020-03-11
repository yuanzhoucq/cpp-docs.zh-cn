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
ms.openlocfilehash: ded158b0ec862de5b0d0b23dd4b9edb50ad577ef
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862903"
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl 类

此类实现 `IUnknown`，它是容器与控件进行通信时所使用的主要接口。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>parameters

*T*<br/>
派生自 `IOleObjectImpl`的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IOleObjectImpl：： Advise](#advise)|建立与控件的通知连接。|
|[IOleObjectImpl：： Close](#close)|将控件状态从 "正在运行" 更改为 "已加载"。|
|[IOleObjectImpl：:D oVerb](#doverb)|通知控件执行它的一个枚举操作。|
|[IOleObjectImpl：:D oVerbDiscardUndo](#doverbdiscardundo)|通知控件丢弃其维护的任何撤消状态。|
|[IOleObjectImpl：:D oVerbHide](#doverbhide)|通知控件从视图中删除其用户界面。|
|[IOleObjectImpl：:D oVerbInPlaceActivate](#doverbinplaceactivate)|运行控件并安装其窗口，但不安装控件的用户界面。|
|[IOleObjectImpl：:D oVerbOpen](#doverbopen)|使控件在单独的窗口中打开编辑。|
|[IOleObjectImpl：:D oVerbPrimary](#doverbprimary)|当用户双击控件时，执行指定的操作。 控件定义操作，通常用于就地激活控件。|
|[IOleObjectImpl：:D oVerbShow](#doverbshow)|向用户显示新插入的控件。|
|[IOleObjectImpl：:D oVerbUIActivate](#doverbuiactivate)|就地激活控件并显示控件的用户界面，如菜单和工具栏。|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|枚举控件的通知连接。|
|[IOleObjectImpl：： EnumVerbs](#enumverbs)|枚举控件的操作。|
|[IOleObjectImpl::GetClientSite](#getclientsite)|检索控件的客户端站点。|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|从剪贴板检索数据。 ATL 实现返回 E_NOTIMPL。|
|[IOleObjectImpl::GetExtent](#getextent)|检索控件的显示区域的范围。|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|检索控件的状态。|
|[IOleObjectImpl：： GetMoniker](#getmoniker)|检索控件的名字对象。 ATL 实现返回 E_NOTIMPL。|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|检索控件的类标识符。|
|[IOleObjectImpl::GetUserType](#getusertype)|检索控件的用户类型名称。|
|[IOleObjectImpl::InitFromData](#initfromdata)|从所选数据中初始化控件。 ATL 实现返回 E_NOTIMPL。|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|检查控件是否为最新。 ATL 实现返回 S_OK。|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|在放弃撤消状态之后由[DoVerbDiscardUndo](#doverbdiscardundo)调用。|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|在隐藏控件后由[DoVerbHide](#doverbhide)调用。|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|就地激活控件后，由[DoVerbInPlaceActivate](#doverbinplaceactivate)调用。|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|在控件已打开以便在单独的窗口中进行编辑后，由[DoVerbOpen](#doverbopen)调用。|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|使控件可见后，由[DoVerbShow](#doverbshow)调用。|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|在控件的用户界面激活后，由[DoVerbUIActivate](#doverbuiactivate)调用。|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|在撤消状态被丢弃之前由[DoVerbDiscardUndo](#doverbdiscardundo)调用。|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|在隐藏控件之前由[DoVerbHide](#doverbhide)调用。|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|就地激活控件之前，由[DoVerbInPlaceActivate](#doverbinplaceactivate)调用。|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|在控件已打开以便在单独的窗口中进行编辑之前，由[DoVerbOpen](#doverbopen)调用。|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|在控件变为可见之前由[DoVerbShow](#doverbshow)调用。|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|在控件的用户界面激活之前由[DoVerbUIActivate](#doverbuiactivate)调用。|
|[IOleObjectImpl::SetClientSite](#setclientsite)|向控件通知容器中的客户端站点。|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|为控件的应用程序推荐配色方案（如果有）。 ATL 实现返回 E_NOTIMPL。|
|[IOleObjectImpl：： SetExtent](#setextent)|设置控件显示区的范围。|
|[IOleObjectImpl::SetHostNames](#sethostnames)|向控件通知容器应用程序和容器文档的名称。|
|[IOleObjectImpl::SetMoniker](#setmoniker)|通知控件其名字对象是什么。 ATL 实现返回 E_NOTIMPL。|
|[IOleObjectImpl::Unadvise](#unadvise)|删除与控件的通知连接。|
|[IOleObjectImpl：： Update](#update)|更新控件。 ATL 实现返回 S_OK。|

## <a name="remarks"></a>备注

[IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject)接口是容器与控件进行通信时所使用的主体接口。 类 `IOleObjectImpl` 提供此接口的默认实现，并通过在调试版本中将信息发送到转储设备来实现 `IUnknown`。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 atl 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>要求

**标头：** atlctl

##  <a name="advise"></a>IOleObjectImpl：： Advise

建立与控件的通知连接。

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleObject：： Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) 。

##  <a name="close"></a>IOleObjectImpl：： Close

将控件状态从 "正在运行" 更改为 "已加载"。

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>备注

停用控件并销毁控件窗口（如果它存在）。 如果控件类数据成员[CComControlBase：： m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave)为 TRUE，并且*dwSaveOption*参数 OLECLOSE_SAVEIFDIRTY 或 OLECLOSE_PROMPTSAVE，则在关闭之前保存控件属性。

控制类数据成员[CComControlBase：： m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite)和[CComControlBase：： m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)中包含的指针已释放，并且数据成员[CComControlBase：： m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd)、 [CComControlBase：： m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)和[CComControlBase：： m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex)设置为 FALSE。

请参阅 Windows SDK 中的[IOleObject：： Close](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close) 。

##  <a name="doverb"></a>IOleObjectImpl：:D oVerb

通知控件执行它的一个枚举操作。

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

根据 `iVerb`的值，将调用其中一个 ATL `DoVerb` helper 函数，如下所示：

|*iVerb*负值|已调用 DoVerb helper 函数|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase：:D oVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

请参阅 IOleObject： Windows SDK 中的[：:D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 。

##  <a name="doverbdiscardundo"></a>IOleObjectImpl：:D oVerbDiscardUndo

通知控件丢弃其维护的任何撤消状态。

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>parameters

*prcPosRec*<br/>
中一个指针，指向容器希望控件绘制到的矩形。

*hwndParent*<br/>
中包含控件的窗口的句柄。

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="doverbhide"></a>IOleObjectImpl：:D oVerbHide

停用并删除控件的用户界面，并隐藏控件。

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>parameters

*prcPosRec*<br/>
中一个指针，指向容器希望控件绘制到的矩形。

*hwndParent*<br/>
中包含控件的窗口的句柄。 不在 ATL 实现中使用。

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="doverbinplaceactivate"></a>IOleObjectImpl：:D oVerbInPlaceActivate

运行控件并安装其窗口，但不安装控件的用户界面。

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>parameters

*prcPosRec*<br/>
中一个指针，指向容器希望控件绘制到的矩形。

*hwndParent*<br/>
中包含控件的窗口的句柄。 不在 ATL 实现中使用。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

通过调用[CComControlBase：： InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate)就地激活控件。 除非控件类的数据成员 `m_bWindowOnly` 为 TRUE，否则 `DoVerbInPlaceActivate` 首先尝试将控件作为无窗口控件来激活（仅当容器支持[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)时可能）。 如果此操作失败，则该函数尝试激活具有扩展功能的控件（仅当容器支持[IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)时可能）。 如果此操作失败，则该函数将尝试激活没有扩展功能的控件（仅当容器支持[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)时才可能）。 如果激活成功，则该函数将通知容器控件已激活。

##  <a name="doverbopen"></a>IOleObjectImpl：:D oVerbOpen

使控件在单独的窗口中打开编辑。

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>parameters

*prcPosRec*<br/>
中一个指针，指向容器希望控件绘制到的矩形。

*hwndParent*<br/>
中包含控件的窗口的句柄。

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="doverbprimary"></a>IOleObjectImpl：:D oVerbPrimary

定义用户双击控件时执行的操作。

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>parameters

*prcPosRec*<br/>
中一个指针，指向容器希望控件绘制到的矩形。

*hwndParent*<br/>
中包含控件的窗口的句柄。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

默认情况下，设置以显示属性页。 可以在控件类中重写此项，以便在双击时调用不同的行为;例如，播放视频或就地激活。

##  <a name="doverbshow"></a>IOleObjectImpl：:D oVerbShow

通知容器使控件可见。

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>parameters

*prcPosRec*<br/>
中一个指针，指向容器希望控件绘制到的矩形。

*hwndParent*<br/>
中包含控件的窗口的句柄。 不在 ATL 实现中使用。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="doverbuiactivate"></a>IOleObjectImpl：:D oVerbUIActivate

激活控件的用户界面，并通知容器其菜单被复合菜单替换。

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>parameters

*prcPosRec*<br/>
中一个指针，指向容器希望控件绘制到的矩形。

*hwndParent*<br/>
中包含控件的窗口的句柄。 不在 ATL 实现中使用。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="enumadvise"></a>IOleObjectImpl::EnumAdvise

提供此控件的已注册通知连接的枚举。

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleObject：： EnumAdvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) 。

##  <a name="enumverbs"></a>IOleObjectImpl：： EnumVerbs

通过调用 `OleRegEnumVerbs`为此控件提供已注册操作（谓词）的枚举。

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>备注

可以向项目的 .rgs 文件添加谓词。 例如，请参阅 CIRCCTL。[CIRC](../../overview/visual-cpp-samples.md)示例中的 RGS。

请参阅 Windows SDK 中的[IOleObject：： EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) 。

##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite

将控件类数据成员[CComControlBase：： m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite)中的指针放入*ppClientSite* ，并递增指针上的引用计数。

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleObject：： GetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite) 。

##  <a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData

从剪贴板检索数据。

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleObject：： GetClipboardData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) 。

##  <a name="getextent"></a>IOleObjectImpl::GetExtent

以 HIMETRIC 单位（每个单位0.01 毫米）检索正在运行的控件的显示大小。

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>备注

大小存储在 control 类数据成员[CComControlBase：： m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)中。

请参阅 Windows SDK 中的[IOleObject：： GetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent) 。

##  <a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus

通过调用 `OleRegGetMiscStatus`，返回指向控件的已注册状态信息的指针。

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>备注

状态信息包括控件和显示数据所支持的行为。 您可以将状态信息添加到您的项目的 .rgs 文件中。

请参阅 Windows SDK 中的[IOleObject：： GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) 。

##  <a name="getmoniker"></a>IOleObjectImpl：： GetMoniker

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

请参阅 Windows SDK 中的[IOleObject：： GetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker) 。

##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID

返回控件的类标识符。

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleObject：： GetUserClassID](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid) 。

##  <a name="getusertype"></a>IOleObjectImpl::GetUserType

通过调用 `OleRegGetUserType`返回控件的用户类型名称。

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>备注

用户类型名称用于在用户界面元素（如菜单和对话框）中显示。 可以在项目的 .rgs 文件中更改用户类型名称。

请参阅 Windows SDK 中的[IOleObject：： GetUserType](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype) 。

##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData

从所选数据中初始化控件。

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleObject：： InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) 。

##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate

检查控件是否为最新。

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleObject：： IsUpToDate](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate) 。

##  <a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo

在放弃撤消状态之后由[DoVerbDiscardUndo](#doverbdiscardundo)调用。

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

在放弃撤消状态之后要执行的代码重写此方法。

##  <a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide

在隐藏控件后由[DoVerbHide](#doverbhide)调用。

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

在隐藏控件后执行要执行的代码，重写此方法。

##  <a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate

就地激活控件后，由[DoVerbInPlaceActivate](#doverbinplaceactivate)调用。

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

在就地激活控件后要执行的代码重写此方法。

##  <a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen

在控件已打开以便在单独的窗口中进行编辑后，由[DoVerbOpen](#doverbopen)调用。

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

在单独的窗口中打开要编辑的控件后要执行的代码重写此方法。

##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow

使控件可见后，由[DoVerbShow](#doverbshow)调用。

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

用要在控件可见后执行的代码重写此方法。

##  <a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate

在控件的用户界面激活后，由[DoVerbUIActivate](#doverbuiactivate)调用。

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

用要在控件的用户界面激活后执行的代码重写此方法。

##  <a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo

在撤消状态被丢弃之前由[DoVerbDiscardUndo](#doverbdiscardundo)调用。

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要防止撤消状态被丢弃，请重写此方法以返回错误 HRESULT。

##  <a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide

在隐藏控件之前由[DoVerbHide](#doverbhide)调用。

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要防止控件被隐藏，请重写此方法以返回错误 HRESULT。

##  <a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate

就地激活控件之前，由[DoVerbInPlaceActivate](#doverbinplaceactivate)调用。

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要禁止就地激活控件，请重写此方法以返回错误 HRESULT。

##  <a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen

在控件已打开以便在单独的窗口中进行编辑之前，由[DoVerbOpen](#doverbopen)调用。

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要防止在单独的窗口中打开控件进行编辑，请重写此方法以返回错误 HRESULT。

##  <a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow

在控件变为可见之前由[DoVerbShow](#doverbshow)调用。

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要禁止使控件可见，请重写此方法以返回错误 HRESULT。

##  <a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate

在控件的用户界面激活之前由[DoVerbUIActivate](#doverbuiactivate)调用。

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要防止激活控件的用户界面，请重写此方法以返回错误 HRESULT。

##  <a name="setclientsite"></a>IOleObjectImpl::SetClientSite

向控件通知容器中的客户端站点。

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>备注

然后，该方法返回 S_OK。

请参阅 Windows SDK 中的[IOleObject：： SetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite) 。

##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme

为控件的应用程序推荐配色方案（如果有）。

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleObject：： SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) 。

##  <a name="setextent"></a>IOleObjectImpl：： SetExtent

设置控件显示区的范围。

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>备注

否则，`SetExtent` 会在 control 类数据成员[CComControlBase：： m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)中存储 `psizel` 指向的值。 此值为 HIMETRIC 单位（每个单位0.01 毫米）。

如果控件类数据成员[CComControlBase：： m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural)为 TRUE，`SetExtent` 还会通过在 control 类数据成员[CComControlBase：： m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)中 `psizel` 来存储指向的值。

如果控件类数据成员[CComControlBase：： m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize)为 TRUE，`SetExtent` 将调用 `SendOnDataChange` 和 `SendOnViewChange` 以通知所有注册了通知持有人的通知接收器控件大小已更改。

请参阅 Windows SDK 中的[IOleObject：： SetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent) 。

##  <a name="sethostnames"></a>IOleObjectImpl::SetHostNames

向控件通知容器应用程序和容器文档的名称。

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleObject：： SetHostNames](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames) 。

##  <a name="setmoniker"></a>IOleObjectImpl::SetMoniker

通知控件其名字对象是什么。

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleObject：： SetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker) 。

##  <a name="unadvise"></a>IOleObjectImpl::Unadvise

删除控件类的 `m_spOleAdviseHolder` 数据成员中存储的通知连接。

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleObject：： Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) 。

##  <a name="update"></a>IOleObjectImpl：： Update

更新控件。

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleObject：： Update](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update) 。

## <a name="see-also"></a>另请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控件接口](/windows/win32/com/activex-controls-interfaces)<br/>
[类概述](../../atl/atl-class-overview.md)
