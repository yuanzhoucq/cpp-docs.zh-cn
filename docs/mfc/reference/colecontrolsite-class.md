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
ms.openlocfilehash: 9b9b68a001acdf4b08d9cfc01cc67c43217d9a57
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504305"
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
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|将所承载控件的默认属性绑定到数据源。|
|[COleControlSite::BindProperty](#bindproperty)|将所承载控件的属性绑定到数据源。|
|[COleControlSite::CreateControl](#createcontrol)|创建承载的 ActiveX 控件。|
|[COleControlSite::DestroyControl](#destroycontrol)|销毁寄宿控件。|
|[COleControlSite::DoVerb](#doverb)|执行寄宿控件的特定谓词。|
|[COleControlSite::EnableDSC](#enabledsc)|启用控件站点的数据源。|
|[COleControlSite::EnableWindow](#enablewindow)|启用控件站点。|
|[COleControlSite::FreezeEvents](#freezeevents)|指定控件站点是否接受事件。|
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|检索寄宿控件的默认按钮代码。|
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|检索控件的标识符。|
|[COleControlSite::GetEventIID](#geteventiid)|检索承载的控件的事件接口的 ID。|
|[COleControlSite::GetExStyle](#getexstyle)|检索控件网站的扩展样式。|
|[COleControlSite::GetProperty](#getproperty)|检索寄宿控件的特定属性。|
|[COleControlSite::GetStyle](#getstyle)|检索控件网站的样式。|
|[COleControlSite::GetWindowText](#getwindowtext)|检索所承载控件的文本。|
|[COleControlSite::InvokeHelper](#invokehelper)|调用寄宿控件的特定方法。|
|[COleControlSite::InvokeHelperV](#invokehelperv)|使用参数的变量列表调用寄宿控件的特定方法。|
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|确定控件是否为窗口中的默认按钮。|
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|检查控件站点的可见状态。|
|[COleControlSite::ModifyStyle](#modifystyle)|修改控件网站的当前扩展样式。|
|[COleControlSite::ModifyStyleEx](#modifystyleex)|修改控件网站的当前样式。|
|[COleControlSite::MoveWindow](#movewindow)|更改控件站点的位置。|
|[COleControlSite::QuickActivate](#quickactivate)|快速激活承载的控件。|
|[COleControlSite::SafeSetProperty](#safesetproperty)|设置控件的属性或方法, 而不会引发异常。|
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|设置窗口中的默认按钮。|
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|检索控件的标识符。|
|[COleControlSite::SetFocus](#setfocus)|将焦点设置到控件站点。|
|[COleControlSite::SetProperty](#setproperty)|设置寄宿的控件的特定属性。|
|[COleControlSite::SetPropertyV](#setpropertyv)|使用参数的变量列表设置承载控件的特定属性。|
|[COleControlSite::SetWindowPos](#setwindowpos)|设置控件站点的位置。|
|[COleControlSite::SetWindowText](#setwindowtext)|设置寄宿的控件的文本。|
|[COleControlSite::ShowWindow](#showwindow)|显示或隐藏控制站点。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[COleControlSite::GetControlInfo](#getcontrolinfo)|检索承载的控件的键盘信息和助记键。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|确定承载的控件是否为无窗口控件。|
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|包含控件的键盘处理信息。|
|[COleControlSite::m_dwEventSink](#m_dweventsink)|控件的连接点的 cookie。|
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|承载的控件的其他状态。|
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|控件`IPropertyNotifySink`的 cookie。|
|[COleControlSite::m_dwStyle](#m_dwstyle)|承载的控件的样式。|
|[COleControlSite::m_hWnd](#m_hwnd)|控制站点的句柄。|
|[COleControlSite::m_iidEvents](#m_iidevents)|承载的控件的事件接口的 ID。|
|[COleControlSite::m_nID](#m_nid)|承载的控件的 ID。|
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|指向所承载控件`IOleInPlaceActiveObject`的对象的指针。|
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|承载的控件的容器。|
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|指向所承载控件`IOleInPlaceObject`的对象的指针。|
|[COleControlSite::m_pObject](#m_pobject)|指向控件的`IOleObjectInterface`接口的指针。|
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|指向控件的`IOleInPlaceObjectWindowless`接口的指针。|
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|指向所承载控件的窗口对象的指针。|
|[COleControlSite::m_rect](#m_rect)|控制站点的尺寸。|

## <a name="remarks"></a>备注

这种支持是嵌入的 ActiveX 控件获取有关其显示站点的位置和范围、其名字对象、其用户界面、环境属性以及其容器提供的其他资源的信息的主要方式。 `COleControlSite`完全实现[IOleControlSite](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite)、 [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite)、 [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) `IBoundObjectSite`、、 `INotifyDBEvents`、 [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md)接口。 此外, 还实现了 IDispatch 接口 (提供对环境属性和事件接收器的支持)。

若要使用`COleControlSite`创建 ActiveX 控件站点, 请从`COleControlSite`派生一个类。 在用于容器的派生类 (例如, 对话框) 中, `CWnd::CreateControlSite`重写函数。 `CWnd`

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>要求

**标头:** afxocc

##  <a name="binddefaultproperty"></a>  COleControlSite::BindDefaultProperty

将调用对象的默认简单绑定属性 (如类型库中的标记) 绑定到数据源控件的数据源、用户名、密码和 SQL 属性所定义的基础游标。

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
指定要绑定到数据源控件的数据绑定控件上的属性的 DISPID。

*vtProp*<br/>
指定要绑定的属性的类型, 例如 VT_BSTR、VT_VARIANT 等。

*szFieldName*<br/>
指定数据源控件所提供的、要将属性绑定到的列的名称。

*pDSCWnd*<br/>
指向`CWnd`派生对象的指针, 该对象承载属性将绑定到的数据源控件。

### <a name="remarks"></a>备注

调用此函数的对象必须是数据绑定控件。`CWnd`

##  <a name="bindproperty"></a>  COleControlSite::BindProperty

将调用对象的简单绑定属性 (在类型库中标记) 绑定到数据源控件的数据源、用户名、密码和 SQL 属性所定义的基础游标。

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>参数

*dwDispId*<br/>
指定要绑定到数据源控件的数据绑定控件上的属性的 DISPID。

*pWndDSC*<br/>
指向`CWnd`派生对象的指针, 该对象承载属性将绑定到的数据源控件。

### <a name="remarks"></a>备注

调用此函数的对象必须是数据绑定控件。`CWnd`

##  <a name="colecontrolsite"></a>  COleControlSite::COleControlSite

构造一个新`COleControlSite`的对象。

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>参数

*pCtrlCont*<br/>
指向控件的容器 (表示承载 AtiveX 控件的窗口) 的指针。

### <a name="remarks"></a>备注

此函数由[COccManager:: CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer)函数调用。 有关自定义容器创建的详细信息, 请参阅[COccManager:: 网站](../../mfc/reference/coccmanager-class.md#createsite)。

##  <a name="createcontrol"></a>COleControlSite:: CreateControl

创建由`COleControlSite`对象承载的 ActiveX 控件。

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
指向要在控件中显示的文本的指针。 设置 winodw 的标题或文本属性的值 (如果有)。

*dwStyle*<br/>
窗口样式。 可用样式在 "**备注**" 部分下列出。

*rect*<br/>
指定控件的大小和位置。 它可以`CRect`是对象`RECT`或结构。

*nID*<br/>
指定控件的子窗口 ID。

*pPersist*<br/>
指向的`CFile`指针, 该指针包含控件的持久状态。 默认值为 NULL, 指示控件将初始化自身, 而不从任何持久性存储还原其状态。 如果不为 NULL, 则它应为指向`CFile`派生对象的指针, 该对象包含控件的持久性数据 (以流或存储的形式)。 此数据可能已在以前的客户端激活中保存。 可以包含其他数据, 但必须在`CreateControl`调用时将其读写指针设置为持久性数据的第一个字节。 `CFile`

*bStorage*<br/>
指示*pPersist*中的数据是否应解释为`IStorage`或`IStream`数据。 如果*pPersist*中的数据是存储, 则*bStorage*应为 TRUE。 如果*pPersist*中的数据是流, 则*BSTORAGE*应为 FALSE。 默认值是 FALSE。

*bstrLicKey*<br/>
可选许可证密钥数据。 此数据仅用于创建需要运行时许可证密钥的控件。 如果控件支持授权, 则必须提供许可证密钥才能成功创建控件。 默认值为 NULL。

*ppt*<br/>
指向`POINT`结构的指针, 该结构包含控件的左上角。 控件的大小由*psize*的值确定。 *Ppt*和*psize*值是指定控件处于其中大小和位置的可选方法。

*psize*<br/>
指向`SIZE`结构的指针, 该结构包含控件的大小。 左上角由*ppt*的值确定。 *Ppt*和*psize*值是指定控件处于其中大小和位置的可选方法。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

仅支持`CreateControl`部分 Windows *dwStyle*标志:

- WS_VISIBLE 创建一个最初可见的窗口。 如果希望立即显示控件 (如普通窗口), 则为必需。

- WS_DISABLED 创建一个最初处于禁用状态的窗口。 禁用的窗口无法接收来自用户的输入。 如果控件具有 Enabled 属性, 则可以设置。

- WS_BORDER 创建一个具有细线边框的窗口。 如果控件具有 BorderStyle 属性, 则可以设置。

- WS_GROUP 指定一组控件的第一个控件。 用户可以使用方向键将键盘焦点从组中的一个控件更改为下一个控件。 在第一个控件属于同一组后, 所有用 WS_GROUP 样式定义的控件。 具有 WS_GROUP 样式的下一个控件将结束组并启动下一组。

- WS_TABSTOP 指定当用户按 TAB 键时可接收键盘焦点的控件。 按 TAB 键会将键盘焦点更改为 WS_TABSTOP 样式的下一个控件。

使用第二个重载创建默认大小的控件。

##  <a name="destroycontrol"></a>  COleControlSite::DestroyControl

`COleControlSite`销毁对象。

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>返回值

如果成功, 则为非零; 否则为0。

### <a name="remarks"></a>备注

完成后, 将从内存中释放对象, 并使任何指向该对象的指针不再有效。

##  <a name="doverb"></a>  COleControlSite::DoVerb

执行指定的谓词。

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>参数

*nVerb*<br/>
指定要执行的谓词。 它可以包括以下内容之一:

|值|含义|符号|
|-----------|-------------|------------|
|0|主谓词|OLEIVERB_PRIMARY|
|-1|辅助谓词|（无）|
|1|显示要编辑的对象。|OLEIVERB_SHOW|
|-2|在单独的窗口中编辑项。|OLEIVERB_OPEN|
|-3|隐藏对象。|OLEIVERB_HIDE|
|-4|就地激活控件。|OLEIVERB_UIACTIVATE|
|-5|就地激活控件, 无需其他用户界面元素。|OLEIVERB_INPLACEACTIVATE|
|-7|显示控件的属性。|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
指向导致激活项的消息的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

此函数直接调用控件的`IOleObject`接口以执行指定的谓词。 如果通过此函数调用引发了异常, 则返回 HRESULT 错误代码。

有关详细信息, 请参阅 IOleObject: Windows SDK 中的[::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 。

##  <a name="enabledsc"></a>  COleControlSite::EnableDSC

启用控件站点的数据源。

```
virtual void EnableDSC();
```

### <a name="remarks"></a>备注

由框架调用, 用于启用和初始化控件网站的数据源。 重写此函数以提供自定义的行为。

##  <a name="enablewindow"></a>  COleControlSite::EnableWindow

启用或禁用控制站点的鼠标和键盘输入。

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
指定是启用还是禁用窗口:如果要启用窗口输入, 则为 TRUE; 否则为 FALSE。

### <a name="return-value"></a>返回值

如果先前禁用了窗口, 则为非零; 否则为0。

##  <a name="freezeevents"></a>COleControlSite:: Freezeevents 时调用

指定控件站点是否将处理或忽略从控件激发的事件。

```
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>参数

*bFreeze*<br/>
指定控件所在位置是否希望停止接受事件。 如果控件不接受事件, 则为非零值;否则为零。

### <a name="remarks"></a>备注

如果*bFreeze*为 TRUE, 则控制站点请求控件停止 fring 事件。 如果*bFreeze*为 FALSE, 则控制站点请求控件继续激发事件。

> [!NOTE]
>  如果控制站点请求, 则不需要控件来停止激发事件。 它可以继续触发, 但所有后续事件都将被控制站点忽略。

##  <a name="getcontrolinfo"></a>  COleControlSite::GetControlInfo

检索有关控件的键盘助记键和键盘行为的信息。

```
void GetControlInfo();
```

### <a name="remarks"></a>备注

此信息存储在[COleControlSite:: m_ctlInfo](#m_ctlinfo)中。

##  <a name="getdefbtncode"></a>  COleControlSite::GetDefBtnCode

确定控件是否为默认按钮。

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>返回值

可以是以下值之一：

- DLGC_DEFPUSHBUTTON 控件是对话框中的默认按钮。

- DLGC_UNDEFPUSHBUTTON 控件不是对话框中的默认按钮。

- **0**控件不是按钮。

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
指向接口 ID 的指针。

### <a name="return-value"></a>返回值

如果成功, 则为非零; 否则为0。 如果成功, *piid*将包含控件默认事件接口的接口 ID。

##  <a name="getexstyle"></a>  COleControlSite::GetExStyle

检索窗口的扩展样式。

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>返回值

控件窗口的扩展样式。

### <a name="remarks"></a>备注

若要检索常规样式, 请调用[COleControlSite:: GetStyle](#getstyle)。

##  <a name="getproperty"></a>  COleControlSite::GetProperty

获取*dwDispID*指定的控件属性。

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识要检索的控件的默认`IDispatch`接口上的属性的调度 ID。

*vtProp*<br/>
指定要检索的属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*pvProp*<br/>
将接收属性值的变量的地址。 它必须与*vtProp*指定的类型匹配。

### <a name="remarks"></a>备注

该值通过*pvProp*返回。

##  <a name="getstyle"></a>  COleControlSite::GetStyle

检索控件网站的样式。

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>返回值

窗口的样式。

### <a name="remarks"></a>备注

有关可能值的列表, 请参阅[Windows 样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 若要检索控件网站的扩展样式, 请调用[COleControlSite:: GetExStyle](#getexstyle)。

##  <a name="getwindowtext"></a>  COleControlSite::GetWindowText

检索控件的当前文本。

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>参数

*str*<br/>
对`CString`对象的引用, 该对象包含控件的当前文本。

### <a name="remarks"></a>备注

如果控件支持标题常用属性, 则返回此值。 如果不支持标题常用属性, 则返回 Text 属性的值。

##  <a name="invokehelper"></a>COleControlSite:: InvokeHelper

在*wFlags*指定的上下文中调用*dwDispID*指定的方法或属性。

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
标识要调用的控件`IDispatch`接口上的属性或方法的调度 ID。

*wFlags*<br/>
描述对 IDispatch:: Invoke 调用的上下文的标志。 有关可能的*wFlags*值, `IDispatch::Invoke`请参阅 Windows SDK 中的。

*vtRet*<br/>
指定返回值的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*pvRet*<br/>
将接收属性值或返回值的变量的地址。 它必须与*vtRet*指定的类型匹配。

*pbParamInfo*<br/>
指向以 null 结尾的字节字符串的指针, 该字符串指定*pbParamInfo*后面的参数类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*...*<br/>
在*pbParamInfo*中指定的类型的参数的变量列表。

### <a name="remarks"></a>备注

*PbParamInfo*参数指定传递到方法或属性的参数的类型。 参数的变量列表用 .。。语法声明中的。

此函数将参数转换为 VARIANTARG 值, 然后调用该`IDispatch::Invoke`控件上的方法。 如果 `IDispatch::Invoke` 调用失败，则此函数会引发异常。 如果返回`IDispatch::Invoke`的状态代码为`COleDispatchException` , `DISP_E_EXCEPTION`则此函数将引发对象, 否则将引发`COleException`。

##  <a name="invokehelperv"></a>COleControlSite::InvokeHelperV

在*wFlags*指定的上下文中调用*dwDispID*指定的方法或属性。

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
标识要调用的控件`IDispatch`接口上的属性或方法的调度 ID。

*wFlags*<br/>
描述对 IDispatch:: Invoke 调用的上下文的标志。

*vtRet*<br/>
指定返回值的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*pvRet*<br/>
将接收属性值或返回值的变量的地址。 它必须与*vtRet*指定的类型匹配。

*pbParamInfo*<br/>
指向以 null 结尾的字节字符串的指针, 该字符串指定*pbParamInfo*后面的参数类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*argList*<br/>
指向变量参数列表的指针。

### <a name="remarks"></a>备注

*PbParamInfo*参数指定传递到方法或属性的参数的类型。 使用*va_list*参数可以传递要调用的方法或属性的额外参数。

通常, 此函数由`COleControlSite::InvokeHelper`调用。

##  <a name="isdefaultbutton"></a>  COleControlSite::IsDefaultButton

确定控件是否为默认按钮。

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>返回值

如果控件为窗口上的默认按钮, 则为非零值; 否则为零。

##  <a name="iswindowenabled"></a>  COleControlSite::IsWindowEnabled

确定是否启用了控制站点。

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>返回值

如果启用控件, 则为非零; 否则为零。

### <a name="remarks"></a>备注

该值是从启用控件的常用属性中检索的。

##  <a name="m_biswindowless"></a>  COleControlSite::m_bIsWindowless

确定对象是否为无窗口控件。

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>备注

如果控件没有窗口, 则为非零; 否则为零。

##  <a name="m_ctlinfo"></a>  COleControlSite::m_ctlInfo

有关控件如何处理键盘输入的信息。

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>备注

此信息存储在[CONTROLINFO](/windows/win32/api/ocidl/ns-ocidl-controlinfo)结构中。

##  <a name="m_dweventsink"></a>  COleControlSite::m_dwEventSink

包含来自控件的事件接收器的连接点的 cookie。

```
DWORD m_dwEventSink;
```

##  <a name="m_dwmiscstatus"></a>  COleControlSite::m_dwMiscStatus

包含有关控件的杂项信息。

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅 Windows SDK 中的[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)。

##  <a name="m_dwpropnotifysink"></a>  COleControlSite::m_dwPropNotifySink

包含[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) cookie。

```
DWORD m_dwPropNotifySink;
```

##  <a name="m_dwstyle"></a>  COleControlSite::m_dwStyle

包含控件的窗口样式。

```
DWORD m_dwStyle;
```

##  <a name="m_hwnd"></a>  COleControlSite::m_hWnd

包含控件的 HWND, 如果控件无窗口, 则为 NULL。

```
HWND m_hWnd;
```

##  <a name="m_iidevents"></a>  COleControlSite::m_iidEvents

包含控件的默认事件接收器接口的接口 ID。

```
IID m_iidEvents;
```

##  <a name="m_nid"></a>  COleControlSite::m_nID

包含控件的对话框项 ID。

```
UINT m_nID;
```

##  <a name="m_pactiveobject"></a>  COleControlSite::m_pActiveObject

包含控件的[IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject)接口。

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

##  <a name="m_pctrlcont"></a>  COleControlSite::m_pCtrlCont

包含控件的容器 (表示窗体)。

```
COleControlContainer* m_pCtrlCont;
```

##  <a name="m_pinplaceobject"></a>  COleControlSite::m_pInPlaceObject

包含控件`IOleInPlaceObject`的[IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject)接口。

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

##  <a name="m_pobject"></a>  COleControlSite::m_pObject

包含控件的接口。 `IOleObjectInterface`

```
LPOLEOBJECT m_pObject;
```

##  <a name="m_pwindowlessobject"></a>  COleControlSite::m_pWindowlessObject

包含控件`IOleInPlaceObjectWindowless`的[IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)接口。

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

##  <a name="m_pwndctrl"></a>  COleControlSite::m_pWndCtrl

包含一个指向`CWnd`对象的指针, 该对象表示控件本身。

```
CWnd* m_pWndCtrl;
```

##  <a name="m_rect"></a>  COleControlSite::m_rect

包含控件的边界, 相对于容器的窗口。

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
要从当前窗口样式中删除的样式。

*dwAdd*<br/>
要从当前窗口样式添加的样式。

*nFlags*<br/>
窗口定位标志。 有关可能值的列表, 请参阅 Windows SDK 中的[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)函数。

### <a name="return-value"></a>返回值

如果更改了样式, 则为非零; 否则为零。

### <a name="remarks"></a>备注

将修改控件的 "启用的库存" 属性, 使其与 WS_DISABLED 的设置相匹配。 将修改控件的 "股票边框样式" 属性, 使其与 WS_BORDER 的请求的设置相匹配。 所有其他样式将直接应用于控件的窗口句柄 (如果存在)。

修改控件的窗口样式。 要添加或删除的样式可以使用按位 OR ( &#124; ) 运算符组合在一起。 有关可用的窗口样式的信息, 请参阅 Windows SDK 中的[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww)函数。

如果*nFlags*为非零`ModifyStyle` , 则调用 Win32 `SetWindowPos`函数, 并通过将*nFlags*与以下四个标志组合来重绘窗口:

- SWP_NOSIZE 保留当前的大小。

- SWP_NOMOVE 保留当前位置。

- SWP_NOZORDER 保留当前的 Z 顺序。

- SWP_NOACTIVATE 不会激活窗口。

若要修改窗口的扩展样式, 请调用[ModifyStyleEx](#modifystyleex)。

##  <a name="modifystyleex"></a>  COleControlSite::ModifyStyleEx

修改控件的扩展样式。

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>参数

*dwRemove*<br/>
要从当前窗口样式中删除的扩展样式。

*dwAdd*<br/>
要从当前窗口样式添加的扩展样式。

*nFlags*<br/>
窗口定位标志。 有关可能值的列表, 请参阅 Windows SDK 中的[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)函数。

### <a name="return-value"></a>返回值

如果更改了样式, 则为非零; 否则为零。

### <a name="remarks"></a>备注

将修改控件的 stock 外观属性, 使其与 WS_EX_CLIENTEDGE 的设置相匹配。 所有其他扩展窗口样式将直接应用于控件的窗口句柄 (如果存在)。

修改控件网站对象的窗口扩展样式。 要添加或删除的样式可以使用按位 OR ( &#124; ) 运算符组合在一起。 有关可用的窗口样式的信息, 请参阅 Windows SDK 中的[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)函数。

如果*nFlags*为非零`ModifyStyleEx` , 则调用 Win32 `SetWindowPos`函数, 并通过将*nFlags*与以下四个标志组合来重绘窗口:

- SWP_NOSIZE 保留当前的大小。

- SWP_NOMOVE 保留当前位置。

- SWP_NOZORDER 保留当前的 Z 顺序。

- SWP_NOACTIVATE 不会激活窗口。

若要修改窗口的扩展样式, 请调用[ModifyStyle](#modifystyle)。

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
窗口左侧的新位置。

*y*<br/>
窗口顶部的新位置。

*nWidth*<br/>
窗口的新宽度

*nHeight*<br/>
窗口的新高度。

##  <a name="quickactivate"></a>  COleControlSite::QuickActivate

快速激活包含的控件。

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>返回值

如果控件站点已激活, 则为非零; 否则为零。

### <a name="remarks"></a>备注

仅当用户正在重写控件的创建进程时, 才应调用此函数。

在快速`IPersist*::InitNew`激活发生之后,应调用和方法。`IPersist*::Load` 在快速激活期间, 控件应建立与容器接收器的连接。 但是, 在调用或`IPersist*::Load` `IPersist*::InitNew`之前, 这些连接不会处于活动状态。

##  <a name="safesetproperty"></a>  COleControlSite::SafeSetProperty

设置由*dwDispID*指定的控件属性。

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识要设置的控件`IDispatch`接口上的属性或方法的调度 ID。

*vtProp*<br/>
指定要设置的属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*...*<br/>
由*vtProp*指定的类型的单个参数。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

> [!NOTE]
>  与`SetProperty` 和`SetPropertyV`不同, 如果遇到错误 (例如, 尝试设置不存在的属性), 则不会引发异常。

##  <a name="setdefaultbutton"></a>  COleControlSite::SetDefaultButton

将控件设置为默认按钮。

```
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>参数

*bDefault*<br/>
如果控件应成为默认按钮, 则为非零值;否则为零。

### <a name="remarks"></a>备注

> [!NOTE]
>  控件必须设置 OLEMISC_ACTSLIKEBUTTON 状态位。

##  <a name="setdlgctrlid"></a>  COleControlSite::SetDlgCtrlID

更改控件的对话框项标识符的值。

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
新的标识符值。

### <a name="return-value"></a>返回值

如果成功, 则为窗口的上一个对话框项标识符;否则为0。

### <a name="remarks"></a>备注

##  <a name="setfocus"></a>  COleControlSite::SetFocus

将焦点设置到控件上。

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>参数

*lpmsg*<br/>
指向[MSG 结构](/windows/win32/api/winuser/ns-winuser-msg)的指针。 此结构包含对当前控制站点中`SetFocus`包含的控件发出请求的 Windows 消息。

### <a name="return-value"></a>返回值

指向以前具有焦点的窗口的指针。

##  <a name="setproperty"></a>  COleControlSite::SetProperty

设置由*dwDispID*指定的控件属性。

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识要设置的控件`IDispatch`接口上的属性或方法的调度 ID。

*vtProp*<br/>
指定要设置的属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*...*<br/>
由*vtProp*指定的类型的单个参数。

### <a name="remarks"></a>备注

如果`SetProperty`遇到错误, 则会引发异常。

异常的类型由尝试设置该属性或方法的返回值决定。 如果返回值为`DISP_E_EXCEPTION` `COleDispatchExcpetion` , 则引发, 否则`COleException`为。

##  <a name="setpropertyv"></a>  COleControlSite::SetPropertyV

设置由*dwDispID*指定的控件属性。

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识要设置的控件`IDispatch`接口上的属性或方法的调度 ID。

*vtProp*<br/>
指定要设置的属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*argList*<br/>
指向参数列表的指针。

### <a name="remarks"></a>备注

使用*arg_list*参数可以 passeed 调用的方法或属性的额外参数。 如果`SetProperty`遇到错误, 则会引发异常。

异常的类型由尝试设置该属性或方法的返回值决定。 如果返回值为`DISP_E_EXCEPTION` `COleDispatchExcpetion` , 则引发, 否则`COleException`为。

##  <a name="setwindowpos"></a>  COleControlSite::SetWindowPos

设置控件站点的大小、位置和 Z 顺序。

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
窗口左侧的新位置。

*y*<br/>
窗口顶部的新位置。

*cx*<br/>
窗口的新宽度

*cy*<br/>
窗口的新高度。

*nFlags*<br/>
指定窗口大小调整和定位标志。 有关可能的值, 请参阅 Windows SDK 中[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)的 "备注" 部分。

### <a name="return-value"></a>返回值

如果成功, 则为非零; 否则为零。

##  <a name="setwindowtext"></a>  COleControlSite::SetWindowText

设置控件站点的文本。

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*lpszString*<br/>
指向以 null 结尾的字符串的指针, 该字符串用作新的标题或控件文本。

### <a name="remarks"></a>备注

此函数首先尝试设置标题常用属性。 如果不支持 "字幕" 常用属性, 则改为设置 "文本" 属性。

##  <a name="showwindow"></a>COleControlSite:: ShowWindow

设置窗口的显示状态。

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>参数

*nCmdShow*<br/>
指定如何显示控件站点。 它必须是下列值之一:

- SW_HIDE 隐藏此窗口, 并将激活传递到另一个窗口。

- SW_MINIMIZE 将窗口最小化, 并激活系统列表中的顶级窗口。

- SW_RESTORE 激活并显示窗口。 如果窗口已最小化或最大化, Windows 会将其还原为原始大小和位置。

- SW_SHOW 激活窗口, 并以其当前大小和位置显示它。

- SW_SHOWMAXIMIZED 激活窗口并将其显示为最大化窗口。

- SW_SHOWMINIMIZED 激活窗口并将其显示为图标。

- SW_SHOWMINNOACTIVE 将窗口显示为图标。 当前处于活动状态的窗口仍处于活动状态。

- SW_SHOWNA 将窗口显示为其当前状态。 当前处于活动状态的窗口仍处于活动状态。

- SW_SHOWNOACTIVATE 按最新的大小和位置显示窗口。 当前处于活动状态的窗口仍处于活动状态。

- SW_SHOWNORMAL 激活并显示窗口。 如果窗口已最小化或最大化, Windows 会将其还原为原始大小和位置。

### <a name="return-value"></a>返回值

如果窗口之前可见, 则为非零值;如果以前隐藏窗口, 则为0。

## <a name="see-also"></a>请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleControlContainer 类](../../mfc/reference/colecontrolcontainer-class.md)
