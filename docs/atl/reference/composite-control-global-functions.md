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
ms.openlocfilehash: 58c7fed2d6e95967101e98589a13c114fe2e9a8a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496640"
---
# <a name="composite-control-global-functions"></a>复合控件全局函数

这些函数支持创建对话框，以及用于创建、承载和授权 ActiveX 控件。

> [!IMPORTANT]
>  下表中列出的函数不能用于在 Windows 运行时中执行的应用程序。

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|从用户提供的对话框模板创建模式对话框。 生成的对话框可以包含 ActiveX 控件。|
|[AtlAxCreateDialog](#atlaxcreatedialog)|从用户提供的对话框模板创建无模式对话框。 生成的对话框可以包含 ActiveX 控件。|
|[AtlAxCreateControl](#atlaxcreatecontrol)|创建 ActiveX 控件，初始化它并在指定窗口中承载它。|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|创建 ActiveX 控件，对其进行初始化，在指定窗口中承载该控件，并从该控件中检索一个接口指针。|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|创建许可的 ActiveX 控件，对其进行初始化，在指定窗口中承载该控件，并从该控件中检索一个接口指针。|
|[AtlAxAttachControl](#atlaxattachcontrol)|将以前创建的控件附加到指定窗口。|
|[AtlAxGetHost](#atlaxgethost)|用于获取指向指定窗口（如果有）的容器的直接接口指针（在给定其句柄的情况下）。|
|[AtlAxGetControl](#atlaxgetcontrol)|在给定的句柄的情况下，用于获取指向指定窗口（如果有）内包含的控件的直接接口指针。|
|[AtlSetChildSite](#atlsetchildsite)|`IUnknown`初始化子站点的。|
|[AtlAxWinInit](#atlaxwininit)|初始化 AxWin 对象的宿主代码。|
|[AtlAxWinTerm](#atlaxwinterm)|取消 AxWin 对象的宿主代码。|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|返回有关对象的默认源接口的信息。|

## <a name="requirements"></a>要求

**标头：** atlhost

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
中标识可执行文件包含对话框模板的模块的实例。

*lpTemplateName*<br/>
中标识对话框模板。 此参数为以 null 结尾的字符串的指针，该字符串指定对话框模板的名称或指定对话框模板的资源标识符的整数值。 如果参数指定资源标识符，则其高序位字必须为零，并且它的低序位字必须包含标识符。 您可以使用[MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew)宏来创建此值。

*hWndParent*<br/>
中标识拥有对话框的窗口。

*lpDialogProc*<br/>
中指向对话框过程。 有关对话框过程的详细信息，请参阅[DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc)。

*dwInitParam*<br/>
中在 WM_INITDIALOG 消息的*lParam*参数中指定要传递到对话框的值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

若要`AtlAxDialogBox`将与包含 ActiveX 控件的对话框模板一起使用，请将有效的 CLSID、APPID 或 URL 字符串指定为对话框资源的**控件**部分的*文本*字段，并将 "AtlAxWin80" 指定为 "*类名称*" 字段在同一节中。 下面演示了有效的**控件**部分可能如下所示：

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

有关编辑资源脚本的详细信息，请[参阅如何：以文本格式](../../windows/how-to-open-a-resource-script-file-in-text-format.md)打开资源脚本文件。 有关控制资源定义语句的详细信息，请参阅 Windows SDK 下的[公共控制参数](/windows/win32/menurc/common-control-parameters)：SDK Tools。

有关一般对话框的详细信息，请参阅 Windows SDK 中的[对话框](/windows/win32/api/winuser/nf-winuser-dialogboxw)和[CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) 。

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
中标识可执行文件包含对话框模板的模块的实例。

*lpTemplateName*<br/>
中标识对话框模板。 此参数为以 null 结尾的字符串的指针，该字符串指定对话框模板的名称或指定对话框模板的资源标识符的整数值。 如果参数指定资源标识符，则其高序位字必须为零，并且它的低序位字必须包含标识符。 您可以使用[MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew)宏来创建此值。

*hWndParent*<br/>
中标识拥有对话框的窗口。

*lpDialogProc*<br/>
中指向对话框过程。 有关对话框过程的详细信息，请参阅[DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc)。

*dwInitParam*<br/>
中在 WM_INITDIALOG 消息的*lParam*参数中指定要传递到对话框的值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

生成的对话框可以包含 ActiveX 控件。

请参阅 Windows SDK 中的[CreateDialog](/windows/win32/api/winuser/nf-winuser-createdialogw)和[CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) 。

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
指向要传递到控件的字符串的指针。 必须采用下列方式之一进行格式化：

- ProgID，如 "MSCAL"。Calendar. 7 "

- CLSID，如 "{8E27C92B-1264-101C-8A2F-040224009C02}"

- URL，如 "<http://www.microsoft.com>"

- 对活动文档的引用，例如 "file://\\\Documents\MyDoc.doc"

- Html 片段，如\<"MSHTML： html >\<BODY > 这是一/BODY >\</HTML >"\<的文本行

   > [!NOTE]
   > "MSHTML：" 必须在 HTML 片段之前，才能指定为 MSHTML 流。

*hWnd*<br/>
中控件将附加到的窗口的句柄。

*pStream*<br/>
中指向用于初始化控件的属性的流的指针。 可以为 NULL。

*ppUnkContainer*<br/>
弄将接收`IUnknown`容器的的指针地址。 可以为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

此全局函数提供与调用[AtlAxCreateControlEx](#atlaxcreatecontrolex)（*lpszName*， *hWnd*， *pStream*，null，null，null，null）; 相同的结果。

若要创建许可的 ActiveX 控件，请参阅[AtlAxCreateControlLic](#atlaxcreatecontrollic)。

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
指向要传递到控件的字符串的指针。 必须采用下列方式之一进行格式化：

- ProgID，如 "MSCAL"。Calendar. 7 "

- CLSID，如 "{8E27C92B-1264-101C-8A2F-040224009C02}"

- URL，如 "<http://www.microsoft.com>"

- 对活动文档的引用，例如 "file://\\\Documents\MyDoc.doc"

- Html 片段，如\<"MSHTML： html >\<BODY > 这是一/BODY >\</HTML >"\<的文本行

   > [!NOTE]
   > "MSHTML：" 必须在 HTML 片段之前，才能指定为 MSHTML 流。

*hWnd*<br/>
中控件将附加到的窗口的句柄。

*pStream*<br/>
中指向用于初始化控件的属性的流的指针。 可以为 NULL。

*ppUnkContainer*<br/>
弄将接收`IUnknown`容器的的指针地址。 可以为 NULL。

*ppUnkControl*<br/>
弄将接收`IUnknown`创建的控件的的指针的地址。 可以为 NULL。

*iidSink*<br/>
所包含对象上的传出接口的接口标识符。

*punkSink*<br/>
一个指针，指向`IUnknown`在已成功创建包含对象后，要连接到由*iidSink*在包含对象上指定的连接点的接收器对象的接口。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

`AtlAxCreateControlEx`类似于[AtlAxCreateControl](#atlaxcreatecontrol) ，但也可用于接收指向新创建的控件的接口指针，并设置用于接收由控件触发的事件的事件接收器。

若要创建许可的 ActiveX 控件，请参阅[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)。

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
指向要传递到控件的字符串的指针。 必须采用下列方式之一进行格式化：

- ProgID，如 "MSCAL"。Calendar. 7 "

- CLSID，如 "{8E27C92B-1264-101C-8A2F-040224009C02}"

- URL，如 "<http://www.microsoft.com>"

- 对活动文档的引用，例如 "file://\\\Documents\MyDoc.doc"

- Html 片段，如\<"MSHTML： html >\<BODY > 这是一/BODY >\</HTML >"\<的文本行

   > [!NOTE]
   > "MSHTML：" 必须在 HTML 片段之前，才能指定为 MSHTML 流。

*hWnd*<br/>
控件将附加到的窗口的句柄。

*pStream*<br/>
指向用于初始化控件的属性的流的指针。 可以为 NULL。

*ppUnkContainer*<br/>
将接收`IUnknown`容器的的指针地址。 可以为 NULL。

*bstrLic*<br/>
包含控件的许可证的 BSTR。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="example"></a>示例

有关如何使用`AtlAxCreateControlLic`的示例，请参阅[使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。

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
指向要传递到控件的字符串的指针。 必须采用下列方式之一进行格式化：

- ProgID，如 "MSCAL"。Calendar. 7 "

- CLSID，如 "{8E27C92B-1264-101C-8A2F-040224009C02}"

- URL，如 "<http://www.microsoft.com>"

- 对活动文档的引用，例如 "file://\\\Documents\MyDoc.doc"

- Html 片段，如\<"MSHTML： html >\<BODY > 这是一/BODY >\</HTML >"\<的文本行

   > [!NOTE]
   > "MSHTML：" 必须在 HTML 片段之前，才能指定为 MSHTML 流。

*hWnd*<br/>
控件将附加到的窗口的句柄。

*pStream*<br/>
指向用于初始化控件的属性的流的指针。 可以为 NULL。

*ppUnkContainer*<br/>
将接收`IUnknown`容器的的指针地址。 可以为 NULL。

*ppUnkControl*<br/>
弄将接收`IUnknown`创建的控件的的指针的地址。 可以为 NULL。

*iidSink*<br/>
所包含对象上的传出接口的接口标识符。

*punkSink*<br/>
一个指针，指向`IUnknown`在已成功创建包含对象后，要连接到由*iidSink*在包含对象上指定的连接点的接收器对象的接口。

*bstrLic*<br/>
包含控件的许可证的 BSTR。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

`AtlAxCreateControlLicEx`类似于[AtlAxCreateControlLic](#atlaxcreatecontrollic) ，但也可用于接收指向新创建的控件的接口指针，并设置用于接收由控件触发的事件的事件接收器。

### <a name="example"></a>示例

有关如何使用`AtlAxCreateControlLicEx`的示例，请参阅[使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。

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
中指向`IUnknown`控件的的指针。

*hWnd*<br/>
中承载控件的窗口的句柄。

*ppUnkContainer*<br/>
弄指向容器对象的`IUnknown`的指针的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

使用[AtlAxCreateControlEx](#atlaxcreatecontrolex)和[AtlAxCreateControl](#atlaxcreatecontrol)同时创建和附加控件。

> [!NOTE]
>  在调用`AtlAxAttachControl`之前，必须正确初始化要附加的控件对象。

##  <a name="atlaxgethost"></a>  AtlAxGetHost

获取指向指定窗口（如果有）的容器的直接接口指针（在给定容器的句柄的情况下）。

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>参数

*h*<br/>
中承载控件的窗口的句柄。

*pp*<br/>
弄`IUnknown`控件的容器的。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="atlaxgetcontrol"></a>  AtlAxGetControl

获取指向包含在指定窗口内的控件的直接接口指针（在给定控件的句柄的情况下）。

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>参数

*h*<br/>
中承载控件的窗口的句柄。

*pp*<br/>
弄`IUnknown`要承载的控件的。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="atlsetchildsite"></a>  AtlSetChildSite

调用此函数可将子对象的站点设置为`IUnknown`父对象的。

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>参数

*punkChild*<br/>
中指向子级的`IUnknown`接口的指针。

*punkParent*<br/>
中指向父级的`IUnknown`接口的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="atlaxwininit"></a>  AtlAxWinInit

此函数通过注册 **"AtlAxWin80"** 和 **"AtlAxWinLic80"** 窗口类以及一些自定义窗口消息来初始化 ATL 的控件托管代码。

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>返回值

如果控件承载代码的初始化成功，则为非零值;否则为 FALSE。

### <a name="remarks"></a>备注

使用 ATL 控件托管 API 之前，必须先调用此函数。 调用此函数后，可以在对[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww)或[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的调用中使用 **"AtlAxWin"** 窗口类，如 Windows SDK 中所述。

##  <a name="atlaxwinterm"></a>  AtlAxWinTerm

此函数通过注销 **"AtlAxWin80"** 和 **"AtlAxWinLic80"** 窗口类来取消 ATL 的控件承载代码。

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

此函数只需调用[UnregisterClass](/windows/win32/api/winuser/nf-winuser-unregisterclassw) ，如 Windows SDK 中所述。

如果调用[AtlAxWinInit](#atlaxwininit)并且不再需要创建主机窗口，则在销毁所有现有主机窗口后，调用此函数以进行清理。 如果不调用此函数，则在进程终止时将自动注销窗口类。

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
中指向要为其返回信息的对象的指针。

*plibid*<br/>
弄一个指针，指向包含源接口定义的类型库的 LIBID。

*piid*<br/>
弄指向对象的默认源接口的接口 ID 的指针。

*pdwMajor*<br/>
弄一个指针，指向包含源接口定义的类型库的主版本号。

*pdwMinor*<br/>
弄一个指针，指向包含源接口定义的类型库的次版本号。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

`AtlGetObjectSourceInterface`可为您提供默认源接口的接口 ID，以及描述该接口的类型库的 LIBID 和主版本号和次版本号。

> [!NOTE]
>  要使此函数成功检索所请求的信息， *punkObj*表示的对象必须实现`IDispatch` （并通过`IDispatch::GetTypeInfo`返回类型信息`IProvideClassInfo2` ），此外，它还必须实现或`IPersist`. 源接口的类型信息必须与的类型信息`IDispatch`位于同一类型库中。

### <a name="example"></a>示例

下面的示例演示了如何定义事件接收器类`CEasySink`，从而减少了可`IDispEventImpl`传递给 bare essentials 的模板参数的数目。 `EasyAdvise`和`EasyUnadvise`用于 `AtlGetObjectSourceInterface` 在调用 [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) 或 [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) 之前初始化 [IDispEventImpl](../../atl/reference/idispeventimpl-class.md) 成员。

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)<br/>
[复合控件宏](../../atl/reference/composite-control-macros.md)
