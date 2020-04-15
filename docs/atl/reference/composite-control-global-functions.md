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
ms.openlocfilehash: 99ecd4cf04b3eb696f897d6ef5a5e3839d46ef17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331602"
---
# <a name="composite-control-global-functions"></a>复合控件全局函数

这些功能支持创建对话框，以及创建、托管和许可 ActiveX 控件。

> [!IMPORTANT]
> 下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|从用户提供的对话框模板创建模式对话框。 生成的对话框可以包含 ActiveX 控件。|
|[AtlAxCreateDialog](#atlaxcreatedialog)|从用户提供的对话框模板创建无模式对话框。 生成的对话框可以包含 ActiveX 控件。|
|[AtlAxCreateControl](#atlaxcreatecontrol)|创建 ActiveX 控件，初始化它并在指定窗口中承载它。|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|创建 ActiveX 控件，初始化它，在指定的窗口中托管它，并从控件中检索接口指针（或指针）。|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|创建许可的 ActiveX 控件，初始化它，在指定的窗口中托管它，并从控件中检索接口指针（或指针）。|
|[AtlAxAttachControl](#atlaxattachcontrol)|将以前创建的控件附加到指定窗口。|
|[AtlAxGetHost](#atlaxgethost)|用于获取指向指定窗口（如果有）容器的直接接口指针，给定其句柄。|
|[AtlAxGetControl](#atlaxgetcontrol)|用于获取指向指定窗口内（如果有）中包含的控件的直接接口指针，给定其句柄。|
|[AtlSetChildSite](#atlsetchildsite)|初始化`IUnknown`子站点。|
|[AtlAxWinInit](#atlaxwininit)|初始化 AxWin 对象的托管代码。|
|[AtlAxWinTerm](#atlaxwinterm)|取消初始化 AxWin 对象的托管代码。|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|返回有关对象的默认源接口的信息。|

## <a name="requirements"></a>要求

**标题：** atlhost.h

## <a name="atlaxdialogbox"></a><a name="atlaxdialogbox"></a>阿托克斯对话盒

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
[在]标识可执行文件的可执行文件包含对话框模板的模块的实例。

*lpTemplate 名称*<br/>
[在]标识对话框模板。 此参数是指向指定对话框模板名称的 null 端接字符串的指针，或指定对话框模板的资源标识符的整数值。 如果参数指定资源标识符，则其高阶单词必须为零，其低阶字必须包含标识符。 您可以使用[MAKEINTRESOURCE 宏](/windows/win32/api/winuser/nf-winuser-makeintresourcew)创建此值。

*hWnd 父母*<br/>
[在]标识拥有对话框的窗口。

*lpDialogProc*<br/>
[在]指向对话框过程。 有关对话框过程的详细信息，请参阅[对话框过程](/windows/win32/api/winuser/nc-winuser-dlgproc)。

*德维尼帕拉姆*<br/>
[在]指定要传递给WM_INITDIALOG消息的*lParam*参数中的对话框的值。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

要与`AtlAxDialogBox`包含 ActiveX 控件的对话框模板一起使用，请指定有效的 CLSID、APPID 或 URL 字符串作为对话框资源**CONTROL**部分*的文本*字段，以及同一节下的*类名*字段的"AtlAxWin80"。 下面演示了有效的**CONTROL**部分可能是什么样子：

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

有关编辑资源脚本的详细信息，请参阅[如何：以文本格式打开资源脚本文件](../../windows/how-to-open-a-resource-script-file-in-text-format.md)。 有关控件资源定义语句的详细信息，请参阅 Windows SDK[下的通用控制参数](/windows/win32/menurc/common-control-parameters)：SDK 工具。

有关对话框的详细信息，请参阅 Windows SDK 中的[对话框](/windows/win32/api/winuser/nf-winuser-dialogboxw)和[创建对话帕拉姆](/windows/win32/api/winuser/nf-winuser-createdialogparamw)。

## <a name="atlaxcreatedialog"></a><a name="atlaxcreatedialog"></a>AtlAx创建对话

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
[在]标识可执行文件的可执行文件包含对话框模板的模块的实例。

*lpTemplate 名称*<br/>
[在]标识对话框模板。 此参数是指向指定对话框模板名称的 null 端接字符串的指针，或指定对话框模板的资源标识符的整数值。 如果参数指定资源标识符，则其高阶单词必须为零，其低阶字必须包含标识符。 您可以使用[MAKEINTRESOURCE 宏](/windows/win32/api/winuser/nf-winuser-makeintresourcew)创建此值。

*hWnd 父母*<br/>
[在]标识拥有对话框的窗口。

*lpDialogProc*<br/>
[在]指向对话框过程。 有关对话框过程的详细信息，请参阅[对话框过程](/windows/win32/api/winuser/nc-winuser-dlgproc)。

*德维尼帕拉姆*<br/>
[在]指定要传递给WM_INITDIALOG消息的*lParam*参数中的对话框的值。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

生成的对话框可以包含 ActiveX 控件。

请参阅在 Windows SDK 中[创建对话](/windows/win32/api/winuser/nf-winuser-createdialogw)和[创建对话帕拉姆](/windows/win32/api/winuser/nf-winuser-createdialogparamw)。

## <a name="atlaxcreatecontrol"></a><a name="atlaxcreatecontrol"></a>AtlAx创建控制

创建 ActiveX 控件，初始化它并在指定窗口中承载它。

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
指向要传递给控件的字符串的指针。 必须采用以下方式之一进行格式化：

- ProgID，如`"MSCAL.Calendar.7"`

- CLSID，如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，如`"<https://www.microsoft.com>"`

- 对活动文档的引用，例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必须在 HTML 片段之前，以便将其指定为 MSHTML 流。

*hwnd*<br/>
[在]处理控件将附加到的窗口。

*pStream*<br/>
[在]指向用于初始化控件属性的流的指针。 可以为 NULL。

*ppUnk容器*<br/>
[出]将接收容器`IUnknown`的指针的地址。 可以为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

此全局函数为您提供与调用 AtlAxCreateControlEx（lpszName、hwnd、pStream、NULL、NULL、NULL）相同的结果; [AtlAxCreateControlEx](#atlaxcreatecontrolex)*lpszName* *hWnd* *pStream*

要创建许可的 ActiveX 控件，请参阅[AtlAx 创建控制 。](#atlaxcreatecontrollic)

## <a name="atlaxcreatecontrolex"></a><a name="atlaxcreatecontrolex"></a>AtlAx创建控制Ex

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

*lpsz名称*<br/>
指向要传递给控件的字符串的指针。 必须采用以下方式之一进行格式化：

- ProgID，如`"MSCAL.Calendar.7"`

- CLSID，如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，如`"<https://www.microsoft.com>"`

- 对活动文档的引用，例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必须在 HTML 片段之前，以便将其指定为 MSHTML 流。

*hwnd*<br/>
[在]处理控件将附加到的窗口。

*pStream*<br/>
[在]指向用于初始化控件属性的流的指针。 可以为 NULL。

*ppUnk容器*<br/>
[出]将接收容器`IUnknown`的指针的地址。 可以为 NULL。

*ppUnkControl*<br/>
[出]将接收已创建控件`IUnknown`的指针的地址。 可以为 NULL。

*iidSink*<br/>
包含对象上传出接口的接口标识符。

*朋克辛克*<br/>
指向接收器对象`IUnknown`接口的指针，用于在成功创建包含的对象后，将连接到*iidSink*在包含对象上指定的连接点。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

`AtlAxCreateControlEx`与[AtlAxCreateControl](#atlaxcreatecontrol)类似，但也允许您接收指向新创建的控件的接口指针，并设置事件接收器以接收控件触发的事件。

要创建许可的 ActiveX 控件，请参阅[AtlAxCreateControllicEx](#atlaxcreatecontrollicex)。

## <a name="atlaxcreatecontrollic"></a><a name="atlaxcreatecontrollic"></a>AtlAx 创建控制

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

*lpsz名称*<br/>
指向要传递给控件的字符串的指针。 必须采用以下方式之一进行格式化：

- ProgID，如`"MSCAL.Calendar.7"`

- CLSID，如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，如`"<https://www.microsoft.com>"`

- 对活动文档的引用，例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必须在 HTML 片段之前，以便将其指定为 MSHTML 流。

*hwnd*<br/>
处理控件将附加到的窗口。

*pStream*<br/>
指向用于初始化控件属性的流的指针。 可以为 NULL。

*ppUnk容器*<br/>
将接收容器`IUnknown`的指针的地址。 可以为 NULL。

*bstrLIC*<br/>
包含控件许可证的 BSTR。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="example"></a>示例

有关如何 使用`AtlAxCreateControlLic`[的 托管 ActiveX 控件，请参阅 ATL AXHost。](../../atl/hosting-activex-controls-using-atl-axhost.md)

## <a name="atlaxcreatecontrollicex"></a><a name="atlaxcreatecontrollicex"></a>AtlAx 创建控制

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

*lpsz名称*<br/>
指向要传递给控件的字符串的指针。 必须采用以下方式之一进行格式化：

- ProgID，如`"MSCAL.Calendar.7"`

- CLSID，如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，如`"<https://www.microsoft.com>"`

- 对活动文档的引用，例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必须在 HTML 片段之前，以便将其指定为 MSHTML 流。

*hwnd*<br/>
处理控件将附加到的窗口。

*pStream*<br/>
指向用于初始化控件属性的流的指针。 可以为 NULL。

*ppUnk容器*<br/>
将接收容器`IUnknown`的指针的地址。 可以为 NULL。

*ppUnkControl*<br/>
[出]将接收已创建控件`IUnknown`的指针的地址。 可以为 NULL。

*iidSink*<br/>
包含对象上传出接口的接口标识符。

*朋克辛克*<br/>
指向接收器对象`IUnknown`接口的指针，用于在成功创建包含的对象后，将连接到*iidSink*在包含对象上指定的连接点。

*bstrLIC*<br/>
包含控件许可证的 BSTR。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

`AtlAxCreateControlLicEx`与[AtlAxCreateControlLic](#atlaxcreatecontrollic)类似，但也允许您接收指向新创建的控件的接口指针，并设置事件接收器以接收控件触发的事件。

### <a name="example"></a>示例

有关如何 使用`AtlAxCreateControlLicEx`[的 托管 ActiveX 控件，请参阅 ATL AXHost。](../../atl/hosting-activex-controls-using-atl-axhost.md)

## <a name="atlaxattachcontrol"></a><a name="atlaxattachcontrol"></a>Atlax 附加控制

将以前创建的控件附加到指定窗口。

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>参数

*pControl*<br/>
[在]指向控件`IUnknown`的指针。

*hwnd*<br/>
[在]处理将承载控件的窗口。

*ppUnk容器*<br/>
[出]指向容器对象的指针`IUnknown`。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

使用[AtlAxCreateControlEx](#atlaxcreatecontrolex)和[AtlAxCreateControl](#atlaxcreatecontrol)可同时创建和附加控件。

> [!NOTE]
> 在调用`AtlAxAttachControl`之前，必须正确初始化所连接的控件对象。

## <a name="atlaxgethost"></a><a name="atlaxgethost"></a>AtlAxGetHost

获取指向指定窗口（如果有）的容器的直接接口指针（在给定容器的句柄的情况下）。

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>参数

*H*<br/>
[在]承载控件的窗口的句柄。

*Pp*<br/>
[出]控件`IUnknown`的容器的 。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="atlaxgetcontrol"></a><a name="atlaxgetcontrol"></a>AtlAxGetControl

获取指向包含在指定窗口内的控件的直接接口指针（在给定控件的句柄的情况下）。

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>参数

*H*<br/>
[在]承载控件的窗口的句柄。

*Pp*<br/>
[出]要`IUnknown`承载的控件的 。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="atlsetchildsite"></a><a name="atlsetchildsite"></a>AtlSet儿童网站

调用此函数以将子对象的站点设置为`IUnknown`父对象的站点。

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>参数

*朋克儿童*<br/>
[在]指向`IUnknown`子接口的指针。

*朋克家长*<br/>
[在]指向父级`IUnknown`接口的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="atlaxwininit"></a><a name="atlaxwininit"></a>阿托尔克斯·维尼尼特

此功能通过注册 **"AtlAxWin80"** 和 **"AtlAxWinLic80"** 窗口类以及几个自定义窗口消息来初始化 ATL 的控制托管代码。

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>返回值

如果控件托管代码的初始化成功，则非零;否则 FALSE。

### <a name="remarks"></a>备注

在使用 ATL 控件托管 API 之前，必须调用此功能。 调用此功能后 **，"AtlAxWin"** 窗口类可用于[创建窗口](/windows/win32/api/winuser/nf-winuser-createwindoww)或[创建WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的调用，如 Windows SDK 中所述。

## <a name="atlaxwinterm"></a><a name="atlaxwinterm"></a>AtlAxWinterm

此函数通过取消注册 **"AtlAxWin80"** 和 **"AtlAxWinLic80"** 窗口类来取消初始化 ATL 的控制托管代码。

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

此函数只是调用 Windows SDK 中所述[的取消注册类](/windows/win32/api/winuser/nf-winuser-unregisterclassw)。

如果调用[AtlAxWinInit，](#atlaxwininit)并且不再需要创建主机窗口，则调用此函数以在所有现有主机窗口被销毁后进行清理。 如果不调用此函数，则进程终止时将自动取消注册窗口类。

## <a name="atlgetobjectsourceinterface"></a><a name="atlgetobjectsourceinterface"></a>AtlGetObject来源接口

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

*朋克奥比*<br/>
[在]指向要为其返回信息的对象的指针。

*普利比德*<br/>
[出]指向包含源接口定义的类型库的 LIBID 的指针。

*皮伊德*<br/>
[出]指向对象默认源接口的接口 ID 的指针。

*pdwMajor*<br/>
[出]指向包含源接口定义的类型库的主要版本号的指针。

*pdwMinor*<br/>
[出]指向包含源接口定义的类型库的次要版本号的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

`AtlGetObjectSourceInterface`可以为您提供默认源接口的接口 ID，以及描述该接口的类型库的 LIBID 和主要版本号和次要版本号。

> [!NOTE]
> 若要成功检索请求的信息，*由 punkObj* `IDispatch`表示的对象必须实现（并通过`IDispatch::GetTypeInfo`返回类型信息），并且还必须实现`IProvideClassInfo2`或`IPersist`。 源接口的类型信息必须与 的类型信息位于同一`IDispatch`类型库中。

### <a name="example"></a>示例

下面的示例显示了如何定义事件接收器类 ，`CEasySink`这减少了可以传递给`IDispEventImpl`基本要素的模板参数数。 `EasyAdvise`并`EasyUnadvise`用于`AtlGetObjectSourceInterface`初始化[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)成员，然后再致电[DispEvent 建议](idispeventsimpleimpl-class.md#dispeventadvise)或[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)。

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)<br/>
[复合控制宏](../../atl/reference/composite-control-macros.md)
