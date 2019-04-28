---
title: COleControlSite 类
ms.date: 11/04/2016
f1_keywords:
- COleControlSite
- AFXOCC/COleControlSite
- AFXOCC/COleControlSite::COleControlSite
- AFXOCC/COleControlSite::BindDefaultProperty
- AFXOCC/COleControlSite::BindProperty
- AFXOCC/COleControlSite::CreateControl
- AFXOCC/COleControlSite::DestroyControl
- AFXOCC/COleControlSite::DoVerb
- AFXOCC/COleControlSite::EnableDSC
- AFXOCC/COleControlSite::EnableWindow
- AFXOCC/COleControlSite::FreezeEvents
- AFXOCC/COleControlSite::GetDefBtnCode
- AFXOCC/COleControlSite::GetDlgCtrlID
- AFXOCC/COleControlSite::GetEventIID
- AFXOCC/COleControlSite::GetExStyle
- AFXOCC/COleControlSite::GetProperty
- AFXOCC/COleControlSite::GetStyle
- AFXOCC/COleControlSite::GetWindowText
- AFXOCC/COleControlSite::InvokeHelper
- AFXOCC/COleControlSite::InvokeHelperV
- AFXOCC/COleControlSite::IsDefaultButton
- AFXOCC/COleControlSite::IsWindowEnabled
- AFXOCC/COleControlSite::ModifyStyle
- AFXOCC/COleControlSite::ModifyStyleEx
- AFXOCC/COleControlSite::MoveWindow
- AFXOCC/COleControlSite::QuickActivate
- AFXOCC/COleControlSite::SafeSetProperty
- AFXOCC/COleControlSite::SetDefaultButton
- AFXOCC/COleControlSite::SetDlgCtrlID
- AFXOCC/COleControlSite::SetFocus
- AFXOCC/COleControlSite::SetProperty
- AFXOCC/COleControlSite::SetPropertyV
- AFXOCC/COleControlSite::SetWindowPos
- AFXOCC/COleControlSite::SetWindowText
- AFXOCC/COleControlSite::ShowWindow
- AFXOCC/COleControlSite::GetControlInfo
- AFXOCC/COleControlSite::m_bIsWindowless
- AFXOCC/COleControlSite::m_ctlInfo
- AFXOCC/COleControlSite::m_dwEventSink
- AFXOCC/COleControlSite::m_dwMiscStatus
- AFXOCC/COleControlSite::m_dwPropNotifySink
- AFXOCC/COleControlSite::m_dwStyle
- AFXOCC/COleControlSite::m_hWnd
- AFXOCC/COleControlSite::m_iidEvents
- AFXOCC/COleControlSite::m_nID
- AFXOCC/COleControlSite::m_pActiveObject
- AFXOCC/COleControlSite::m_pCtrlCont
- AFXOCC/COleControlSite::m_pInPlaceObject
- AFXOCC/COleControlSite::m_pObject
- AFXOCC/COleControlSite::m_pWindowlessObject
- AFXOCC/COleControlSite::m_pWndCtrl
- AFXOCC/COleControlSite::m_rect
helpviewer_keywords:
- COleControlSite [MFC], COleControlSite
- COleControlSite [MFC], BindDefaultProperty
- COleControlSite [MFC], BindProperty
- COleControlSite [MFC], CreateControl
- COleControlSite [MFC], DestroyControl
- COleControlSite [MFC], DoVerb
- COleControlSite [MFC], EnableDSC
- COleControlSite [MFC], EnableWindow
- COleControlSite [MFC], FreezeEvents
- COleControlSite [MFC], GetDefBtnCode
- COleControlSite [MFC], GetDlgCtrlID
- COleControlSite [MFC], GetEventIID
- COleControlSite [MFC], GetExStyle
- COleControlSite [MFC], GetProperty
- COleControlSite [MFC], GetStyle
- COleControlSite [MFC], GetWindowText
- COleControlSite [MFC], InvokeHelper
- COleControlSite [MFC], InvokeHelperV
- COleControlSite [MFC], IsDefaultButton
- COleControlSite [MFC], IsWindowEnabled
- COleControlSite [MFC], ModifyStyle
- COleControlSite [MFC], ModifyStyleEx
- COleControlSite [MFC], MoveWindow
- COleControlSite [MFC], QuickActivate
- COleControlSite [MFC], SafeSetProperty
- COleControlSite [MFC], SetDefaultButton
- COleControlSite [MFC], SetDlgCtrlID
- COleControlSite [MFC], SetFocus
- COleControlSite [MFC], SetProperty
- COleControlSite [MFC], SetPropertyV
- COleControlSite [MFC], SetWindowPos
- COleControlSite [MFC], SetWindowText
- COleControlSite [MFC], ShowWindow
- COleControlSite [MFC], GetControlInfo
- COleControlSite [MFC], m_bIsWindowless
- COleControlSite [MFC], m_ctlInfo
- COleControlSite [MFC], m_dwEventSink
- COleControlSite [MFC], m_dwMiscStatus
- COleControlSite [MFC], m_dwPropNotifySink
- COleControlSite [MFC], m_dwStyle
- COleControlSite [MFC], m_hWnd
- COleControlSite [MFC], m_iidEvents
- COleControlSite [MFC], m_nID
- COleControlSite [MFC], m_pActiveObject
- COleControlSite [MFC], m_pCtrlCont
- COleControlSite [MFC], m_pInPlaceObject
- COleControlSite [MFC], m_pObject
- COleControlSite [MFC], m_pWindowlessObject
- COleControlSite [MFC], m_pWndCtrl
- COleControlSite [MFC], m_rect
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
ms.openlocfilehash: 31502f2ecda1c14cb68c83da98cf2b764baba461
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310378"
---
# <a name="colecontrolsite-class"></a>COleControlSite 类

提供自定义客户端控件接口支持。

## <a name="syntax"></a>语法

```
class COleControlSite : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleControlSite::COleControlSite](#colecontrolsite)|构造 `COleControlSite` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|将托管控件的默认属性绑定到数据源。|
|[COleControlSite::BindProperty](#bindproperty)|将所承载控件的属性绑定到数据源。|
|[COleControlSite::CreateControl](#createcontrol)|创建托管的 ActiveX 控件。|
|[COleControlSite::DestroyControl](#destroycontrol)|销毁所承载的控件。|
|[COleControlSite::DoVerb](#doverb)|执行所承载控件的特定谓词。|
|[COleControlSite::EnableDSC](#enabledsc)|使数据源控件站点。|
|[COleControlSite::EnableWindow](#enablewindow)|使控件站点。|
|[COleControlSite::FreezeEvents](#freezeevents)|指定控件站点接受事件。|
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|检索托管控件的默认按钮代码。|
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|检索控件的标识符。|
|[COleControlSite::GetEventIID](#geteventiid)|检索事件接口的托管控件的 ID。|
|[COleControlSite::GetExStyle](#getexstyle)|检索控件站点的扩展的样式。|
|[COleControlSite::GetProperty](#getproperty)|检索托管控件的特定属性。|
|[COleControlSite::GetStyle](#getstyle)|检索控件所在位置的样式。|
|[COleControlSite::GetWindowText](#getwindowtext)|检索所承载控件的文本。|
|[COleControlSite::InvokeHelper](#invokehelper)|调用托管控件的特定方法。|
|[COleControlSite::InvokeHelperV](#invokehelperv)|调用所承载控件的带变量参数列表的特定方法。|
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|确定控件是否在窗口中的默认按钮。|
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|检查控件站点的可见状态。|
|[COleControlSite::ModifyStyle](#modifystyle)|修改当前扩展样式的控件站点。|
|[COleControlSite::ModifyStyleEx](#modifystyleex)|修改控件站点的当前样式。|
|[COleControlSite::MoveWindow](#movewindow)|更改控件站点的位置。|
|[COleControlSite::QuickActivate](#quickactivate)|快速激活所承载的控件。|
|[COleControlSite::SafeSetProperty](#safesetproperty)|设置的属性或控件而不引发异常的可能性的方法。|
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|在窗口中设置的默认按钮。|
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|检索控件的标识符。|
|[COleControlSite::SetFocus](#setfocus)|将焦点设置到控件站点。|
|[COleControlSite::SetProperty](#setproperty)|设置托管控件的特定属性。|
|[COleControlSite::SetPropertyV](#setpropertyv)|设置托管控件的具有变量参数列表的特定属性。|
|[COleControlSite::SetWindowPos](#setwindowpos)|设置控件站点的位置。|
|[COleControlSite::SetWindowText](#setwindowtext)|设置托管控件的文本。|
|[COleControlSite::ShowWindow](#showwindow)|显示或隐藏控件站点。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[COleControlSite::GetControlInfo](#getcontrolinfo)|检索键盘信息和所承载的控件的助记键。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|确定所承载的控件是一个无窗口控件。|
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|包含处理控件的键盘上的信息。|
|[COleControlSite::m_dwEventSink](#m_dweventsink)|控件的连接点的 cookie。|
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|所承载的控件的其他状态。|
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|`IPropertyNotifySink`控件的 cookie。|
|[COleControlSite::m_dwStyle](#m_dwstyle)|所承载控件的样式。|
|[COleControlSite::m_hWnd](#m_hwnd)|控制站点的句柄。|
|[COleControlSite::m_iidEvents](#m_iidevents)|所承载的控件的事件接口 ID。|
|[COleControlSite::m_nID](#m_nid)|所承载控件的 ID。|
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|一个指向`IOleInPlaceActiveObject`所承载控件的对象。|
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|所承载控件的容器。|
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|一个指向`IOleInPlaceObject`所承载控件的对象。|
|[COleControlSite::m_pObject](#m_pobject)|一个指向`IOleObjectInterface`控件的接口。|
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|一个指向`IOleInPlaceObjectWindowless`控件的接口。|
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|指向托管控件的窗口对象的指针。|
|[COleControlSite::m_rect](#m_rect)|控制站点的维度。|

## <a name="remarks"></a>备注

此支持仅通过其嵌入的 ActiveX 控件获取的位置和其显示站点、 其名字对象，其用户界面，其环境属性和提供其容器的其他资源的范围有关的信息的主要方式。 `COleControlSite` 完全实现[IOleControlSite](/windows/desktop/api/ocidl/nn-ocidl-iolecontrolsite)， [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)， [IOleClientSite](/windows/desktop/api/oleidl/nn-oleidl-ioleclientsite)， [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)， `IBoundObjectSite`，`INotifyDBEvents`， [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md)接口。 此外，还实现 IDispatch 接口 （提供对环境属性和事件接收器的支持）。

若要创建使用 ActiveX 控件站点`COleControlSite`，从派生类`COleControlSite`。 在你`CWnd`的容器 （例如，在对话框中） 的派生的类重写`CWnd::CreateControlSite`函数。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>要求

**标头：** afxocc.h

##  <a name="binddefaultproperty"></a>  COleControlSite::BindDefaultProperty

将调用对象的默认简单绑定的属性，作为在类型库中标记绑定到基础数据源控件的数据源、 用户名、 密码和 SQL 属性定义的游标。

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
指定要绑定到数据源控件的数据绑定控件属性的 DISPID。

*vtProp*<br/>
指定要绑定的属性的类型，例如，VT_BSTR、 VT_VARIANT、 等等。

*szFieldName*<br/>
指定数据源控件，该属性将绑定到提供的游标中的列的名称。

*pDSCWnd*<br/>
一个指向`CWnd`-派生的对象，承载该属性将绑定到数据源控件。

### <a name="remarks"></a>备注

`CWnd`对象调用此函数必须是数据绑定控件。

##  <a name="bindproperty"></a>  COleControlSite::BindProperty

将调用对象的简单绑定的属性，作为在类型库中标记绑定到基础数据源控件的数据源、 用户名、 密码和 SQL 属性定义的游标。

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>参数

*dwDispId*<br/>
指定要绑定到数据源控件的数据绑定控件属性的 DISPID。

*pWndDSC*<br/>
一个指向`CWnd`-派生的对象，承载该属性将绑定到数据源控件。

### <a name="remarks"></a>备注

`CWnd`对象调用此函数必须是数据绑定控件。

##  <a name="colecontrolsite"></a>  COleControlSite::COleControlSite

构造一个新`COleControlSite`对象。

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>参数

*pCtrlCont*<br/>
指向控件的容器 （它表示承载 AtiveX 控件的窗口） 的指针。

### <a name="remarks"></a>备注

调用此函数[COccManager::CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer)函数。 自定义创建容器的详细信息，请参阅[COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite)。

##  <a name="createcontrol"></a>  COleControlSite::CreateControl

创建承载的 ActiveX 控件`COleControlSite`对象。

```
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist = NULL,
    BOOL bStorage = FALSE,
    BSTR bstrLicKey = NULL);

virtual HRESULT CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist = NULL,
    BOOL bStorage = FALSE,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>参数

*pWndCtrl*<br/>
指向表示控件的窗口对象的指针。

*clsid*<br/>
控件的唯一类 ID。

*lpszWindowName*<br/>
指向要在控件中显示的文本的指针。 设置 winodw 的标题或文本属性的值 （如果有）。

*dwStyle*<br/>
窗口样式。 下列出的可用样式**备注**部分。

*rect*<br/>
指定控件的大小和位置。 它可以是`CRect`对象或`RECT`结构。

*nID*<br/>
指定控件的子窗口 id。

*pPersist*<br/>
一个指向`CFile`包含控件的持久状态。 默认值为 NULL，指示该控件而不从任何持久性存储区中还原其状态初始化自身。 如果不为 NULL，它应该是一个指向`CFile`-派生对象，它包含控件的持久性数据的流或存储形式。 此数据可能已保存在客户端的上一个激活。 `CFile`可以包含其他数据，但必须在调用时将设置为持久性数据的第一个字节其读写指针`CreateControl`。

*bStorage*<br/>
指示是否在数据*pPersist*应解释为`IStorage`或`IStream`数据。 如果中的数据*pPersist*是存储*bStorage*应为 TRUE。 如果中的数据*pPersist*是一个流*bStorage*应为 FALSE。 默认值是 FALSE。

*bstrLicKey*<br/>
可选的许可证密钥数据。 仅用于创建控件需要运行时许可证密钥的情况下，需要此数据。 如果控件支持授权，则必须提供要成功完成的控件创建的许可证密钥。 默认值为 NULL。

*ppt*<br/>
一个指向`POINT`结构，其中包含控件的左上角。 值确定控件的大小*psize*。 *Ppt*并*psize*值是一种可选方法的指定大小和位置处于控件。

*psize*<br/>
一个指向`SIZE`结构，其中包含控件的大小。 值确定左上角*ppt*。 *Ppt*并*psize*值是一种可选方法的指定大小和位置处于控件。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

Windows 的一个子集*dwStyle*支持标志`CreateControl`:

- WS_VISIBLE 创建初始可见的窗口。 如果您希望控件立即，像普通窗口可见，则必须填写。

- WS_DISABLED 创建最初处于禁用状态的窗口。 被禁用的窗口不能接收来自用户的输入。 如果控件具有已启用属性可以设置。

- WS_BORDER 创建与细线边框的窗口。 如果控件具有 BorderStyle 属性可以设置。

- WS_GROUP 指定一组控件的第一个控件。 用户可以通过使用箭头键键盘焦点从一个控件组中更改为下一步。 定义与 WS_GROUP 样式后的第一个控件属于相同组的所有控件。 WS_GROUP 样式的下一个控件结束组，并启动下一个组。

- WS_TABSTOP 指定一个在用户按 TAB 键时可以接收键盘焦点的控件。 按 TAB 键将键盘焦点更改到 WS_TABSTOP 样式的下一个控件。

使用第二个重载来创建默认大小的控件。

##  <a name="destroycontrol"></a>  COleControlSite::DestroyControl

销毁`COleControlSite`对象。

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>返回值

非零，如果成功，否则为 0。

### <a name="remarks"></a>备注

一旦完成，该对象从内存中释放，且任何指向对象不再有效。

##  <a name="doverb"></a>  COleControlSite::DoVerb

执行指定的谓词。

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>参数

*nVerb*<br/>
指定要执行的谓词。 它可以包括以下项之一：

|“值”|含义|符号|
|-----------|-------------|------------|
|0|主谓词|OLEIVERB_PRIMARY|
|-1|辅助谓词|（无）|
|1|显示要编辑的对象。|OLEIVERB_SHOW|
|-2|编辑一个单独的窗口中的项。|OLEIVERB_OPEN|
|-3|隐藏对象。|OLEIVERB_HIDE|
|-4|控件被就地激活。|OLEIVERB_UIACTIVATE|
|-5|控件被就地激活，而无需附加用户界面元素。|OLEIVERB_INPLACEACTIVATE|
|-7|显示控件的属性。|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
指向导致要激活的项的消息。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

通过控件的直接调用此函数`IOleObject`接口以执行指定的谓词。 如果通过此函数调用将引发异常，则返回一个 HRESULT 错误代码。

有关详细信息，请参阅[IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) Windows SDK 中。

##  <a name="enabledsc"></a>  COleControlSite::EnableDSC

使数据源控件站点。

```
virtual void EnableDSC();
```

### <a name="remarks"></a>备注

由框架调用以启用并初始化数据源控件站点。 重写此函数可提供自定义的行为。

##  <a name="enablewindow"></a>  COleControlSite::EnableWindow

启用或禁用鼠标和键盘输入到控件站点。

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
指定是否启用或禁用窗口：如果窗口输入，则为已启用，否则为 FALSE，则为 TRUE。

### <a name="return-value"></a>返回值

非零，如果以前禁用的窗口，否则为 0。

##  <a name="freezeevents"></a>  COleControlSite::FreezeEvents

指定控件站点将处理还是忽略从控件触发的事件。

```
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>参数

*bFreeze*<br/>
指定控件所在位置是否希望停止接受事件。 如果该控件不接受事件，则非零值否则为零。

### <a name="remarks"></a>备注

如果*bFreeze*为 TRUE 时，控制站点请求要停止导事件的控件。 如果*bFreeze*为 FALSE 时，控制站点请求要继续触发事件的控件。

> [!NOTE]
>  该控件不需要停止触发事件，如果请求的控件站点。 它可以继续激发，但控件站点时将忽略所有后续事件。

##  <a name="getcontrolinfo"></a>  COleControlSite::GetControlInfo

检索有关控件的键盘助记键和键盘行为的信息。

```
void GetControlInfo();
```

### <a name="remarks"></a>备注

信息存储在[COleControlSite::m_ctlInfo](#m_ctlinfo)。

##  <a name="getdefbtncode"></a>  COleControlSite::GetDefBtnCode

确定控件是否为默认按钮。

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>返回值

可以是以下值之一：

- DLGC_DEFPUSHBUTTON 控件是对话框中的默认按钮。

- DLGC_UNDEFPUSHBUTTON 控件不是对话框中的默认按钮。

- **0**控件不是一个按钮。

##  <a name="getdlgctrlid"></a>  COleControlSite::GetDlgCtrlID

检索控件的标识符。

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>返回值

控件的对话框项标识符。

##  <a name="geteventiid"></a>  COleControlSite::GetEventIID

检索指向控件的默认事件接口的指针。

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>参数

*piid*<br/>
一个指向接口 id。

### <a name="return-value"></a>返回值

非零，如果成功，否则为 0。 如果成功， *piid*包含控件的默认事件接口的接口 ID。

##  <a name="getexstyle"></a>  COleControlSite::GetExStyle

检索窗口的扩展的样式。

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>返回值

控制窗口的扩展样式。

### <a name="remarks"></a>备注

若要检索的正则样式，请调用[COleControlSite::GetStyle](#getstyle)。

##  <a name="getproperty"></a>  COleControlSite::GetProperty

获取指定的控件属性*dwDispID*。

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识控件的默认上找到的属性的调度 ID`IDispatch`接口，以检索。

*vtProp*<br/>
指定要检索的属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*pvProp*<br/>
将接收属性值的变量的地址。 它必须匹配指定的类型*vtProp*。

### <a name="remarks"></a>备注

通过返回的值*pvProp*。

##  <a name="getstyle"></a>  COleControlSite::GetStyle

检索控件所在位置的样式。

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>返回值

窗口样式。

### <a name="remarks"></a>备注

有关可能的值的列表，请参阅[Windows 样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 若要检索的控件站点的扩展的样式，请调用[COleControlSite::GetExStyle](#getexstyle)。

##  <a name="getwindowtext"></a>  COleControlSite::GetWindowText

检索控件的当前文本。

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>参数

*str*<br/>
对引用`CString`对象，其中包含该控件的当前文本。

### <a name="remarks"></a>备注

如果该控件支持标题常用属性，则返回此值。 如果不支持标题常用属性，则返回的 Text 属性的值。

##  <a name="invokehelper"></a>  COleControlSite::InvokeHelper

调用的方法或属性指定的*dwDispID*，在指定的上下文*wFlags*。

```
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识属性或方法，在控件上找到的调度 ID`IDispatch`接口，以调用。

*wFlags*<br/>
描述对 idispatch:: Invoke 调用的上下文的标志。 有关可能*wFlags*值，请参阅`IDispatch::Invoke`Windows SDK 中。

*vtRet*<br/>
指定返回值的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*pvRet*<br/>
将接收属性值或返回值的变量的地址。 它必须匹配指定的类型*vtRet*。

*pbParamInfo*<br/>
指向以 null 结尾字节指定后面的参数的类型的字符串指针*pbParamInfo*。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*...*<br/>
参数中指定的类型的变量列表*pbParamInfo*。

### <a name="remarks"></a>备注

*PbParamInfo*参数指定的参数传递到方法或属性的类型。 变量参数列表是由表示...语法声明中。

此函数将参数转换为 VARIANTARG 值，然后调用`IDispatch::Invoke`在控件上的方法。 如果 `IDispatch::Invoke` 调用失败，则此函数会引发异常。 如果返回状态代码`IDispatch::Invoke`是`DISP_E_EXCEPTION`，此函数将引发`COleDispatchException`对象中，否则为它会引发`COleException`。

##  <a name="invokehelperv"></a>  COleControlSite::InvokeHelperV

调用的方法或属性指定的*dwDispID*，在指定的上下文*wFlags*。

```
virtual void InvokeHelperV(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo,
    va_list argList);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识属性或方法，在控件上找到的调度 ID`IDispatch`接口，以调用。

*wFlags*<br/>
描述对 idispatch:: Invoke 调用的上下文的标志。

*vtRet*<br/>
指定返回值的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*pvRet*<br/>
将接收属性值或返回值的变量的地址。 它必须匹配指定的类型*vtRet*。

*pbParamInfo*<br/>
指向以 null 结尾字节指定后面的参数的类型的字符串指针*pbParamInfo*。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*argList*<br/>
到变量自变量列表的指针。

### <a name="remarks"></a>备注

*PbParamInfo*参数指定的参数传递到方法或属性的类型。 可以使用传递额外参数的方法或属性调用*va_list*参数。

通常情况下，调用此函数`COleControlSite::InvokeHelper`。

##  <a name="isdefaultbutton"></a>  COleControlSite::IsDefaultButton

确定控件是否为默认按钮。

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>返回值

如果该控件为非零的默认按钮在窗口中，否则为零。

##  <a name="iswindowenabled"></a>  COleControlSite::IsWindowEnabled

确定是否启用控件站点。

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>返回值

非零值如果启用该控件，否则为零。

### <a name="remarks"></a>备注

从控件的已启用常用属性检索的值。

##  <a name="m_biswindowless"></a>  COleControlSite::m_bIsWindowless

确定对象是否无窗口控件。

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>备注

非零值如果控件具有没有窗口，否则为零。

##  <a name="m_ctlinfo"></a>  COleControlSite::m_ctlInfo

控制如何处理键盘输入的信息。

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>备注

此信息存储在[CONTROLINFO](/windows/desktop/api/ocidl/ns-ocidl-tagcontrolinfo)结构。

##  <a name="m_dweventsink"></a>  COleControlSite::m_dwEventSink

包含控件的事件接收器的连接点的 cookie。

```
DWORD m_dwEventSink;
```

##  <a name="m_dwmiscstatus"></a>  COleControlSite::m_dwMiscStatus

包含有关控件的其他信息。

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc)Windows SDK 中。

##  <a name="m_dwpropnotifysink"></a>  COleControlSite::m_dwPropNotifySink

包含[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) cookie。

```
DWORD m_dwPropNotifySink;
```

##  <a name="m_dwstyle"></a>  COleControlSite::m_dwStyle

包含控件的窗口样式。

```
DWORD m_dwStyle;
```

##  <a name="m_hwnd"></a>  COleControlSite::m_hWnd

如果无窗口控件，包含的 HWND 的控件，则为 NULL。

```
HWND m_hWnd;
```

##  <a name="m_iidevents"></a>  COleControlSite::m_iidEvents

包含控件的默认事件接收器接口的接口 ID。

```
IID m_iidEvents;
```

##  <a name="m_nid"></a>  COleControlSite::m_nID

包含控件的对话框项的 id。

```
UINT m_nID;
```

##  <a name="m_pactiveobject"></a>  COleControlSite::m_pActiveObject

包含[IOleInPlaceActiveObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceactiveobject)控件的接口。

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

##  <a name="m_pctrlcont"></a>  COleControlSite::m_pCtrlCont

包含控件的容器 （表示形式）。

```
COleControlContainer* m_pCtrlCont;
```

##  <a name="m_pinplaceobject"></a>  COleControlSite::m_pInPlaceObject

包含`IOleInPlaceObject` [IOleInPlaceObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceobject)控件的接口。

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

##  <a name="m_pobject"></a>  COleControlSite::m_pObject

包含`IOleObjectInterface`控件的接口。

```
LPOLEOBJECT m_pObject;
```

##  <a name="m_pwindowlessobject"></a>  COleControlSite::m_pWindowlessObject

包含`IOleInPlaceObjectWindowless` [IOleInPlaceObjectWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)控件的接口。

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

##  <a name="m_pwndctrl"></a>  COleControlSite::m_pWndCtrl

包含一个指向`CWnd`对象，表示在控件自身。

```
CWnd* m_pWndCtrl;
```

##  <a name="m_rect"></a>  COleControlSite::m_rect

包含控件，相对于容器的窗口边界。

```
CRect m_rect;
```

##  <a name="modifystyle"></a>  COleControlSite::ModifyStyle

修改控件的样式。

```
virtual BOOL ModifyStyle(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>参数

*dwRemove*<br/>
要删除从当前窗口样式的样式。

*dwAdd*<br/>
要添加从当前窗口样式的样式。

*nFlags*<br/>
窗口定位标志。 有关可能的值的列表，请参阅[SetWindowPos](/windows/desktop/api/winuser/nf-winuser-setwindowpos) Windows SDK 中的函数。

### <a name="return-value"></a>返回值

如果更改样式，否则为零，非零值。

### <a name="remarks"></a>备注

将修改控件的股票 Enabled 属性来匹配 WS_DISABLED 的设置。 将修改控件的边框样式的常用属性以匹配为 WS_BORDER 所请求的设置。 所有其他样式是直接应用于控件的窗口句柄，如果不存在。

修改控件的窗口样式。 可以通过使用按位 OR 组合样式来添加或删除 ( &#124; ) 运算符。 请参阅[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa)适用于有关可用的窗口样式的信息的 Windows SDK 中的函数。

如果*nFlags*为非零值，`ModifyStyle`调用 Win32 函数`SetWindowPos`，并通过组合重绘的窗口*nFlags*与以下四个标志：

- SWP_NOSIZE 保留当前的大小。

- SWP_NOMOVE 保留当前的位置。

- SWP_NOZORDER 保留当前的 Z 顺序。

- SWP_NOACTIVATE 不会激活窗口。

若要修改一个窗口的扩展样式，请调用[ModifyStyleEx](#modifystyleex)。

##  <a name="modifystyleex"></a>  COleControlSite::ModifyStyleEx

修改控件的扩展的样式。

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>参数

*dwRemove*<br/>
若要从当前窗口样式删除扩展的样式。

*dwAdd*<br/>
若要从当前窗口样式添加扩展的样式。

*nFlags*<br/>
窗口定位标志。 有关可能的值的列表，请参阅[SetWindowPos](/windows/desktop/api/winuser/nf-winuser-setwindowpos) Windows SDK 中的函数。

### <a name="return-value"></a>返回值

如果更改样式，否则为零，非零值。

### <a name="remarks"></a>备注

将修改控件的股票外观属性来匹配 WS_EX_CLIENTEDGE 的设置。 所有其他扩展的窗口样式是直接应用于控件的窗口句柄，如果不存在。

修改扩展的控件站点对象的样式的窗口。 可以通过使用按位 OR 组合样式来添加或删除 ( &#124; ) 运算符。 请参阅[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)适用于有关可用的窗口样式的信息的 Windows SDK 中的函数。

如果*nFlags*为非零值，`ModifyStyleEx`调用 Win32 函数`SetWindowPos`，并通过组合重绘的窗口*nFlags*与以下四个标志：

- SWP_NOSIZE 保留当前的大小。

- SWP_NOMOVE 保留当前的位置。

- SWP_NOZORDER 保留当前的 Z 顺序。

- SWP_NOACTIVATE 不会激活窗口。

若要修改一个窗口的扩展样式，请调用[ModifyStyle](#modifystyle)。

##  <a name="movewindow"></a>  COleControlSite::MoveWindow

更改控件的位置。

```
virtual void MoveWindow(
    int x,
    int y,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>参数

*x*<br/>
左侧和右侧窗口的新位置。

*y*<br/>
新的窗口的顶部位置。

*nWidth*<br/>
新窗口的宽度

*nHeight*<br/>
新窗口的高度。

##  <a name="quickactivate"></a>  COleControlSite::QuickActivate

快速激活所包含的控件。

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>返回值

非零值控制站点已激活，否则为零。

### <a name="remarks"></a>备注

仅当用户重写控件的创建过程，应调用此函数。

`IPersist*::Load`和`IPersist*::InitNew`快速激活发生后应调用的方法。 该控件应在快速激活过程中建立它与容器的接收器的连接。 但是，这些连接不是实时直到`IPersist*::Load`或`IPersist*::InitNew`已调用。

##  <a name="safesetproperty"></a>  COleControlSite::SafeSetProperty

设置指定的控件属性*dwDispID*。

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识属性或方法，在控件上找到的调度 ID`IDispatch`接口，以设置。

*vtProp*<br/>
指定要设置属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*...*<br/>
指定的类型的单个参数*vtProp*。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

> [!NOTE]
>  与不同`SetProperty`和`SetPropertyV`，如果遇到错误 （如尝试设置不存在的属性），不会引发异常。

##  <a name="setdefaultbutton"></a>  COleControlSite::SetDefaultButton

将控件设置为默认按钮。

```
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>参数

*bDefault*<br/>
如果控件应成为默认按钮，则非零值否则为零。

### <a name="remarks"></a>备注

> [!NOTE]
>  控件必须具有 OLEMISC_ACTSLIKEBUTTON 位的状态集。

##  <a name="setdlgctrlid"></a>  COleControlSite::SetDlgCtrlID

更改控件的对话框中的项标识符的值。

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
新的标识符值。

### <a name="return-value"></a>返回值

如果成功上, 一对话框项窗口; 的标识符否则为 0。

### <a name="remarks"></a>备注

##  <a name="setfocus"></a>  COleControlSite::SetFocus

将焦点设置到控件。

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>参数

*lpmsg*<br/>
一个指向[MSG 结构](/windows/desktop/api/winuser/ns-winuser-tagmsg)。 此结构包含的 Windows 消息触发`SetFocus`请求包含当前控件站点中的控件。

### <a name="return-value"></a>返回值

指向以前具有焦点的窗口的指针。

##  <a name="setproperty"></a>  COleControlSite::SetProperty

设置指定的控件属性*dwDispID*。

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识属性或方法，在控件上找到的调度 ID`IDispatch`接口，以设置。

*vtProp*<br/>
指定要设置属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*...*<br/>
指定的类型的单个参数*vtProp*。

### <a name="remarks"></a>备注

如果`SetProperty`遇到的错误，将引发异常。

尝试设置属性或方法的返回值确定异常的类型。 如果返回值是`DISP_E_EXCEPTION`、 一个`COleDispatchExcpetion`则引发该异常; 否则为`COleException`。

##  <a name="setpropertyv"></a>  COleControlSite::SetPropertyV

设置指定的控件属性*dwDispID*。

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识属性或方法，在控件上找到的调度 ID`IDispatch`接口，以设置。

*vtProp*<br/>
指定要设置属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*argList*<br/>
指向参数列表的指针。

### <a name="remarks"></a>备注

为方法或属性进行调用的额外参数可以是 passeed 使用*arg_list*参数。 如果`SetProperty`遇到的错误，将引发异常。

尝试设置属性或方法的返回值确定异常的类型。 如果返回值是`DISP_E_EXCEPTION`、 一个`COleDispatchExcpetion`则引发该异常; 否则为`COleException`。

##  <a name="setwindowpos"></a>  COleControlSite::SetWindowPos

设置大小、 位置和控件站点的 Z 顺序。

```
virtual BOOL SetWindowPos(
    const CWnd* pWndInsertAfter,
    int x,
    int y,
    int cx,
    int cy,
    UINT nFlags);
```

### <a name="parameters"></a>参数

*pWndInsertAfter*<br/>
指向窗口的指针。

*x*<br/>
左侧和右侧窗口的新位置。

*y*<br/>
新的窗口的顶部位置。

*cx*<br/>
新窗口的宽度

*cy*<br/>
新窗口的高度。

*nFlags*<br/>
指定窗口大小调整和定位标志。 有关可能的值，请参阅备注部分[SetWindowPos](/windows/desktop/api/winuser/nf-winuser-setwindowpos) Windows SDK 中。

### <a name="return-value"></a>返回值

非零值如果成功，否则为零。

##  <a name="setwindowtext"></a>  COleControlSite::SetWindowText

设置该控件站点的文本。

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*lpszString*<br/>
指向以 null 结尾的字符串，要用作新的标题或控件文本。

### <a name="remarks"></a>备注

此函数首先尝试设置标题的常用属性。 如果不支持标题常用属性，而是设置的 Text 属性。

##  <a name="showwindow"></a>  COleControlSite::ShowWindow

设置窗口的显示状态。

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>参数

*nCmdShow*<br/>
指定控件所在位置的显示方式。 它必须是以下值之一：

- SW_HIDE 隐藏此窗口，并将激活传递到另一个窗口。

- SW_MINIMIZE 最小化窗口，并激活系统的列表中的顶级窗口。

- SW_RESTORE 激活并显示窗口。 如果最小化或最大化窗口，Windows 会将其还原到其原始大小和位置。

- SW_SHOW 激活窗口并将其显示在其当前大小和位置。

- SW_SHOWMAXIMIZED 激活窗口，并将其显示为最大化窗口。

- SW_SHOWMINIMIZED 激活窗口，并将其显示为一个图标。

- SW_SHOWMINNOACTIVE 以图标形式显示的窗口。 当前处于活动状态的窗口将保持活动状态。

- SW_SHOWNA 在其当前状态将显示窗口。 当前处于活动状态的窗口将保持活动状态。

- SW_SHOWNOACTIVATE 显示窗口中的最新的大小和位置。 当前处于活动状态的窗口将保持活动状态。

- SW_SHOWNORMAL 激活并显示窗口。 如果最小化或最大化窗口，Windows 会将其还原到其原始大小和位置。

### <a name="return-value"></a>返回值

如果窗口是以前可见，则非零值如果以前隐藏的窗口，则为 0。

## <a name="see-also"></a>请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleControlContainer 类](../../mfc/reference/colecontrolcontainer-class.md)
