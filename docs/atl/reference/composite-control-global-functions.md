---
title: 复合控件全局函数
ms.date: 11/04/2016
f1_keywords:
- atlhost/ATL::AtlAxDialogBox
- atlhost/ATL::AtlAxCreateDialog
- atlhost/ATL::AtlAxCreateControl
- atlhost/ATL::AtlAxCreateControlEx
- atlhost/ATL::AtlAxCreateControlLic
- atlhost/ATL::AtlAxCreateControlLicEx
- atlhost/ATL::AtlAxAttachControl
- atlhost/ATL::AtlAxGetHost
- atlhost/ATL::AtlAxGetControl
- atlhost/ATL::AtlSetChildSite
- atlhost/ATL::AtlAxWinInit
- atlhost/ATL::AtlAxWinTerm
- atlhost/ATL::AtlGetObjectSourceInterface
helpviewer_keywords:
- composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
ms.openlocfilehash: 6438b9d125cc2b44c6c4525dcfa5a2bd95763304
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524425"
---
# <a name="composite-control-global-functions"></a>复合控件全局函数

用于创建对话框框中，以及用于创建、 托管和授权 ActiveX 控件，这些函数提供支持。

> [!IMPORTANT]
>  下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|从用户提供的对话框模板创建模式对话框。 随后出现的对话框中可以包含 ActiveX 控件。|
|[AtlAxCreateDialog](#atlaxcreatedialog)|从用户提供的对话框模板创建无模式对话框。 随后出现的对话框中可以包含 ActiveX 控件。|
|[AtlAxCreateControl](#atlaxcreatecontrol)|创建 ActiveX 控件，初始化它并在指定窗口中承载它。|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|创建 ActiveX 控件，初始化它、 承载在指定的窗口中，并从控件检索接口指针 （或指针）。|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|创建授权的 ActiveX 控件、 其进行初始化，承载在指定的窗口中，并从控件检索接口指针 （或指针）。|
|[AtlAxAttachControl](#atlaxattachcontrol)|将以前创建的控件附加到指定窗口。|
|[AtlAxGetHost](#atlaxgethost)|用于获取到指定窗口 （如果有），该容器的直接接口指针给定其句柄。|
|[AtlAxGetControl](#atlaxgetcontrol)|用于获取在指定窗口 （如果有），包含的控件的直接接口指针给定其句柄。|
|[AtlSetChildSite](#atlsetchildsite)|初始化`IUnknown`的子站点。|
|[AtlAxWinInit](#atlaxwininit)|初始化 AxWin 对象的托管代码。|
|[AtlAxWinTerm](#atlaxwinterm)|取消初始化 AxWin 对象的托管代码。|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|返回对象的默认源接口的信息。|

## <a name="requirements"></a>要求

**标头：** atlhost.h

##  <a name="atlaxdialogbox"></a>  AtlAxDialogBox

从用户提供的对话框模板创建模式对话框。

```
ATLAPI_(int) AtlAxDialogBox(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>参数

*hInstance*<br/>
[in]标识其可执行文件包含对话框模板的模块的实例。

*lpTemplateName*<br/>
[in]标识对话框模板。 此参数是指向一个以 null 结尾的字符字符串，指定的对话框模板的名称的指针或整数值，该值指定对话框模板的资源标识符。 如果参数指定资源标识符，其高序位字必须为零，其低序位字必须包含标识符。 可以使用[MAKEINTRESOURCE](/windows/desktop/api/winuser/nf-winuser-makeintresourcea)宏来创建此值。

*hWndParent*<br/>
[in]标识拥有对话框的窗口。

*lpDialogProc*<br/>
[in]指向对话框过程。 有关对话框过程的详细信息，请参阅[DialogProc](https://msdn.microsoft.com/library/windows/desktop/ms645469)。

*dwInitParam*<br/>
[in]指定要传递到该对话框中的值*lParam* WM_INITDIALOG 消息参数。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

若要使用`AtlAxDialogBox`与包含 ActiveX 控件的对话框模板，请指定有效的 CLSID、 应用程序标识或 URL 作为字符串*文本*字段**控制**对话框资源的部分以及"AtlAxWin80"作为*类名*字段下的同一部分。 以下内容演示的哪些是有效**控制**部分可能如下所示：

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

编辑资源脚本的详细信息，请参阅[如何： 以文本格式打开资源脚本文件](../../windows/how-to-open-a-resource-script-file-in-text-format.md)。 控制资源定义语句的详细信息，请参阅[常见控制参数](/windows/desktop/menurc/common-control-parameters)下 Windows SDK: SDK Tools。

有关常规中的对话框的详细信息，请参阅[DialogBox](/windows/desktop/api/winuser/nf-winuser-dialogboxa)并[CreateDialogParam](/windows/desktop/api/winuser/nf-winuser-createdialogparama) Windows SDK 中。

##  <a name="atlaxcreatedialog"></a>  AtlAxCreateDialog

从用户提供的对话框模板创建无模式对话框。

```
ATLAPI_(HWND) AtlAxCreateDialog(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>参数

*hInstance*<br/>
[in]标识其可执行文件包含对话框模板的模块的实例。

*lpTemplateName*<br/>
[in]标识对话框模板。 此参数是指向一个以 null 结尾的字符字符串，指定的对话框模板的名称的指针或整数值，该值指定对话框模板的资源标识符。 如果参数指定资源标识符，其高序位字必须为零，其低序位字必须包含标识符。 可以使用[MAKEINTRESOURCE](/windows/desktop/api/winuser/nf-winuser-makeintresourcea)宏来创建此值。

*hWndParent*<br/>
[in]标识拥有对话框的窗口。

*lpDialogProc*<br/>
[in]指向对话框过程。 有关对话框过程的详细信息，请参阅[DialogProc](https://msdn.microsoft.com/library/windows/desktop/ms645469)。

*dwInitParam*<br/>
[in]指定要传递到该对话框中的值*lParam* WM_INITDIALOG 消息参数。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

随后出现的对话框中可以包含 ActiveX 控件。

请参阅[CreateDialog](/windows/desktop/api/winuser/nf-winuser-createdialoga)并[CreateDialogParam](/windows/desktop/api/winuser/nf-winuser-createdialogparama) Windows SDK 中。

##  <a name="atlaxcreatecontrol"></a>  AtlAxCreateControl

创建 ActiveX 控件，初始化它并在指定窗口中承载它。

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
指向要传递给控件的字符串的指针。 通过以下方式之一的格式必须：

- 例如，"MSCAL ProgID。Calendar.7"

- 例如"{8E27C92B-1264-101C-8A2F-040224009C02}"CLSID

- URL，例如"<http://www.microsoft.com>"

- 对等活动文档的引用"file://\\\Documents\MyDoc.doc"

- 如 HTML 片段"MSHTML:\<HTML >\<正文 > 这是文本行\</B o d >\</HTML >"

   > [!NOTE]
   > "MSHTML:"，以便它指定为 MSHTML 流必须在之前的 HTML 片段。

*hWnd*<br/>
[in]控件将附加到窗口句柄。

*pStream*<br/>
[in]指向用于初始化控件的属性的流的指针。 可以为 NULL。

*ppUnkContainer*<br/>
[out]将接收的指针的地址`IUnknown`的容器。 可以为 NULL。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

此全局函数可调用相同的结果[AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*， *hWnd*， *pStream*、 NULL、 为 NULL，为 NULL，NULL);。

若要创建授权的 ActiveX 控件，请参阅[AtlAxCreateControlLic](#atlaxcreatecontrollic)。

##  <a name="atlaxcreatecontrolex"></a>  AtlAxCreateControlEx

创建 ActiveX 控件，初始化它并在指定窗口中承载它。 也可以创建新控件的接口指针和事件接收器。

```
ATLAPI AtlAxCreateControlEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
指向要传递给控件的字符串的指针。 通过以下方式之一的格式必须：

- 例如，"MSCAL ProgID。Calendar.7"

- 例如"{8E27C92B-1264-101C-8A2F-040224009C02}"CLSID

- URL，例如"<http://www.microsoft.com>"

- 对等活动文档的引用"file://\\\Documents\MyDoc.doc"

- 如 HTML 片段"MSHTML:\<HTML >\<正文 > 这是文本行\</B o d >\</HTML >"

   > [!NOTE]
   > "MSHTML:"，以便它指定为 MSHTML 流必须在之前的 HTML 片段。

*hWnd*<br/>
[in]控件将附加到窗口句柄。

*pStream*<br/>
[in]指向用于初始化控件的属性的流的指针。 可以为 NULL。

*ppUnkContainer*<br/>
[out]将接收的指针的地址`IUnknown`的容器。 可以为 NULL。

*ppUnkControl*<br/>
[out]将接收的指针的地址`IUnknown`的创建的控件。 可以为 NULL。

*iidSink*<br/>
包含的对象上的传出接口的接口标识符。

*punkSink*<br/>
一个指向`IUnknown`接收器对象连接到由指定的连接点的接口*iidSink*上包含的对象后已成功创建包含的对象。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

`AtlAxCreateControlEx` 类似于[AtlAxCreateControl](#atlaxcreatecontrol)但还允许您接收到新创建的控件的接口指针并将事件接收器设置为接收控件触发的事件。

若要创建授权的 ActiveX 控件，请参阅[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)。

##  <a name="atlaxcreatecontrollic"></a>  AtlAxCreateControlLic

创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。

```
ATLAPI AtlAxCreateControlLic(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
指向要传递给控件的字符串的指针。 通过以下方式之一的格式必须：

- 例如，"MSCAL ProgID。Calendar.7"

- 例如"{8E27C92B-1264-101C-8A2F-040224009C02}"CLSID

- URL，例如"<http://www.microsoft.com>"

- 对等活动文档的引用"file://\\\Documents\MyDoc.doc"

- 如 HTML 片段"MSHTML:\<HTML >\<正文 > 这是文本行\</B o d >\</HTML >"

   > [!NOTE]
   > "MSHTML:"，以便它指定为 MSHTML 流必须在之前的 HTML 片段。

*hWnd*<br/>
控件将附加到窗口句柄。

*pStream*<br/>
指向用于初始化控件的属性的流的指针。 可以为 NULL。

*ppUnkContainer*<br/>
将接收的指针的地址`IUnknown`的容器。 可以为 NULL。

*bstrLic*<br/>
包含控件的许可证 BSTR。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="example"></a>示例

请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关如何使用的示例`AtlAxCreateControlLic`。

##  <a name="atlaxcreatecontrollicex"></a>  AtlAxCreateControlLicEx

创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。 也可以创建新控件的接口指针和事件接收器。

```
ATLAPI AtlAxCreateControlLicEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
指向要传递给控件的字符串的指针。 通过以下方式之一的格式必须：

- 例如，"MSCAL ProgID。Calendar.7"

- 例如"{8E27C92B-1264-101C-8A2F-040224009C02}"CLSID

- URL，例如"<http://www.microsoft.com>"

- 对等活动文档的引用"file://\\\Documents\MyDoc.doc"

- 如 HTML 片段"MSHTML:\<HTML >\<正文 > 这是文本行\</B o d >\</HTML >"

   > [!NOTE]
   > "MSHTML:"，以便它指定为 MSHTML 流必须在之前的 HTML 片段。

*hWnd*<br/>
控件将附加到窗口句柄。

*pStream*<br/>
指向用于初始化控件的属性的流的指针。 可以为 NULL。

*ppUnkContainer*<br/>
将接收的指针的地址`IUnknown`的容器。 可以为 NULL。

*ppUnkControl*<br/>
[out]将接收的指针的地址`IUnknown`的创建的控件。 可以为 NULL。

*iidSink*<br/>
包含的对象上的传出接口的接口标识符。

*punkSink*<br/>
一个指向`IUnknown`接收器对象连接到由指定的连接点的接口*iidSink*上包含的对象后已成功创建包含的对象。

*bstrLic*<br/>
包含控件的许可证 BSTR。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

`AtlAxCreateControlLicEx` 类似于[AtlAxCreateControlLic](#atlaxcreatecontrollic)但还允许您接收到新创建的控件的接口指针并将事件接收器设置为接收控件触发的事件。

### <a name="example"></a>示例

请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关如何使用的示例`AtlAxCreateControlLicEx`。

##  <a name="atlaxattachcontrol"></a>  AtlAxAttachControl

将以前创建的控件附加到指定窗口。

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>参数

*pControl*<br/>
[in]一个指向`IUnknown`的控件。

*hWnd*<br/>
[in]将承载控件的窗口的句柄。

*ppUnkContainer*<br/>
[out]指针到指向`IUnknown`的容器对象。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

使用[AtlAxCreateControlEx](#atlaxcreatecontrolex)并[AtlAxCreateControl](#atlaxcreatecontrol)以同时创建并附加一个控件。

> [!NOTE]
>  要附加的控件对象必须正确初始化，然后再调`AtlAxAttachControl`。

##  <a name="atlaxgethost"></a>  AtlAxGetHost

获取指向指定窗口（如果有）的容器的直接接口指针（在给定容器的句柄的情况下）。

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>参数

*h*<br/>
[in]托管控件的窗口句柄。

*pp*<br/>
[out]`IUnknown`的控件的容器。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="atlaxgetcontrol"></a>  AtlAxGetControl

获取指向包含在指定窗口内的控件的直接接口指针（在给定控件的句柄的情况下）。

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>参数

*h*<br/>
[in]托管控件的窗口句柄。

*pp*<br/>
[out]`IUnknown`正在承载的控件。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="atlsetchildsite"></a>  AtlSetChildSite

调用此函数可设置到子对象的站点`IUnknown`的父对象。

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>参数

*punkChild*<br/>
[in]一个指向`IUnknown`子接口。

*punkParent*<br/>
[in]一个指向`IUnknown`父级的接口。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="atlaxwininit"></a>  AtlAxWinInit

此函数将初始化 ATL 的控件承载代码通过注册 **"AtlAxWin80"** 并 **"AtlAxWinLic80"** 窗口类以及一些自定义窗口消息。

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>返回值

如果控件承载代码的初始化成功，则非零值否则为 FALSE。

### <a name="remarks"></a>备注

使用 ATL 控件承载 API 之前，必须调用此函数。 向此函数中调用 **"AtlAxWin"** 窗口类可用于调用[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa)或[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)，如 Windows SDK 中所述。

##  <a name="atlaxwinterm"></a>  AtlAxWinTerm

此函数取消初始化 ATL 的控件承载代码通过注销 **"AtlAxWin80"** 并 **"AtlAxWinLic80"** 窗口类。

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

此函数将只需调用[UnregisterClass](https://msdn.microsoft.com/library/windows/desktop/ms644899) Windows SDK 中所述。

调用此函数已被销毁所有现有主机窗口，如果您调用之后进行清理[AtlAxWinInit](#atlaxwininit)和不再需要创建宿主窗口。 如果不调用此函数，窗口类将自动取消注册在进程终止时。

##  <a name="atlgetobjectsourceinterface"></a>  AtlGetObjectSourceInterface

调用此函数可检索有关对象的默认源接口的信息。

```
ATLAPI AtlGetObjectSourceInterface(
    IUnknown* punkObj,
    GUID* plibid,
    IID* piid,
    unsigned short* pdwMajor,
    unsigned short* pdwMinor);
```

### <a name="parameters"></a>参数

*punkObj*<br/>
[in]指向为其返回信息的对象的指针。

*plibid*<br/>
[out]一个指向包含源接口的定义的类型库的 LIBID。

*piid*<br/>
[out]指向对象的默认源接口的接口 ID 的指针。

*pdwMajor*<br/>
[out]指向包含源接口的定义的类型库的主版本号的指针。

*pdwMinor*<br/>
[out]指向包含源接口的定义的类型库的次版本号的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

`AtlGetObjectSourceInterface` 可以为您提供的默认源接口，以及 LIBID 和主要的接口 ID 和描述该接口的类型库的次版本号。

> [!NOTE]
>  要使此函数已成功检索所需的信息，该对象表示*punkObj*必须实现`IDispatch`(并返回类型信息通过`IDispatch::GetTypeInfo`) 以及它还必须实现任一`IProvideClassInfo2`或`IPersist`。 源接口的类型信息的类型信息位于同一个类型库中必须是`IDispatch`。

### <a name="example"></a>示例

下面的示例显示可以如何定义事件接收器类中， `CEasySink`，这样做可以减小的可传递给模板参数的数目`IDispEventImpl`到裸机 essentials。 `EasyAdvise` 并`EasyUnadvise`使用`AtlGetObjectSourceInterface`来初始化[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)成员之前调用[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)或者[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)。

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)<br/>
[复合控件宏](../../atl/reference/composite-control-macros.md)
