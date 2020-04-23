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
ms.openlocfilehash: 90c41a1be1a66cdceebb3f045a98167e56b7cf4c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753954"
---
# <a name="colecontrolsite-class"></a>COleControlSite 类

提供自定义客户端控件接口支持。

## <a name="syntax"></a>语法

```
class COleControlSite : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle 控制网站：COle 控制网站](#colecontrolsite)|构造 `COleControlSite` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COle 控制网站：：绑定默认属性](#binddefaultproperty)|将托管控件的默认属性绑定到数据源。|
|[COle 控制网站：绑定属性](#bindproperty)|将托管控件的属性绑定到数据源。|
|[COle 控制网站：创建控制](#createcontrol)|创建托管的 ActiveX 控件。|
|[COleControlSite：:D控制](#destroycontrol)|销毁托管控件。|
|[COleControlSite：:DoVerb](#doverb)|执行托管控件的特定谓词。|
|[COle 控制网站：启用DSC](#enabledsc)|支持控制站点的数据源。|
|[COle 控制网站：启用窗口](#enablewindow)|启用控制站点。|
|[COle 控制网站：冻结事件](#freezeevents)|指定控件站点是否接受事件。|
|[COle 控制网站：获取DefBtn代码](#getdefbtncode)|检索托管控件的默认按钮代码。|
|[COle 控制网站：获取DlgCtrlID](#getdlgctrlid)|检索控件的标识符。|
|[COle 控制网站：获取事件Id](#geteventiid)|检索托管控件的事件接口的 ID。|
|[COle 控制网站：获取样式](#getexstyle)|检索控件站点的扩展样式。|
|[COle 控制网站：获取财产](#getproperty)|检索托管控件的特定属性。|
|[COle 控制网站：获取样式](#getstyle)|检索控件站点的样式。|
|[COle 控制网站：获取窗口文本](#getwindowtext)|检索托管控件的文本。|
|[COle 控制网站：：调用帮助者](#invokehelper)|调用托管控件的特定方法。|
|[COle 控制网站：：调用帮助者V](#invokehelperv)|使用参数的变量列表调用托管控件的特定方法。|
|[COle 控制网站：默认按钮](#isdefaultbutton)|确定控件是否为窗口中的默认按钮。|
|[COle 控制网站：启用窗口](#iswindowenabled)|检查控制站点的可见状态。|
|[COle 控制网站：修改样式](#modifystyle)|修改控件站点的当前扩展样式。|
|[COle 控制网站：修改样式](#modifystyleex)|修改控件站点的当前样式。|
|[COle 控制网站：移动窗口](#movewindow)|更改控制站点的位置。|
|[COle 控制网站：快速激活](#quickactivate)|快速激活托管控件。|
|[COle 控制网站：安全设置属性](#safesetproperty)|设置控件的属性或方法，而不会引发异常。|
|[COle 控制网站：设置默认按钮](#setdefaultbutton)|设置窗口中的默认按钮。|
|[COle 控制网站：SetDlgCtrlID](#setdlgctrlid)|检索控件的标识符。|
|[COle 控制网站：设置焦点](#setfocus)|将焦点设置到控制站点。|
|[COle 控制网站：设置属性](#setproperty)|设置托管控件的特定属性。|
|[COle 控制网站：SetPropertyV](#setpropertyv)|使用参数的可变列表设置托管控件的特定属性。|
|[COle 控制网站：设置窗口位置](#setwindowpos)|设置控制站点的位置。|
|[COle 控制网站：设置窗口文本](#setwindowtext)|设置托管控件的文本。|
|[COle 控制网站：显示窗口](#showwindow)|显示或隐藏控制站点。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[COle 控制网站：获取控制信息](#getcontrolinfo)|检索托管控件的键盘信息和助记符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COle 控制网站：m_bIsWindowless](#m_biswindowless)|确定托管控件是否为无窗口控件。|
|[COle 控制网站：m_ctlInfo](#m_ctlinfo)|包含有关控件的键盘处理的信息。|
|[COle 控制网站：m_dwEventSink](#m_dweventsink)|控件连接点的 Cookie。|
|[COle 控制网站：m_dwMiscStatus](#m_dwmiscstatus)|托管控件的杂项状态。|
|[COle 控制网站：m_dwPropNotifySink](#m_dwpropnotifysink)|控件`IPropertyNotifySink`的 Cookie。|
|[COle 控制网站：m_dwStyle](#m_dwstyle)|托管控件的样式。|
|[COle 控制网站：m_hWnd](#m_hwnd)|控制站点的句柄。|
|[COle 控制网站：m_iidEvents](#m_iidevents)|托管控件的事件接口的 ID。|
|[COle 控制网站：m_nID](#m_nid)|托管控件的 ID。|
|[COle 控制网站：m_pActiveObject](#m_pactiveobject)|指向托管控件`IOleInPlaceActiveObject`对象的指针。|
|[COle 控制网站：m_pCtrlCont](#m_pctrlcont)|托管控件的容器。|
|[COle 控制网站：m_pInPlaceObject](#m_pinplaceobject)|指向托管控件`IOleInPlaceObject`对象的指针。|
|[COle 控制网站：m_pObject](#m_pobject)|指向控件`IOleObjectInterface`接口的指针。|
|[COle 控制网站：m_pWindowlessObject](#m_pwindowlessobject)|指向控件`IOleInPlaceObjectWindowless`接口的指针。|
|[COle 控制网站：m_pWndCtrl](#m_pwndctrl)|指向托管控件的窗口对象的指针。|
|[COle控制网站：：m_rect](#m_rect)|控制站点的尺寸。|

## <a name="remarks"></a>备注

此支持是嵌入式 ActiveX 控件获取有关其显示站点的位置和范围、其名字对象、用户界面、其环境属性及其容器提供的其他资源的主要方法。 `COleControlSite`全面实施[IOleControlSite，IOleInPlaceSite，IOleClientSite，IpropertynotifySink，、、IrowSetnotify](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite)[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)`IBoundObjectSite``INotifyDBEvents`[接口](../../data/oledb/irowsetnotifyimpl-class.md)。 [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite) [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite) 此外，还实现了 IDispatch 接口（支持环境属性和事件接收器）。

要使用`COleControlSite`创建 ActiveX 控件网站，请派生`COleControlSite`类。 在容器`CWnd`的派生类中（例如，对话框）将覆盖该`CWnd::CreateControlSite`函数。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>要求

**标题：** afxocc.h

## <a name="colecontrolsitebinddefaultproperty"></a><a name="binddefaultproperty"></a>COle 控制网站：：绑定默认属性

将调用对象的默认简单绑定属性（如类型库中标记）绑定到数据源控件的 DataSource、用户名、密码和 SQL 属性定义的基础游标。

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
指定要绑定到数据源控件的数据绑定控件上属性的 DISPID。

*vtProp*<br/>
指定要绑定的属性的类型，例如，VT_BSTR、VT_VARIANT 等。

*szfield名称*<br/>
指定列的名称，在数据源控件提供的游标中，该属性将绑定到该列。

*pDSCWnd*<br/>
指向`CWnd`承载将属性绑定到的数据源控件的派生对象的指针。

### <a name="remarks"></a>备注

调用`CWnd`此函数的对象必须是数据绑定控件。

## <a name="colecontrolsitebindproperty"></a><a name="bindproperty"></a>COle 控制网站：绑定属性

将调用对象的简单绑定属性（如类型库中标记）绑定到数据源控件的 DataSource、用户名、密码和 SQL 属性定义的基础游标。

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>参数

*dwDispId*<br/>
指定要绑定到数据源控件的数据绑定控件上属性的 DISPID。

*pWndDSC*<br/>
指向`CWnd`承载将属性绑定到的数据源控件的派生对象的指针。

### <a name="remarks"></a>备注

调用`CWnd`此函数的对象必须是数据绑定控件。

## <a name="colecontrolsitecolecontrolsite"></a><a name="colecontrolsite"></a>COle 控制网站：COle 控制网站

构造新的 `COleControlSite` 对象。

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>参数

*pCtrlCont*<br/>
指向控件容器的指针（表示承载 AtiveX 控件的窗口）。

### <a name="remarks"></a>备注

此函数由[COccManager：创建容器](../../mfc/reference/coccmanager-class.md#createcontainer)函数调用。 有关自定义容器创建的详细信息，请参阅[COccManager：：：createSite](../../mfc/reference/coccmanager-class.md#createsite)。

## <a name="colecontrolsitecreatecontrol"></a><a name="createcontrol"></a>COle 控制网站：创建控制

创建由对象托管的`COleControlSite`ActiveX 控件。

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

*Clsid*<br/>
控件的唯一类 ID。

*lpsz窗口名称*<br/>
指向要在控件中显示的文本的指针。 设置 winodw 的标题或文本属性（如果有）的值。

*dwStyle*<br/>
窗口样式。 可用样式列在 **"备注"** 部分下。

*矩形*<br/>
指定控件的大小和位置。 它可以是`CRect`对象或`RECT`结构。

*nID*<br/>
指定控件的子窗口 ID。

*p 坚持*<br/>
指向`CFile`包含控件的持久状态的 指针。 默认值为 NULL，指示控件在不从任何持久存储还原其状态的情况下初始化自身。 如果不是 NULL，它应该是指向包含控件持久数据的`CFile`派生对象的指针，其形式是流或存储。 此数据可能已保存在客户端的上次激活中。 `CFile`可以包含其他数据，但必须将其读写指针设置为调用`CreateControl`时持久性数据的第一个字节。

*b 存储*<br/>
指示是否应将*pPersist*中的数据解释为`IStorage`或`IStream`数据。 如果*pPersist*中的数据是存储，*则 b 存储*应为 TRUE。 如果*pPersist*中的数据是流，*则 b 存储*应为 FALSE。 默认值是 FALSE。

*bstrLicKey*<br/>
可选的许可证密钥数据。 仅创建需要运行时许可证密钥的控件才需要此数据。 如果控件支持许可，则必须提供许可证密钥才能成功创建控件。 默认值为 NULL。

*Ppt*<br/>
指向包含控件左`POINT`上角的结构的指针。 控件的大小由*size*的值决定。 *ppt*和*size 值*是指定控件的大小和位置的可选方法。

*psize*<br/>
指向包含控件大小的`SIZE`结构的指针。 左上角由*ppt*的值决定。 *ppt*和*size 值*是指定控件的大小和位置的可选方法。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

只有 Windows *dwStyle*标志的子集受`CreateControl`支持：

- WS_VISIBLE 创建最初可见的窗口。 如果希望控件立即可见（如普通窗口），则需要。

- WS_DISABLED 创建最初禁用的窗口。 禁用的窗口无法接收用户输入。 如果控件具有"已启用"属性，则可以进行设置。

- WS_BORDER 创建具有细线边框的窗口。 如果控件具有 BorderStyle 属性，则可以进行设置。

- WS_GROUP 指定一组控件的第一个控件。 用户可以使用方向键将键盘焦点从组中的一个控件更改为下一个控件。 在第一个控件之后使用WS_GROUP样式定义的所有控件都属于同一组。 具有WS_GROUP样式的下一个控件将结束组并启动下一个组。

- WS_TABSTOP 指定可在用户按下 TAB 键时接收键盘焦点的控件。 按下 TAB 键会将键盘焦点更改为WS_TABSTOP样式的下一个控件。

使用第二个重载创建默认大小的控件。

## <a name="colecontrolsitedestroycontrol"></a><a name="destroycontrol"></a>COleControlSite：:D控制

销毁`COleControlSite`对象。

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>返回值

如果成功，则非零，否则为 0。

### <a name="remarks"></a>备注

完成后，对象将从内存中释放，并且指向该对象的任何指针都不再有效。

## <a name="colecontrolsitedoverb"></a><a name="doverb"></a>COleControlSite：:DoVerb

执行指定的谓词。

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>参数

*nVerb*<br/>
指定要执行的谓词。 它可以包括以下之一：

|“值”|含义|符号|
|-----------|-------------|------------|
|0|主谓词|OLEIVERB_PRIMARY|
|-1|次要动词|（无）|
|1|显示要编辑的对象。|OLEIVERB_SHOW|
|-2|在单独的窗口中编辑项目。|OLEIVERB_OPEN|
|-3|隐藏对象。|OLEIVERB_HIDE|
|-4|就地激活控件。|OLEIVERB_UIACTIVATE|
|-5|就地激活控件，而无需其他用户界面元素。|OLEIVERB_INPLACEACTIVATE|
|-7|显示控件的属性。|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
指向导致项目被激活的消息的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

此函数直接通过控件的`IOleObject`接口调用以执行指定的谓词。 如果由于此函数调用而引发异常，则返回 HRESULT 错误代码。

有关详细信息，请参阅 Windows SDK 中的[IOleObject：:DoVerb。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)

## <a name="colecontrolsiteenabledsc"></a><a name="enabledsc"></a>COle 控制网站：启用DSC

支持控制站点的数据源。

```
virtual void EnableDSC();
```

### <a name="remarks"></a>备注

由框架调用，以启用和初始化控制站点的数据源。 重写此函数以提供自定义行为。

## <a name="colecontrolsiteenablewindow"></a><a name="enablewindow"></a>COle 控制网站：启用窗口

启用或禁用鼠标和键盘输入到控制站点。

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
指定是启用还是禁用窗口：如果要启用窗口输入，则为 TRUE，否则为 FALSE。

### <a name="return-value"></a>返回值

如果窗口以前已禁用，则非零，否则为 0。

## <a name="colecontrolsitefreezeevents"></a><a name="freezeevents"></a>COle 控制网站：冻结事件

指定控制站点是处理还是忽略从控件触发的事件。

```cpp
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>参数

*bFreeze*<br/>
指定控件所在位置是否希望停止接受事件。 如果控件不接受事件，则非零;否则为零。

### <a name="remarks"></a>备注

如果*bFreeze*为 TRUE，则控制站点请求控件停止 fring 事件。 如果*bFreeze*为 FALSE，则控制站点请求控件继续触发事件。

> [!NOTE]
> 如果控制站点请求，则不需要该控件停止触发事件。 它可以继续触发，但控制站点将忽略所有后续事件。

## <a name="colecontrolsitegetcontrolinfo"></a><a name="getcontrolinfo"></a>COle 控制网站：获取控制信息

检索有关控件的键盘助记符和键盘行为的信息。

```cpp
void GetControlInfo();
```

### <a name="remarks"></a>备注

信息存储在[COleControlSite：：m_ctlInfo](#m_ctlinfo)。

## <a name="colecontrolsitegetdefbtncode"></a><a name="getdefbtncode"></a>COle 控制网站：获取DefBtn代码

确定控件是否为默认按钮。

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>返回值

可以是以下值之一：

- DLGC_DEFPUSHBUTTON控件是对话框中的默认按钮。

- DLGC_UNDEFPUSHBUTTON控件不是对话框中的默认按钮。

- **0**控件不是按钮。

## <a name="colecontrolsitegetdlgctrlid"></a><a name="getdlgctrlid"></a>COle 控制网站：获取DlgCtrlID

检索控件的标识符。

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>返回值

控件的对话框项标识符。

## <a name="colecontrolsitegeteventiid"></a><a name="geteventiid"></a>COle 控制网站：获取事件Id

检索指向控件的默认事件接口的指针。

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>参数

*皮伊德*<br/>
指向接口 ID 的指针。

### <a name="return-value"></a>返回值

如果成功，则非零，否则为 0。 如果成功 *，piid*包含控件的默认事件接口的接口 ID。

## <a name="colecontrolsitegetexstyle"></a><a name="getexstyle"></a>COle 控制网站：获取样式

检索窗口的扩展样式。

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>返回值

控件窗口的扩展样式。

### <a name="remarks"></a>备注

要检索常规样式，请致电[COleControlSite：：getStyle](#getstyle)。

## <a name="colecontrolsitegetproperty"></a><a name="getproperty"></a>COle 控制网站：获取财产

获取*dwDispID*指定的控件属性。

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识要检索的控件默认`IDispatch`接口上找到的属性的调度 ID。

*vtProp*<br/>
指定要检索的属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*pvProp*<br/>
将接收属性值的变量的地址。 它必须匹配*vtProp*指定的类型。

### <a name="remarks"></a>备注

该值通过*pvProp*返回。

## <a name="colecontrolsitegetstyle"></a><a name="getstyle"></a>COle 控制网站：获取样式

检索控件站点的样式。

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>返回值

窗口的样式。

### <a name="remarks"></a>备注

有关可能值的列表，请参阅[Windows 样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 要检索控件站点的扩展样式，请致电[COleControlSite：：GetExStyle](#getexstyle)。

## <a name="colecontrolsitegetwindowtext"></a><a name="getwindowtext"></a>COle 控制网站：获取窗口文本

检索控件的当前文本。

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>参数

*Str*<br/>
对包含控件当前`CString`文本的对象的引用。

### <a name="remarks"></a>备注

如果控件支持标题股票属性，则返回此值。 如果不支持"标题"股票属性，则返回 Text 属性的值。

## <a name="colecontrolsiteinvokehelper"></a><a name="invokehelper"></a>COle 控制网站：：调用帮助者

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
标识要调用的属性或方法的`IDispatch`调度 ID。

*wFlags*<br/>
描述 IDispatch::Invoke 调用的上下文的标志。 有关可能的*wFlags*值`IDispatch::Invoke`，请参阅 Windows SDK。

*弗特雷特*<br/>
指定返回值的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*pvRet*<br/>
将接收属性值或返回值的变量的地址。 它必须与*vtRet*指定的类型匹配。

*pbParamInfo*<br/>
指向 null 端接字节字符串的指针，指定*pbParamInfo*之后的参数类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*...*<br/>
参数的变量列表，在*pbParamInfo*中指定的类型。

### <a name="remarks"></a>备注

*pbParamInfo*参数指定传递给方法或属性的参数的类型。 自变量的变量列表在语法声明中通过 ... 进行表示。

此函数将参数转换为 VARIANTARG 值，然后在控件上调用`IDispatch::Invoke`方法。 如果 `IDispatch::Invoke` 调用失败，则此函数会引发异常。 如果 返回`IDispatch::Invoke`的状态代码 为`DISP_E_EXCEPTION`，则此函数`COleDispatchException`将引发一个对象，`COleException`否则将引发 。

## <a name="colecontrolsiteinvokehelperv"></a><a name="invokehelperv"></a>COle 控制网站：：调用帮助者V

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
标识要调用的属性或方法的`IDispatch`调度 ID。

*wFlags*<br/>
描述 IDispatch::Invoke 调用的上下文的标志。

*弗特雷特*<br/>
指定返回值的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*pvRet*<br/>
将接收属性值或返回值的变量的地址。 它必须与*vtRet*指定的类型匹配。

*pbParamInfo*<br/>
指向 null 端接字节字符串的指针，指定*pbParamInfo*之后的参数类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*阿格列斯*<br/>
指向变量参数列表的指针。

### <a name="remarks"></a>备注

*pbParamInfo*参数指定传递给方法或属性的参数的类型。 可以使用*va_list*参数传递所调用的方法或属性的额外参数。

通常，此函数由 调用`COleControlSite::InvokeHelper`。

## <a name="colecontrolsiteisdefaultbutton"></a><a name="isdefaultbutton"></a>COle 控制网站：默认按钮

确定控件是否为默认按钮。

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>返回值

如果控件是窗口上的默认按钮，则为非零，否则为零。

## <a name="colecontrolsiteiswindowenabled"></a><a name="iswindowenabled"></a>COle 控制网站：启用窗口

确定控制站点是否启用。

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>返回值

如果启用了控件，则为非零，否则为零。

### <a name="remarks"></a>备注

该值将从控件的"已启用"股票属性中检索。

## <a name="colecontrolsitem_biswindowless"></a><a name="m_biswindowless"></a>COle 控制网站：m_bIsWindowless

确定对象是否为无窗口控件。

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>备注

如果控件没有窗口，则非零，否则为零。

## <a name="colecontrolsitem_ctlinfo"></a><a name="m_ctlinfo"></a>COle 控制网站：m_ctlInfo

有关控件如何处理键盘输入的信息。

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>备注

此信息存储在[CONTROLINFO](/windows/win32/api/ocidl/ns-ocidl-controlinfo)结构中。

## <a name="colecontrolsitem_dweventsink"></a><a name="m_dweventsink"></a>COle 控制网站：m_dwEventSink

包含来自控件事件接收器的连接点的 Cookie。

```
DWORD m_dwEventSink;
```

## <a name="colecontrolsitem_dwmiscstatus"></a><a name="m_dwmiscstatus"></a>COle 控制网站：m_dwMiscStatus

包含有关控件的杂项信息。

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[OLEMISC。](/windows/win32/api/oleidl/ne-oleidl-olemisc)

## <a name="colecontrolsitem_dwpropnotifysink"></a><a name="m_dwpropnotifysink"></a>COle 控制网站：m_dwPropNotifySink

包含[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) Cookie。

```
DWORD m_dwPropNotifySink;
```

## <a name="colecontrolsitem_dwstyle"></a><a name="m_dwstyle"></a>COle 控制网站：m_dwStyle

包含控件的窗口样式。

```
DWORD m_dwStyle;
```

## <a name="colecontrolsitem_hwnd"></a><a name="m_hwnd"></a>COle 控制网站：m_hWnd

包含控件的 HWND，如果控件没有窗口，则包含 NULL。

```
HWND m_hWnd;
```

## <a name="colecontrolsitem_iidevents"></a><a name="m_iidevents"></a>COle 控制网站：m_iidEvents

包含控件的默认事件接收器接口的接口 ID。

```
IID m_iidEvents;
```

## <a name="colecontrolsitem_nid"></a><a name="m_nid"></a>COle 控制网站：m_nID

包含控件的对话框项 ID。

```
UINT m_nID;
```

## <a name="colecontrolsitem_pactiveobject"></a><a name="m_pactiveobject"></a>COle 控制网站：m_pActiveObject

包含控件的[IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject)接口。

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

## <a name="colecontrolsitem_pctrlcont"></a><a name="m_pctrlcont"></a>COle 控制网站：m_pCtrlCont

包含控件的容器（表示窗体）。

```
COleControlContainer* m_pCtrlCont;
```

## <a name="colecontrolsitem_pinplaceobject"></a><a name="m_pinplaceobject"></a>COle 控制网站：m_pInPlaceObject

包含控件的`IOleInPlaceObject` [IOleInPlace 对象](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject)接口。

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

## <a name="colecontrolsitem_pobject"></a><a name="m_pobject"></a>COle 控制网站：m_pObject

包含控件`IOleObjectInterface`的接口。

```
LPOLEOBJECT m_pObject;
```

## <a name="colecontrolsitem_pwindowlessobject"></a><a name="m_pwindowlessobject"></a>COle 控制网站：m_pWindowlessObject

包含控件的`IOleInPlaceObjectWindowless` [IOleInPlace 无窗口](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)接口。

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

## <a name="colecontrolsitem_pwndctrl"></a><a name="m_pwndctrl"></a>COle 控制网站：m_pWndCtrl

包含指向表示控件本身`CWnd`的对象的指针。

```
CWnd* m_pWndCtrl;
```

## <a name="colecontrolsitem_rect"></a><a name="m_rect"></a>COle控制网站：：m_rect

包含控件相对于容器窗口的边界。

```
CRect m_rect;
```

## <a name="colecontrolsitemodifystyle"></a><a name="modifystyle"></a>COle 控制网站：修改样式

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
窗口定位标志。 有关可能值的列表，请参阅 Windows SDK 中的[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)函数。

### <a name="return-value"></a>返回值

如果样式已更改，则非零，否则为零。

### <a name="remarks"></a>备注

控件的"已启用"属性将修改以匹配WS_DISABLED设置。 控件的库存边框样式属性将修改以匹配 WS_BORDER请求的设置。 所有其他样式将直接应用于控件的窗口句柄（如果存在）。

修改控件的窗口样式。 要添加或删除的样式可以使用位或 （ &#124; ） 运算符进行组合。 有关可用窗口样式的信息，请参阅 Windows SDK 中的["创建窗口](/windows/win32/api/winuser/nf-winuser-createwindoww)"功能。

如果*nFlags*是非零`ModifyStyle`，请调用 Win32 函数`SetWindowPos`，并通过将*nFlags*与以下四个标志组合来重绘窗口：

- SWP_NOSIZE 保留当前大小。

- SWP_NOMOVE 保留当前位置。

- SWP_NOZORDER保留当前 Z 订单。

- SWP_NOACTIVATE不激活窗口。

要修改窗口的扩展样式，请调用[ModifyStyleEx](#modifystyleex)。

## <a name="colecontrolsitemodifystyleex"></a><a name="modifystyleex"></a>COle 控制网站：修改样式

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
窗口定位标志。 有关可能值的列表，请参阅 Windows SDK 中的[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)函数。

### <a name="return-value"></a>返回值

如果样式已更改，则非零，否则为零。

### <a name="remarks"></a>备注

控件的"外观"属性将修改以匹配WS_EX_CLIENTEDGE设置。 所有其他扩展窗口样式将直接应用于控件的窗口句柄（如果存在）。

修改控件站点对象的窗口扩展样式。 要添加或删除的样式可以使用位或 （ &#124; ） 运算符进行组合。 有关可用窗口样式的信息，请参阅 Windows SDK 中的["创建窗口Ex"](/windows/win32/api/winuser/nf-winuser-createwindowexw)功能。

如果*nFlags*是非零`ModifyStyleEx`，请调用 Win32 函数`SetWindowPos`，并通过将*nFlags*与以下四个标志组合来重绘窗口：

- SWP_NOSIZE 保留当前大小。

- SWP_NOMOVE 保留当前位置。

- SWP_NOZORDER保留当前 Z 订单。

- SWP_NOACTIVATE不激活窗口。

要修改窗口的扩展样式，请调用["修改样式](#modifystyle)"。

## <a name="colecontrolsitemovewindow"></a><a name="movewindow"></a>COle 控制网站：移动窗口

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

*Y*<br/>
窗口顶部的新位置。

*n 宽度*<br/>
窗口的新宽度

*nHeight*<br/>
窗口的新高度。

## <a name="colecontrolsitequickactivate"></a><a name="quickactivate"></a>COle 控制网站：快速激活

快速激活包含的控件。

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>返回值

如果控制站点已激活，则非零，否则为零。

### <a name="remarks"></a>备注

仅当用户重写控件的创建过程时，才应调用此函数。

发生`IPersist*::Load`快速`IPersist*::InitNew`激活后应调用 和 方法。 在快速激活期间，控件应建立与容器接收器的连接。 但是，这些连接在调用或`IPersist*::Load``IPersist*::InitNew`被调用之前不会活。

## <a name="colecontrolsitesafesetproperty"></a><a name="safesetproperty"></a>COle 控制网站：安全设置属性

设置*dwDispID*指定的控件属性。

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识要设置的属性或方法的调度 ID，该 ID 位于控件`IDispatch`的接口上。

*vtProp*<br/>
指定要设置的属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*...*<br/>
*vtProp*指定的类型的单个参数。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

> [!NOTE]
> 如果`SetProperty`遇到`SetPropertyV`错误（例如尝试设置不存在的属性），则与 和 不同，则不引发异常。

## <a name="colecontrolsitesetdefaultbutton"></a><a name="setdefaultbutton"></a>COle 控制网站：设置默认按钮

将控件设置为默认按钮。

```cpp
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>参数

*b默认*<br/>
如果控件应成为默认按钮，则非零;否则为零。

### <a name="remarks"></a>备注

> [!NOTE]
> 控件必须设置OLEMISC_ACTSLIKEBUTTON状态位。

## <a name="colecontrolsitesetdlgctrlid"></a><a name="setdlgctrlid"></a>COle 控制网站：SetDlgCtrlID

更改控件的对话框项标识符的值。

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
新的标识符值。

### <a name="return-value"></a>返回值

如果成功，窗口的上一个对话框项标识符;如果成功，则窗口的上一个对话框项标识符。否则 0。

### <a name="remarks"></a>备注

## <a name="colecontrolsitesetfocus"></a><a name="setfocus"></a>COle 控制网站：设置焦点

将焦点设置到控件。

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>参数

*lpmsg*<br/>
指向[MSG 结构](/windows/win32/api/winuser/ns-winuser-msg)的指针。 此结构包含触发当前控件站点中包含的控件`SetFocus`请求的 Windows 消息。

### <a name="return-value"></a>返回值

指向以前具有焦点的窗口的指针。

## <a name="colecontrolsitesetproperty"></a><a name="setproperty"></a>COle 控制网站：设置属性

设置*dwDispID*指定的控件属性。

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识要设置的属性或方法的调度 ID，该 ID 位于控件`IDispatch`的接口上。

*vtProp*<br/>
指定要设置的属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*...*<br/>
*vtProp*指定的类型的单个参数。

### <a name="remarks"></a>备注

如果`SetProperty`遇到错误，将引发异常。

异常的类型由尝试设置属性或方法的返回值确定。 如果返回值为`DISP_E_EXCEPTION`，`COleDispatchExcpetion`则引发否则为`COleException`。

## <a name="colecontrolsitesetpropertyv"></a><a name="setpropertyv"></a>COle 控制网站：SetPropertyV

设置*dwDispID*指定的控件属性。

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>参数

*dwDispID*<br/>
标识要设置的属性或方法的调度 ID，该 ID 位于控件`IDispatch`的接口上。

*vtProp*<br/>
指定要设置的属性的类型。 有关可能的值，请参阅备注部分 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。

*阿格列斯*<br/>
指向参数列表的指针。

### <a name="remarks"></a>备注

可以使用*arg_list*参数传递所调用的方法或属性的额外参数。 如果`SetProperty`遇到错误，将引发异常。

异常的类型由尝试设置属性或方法的返回值确定。 如果返回值为`DISP_E_EXCEPTION`，`COleDispatchExcpetion`则引发否则为`COleException`。

## <a name="colecontrolsitesetwindowpos"></a><a name="setwindowpos"></a>COle 控制网站：设置窗口位置

设置控制站点的大小、位置和 Z 顺序。

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

*pWndInsert 后*<br/>
指向窗口的指针。

*x*<br/>
窗口左侧的新位置。

*Y*<br/>
窗口顶部的新位置。

*残雪*<br/>
窗口的新宽度

*cy*<br/>
窗口的新高度。

*nFlags*<br/>
指定窗口大小调整和定位标志。 有关可能的值，请参阅 Windows SDK 中["设置窗口Pos"](/windows/win32/api/winuser/nf-winuser-setwindowpos)的备注部分。

### <a name="return-value"></a>返回值

如果成功，则非零，否则为零。

## <a name="colecontrolsitesetwindowtext"></a><a name="setwindowtext"></a>COle 控制网站：设置窗口文本

设置控件站点的文本。

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*lpszString*<br/>
指向要用作新标题或控件文本的 null 终止字符串的指针。

### <a name="remarks"></a>备注

此函数首先尝试设置标题股票属性。 如果不支持"标题"股票属性，则改为设置 Text 属性。

## <a name="colecontrolsiteshowwindow"></a><a name="showwindow"></a>COle 控制网站：显示窗口

设置窗口的显示状态。

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>参数

*nCmdShow*<br/>
指定如何显示控件站点。 它必须是以下值之一：

- SW_HIDE隐藏此窗口并将激活传递到另一个窗口。

- SW_MINIMIZE最小化窗口并激活系统列表中的顶级窗口。

- SW_RESTORE 激活并显示窗口。 如果窗口最小化或最大化，Windows 会将其还原到其原始大小和位置。

- SW_SHOW激活窗口，并将其以当前大小和位置显示。

- SW_SHOWMAXIMIZED激活窗口并将其显示为最大化窗口。

- SW_SHOWMINIMIZED激活窗口并将其显示为图标。

- SW_SHOWMINNOACTIVE将窗口显示为图标。 当前处于活动状态的窗口保持活动状态。

- SW_SHOWNA 显示窗口当前状态。 当前处于活动状态的窗口保持活动状态。

- SW_SHOWNOACTIVATE 以最新的大小和位置显示窗口。 当前处于活动状态的窗口保持活动状态。

- SW_SHOWNORMAL 激活并显示窗口。 如果窗口最小化或最大化，Windows 会将其还原到其原始大小和位置。

### <a name="return-value"></a>返回值

如果窗口以前可见，则非零;如果窗口以前已隐藏，则为 0。

## <a name="see-also"></a>请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleControlContainer 类](../../mfc/reference/colecontrolcontainer-class.md)
